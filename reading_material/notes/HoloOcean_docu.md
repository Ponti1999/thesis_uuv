# HoloOcean Documentation


## Installation

HoloOcean is installed in two portions: a client python library (holoocean) is installed first, which then downloads world packages. The python portion is very small, while the world packages (“binaries”) can be several gigabytes.


A minimal HoloOcean usage example is below:
```python
import holoocean
import numpy as np

env = holoocean.make("PierHarbor-Hovering")

# The hovering AUV takes a command for each thruster
command = np.array([10,10,10,10,0,0,0,0])

for _ in range(180):
   state = env.step(command)
```
You pass the name of a scenario into holoocean.make


You can access data from a specific sensor with the state dictionary:
dvl = state["DVLSensor"]



## Custom scenario configuration

Custom Scenario Configurations
HoloOcean worlds are meant to be configurable by changing out the scenario. There are some scenarios included with HoloOcean packages distributed as .json files, but HoloOcean is intended to be used with user-created scenarios as well.

These can be created using a dictionary in a Python script or by creating a .json file. Both methods follow the same format, see Scenario File Format


## Scenarios

A scenario tells HoloOcean which world to load, which agents to place in the world, and which sensors they need.

It defines:
- Which world to load
- Agent Definitions
    - What type of agent they are
    - Where they are
    - What sensors they have


You can think of scenarios like a map or gametype variant from Halo: the world or map itself doesn’t change, but the things in the world and your objective can change.

Scenarios allow the same world to be used for many different purposes, and allows you to extend and customize the scenarios we provide to suit your needs without repackaging the engine.

When you call holoocean.make() to create an environment, you pass in the name of a scenario, eg holoocean.make("Pier-Hovering"). This tells HoloOcean which world to load and where to place agents.

Agent Types:
- HoveringAUV
- TorpedoAUV
- TurtleAgent
- UavAgent

## Publishing Sensor Data
Currently, HoloOcean supports publishing data to LCM (with a potential ROS wrapper being considered). All this config happens in the scenario file. We’ll outline what this takes here.

LCM publishes data to a certain medium, called the provider. This can be locally, over the network, a log file, etc. This can be specified in the header of the scenario file. See _here for options on this. If no provider is specified, HoloOcean uses the default LCM udqm.
