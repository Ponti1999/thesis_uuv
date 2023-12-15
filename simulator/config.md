# Page of the UWSim

The currently discussed topic [can be found here](https://www.irs.uji.es/uwsim/wiki/index.php?title=First_steps:_Dynamic_simulation) </br>
If you know any required parameter of the following chapter please add it to the [parameter list](#parameters) </br>

Thank you for your help!

</br>

# Dynamics model parameters

- num_actuators:
  - The number of actuators (like thrusters or propellers) on the vehicle. Actuators are the components that provide movement and control

- period:
  - The time period (in seconds) for the dynamics simulation. This parameter likely controls the frequency at which the dynamics calculations are - pdated

- uwsim_period:
  - Similar to period, this might specifically refer to the update period for the dynamics within the UWSim environment
  - The configuration file you provided refers to the period of the dynamics model in seconds

- ctf and ctb:
  - These are the coefficients related to the vehicle's thrusters. "ctf" stand for "Coefficient of Thrust Forward" and - ctb" for "Coefficient of Thrust Backward", which are used in the thrust calculations for forward and reverse motion
  - Thrust coefficient of the forward direction
  - Thrust coefficient of the backward direction

- actuators_tau:
  - The time constant (tau) for the vehicle's actuators, used in the first-order dynamic model of the actuators. This value affects how - quickly the actuators respond to control inputs
  - Parameter refers to the actuator tau for the first-order actuator dynamic model

- actuators_maxsat and actuators_minsat:
  - These are saturation limits for the actuators. "maxsat" is the maximum saturation limit, and - minsat" is the minimum. These limits prevent the actuator input values from going beyond specified bounds

- actuators_gain:
  - Gain factors for the actuators. These values are used to scale the input to the actuators, affecting their output force or torque

- dzv, dv, dh:
  - These are likely dimensional parameters of the vehicle. They might represent distances or offsets in the - vehicle's structure, relevant to the placement of sensors or actuators
  - dzv refers to the vertical distance between the center of gravity and the center of buoyancy
  - dv refers to the volume of the vehicle
  - dh refers to the height of the vehicle

- density:
  - Refers to the density of the vehicle

- tensor:
  - This could refer to the inertia tensor of the vehicle, which is a matrix that describes how the mass of the vehicle is distributed in space. - it's crucial for calculating rotational dynamics
  - Refers to the moment of inertia tensor of the vehicle

- damping and quadratic_damping:
  - These parameters are related to the damping forces acting on the vehicle. Damping is a force that opposes motion and is usually proportional to the velocity (linear damping) or the square of the velocity (quadratic damping)
  - damping refers to the linear damping coefficients of the vehicle
  - quadratic_damping refers to the quadratic damping coefficients of the vehicle

- allocation_matrix:
  - A matrix used to allocate control inputs (like thrust commands) to the various actuators. It maps high-level control actions to the  pecific actions of each actuator

- initial_pose and initial_velocity:
  - The starting position (pose) and velocity of the vehicle when the simulation begins

- Mrb:
  - Refers to the rigid body mass matrix of the vehicle
  - This parameter likely represents the rigid-body mass matrix of the vehicle. In underwater vehicle dynamics, the rigid-body mass matrix includes the actual mass of the vehicle and the added mass due to the displaced water. This matrix is used in the dynamics equations to model how the vehicle's mass and inertia affect its motion
    - The matrix is usually a 6x6 matrix, accounting for linear and angular components in three dimensions (X, Y, Z, Roll, Pitch, Yaw)
    - The diagonal elements typically represent the mass and moments of inertia, while the off-diagonal elements can represent the cross-inertial terms

- Ma:
  - Refers to the added mass matrix of the vehicle
  - This parameter likely represents the added mass matrix. The added mass is a concept in fluid dynamics and naval architecture that describes the additional inertia that a body experiences when it is accelerating through a fluid. For an underwater vehicle, the added mass accounts for the water mass that is accelerated along with the vehicle as it moves
    - Similar to the rigid-body mass matrix, the added mass matrix is also a 6x6 matrix
    - It captures the added resistance experienced in linear and rotational movements due to the presence of the surrounding fluid


</br>
</br>


# Config files what parameters are used for

```yaml
# Dynamics model parameters for G500

g500/num_actuators: 5
g500/dynamics/period: 0.001
g500/dynamics/uwsim_period: 0.001
g500/dynamics/mass: 98.0
g500/dynamics/gravity_center: [0.0, 0.0, 0.05]
g500/dynamics/g: 9.81
g500/dynamics/radius: 0.286

g500/dynamics/ctf: 0.00006835
g500/dynamics/ctb: 0.00006835

#Actuator tau for first order actuator dynamic model
g500/dynamics/actuators_tau: [0.2, 0.2, 0.2, 0.2, 0.2]
#Inputs higher than actuators_maxsat will saturate to actuators_maxsat
g500/dynamics/actuators_maxsat: [1, 1, 1, 1, 1]
#Inputs below actuators_minsat will saturate to actuators_minsat
g500/dynamics/actuators_minsat: [-1, -1, -1, -1, -1]
#Inputs to actuators will be scaled to actuators_gain,
g500/dynamics/actuators_gain: [1500, 1500, 1500, 1500, 1500]

g500/dynamics/dzv: 0.05
g500/dynamics/dv: 0.35
g500/dynamics/dh: 0.4
g500/dynamics/density: 1000.0

g500/dynamics/tensor: [8.0, 0.0, 0.0, 0.0, 8.0, 0.0, 0.0, 0.0, 8.0]
g500/dynamics/damping: [.0, .0, .0, -130.0, -130.0, -130.0]
g500/dynamics/quadratic_damping: [-148.0, -148.0, -148.0, -180.0, -180.0, -180.0]

g500/dynamics/Mrb: [ 98.0,    0.0,    0.0,    0.0,    4.9,  -0.0,
                     0.0,   98.0,    0.0,   -4.9,   0.0,    0.0,
                     0.0,    0.0,   98.0,    0.0,   -0.0,    0.0,
                     0.0,   -4.9,   0.0,    8.0,    0.0,    0.0,
                     4.9,   0.0,   -0.0,    0.0,    8.0,    0.0,
                     -0.0,    0.0,    0.0,    0.0,    0.0,    8.0 ]

g500/dynamics/Ma: [  49.0,    0.0,    0.0,    0.0,    0.0,   0.0,
                     0.0,    49.0,    0.0,    0.0,    0.0,   0.0,
                     0.0,    0.0,    49.0,    0.0,    0.0,   0.0,
                     0.0,    0.0,    0.0,    0.0,    0.0,   0.0,
                     0.0,    0.0,    0.0,    0.0,    0.0,   0.0,
                     0.0,    0.0,    0.0,    0.0,    0.0,   0.0 ]

#G500 thrusters.
#Expresion evaluated at each iteration by the python interpreter
#ct is a vector internally defined such that if u[i]>0 then ct[i]=ctf, else ct[i]=ctb, i>=0 and i<number_of_actuators
#du is the vector with the control inputs
#The rest of parameters defined in this file can be referenced here as "self.param", i.e /dynamics/dh maps to "self.dh"
g500/dynamics/allocation_matrix: "
[-ct[0]*abs(du[0]),            -ct[1]*abs(du[1]),              .0,                       .0,                           .0,
.0,                             .0,                             .0,                       .0,                           ct[4]*abs(du[4]),
.0,                             .0,                             -ct[2]*abs(du[2]),          -ct[3]*abs(du[3]),            .0,
.0,                             .0,                             .0,                       .0,                           .0,
.0,                             .0,                             -ct[2]*self.dv*abs(du[2]), ct[3]*self.dv*abs(du[3]),     .0,
-ct[0]*self.dh*abs(du[0]),      ct[1]*self.dh*abs(du[1]),       .0,                       .0,                           .0]"

#Meters and Rads [X, Y, Z, Roll, Pitch, Yaw]
g500/dynamics/initial_pose: [0.0, 0.0, 0.0, 0, 0, 1.57] #[3.0, 1.1, 2.8, 0, 0, 3.14]
g500/dynamics/initial_velocity: [0, 0, 0, 0, 0, 0]

g500/dynamics/topic_name: "/dataNavigator"
g500/dynamics/external_force_topic: "/g500/external_force"
g500/dynamics/frame_id: "g500_base_link"


#WATER CURRENTs SIMULATION
dynamics/current_mean: [0.05, 0, 0]
dynamics/current_sigma: [0.002, 0.001, 0.001]
dynamics/current_min: [0.0, 0.0, 0.0]
dynamics/current_max: [0.0, 0.0, 0.0]

```

# Parameters

Any parameter that you know about and can be helpful.
