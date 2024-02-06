+++
title = 'The Decision Transformer'
date = 2024-02-05T19:06:41+08:00
draft = false
+++



# What are Decision Transformers?
[Decision Transformers](https://arxiv.org/abs/2106.01345) are a type of [transformer neural network achitecture](https://jalammar.github.io/illustrated-transformer/) suited for the offline reinforcement learning setting.

Although, it has been shown [that the transformer architecture is not the pure reason Sequence Modeling can excel reinforcement learning tasks](https://arxiv.org/abs/2211.14655), and that [online learning can still be a challenge worth inversitgating](https://sled.eecs.umich.edu/media/eecs595_fa22/11_Nguyen_Glasscock.pdf), it is still an important building block to consider why and how sequence models can achieve state of the art performance in famous RL tasks, and perhaps even play games!

![Image](/mario.png)


### Why sequence models?
Using sequence modeling means treating each RL trajectory just like text, and then using the sequence prediction capabilities of sequence models like the transformer to predict the next token in the sequence(i.e. what is most likely going to happen, or what should happen).

There are some advantages to this method of learning the environment: 

1. We do not bootstrap values, which led to instabilities, removing one of the 3 members of the deadly triad problem in RL.

2. The self-attention mechanism can automatically learn and do credit assignment, and can even be robust to "distractor" events that might throw off the agent.

3. Because we are not bootstrapping using methods like Q-Learning, there is no pesky value overestimaation, and that there are no errors that can propagate and derail the training process, we are just learning a sequence.


The interesting thing about this process is that we can simple introduce a prior to the model's probability output([using bayes' theorem](https://www.statlect.com/glossary/prior-probability)), and this will give us the shortest path!

### How does the network work?
Let's take a look at how the architecture works: The transformer architecture is an autoregressive architecture, meaning previous outputs are used as new inputs to the network. Let's take a look at the Decision Transformer's input: 

![Image](/DT.png)


