## World Data Structure:
```lua
getOwner() -- Returns the world's owner.
getName() -- Returns the world's Owner's name.
getWorldName() -- Returns the world's name.
enterWorld(WorldName, "Message") -- Enters the specified world.
useItemEffect(player:getNetID(), itemID, replacethis:getNetID(), arg1) -- Uses the item effect.
updateClothing(player) -- Updates the player's clothing.
spawnGems(x, y, amount, player) -- Spawns gems.
useItemEffect(player:getNetID(), itemID, arg1, replacethis)
world:getVisiblePlayersCount()
world:isGameActive() - Returns if Game is Active
world:onGameWinHighestScore() - Returns The Game's Highest Win Score
world:onCreateChatBubble(x, y, text, netid)
world:onCreateExplosion(x, y, radius, power)
world:addXP(player, amount)
world:setPlayerPosition(player, x, y) -- teleport a player
world:getDroppedItems() - returns list of all dropped items
world:getTileDroppedItems(tile) - returns list of all dropped items in tile
world:removeDroppedItem(DropUID) -- Removes the dropped item
world:getID() -- Returns The World's ID
getWorldSizeX() --Get the world size horizontally
getWorldSizeY() --Get the world size vertically
getTile(x, y)
```

---
