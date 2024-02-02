+++
title = 'Sequence modeling and RL'
date = 2024-02-01T17:59:12+03:30
draft = false
+++


## The transformer architecture opens up a new way of doing RL

### Why would a reinforcement learning algorithm need to learn value functions? What is the purpose of us learning values? while the goal is to create a policy that takes the best actions?

There are some arguments as to why this might be the case. firstly, it's a need to understand these models, instead of having black boxes, having the value function helps the engineer understand which states the agent likes, and which actions are liked for each state. This gives us the flexibility to interpret the actions and the learn about the enviornment, through the agent.

But What about sequence modeling? Isn't that just a better way of doing RL? the fact that Transfomers and sequence models are so prevalent today, lends itself to the success of LLMs like chatGPT and the like, which have shown to have incredibly human like or even exceeding human like performance. 
This has made them a promising avenue of research for many other tasks which are amenable to a sequence model, of which Reinforcement learning definitely is. 


What does it mean to model RL as a sequence model?

A sequence model is a just an alphabet and a langauge (in the chomskian sense) and inputting a sequence from the language, and expecting the model to output a next token (a member of the alphabet) which is in the language and which in some semantic sense (could be linguistic or otherwise), has meaning to be there. 

To look at RL from this lens, it means to show that any interaction the RL agent takes, are alphabets in a language and there are tokens to be predicted. This is trivial to demonstrate, as if we take the sequence of states, actions, rewards, and use these as tokens, then the agent can simply look at them as an alphabet and try to learn the "language" of the environment. 
By learning the language of the enviornment, I mean to know how to make sense of the situation, and find the patterns of the enviornment, to correctly output the next token.


### How would such an agent be trained?

The most natural way to train such an agent is in an offline manner. This means that we need to get the full episodes of the task, and first, learn to predict the next token unconditionally, which would be akin to making predictions and finding value functions (but there are some differences), and on the other hand, we could simply, just like prompting chagpt or anyother agent, we could prompt the agent to maximize the reward from the enviornment, by taking actions that do so (This is my simplfied understanding of it). 
This to me seems like a much more versatile way of handling the enviornment, since we can easily prompt the agent on sophisticated conditions (maybe even teach the agent natural language as well, and encode our wants and desires as natural language codes?). If we can combine this linguistic intelligence, with the ability to make good decisions, we have made big progress. 


### Are we getting rid of previous methods?

Since sequence modeling does not require any type of dynamic programming, many methods from the theory of Reinforcement learning seem to be useless. 
But don't forget that without having done the work on these models, we could not have discovered the instability issues of deep reinforcement learning, which has a lot of sensitiy on hyperparameters, making it very difficult to predict and make them consistently, and use them in everyday life, which from a practical sense, would be the ultimate goal of such research. 
Sequence modeling seems to have many advantages over DRL, however, its main drawback is its inability (yet) to learn online. 

In general, since language models do not learn online, this by extension means that a decision transformer or any other architecture inspired by language models, cannot learn on the spot, and has to wait for the accumulation of experience to learn any effective policy to solve the environment it is put in. 
Another problem would still remain, which is the lack of experience and data, which would still be a problem with decision transformers, the fact the using real world agents to learn is extremely prohibtive, and sim2real is a hard task as well.


So there are still many unsolved problems about this issue, and hence, it cannot be said that decision transformer can "solve" RL. It is that they are a promising avenue to consider when it comes to the future of reinforcement learning research. 
To add another note, the instability of current DRL algorithms is an issue of hot debate. Many researcher believe that stable deep reinforcement learning algorithms are around the corner, and that this instability is just a temporary hiccup.

Others feel differently about the situation. They believe that the problem is inherent with Deep reinforcement learning, and that it cannot be resolved. 


There are arguments for and against this issue:

1. Deep reinforcement learning is not stable, because it is trying to do something which deep neural networks are bad at, which is supervised learning in reverse. 


In TD learning, we use bootstrapping (a method borrowed from dynamic programming), and the instability comes from the fact that we are using the same value function to query and then update. This creates a vicious self-reliance loop in which we are using ourselves to determine ourselves. 

This isn't such a big problem with tabular reinforcement learning, because in tabular RL, state-values are separately learned and the value of one state does not affect the value of the other directly. 

In DRL, when we update our network, this creates changes in all states, which creates this instability issue, since previously learned states become unlearned again, because their values are changed due to general network weight updates. 

In a decision transformer, the input to the model or agent, is not the state and previous reward, but the sequence of states, actions and rewards, up until this point. And unlike our expectation where the we think that the markov property means that the only information required to make informed decisions is the current state, decision transformers show that this might not be the case, and bigger context length show better performance that k = 1 scenarios where we only see the previous state, action and reward. 


This complicates the picture significantly. To put it into perspective, this means that it is very possible that the MDP framework in its entirety might need a rebranding, and that a more relaxed assumption (like sequence modeling) could replace it. 

Advances in Sequence modeling, especially in context-length related areas, can be a promising part of future RL research using sequence models. This also requires more advances in parts like sim2real, data2real, and such parts, to show veritable and deployable models which are used now, in the market, and create a real difference, by creating positive economic, quality of life, and ... impacts on human life. 

### How to respond to RL hype/anti-hype trains?

One thing to consider as a researcher in modern times, are hype/anti-hype waves that strike a particular area, and the fact that each can create damaging distortions to the perception of the researcher, the consumer market, and the investing campaigns. 

This puts a big responsibility on the shoulder of the expert, to assess and evaluate any claims that are unfounded, to see where there might be tortions to the ground-truth of things, and communicate this effectively with their peers. 

There are some problems with our current state of affairs as well. The platforms and our way of communications on them, have some fundamental effect on the whole hype/anti-hype effect, and some changes are needed to create a better environment that does not propagate distortions and misinformation as widely as it does today. 


Of course that could be another discussion in and of itself. The point is to be cognizant of the complexity of the information which we receive, but the limited amount of assessment we can afford to give it. Being more aware of this fact can help us come up with better solutions in general, as research in general is not a one man job.

Why are some people more likely to believe the hype/anti-hype train?

Shock, fear, and other forms of extreme emotion are just more paid attention to than other more neutral forms of media. This means that content that is more shocking, scary or... will propagate faster and more widely, which makes it seem that its more important, and since many more instances of it are shown, it even seems to be more truthful. 

This is not always the case. the fact of the matter is that we can know that emotionalizing such issues is not always helpful (other than good propagation properties on social media), and we can have a semi-good heuristic (or at least a mental alarm) that, if its sensational, it should be investigated more profoundly, and conclusions from it need to go through more scrutiny. 

This scrutiny could be simple reflection, or speaking with other experts, simulations and experiments, and all in all good scientific practice. In fact, it could argues that such events are opportunities for the researcher to sharpen their scientific swords and practice using the most reliable scientific methods and spread them more in their network of colleagues and interested friends. 

The end goal of reinforcement learning and AI research, in my humble opinion, should be the betterment of human life, and by extension, all life. Misinformation is a great threat to that end, and not taking it seriously can have severe consequences for basically everything. 

Finally, to end this blog post, It's important to notice the effect of outside developments (new methods, technologies and even misinformation) to our own way of life. reminding yourself that your efforts are involved in an interconnected web of influence, and almost no cause and effect chain has linear responses to effort. We can see more clearly that by thinking in an isolated eco-chamber, we run the risk of wasting our time, and the time of others.

