# Movement Component

The movement component is of class `MovementComponent` and handles the player's velocity.

## Properties

| Type            | Name                                                        | Default        |
| :-------------- | :---------------------------------------------------------- | :------------- |
| CharacterBody2D | [`body`](#characterbody2d-body)                             | N/A            |
| | | |
| float           | [`walk_move_speed`](#float-walk_move_speed)                 | 100.0          |
| float           | [`sprint_speed_multiplier`](#float-sprint_speed_multiplier) | 2.0            |
| float           | [`acc`](#float-acc)                                         | 600.0          |
| float           | [`dec`](#float-dec)                                         | 800.0          |
| | | |
| float           | [`jump_velocity`](#float-jump_velocity)                     | -200.0         |
| float           | [`coyote_time_max`](#float-coyote_time_max)                 | 0.15           |

## Methods

| Return | Name                                                                              |
| :----- | :-------------------------------------------------------------------------------- |
| void   | [`initialize(_body : CharacterBody2D)`](#void-initialize_body-characterbody2d)            |
| void   | [`update(delta : float, is_jumping : bool, move_dir : float, sprinting : bool)`](#void-updatedelta-float-is_jumping-bool-move_dir-float-sprinting-bool) |

## Property Descriptions

### `CharacterBody2D` - `body`
- The body that velocity is applied to,

### `float` - `walk_move_speed`
- How quickly the player moves when walking. 

### `float` - `sprint_speed_multiplier`
- The multiplier applied to the player's movement speed when sprinting.

### `float` - `acc`
- How quickly the player accelerates.

### `float` - `dec`
- How quickly the player decelerates.

### `float` - `jump_velocity`
- How strong the player's jump is.

### `float` - `coyote_time_max`
- "Coyote time" is a grace period after walking off a ledge where a player can still jump. 

## Method Descriptions

### `void` - `initialize(_body : CharacterBody2D)`
- Assigns a passed `CharacterBody2D` as the body this component will manipulate.

### `void` - `update(delta : float, is_jumping : bool, move_dir : float, sprinting : bool)`
- Applies gravity on the player.
- Checks and updates for coyote time.
- Applies jumping velocity.
- Applies horizontal velocity.