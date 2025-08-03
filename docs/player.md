# Player

The player controller is separated into various `components` that handle the different aspects of what the player can do. The player controller script `player.gd` handles input, connects all of the component scripts, and updates UI elements accordingly.









## Stamina Component

The stamina component is of class `StaminaComponent` and handles the player's stamina state. It provides functions to update the stamina cap, maximum stamina, and current stamina.

### Properties

| Type  | Name                                              | Default                             |
| :---- | :------------------------------------------------ | :---------------------------------- |
| float | [`cap_stamina`](#float-cap_stamina)               | 100.0                               |
| float | [`max_stamina`](#float-max_stamina)               | [`cap_stamina`](#float-cap_stamina) |
| float | [`cur_stamina`](#float-cur_stamina)               | [`cap_stamina`](#float-cap_stamina) |
| | | |
| float | [`sprint_drain_speed`](#float-sprint_drain_speed) | 10.0                                |
| float | [`regen_speed`](#float-regen_speed)               | 5.0                                 |
| bool  | [`stamina_drained`](#bool-stamina_drained)        | false                               |

### Methods

| Return | Name                                                                              |
| :----- | :-------------------------------------------------------------------------------- |
| void   | [`update(delta : float, draining : bool)`](#void-updatedelta-float-draining-bool) |
| | | |
| void   | [`add_cur(amount : float)`](#void-add_curamount-float)                            |
| void   | [`add_max(amount : float)`](#void-add_maxamount-float)                            |
| void   | [`add_cap(amount : float)`](#void-add_capamount-float)                            |
| | | |
| void   | [`drain()`](#void-drain)                                                          |
| void   | [`restore()`](#void-restore)                                                      |

### Signals
| Signal                                                                                     |
|:-----------------------------------------------------------------------------------------: |
| [`update_max_stamina(cap : float, max : float)`](#update_max_staminacap-float-max-float)   |
| [`update_cur_stamina(cap : float, cur : float)`](#update_cur_staminacap-float-cur-float_1) |
| [`update_stamina_drained(drained : bool)`](#update_stamina_draineddrained-bool_1)          |

### Property Descriptions

#### `float` - `cap_stamina`
- The absolute maximum stamina the player can have.
- This is different from `max_stamina` because `max_stamina` fluctuates often from digging, items, and abilities.
- This is denoted by the entire stamina bar (black, yellow, and green).

#### `float` - `max_stamina`
- The current maximum usable stamina the player has.
- This fluctuates often, most notably from digging.
- This is denoted by the yellow and green sections of the stamina bar.

#### `float` - `cur_stamina`
- The current usable stamina the player has.
- This is used for actions like sprinting.
- This is denoted by the green section of the stamina bar.

#### `float` - `sprint_drain_speed`
- How fast the player's stamina drains while sprinting.

#### `float` - `regen_speed`
- How quickly the player's stamina regenerates when not sprinting.

#### `bool` - `stamina_drained`
- Whether the player's stamina has been drained.
- When the player's stamina is drained, they cannot mine or sprint.
- If the player's stamina is drained, the yellow and green sections of the stamina bar appear red.

### Method Descriptions

#### `void` - `update(delta : float, draining : bool)`
- Updates the player's passive stamina.
- Regenerates if no stamina is being used, drains when sprinting.
- Keeps track of whether stamina has been drained or not.

#### `void` - `add_cur(amount : float)`
- Adds `amount` to the player's current stamina.
- Despite the name being "add," this function is used for both addition and subtraction.

#### `void` - `add_max(amount : float)`
- Adds `amount` to the player's maximum stamina.
- Despite the name being "add," this function is used for both addition and subtraction.

#### `void` - `add_cap(amount : float)`
- Adds `amount` to the player's stamina cap.
- Despite the name being "add," this function is used for both addition and subtraction.

#### `void` - `drain()`
- Sets `stamina_drained` to true.
- Also sets `current_stamina` to 0.0.

#### `void` - `restore()`
- Sets `stamina_drained` to false.
- Also sets `current_stamina` to `max_stamina`.

### Signal Descriptions

#### `update_max_stamina(cap : float, max : float)`
- Signals an update the maximum stamina.
- For the player, this updates the HUD.

#### `update_cur_stamina(cap : float, cur : float)`
- Signals an update to the current stamina.
- For the player, this updates the HUD.

#### `update_stamina_drained(drained : bool)`
- Signals an update to the state of drained stamina.
- For the player, this updates the HUD.









## Movement Component

The movement component is of class `MovementComponent` and handles the player's velocity.

### Properties

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

### Methods

| Return | Name                                                                              |
| :----- | :-------------------------------------------------------------------------------- |
| void   | [`init(_body : CharacterBody2D)`](#void-init_body-characterbody2d)            |
| void   | [`update(delta : float, is_jumping : bool, move_dir : float, is_sprinting : bool, can_sprint : bool)`](#void-updatedelta-float-is_jumping-bool-move_dir-float-is_sprinting-bool-can_sprint-bool) |

### Property Descriptions

#### `CharacterBody2D` - `body`
- The body that velocity is applied to,

#### `float` - `walk_move_speed`
- How quickly the player moves when walking. 

#### `float` - `sprint_speed_multiplier`
- The multiplier applied to the player's movement speed when sprinting.

#### `float` - `acc`
- How quickly the player accelerates.

#### `float` - `dec`
- How quickly the player decelerates.

#### `float` - `jump_velocity`
- How strong the player's jump is.

#### `float` - `coyote_time_max`
- "Coyote time" is a grace period after walking off a ledge where a player can still jump. 

### Method Descriptions

#### `void` - `init(_body : CharacterBody2D)`
- Assigns a passed `CharacterBody2D` as the body this component will manipulate.

#### `void` - `update(delta : float, is_jumping : bool, move_dir : float, is_sprinting : bool, can_sprint : bool)`
- Applies gravity on the player.
- Checks and updates for coyote time.
- Applies jumping velocity.
- Applies horizontal velocity.









## Digging Component

The digging component is of class `DiggingComponent` and handles the player's digging state.

### Properties

| Type     | Name                                               | Default |
| :------- | :------------------------------------------------- | :------ |
| bool     | [`is_digging`](#bool-is_digging)                   | false   |
| float    | [`dig_timer`](#float-dig_timer)                    | 0.0     |
| float    | [`dig_duration`](#float-dig_duration)              | 10.0    |
| Vector2i | [`dig_target_coords`](#vector2i-dig_target_coords) | N/A     |

### Methods

| Return | Name                                                                              |
| :----- | :-------------------------------------------------------------------------------- |
| void   | [`determine_dig_state(delta : float, can_dig : bool, target_coords : Vector2i, player_coords : Vector2i, target_cell_id : int, cur_tool)`]() |

### Signals
| Signal                                                                                                             |
|:-----------------------------------------------------------------------------------------------------------------: |
| [`dig_overlay_set_frame(coords : Vector2i, progress : int)`](#dig_overlay_set_framecoords-vector2i-progress-int)   |
| [`clear_dig_overlay(coords : Vector2i)`](#clear_dig_overlaycoords-vector2i)                                        |
| [`dig_complete(coords : Vector2i)`](#dig_completecoords-vector2i)                                                  |
| [`update_max_stamina(amount : float)`](#update_max_staminaamount-float)                                            |

### Property Descriptions

#### `bool` - `is_digging`
- Whether the player is currently digging.

#### `float` - `dig_timer`
- How long the player has been digging the current cell.

#### `float` - `dig_duration`
- How long it takes to fully mine the current cell.

#### `Vector2i` - `dig_target_pos`
- The position of the target cell in TileMapLayer coordinates.

### Method Descriptions

#### `void` - `determine_dig_state(delta : float, can_dig : bool, target_coords : Vector2i, player_coords : Vector2i, target_cell_id : int, cur_tool)`
- Updates the current digging state the player is in.
- Will prevent digging if the player is out of stamina.

### Signal Descriptions

#### `dig_overlay_set_frame(coords : Vector2i, progress : int)`
- Sends out the signal to update the frame dig overlay at `coords` to frame `progress`.

#### `clear_dig_overlay(coords : Vector2i)`
- Sends out the signal to erase the cell at `coords`.

#### `dig_complete(coords : Vector2i)`
- Sends out the signal that a successful dig was preformed at `coords`.

#### `update_max_stamina(amount : float)`
- Sends out the signal to reduce the player's maximum stamina after mining a cell.