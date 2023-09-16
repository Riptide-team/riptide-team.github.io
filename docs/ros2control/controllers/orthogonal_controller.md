# Orthogonal controller

Orthogonal controller able to control the Riptide in such a way that it makes vectors expressed in the robot frame orthogonal to vectors in the world frame.

This controller is related to the [log_controller](./log_controller.md) in the way that it generate angular velocity for the Riptide, but, unlike the latter, it allows you to control only part of the robot's orientation. This lead to fastest reorientations, and the possibility to control uncontrolled degrees of freedom using other controllers.

```mermaid
flowchart LR
    r1[additionnal_angular_velocity.x] & r2[additionnal_angular_velocity.y] & r3[additionnal_angular_velocity.z] --- S( ):::empty --> c(orthogonal_controller) --- R( ):::empty --> c1[linear_velocity.x] & c2[angular_velocity.x] & c3[angular_velocity.y] & c4[angular_velocity.z]
    class c1,c2,c3,c4 command;
    class r1,r2,r3 reference;
    class c controller;
    classDef state stroke:#2ecc71,stroke-width:2px;
    classDef controller stroke:#3498db,stroke-width:2px;
    classDef command stroke:#e74c3c,stroke-width:2px;
    classDef reference stroke:#8e44ad,stroke-width:2px;
    classDef empty width:-1px,height:-1px;
```

## Command Interfaces

| `command_interface`  | Description                             |
|----------------------|-----------------------------------------|
| `linear_velocity.x`  | Requested linear velocity along x axis  |
| `angular_velocity.x` | Requested angular velocity along x axis |
| `angular_velocity.y` | Requested angular velocity along y axis |
| `angular_velocity.z` | Requested angular velocity along z axis |

## State Interfaces

-


## Reference Interfaces

| `reference_interface`           | Description                               |
|---------------------------------|-------------------------------------------|
| `additional_angular_velocity.x` | Additionnal angular velocity along x axis |
| `additional_angular_velocity.y` | Additionnal angular velocity along y axis |
| `additional_angular_velocity.z` | Additionnal angular velocity along z axis |