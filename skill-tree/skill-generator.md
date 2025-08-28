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

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
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



<figure><img src="../.gitbook/assets/image (142).png" alt=""><figcaption><p>Showcase of skill tree generator</p></figcaption></figure>
