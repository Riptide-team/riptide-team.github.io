# Immersion controller

Open loop immersion controller able to immerse the Riptide 1m below the sea surface. The strategy is to set the thruster's velocity at its maximum, and to perform a maneuver on the fins such as the Riptide's pitch increase and then decrease suddenly.

```mermaid
flowchart LR
    c(immersion_controller) --- C( ):::empty -->c1[thruster] & c2[d_fin] & c3[p_fin] & c4[s_fin]
    class s1,s2,s3,s4 state;
    class c1,c2,c3,c4 command;
    class c controller;
    classDef controller stroke:#3498db,stroke-width:2px;
    classDef command stroke:#e74c3c,stroke-width:2px;
    classDef empty width:-1px,height:-1px;
```

## Command Interfaces

| `command_interface` | Description         |
| ------------------- | ------------------- |
| `thruster`          | Thruster velocity   |
| `p_fin`             | Direction-fin angle |
| `p_fin`             | Port-fin angle      |
| `s_fin`             | Starboard-fin angle |

## Provided action

| Action name | Type                   | Description              |
|-------------|------------------------|--------------------------|
| `~/immerse` | `riptide_msgs/Immerse` | Controller immerse order |