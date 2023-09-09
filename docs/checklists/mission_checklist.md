# Mission Checklist

## Sensors calibration

- [ ] Checking pressure zero
- [ ] Checking imu calibration

??? Tips "Fast sensor's status checking"
    To quickly check robot's sensors state, you could use the ncurses interfaces on the robot by typing in a terminal

    ```bash
    > wtf
    ```

    or

    ```bash
    > ros2 run riptide_wtf riptide_wtf
    ```

## Actuators calibration

- [ ] Checking fins zeros
- [ ] Checking actuators with [RC controller](../quickstart/taranis_qx7.md)