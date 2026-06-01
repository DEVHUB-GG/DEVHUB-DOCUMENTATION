# 💻 Installation

{% stepper %}
{% step %}
### Install devhub\_lib

Download and install the required library and configure it according to your framework.

Download [https://github.com/DEVHUB-GG/devhub\_lib ](https://github.com/DEVHUB-GG/devhub_lib)or use command

```bash
git clone https://github.com/DEVHUB-GG/devhub_lib.git
```
{% endstep %}

{% step %}
### Install screenshot-basic

The license system uses `screenshot-basic` to capture player avatars for licenses.

Download [https://github.com/citizenfx/screenshot-basic](https://github.com/citizenfx/screenshot-basic)
{% endstep %}

{% step %}
### Install resources from keymaster

Download the <mark style="color:red;">LICENSE SYSTEM</mark> script file from keymaster.
{% endstep %}

{% step %}
### Start resources

Move the files to the `resources` folder on your server and add the following lines to your server.cfg in the correct order:

```javascript
ensure devhub_lib
ensure screenshot-basic
ensure devhub_licenses
```
{% endstep %}

{% step %}
### Restart your server
{% endstep %}
{% endstepper %}



{% content-ref url="../scripts/devhub_lib-needed-for-each-script/" %}
[devhub\_lib-needed-for-each-script](../scripts/devhub_lib-needed-for-each-script/)
{% endcontent-ref %}
