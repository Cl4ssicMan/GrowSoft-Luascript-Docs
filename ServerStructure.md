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
getServerName() -- returns the server name
getNewsBanner() -- returns the news banner
getNewsBannerDimensions() -- returns the news banner dimensions
getTodaysDate() -- returns the Date
getTodaysEvents() -- returns the Event of that day
getCurrentEventDescription() -- returns the current event's description
getCurrentDailyEventDescription() -- returns the current daily event's description
getCurrentRoleDayDescription() -- returns the current role day's description
addWorldMenuWorld(worldID, displayName, color, priority) -- priority is either 0 or 1. 0 meaning its whown after special worlds like locke, growmines, etc. If its 1 then before them.
--If that addworldmenuworld is called for the same world again, it will replace the older one to reduce issues
removeWorldMenuWorld(worldID)
hideWorldMenuDefaultSpecialWorlds(0/1) -- 1 meaning yes and 0 meaning no
getServerID() -- Returns server ID
getServerPlayers() -- returns server players

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
