# Taranis QX7 Controller

## Switch Layout

Here is the switch layout of the `FrSky Taranis Q X7` controller.

![FrSky Taranis Q X7 layout](./taranis-q-x7-switches.png)

Control are currently bind respecting the following table:

| Input | Command                      | Description                                                 |
|-------|------------------------------|-------------------------------------------------------------|
| `J1`  | Rudder (RUD / Yaw)           | Yaw of the robot                                            |
| `J2`  | Elevator (ELE / Pitch)       | Pitch of the robot                                          |
| `J3`  | {--Aileron (AIL / Roll)--}   | {--Roll (not bind for now)--}                               |
| `J4`  | Thrust                       | Thrust value of the propeller                               |
| `SA`  | Forward / Neutral / Backward | Sign of the thrust                                          |
| `SF`  | Automatic / Manual           | Enable the controller                                       |
| `SH`  | Multiplexer ignition         | Latching the switch launch the multiplexer                  |
| `SD`  | Multiplexer multiplicator    | Multiplication factor: $\times 1$ / $\times 2$ / $\times 3$ |
| `S1`  | Multiplexer value            | Value of the time alloxed for the mission                   |


## Simulation

Here is the procedure to use the `FrSky Taranis Q X7` controller with the simulator.

- Put a battery in the `FrSky Taranis Q X7`
- Start the `FrSky Taranis Q X7`
- Plug an usb cable in the bottom usb port of the `FrSky Taranis Q X7`
- Plug this cabe in an usb port of the computer
- Select mode `USB Joystick (HID)` on the `FrSky Taranis Q X7`
- Check that the device is recognized by the computer and accessible by `Ros2`
- Launch the `joy_node` of the `joy` package

```bash
> ros2 run joy joy_node
[INFO 1693900564.881254763] [joy_node]: No haptic (rumble) available, skipping initialization (handleJoyDeviceAdded() at ./src/joy.cpp:394)                                                                 
[INFO 1693900564.881379413] [joy_node]: Opened joystick: OpenTX FrSky Taranis Joystick.  deadzone: 0.0 50000 (handleJoyDeviceAdded() at ./src/joy.cpp:397)
```

`sensor_msgs/msg/Joy` should be published by the `joy_node` under the `/joy` topic.

### Troubleshooting

??? Question "Is the controller well recognized by the computer ?"
	To check that the `Taranis QX7 Controller` is well recognized by the computer and `Ros2` you can run

	```bash
	> ros2 run joy joy_enumerate_devices
	Joystick Device ID : Joystick Device Name
	-----------------------------------------
					0 : OpenTX FrSky Taranis Joystick
	```
	Here the controller is well recognized.

??? Question "How to check that messages are correctly published ?"

	You can check that the `/joy` topic is welle created by the `joy_node`

	```bash
	> ros2 topic list
	/joy
	/joy/set_feedback
	/parameter_events
	/rosout
	```

	And then check published messages and control that messages are changing relative to controller's input

	```bash
	> ros2 topic echo /joy
	header:
	stamp:
		sec: 1693900834
		nanosec: 880572482
	frame_id: joy
	axes:
	- 1.0
	- 1.0
	- -0.0
	- -0.0
	- -0.0
	- -0.0
	- -0.0
	buttons:
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	- 0
	---
	```

??? Question "Can I unplug the TBS Crossfire RC emitter from the Controller ?"
	Yes indeed ! It's safer to avoid unwanted control of the Riptide through simulation and to avoid emitter's buzzing noise while trying to communicate with the RC receiver in the Riptide.