# 🎨 UI Color Customization

## <mark style="color:yellow;">Usage</mark>

{% stepper %}
{% step %}
### Enter the folder with the script
{% endstep %}

{% step %}
### Enter `html` folder
{% endstep %}

{% step %}
### Open the `colors.css` file
{% endstep %}
{% endstepper %}

#### The code looks like this

```css
/* YOU CAN'T USE A COMMA BETWEEN RGB */
--primary: 253 209 64; /* #fdd140 */
--background: 32 46 59; /* #202e3b */
--light-blue: 33 255 222; /* #21ffde */
--silver-default: 192 192 192; /* #c0c0c0  */
--silver-secondary: 152 151 151; /* #989797 */
--bronze-default: 203 158 96; /* #cb9e60 */
--bronze-secondary: 151 117 71; /* #977547 */
--gold-default: 253 209 64; /* #fdd140 */
--gold-secondary: 186 152 43; /* #ba982b */
--disabled: 83 83 83; /* #535353 */
--modal-background: 25 25 31; /* #19191f */
--background-body: 11 19 32; /* #0b1320 */
--background-border: 49 71 90; /* #31475a */

/*!!! YOU MUST USE A COMMA BETWEEN RGB !!!*/
--primary-rgba: 253, 209, 64; /* #fdd140 */
--grid-dark-rgba: 11, 19, 32; /* #0b1320 */
```

#### To customize the UI for yourself, simply edit the RGB color.

{% hint style="danger" %}
If you are editing the primary color, we recommend changing it in two locations!
{% endhint %}

## <mark style="color:yellow;">Examples of color changes</mark>

<div data-full-width="false"><figure><img src="../.gitbook/assets/image (310).png" alt=""><figcaption></figcaption></figure></div>

***

## <mark style="color:yellow;">Themes (v3)</mark>

v3 ships with four built-in visual themes. Switch between them by setting `Config.Theme` in `configs/sh.main.lua`:

```lua
Config.Theme = "modern" -- "legacy" | "modern" | "zombie" | "fantasy"
```

| Theme     | Description                                                         |
| --------- | ------------------------------------------------------------------- |
| `legacy`  | Original v1/v2 look                                                  |
| `modern`  | Default — clean modern look                                          |
| `zombie`  | Survival / post-apocalyptic style (concrete wall + grid background) |
| `fantasy` | Fantasy RPG style with ornate frames                                |

{% hint style="info" %}
Theme assets live in `html/themes/<themeName>/`. The theme is applied automatically when the config value changes — restart the resource to take effect.
{% endhint %}

{% hint style="warning" %}
Custom color overrides in `colors.css` apply on top of the chosen theme. Combine them to fine-tune any of the built-in themes.
{% endhint %}
