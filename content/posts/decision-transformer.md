+++
title = 'The Decision Transformer'
date = 2024-02-05T19:06:41+08:00
draft = false
+++



# What are Decision Transformers?
[Decision Transformers](https://arxiv.org/abs/2106.01345) are a type of [transformer neural network achitecture](https://jalammar.github.io/illustrated-transformer/) suited for the offline reinforcement learning setting.

Although, it has been shown [that the transformer architecture is not the pure reason Sequence Modeling can excel reinforcement learning tasks](https://arxiv.org/abs/2211.14655), and that [online learning can still be a challenge worth inversitgating](https://sled.eecs.umich.edu/media/eecs595_fa22/11_Nguyen_Glasscock.pdf), it is still an important building block to consider why and how sequence models can achieve state of the art performance in famous RL tasks, and perhaps even play games!

![Image](/img/mario.png)


## Why sequence models?
Using sequence modeling means treating each RL trajectory just like text, and then using the sequence prediction capabilities of sequence models like the transformer to predict the next token in the sequence(i.e. what is most likely going to happen, or what should happen).

There are some advantages to this method of learning the environment: 

1. We do not bootstrap values, which led to instabilities, removing one of the 3 members of the deadly triad problem in RL.

2. The self-attention mechanism can automatically learn and do credit assignment, and can even be robust to "distractor" events that might throw off the agent.

3. Because we are not bootstrapping using methods like Q-Learning, there is no pesky value overestimaation, and that there are no errors that can propagate and derail the training process, we are just learning a sequence.


The interesting thing about this process is that we can simple introduce a prior to the model's probability output([using bayes' theorem](https://www.statlect.com/glossary/prior-probability)), and this will give us the shortest path!


## How does the network work?
Instead of using the transformer architecture, which gets the input sequence directly(the main task in the original paper was sequence to sequence translation), the authors of the decision transformer paper use the [GPT(Generative Pre-Training)](https://paperswithcode.com/paper/improving-language-understanding-by) architecture, which masks parts of the input not currently generated, to give a chance to the network to indpendently generate the sequence.

![Image](/img/GPT.png)


## What Trajectories are given to the network?
One important aspect to consider, is the fact that we want to *Maximize future rewards*. A reinforcement learning agent, unlike a langauge model, needs to generate trajectories based on future outcomes(Expected Return), instead of previously generated tokes(Past Reward). Hence, as input to the network we cannot simply give it the rewards received until now, but a sort of "oracle reward signal", called the return to go, meaning **the remaining return until the end of the episode**.

This, in this case, immediately means that we cannot learn online, since we do not have access to the return-to-go in the online setting, and that trajectories must have been compeleted before training can begin.







