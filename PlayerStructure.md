## Player Data Structure:

Getting the player data, usually is used within a function.
```lua
player:getGems() -- Returns the player's gems count.
player:removeGems(amount, arg1, arg2) -- Removes gems from the player.
player:addGems(amount, arg1, arg2) -- Adds gems to the player.
player:onConsoleMessage(message) -- Sends a console message to the player.
player:onTalkBubble(player:getNetID(), message, [0 or 1]) -- Sends a talk bubble message to the player.
player:onDialogRequest(dialog) -- Sends a dialog request to the player.
player:getNetID() -- Returns the player's net ID.
player:playAudio("audio.wav") -- Plays an audio for the player.
player:getInventorySize() -- Returns the player's inventory size.
player:isMaxInventorySpace() -- Returns if the player's inventory is full.
player:upgradeInventorySpace(amount) -- Upgrades the player's inventory space.
player:onStorePurchaseResult() -- Sends a store purchase result to the player.
player:getUserID() -- Returns the player's user ID.
player:getCoins() -- Returns the player's coins count.
player:removeCoins(amount, arg1) -- Removes coins from the player.
player:getItemAmount(itemID) -- Returns the player's item amount.
player:changeItem(itemID, amount, arg1) -- Changes the player's item amount.
player:onGrow4GoodDonate() -- Fires Grow4GoodDonate Event.
player:onRedeemMenu() -- Sends a redeem menu to the player.
player:enterWorld(worldName, "Message") -- Enters the specified world.
player:getWorldName() -- Returns the player's world name.
player:onTextOverlay("text") -- Sends a text overlay to the player.
player:getCleanName() -- Returns the player's clean name.
player:getCleanName():lower() -- Returns the player's clean name in lowercase.
player:lower() -- Returns the player's name in lowercase.
player:hasRole(role) -- Returns if the player has the specified role.
player:setRole(role) -- Sets the player's role.
player:getMod(playModID) -- Returns the player's mod.
player:addMod(playModID, number) -- Adds a mod to the player.
player:setNextDialogRGBA(255, 255, 255, 255) -- Change color of the dialog's background
player:setNextDialogBorderRGBA(255, 255, 255, 255) -- Change color of the dialog's border
player:resetDialogColor() -- Resets the dialog's color IMPORTANT! IF USING THE ABOVE TWO FUNCTIONS, USE THIS AFTER!
player:getSubscription(subscription) -- Returns the player's specified subscription status.
player:getHomeWorldID() - -Returns Player's Home World ID
player:getOnlineStatus() -- Returns The Online Status
player:getGuildID() -- Returns the Guild ID
player:getTransformProfileButtons() - Returns Player's TransformProfile Buttons
player:getDiscordID() -- Returns the Player's Discord ID
player:getAccountCreationDateStr() -- Returns the Account Creation Date
player:getClassicProfileContent(cat, flags) -- Returns the ClassicProfile Content
player:onTradeScanUI() -- Returns Player's Trade Scans
player:onGrow4GoodUI() -- Returns the Grow4Good UI
player:onGuildNotebookUI() -- Returns The GuildNotebook UI
Extras:
player:onGrowmojiUI()
player:onGrowpassUI()
player:onNotebookUI()
player:onBillboardUI()
player:onPersonalizeWrenchUI()
player:onOnlineStatusUI()
player:onFavItemsUI()
player:onCoinsBankUI()
player:onUnlinkDiscordUI()
player:onLinkDiscordUI()
player:onClothesUI(player) -- player is the Target player (whos content will be shown) (not required)
player:onAchievementsUI(player) -- player is the Target player (whos content will be shown) (not required)
player:onTitlesUI(player) -- player is the Target player (whos content will be shown) (not required)
player:onWrenchIconsUI(player) -- player is the Target player (whos content will be shown) (not required)
player:onNameIconsUI(player) -- player is the Target player (whos content will be shown) (not required)
player:onVouchersUI()
player:onMentorshipUI()
player:onBackpackUI(player) -- player is the Target player (whos content will be shown) (not required)
player:getClothingItemID()
player:getUnlockedAchievementsCount()
player:getAchievementsCount()
player:getBackpackUsedSize()
player:getCountry() - returns player’s country letter (string), works only for online player’s
player:getPlatform() - returns player’s platform ID (string), works only for online player’s 0,1,1 and 0 is windows. 4 is android. 1 is ios. 2 is macos
***
player:sendVariant() - send any type of variant packet, examples:

player:sendVariant({"OnTalkBubble", player:getNetID(), “Hello”, 0, 0})
player:sendVariant({“OnConsoleMessage”, “Hello”})
player:sendVariant({“OnConsoleMessage”, “Hello”}, delay, netid)
***
player:getClothingItemID(PlayerClothes.CHANGETHIS)
***
player:getInventoryItems()
player:sendAction("action|play_sfx\nfile|audio/blabla.mp3\ndelayMS|0") -- This is Growtopia default format
--There are many other actions as well that Growtopia uses.

Example:
    local inventory_items = player:getInventoryItems()
    for i = 1, #inventory_items do
        local inventory_item = inventory_items[i]
        print(inventory_item:getItemID())
        print(inventory_item:getItemCount())
    end
***
player:getWorld() -- returns the current world, the player is in, and return nil if the player isnt in a world
player:disconnect() -- Disconnects the player
PlayerStats.ConsumablesUsed -- Returns the player's consumables used.
getPlayerByName(name) -- Returns the player data table by name.
getAutofarm() -- Returns the player's autofarm.
setSlots(slotAmount) -- Sets the player's slots.
```



---
