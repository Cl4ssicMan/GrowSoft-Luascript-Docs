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

TileDataProperties = {
    TILE_DATA_TYPE_SEED_FRUITS_COUNT = 0
};

local tree_fruits = tile:getTileData(TileDataProperties.TILE_DATA_TYPE_SEED_FRUITS_COUNT) -- Get tile property

print("Tree fruit count is: " .. tostring(tree_fruits))

tile:setTileDataInt(TileDataProperties.TILE_DATA_TYPE_SEED_FRUITS_COUNT, 1) -- Change tile fruits to 1

world:updateTile(tile) -- Update tile so it displays the new data in-game, otherwise will require re-entering world
```
---
