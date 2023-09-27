# Secrets of RLHF in Large Language Models Part I: PPO

## Abstract
- Objective: Alignment with humans assumes paramout significance.
- Tool: Reinforcement learning with human feedback (RLHF)
  - Reward models: measure human preferences
  - Proximal policy optimization (PPO): optimize polocy model outputs
  - Process supervision: improve step-by-step reasoning capabilities.
- Challenges: Reward design, environment interaction, agent training, coupled with huge trial and error cost of large language models.
- Goal: Dissect the framework of RLHF, re-evaluate the inner workings of PPO, and explore how the parts comprising PPO algorithms impact policy agent training.
- Results: Identify policy constraints being the key factor for the effective implementation of the PPO algorithm. Explore the PPO-max, an advanced version of PPO algorithm, to efficiently improve the training stability of the policy model. 
- Achievements: Based on our main results, we perform a comprehensive analysis of RLHF abilities compared with SFT models and ChatGPT. Beyond additional qualitative results, we even find that LLMs successfully trained by our algorithm can often better understand the deep meaning of the queries, and its responses are more able to hit people’s souls directly.
------------------------------

## Introduction
LLMs are trained to capture the data characteristics of pre-training corpora (including both high-quality and low-quality data), these models are likely to express unintended behaviors such as making up facts, generating biased or toxic text or even harmful content for humans.

Contributions are summarized as follows: 1) we release competitive Chinese and English reward models, respectively, which have good cross-model generalization ability, alleviating the cost of relabeling human preference data; 2) we conduct in-depth analysis on the inner workings of PPO algorithm and propose the PPO-max algorithm to ensure stable model training; and 3) we release the complete PPO-max codes to ensure that the LLMs in the current SFT stage can be better aligned with humans.

## Reinforcement Learning from Human Feedback
The training process of AI assistant comprises three main stages: supervised fine-tuning (SFT), reward model (RM) training, and proximal policy optimization (PPO) on this reward model. During the SFT phase, the model learns to engage in general human-like dialogues by imitating human-annotated dialogue examples. Subsequently, the reward model is trained, in which the model learns to compare the preference of different responses based on human feedback. Lastly, in the PPO phase, the model is updated based on feedback from the reward model, striving to discover an optimized policy through exploration and exploitation. In the RLHF process, we mainly consider the stages of RM training and reinforcement learning via PPO. The PPO algorithm follows a series of steps as depicted in Figure 1.
