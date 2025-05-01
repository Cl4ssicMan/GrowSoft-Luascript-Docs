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
- `disable_resize|`: Disables automatic dialog resize
- `reset_placement_x|`: Resets placement X

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
- `add_searchable_item_list|data|listType:iconGrid;resultLimit:[amount]|searchFixedName|`: Adds a Searchable Item List.
  - Example: `add_searchable_item_list|data|listType:iconGrid;resultLimit:12|searchFixedName|`
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
