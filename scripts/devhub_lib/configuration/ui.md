# 📳 Ui

{% hint style="warning" %}
Ensure that if custom functionality is utilized, it returns true.
{% endhint %}

## <mark style="color:yellow;">Notification</mark>

Displays a notification to the user.

<kbd>text</kbd> The text of the notification. \
<kbd>duration</kbd> The duration for which the notification should be displayed. In milliseconds. \
<kbd>notificationType</kbd> The type of the notification.

```lua
CustomUi.Notify = function(text, duration, notificationType)
    return false -- if you are using a custom notification, return true
end
```

***

## <mark style="color:yellow;">Static Message</mark>

Displays a static message to the user.

<kbd>text</kbd> The text of the static message, if false ui is hidden.

```lua
CustomUi.ShowStaticMessage = function(text)
    return false -- if you are using a custom static message, return true
end
```

***

## <mark style="color:yellow;">Control Buttons</mark>

Displays control buttons to the user.

<kbd>text</kbd>  The text associated with the control buttons, if false ui is hidden.

```lua
CustomUi.ShowControlButtons = function(text)
    return false -- if you are using a custom control buttons system, return true
end
```

***

## <mark style="color:yellow;">Progressbar</mark>

Displays a progress bar to the user.

<kbd>data</kbd>  The data for the progress bar.

&#x20;            <kbd>data.duration</kbd>  The duration for which the progress bar should be displayed. In milliseconds.

&#x20;            <kbd>data.text</kbd>  The text associated with the progress bar.

&#x20;            <kbd>data.canStop</kbd>  A boolean indicating whether the progress bar can be stopped by the user.

&#x20;            <kbd>data.placement</kbd>  The placement of the progress bar. Default low. \[low, medium, high]

<kbd>cb</kbd>  The callback function to be executed when the progress bar completes.

```lua
CustomUi.ShowProgressbar = function(data, cb)
    return false -- if you are using a custom progress bar, return true
end
```

***

## <mark style="color:yellow;">Close Progressbar</mark>

Closes the progress bar

```lua
CustomUi.CloseProgressbar = function()
    return false -- if you are using a custom progress bar, return true
end
```
