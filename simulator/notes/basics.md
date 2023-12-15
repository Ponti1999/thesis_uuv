# Important parts

- In UWSim 1 unit is equal to 1 meter
- example ROS interface nodes in the <tt>interface_examples</tt> folder
- Updating the vehicle position with the /dataNavigator topic

- Full Source -based installation: Installs simulater and libraries from source. Complete control for developing, latest features but slower and harder building.


# rostopic list

- /dataNavigator
- /g500/ForceSensor
- /g500/contactSensor
- /g500/dvl
- /g500/echo1
- /g500/echo2
- /g500/gps
- /g500/imu
- /g500/multibeam
- /g500/pose
- /g500/pressure
- /g500/twist
- /rosout
- /rosout_agg
- /tf
- /tf_static
- /uwsim/camera1
- /uwsim/camera1/compressed
- /uwsim/camera1/compressed/parameter_descriptions
- /uwsim/camera1/compressed/parameter_updates
- /uwsim/camera1/compressedDepth
- /uwsim/camera1/compressedDepth/parameter_descriptions
- /uwsim/camera1/compressedDepth/parameter_updates
- /uwsim/camera1/theora
- /uwsim/camera1/theora/parameter_descriptions
- /uwsim/camera1/theora/parameter_updates
- /uwsim/camera1_info
- /uwsim/g500/range
- /uwsim/joint_state
- /uwsim/joint_state_command
- /uwsim/rangecamera
- /uwsim/rangecamera/compressed
- /uwsim/rangecamera/compressed/parameter_descriptions
- /uwsim/rangecamera/compressed/parameter_updates
- /uwsim/rangecamera/compressedDepth
- /uwsim/rangecamera/compressedDepth/parameter_descriptions
- /uwsim/rangecamera/compressedDepth/parameter_updates
- /uwsim/rangecamera/theora
- /uwsim/rangecamera/theora/parameter_descriptions
- /uwsim/rangecamera/theora/parameter_updates
- /uwsim/rangecamera_info
- /uwsim_marker/update
- /uwsim_marker/update_full

## /dataNavigator
- update the vehicle position in the default scenario (2 meters along positive X axis): </br>
```console
rosrun uwsim setVehiclePosition /dataNavigator 2 0 0 0 0 0
```