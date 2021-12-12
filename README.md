## Lua Duel AI

This is the documentation for the [Lua](https://www.lua.org) [Drool Links Saliva](https://github.com/BullyWiiPlaza/JDuel-Links-Bot) duel bot AI which is compatible with PvE and PvP duels.

### Executing Lua Scripts

Lua scripts can be executed directly through the Drool Links Saliva mod menu GUI.

## API

Lua is a scripting language which can be edited with a simple text editor. The Drool Links Saliva mod exposes a variety of functions, enums and classes (= user types) for Lua to work with. They will be listed and explained below.

### Functions

* `int get_turn_number()`: Gets the current turn number in the duel
* `duel_phase_t get_current_phase()`: Gets the current duel phase
* `turn_player_t get_turn_player()`: Gets the current turn player
* `void wait_for_input_enabled()`: Waits until the player can perform input again (e.g. when an animation plays)
* `int get_lp(turn_player_t)`: Gets the LP of the specified turn player
* `void log_message(log_message, log_level_t = info)`: Prints a message to the logger with the given log level. By default, the log level is info (if not passed as argument)

### Enums

* `turn_player_t`: An enumeration representing the turn players holding the constant `myself` and `rival`
* `duel_phase_t`: An enumeration representing the duel phases holding the constants `draw`, `standby`, `main_1`, `battle` and `end`
* `log_level_t`: For the `log_message()` function the 2nd parameter may be one of the log level constant of `debug`, `info`, `warning` or `error`.

### User Types

* `duel_card_t`: A class representing a card which has a `card_id`, `card_name` and an `is_face_up` property
* `duel_card_state_t`: A class representing the card state of the entire duel including all players. It has the property `player_card_states` which is a map of `turn_player_t` to `player_card_state_t`.
* `player_card_state_t`: A class representing the cards on the player's side. It has the properties `hand_cards`, `spells_and_traps`, `field_spell`, `main_deck`, `extra_deck`, `graveyard`, `banished` and `monsters`. Besides the `field_spell` property, all other properties are a list of `duel_card_t`. If the `duel_card_t` is non-existent, the value is `nil`.

## Credits

BullyWiiPlaza for designing and documenting the Lua duel API