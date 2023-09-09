# Depth controller

Depth controller able to control depth of the Riptide by controlling the robot's pitch.

```mermaid
flowchart LR
    s1[depth] --> c(depth_controller) --> c1[orientation.x] & c2[orientation.y] & c3[orientation.z] & c4[orientation.w]
    class s1 state;
    class c1,c2,c3,c4 command;
    class c controller;
    classDef state stroke:#2ecc71,stroke-width:2px;
    classDef controller stroke:#3498db,stroke-width:2px;
    classDef command stroke:#e74c3c,stroke-width:2px;
```

## Command interfaces

| `command_interface` | Description                      |
|---------------------|----------------------------------|
| `quaternion.x`      | Desired orientation quaternion x |
| `quaternion.y`      | Desired orientation quaternion y |
| `quaternion.z`      | Desired orientation quaternion z |
| `quaternion.w`      | Desired orientation quaternion w |

## State interfaces

| `state_interface` | Description   |
| ----------------- | ------------- |
| `depth`           | Riptide depth |

## Published topics

| Topic name            | Type                                  | Description             |
|-----------------------|---------------------------------------|-------------------------|
| `~/controller_state`  | `riptide_msgs/RiptideControllerState` | Controller actual state |

## Provided action

| Action name | Type                 | Description              |
|-------------|----------------------|--------------------------|
| `~/depth`   | `riptide_msgs/Depth` | Controller desired depth |