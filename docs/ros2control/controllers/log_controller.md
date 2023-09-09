# Log Controller

Log controller able to generate angular velocity from current robot's orientation and desired orientation.

```mermaid
flowchart LR
    s1[desired_quaternion.x] & s2[desired_quaternion.y] & s3[desired_quaternion.z] & s4[desired_quaternion.w] --> c(log_controller) --> c1[linear_velocity.x] & c2[angular_velocity.x] & c3[angular_velocity.y] & c4[angular_velocity.z]
    class s1,s2,s3,s4 state;
    class c1,c2,c3,c4 command;
    class c controller;
    classDef state stroke:#2ecc71,stroke-width:2px;
    classDef controller stroke:#3498db,stroke-width:2px;
    classDef command stroke:#e74c3c,stroke-width:2px;
```

## Command interfaces

| `command_interface`  | Description                             |
|----------------------|-----------------------------------------|
| `linear_velocity.x`  | Requested linear velocity along x axis  |
| `angular_velocity.x` | Requested angular velocity along x axis |
| `angular_velocity.y` | Requested angular velocity along y axis |
| `angular_velocity.z` | Requested angular velocity along z axis |

## State interfaces

| `state_interface` | Description                    |
| ----------------- | ------------------------------ |
| `orientation.x`   | Robot orientation quaternion x |
| `orientation.y`   | Robot orientation quaternion y |
| `orientation.z`   | Robot orientation quaternion z |
| `orientation.w`   | Robot orientation quaternion w |

## Reference interfaces

| `reference_interface`   | Description                      |
|-------------------------|----------------------------------|
| `desired_orientation.x` | Desired orientation quaternion x |
| `desired_orientation.y` | Desired orientation quaternion y |
| `desired_orientation.z` | Desired orientation quaternion z |
| `desired_orientation.w` | Desired orientation quaternion w |

## Subscribed topic

| Topic name             | Type                                                                                                   | Description                    |
|------------------------|--------------------------------------------------------------------------------------------------------|--------------------------------|
| `~/desired_quaternion` | [`geometry_msgs/Quaternion`](http://docs.ros.org/en/noetic/api/geometry_msgs/html/msg/Quaternion.html) | Desired orientation quaternion |

## Published topics

| Topic name            | Type                              | Description             |
|-----------------------|-----------------------------------|-------------------------|
| `~/controller_state`  | `riptide_msgs/LogControllerState` | Controller actual state |
