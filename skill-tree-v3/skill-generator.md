---
description: >-
  The skill generator and adding your own skills is only available in the
  exclusive version
---

# ⚙️ Skill Generator

{% hint style="danger" %}
Make sure `devhub_skillTree_generator` is started
{% endhint %}

{% stepper %}
{% step %}
### Open configs/sh.main.lua
{% endstep %}

{% step %}
### Change `Config.EnableGenerator` to <mark style="color:green;">**true**</mark>
{% endstep %}

{% step %}
### Restart `devhub_skillTree` script
{% endstep %}

{% step %}
### A new button will appear in the right top corner

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Click at any box on the grid and start creating or editing

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Make sure that not errors are found

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Confirm generation of file

Config will be saved to your <mark style="color:green;">**clipboard**</mark>
{% endstep %}

{% step %}
### Open your `configs/sh.skills.lua` and paste copied skill tree
{% endstep %}

{% step %}
### Create your skill functionality using our export and listeners
{% endstep %}
{% endstepper %}

{% content-ref url="development/" %}
[development](development/)
{% endcontent-ref %}

***

## <mark style="color:yellow;">New in v3</mark>

The generator UI has been expanded with new editors for everything you previously had to hand-edit in config files:

* **Visibility handlers** — edit per-category visibility filters that get saved to `Config.CategoryVisibilityHandler`
* **Unlock handlers** — per-skill unlock conditions saved to `Config.UnlockHandlerForSkills`, with support for the new [Helpers](development/helpers.md)
* **Trigger on unlock** — auto-fire your own events when a skill is unlocked, saved to `Config.TriggerOnSkillUnlock`
* **Premium currency** — configure the global premium currency directly from the UI
* **Daily XP limits** — set per-category caps that write to `Config.DailyXpLimit.Limits`
* **Degradation overrides** — per-category overrides written to `Config.SkillDegradation.Categories`
* **Category groups & icons** — assign `group` and `icon` to organize categories in the menubar

***

## <mark style="color:yellow;">Automatic Config Backups</mark>

Every time you save from the generator, the affected config files (`sh.main.lua`, `sh.skills.lua`, `s.main.lua`) are backed up first. You can list, restore, or delete backups from the admin panel.

```lua
Config.MaxBackups = 5 -- int | Maximum backups to keep (0 = unlimited)
```

{% hint style="info" %}
Backups are stored on disk under the resource's `backups/` folder with a JSON index. Restoring a backup also creates a safety backup of the current state first.
{% endhint %}

{% content-ref url="admin-panel.md" %}
[admin-panel.md](admin-panel.md)
{% endcontent-ref %}

***

<figure><img src="../.gitbook/assets/image (142).png" alt=""><figcaption><p>Showcase of skill tree generator</p></figcaption></figure>
