# Deep Reinforcement Learning Nanodegree - Project 3: Competition via DDPG

## Introduction
This project is part of the Udacity course I took on Deep Reinforcement Learning (DRL).

Goal of the project is training two agents to compete against each other in a tennis-like game through a suitable DRL algorithm ([DDPG](https://arxiv.org/abs/1509.02971)). 
The agents are trained in an environment simulated through the [Unity ML-Agents Toolkit](https://github.com/Unity-Technologies/ml-agents)

## The environment

The environment simulates the physics of two rackets bouncing a ball over a net. Each racket is controlled by an agent. If one of the agents hits the ball over the net, it's given a reward of +0.1; if it lets the ball hit the ground or hits the ball out of bounds, it's given a negative reward (i.e. a penalty) of -0.01. Thus, the reward assignement expresses the goal of keeping the ball in play.

The environment generates 'observations' for the agents (position and velocities of rackets and ball) which in turn react with 'actions' over the rackets (moves and 'jumps').

In details, the observation for one agent consists of position and velocity (both are bi-dimensional variables) of ball and racket sampled at three consecutive time steps; hence, we have 2 variables x 2 dimensions x 2 objects (racket and ball) x 3 time steps = 24 continuous variables for observation. Two actions can be actuated by each agent: moving toward/away from the net and jumping. Every action must be a number between -1 and 1.  [//]: # (check this)

The task is episodic, and in order to solve the environment, the *winner* agent must get an average score of +0.5 over 100 consecutive episodes.

Since each agent receives own observations and rewards and given the simmetry of the game, both agents can be trained as one only agent. In other words, they can be considered as one self-playing agent. Therefore, the experience gathered by both of them is collected in a common memory buffer and then sampled to train a common model. 

As by DDPG, the model consists of two deep neural networks: one, the 'actor', is trained to estimate the *best* action to pick in a certain state while the other, the critic, is trained to estimate the value (future expected rewards) of the picked action; in turn, the action-value is used to train the actor in the next estimations of the *best* action in any given state. Two additional clones of the models (target models) slowly track the previous ones (their parameters are slowly updated in accordance) and are exclusively employed on training to improve the convergence properties of the algorithm.[//]: # (check this)

## The solution
Once trained, the agent can be seen in action in the Unity environment.   
![image](https://user-images.githubusercontent.com/53077127/140544361-daaf4925-fa6b-4408-8119-19cf42f339c6.png)
[Click here to see the agent in action!](https://user-images.githubusercontent.com/53077127/140923741-4a67c160-ea6f-4623-b1b3-fdb3ab76b7fa.mp4)


 [//]: # (in installation try to expand instructions)
## Installation
Follow the instructions in the [DRLND GitHub repository](https://github.com/udacity/deep-reinforcement-learning#dependencies) to set up your Python environment. These instructions can be found in README.md at the root of the repository. You will install PyTorch, the ML-Agents toolkit, and a few more Python packages required to run the project.

Note: the project is provided with pre-built Unity environemnt for Windows 10 (64 bit). Other operating systems need custom environment.

## Try it for yourself!
Open the Jupyter notebook: Tennis.ipynb 
Run steps from 1 to 4 to train an agent.  
Run step 5 to watch the agents play; a pre-trained version is also available.    
