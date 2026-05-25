---
description: How to upgrade an existing v2 install of devhub_skillTree to v3.
---

# 🔄 Migration v2 → v3

{% hint style="warning" %}
**Back up your `configs/` folder and export your `dh_skilltree` database table before starting.** v3 is a major version bump (v3.0.0) with one soft-breaking config change and new DB columns.
{% endhint %}

## <mark style="color:yellow;">Migration steps</mark>

{% stepper %}
{% step %}
### Back up your files

* Copy your current `configs/` folder somewhere safe
* Export the `dh_skilltree` SQL table (e.g. `mysqldump`)
{% endstep %}

{% step %}
### Replace resource files

* Stop your server
* Delete the old `devhub_skillTree` folder
* Drop in the v3 download from keymaster
* Keep your old `configs/` accessible for reference while you copy values over
{% endstep %}

{% step %}
### Run the database migration

v3 adds two new columns to `dh_skilltree`:

```sql
ALTER TABLE `dh_skilltree`
ADD COLUMN IF NOT EXISTS `data` LONGTEXT DEFAULT NULL,
ADD COLUMN IF NOT EXISTS `name` VARCHAR(255) DEFAULT NULL;
```

{% hint style="info" %}
The `identifier` column was also redefined as `varchar(46)` (down from `varchar(100)`) in the fresh `sql.sql`. You only need to change yours if your existing identifiers fit in 46 chars — otherwise leave it alone.
{% endhint %}
{% endstep %}

{% step %}
### Update `Config.EarnXp` (BREAKING)

The structure changed. Old v2 configs still execute, but `addTo` values that are `true` instead of numbers silently fall back to **5 XP** per tick — so your customized XP amounts disappear.

**Before (v2):**

```lua
['running'] = {
    xp = 10,
    timeout = 10000,
    addTo = { ['personal'] = true },
}
```

**After (v3):**

```lua
['running'] = {
    timeout = 10000,
    addTo = { ['personal'] = 10 },
}
```

The top-level `xp` field is no longer read. Move the value into `addTo`.
{% endstep %}

{% step %}
### Add the new XP-earning activities

v3 ships with **6 new built-in activities**: `climbing`, `parachuting`, `flying`, `boating`, `reloading`, `takingDamage`. Copy them from the fresh `configs/sh.main.lua` or skip the ones you don't want.

```lua
['climbing']     = { timeout = 10000, addTo = { ['personal'] = 5 } },
['parachuting']  = { timeout = 15000, addTo = { ['personal'] = 5 } },
['flying']       = { timeout = 10000, addTo = { ['personal'] = 5 } },
['boating']      = { timeout = 10000, addTo = { ['personal'] = 5 } },
['reloading']    = { timeout = 10000, addTo = { ['personal'] = 5 } },
['takingDamage'] = { timeout = 15000, addTo = { ['personal'] = 5 } },
```
{% endstep %}

{% step %}
### Copy over the new config blocks

The following blocks are new in v3 — copy them from the fresh `configs/sh.main.lua`. Each one can be disabled by setting it to `nil` (or just leaving the defaults).

* `Config.Theme` — `"legacy" | "modern" | "zombie" | "fantasy"`
* `Config.DailyXpLimit` — per-category daily XP caps
* `Config.SkillDegradation` — optional decay mechanic
* `Config.PremiumCurrency` — optional secondary currency for unlocks (default `nil`)
* `Config.TriggerOnSkillUnlock` — auto-fire events on specific skill unlocks
* `Config.DisabledListeners` — selectively disable listener events for performance
* `Config.MaxBackups` — keep N generator backups (exclusive only)

{% content-ref url="configuration.md" %}
[configuration.md](configuration.md)
{% endcontent-ref %}
{% endstep %}

{% step %}
### Skills config additions (optional)

If you use `Config.SkillsCategory`, entries now accept two optional fields:

```lua
Config.SkillsCategory = {
    { skill = 'personal', title = 'Personal', group = nil,    icon = nil },
    { skill = 'police',   title = 'Police',   group = 'Jobs', icon = 'fas fa-shield' },
}
```

* `group` — categories sharing a group string are visually grouped under one tab
* `icon` — FontAwesome icon shown next to the category name

Existing v2 entries continue to work unchanged — these fields are optional.

Per-skill `degradation = {...}` blocks are also a new optional addition — see the [Skill Degradation](degradation.md) page.
{% endstep %}

{% step %}
### Server admin commands now enabled by default

`/addXp` and `/addPoints` were commented out in v2's `configs/s.main.lua`. v3 enables them by default with a `Core.IsPlayerAdmin(source)` permission check. If you don't want these commands, comment them out in `configs/s.main.lua`.
{% endstep %}

{% step %}
### Restart your server

Start the resource and check the console for any errors. With debug enabled (`Config.Debug = true`), v3 prints a lot of trace logs — useful for diagnosing migration issues.
{% endstep %}
{% endstepper %}

***

## <mark style="color:yellow;">What's new — quick reference</mark>

{% content-ref url="configuration.md" %}
[configuration.md](configuration.md)
{% endcontent-ref %}

{% content-ref url="degradation.md" %}
[degradation.md](degradation.md)
{% endcontent-ref %}

{% content-ref url="admin-panel.md" %}
[admin-panel.md](admin-panel.md)
{% endcontent-ref %}

{% content-ref url="ui-color-customization.md" %}
[ui-color-customization.md](ui-color-customization.md)
{% endcontent-ref %}

{% content-ref url="development/helpers.md" %}
[helpers.md](development/helpers.md)
{% endcontent-ref %}

***

## <mark style="color:yellow;">Files that moved internally</mark>

These are inside `escrowed/` and don't require any action from server owners — listed for completeness:

* `escrowed/server/s.generator.lua` was expanded into the `escrowed/server/generator/` folder with one file per concern (skills, levels, earnxp, unlock handlers, trigger on unlock, visibility, premium currency, utils)
* `escrowed/server/s.degradation.lua`, `escrowed/server/s.admin.lua`, `escrowed/server/s.backup.lua` are new
* `escrowed/client/c.degradation.lua`, `escrowed/client/c.admin.lua`, `escrowed/client/c.generator.lua` are new

***

## <mark style="color:yellow;">If something breaks</mark>

1. Check the [FAQ → Common Issues](faq.md#common-issues)
2. Make sure `devhub_lib` is up to date and your framework adapter is configured
3. Enable `Config.Debug = true` in `sh.main.lua` and read the console output carefully — almost every internal step logs a trace line in v3
4. Join the Discord support — share your debug log, your `configs/sh.main.lua`, and the error message
