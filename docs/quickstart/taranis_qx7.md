# Taranis QX7 Controller

## Simulation

Here is the procedure to use the `Taranis QX7 controller` with the simulator.

- Put a battery in the `Taranis QX7 Controller`
- Start the `Taranis QX7 Controller`
- Plug an usb cable in the bottom usb port of the `Taranis QX7 Controller`
- Plug this cabe in an usb port of the computer
- Select mode `USB Joystick (HID)` on the `Taranis QX7 Controller`
- Check that the device is recognized by the computer and accessible by `Ros2`
- Launch the `joy_node` of the `joy` package

```bash
> ros2 run joy joy_node
[INFO 1693900564.881254763] [joy_node]: No haptic (rumble) available, skipping initialization (handleJoyDeviceAdded() at ./src/joy.cpp:394)                                                                 
[INFO 1693900564.881379413] [joy_node]: Opened joystick: OpenTX FrSky Taranis Joystick.  deadzone: 0.0 50000 (handleJoyDeviceAdded() at ./src/joy.cpp:397)  
```

??? Question "Is the controller well recognized by the computer ?"
	To check that the `Taranis QX7 Controller` is well recognized by the computer and `Ros2` you can run

	```bash
	> ros2 run joy joy_enumerate_devices
	Joystick Device ID : Joystick Device Name
	-----------------------------------------
					0 : OpenTX FrSky Taranis Joystick
	```
	Here the controller is well recognized.

`sensor_msgs/msg/Joy` should be published by the `joy_node` under the `/joy` topic.

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