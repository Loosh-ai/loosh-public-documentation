## Quantization-Workload Emission Formula

Below is a formula to allocate a total emission pool \(Z\) among miners who submit quantized models. Allocation is based primarily on **accuracy**, with secondary consideration for **model size**, **protocol/target compliance**, **processing speed** (only if significantly different), and **availability**.



### 1. Definitions

1. **Total emission for this challenge**  

$Z$

   The total reward pool (in TAO) allocated to miners who submit quantized models meeting the requirements.

2. **Set of participating miners**  

   $$y = \{\,i \mid \text{miner } i \text{ submitted a quantized model adhering to protocol/targets}\}.$$
 

3. **Accuracy score of miner \(i\)**  
$$
   A_i \in [0,\,1]
$$
   Defined as the normalized accuracy (e.g., validation-set accuracy divided by 100%). Since accuracy is the dominant factor, we assign it the largest weight.

4. **Model-size score of miner \(i\)**  

   Let \(M_i\) be the size (in megabytes) of miner \(i\)’s quantized model. Define:  

$$
   S_i = \frac{M_{\max}}{M_i}, 
   \quad 
   \text{where } 
   M_{\max} = \max_{j\in y} M_j.
 $$

   Hence \(S_i \in (0,1]\), with smaller models receiving a larger \(S_i\).

5. **Compliance score of miner \(i\)**  

$$
   P_i \in [0,\,1]
 $$

   A continuous measure (or binary if strict) of how well the submitted quantized model adheres to the protocol and meets target specifications (e.g., correct quantization scheme, target bit-width, correct repository structure on Hugging Face). \(P_i = 1\) if fully compliant; lower values if minor deviations.

6. **Raw inference-latency of miner \(i\)**  

$$
   \ell_i > 0 
   \quad (\text{in seconds, measured on a fixed hardware baseline}).
 $$

7. **Processing-speed score of miner \(i\)**  

   Define a small threshold ($\tau \ge 0\) so that “minor differences” in latency are ignored. Let  

$$
   \ell_{\min} = \min_{\,j \in y} \ell_j
 $$

   be the best (lowest) latency among all winners. Then set  

$$
   V_i = 
   \begin{cases}
     1, & \ell_i \le \ell_{\min} + \tau, \\[6pt]
     \displaystyle \frac{\ell_{\min} + \tau}{\ell_i}, & \ell_i > \ell_{\min} + \tau.
   \end{cases}
 $$

   Thus, if miner \(i\) is within ($\tau\) seconds of the fastest, \(V_i = 1\). Otherwise \(V_i < 1\), penalizing significant slowdowns.

8. **Availability score of miner \(i\)**  

$$
   U_i \in [0,\,1]
$$

   Defined as  

$$
   U_i = \frac{\text{time miner }i\text{ was reachable over the evaluation window}}{\text{window length}}.
$$

9. **Hyperparameters (weights)**  
$$
   \alpha,\;\beta,\;\gamma,\;\delta,\;\zeta \;\ge\; 0,
   \qquad 
   \alpha \;>\; \beta,\;\gamma,\;\delta,\;\zeta.
$$
 
- ($\alpha$) (coefficient for **accuracy**)  
- ($\beta$) (coefficient for **model-size**)  
- ($\gamma$) (coefficient for **compliance**)  
- ($\delta$) (coefficient for **speed**)  
- ($\zeta$) (coefficient for **availability**)  

   In practice, choose ($alpha$) significantly larger than the others so that accuracy dominates.

   Additionally, choose a **minimum-guarantee floor**  

$$
   \varepsilon > 0
$$

   so that no miner’s composite weight drops below ($\varepsilon$).


### 2. Composite Weight Computation

For each miner ($i \in y$), compute:

1. **Raw composite weight**  

$$
   w_i^{\mathrm{raw}}
   \;=\;
   \alpha\,A_i 
   \;+\; 
   \beta\,S_i 
   \;+\; 
   \gamma\,P_i 
   \;+\; 
   \delta\,V_i 
   \;+\; 
   \zeta\,U_i.
$$

   Because ($\alpha$) is much larger than ($\beta,\gamma,\delta,\zeta$), accuracy ($A_i$) drives most of the allocation.

2. **Apply minimum-guarantee floor**  

$$
   \widetilde{w}_i 
   \;=\; 
   \max\bigl(w_i^{\mathrm{raw}},\,\varepsilon\bigr).
$$

   Ensures every compliant miner gets at least a small nonzero share.

3. **Sum of floored weights**  

$$
   \widetilde{W} 
   \;=\; 
   \sum_{j \in y} \widetilde{w}_j,
   \quad 
   \widetilde{W} > 0.
$$


### 3. Emission Allocation

Each miner ($i \in y$) receives:  

$$
E_i 
= 
Z 
\;\times\; 
\frac{\widetilde{w}_i}{\widetilde{W}},
\qquad
E_i = 0 
\quad\text{if}\quad i \notin y.
$$

Equivalently, for ($i \in y$):  

$$
E_i 
= 
Z 
\;\times\; 
\frac{\displaystyle 
  \max\bigl(
    \alpha\,A_i 
    + 
    \beta\,S_i 
    + 
    \gamma\,P_i 
    + 
    \delta\,V_i 
    + 
    \zeta\,U_i,
    \;\varepsilon
  \bigr)
}
{\displaystyle
  \sum_{j \in y} 
  \max\bigl(
    \alpha\,A_j 
    + 
    \beta\,S_j 
    + 
    \gamma\,P_j 
    + 
    \delta\,V_j 
    + 
    \zeta\,U_j,
    \;\varepsilon
  \bigr)
}.
$$

- Since ($\alpha\) is dominant, the highest-accuracy quantized models earn most of the pool.  
- Model-size score \(S_i\), compliance \(P_i\), and availability \(U_i\) provide moderate secondary boosts.  
- Processing-speed \(V_i\) only deviates from 1 if latency exceeds ($\ell_{\min} + \tau\), so it only penalizes “significantly slower” submissions.



### 4. Example Walkthrough

Suppose five miners submit quantized models. Their measured metrics are:

| Miner | ($A_i$) (accuracy) | ($M_i$) (MB) | ($P_i$) (compliance) | ($\ell_i$) (s) | ($U_i) (avail.) -|
|:-----:|:------------------:|:------------:|:--------------------:|:--------------:|:----------------:|
| 1     | 0.92               | 50           | 1.00                 | 0.60           | 0.95             |
| 2     | 0.90               | 45           | 0.90                 | 0.55           | 0.90             |
| 3     | 0.89               | 40           | 1.00                 | 0.80           | 0.98             |
| 4     | 0.85               | 30           | 0.95                 | 1.50           | 0.80             |
| 5     | 0.83               | 25           | 1.00                 | 0.70           | 0.88             |  
  
  
1. Compute  

$$
   M_{\max} = 50.
$$

   Then  

$$
   S_1 = \frac{50}{50} = 1.00,\quad
   S_2 = \frac{50}{45} \approx 1.111,\quad
   S_3 = \frac{50}{40} = 1.25,\quad
   S_4 = \frac{50}{30} \approx 1.667,\quad
   S_5 = \frac{50}{25} = 2.00.
$$

2. Latency threshold:  

$$
   \ell_{\min} = 0.55 \quad(\text{miner 2}).
$$
 
   Choose ($\tau = 0.10.$)  Then ($\ell_{\min} + \tau = 0.65.$) Compute ($V_i$):  

- Miner 1: ($\ell_1 = 0.60 \le 0.65 \;\Rightarrow\; V_1 = 1.00.$)  
- Miner 2: ($\ell_2 = 0.55 \le 0.65 \;\Rightarrow\; V_2 = 1.00.$)  
- Miner 3: ($\ell_3 = 0.80 > 0.65 \;\Rightarrow\; V_3 = \tfrac{0.65}{0.80} \approx 0.8125.$)  
- Miner 4: ($\ell_4 = 1.50 > 0.65 \;\Rightarrow\; V_4 = \tfrac{0.65}{1.50} \approx 0.4333.$)  
- Miner 5: ($\ell_5 = 0.70 > 0.65 \;\Rightarrow\; V_5 = \tfrac{0.65}{0.70} \approx 0.9286.$)

3. Choose hyperparameters (emphasizing accuracy):  

$$
   \alpha = 10,\quad
   \beta = 1,\quad
   \gamma = 2,\quad
   \delta = 0.5,\quad
   \zeta = 1,\quad
   \varepsilon = 0.1.
$$

4. Compute raw weights  

$$

   w_i^{\mathrm{raw}} = 10A_i + 1S_i + 2P_i + 0.5V_i + 1U_i:
$$

- **Miner 1**  

$$
     w_1^{\mathrm{raw}} 
     = 10(0.92) + 1(1.00) + 2(1.00) + 0.5(1.00) + 1(0.95) 
     = 9.20 + 1.00 + 2.00 + 0.50 + 0.95 = 13.65.
$$

- **Miner 2**  

$$
     w_2^{\mathrm{raw}} 
     = 10(0.90) + 1(1.111) + 2(0.90) + 0.5(1.00) + 1(0.90) 
     = 9.00 + 1.111 + 1.80 + 0.50 + 0.90 \approx 13.311.
$$

- **Miner 3**  

$$
     w_3^{\mathrm{raw}} 
     = 10(0.89) + 1(1.25) + 2(1.00) + 0.5(0.8125) + 1(0.98) 
     = 8.90 + 1.25 + 2.00 + 0.40625 + 0.98 \approx 13.53625.
$$ 
- **Miner 4**

$$
     w_4^{\mathrm{raw}} 
     = 10(0.85) + 1(1.667) + 2(0.95) + 0.5(0.4333) + 1(0.80) 
     = 8.50 + 1.667 + 1.90 + 0.21665 + 0.80 \approx 13.08365.
$$ 

- **Miner 5**  

$$
     w_5^{\mathrm{raw}} 
     = 10(0.83) + 1(2.00) + 2(1.00) + 0.5(0.9286) + 1(0.88) 
     = 8.30 + 2.00 + 2.00 + 0.4643 + 0.88 \approx 13.6443.
$$

5. Apply minimum floor ($\varepsilon = 0.1$):  
   Since each ($w_i^{\mathrm{raw}} \gg 0.1$),  

$$
   \widetilde{w}_i = w_i^{\mathrm{raw}}
   \quad(\text{none hit the floor}).
$$

6. Sum floored weights  

$$
   \widetilde{W} 
   = 13.65 + 13.311 + 13.53625 + 13.08365 + 13.6443 
   \approx 67.2252.
$$

7. Allocate emissions (e.g., ($Z = 1000$))  

$$
   \begin{aligned}
   E_1 &= 1000 \times \frac{13.65}{67.2252} \approx 203.10,\\
   E_2 &= 1000 \times \frac{13.311}{67.2252} \approx 197.96,\\
   E_3 &= 1000 \times \frac{13.53625}{67.2252} \approx 201.44,\\
   E_4 &= 1000 \times \frac{13.08365}{67.2252} \approx 194.60,\\
   E_5 &= 1000 \times \frac{13.6443}{67.2252} \approx 203.90.
   \end{aligned}
$$

   Check: ($203.10 + 197.96 + 201.44 + 194.60 + 203.90 \approx 1000.$)

- Miner 5 earned slightly more than Miner 1 because its model was smallest ($(S_5 = 2.00$) vs. ($S_1 = 1.00$)), despite slightly lower accuracy.  
- Miner 4 received the lowest share because its accuracy (0.85) was the lowest and it also had slower inference ($V_4 \approx 0.4333$).  
- The speed penalty only applied to Miners 3, 4, 5 whose latency exceeded ($\ell_{\min} + \tau$).



### 5. Compact Formula

For each ($i \in y$):

1. **Compute sub-scores**  

$$
   S_i = \frac{M_{\max}}{M_i}, 
   \quad
   P_i \in [0,1], 
   \quad
   V_i = 
     \begin{cases}
       1, & \ell_i \le \ell_{\min} + \tau,\\
       \displaystyle \frac{\ell_{\min} + \tau}{\ell_i}, & \ell_i > \ell_{\min} + \tau,
     \end{cases}
$$

$$
   U_i = \frac{\text{uptime}_i}{\text{window length}}, 
   \quad
   \ell_{\min} = \min_{j\in y} \ell_j, 
   \quad
   M_{\max} = \max_{j\in y} M_j.
$$

2. **Raw composite weight**  

$$
   w_i^{\mathrm{raw}} 
   = \alpha\,A_i + \beta\,S_i + \gamma\,P_i + \delta\,V_i + \zeta\,U_i.
$$

3. **Floor at ($\varepsilon$)**  

$$
   \widetilde{w}_i 
   = \max\bigl(w_i^{\mathrm{raw}},\,\varepsilon\bigr).
$$

4. **Sum of floored weights**  

$$
   \widetilde{W} 
   = \sum_{j\in y} \widetilde{w}_j, 
   \quad 
   \widetilde{W} > 0.
$$

5. **Allocate**  
$$
   E_i =  Z \times \displaystyle\frac{\widetilde{w}_i}{\widetilde{W}} \\
where (i \in y)
$$

- Choose ($\alpha \gg \beta,\gamma,\delta,\zeta$) so accuracy dominates.  
- Model-size score ($S_i$) rewards smaller quantized files.  
- Compliance score ($P_i$) enforces correct protocol/targets.  
- Speed score ($V_i$) only penalizes when ($\ell_i$) exceeds ($\ell_{\min} + \tau$).  
- Availability ($U_i$) provides a modest bonus for consistently reachable nodes.  
- Floor ($\varepsilon$) ensures even marginal submissions get a token share.  
