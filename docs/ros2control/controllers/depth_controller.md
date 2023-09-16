# Depth controller

Depth controller able to control depth of the Riptide by controlling the robot's pitch.

```mermaid
flowchart LR
    s1[depth] & s2[orientation.x] & s3[orientation.y] & s4[orientation.z] & s5[orientation.w] --- S( ):::empty --> c(depth_controller) --- R( ):::empty --> c1[orientation.x] & c2[orientation.y] & c3[orientation.z] & c4[orientation.w]
    class s1,s2,s3,s4,s5 state;
    class c1,c2,c3,c4 command;
    class c controller;
    classDef state stroke:#2ecc71,stroke-width:2px;
    classDef controller stroke:#3498db,stroke-width:2px;
    classDef command stroke:#e74c3c,stroke-width:2px;
    classDef empty width:-1px,height:-1px;
```

## Command interfaces

| `command_interface` | Description                      |
|---------------------|----------------------------------|
| `orientation.x`      | Desired orientation quaternion x |
| `orientation.y`      | Desired orientation quaternion y |
| `orientation.z`      | Desired orientation quaternion z |
| `orientation.w`      | Desired orientation quaternion w |

## State interfaces

| `state_interface` | Description                    |
|-------------------|--------------------------------|
| `depth`           | Riptide depth                  |
| `orientation.x`   | Robot orientation quaternion x |
| `orientation.y`   | Robot orientation quaternion y |
| `orientation.z`   | Robot orientation quaternion z |
| `orientation.w`   | Robot orientation quaternion w |

## Published topics

| Topic name            | Type                                  | Description             |
|-----------------------|---------------------------------------|-------------------------|
| `~/controller_state`  | `riptide_msgs/RiptideControllerState` | Controller actual state |

## Provided action

| Action name | Type                 | Description              |
|-------------|----------------------|--------------------------|
| `~/depth`   | `riptide_msgs/Depth` | Controller desired depth |