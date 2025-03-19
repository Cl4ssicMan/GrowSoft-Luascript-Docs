# Lua Scripting Documentation For GrowSoft.

-Document By Gnome

-GrowSoft Creator: Sebia

This documentation explains how to create and register custom commands, handle player dialogs, and manage interactions in your Lua scripting environment in GrowSoft.

---

## Command Data Structure
To create a custom command, define a command data table with the following fields:
- `command`: The name of the command.
- `roleRequired`: The role required to use the command.
- `description`: A description of the command.

```lua
Example:
local nameCommandData = {
    command = "commandName", <-- This is the command that players will type in the game as in /commandName
    roleRequired = Roles.ROLE_NONE, <--- These roles are defined in the game's API as ROLE_NONE = 0, ROLE_VIP = 1, ROLE_SUPER_VIP = 2, ROLE_MODERATOR = 3, ROLE_ADMIN = 4, ROLE_COMMUNITY_MANAGER = 5, ROLE_CREATOR = 6, ROLE_GOD = 7, ROLE_DEVELOPER = 51
    description = "Description of the command" <-- This is the description that will be displayed on usage.
}
```

---

## Registering a Command
Register the command using `registerLuaCommand`.

```lua
Example:
registerLuaCommand(commandnameCommandData) <-- This is the command data table that you defined in the previous step.
```

---

## Handling Player Commands
Use `onPlayerCommandCallback` to handle player commands.

```lua
Example:
onPlayerCommandCallback(function(world, player, fullCommand) <-- This is the function that will be called when the command is used.
    local command = fullCommand:match("^(%S+)%s*(.*)") <-- This is used to extract the command from the full command.
    if command == nameCommandData.command then <-- This checks if the command matches the registered command.
        oncommandNameMenu(player, message) <-- This is the function that will be called when the command is used.
        return true
    end
    return false
end)
```

---

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

## onDialogRequest String Syntax
The `onDialogRequest` function uses a custom string syntax to define the layout and content of dialogs. Below is a comprehensive list of available commands and their usage:

### Basic Commands:
- `set_default_color|Color`: Sets the default dialog text color.
- `set_border_color|r,g,b,a|`: Sets the border color of the dialog.
- `set_bg_color|r,g,b,a|`: Sets the background color of the dialog.
- `set_custom_spacing|x:value;y:value|`: Adds custom spacing between elements.
- `add_custom_break|`: Adds a line break.
- `start_custom_tabs|`: Starts custom tabs.
- `end_custom_tabs|`: Ends custom tabs.

### UI Elements:
- `add_item_picker|name|message|placeholder|`: Adds an item picker.
- `add_player_info|name|level|exp|expRequired|`: Displays player information.
- `add_checkbox|name|message|checked|`: Adds a checkbox.
- `add_friend_image_label_button|name|label|texture_path|size|texture_x|texture_y|`: Adds a button with a friend image.
- `add_smalltext|message|`: Adds small text.
- `add_button_with_icon|big/small|label|flags|iconID|hoverNumber|`: Adds a button with an icon.
- `add_label_with_icon|size|message|alignment|iconID|`: Adds a label with an icon.
- `add_text_input|name|message|defaultInput|length|`: Adds a text input field.
- `add_spacer|size|`: Adds a spacer.
- `add_textbox|message|`: Adds a text box.
- `add_quick_exit|`: Adds a quick exit button.

### Advanced Commands:
- `embed_data|embed|data|`: Embeds data into the dialog.
- `add_progress_bar|name|size|text|current|max|color|`: Adds a progress bar.
- `add_image_button|name|imagePath|flags|open|label|`: Adds a button with an image.
- `add_tab_button|name|label|iconPath|x|y|`: Adds a tab button.
- `add_banner|imagePath|x|y|`: Adds a banner.
- `add_big_banner|imagePath|x|y|text|`: Adds a big banner with text.

### Additional Commands:
- `add_dual_layer_icon_label|size|message|alignment|iconID|background|foreground|size|toggle|`: Adds a dual-layer icon label.
  - Example: `add_dual_layer_icon_label|big|Welcome|left|6016|background|foreground|32|1|`
- `add_seed_color_icons|itemId|`: Adds seed color icons for a specific item.
  - Example: `add_seed_color_icons|112|`
- `add_label_with_icon_button|size|message|alignment|iconID|buttonName|`: Adds a label with an icon and a button.
  - Example: `add_label_with_icon_button|big|Welcome|left|6016|btn1|`
- `add_button_with_icon|btnName|text|option|itemID|unkVal|`: Adds a button with an icon and other specified options.
  - Example: `add_button_with_icon|btn1|Click Me|option|112|0|`
- `add_button_with_icon|btnName|progress|itemID|`: Adds a button with an icon and a progress indicator.
  - Example: `add_button_with_icon|btn1|50%|112|`
- `add_button_with_icon|btnName|underText|itemID|`: Adds a button with an icon and under text.
  - Example: `add_button_with_icon|btn1|Under Text|112|`
- `add_button_with_icon|btnName|itemID|`: Adds a button with an icon for a claimed item.
  - Example: `add_button_with_icon|btn1|112|`
- `add_label|size|message|alignment|`: Adds a label with specified size and message.
  - Example: `add_label|big|Welcome|left|`
- `add_button_with_icon|name|text|staticBlueFrame[is_count_label][no_padding_x]|itemID|left|` : Adds a static frame button.
  - Example: `add_button_with_icon|hello|Hello There|staticBlueFrame|242|left|`
- `add_small_font_button|name|button|noflags|0|0|`: Adds a small font button.
  - Example: `add_small_font_button|btn1|Click Me|noflags|0|0|`
- `add_button|name|button|noflags|0|0|`: Adds a button.
  - Example: `add_button|btn1|Click Me|noflags|0|0|`
- `add_button|name|button|off|0|0|`: Adds a button in an off state.
  - Example: `add_button|btn1|Click Me|off|0|0|`
- `add_small_font_button|name|button|off|0|0|`: Adds a small font button in an off state.
  - Example: `add_small_font_button|btn1|Click Me|off|0|0|`
- `add_custom_button|name|option|`: Adds a custom button.
  - Example: `add_custom_button|btn1|option|`
- `add_custom_label|option1|option2|`: Adds a custom label with options.
  - Example: `add_custom_label|option1|option2|`
- `add_custom_spacer|x:value|`: Adds a custom spacer with specified width.
  - Example: `add_custom_spacer|x:10|`
- `add_custom_textbox|text|size:value|`: Adds a custom textbox with specified size.
  - Example: `add_custom_textbox|Welcome|size:small|`
- `add_achieve_button|achName|achToGet|achID|unk|`: Adds an achievement button.
  - Example: `add_achieve_button|ach1|Get 100 points|1|0|`
- `add_community_button|button|btnName|noflags|0|0|`: Adds a community button.
  - Example: `add_community_button|btn1|Community|noflags|0|0|`
- `add_cmmnty_ft_wrld_bttn|worldName|ownerName|worldName|`: Adds a community feature world button.
  - Example: `add_cmmnty_ft_wrld_bttn|World1|Owner1|World1|`
- `add_cmmnty_wotd_bttn|top|worldName|ownerName|imagePath|x|y|worldName|`: Adds a community world of the day button.
  - Example: `add_cmmnty_wotd_bttn|1|World1|Owner1|image.png|0|0|World1|`
- `community_hub_type|hubType|`: Sets the community hub type.
  - Example: `community_hub_type|1|`
- `enable_tabs|enable|`: Enables or disables tabs.
  - Example: `enable_tabs|1|`
- `add_tab_button|btn|name|iconPath|x|y|`: Adds a tab button.
  - Example: `add_tab_button|btn1|Tab1|icon.png|0|0|`
- `add_banner|imagePath|x|y|`: Adds a banner.
  - Example: `add_banner|banner.png|0|0|`
- `add_big_banner|imagePath|x|y|text|`: Adds a big banner with text.
  - Example: `add_big_banner|banner.png|0|0|Welcome|`

---


### 🚨 IMPORTANT! 🚨
arg1 and arg2's are usually either 0 or 1! BUT NOT ALWAYS WHEN LOOKING AT THE DOCS BELOW!!



### Item Data Structure:
```lua
getItem() -- Returns the item data table.
getItem():setPrice() -- Sets the price of the item desired.
getItem():isObtainable() -- Returns if the item is obtainable.
getItem():getNetID() -- Returns the item's net ID.
getItem():getName() -- Returns the item's name.
```
Examples:
```lua
getItem(itemID):setPrice(price) <-- The itemID is the ID of the item and the price is the price of the item.
getItem(itemID):isObtainable() <-- See if the item is obtainable.
getItem(itemID):getNetID() <-- Get the item's net ID.
getItem(itemID):getName() <-- Get the item's name.
getItem(itemID):getName():lower() <-- Get the item's name in lowercase.
getItem(itemID):getName():lower():find("type", arg1, true/false) <-- Find the item's name and type in lowercase.
getItemsCount() -- Returns the items count.
getItemAmount(itemID) -- Returns the item amount.
itemCount() -- Returns the item count.
```
---

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
player:getPlatform() - returns player’s platform ID (string), works only for online player’s
***
player:sendVariant() - send any type of variant packet, examples:

player:sendVariant({"OnTalkBubble", player:getNetID(), “Hello”, 0, 0})
player:sendVariant({“OnConsoleMessage”, “Hello”})
player:sendVariant({“OnConsoleMessage”, “Hello”}, delay, netid)
***
PlayerStats.ConsumablesUsed -- Returns the player's consumables used.
getPlayerByName(name) -- Returns the player data table by name.
getAutofarm() -- Returns the player's autofarm.
setSlots(slotAmount) -- Sets the player's slots.
```



---

## Server Data Structure:
```lua
getRequiredEvent() -- Returns the required event.
isVoucher() -- Returns if the item is a voucher.
getCurrentServerDailyEvent() -- Returns the current server's daily event.
getServerCurrentEvent() -- Returns the current server's event.
getItemID() -- Returns the item's ID.
getTitle() -- Returns the title.
getAmount() -- Returns the amount.
getIOTMItem() -- Returns the IOTM item.
makePurchaseItem(amount) -- Makes a purchase of the item. THIS IS KEPT IN THE SERVER NOT LUA!!!
onStorePurchaseResult() -- Sends a store purchase result to the player. THIS IS KEPT IN THE SERVER NOT LUA!!!
getPrice() -- Returns the price of the item.
isGrowtoken() -- Returns if the item is a Growtoken.
addDailyOfferPurchased(player:getUserID(), changethis:getItemID()) -- Adds a daily offer purchased.
getCategory() -- Returns the category of the item.
getRealGTItemsCount() -- Returns the real GT items count.
getTexture() -- Returns the texture.
getEventOffers() -- Returns the event offers.
getActiveDailyOffers() -- Returns the active daily offers.
onPurchaseItem(player, item, true/false) -- Firing the purchase item event.
getDescription() -- Returns the description.
getItemsDescription() -- Returns the items description.
isRPC() -- Returns if the item is an RPC.
getTexturePosX() -- Returns the texture position X.
getTexturePosY() -- Returns the texture position Y.
getTopPlayerByBalance() -- Returns the top player by balance.
getTopWorldByVisitors() -- Returns the top world by visitors.
onPurchaseItemReq(player, itemID) -- Firing the purchase item request event.
getStoreItems() -- Returns the store items.
getEnumItem("ITEM_[NAME]") -- Returns the item by enum name.
getID() -- Returns the ID.
registerLuaPlaymod(PLAYMODDATA) -- Registers the Lua playmod.
addMod(MODID, amount) -- Adds a mod.
reloadScripts() -- Reloads the Lua scripts.
getTileID() -- Returns the tile ID.
tile:getPosX() -- Returns the tile's position X.
tile:getPosY() -- Returns the tile's position Y.
resetColor(replacethis) -- Resets the color.
loadDataFromServer(data) -- Loads data from the server.
loadData() -- Loads data.
saveDataToServer(data, data2)
onAutoSaveRequest(function()) -- Fires the auto save request.
getExpireTime() - Returns the Expire Time

data["selection"] -- Returns the selection.
data["item"] -- Returns the item.
data["buttonClicked"] -- Returns the button clicked.
data["dialog_name"] -- Returns the dialog name.
```
Examples:
```lua
local greenBeerModData = { <---- THIS EXAMPLE IS ALREADY IN YOUR LUASCRIPTS IN YOUR SERVER!
    modID = -1100, -- Ensure it's unique and negative
    modName = "Envious",
    onAddMessage = "It ain't easy being you.",
    onRemoveMessage = "Healthy color restored.",
    iconID = getEnumItem("ITEM_GREEN_BEER"):getID(),
    changeSkin = {52, 235, 107, 255}, -- RGBA
    modState = {StateFlags.STATE_DOUBLE_JUMP, StateFlags.STATE_SHINING},
    changeMovementSpeed = 500,
    changeAcceleration = 0,
    changeGravity = 0,
    changePunchStrength = 0,
    changeBuildRange = 0,
    changePunchRange = 0,
    changeWaterMovementSpeed = 0
}

registerLuaPlaymod(greenBeerModData) <-- This is the playmod data table that you defined in the previous step.
```

---

## World Data Structure:
```lua
getOwner() -- Returns the world's owner.
getName() -- Returns the world's Owner's name.
getWorldName() -- Returns the world's name.
enterWorld(WorldName, "Message") -- Enters the specified world.
useItemEffect(player:getNetID(), itemID, replacethis:getNetID(), arg1) -- Uses the item effect.
updateClothing(player) -- Updates the player's clothing.
spawnGems(x, y, amount) -- Spawns gems.
useItemEffect(player:getNetID(), itemID, arg1, replacethis)
world:getVisiblePlayersCount()
world:isGameActive() - Returns if Game is Active
world:onGameWinHighestScore() - Returns The Game's Highest Win Score
```


Happy Coding! -Gnome
