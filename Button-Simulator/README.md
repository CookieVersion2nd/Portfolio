# 🧪 Button Simulator

A Roblox simulator built around a fully customizable core loop — procedural generation, progression, and a shop system, all driven by configuration rather than hardcoded values. Development was paused before a full public release, but the core systems described below are implemented and functional.

**📦 Currently available for sale** — if you want to continue development or license the existing systems, DM me for details.

## 🎥 Project Overview

https://github.com/user-attachments/assets/5c3ab8fb-66db-45f2-91fa-06b594692932

A full walkthrough of every system below.

## 🧩 Built to Be Customized

This is the core design principle behind the whole project: **every gameplay value lives in configuration, not in the logic itself.** That means a client (or future developer) can reshape the game without touching the underlying systems.

What that looks like in practice:

- **Add a new button type** — just drop in an ImageLabel-based button and register it. No changes to the generator.
- **Rebalance instantly** — change spawn probabilities, rebirth costs, or upgrade values by editing a config table, not the code that runs them.
- **Scale progression freely** — add Rebirth 4, 5, 6+ the same way Rebirth 1–3 were built, with zero duplicated logic.

```lua
local randomNumber = math.random(1, 100)

if randomNumber <= 2 then
    rewardType = "Bomb"
    buttonModel.visual.SurfaceGui.ImageLabel.Image = BOMB_IMAGE
elseif randomNumber <= 12 then
    rewardType = "Gem"
    buttonModel.visual.SurfaceGui.ImageLabel.Image = GEM_IMAGE
else
    rewardType = "Coin"
    buttonModel.visual.SurfaceGui.ImageLabel.Image = COIN_IMAGE
end

buttonModel:SetAttribute("RewardType", rewardType)
```


This is the system I'd point to first if you're evaluating whether I can build something you can keep adjusting after handoff — not just something that works once and is done.

## 🎲 Procedural Button Field Generation

The button field isn't hand-placed. The generator calculates how many buttons fit in a given area, spaces them automatically, and assigns each one a type via weighted probability.

| Button | Probability |
|---|---:|
| 🪙 Coin | 88% |
| 💎 Gem | 10% |
| 💣 Bomb | 2% |

```lua
local spacingX = visual.Size.X + 0.3
local spacingZ = visual.Size.Z + 0.3

local columns = math.floor(area.Size.X / spacingX)
local rows = math.floor(area.Size.Z / spacingZ)
```


https://github.com/user-attachments/assets/b17ba0b3-16fb-4b89-9c0e-4041c54aff97



## 🔄 Rebirth System

Rebirth requirements (coins, buttons pressed, etc.) are pulled from a shared config rather than hardcoded per-tier — so **Rebirth 1: 1,000 coins / 500 buttons** and every tier after it run through the same logic.

*UI provided by the client — scripting and functionality implemented by me.*


<img width="544" height="247" alt="image" src="https://github.com/user-attachments/assets/87c05156-60a7-4747-a38c-fc2beba2b87a" />
<img width="523" height="257" alt="image" src="https://github.com/user-attachments/assets/ebea76d8-8934-4152-a775-0483b26dbb66" />



## ⚡ Upgrade Shop

Tweened upgrade menu with animated UI transitions. Currently drives a speed upgrade, validated and applied through the same config-driven pattern as the rebirth system.

<img width="555" height="220" alt="image" src="https://github.com/user-attachments/assets/ee01b9ba-332c-498f-b258-37ffb93542e4" />
<img width="521" height="218" alt="image" src="https://github.com/user-attachments/assets/682952e9-7cec-420e-8b9b-94b8aa900ca8" />


## 💾 Data Persistence

Coins, gems, buttons pressed, and upgrade progression are saved via DataStores on join/leave, with `pcall`-wrapped error handling.

```lua
local success, currentGems = pcall(function()
    return PlayerGems:GetAsync(player.UserId)
end)

if success and currentGems then
    gems.Value = currentGems
end
```


## ♻️ Field Regeneration

The entire button field clears and regenerates every 5 minutes, using the same generation system above — so special buttons (already converted to normal after being pressed) get refreshed back into circulation automatically.
(set to reseting every 2 seconds for video purposes)





https://github.com/user-attachments/assets/82595d96-dae5-454e-ab64-2467422c0478





## 🛠️ Technical Skills Demonstrated

- Luau
- Roblox Studio
- ModuleScripts
- RemoteEvents
- Client/Server Architecture
- DataStores
- GUI Scripting
- TweenService
- Attributes
- Procedural Generation
- Weighted Probability
- Spatial Calculation

## 🎯 Development Focus

I focus on scripting and gameplay systems. I can script functionality around assets a client provides, but I don't currently cover 3D modeling, UI/UX design, map building, artwork, VFX, or animation.
