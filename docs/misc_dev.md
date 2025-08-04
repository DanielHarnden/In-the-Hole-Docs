# Misc. Dev Information

## Project Naming Schemes

- Folders in the Godot project should be named using proper [title case](https://capitalizemytitle.com/).
    - `This is an Example Folder Name`
- Files should be named using [snake case](https://en.wikipedia.org/wiki/Snake_case).
    - `this_is_an_example_file_name.gd`
- Functions should be named in the same way as files.
    - Function return and variable typings should be declared whenever possible.
    - Private functions should be prefixed with an underscore.
        - `func example_public_function(input : float) -> void:`
        - `func _example_private_function(input : float) -> void:`
- Variables should be named in the same way as files.
    - Variable typings should be declared whenever possible.
    - Variable names should be descriptive; it is preferred to have verbose names rather than vague names.
    - Private variables should be prefixed with an underscore.
    - Constant variables and enums should be written in all caps.
        - `var example_public_variable : bool = true`
        - `var _example_private_variable : bool = true`
        - `const EXAMPLE_CONST = : bool true`
    - The following are **improper variable names** and should be avoided.
        - `var a : bool = false`
        - `var stupid_idiot_variable_for_dumb_babies := false`
        - `var is_not_jumping2 = false`

## Project Organization

The Godot project is structured based on main features, which are then grouped by asset type. Below is the example file structure that each main feature should follow. If a file doesn't fit into any one main feature, it should go in `res://General`.

``` txt
res://
└── Slot Machine/
    ├── Assets/
    │    ├── Audio/
    │    │    └── jackpot.wav
    │    └── Images/
    │         └── cherry_icon.png
    ├── Data/
    │    └── stats.gd
    ├── Scenes/
    │    └── player.tscn
    └── Scripts/
         └── player_controller.gd
```
