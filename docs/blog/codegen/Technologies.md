# Code generation from state machines to DDS execution environment

	
Our main goal was to develop a designer tool for critical, distributed real-time applications. Our tool facilitates the creation and distribution of systems running on multiple devices, communicating over DDS. We used various open-source technologies during the development. 

## DDS
DDS is a communication middleware standard that enables scalable, dependable and high-performance data exchange for real-time and embedded systems. It uses a publish-subscribe pattern, which was perfect for our needs. We would like to thank the support of Prismtech, and we are especially grateful to Hans van't Hag (Product manager of Prismtech), who helped us a lot in using DDS. The DDS implementation is available here:
<http://www.prismtech.com/vortex/>
This will be part of the Eclipse Cyclone project:
<https://projects.eclipse.org/proposals/eclipse-cyclone-dds>

## YAKINDU
YAKINDU Statechart Tools is a modelling tool used for development of event-driven systems with the help of state machines. Graphical representation makes the models comprehensible, where simulation and code generation are also possible.

<https://www.itemis.com/en/yakindu/state-machine/>


## Gamma
The Gamma Statechart Composition Framework is a modeling tool that supports the hierarchical composition of statechart components, as well as source code generation and formal verification. It is the most important of the technologies listed above and below, as it is Gamma state machines that run on each node of our distributed systems.

<https://inf.mit.bme.hu/en/gamma/>


## EMF
Eclipse Modeling Framework is an Eclipse-based modeling framework which supports code generation and allows building applications from structured data models. With EMF it was possible to generate Java code from our metamodels easily.

<http://www.eclipse.org/modeling/emf/>


## EGit
EGit is an Eclipse built-in git client. It helped us work on multiple computers at the same time, and then synchronize the updates with one click in the Git perspective.

<http://www.eclipse.org/egit/>


## VIATRA
The VIATRA framework is a useful and efficient tool for finding occurrences of specified patterns in our model items, thus making our models much more manageable.

<https://www.eclipse.org/viatra/>


## Xtext
Xtext is a framework for development of programming languages and domain-specific languages. It was necessary for creating a simple and user-friendly language for describing the way a system is to be distributed. Thanks to that the user only has to type the most important information (e.g. computer name, deployed/executed components), and the Java code will be automatically generated.

<https://www.eclipse.org/Xtext/>


## Sirius
The purpose of this tool is to make modeling painless. It is easy to use, and by visualization the model gets clearer.

<http://www.eclipse.org/sirius/>


## Xtend
With Xtend you can realize template-based text generators (e.g. code, configuration, documentation, etc.). It has a simpler syntax than Java, it is more readable and expressive, and it translates to comprehensible Java source code. 

<https://eclipse.org/xtend/>
