# Loosh.ai Incentive Design

## Abstract
Loosh.ai has a variety of workloads to be run on bittensor. Each workload has a different frequency, goal, compute requirement, and evaluative mechanism. This document describes each of the general types of workloads and the incentive design for that workload.

## Subnets
We recognize that the variety of workloads may present a challenge to attracting miners who may find the system too complex. The best approach to mitigate this is to segregate different workloads into separate subnets. There has been some discussion of sub-subnets, which would be an ideal scenario, as we could easily segregate workloads by type at a fine-grained level. However, this is speculation and no official feature has been announced. As such, we will proceed with the assumption that such functionality will not exist in the timeline in which we wish to begin running workloads on bittensor.

Loosh.ai intends to implement two subnets:

### Loosh-Communication
- Focuses on building empathetic and emotionally intelligent communication systems for AI agents.
- Includes the ability to understand and respond to:
  - Emotion
  - Tone
  - Mental state
  - Subtext
  - Intention

### Loosh-Cognition
- A decentralized model of machine reasoning, reflection, memory, and self-directed improvement.
- Inspired by neuroscience, this subnet implements discrete cognitive functions as individual models working in coordination.
- Each function is handled by a lightweight, optimized, quantized model trained independently—enabling interpretability, composability, and continuous evolution.


## Workload Types
The tasks required of the subnets align with four types of workloads:
1. Pretraining  
2. Inference  
3. Fine Tuning  
4. Quantization  

### Pretraining
We have a need for some models to be trained from the ground up. These mostly reside in the Loosh-Communication subnet and are focused on multimodal identification of emotional and mental states. In particular, we intend to train models for the following functions:

#### Multimodal Emotion Detection
- **Audio:** Tone, pitch, cadence, hesitation  
- **Visual:** Facial expressions, micro-gestures, posture  
- **Text:** Sentiment, sarcasm, ambiguity, implicit meaning  

#### Multimodal Nonverbal Communication (NVC)
- Interprets body language, rhythm, gaze, and subtle environmental signals  
- Anchors communications in physiological and neurological data (e.g., EEG, EMF)  

#### Multimodal EEG Analysis
- Detects and classifies brainwave states  
- Measures attention, calmness, stress, altered states  
- Investigates extended consciousness phenomena (telepathy, intuition)  

#### MIME: MIMicking Emotions for Empathetic Response
A flagship model family trained on multimodal data to:
- Interpret emotional context and unstated needs  
- Generate responses that reflect empathy, understanding, and nuance  
- Handle sarcasm, euphemism, ambiguity, and emotionally charged inputs  

The pretraining workloads will be implemented as a multi-round competition. Each round, a set of miners will compete to train a model with the greatest improvement over the starting point. Each round will be awarded on a winner-takes-all basis. Because each model has a different purpose and validation metrics, the methodology for validating model improvement will be determined and communicated on a per-model basis.

We find Subnet 9’s incentive mechanism to be thorough and well tested for pretraining workloads. As such, and seeing no reason to reinvent the wheel, we intend to gratefully leverage their code and approach to this problem.


### Inference
We intend to not only train our models on bittensor but also to run our cognition engine on it. Each subsystem within the Loosh-Cognition engine is designed to leverage one or more types of inference to accomplish its function.  
- Requests for inference will be placed on the chain and distributed to the appropriate subsystem.  
- Validators will receive the challenge and send it to a parametrically driven number of miners.  
- The responses from the miners will be evaluated and scored for consensus.  
- The response with the most miner agreement will be awarded the emissions for that challenge.  
- Each correct respondent will receive a share of the pool of emissions for that challenge, with additional scoring for availability and processing speed.  

[You can view the incentive design here](inference_scoring.md)

### Fine Tuning
During the course of inference, we will collect or extract feedback that can be used to fine tune the models. Similar to pretraining, we will run winner-takes-all competitions to fine tune models. Also, as with pretraining, Macrocosmos has provided a well-structured and well-tested mechanism for scoring based on evaluating improvement of models against a dynamically scaling improvement threshold (epsilon). We intend to gratefully leverage their code and approach as a foundation for our scoring.


### Quantization
We intend to provide quantized versions of our models for running inference. This will reduce the compute requirements significantly, which will allow lower-performing miners an opportunity to earn. We will provide challenges that point to a non-quantized model and provide guidance on the protocol and targets.  
- Miners will upload their versions to Hugging Face.  
- Accuracy evaluation will be based on:
  - The size of the quantized model  
  - Adherence to protocols and targets  
- Scoring will be based on accuracy, processing speed, and availability.  

[You can view the incentive design here](quantization_scoring.md)

