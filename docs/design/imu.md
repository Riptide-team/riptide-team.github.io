# IMU

Riptide imu follows the [REP-145: Conventions for IMU Sensor Drivers](https://ros.org/reps/rep-0145.html). IMU associated frame is in NED convention (x-North, y-East, z-Down). 

## Published topics

| Topic name    | Type                                                                                               |
| ------------- | -------------------------------------------------------------------------------------------------- |
| `imu_raw_ned` | [`sensor_msgs/Imu`](https://docs.ros2.org/latest/api/sensor_msgs/msg/Imu.html)                     |
| `imu_ned`     | [`sensor_msgs/Imu`](https://docs.ros2.org/latest/api/sensor_msgs/msg/Imu.html)                     |
| `magnetic`    | [`sensor_msgs/MagneticField`](https://docs.ros2.org/latest/api/sensor_msgs/msg/MagneticField.html) |

## Calibration