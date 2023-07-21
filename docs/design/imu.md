# IMU

Riptide imu follows the [REP-145: Conventions for IMU Sensor Drivers](https://ros.org/reps/rep-0145.html). IMU associated frame is in NED convention (x-North, y-East, z-Down). 

## Published topics

| Topic name       | Type                                                                                               |
| ---------------- | -------------------------------------------------------------------------------------------------- |
| `~/imu/data_raw` | [`sensor_msgs/Imu`](https://docs.ros2.org/latest/api/sensor_msgs/msg/Imu.html)                     |
| `~/imu/data`     | [`sensor_msgs/Imu`](https://docs.ros2.org/latest/api/sensor_msgs/msg/Imu.html)                     |
| `~/imu/mag`      | [`sensor_msgs/MagneticField`](https://docs.ros2.org/latest/api/sensor_msgs/msg/MagneticField.html) |

## Calibration