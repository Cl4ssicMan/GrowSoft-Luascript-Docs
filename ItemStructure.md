### Item Data Structure:
```lua
getItem() -- Returns the item data table.
getItem():setPrice() -- Sets the price of the item desired.
getItem():isObtainable() -- Returns if the item is obtainable.
getItem():getNetID() -- Returns the item's net ID.
getItem():getName() -- Returns the item's name.
getActionType() (can be used to check the type of item, for example if its clothing or seed or magplant, fish… basically anything)
getItem(2):getRarity()
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
