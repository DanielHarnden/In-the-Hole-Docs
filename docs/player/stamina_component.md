# Stamina Component

The stamina component is of class `StaminaComponent` and handles the player's stamina state. It provides functions to update the stamina cap, maximum stamina, and current stamina.

The stamina component also manages the player's sprinting state.

## Properties

| Type  | Name                                              | Default                             |
| :---- | :------------------------------------------------ | :---------------------------------- |
| float | [`cap_stamina`](#float-cap_stamina)               | 100.0                               |
| float | [`max_stamina`](#float-max_stamina)               | [`cap_stamina`](#float-cap_stamina) |
| float | [`cur_stamina`](#float-cur_stamina)               | [`cap_stamina`](#float-cap_stamina) |
| | | |
| float | [`sprint_drain_speed`](#float-sprint_drain_speed) | 10.0                                |
| float | [`regen_speed`](#float-regen_speed)               | 5.0                                 |
| bool  | [`stamina_drained`](#bool-stamina_drained)        | false                               |

## Methods

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

## Signals
| Signal                                                                                     |
|:-----------------------------------------------------------------------------------------: |
| [`update_max_stamina(cap : float, max : float)`](#update_max_staminacap-float-max-float)   |
| [`update_cur_stamina(cap : float, cur : float)`](#update_cur_staminacap-float-cur-float_1) |
| [`update_stamina_drained(drained : bool)`](#update_stamina_draineddrained-bool_1)          |

## Property Descriptions

### `float` - `cap_stamina`
- The absolute maximum stamina the player can have.
- This is different from `max_stamina` because `max_stamina` fluctuates often from digging, items, and abilities.
- This is denoted by the entire stamina bar (black, yellow, and green).

### `float` - `max_stamina`
- The current maximum usable stamina the player has.
- This fluctuates often, most notably from digging.
- This is denoted by the yellow and green sections of the stamina bar.

### `float` - `cur_stamina`
- The current usable stamina the player has.
- This is used for actions like sprinting.
- This is denoted by the green section of the stamina bar.

### `float` - `sprint_drain_speed`
- How fast the player's stamina drains while sprinting.

### `float` - `regen_speed`
- How quickly the player's stamina regenerates when not sprinting.

### `bool` - `stamina_drained`
- Whether the player's stamina has been drained.
- When the player's stamina is drained, they cannot mine or sprint.
- If the player's stamina is drained, the yellow and green sections of the stamina bar appear red.

## Method Descriptions

### `void` - `update(delta : float, draining : bool)`
- Updates the player's passive stamina.
- Regenerates if no stamina is being used, drains when sprinting.
- Keeps track of whether stamina has been drained or not.

### `void` - `add_cur(amount : float)`
- Adds `amount` to the player's current stamina.
- Despite the name being "add," this function is used for both addition and subtraction.

### `void` - `add_max(amount : float)`
- Adds `amount` to the player's maximum stamina.
- Despite the name being "add," this function is used for both addition and subtraction.

### `void` - `add_cap(amount : float)`
- Adds `amount` to the player's stamina cap.
- Despite the name being "add," this function is used for both addition and subtraction.

### `void` - `drain()`
- Sets `stamina_drained` to true.
- Also sets `current_stamina` to 0.0.

### `void` - `restore()`
- Sets `stamina_drained` to false.
- Also sets `current_stamina` to `max_stamina`.

## Signal Descriptions

### `update_max_stamina(cap : float, max : float)`
- Signals an update the maximum stamina.
- For the player, this updates the HUD.

### `update_cur_stamina(cap : float, cur : float)`
- Signals an update to the current stamina.
- For the player, this updates the HUD.

### `update_stamina_drained(drained : bool)`
- Signals an update to the state of drained stamina.
- For the player, this updates the HUD.