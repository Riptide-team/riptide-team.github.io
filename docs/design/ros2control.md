# Ros2Control

## Why using Ros2 control

Ros2Control is a framework providing interesting features in robotics, such as realtime control.

Here is listed the main features that are usefull in the Riptide:
- Realtime control of actuators
- Sensors / actuators failure detection (reactivity in such situations is not yet implemented)
- Actuators control interface claimable by only one controller
- Chaining controllers

## Design

Hardware interfaces should be implemented to communicate with sensors and actuators and provide `command_interface` and `state_interface`.

Controllers are also implemented which are claiming these `command_interface` and `state_interface` to compute the command to be applied on actuators following custom or classical control theory.