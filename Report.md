# Report with results

## Introduction

We have implemented the Deep Deterministic Policy Gradient (DDPG) algorithm described in [Continuous Control with Deep Reinforcement Learning](https://arxiv.org/pdf/1509.02971.pdf). The implementation has been done in PyTorch, in the Unity environment called [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher). The objective of the agent is to move the double-jointed arm to the moving target location represented by a green sphere.

## Methodology

We used the Deep Deterministic Policy Gradients (DDPG), where the actor and critic has been modeled with a fully connected neural network with RELU activations. To ensure that the output of the actor is bounded between -1 and 1 for each action, we employed the `tanh` function.

### Techniques

To help model convergence, we used the following techniques: 

(1) Experience replay, which breaks the sequential order of one experience and keeps track of a replay buffer of (State, Action, Rewards, Next state, Dones). When the model is trained it samples at random from the replay buffer, which will break the correlations happening from repeating always similar actions plus allows to train multiple times from different events, including rare events.

(2) Fixed Q-Targets, where the target used in the loss function is the same Q function that we are training but with a weighted average of previous learned parameters. This ensures that we don't shift the parameters chasing a constantly moving target. The target network was updated "softly", at every training step, with the function `θ_target = τ*θ_local + (1 - τ)*θ_target`.

(3) To ensure the exploration, we added to each action noise via an Ornstein-Uhlenbeck process, similarly to the paper. 

(4) The state vector was enriched by appending the value of the noise at each time step, so that the agent not only knew about the state but also about the noise, and could act accordingly.

### Hyper parameters

The replay buffer had a size of 100,000 experiences, and returned a batch of 256 experiences at every training step.

With respect to the training parameters, we used:
`gamma = 0.99
tau = 0.001
learning rate critic = 1E-3
learning rate agent = 1E-3
steps before training = 20
number of training steps = 10`

The neural network representing the actor and the critic are composed by 2 layers of 400 and 300 hidden neurons, with RELU activations.

## Results

The model converges to an average over 100 episode higher than 30 after 111 episodes.

and the score plot during training is:

![score plot](link)

Note that the parameters of the actor and critic can be found in the files `models-parameters/agent_reacher.torch` and `models-parameters/critic_reacher.torch`.

# Next steps

There are a few next steps that can be researched:

1. Use a shared representation for the critic and the actor, with different output.
2. Solve the crawler environment. This is currently work in progress.
3. Apply the branching Dueling Q-Network as presented in https://arxiv.org/pdf/1711.08946.pdf

In a personal note, I have enjoyed this project very much, and also the fact that there is so much to learn and try.