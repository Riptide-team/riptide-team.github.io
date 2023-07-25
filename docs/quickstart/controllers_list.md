# Available controllers

Here is the list of implemented controllers for the Riptide

| Controller name          | Description                         |
| ------------------------ | ----------------------------------- |
| `depth_controller`       | Simple depth controller             |
| `riptide_controller`     | Riptide twist controller            |
| `log_controller`         | Log based atitude controller        |
| `orthogonal_controller`  | Orhtogonal based atitude controller |
| `immersion_controller`   | Riptide immersion controller        |


??? Example "Implementation of `orthogonal_controller`"
    `orthogonal_controller` implementation is still in progress!

??? Example "Implementation of `immersion_controller`"
    `immersion_controller` implementation is not yet implemented!

??? Failure "Chaining controllers"
    Controller chaining is not yet implemented for these controllers!

## Depth controller

### Claimed interfaces

#### `command_interfaces`

- `p_fin`: port-fin `command_interface`
- `s_fin`: starboard-fin `command_interface`

#### `state_interfaces`

- `depth`: depth of the pressure sensor

### Parameters

-

## Riptide Controller

### Claimed interfaces

#### `command_interfaces`

- `thruster`: thruster `command_interface`
- `d_fin`: direction-fin `command_interface`
- `p_fin`: port-fin `command_interface`
- `s_fin`: starboard-fin `command_interface`

#### `state_interfaces`

- `orientation.x` orientation quaternion x `state_interface`
- `orientation.y` orientation quaternion y `state_interface`
- `orientation.z` orientation quaternion z `state_interface`
- `orientation.q` orientation quaternion q `state_interface`

#### Parameters

- 

#### Actions server

actioncan be called 


