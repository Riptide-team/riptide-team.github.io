# Available controllers

Here is the list of implemented controllers for the Riptide

| Controller name                                       | Type                  | Description                         |
|-------------------------------------------------------|-----------------------|-------------------------------------|
| [`depth_controller`](./depth_controller.md)           | `Controller`          | Simple depth controller             |
| [`riptide_controller`](./riptide_controller.md)       | `ChainableController` | Riptide twist controller            |
| [`log_controller`](./log_controller.md)               | `Controller`          | Log based atitude controller        |
| [`orthogonal_controller`](./orthogonal_controller.md) | `Controller`          | Orhtogonal based atitude controller |
| [`immersion_controller`](./immersion_controller.md)   | `Controller`          | Riptide immersion controller        |


??? Example "Implementation of `orthogonal_controller`"
    `orthogonal_controller` implementation is still in progress!

??? Example "Implementation of `immersion_controller`"
    `immersion_controller` implementation is not yet implemented!

??? Failure "Chaining controllers"
    Controller chaining is not yet implemented for these controllers!
