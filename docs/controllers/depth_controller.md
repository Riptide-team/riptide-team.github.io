# Depth controller

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

## Command interfaces

| `command_interface` | Description         |
| ------------------- | ------------------- |
| `thruster`          | Thruster velocity   |
| `p_fin`             | Port-fin angle      |
| `s_fin`             | Starboard-fin angle |

## State interfaces

| `state_interface` | Description   |
| ----------------- | ------------- |
| `depth`           | Riptide depth |

## Parameters
-