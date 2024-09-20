# ⚙️ Configuration

1. Download resource from our [github](https://github.com/DEVHUB-GG/dh\_lib)
2. Open shared.lua
3. Adjust script to server frameworks

{% code title="shared.lua" %}
```lua
-- This module contains shared configuration settings for the DEVHUB library.
-- The framework being used. Possible frameworks: "ESX", "QBCore", "Custom"
Shared.Framework = "ESX"

-- The target system being used. Possible targets: "ox_target", "qb-target", "Custom"
Shared.Target = "ox_target"
```
{% endcode %}

