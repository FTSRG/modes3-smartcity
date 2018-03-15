IIoT applications are complex, distributed with many critical components. This motivated our monitoring solution: this way we can further improve the realiability and availability of our systems. Our goal is to supplement design time verification (provided by the Gamma framework) with online monitoring and fault detection.

The result of our work is an end-to-end development platform for critical, distributed IIoT applications supporting the design and correct operation of these complex systems.

# Monitoring solution
One of the biggest problem that we faced during the development of our project was the management of the *Distributed System* that we were aiming to control. The mere number of devices that we had to oversee was more than 3 times the people that could work on them - having an SSH session to each node was just way more tedious than it should have been; not even mentioning the duty of having to monitor each of them individually: These are the experiences what led us to the conclusion that we need to employ some kind of centralized system that could do all the following:

* Display the important details of the devices (CPU type, kernel version, Operating System (and/or distro) name, total RAM and SWAP size, etc.)
* Monitor the system in real time, and display the node's status individually (such as CPU utilization or temperature, RAM  usage, and many more)
    * Graphical representation of historical data
    * Accurate details about the device in real time
    * Complete list of processes (similar to the gnu program `top`)
* Manage the available devices via *one-click SSH*
* Deploy the generated package (pair IP addresses with node names)

## Technologies used
Unfortunately there is (at this time) no complete solution for the above described problem, therefore leaving us with no choice: we had to develop this system ourselves. Of course this could not have been done without the use of many open-source libraries and technologies, such as [WebSSH2](https://github.com/billchurch/WebSSH2), [D3.js](https://d3js.org/), [MDL](https://getmdl.io/) or the emblematic middleware of our project, [OpenSplice DDS](http://www.prismtech.com/vortex/vortex-opensplice).

For all four of the above listed features there is a blogpost coming - stay tuned!