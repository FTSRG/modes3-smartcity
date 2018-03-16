Internet revolutionized how people interact, communicate and what they do. However, in the era of Industrial IoT, a growing demand appeared for real-time, reliable and secure communication. 
New computing paradigms, such as Fog and Edge computing necessitate technologies and methodologies to handle complex networks and strict requirements.
Data Distribution Service (DDS) seems to be the solution for the problems of IIoT, which motivated our teem to choose DDS also as a communication midleware in our project. 

# Our choice of DDS implementation: Vortex OpenSplice DDS

After we had decided to use DDS for the communication between the components of our distributed system that we would like to manage, we had to choose the implementation of this middleware. Even though the standard is established by the Object Management Group (OMG) quite thoroughly, the available open source implementations (such as OpenDDS) lack not only extra features, but some core functionalities as well, and outright refuse to work sometimes. Therefore we had to find an alternative - luckily the OpenSplice DDS (from Vortex) ticked all the right boxes on our checklist - proven to be reliable, compatible with Java and C++ (and even C, if we ever need something even more mission critical, and would need the speed and timing capabilities of a C program), fault tolerant to great extents, but it was missing a serious 'feature': it is as proprietary as proprietary goes. This will change in the very near future though - Vortex [decided](http://www.prismtech.com/news/prismtech-moves-market-leading-proven-dds-solution-open-source-eclipse-cyclone) to open its sources as of late March 2018, making this the best choice for us.
 
## Introducing an abstraction layer to OpenSplice DDS

Even though this DDS implementation is the optimal library for our needs, it is very far from perfect (as it is to be expected from a software this versatile). The documentation is sparse, the available materials are not at all straightforward, and overall the feeling of it is that it *can* do everything we ask for (and even more), but it *will not* show you how to achieve that.
In order to overcome this kind-of serious issue our teem has developed a library (to serve as an abstraction layer) that sits on top of the OpenSplice libraries and does all the dirty work - initializes the runtime environment, loads the classes, creates the domain participants and so on. Of course, as it is only an abstraction (and we're not stating that we would've created a better solution for the problem than Vortex itself) it can do way less than what the OpenSplice DDS is capable of, but for what we need it, it is perfect: 

* Creating `Topics` in `Partitions` of the `GDS` (Global Data Space)
* `Subscribing` to these `Topics` via `Listeners` (and of course via `DataReader` instances)
* `Publishing` Events to these `Topics` via a `DataWriter` instance
    * `Events` consist of a name and a list of parameters
* Handling `QoS`s 

## Using our library
Unfortunately at this time we cannot redistribute the binary packages of the Vortex OpenSplice DDS that we got as part of the Evaluation License. However, the introduced library works just as well with the Community Edition releases therefore providing an exceptionally easy-to-use way of using DDS in your application as well - see the [technical documentation](http://modes3-smartcity.readthedocs.io/en/latest/technical_documentation/dds/dds_java_lib/) for more details and a user guide! 
We have successfully used it as a means of getting Events in complex statemachines go through our LAN (and even the University's quite big network!), so it is definitely functional and reliable - maybe this is what you need for your next project.
We hope that our contribution combined with the design tool (also introduced in an other blogpost) will serve the needs of the designers of future IIoT applications. 
