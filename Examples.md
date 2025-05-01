# Extra Examples

Added a way to get default item gem drops and xp, depending on how you want to use it there are two different ways:
```lua
local item = getItem(340) -- chandelier
print(item:getGems()) -- shows random amount of gems chandelier would drop
print(item:getXP()) -- shows amount of XP chandelier would give

Second option, if you want to include player buffs to boost the gems or XP such as item effects etc...:

local item = getItem(340) -- chandelier
print(item:getGems(world, player))
print(item:getXP(world, player))
```
