# Controllers

## Available broadcasters

Here is the list of implemented broadcasters for the Riptide

| Controller name                                                                  | Type         | Description                 |
|----------------------------------------------------------------------------------|--------------|-----------------------------|
| [`joint_state_broadcaster`](./broadcasters/joint_state_broadcaster.md)           | `Controller` | Broadcast joint states      |
| [`imu_sensor_broadcaster`](./broadcasters/imu_sensor_broadcaster.md)             | `Controller` | Broadcast imu sensor's data |
| [`riptide_pressure_broadcaster`](./broadcasters/riptide_pressure_broadcaster.md) | `Controller` | Broadcast pressure data     |
| [`riptide_tail_broadcaster`](./broadcasters/riptide_tail_broadcaster.md)         | `Controller` | Broadcast tail data         |

## Available controllers

Here is the list of implemented controllers for the Riptide

| Controller name                                                   | Type                  | Description                         |
|-------------------------------------------------------------------|-----------------------|-------------------------------------|
| [`depth_controller`](./controllers/depth_controller.md)           | `Controller`          | Simple depth controller             |
| [`riptide_controller`](./controllers/riptide_controller.md)       | `ChainableController` | Riptide twist controller            |
| [`log_controller`](./controllers/log_controller.md)               | `Controller`          | Log based atitude controller        |
| [`orthogonal_controller`](./controllers/orthogonal_controller.md) | `Controller`          | Orhtogonal based atitude controller |
| [`immersion_controller`](./controllers/immersion_controller.md)   | `Controller`          | Riptide immersion controller        |


??? Example "Implementation of `orthogonal_controller`"
    `orthogonal_controller` implementation is still in progress!

??? Example "Implementation of `immersion_controller`"
    `immersion_controller` implementation is not yet implemented!

??? Failure "Chaining controllers"
    Controller chaining is not yet implemented for these controllers!

---
