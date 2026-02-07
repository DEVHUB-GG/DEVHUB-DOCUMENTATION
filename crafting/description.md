---
description: >-
  This document describes all configuration options for the DevHub Truck robbery
  resource.
---

# 📜 Description

## Overview

DevHub Crafting is an advanced, feature-rich crafting system designed for FiveM servers. It provides a complete crafting experience with a modern, animated UI built with Vue.js, supporting multiple crafting stations, blueprints, weapon attachments, community-driven projects, and detailed player statistics.

## Key Features

* **Multi-Station Crafting System** - Create multiple crafting workbenches with unique recipes, props, and camera angles
* **Blueprint Collection** - Unlockable blueprints with rarity tiers and custom unlock conditions
* **Weapon Attachment System** - Full 3D preview with real-time attachment management (suppressors, scopes, grips, magazines, tints)
* **Community Projects** - Server-wide collaborative goals where players contribute materials
* **Statistics Tracking** - Comprehensive player statistics including crafted items, time spent, and leaderboards
* **Admin Panel** - In-game configuration editor for categories, blueprints, crafts, and workbenches
* **Queue System** - Time-based crafting with queue management and reordering
* **Discord Integration** - Personal webhook notifications when crafts complete

## Supported Frameworks

* **ESX**
* **QBCore**
* **QBOX**
* **VRP**
* **Custom frameworks** via devhub\_lib bridge

## Supported Inventories

* ox\_inventory
* qb-inventory
* qs-inventory
* esx\_inventoryhud
* and more...
* Custom inventories via devhub\_lib

***

## UI Features

### Modern Interface

* Elegant dark theme with gold accents
* Smooth page transitions and entrance animations
* Three-panel layout (item list, 3D preview, queue/details)
* Responsive design with custom scrollbars

### Crafting Panel

* Category filtering with custom icons
* List and grid view modes
* Multiple sort options (Name, Craftable, Blueprint status)
* Real-time ingredient tracking with visual indicators
* 3D prop preview with mouse rotation

### Weapon Attachments Panel

* Real-time 3D weapon preview
* Mouse drag rotation and scroll zoom
* Dynamic bone-based attachment positioning
* Visual connection lines from UI to attachment points
* Install/remove attachments with inventory integration

### Blueprint Collection

* Visual grid display with rarity colors
* Lock/unlock status indicators
* Sorting by rarity, name, or unlock status
* Detailed tooltip with required materials

### Statistics Dashboard

* Top 5 most crafted items display
* Total crafting time tracking
* Resources used counter
* Blueprint collection progress
* Community donation totals
