Demo 5 : hud

A typical FPS game has a user interface, with a HUD that displays informations about the player, like life and ammo state. It is also quite common that the player has an inventory of weapons, which can be cycled with hotkeys.
This demo shows how to get signals from the controller's data model to get its current state. It also implements a rudimentary weapon inventory which remembers the current weapon state of each weapon. By pressing keys 1-6, the controller selects a different weapon and updates its ammo state as well as the attributes of the maximum ammo and cartridge capacity.
It is not implemented by default in the controller because it can be specific to only some kinds of gameplay (ww2 games, hl games), where other kinds of gameplay need a different implementation of weapon switch (halo with only 2 weapons at a time, or non shooting 1st person game with a totally different gameplay and "weapons" are customized for other kinds of behavior like tools).

The current weapon selection is organized by racks of weapons, like in half life series. Pressing "1" cycles through the first rack of weapons, composed of laser beam weapons. "2" cycles through a rack of instant bullet weapons. 