# Development of a Three-Dimensional Simulator for Integrated Testing of Path-Planners and Controllers for Autonomous Underwater Vehicles

## Abstract

Autonomous underwater vehicles (AUVs) operating in deep sea and littoral environments have diverse applications
ranging from marine biology exploration and search for plane crash sites to ship-hull inspection and border patrol.

The dynamical behavior of the AUV is modeled using the equations of motion that incorporate the effects of
external forces (e.g., buoyancy, gravity, hydrodynamic drag, centripetal force, Coriolis force, etc.), thrust forces, and inertial
forces acting on the AUV.

The equations of motion are translated into a state space formulation and the S-function feature of the
Simulink and MATLAB scripts are used to evolve the state trajectories from initial conditions.

An underwater pipe-line inspection task carried out by the AUV is demonstrated in a simulated environment

## Introduction

Autonomous underwater vehicles (AUVs) operating in deep sea and littoral environments have diverse applications
including marine biology exploration [1], ocean environment monitoring [2], search for plane crash sites [3], inspection of
ship-hulls [4] and pipelines [5], harbor patrolling [6], etc.
Depending on the mission, the distances traveled by the AUVs
can drastically vary anywhere from 500 meters (e.g., in a ship hull inspection task) to thousands of kilometers (e.g., in an ocean
environment monitoring task).

Challenging conditions of the deep sea (e.g., limited communication and refueling/recharging resources, strong disturbances due to ocean currents, etc.)
make it highly difficult to accomplish the tasks of feasibility testing, field trials, and deployment.

Owing to these reasons, the AUV system integration effort can benefit from testing the related algorithms
and techniques in a simulated environment before implementation in a physical test bed.
For example, an AUV simulator allows preliminary testing of various autonomy modules, configurations, and mission scenarios without the fear
of losing the physical AUV in the deep sea during the development phase. Difficulty in reaching the test sites and
conducting experimental trials can also be avoided by using an AUV simulator.


## Related work

Many control strategies have been developed to stabilize the AUV in the presence of unknown perturbations and modeling
uncertainties [15]. Control is required at three levels of autonomy including stabilization to a point, path following, and
trajectory tracking [16].
The AUV control system is traditionally based on a proportional–integral–derivative (PID) controller.
PID systems can be divided into proportional–integral (PI) or proportional–derivative (PD) systems, depending on whether
the vehicle is inertia sensitive [17].

Different control methods with adaptive properties have been developed to stabilize an underwater vehicle in the
presence of external disturbances [18-20]. For the path following problem, a controller based on Lyapunov theory and
Backstepping technique was designed by Lapierre et al. [21]. A robust controller based on sliding modes technique is presented
by Elmokadem et al. [22], which can ensure finite time convergence of the AUV to the desired path even in the presence
of bounded perturbations. However, both works validated the proposed controller only via simulations.

Sahu and Subudhi [23] designed an adaptable controller capable of estimating parametric
perturbations and uncertainties. Li et al. [24] designed an adaptive fuzzy PID controller to follow straight lines that are
commonly used in underwater reconnaissance missions. Guerrero et al., (2018) [15] designed a robust algorithm based
on the second order sliding mode technique with a self-adjusting gain proposed by Gonzalez et al. [25], which is applied to a
Linear Time Invariant (LTI) system. The authors designed a trajectory tracking controller based
on the Generalized SuperTwisting Algorithm (GSTA) with self-adjusting gains for a MIMO system.


### Workspace Dimension of the Operating Environment

The dynamics of underwater vehicles involve nonlinear and coupled hydrodynamic parameters, making it difficult to
implement a controller for a six DOF AUV operating in a three dimensional space. Therefore, many controller designs
considered a simplified 3 DOF AUV model operating in a two dimensional space. Typically, the roll DOF in most underwater
vehicle is passively stable.
Neglecting the stable roll DOF and considering the vehicle symmetry, the AUV model can be
simplified into two decoupled subsystems in the longitudinal (vertical) and lateral (horizontal) planes [26].

### AUV Simulators

#### **Offline**
simulators are mainly intended for design and preliminary testing using a synthetic AUV before
implementation in a physical AUV. Also, there is no interaction between the simulator and the physical AUV. In some cases,
the simulation load is so heavy that one second of simulation last for more than one second in the reality. In other cases, one
second of simulation does not last for one second of the reality. In both cases, the temporal properties of the implemented
algorithms are not considered [29].
There also exist more high-fidelity three-dimensional dynamic simulators for AUVs such as SUBSIM and DEEPWORKS [32].

#### **Online**
simulators allow real-time interaction with a physical AUV, ensuring time consistency between the simulated and the real
time. Hence, the time properties of the simulated algorithm are taken into account within the simulation.
NEPTUNE is a multi vehicle, real-time, graphical simulator based on OpenGL that allows hardware in the loop simulations.
Although there exist several commercial AUV simulators like UWSim, MORSE, and Gazebo, it may be more appropriate to build a simulator
customized for individual research goals [28].
