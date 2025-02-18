---
description: Migrating from version 1 to 2 should not be difficult in any way.
---

# 2️⃣ Migration from v1 to v2

## <mark style="color:yellow;">What Changed in Version 2?</mark>

* **New Folder Structure**: Easier configuration with a `core` folder containing all mechanics and a `modules` folder with files you might want to configure based on your framework.
* **Sound System Customization**: Added the option to change the sound system.
* **Vehicle Keys System Auto-Detection**: The system now automatically detects the vehicle keys system, and allows modification in a easier way.
* **Vehicle Fuel System Auto-Detection**: The system now automatically detects the vehicle fuel system, and allows modification in a easier way..
* **Easier UI Changes**: UI customization has been simplified.

***

## <mark style="color:yellow;">How to Migrate from v1 to v2</mark>

#### File and Folder Mappings

| v1 Location                                                                                | v2 Location           | Notes                                                                                                 |
| ------------------------------------------------------------------------------------------ | --------------------- | ----------------------------------------------------------------------------------------------------- |
| `frameworks/`                                                                              | `modules/frameworks/` | No changes in code, you can copy and paste.                                                           |
| `c.clothing.lua, s.sql.lua`                                                                | `modules/systems/`    | No changes in code, you can copy and paste.                                                           |
| `s.logs.lua`                                                                               | `modules/systems/`    | Changed displayed name from in-game to Steam name.                                                    |
| `/targets`                                                                                 | `modules/systems/`    | Minor changes in `c.custom.lua`, added `Core.AddCoordsToTarget`.                                      |
| `c.ui.lua`                                                                                 | `modules/systems/`    | Added a few options. If you modified this file, it is recommended to compare it with the old version. |
| `/client, /server, /shared, /tests, c.main.lua, s.main.lua, sh.autoDetect.lua, shared.lua` | `/core/`              | Recommended to use the latest files.                                                                  |

***

{% hint style="warning" %}
You no longer have to edit the `Core.SpawnVehicle` function to add your keys or fuel system. The system now detects them automatically.
{% endhint %}

{% content-ref url="vehicle-keys.md" %}
[vehicle-keys.md](vehicle-keys.md)
{% endcontent-ref %}

{% content-ref url="vehicle-fuel.md" %}
[vehicle-fuel.md](vehicle-fuel.md)
{% endcontent-ref %}
