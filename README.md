# SPACESHIP EVOLUTIONARY AGENT

## Overview 

This repository aims to describe the process of building a game agent with no framework in C#, and present the results. A game has been developed with Unity as a testing ground for the agent. A neural network have been built in pure C#, and evolutionary methods have been used to train the agent. The differents results according to the parameters of the training method and of the neural network have been compared. 

## The game

The player controls a spaceship that must avoid obstacles to reach the highest score possible. The spaceship can only moves on the x axis, and has a fixed speed.

## The agent

The agent has the same controls as a human player : left, right, idle. To acknowledge its environment, a set of rays are casted from the spaceship so the agent can spot the borders and the obstacles.  

## Neural network

The "brain" of the agent is a neural network built from scratch in C#. This network is a set of C# arrays to store the neurons, weights and biases values. The inputs are the raycast values (distance to an obstacle of a ray casted from the spaceship). The output of the network represents the 3 possibles moves the payer can do : LEFT, IDLE, RIGHT. (See neuralNetwork.cs)

## Evolutionary methods

To train the agent, a genetic algorithm has been developped. N randomly-initialized agents (random weights and biases) are created and play the game simultaneously. M best are "selected" which means that their neural network state is saved. These bests are "cloned", their neural network is duplicated X times, R randomly-initialized agents are added, to create the new generation (M * X + R individuals). All clones are then "mutated" (their neural network weights and biases are randomly (A) and slightly (B) modified (A is the probability that a weight or a bias will change, B is the intensity of a modification if a weight or bias changes). Over several generations, the individuals are supposed to reach a better score. N, M, R, X, A, B are some parameters that must be ajusted. As the agents are getting better, the intensity of the mutation are reduced to ajust more precisely the parameters of the neural network. 

## Testing the game

To execute the algorithm just execute spaceship_game.exe and you will be able to visualize the agent learning how to play the game. You should see the individuals start to play better after few generations.

## Results

This agent shows very encouraging results. The learning curve is really fast and the agent reach a very good score. However, the agent didn't "broke" the game and could be improved. Let's see the evolution of the score according to differents parameters :

### Without raycasts, 8 neurons in hidden layer, no intensity reduction

![alt text](https://github.com/JulienRZ-Dev/spaceship-evolutionnary-agent/blob/master/plots/1.png?raw=true)

### With raycasts, 8 neurons in hidden layer, no intensity reduction

![alt text](https://github.com/JulienRZ-Dev/spaceship-evolutionnary-agent/blob/master/plots/2.png?raw=true)

### With raycasts, 20 neurons in hidden layer, 10% intensity reduction every 50 generation

![alt text](https://github.com/JulienRZ-Dev/spaceship-evolutionnary-agent/blob/master/plots/3.png?raw=true)


## Authors

Julien Rouzot (rouzot@etud.insa-toulouse.fr; julien.rouzot@live.fr)
Gwenaël Ebersohl (ebersohl@insa-toulouse.fr; gwenael.ebersohl@gmail.com)
