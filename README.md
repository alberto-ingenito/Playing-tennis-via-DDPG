# Deep Reinforcement Learning Nanodegree - Project 3: Competition via DDPG

## Introduction
This project is the third of the three assigned in the Udacity course I followed about Deep Reinforcement Learning.  

Aim of the project is to train two agents to compete against each other in a tennis-like game by using a suitable deep reinforcement-learning technique ([DDPG](https://arxiv.org/abs/1509.02971)). 

## The environment

The environment is populated by two agents which control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.

The observation space (or state space) consists of 4 bi-dimensional variables corresponding to the position and velocity of the ball and racket sampled at three consecutive time instants; hence, we have 4x2x2x3 = 24 variables for observation. Each agent receives its own, local observation. Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping. Every action must be a number between -1 and 1.

The task is episodic, and in order to solve the environment, the *winner* agent must get an average score of +0.5 over 100 consecutive episodes (in each episode, the winner score is obviously given by the maximum score over both agents).

Since each agent receives local observations and own rewards and since the game is simmetrical, both agents can be trained as one only agent. In other words, the two competing agents can be considered as one self-playing agent. Therefore, the experience gathered by both of them is collected in a common memory buffer and then sampled to train one common model. 
As by DDPG, the model consists of two deep neural networks: one, the 'actor', trained to estimate the *best* action to pick in a certain state, and an other one, the critic, trained to estimate the value (future expected rewards) of the action suggested by the actor; in turn, the value is used to train the actor in the estimation of the *best* action in the given state. Two additional clones of the models (target models) slowly track the previous ones (the parameters are slightly shifted in their direction) and are exclusively employed in the training phase to improve convergence properties of the algorithm.

## The solution
Once trained, the agent can be seen in action in the Unity environment.    
#[Click here to take a #look!](https://user-images.githubusercontent.com/53077127/138491669-c4abcc72-b5bb-44da-90fc-d1b8786626cd.mp4)

## Installation
Follow the instructions in the [DRLND GitHub repository](https://github.com/udacity/deep-reinforcement-learning#dependencies) to set up your Python environment. These instructions can be found in README.md at the root of the repository. You will install PyTorch, the ML-Agents toolkit, and a few more Python packages required to run the project.

Note: the project is provided with pre-built Unity environemnt for Windows 10 (64 bit). Other operating systems need custom environment.

## Try it for yourselft!
Open the Jupyter notebook: Continuous_Control.ipynb 
Run steps from 1 to 4 to train an agent.  
Run step 5 if you want to watch the agent play. If you don't train it, a pre-trained version is available.    
