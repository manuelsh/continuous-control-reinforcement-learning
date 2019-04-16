# Banana Navigator

## Introduction

This repository contains an implementation of the Deep Deterministic Policy Gradient (DDPG) algorithm described in [Continuous Control with Deep Reinforcement Learning](https://arxiv.org/pdf/1509.02971.pdf). The implementation has been done in PyTorch, in the Unity environment called [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher). The objective of the agent is to move the double-jointed arm to the moving target location represented by a green sphere.

![reacher](link)

We will use a custom version of the environment with 20 arms. The agent will control each arm rigid body with the goal of moving and keeping the hand in the moving target. See more information in the section **Environment details**.

The agent is implemented and trained in the notebook `continuous-control-reacher.ipynb`.

To see a comprehensive report on the results, use the following [link]( LINK ).


## Environment details

The agent will interact with a version of the [Reacher Unity environment](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher).

### Rewards

A reward of +0.1 is provided for eacg step the agent's hand is in the target location.


### State space

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of each arm.

### Action space

Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

## Goal of the task

In order to solve the environment, the agent must get an average score of +30 over 100 consecutive episodes, averaging over the 20 arms.

# Requirements installation

To be able to run the notebooks, one needs to prepare the environment and download the Unity environment.

## Preparing the environment

As described in the [Udacity github repo](https://github.com/udacity/deep-reinforcement-learning#dependencies), to set up your python environment, follow the instructions below.

1. Create (and activate) a new environment with Python 3.6.

	- __Linux__ or __Mac__: 
	```bash
	conda create --name drlnd python=3.6
	source activate drlnd
	```
	- __Windows__: 
	```bash
	conda create --name drlnd python=3.6 
	activate drlnd
	```
	
2. Follow the instructions in [this repository](https://github.com/openai/gym) to perform a minimal install of OpenAI gym.  
	- Next, install the **classic control** environment group by following the instructions [here](https://github.com/openai/gym#classic-control).
	- Then, install the **box2d** environment group by following the instructions [here](https://github.com/openai/gym#box2d).
	
3. Clone the repository (if you haven't already!), and navigate to the `python/` folder.  Then, install several dependencies.
```bash
git clone https://github.com/udacity/deep-reinforcement-learning.git
cd deep-reinforcement-learning/python
pip install .
```

4. Create an [IPython kernel](http://ipython.readthedocs.io/en/stable/install/kernel_install.html) for the `drlnd` environment.  
```bash
python -m ipykernel install --user --name drlnd --display-name "drlnd"
```

5. Before running code in a notebook, change the kernel to match the `drlnd` environment by using the drop-down `Kernel` menu. 

## Donwload the Unity Environment

Select and download the environment that matches your operating system:

Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)
Then, place the file in the `p2_continuous-control/` folder in the DRLND GitHub repository, and unzip (or decompress) the file.

(For Windows users) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

(For AWS) If you'd like to train the agent on AWS (and have not enabled a virtual screen), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux_NoVis.zip) to obtain the "headless" version of the environment. You will not be able to watch the agent without enabling a virtual screen, but you will be able to train the agent. (To watch the agent, you should follow the instructions to enable a virtual screen, and then download the environment for the Linux operating system above.)

# Instructions to train the agent

Once your environment is set-up, just run the notebook `continuous-control-reacher.ipynb`.

