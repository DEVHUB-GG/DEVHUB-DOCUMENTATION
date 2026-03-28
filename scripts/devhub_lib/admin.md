# 🛡️ Admin System

## Overview

The admin check used across all DevHub scripts (e.g. the `/craftingadmin` command) is handled by the file:

```
devhub_lib/modules/systems/s.admin.lua
```

This file defines which players are treated as admins. It is automatically adapted to the configured framework (`ESX`, `QBCore`, `QBOX`, `VRP`, or `custom`), but you can edit it directly to add custom permission logic.

***

## Default Admin Groups

| Framework  | Default admin groups          |
| ---------- | ----------------------------- |
| **ESX**    | `admin`, `superadmin`         |
| **QBCore** | `god`, `admin`                |
| **QBOX**   | `god`, `admin`                |
| **VRP**    | Configured via `devhub_lib`   |

***

## Customising the Admin Check

Open `devhub_lib/modules/systems/s.admin.lua` and locate the admin check function. You can extend or replace the default logic to match your server's permission setup.

**Example — adding a custom group:**

```lua
-- devhub_lib/modules/systems/s.admin.lua

local adminGroups = { "admin", "superadmin", "moderator" }  -- add your groups here

function IsPlayerAdmin(source)
    local group = GetPlayerGroup(source)  -- or your framework's equivalent
    for _, v in ipairs(adminGroups) do
        if group == v then
            return true
        end
    end
    return false
end
```

{% hint style="info" %}
After editing `s.admin.lua`, restart the `devhub_lib` resource (or the whole server) for changes to take effect.
{% endhint %}

***

## Used By

The admin check in `s.admin.lua` is used by:

* `/craftingadmin` — opens the crafting Admin Panel
* Any other DevHub script that restricts commands or features to server administrators
