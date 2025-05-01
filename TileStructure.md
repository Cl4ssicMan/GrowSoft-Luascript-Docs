## Tile Structure
```lua
getTileForeground()
getTileBackground()
setTileForeground(tile, id, 0, avatar) (maybe wants world:)
setTileBackground(tile, id, 0, avatar) (..)
**
Info About above:

The parameter boolean (optional, default 0) (number 0 or 1), if its 1 then the tile IS NOT placed in the world, only placed to players visually until they re-enter the world.
Avatar is optional here, if you specify it then the tile will visually update only for that person, otherwise for everyone
**
getTiles() - array of all tiles
getTilesByActionType(actiontype)
```
---
