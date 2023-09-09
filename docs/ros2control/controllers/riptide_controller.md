# Riptide Controller

Riptide controller able to generate thruster and fin control values from desired linear and angular velocities.

```mermaid
flowchart LR
    s1[linear_velocity.x] & s2[angular_velocity.x] & s3[angular_velocity.y] & s4[angular_velocity.z] --> c(riptide_controller) --> c1[thruster] & c2[d_fin] & c3[p_fin] & c4[s_fin]
    class s1,s2,s3,s4 state;
    class c1,c2,c3,c4 command;
    class c controller;
    classDef state stroke:#2ecc71,stroke-width:2px;
    classDef controller stroke:#3498db,stroke-width:2px;
    classDef command stroke:#e74c3c,stroke-width:2px;
```

## Command interfaces

| `command_interface` | Description         |
| ------------------- | ------------------- |
| `thruster`          | Thruster velocity   |
| `p_fin`             | Direction-fin angle |
| `p_fin`             | Port-fin angle      |
| `s_fin`             | Starboard-fin angle |

## State interfaces

| `state_interface` | Description                    |
| ----------------- | ------------------------------ |
| `orientation.x`   | Robot orientation quaternion x |
| `orientation.y`   | Robot orientation quaternion y |
| `orientation.z`   | Robot orientation quaternion z |
| `orientation.w`   | Robot orientation quaternion w |

## Reference interfaces

| `reference_interface` | Description                             |
|-----------------------|-----------------------------------------|
| `linear_velocity.x`   | Requested linear velocity along x axis  |
| `angular_velocity.x`  | Requested angular velocity along x axis |
| `angular_velocity.y`  | Requested angular velocity along y axis |
| `angular_velocity.z`  | Requested angular velocity along z axis |

## Subscribed topic

| Topic name  | Type                                                                                         | Description   |
|-------------|----------------------------------------------------------------------------------------------|---------------|
| `~/cmd_vel` | [`geometry_msgs/Twist`](http://docs.ros.org/en/noetic/api/geometry_msgs/html/msg/Twist.html) | Desired Twist |

## Published topics

| Topic name            | Type                                  | Description             |
|-----------------------|---------------------------------------|-------------------------|
| `~/controller_state`  | `riptide_msgs/RiptideControllerState` | Controller actual state |
