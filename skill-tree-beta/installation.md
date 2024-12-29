# 💻 Installation

{% content-ref url="../download-purchased-assets.md" %}
[download-purchased-assets.md](../download-purchased-assets.md)
{% endcontent-ref %}

***

## <mark style="color:yellow;">Installation</mark>

### 1. Install devhub\_lib

Download and install the required library:

Visit https://github.com/DEVHUB-GG/devhub\_lib and download or

```bash
git clone https://github.com/DEVHUB-GG/devhub_lib.git
```

Configure it according to your framework.

***

### 2. Configure server.cfg

Add the following lines to your server.cfg in the correct order:

```bash
ensure devhub_lib        # Must be loaded before devhub_skillTree
ensure devhub_skillTree  # Main resource
```

***

### 3. Database Setup

Import the `sql.sql` file into your database.

***

## <mark style="color:yellow;">Configuration</mark>

The configuration files can be found in the `configs` folder:

***

## <mark style="color:yellow;">Versions</mark>

### Standard Version

Basic installation as described above.

### Exclusive Version

For the exclusive version, add this line before `ensure devhub_skillTree`:

```bash
ensure devhub_skillTree_generator
```

***

{% hint style="danger" %}
DO NOT CHANGE RESOURCE NAME
{% endhint %}
