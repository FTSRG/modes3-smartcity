[![](http://img.youtube.com/vi/PqeAt9e4j5s/0.jpg)](http://www.youtube.com/watch?v=PqeAt9e4j5s "Scheduler program Test")

An intelligent railway system necessitates not only sensor data, but also a management system, which is responsible for scheduling and controlling the trains. In former years (and in a former IoT challenge), the physical layout, and a safety logic was developed by the research group. In this project we aimed at extending former developments with an intelligent component to support the smart operation of the system.

### Scheduling trains in a smart way

As the project grew and grew hardware-wise, the group realised that in order to bring it all together, our solution needs logic: a sophisticated software that utilizes the (almost) endless possibilities of the physical system. This is actually what IoT is about, so we started to evaluate the possibilities. In the following, we will overview the main controller part of the systems, which is responsible for controlling and scheduling the trains according to the high-level requirements. 

### So how did things start?

For our newly recruited, open-minded (soon-to-be) software engineer team this was a dream come true. The project felt like the hotbed of cutting edge, fresh-out-of-the-oven technologies supported by this huge interconnected system of various sensors, IoT gadgets and microprocessors – to make it all work.

We aimed to develop a control and monitoring system, that is capable of creating train schedules with a great deal of options for optimalisation techniques regarding travel time, covered distance and else. Being consistent with the FTSRG name (Fault Tolerant Systems Research Group), the other main aspect was to make it responsive to changes in the environment, such as weather conditions or failure of a track segment (e.g. an impediment caused by a fallen tree branch).
We have evaluated multiple approaches such as the live-model approach, and traditional database technologies. While using live models and graph queries at runtime seemed to be an interesting direction, we finally decided to use another approach.
We spent a few days building a solid data model and then we worked out an instance model. And this was the point where things started to get a little bit tricky. Finding an efficient way to use live models for managing our system and also persisting the information (which is extremely important in the case of schedules) is not trivial. In addition, the immature technological background also made our work difficult: we decided to use traditional database techniques combined with smart technologies.

I really do hope, that later in this project's lifecycle, we will have the time (and courage) to go on a battle with the complex technology (behind working with live models) again and switch the current solution to one that draws on the endless possibilities of the VIATRA Framework – one of the most interesting and promising technologies that we have tried out during this process.

Eventually, we arrived at the combination of many traditional techniques and we focused on how to make the controller intelligent (in a traditional software environment). Our solution is based on calculating the optimal route between two arbitrary stations using Dijkstra’s algorithm. The controller then communicates through the MQTT protocol, which receives information, and sends instructions to the switches based on real-time data about the train’s position, collected by sensors on the tracks.

The final product of our work is easily extensible and has an elegant graphical user interface as well. Given two stations, it will calculate the route between them, following which the user can track the train in motion on a map of our railway system.
