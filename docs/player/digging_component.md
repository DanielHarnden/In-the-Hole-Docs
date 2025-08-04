# Digging Component

The digging component is of class `DiggingComponent` and handles the player's digging state.

## Methods

| Return | Name                                                                              |
| :----- | :-------------------------------------------------------------------------------- |
| void   | [`determine_dig_state(delta : float, can_dig : bool, target_coords : Vector2i, player_coords : Vector2i, target_cell_id : int, cur_tool, terrain : TileMapLayer)`](#void-determine_dig_statedelta-float-can_dig-bool-target_coords-vector2i-player_coords-vector2i-target_cell_id-int-cur_tool-terrain-tilemaplayer) |

## Signals
| Signal                                                                                                             |
|:-----------------------------------------------------------------------------------------------------------------: |
| [`dig_overlay_set_frame(coords : Vector2i, progress : int)`](#dig_overlay_set_framecoords-vector2i-progress-int)   |
| [`clear_dig_overlay(coords : Vector2i)`](#clear_dig_overlaycoords-vector2i)                                        |
| [`dig_complete(coords : Vector2i)`](#dig_completecoords-vector2i)                                                  |
| [`update_max_stamina(amount : float)`](#update_max_staminaamount-float)                                            |

## Method Descriptions

### `void` - `determine_dig_state(delta : float, can_dig : bool, target_coords : Vector2i, player_coords : Vector2i, target_cell_id : int, cur_tool, terrain : TileMapLayer)`
- Updates the current digging state the player is in.
- Will prevent digging if the player is out of stamina.

## Signal Descriptions

### `dig_overlay_set_frame(coords : Vector2i, progress : int)`
- Sends out the signal to update the frame dig overlay at `coords` to frame `progress`.

### `clear_dig_overlay(coords : Vector2i)`
- Sends out the signal to clear the digging animation cell at `coords`.

### `dig_complete(coords : Vector2i)`
- Sends out the signal that a successful dig was preformed at `coords`.

### `update_max_stamina(amount : float)`
- Sends out the signal to reduce the player's maximum stamina after mining a cell.