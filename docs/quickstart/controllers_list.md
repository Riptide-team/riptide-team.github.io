# Available controllers

Here is the list of implemented controllers for the Riptide

| Controller name          | Description                         |
| ------------------------ | ----------------------------------- |
| `depth_controller`       | Simple depth controller             |
| `riptide_controller`     | Riptide twist controller            |
| `log_controller`         | Log based atitude controller        |
| `orthogonal_controller`  | Orhtogonal based atitude controller |

??? Example "Implementation of `orthogonal_controller`"
    `orthogonal_chaining` implementation is still in progress!

??? Failure "Chaining controllers"
    Controller chaining is not yet implemented for these controllers!

## Depth controller

### Claimed interfaces

#### `command_interfaces`

- `p_fin`: port-fin `command_interface`
- `s_fin`: starboard-fin `command_interface`

#### `state_interfaces`

- `depth`: depth of the pressure sensor