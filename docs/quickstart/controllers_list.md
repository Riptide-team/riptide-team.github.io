# Available controllers

Here is the list of implemented controllers for the Riptide

| Controller name          | Type                  | Description                         |
| ------------------------ | --------------------- |------------------------------------ |
| `depth_controller`       | `Controller`          | Simple depth controller             |
| `riptide_controller`     | `ChainableController` | Riptide twist controller            |
| `log_controller`         | `Controller`          | Log based atitude controller        |
| `orthogonal_controller`  | `Controller`          | Orhtogonal based atitude controller |
| `immersion_controller`   | `Controller`          | Riptide immersion controller        |


??? Example "Implementation of `orthogonal_controller`"
    `orthogonal_controller` implementation is still in progress!

??? Example "Implementation of `immersion_controller`"
    `immersion_controller` implementation is not yet implemented!

??? Failure "Chaining controllers"
    Controller chaining is not yet implemented for these controllers!

## Depth controller

Depth controller able to control depth of the Riptide by controlling the robot's pitch.

```mermaid
flowchart LR
    s1[depth] --> c(depth_controller) --> c1[thruster] & c2[p_fin] & c3[s_fin]
    class s1 state;
    class c1,c2,c3 command;
    class c controller;
    classDef state stroke:#2ecc71,stroke-width:2px;
    classDef controller stroke:#3498db,stroke-width:2px;
    classDef command stroke:#e74c3c,stroke-width:2px;
```

### Command interfaces

| `command_interface` | Description         |
| ------------------- | ------------------- |
| `thruster`          | Thruster velocity   |
| `p_fin`             | Port-fin angle      |
| `s_fin`             | Starboard-fin angle |

### State interfaces

| `state_interface` | Description   |
| ----------------- | ------------- |
| `depth`           | Riptide depth |

### Parameters

-

## Riptide Controller

Riptide controller able to generate thruster and fin control values from desired linear and angular velocities.

```mermaid
flowchart LR
    s1[orientation.x] & s2[orientation.y] & s3[orientation.z] & s4[orientation.w] --> c(depth_controller) --> c1[thruster] & c2[d_fin] & c3[p_fin] & c4[s_fin]
    class s1,s2,s3,s4 state;
    class c1,c2,c3,c4 command;
    class c controller;
    classDef state stroke:#2ecc71,stroke-width:2px;
    classDef controller stroke:#3498db,stroke-width:2px;
    classDef command stroke:#e74c3c,stroke-width:2px;
```

### Command interfaces

| `command_interface` | Description         |
| ------------------- | ------------------- |
| `thruster`          | Thruster velocity   |
| `p_fin`             | Direction-fin angle |
| `p_fin`             | Port-fin angle      |
| `s_fin`             | Starboard-fin angle |

### State interfaces

| `state_interface` | Description                    |
| ----------------- | ------------------------------ |
| `orientation.x`   | Robot orientation quaternion x |
| `orientation.y`   | Robot orientation quaternion y |
| `orientation.z`   | Robot orientation quaternion z |
| `orientation.w`   | Robot orientation quaternion w |

### Parameters

- 

### Actions server

action can be called 


