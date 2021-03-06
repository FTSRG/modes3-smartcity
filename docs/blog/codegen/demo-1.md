# Crossroad: a simple demo application

![crossroad](cross.png)

We chose to demonstrate the power of our tool with a crossroad consisting of 2 coordinated and controllable traffic lights. In each direction, the traffic lights are standard 3-phase lights looping through a red-green-yellow-red sequence. As an extra, there is an interrupted mode that may be triggered by the police – in this state, the yellow light is blinking.

## The models

First we created two simple Yakindu models, one for the controller and one for the lights.

### The controller

![controller](controller.png)

### The lights

![lights](lights.png)

## Realization of the distributed system

After creating the models we connected them using Gamma the following way:

![gamma](cross2.png)

Thus we came to a properly working model - the next task was to divide it up into Nodes, so that it can be run on multiple computers communicating through DDS. To do that, we allocated each component to a node using our language. Then, with the help of our code generator we generated the necessary Java files.

## Setting up the demo

The lamps are controlled by two Raspberry PI 2, the control can be arbitrarily managed from a computer or a physical button run by a third PI 2. To write the programs, we used the PI4J Java library as it seemed convenient to use. As our Java classes respresenting the nodes and the state machines have already been generated, the programs themselves were rather simple to write - they have listeners to various gpio events, which raise the appropriate events of the state machine when a signal is detected and vice versa. The only thing left was to transmit the completed files to our PIs. We carried out the transmissions using our deployer, and finally - after lenghty debugging - the lights came alive.

<div style="text-align:center"><iframe width="560" height="315" src="https://www.youtube.com/embed/a5AO5XbRryw" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe></div>


