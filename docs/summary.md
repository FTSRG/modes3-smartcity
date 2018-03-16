# MoDeS3 - The Smart City

We continued the MoDeS3 project (which won third place in 2016) and we built a smart city on top of the physical architecture.
We have used the MoDeS3 demonstrator as a case-study for our:

- end-to-end data collection, management and data analysis framework
- developer tool, which supports the design and implementation of distributed, real-time, critical applications

We have enhanced the MoDeS3 demonstrator to serve as a smart city platform consisting of a smart transportation system with stations
and other functionalities, such as street-lighting.  We also integrated solar panels as an additional 
energy source and underline the importance of green approaches in future smart cities.

The smart city platform is operated by our management framework and it has various features, such as:

* Transportation system reacts to the (changes of the) environmental conditions. Various sensors on open-source hardware 
observe the conditions on the trains, monitor the temperature and light conditions, measure the vibration of the tracks. 
The information gained from the physical observations is used for various purposes: 

 * Detect anomalies such as accidents, speed limit violations.
 * Report dangerous environmental conditions, such as ice or overheated tracks.
 * Control the system, such as we can switch on the lamps in case of darkness.
 
* Transportation system manages the trains and the tasks intelligently. It makes decision according to the conditions and the system
tries to optimize its operation. 
 
* We have also prepared a prototype of a signalling system with our developer tool to illustrate its applicability in this critical setting.


#	Description of the project
On top of the physical setting, we have designed and implemented sensor packages containing the most essential sensors. The included sensors are the following:

* Vibration sensor to detect problems of the transportation and possible accidents. In addition, these sensors can provide information
regarding the usage of the tracks.
* Temperature sensor is responsible to measure the temperature near/on the tracks. These sensors are especially useful in the "wild", as in our demonstrator,
neither cold, nor too hot temperatures can not occur.
* Speed sensors are used to measure the speed of the trains. 
* Camera sensor gathers visual information especially from the crossing: computer vision is used to recognize the trains and 
check if the schedule is correctly executed. In addition, camera-based observation system can detect objects (with a neural network based recognition system) in the crossing 
and it can transmit this information to the controller.

The physical information is processed on open-source hardware in the Edge: Raspberry Pi microcomputers run the open-source Kura
component and gathers the information from the sensors. In addition, Kura provides management capabilities and we also implemented local reactions in this level.
An example for that: the street-lights are switched on by the local components as we can not ensure that the cloud is always available.
The main rule of thumb is to deploy critical logic at this level, which is needed instantly.

![Collecting and analyzing IoT data](technologies.png)

The gathered information is sent towards an Eclipse Kapua component. We can manage the local components running Kura and Kapua also helps 
gathering the data. Data is also filtered at this level: we can decide the data which is worth sending to the cloud intelligence.
As we mentioned in the former posts, we integrated together various components in the cloud to provide:

 * Stream processing capabilities to react the changes of the environment instantaneously.
 * Data analytics services to use predictive analysis techniques to optimize the operation of the system.

You can find more information of the IoT data processing solution here:
<http://modes3-smartcity.readthedocs.io/en/latest/blog/iot/architecture/>

The aforementioned components are connected to an intelligent control system, which is responsible to:

* manage the train schedule
* control the trains and the transportation between the stations
* react to the environment and reorganize the schedule if necessary

You can find a small demo of the scheduler component driving the trains from one station to another: 
<div style="text-align:center"><iframe width="560" height="315" src="https://www.youtube.com/embed/PqeAt9e4j5s" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe></div>


Beside the huge software stack developed by our team to control a smart city, we also developed a design tool
based on the open-source Yakindu statechart tools and its code generator. We used the Gamma framework, which extends Yakindu
with precise composition semantics, formal verification and test generation. Our tool extends the capabilities of the Yakindu and Gamma tools as:

 * we provide a deployment language
 * a DDS-based runtime
 * a code generator (built using open-source technologies).

![Overview of our approach](overview_of_the_approach.png)

These technologies constitute a framework to support the development of critical, real-time, distributed IIoT applications.

<div style="text-align:center"><iframe width="560" height="315" src="https://www.youtube.com/embed/a5AO5XbRryw" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe></div>


#	Open technology and standards that were used
We used various open-source hardware components: Raspberry Pi and BeagleBone Black microcomputers.
We integrated in the IoT data collector and analysis framework various open-source software components:

 * Eclipse Kura
 * Eclipse Kapua
 * Eclipse Paho
 * Eclipse Mosquitto

We also had to integrate data analytics technologies to prepare for the huge amount of real-life data (coming from hopefully future 
real-life, industrial applications):

* Apache Spark
* Apache Hadoop
* Apache Ambari
* Apache Zeppelin
* Hortonworks solutions

We have used Eclipse open-source technologies in our design tool:

* EMF, VIATRA, VIATRA-Query
* Yakindu statecharts
* Xtext, Xtend

We also integrated the DDS implementation potentially appearing in the Eclipse Cyclone project in the near future. We would like to 
thank Prismtech for the provided licenses and support.

The monitoring of the distributed DDS-based system also uses various open-source technologies such as jquery, dotty, php, DDS and many others.

#	Applicability of a solution to a specific industry
Application was the main motivation during our work, so we tried to apply all the techniques and technologies 
in our MoDeS3 demonstrator system and extend its capabilities. We believe that in this project we can only demonstrate the working of our technology
in the demonstrator, but the used approaches would scale even to the size of real smart city environments. 
Our technology decisions were always motivated to find technologies which could even by used by the industry.
We took the first steps towards a smart city built fully from open-source technologies!
