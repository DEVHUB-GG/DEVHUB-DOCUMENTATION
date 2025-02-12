# 🔊 Sound Systme

If you want to adjust sound system go to **frameworks/c.sound.lua**

{% hint style="info" %}
By default, xsound is configured
{% endhint %}

```lua
    Core.PlaySoundLocally = function(uid, url, volume, loop)
        exports['xsound']:PlayUrl(uid, url, volume, loop)
    end
    Core.PlaySoundCoords = function(uid, url, volume, coords)
        exports['xsound']:PlayUrlPos(uid, url, volume, coords, false, false)
    end
    Core.FadeIn = function(uid, time, volume)
        exports['xsound']:fadeIn(uid, time, volume)
    end
    Core.FadeOut = function(uid, time)
        exports['xsound']:fadeOut(uid, time)
    end
    Core.ChangeDistance = function(uid, distance)
        exports['xsound']:Distance(uid, distance)
    end
    Core.StopSound = function(uid)
        exports['xsound']:Destroy(uid)
    end
    Core.SoundExists = function(uid)
        return exports['xsound']:soundExists(uid)
    end
```
