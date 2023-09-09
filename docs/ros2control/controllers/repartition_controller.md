# Repartition Controller

Riptide forces and torques repartition controller able to generate thruster and fin control values from desired Wrench.

```mermaid
flowchart LR
    s1[force.x] & s2[torque.x] & s3[torque.y] & s4[torque.z] --> c(repartition_controller) --> c1[thruster] & c2[d_fin] & c3[p_fin] & c4[s_fin]
    class s1,s2,s3,s4 state;
    class c1,c2,c3,c4 command;
    class c controller;
    classDef state stroke:#2ecc71,stroke-width:2px;
    classDef controller stroke:#3498db,stroke-width:2px;
    classDef command stroke:#e74c3c,stroke-width:2px;
```

## Command interfaces

| `command_interface` | Description         |
|---------------------|---------------------|
| `thruster`          | Thruster velocity   |
| `d_fin`             | Direction-fin angle |
| `p_fin`             | Port-fin angle      |
| `s_fin`             | Starboard-fin angle |

## State interfaces

| `state_interface` | Description                    |
|-------------------|--------------------------------|
| `force.x`         | Robot force quaternion x |
| `torque.x`        | Robot torque y |
| `torque.y`        | Robot torque z |
| `torque.z`        | Robot torque w |

## Reference interfaces

| `reference_interface` | Description                   |
|-----------------------|-------------------------------|
| `force.x`             | Requested force along x axis  |
| `torque.x`            | Requested torque along x axis |
| `torque.y`            | Requested torque along y axis |
| `torque.z`            | Requested torque along z axis |

## Subscribed topics

| Topic name | Type                                                                                           | Description      |
|------------|------------------------------------------------------------------------------------------------|------------------|
| `~/wrench` | [`geometry_msgs/Wrench`](http://docs.ros.org/en/noetic/api/geometry_msgs/html/msg/Wrench.html) | Requested Wrench |

## Published topics

| Topic name            | Type                                      | Description             |
|-----------------------|-------------------------------------------|-------------------------|
| `~/controller_state`  | `riptide_msgs/RepartitionControllerState` | Controller actual state |
