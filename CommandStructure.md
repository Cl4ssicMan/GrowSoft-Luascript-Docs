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
