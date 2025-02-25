# 🆘 Compatibility test

To ensure the framework configuration is working correctly, run a compatibility test

{% stepper %}
{% step %}
### Go to <kbd>config.lua</kbd> and set **Shared.CompatibilityTest** to true
{% endstep %}

{% step %}
### Add new item named dh\_test
{% endstep %}

{% step %}
### Restart your server
{% endstep %}

{% step %}
### Join the server and type /dh\_startTest to start the test
{% endstep %}

{% step %}
### Follow the instructions shown in the game.
{% endstep %}

{% step %}
### Check the server console for the test results
{% endstep %}
{% endstepper %}

{% hint style="info" %}
During the test, you will need to use an item, revive yourself, and then you will be kicked from the server. Results will be shown in **server console** within 20 seconds after being kicked.
{% endhint %}

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
