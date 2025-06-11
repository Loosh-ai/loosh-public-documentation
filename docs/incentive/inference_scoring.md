## Definitions

1. **Total emission for this challenge**  

$Z$
   The total reward pool (in TAO) allocated to the “winning” miners for this particular challenge.

2. **Set of winning miners** 

$$
   y = \{\,i \mid \text{miner } i \text{ submitted the consensus response}\,\}
$$

   Only those miners whose outputs exactly match the consensus (plurality/majority) answer are included in $y$.

3. **Availability score of miner $i$**  
   
$$
   A_i \in [0,\,1]
$$

   Defined as  
   
   $$
   A_i = \frac{\text{time miner } i \text{ was reachable over the window}}{\text{window length}}
   $$

4. **Raw latency of miner $i$**  

$$
   \ell_i > 0 \quad (\text{in seconds})
$$

5. **Nonlinear speed score of miner $i$**  

$$ 
   S_i = \ell_i^{-\gamma}, \quad \gamma > 1.
$$ 

- If $\gamma = 1$, then $S_i = \frac{1}{\ell_i}.$  
- If $\gamma > 1$, slower nodes are penalized more severely (e.g., $\gamma = 2$ gives $\S_i = \frac{1}{\ell_i^2}$

6. **Preliminary (unfloored) composite weight for miner $i$**  

$$
   w_i^{\text{raw}} = \alpha\,A_i + \beta\,S_i = \alpha\,A_i + \beta\,\ell_i^{-\gamma},\quad\alpha,\beta\ge 0,\; \alpha + \beta > 0.
$$ 

- $\alpha$ is the coefficient for availability.  
- $\beta$ is the coefficient for (nonlinear) speed.

7. **Floored composite weight (applying minimum guarantee)**  

$$
   \widetilde{w}_i = \max\bigl(w_i^{\text{raw}},\,\varepsilon\bigr),\quad \varepsilon > 0.
$$

   Every winning miner’s weight is guaranteed to be at least $\varepsilon$.

8. **Sum of floored weights**  

$$
   \widetilde{W} = \sum_{j \in y} \widetilde{w}_j = \sum_{j \in y} \max\bigl(\alpha\,A_j + \beta\,\ell_j^{-\gamma},\,\varepsilon\bigr).\\ 
  
$$

$$
Since \varepsilon > 0 and \lvert y\rvert \ge 1, we have \widetilde{W} > 0
$$


## 2. Final Emission Allocation

For each miner $i\in y$, define their emission share $E_i$ as  

$$
E_i = \begin{cases}Z \times \displaystyle\frac{\widetilde{w}_i}{\widetilde{W}}, & i \in y, \\  [1em] 0, & i \notin y \end{cases}
$$  

Equivalently, for $i \in y$:  

$$
E_i = Z \times \frac{\max\bigl(\alpha\,A_i + \beta\,\ell_i^{-\gamma},\,\varepsilon \bigr)} {\sum_{j\in y} \max\bigl(\alpha\,A_j + \beta\,\ell_j^{-\gamma},\,\varepsilon \bigr)}
$$  

- Every winning miner $i \in y$ is guaranteed at least $\displaystyle E_i \ge Z \times \frac{\varepsilon}{\widetilde{W}}$.  
- If $\alpha\,A_i + \beta\,\ell_i^{-\gamma} > \varepsilon$, miner $i$ collects a share proportional to $\alpha\,A_i + \beta\,\ell_i^{-\gamma}$.  
- If $\alpha\,A_i + \beta\,\ell_i^{-\gamma} \le \varepsilon$, miner $i$ is treated as having weight exactly $\varepsilon$


## 3. Step-by-Step Summary

1. **Choose hyperparameters**:  
   - $\alpha,\beta \ge 0$, not both zero (weights for availability vs. speed).  
   - $\gamma > 1$ (nonlinear exponent on latency).  
   - $\varepsilon > 0$ (minimum-guarantee floor).

2. **Collect each winning miner’s metrics**:  
   - $A_i \in [0,1]$ (availability fraction).  
   - $\ell_i > 0$ (observed round-trip latency in seconds).

3. **Compute nonlinear speed**:  

$$
   S_i = \ell_i^{-\gamma}.
$$

4. **Compute raw composite weight**:  

$$
w_i^{\text{raw}} = \alpha\,A_i + \beta\,\ell_i^{-\gamma}.
$$

5. **Floor at $\varepsilon$**:  

$$
\widetilde{w}_i = \max\bigl(w_i^{\text{raw}},\,\varepsilon\bigr).
$$

6. **Sum all floored weights**:  

$$
\widetilde{W} = \sum_{j\in y} \widetilde{w}_j.
$$

7. **Allocate emissions**:  

$$
E_i = Z \times \frac{\widetilde{w}_i}{\widetilde{W}}, \quad E_i=0 \text{ if } i\notin y.
$$


## 4. Nonlinear speed penalty and Minimum-guarantee floor

These factors ensure that every winner earns some share, and that the fastest are awarded commensurately

- Total challenge emission:  

$$
  Z = 1000
  $$

- Winning miners:  

$$ 
  y = \{\,m_1,\,m_2,\,m_3\}
$$

- Availability over the last 24 h:

$$  
  A_{m_1} = 0.90,\quad A_{m_2} = 0.75,\quad A_{m_3} = 1.00.
$$

- Latencies (seconds):  

$$
  \ell_{m_1} = 0.8,\quad \ell_{m_2} = 2.0,\quad \ell_{m_3} = 1.0.
$$

- Convert to nonlinear speed ($\gamma = 2$):  

$$
 \begin{aligned}
  S_{m_1} = (0.8)^{-2} = 1.5625,\\
  S_{m_2} = (2.0)^{-2} = 0.25, \\
  S_{m_3} = (1.0)^{-2} = 1.00
\end{aligned}
$$

- Hyperparameters:  

$$
 \begin{aligned}
  \alpha = 1, \\ \quad \beta = 1,\\ \quad \gamma = 2,\\ \quad \varepsilon = 0.5.
     \end{aligned}
$$

1. **Compute raw weights**:  

$$
 \begin{aligned}
   w_{m_1}^{\text{raw}} = \alpha\,A_{m_1} + \beta\,S_{m_1} = 0.90 + 1.5625 = 2.4625 \\
   w_{m_2}^{\text{raw}} = 0.75 + 0.25 = 1.00,\\
   w_{m_3}^{\text{raw}} = 1.00 + 1.00 = 2.00.
   \end{aligned}
$$

2. **Apply floor** ($\varepsilon = 0.5$):  

$$
 \begin{aligned}
   \widetilde{w}_{m_1} = \max(2.4625,\,0.5) = 2.4625, \\
   \widetilde{w}_{m_2} = \max(1.00,\,0.5) = 1.00, \\
   \widetilde{w}_{m_3} = \max(2.00,\,0.5) = 2.00.
   \end{aligned}
$$

3. **Sum floored weights**:  
$$
   \widetilde{W} = 2.4625 + 1.00 + 2.00 = 5.4625
$$

4. **Allocate emissions**:  

$$
 \begin{aligned}
   E_{m_1} = 1000 \times \frac{2.4625}{5.4625} \approx 450.64, \\
   E_{m_2} = 1000 \times \frac{1.00}{5.4625} \approx 183.14, \\
   E_{m_3} = 1000 \times \frac{2.00}{5.4625} \approx 366.22.
\end{aligned}
$$

$$
   Check: (450.64 + 183.14 + 366.22 \approx 1000.)
$$

## 5. Final Compact Formula

Putting everything together, for each $i \in y$:  

1. Compute  

$$
   S_i = \ell_i^{-\gamma},\quad w_i^{\text{raw}} = \alpha\,A_i + \beta\,\ell_i^{-\gamma}
$$

2. Floor at $\varepsilon$:  
$$
   \widetilde{w}_i = \max\bigl(w_i^{\text{raw}},\,\varepsilon\bigr)
$$

3. Sum all floored weights:  

$$
   \widetilde{W} = \sum_{j\in y} \widetilde{w}_j
$$

4. Allocate:  

$$
   E_i = Z \times \frac{\widetilde{w}_i}{\widetilde{W}}, \quad E_i = 0 \text{ for } i\notin y
$$

Equivalently:  

$$
\boxed{  
   E_i = \begin{cases}  
    Z \times \displaystyle \frac{\max\bigl(\alpha\,A_i + \beta\,\ell_i^{-\gamma},\,\varepsilon\bigr)} {\displaystyle\sum_{j\in y} \max\bigl(\alpha\,A_j + \beta\,\ell_j^{-\gamma},\,\varepsilon\bigr)}  
    \end{cases}  
    }
$$

- $\alpha, \beta$ control the balance between availability and (nonlinear) speed.  
- $\gamma$ dictates how harshly you penalize latency.  
- $\varepsilon$ ensures no winner gets “zero” even if their combined availability + speed is tiny.  
