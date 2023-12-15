# HoloOcean: An Underwater Robotics Simulator


HoloOcean, an open source underwater simulator, built upon Unreal Engine 4 (UE4). HoloOcean comes equipped with multiagent support, various sensor implementations of common underwater sensors, and simulated communications support.

Due to being built upon UE4, new environments are straightforward to add, enabling easy extensions to be built. Finally, HoloOcean is controlled via a simple python interface, allowing simple installation via pip, and requiring few lines of code to execute simulations.



An effective simulation environment for autonomous underwater vehicles (AUVs) can accelerate the development of algorithms and applications. This is true for all robotics systems, but is particularly necessary for AUVs.


There are many modern day applications of AUVs that can dramatically improve scientific knowledge, quality of life, and safety. These applications include inspection of marine infrastructure such as dams, ship hulls, and communication lines, as well as exploration of oceans that can lead to discoveries in the fields of geology, marine biology, and medicine. However, all these applications require complex algorithms to be designed and tested, which can be costly and unreasonably challenging without a virtual environment on which to first develop them.


We present HoloOcean, an open source underwater simulator. It is built upon the reinforcement learning simulator Holodeck [1] and the capabilities of Unreal Engine 4 (UE4) [2]. UE4 in particular provides accurate simulation dynamics, high-fidelity imagery, a mature environment construction editor, and a C++ interface to add custom sensors, agents, etc. Specifically, HoloOcean has the following features:
1) A simple python interface, allowing for quick installation and effortless use.
2) Ease of adding new environments. UE4 is a well documented game building engine with many marine and underwater assets already made.
3) A novel and efficient imaging sonar implementation built upon an octree structure that results in realistic sonar imagery


Full support for multi-agent missions, including implemented acoustic and optical modem sensors for realistic cooperative simulations.




Creating a realistic underwater simulator requires many features to be useful for algorithm development including, but not limited to, multi-agent support; realistic sensor simulations; accurate underwater dynamics; ease of use; integration with existing systems; and, preferably, open source [3].

Heavy dependencies, such as Robot Operating System (ROS) [4], can make installation and use cumbersome, particularly when the simulator is only being used for data generation.


In this work, we propose HoloOcean that builds on Holodeck and augments it with accurate underwater dynamics, multi-agent communications, a realistic imaging sonar implementation, and other underwater sensor models.


HoloOcean’s python interface is modeled after OpenAI Gym [25]. This means controlling the robots can be done in a few lines of code

Configuring missions is easily done by defining a custom configuration in json format. Note, the configuration takes in a possible array of agents, as well as an array of sensors objects for each agent. This json, either loaded from a file or inserted directly in the python code, is passed to HoloOcean for mission creation. This allows for painless customization of missions, with any variation of sensors and agents as required.

As one of the most popular game engines, UE4 has a large marketplace full of environments and meshes for purchase by independent users at reasonable prices. This makes rapid development of high quality environments possible. In addition, UE4 has great documentation and a large community behind it, resulting in an abundance of online resources for new users, significantly lessening the initial learning curve.



## Other simulators

UUV Simulator [5] is one of the more mature options, built upon the popular open source robotics simulator Gazebo [6]. It has accurate modeling of hydrostatic and hydrodynamic effects, multi-agent support, a preliminary sonar implementation [7], and is easily configurable. However, it requires the installation of ROS, lacks multi-agent communications, and does not appear to be actively maintained.
The UUV Simulator sonar model leverages a simulated depth camera and GPU computations [7, 13] that appears promising, but has drawbacks due to the depth camera field of view not matching that of a true imaging sonar.


UWSim [8] is built on OpenSceneGraph and osgOcean [9]. It also has multi-agent support and is open source, but depends on ROS, is difficult to configure, is not being actively maintained, and has a sonar model that is more akin to a LiDAR.


Built upon USARSim [10], MarineSIM [11] is another simulator for underwater navigation, but is not open source, which limits the possibility for future development. Other work in USARSim includes an implementation of acoustic multi-agent communications [12], but lacks other common underwater sensors.


Holodeck [1] is an open source reinforcement learning and robotics simulator. It’s built upon UE4 [2], providing it with high-fidelity imagery, accurate dynamics built upon the PhysX physics engine [16], and a mature community with many environment assets already made. Further, Holodeck has a simple python interface, allowing for easy installation and use on a variety of systems.
