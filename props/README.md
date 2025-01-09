# ♟️ Props

## 💻 Installation

{% stepper %}
{% step %}
#### Install devhub\_lib

Download and install the required library and configure it according to your framework.

Download [https://github.com/DEVHUB-GG/devhub\_lib](https://github.com/DEVHUB-GG/devhub_lib) or use the command:

```bash
git clone https://github.com/DEVHUB-GG/devhub_lib.git
```
{% endstep %}

{% step %}
#### Install resources from keymaster

* Download the <mark style="color:red;">CARDANCE</mark> script file from keymaster.
* Download the <mark style="color:red;">CARDANCE ASSETS</mark> script file from keymaster.
{% endstep %}

{% step %}
#### Start resources

Move the files to the `resources` folder on your server and add the following lines to your `server.cfg` in the correct order:

```bash
ensure devhub_lib
ensure devhub_cardance
ensure devhub_cardance_assets
```
{% endstep %}

{% step %}
#### Database Setup

Import the `sql.sql` file into your database.
{% endstep %}

{% step %}
#### Restart your server

Restart your server to apply the changes.
{% endstep %}
{% endstepper %}

{% hint style="danger" %}
DO NOT CHANGE RESOURCE NAME
{% endhint %}
