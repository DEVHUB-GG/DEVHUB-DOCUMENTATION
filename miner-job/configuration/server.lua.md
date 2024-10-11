---
description: Documentation for server.lua Configuration
---

# server.lua

**Drill Item Configuration**

```lua
Config.MenuItem = "dh_drill"
```

* **Description**: Specifies the item required to initiate the drilling process.
* **Example**: `"dh_drill"` means players need this item to start drilling.

**Ore Deletion Chance**

```lua
Config.DeleteOreChance = 10
```

* **Description**: Sets the probability (in percentage) that an ore will be removed after a successful drill.
* **Example**: `10` means there is a 10% chance of the ore disappearing post-drilling.

**Webhook Configuration**

```lua
Config.Webhook = "https://discord.com/api/webhooks/890000000000000000/"
```

* **Description**: URL for sending logs or notifications to a Discord channel.
* **Note**: Replace with your webhook URL for proper functionality.
