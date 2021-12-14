---
description: 'A subscription based GTA:V Roleplay Framework for alt:V.'
---

# Athena Framework for alt:V

## Summary

[Athena Framework](https://athenaframework.com) is Roleplay framework for GTA:V that is utilized by not FiveM or ragemp but the [alt:V platform](https://altv.mp). This is a full fledged framework similar to ESX that allows you to build a more robust game mode out without having to think about core scripts. This framework is built with TypeScript and tries to keep developers in mind for major implementations and extendability.

## Documentation

https://docs.athenaframework.com/

## Development Stack

* MongoDB (Database)
* TypeScript / JavaScript (Programming Language)
* Vue 3 (Frontend)
* Vite (Vue 3 Tooling)

_Using modern development tools for a modern framework._

## Purchase, Buy, and 7-Day Trial

License keys may be purchased from [Athena Framework](https://athenaframework.com).

_There is not a lifetime package for Athena._

## Why is it Open Source?

Unlike other servers and frameworks I believe in helping everyone as much as possible. Leaving Athena open source allows developers to learn a few things about the way the author of this repository thinks. Sharing is caring unless you don't support your care giver.

## Demo

Small demo server available for you to test the framework with Administrative capabilities. 

You can check that out using the alt:V client at [https://altstats.net/server/504](https://altstats.net/server/504)

## Feature List

- Partial Open Source
- TypeScript
-   Developer Features
    -   No Clip
    -   Teleport to Waypoint
    -   Fast Reboot
    -   Multiple Environment Configurations
    -   Modification Support
    -   Uses SWC for Fast Compilation
        -   Roughly 400ms
    - Vite for WebView, CEF, View Debugging
    - Plugin System
-    World
    -   Synchronized World Time
    -   Synchronized Weather Patterns
    -   Different Weather Based on Region
    -   Adjustable Configuration
    -   Performance Grid for Object Interactions / Finding
- Character
  - Appearance
  - Clothing
  - Info
  - Multiple Character Selection
- Discord Integration
  - Welcome List
  - Discord Role / Bot Integration
  - Login / Registration for Server
  - oAuth2 Integration
- Chat
  - Command System
  - Distance
  - Built-in Commands
  - Permission Based Commands
  - Custom Commands
- Console Commands
    -   Ban
    -   Unban
    -   Kick
    -   KickAll
    -   SetAdmin
    -   Dox
    -   Screenshot
    -   Add to Whitelist
    -   Remove from Whitelist
-   Player
    -   Food
    -   Water
    -   Custom Object Prop Synchronization
    -   Revive After 'x' Seconds
-   Name Tags
    -   Display after 7.5s \(Used for Hiding Names Partially\)
    -   Names Hidden in Vehicles
-   Interaction System
    -   Parse Objects by Section
    -   Add Custom Interactions Easily
    -   Colshape System to Represent Interaction Points
    -   ATM Object Interaction
-   Blip System
    -   Global Blip Controller
    -   Repeat Blips are Streamed
    -   Automatically Generate Blips for Useable Objects (Atms, Fuel, etc.)
- External Stream Service
  - Stream Service Utilizes Web Sockets
  - Create Custom Streams of Data for Players
  - Automatically Stream the Following
    - Objects
    - Markers
    - Text Labels
    - Help Text
    - Item Drops
-   Currency System
    -   Deposit Currency
    -   Withdraw Currency
    -   Transfer Bank Currency
-   Vehicle System
    -   Control Vehicle Door Locks
    -   Handle Vehicle Ownership
    -   Control Vehicle Door States
    -   Fuel
    -   Persistent Vehicle Spawning
    -   
-   Inventory System
    -   Custom Drag & Drop System
    -   Drop Items
    -   Pickup Items
    -   Move Items
    -   Multiple Slots for Items
    -   Inventory Item Restriction Flags
    -   Animations for Picking Up / Dropping
    -   All Weapon Icons
    -   Equipment Slots
    -   Toolbar Slots
    -   Custom Item Effects
    -   CONSUMABLE Items
    -   Custom Item Rules for Swapping, Equipping, Dropping, etc.
    -   Item Swap
    -   Item Stack
    -   Item Equip / Unequip
    -   Item Splitting
-   Clothing System
    -   Clothing Selection
    -   Tops
    -   Hats
    -   Bags
    -   Bottoms
    -   Shoes
    -   Accessories
    -   Bracelets
    -   Watches
    -   Masks
    -   Name Individual Items
    -   Describe Individual Items
    -   Separate Item Equips
    -   Customize Each Clothing Shop
    -   Restrict Clothing Items
- Garage System
    - Store Vehicles
    - Spawn Vehicles
- Expandable HUD System
    - Easily create a dynamic HUD
    - Add New HUD Elements
    - Remove HUD Elements
    - Built with Vue 3
-   Toolbar System
    -   Equip an item in a Toolbar Equippable Item
    -   Press 1-4 to swap items in toolbar
-   Custom Job Framework
    -   Easy to Use Job Language / Creation
    -   Play Animations
    -   Play Particles
    -   Play Sounds
    -   Add Blips
    -   Add Markers
    -   Custom Waypoint Types... Go To, Capture, etc.
    -   Custom Criteria: No Vehicle, No Weapon, etc.
    -   Call Events on Objective Completions
    -   Job Menu
-   Action Menus
    -   Infinitely scaling menus
    -   A menu system that calls other events easily.
    -   Easily construct custom menus in minutes to define functionality.
-   Wheel Menu
    -   Dynamic Wheel Menus
-   Dealership
    -   Basic Dealership with Customizable Locations
    -   Purchase Vehicles
    -   Spawn Vehicles from Garage After Purchase
-   Extendable Core Resource
    -   Extend the core resource by writing your own code in the 'plugins' folder.
-   Interior System
    -   Create Interiors Easily
    -   Specify Different Interior Types (House, Faction, System)
    -   Object Streaming for Interiors
-   Faction System
    -   Create Factions
    -   Create Custom Ranks for Factions
    -   Add Members to Factions
    -   Remove Members from Factions
    -   Manage Permissions Per Rank for Factions
    -   Faction Weapon Storage
    -   Faction Bank
    -   Faction Item Storage
    -   Faction Name Changing / Updating