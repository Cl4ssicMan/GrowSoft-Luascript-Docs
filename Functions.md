# Functions

---
Added a way to add buttons in social portal, its made as a callable function to make better support for multiple scripts that add the buttons
```lua
function mySocialPortalButton(world, player)
    print(player:getName())
end

addSocialPortalButton("add_custom_button|button_name_2|image:interface/large/gui_social_c_settings.rttex;image_size:400,260;width:0.19;|\n", mySocialPortalButton)
```
