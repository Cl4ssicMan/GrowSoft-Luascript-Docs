## Handling Player Dialogs
Use `onPlayerDialogCallback` to handle player interactions with dialogs.

```lua
Example:
onPlayerDialogCallback(function(world, player, data) <-- This is the function that will be called when a dialog is called.
    if data["dialog_name"] == "name" then <-- This checks if the dialog name matches the expected dialog.
        if not data["buttonClicked"] then return true end <-- This checks if a button was clicked in the dialog.
        if startsWith(data["buttonClicked"], "name") then <-- This checks if a specific button was clicked in the dialog.
            -- Handle item selection and purchase logic here
        end
        return true
    end
    return false
end)
```

Note: The data to get the dialog name and button clicked, is always data["dialog_name"] and data["buttonClicked"] respectively, nothing else, it's a built in function.

---

## PlayerConsumeableCallback
```lua
onPlayerConsumableCallback(function(world, player, tile, clickedPlayer, itemID) <-- THIS IS AN EXAMPLE THAT IS ALREADY IN YOUR LUASCRIPTS!
    if itemID == getEnumItem("ITEM_GREEN_BEER"):getID() then
        if not clickedPlayer then
            player:onTalkBubble(player:getNetID(), "`wMust be used on a person.``", 1)
            return true
        end
        if player:changeItem(itemID, -1, 0) then
            clickedPlayer:addMod(greenBeerModID, 10)
            world:useItemEffect(player:getNetID(), itemID, clickedPlayer:getNetID(), 0)
            player:updateStats(world, PlayerStats.ConsumablesUsed, 1)
            world:updateClothing(player)
            return true
        end
    end
    return false
end)
```

---

## onTileWrenchCallback
```lua
onTileWrenchCallback(function(world, player, tile) <-- THIS IS AN EXAMPLE THAT IS ALREADY IN YOUR LUASCRIPTS!
    if tile:getTileID() == 4358 then -- Sales-Man Standee
        local itemObj = getItem(4358)
        player:onConsoleMessage("You have wrenched " .. itemObj:getName())
        return true
    end
    return false
end)
```
---

## onPlayerLoginCallback
```lua
onPlayerLoginCallback(function(player) <-- THIS IS AN EXAMPLE THAT IS ALREADY IN YOUR LUASCRIPTS!
    player:onConsoleMessage("`9Welcome back to GrowSoft! We're glad to have you!``")
end)
```

---

## onTilePlaceCallback
```lua
onTilePlaceCallback(function(world, player, tile, placingID)
    if placingID == 2 then -- Dirt
        return true -- Block will not be placed at all
    end
    return false
end)
```

---

## onPlayerTick
```lua
onPlayerTick(function(player) -- Gets called every 1000ms for each player
    print(player:getName())
end)
```
---

## onWorldTick
```lua
onWorldTick(function(world) -- Gets called every 100ms for each world
    print(world:getName())
end)
```

---
## onPlayerFirstTimeLoginCallback

```lua
onPlayerFirstTimeLoginCallback(function(player)
    if not player:changeItem(242, 100, 0) then
        player:changeItem(242, 100, 1)
    end
    player:onConsoleMessage("hi")
end)
```

---
## onPlayerEnterWorldCallback
```lua
onPlayerEnterWorldCallback(function(world, player)
    print("Player entered world")
end)
```
---
## onPlayerLeaveWorldCallback
```lua
onPlayerLeaveWorldCallback(function(world, player)
    print(world:getName())
end)
```

---
## onTilePunchCallback
```lua
onTilePunchCallback(function(world, avatar, tile)
    print(tile:getTileID())
    return false -- false does not prevent default action of player breaking tiles, true does (making player unable to break tiles)
end)
```

---

## onPlayerDisconnectCallback
```lua
onPlayerDisconnectCallback(function(player)
    print("Player has disconnected")
end)
```

---
## onPlayerDeathCallBack
```lua
onPlayerDeathCallback(world, player, isRespawn)

isRespawn is true if player respawns, if not true then the player dead from spikes or lava etc...
```

---
## onPlayerDropCallback
```lua
onPlayerDropCallback(world, player, itemID, itemCount)

need to return true or false, return true to make it unable to drop the item, return false if u want the drop to work as usual.
```

---
## onPlayerLevelUPCallback
```lua
onPlayerLevelUPCallback(world, player, levelReached)
```

---
## onPlayerEquipClothingCallback
```lua
onPlayerEquipClothingCallback(world, player, itemID)

need to return true or false, return true to make it unable to equip the item, return false if u want the equip to work as usual.
```

---
## onPlayerUnequipClothingCallback
```lua
onPlayerUnequipClothingCallback(world, player, itemID)

need to return true or false, return true to make it unable to unequip the item, return false if u want the unequip to work as usual.
```

---
## onPlayerPickupItemCallback
```lua
onPlayerPickupItemCallback(world, player, itemID, itemCount)

need to return true or false, return true to make it unable to pickup the item, return false if u want the pickup to work as usual.
```

---
## onPlayerEnterDoorCallback
```lua
onPlayerEnterDoorCallback(world, player, targetWorldName, doorID)

need to return true or false, return true to make it unable to enter the door, return false if u want the enter door to work as usual.
```

---
## onPlayerPlantCallback
```lua
onPlayerPlantCallback(world, player, tile)
```

---
## onPlayerHarvestCallback
```lua
onPlayerHarvestCallback(world, player, tile)
```

---
## onPlayerCatchFishCallback
```lua
onPlayerCatchFishCallback(world, player, itemID, itemCount)
```

---
## onPlayerCrimeCallback
```lua
onPlayerCrimeCallback(world, player, itemID, itemCount)
```

---
## onPlayerSurgeryCallback
```lua
onPlayerSurgeryCallback(world, player, itemID, itemCount)
```

---
## onPlayerKillCallback
```lua
onPlayerKillCallback(world, player, killedPlayer)
```

---
## onPlayerProviderCallback
```lua
onPlayerProviderCallback(world, player, tile, itemID, itemCount)
```

---
## onPlayerHarmonicCallback
```lua
onPlayerHarmonicCallback(world, player, tile, itemID, itemCount)
```

---
## onPlayerGeigerCallback
```lua
onPlayerGeigerCallback(world, player, itemID, itemCount)
```

---
## onPlayerCatchGhostCallback
```lua
onPlayerCatchGhostCallback(world, player, itemID, itemCount)
```

---
## onPlayerXPCallback
```lua
onPlayerXPCallback(world, player, amount)
```

---
## onPlayerFirePutOutCallback
```lua
onPlayerFirePutOutCallback(world, player, tile)
```

---
## onPlayerGemsObtainedCallback
```lua
onPlayerGemsObtainedCallback(world, player, amount)
```
