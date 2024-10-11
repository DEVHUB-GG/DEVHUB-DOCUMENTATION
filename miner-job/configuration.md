# 🛠️ Configuration

**configs/server.lua**

The `server.lua` file contains settings for how the menu is accessed in-game.

```lua
-- Config.OpenMenuOption can be either "command" or "item".
-- If set to "item", the menu will open upon using an item.
-- If set to "command", the menu will open through a command.
Config.OpenMenuOption = "command" -- Example assignment, change as needed.

-- Config.MenuCommand is the command used to open the menu.
-- This is only used if Config.OpenMenuOption is set to "command".
Config.MenuCommand = "battle" -- Example assignment, change as needed.

-- Config.MenuItem is the item used to open the menu.
-- This is only used if Config.OpenMenuOption is set to "item".
Config.MenuItem = "battle_creator" -- Example assignment, change as needed.
```

* **Config.OpenMenuOption:** Determines whether the menu opens via a command or an item.
  * Options: `"command"`, `"item"`
* **Config.MenuCommand:** The command used to open the menu (only applicable if `Config.OpenMenuOption` is set to `"command"`).
* **Config.MenuItem:** The item used to open the menu (only applicable if `Config.OpenMenuOption` is set to `"item"`).

**shared.lua**

In the `shared.lua` file, you can customize the language settings for various script elements. The keys on the left should not be altered, but you can change the corresponding values on the right to suit your preferences. Ensure that the `${value}` format remains unchanged.

{% code title="shared.lua" %}
```lua
-- Language Configuration
-- Change the value (right side) as needed
-- Do not change the key (left side)
-- Maintain the ${value} format
Shared.Lang = {
    ["neons"] = "Neons",
    ["neon2"] = "Neon color: ${neon}",
    ['Neons'] = "Neons",
    ['Headlights'] = "Headlights",
    ['ChipTuning'] = "Chip tuning",
    ['Stancer'] = "Stancer",
    ['Program'] = "Program",
    ['Off'] = "Off",
    ['PopsAndBangs'] = "Pops and bangs",
    ['ALS'] = "ALS",
    ['Semi'] = "Semi",
    ['On'] = "On",
    ['VehicleTrail'] = "Vehicle Trail",
    ['NoPresetsFound'] = "No presets found",
    ['NewPreset'] = "New Preset",
    ['Presets'] = "Presets",
    ['Cancel'] = "Cancel",
    ['Save'] = "Save",
    ['PresetName'] = "Give a name to your preset",
    ['Time'] = "Time",
    ['Color'] = "Color",
    ['Active'] = "Active",
    ['HeadlightsStatus'] = "Headlights Status: ",
    ['ActivePreset'] = "Active Preset: ",
    ['Disable'] = "Disable",
    ['Apply'] = "Apply",
    ['Presets'] = "Presets",
    ['Success'] = "Success",
    ['PresetDeleted'] = "Preset Deleted",
    ['PresetUpdated'] = "Preset Updated",
    ['PresetSaved'] = "Preset Saved",
    ['NeonsStatus'] = "Neons Status: ",
    ['StancerStatus'] = "Stancer status: ",
    ['ClearAll'] = "Clear all",
    ['SettingsCleared'] = "Settings cleared",
}

```
{% endcode %}

**client.lua**

In the `client.lua` file, you can enable or disable the stancer optimization feature by setting the `Config.StancerOptimalization` variable to `true` or `false`.

{% code title="client.lua" %}
```lua
-- Stancer Optimization Configuration
Config.StancerOptimalization = false
```
{% endcode %}
