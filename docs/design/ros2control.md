# Ros2Control

[Ros2Control](https://control.ros.org/master/index.html) is a framework providing interesting features in robotics, such as realtime control. This page is presenting the main features that are usefull in the Riptide control.

## Realtime control

Ros2Control is able to efficiently read sensors data, and ask the controller to create a command to be applied on actuators in realtime (i.e. in the same loop). No outdated sensor data will be used by the controller.

??? tip "Realtime kernel"
    Use a realtime kernel to benefit of the realtime aspect of Ros2Control.

## Sensors / actuators failure detection

Hardware interfaces always return success or failure at each step. The detection of a failure is then immediate and a strategy could be adopted depending on the encountered fail.

??? warning "Failure detection strategy"
    Failure detection is already implemented for sensor and actuators interfaces, but there is not yet any strategies in such cases.

## Actuators control interface claimable once

It's recommanded to avoid multiple nodes to control the same actuator at the same time, which is possible when using classical Ros2 topics to conrtol an actuator. Using Ros2Control framework prevents this behavior.

## Efficient switch of controllers

Controllers can be switched runtime between two control loops to avoid downtimes. It's better than classical solution provided by ros which cannot perform such tasks.

## Chaining controllers

Controllers can be chained to elaborate more complex control laws based on atomic controlkers.

??? tip "Available controllers"
    Consult the list of [available controllers](../controllers/index.md) 

## Simulation and real code are the same

Hardware interfaces can be transparently switched as soon as they are providing the same `command_interface` and `state_interface`. Simulation specific `hardware_interfaces` can be implemented to interact with the simulator instead sensors and actuators.

??? note "Simulator"
    See the simulator section to know how to simulate the Riptide.

## Design

Hardware interfaces should be implemented to communicate with sensors and actuators and provide `command_interface` and `state_interface`.

Controllers are also implemented which are claiming these `command_interface` and `state_interface` to compute the command to be applied on actuators following custom or classical control theory.