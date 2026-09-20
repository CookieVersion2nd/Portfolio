# 🧪 Button Simulator

A larger Roblox project I developed while exploring interconnected gameplay systems, procedural generation, modular scripting, data persistence, and configurable progression.

The project was stopped before being completed as a full game, but many of its core systems were implemented and functional.

## 🎥 Project Overview

https://github.com/user-attachments/assets/5c3ab8fb-66db-45f2-91fa-06b594692932

A complete walkthrough of the major features and systems currently implemented in Button Simulator.

## 🎲 Procedural Button Field Generation

One of the main systems in Button Simulator is a dynamically generated button field.

Instead of manually placing every button, the system calculates how many buttons can fit inside the selected area, calculates their positions, and generates the field automatically.

### What the System Handles

- Automatic row and column calculation
- Dynamic spacing based on button dimensions
- Automatic positioning
- Randomized button types
- Weighted probabilities
- Configurable button types
- Easy addition of new button types

[screenshot here]

### 🎯 Weighted Probability

Each generated button is assigned a type using weighted probability.

| Button | Probability |
|---|---:|
| 🪙 Coin | 88% |
| 💎 Gem | 10% |
| 💣 Bomb | 2% |

The probability can be changed without rebuilding the rest of the generation system.

For example:

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

The same system can be expanded with additional button types and different probability distributions, for example:

- Coin
- Gem
- Bomb
- Diamond
- Rare Button
- Legendary Button
- ...

This means the system can be adapted to different gameplay designs without rebuilding the entire generator.

### 📐 Automatic Spatial Calculation

The generator also calculates how many buttons can fit inside the generation area based on the dimensions of the area and the button itself.

```lua
local spacingX = visual.Size.X + 0.3
local spacingZ = visual.Size.Z + 0.3

local columns = math.floor(area.Size.X / spacingX)
local rows = math.floor(area.Size.Z / spacingZ)
```

The position of each generated button is then calculated automatically. This allows the generator to work with different sized areas instead of relying on manually placed positions.

### 🧠 Designed With Customization in Mind

A major goal of this system was making it easy to change later. For example:

- What happens if the client wants another button type?
- What happens if a rare button needs to become more common?
- What happens if the entire probability distribution changes?

The system is structured so these kinds of changes can be made without rewriting the positioning and generation logic.

## 🔄 Rebirth & Progression System

Button Simulator includes a configurable rebirth system with multiple requirements and progression values. A rebirth can require things such as:

- Coins
- Buttons pressed
- Current progression
- Other configurable requirements

### ⚙️ Configurable Requirements

Rather than hard-coding values separately into individual UI elements, the rebirth system retrieves the appropriate requirements from the progression configuration.

For example — **Rebirth 1**:
- Coins Required: 1,000
- Buttons Required: 500

Changing these requirements does not require rewriting the entire rebirth system. The same logic can also be used for additional rebirth levels with different requirements.

[screenshot here]

*UI provided by the client. Scripting and functionality implemented by me.*

The system handles the actual requirement checking, progression, rewards, and dynamic updates behind the interface.

## ⚡ Upgrade System

The project includes an upgrade system that allows players to improve progression-related statistics. The system handles:

- Upgrade requirements
- Requirement validation
- Stat changes
- Progression
- UI updates
- Animated UI transitions

[screenshot here]

The upgrade values can be modified without having to rebuild the entire system.

## 💾 Player Data & Persistence

The project uses Roblox DataStores to persist player progression between sessions. Persistent data implemented includes values such as:

- 🪙 Coins
- 💎 Gems
- 🔘 Buttons Pressed
- ⚡ Upgrade-related progression

Player data is loaded when the player joins and saved when the player leaves.

Example:

```lua
local success, currentGems = pcall(function()
    return PlayerGems:GetAsync(player.UserId)
end)

if success and currentGems then
    gems.Value = currentGems
end
```

DataStore operations are handled with error checking so failures can be detected during development.

## 📊 Live Statistics UI

The project includes a live statistics display that updates as the player's progression changes. Information displayed includes values such as:

- Coins
- Gems
- Rebirths
- Buttons Pressed
- Other progression values

[screenshot here]

The displayed values update dynamically while the player is playing.

## ♻️ Automatic Button Field Regeneration

The button field can automatically regenerate after a set amount of time. The regeneration process:

- Removes the existing generated buttons
- Generates a new button field
- Randomizes the button types
- Automatically places the new buttons

[video here]

The regeneration system uses the same procedural generation system, so the new field does not need to be manually constructed.

## 🧩 Modular & Configurable Design

One of the main design goals throughout the project was making systems easier to modify and expand. Examples of configurable values include:

- Button probabilities
- Button types
- Rebirth requirements
- Upgrade requirements
- Progression values
- Other gameplay parameters

Instead of putting every value directly into the core logic, systems can retrieve the values they need from configuration.

For example, instead of:

> "If rebirth = 1, use these exact values."
> "If rebirth = 2, use these exact values."
> "If rebirth = 3, use these exact values."

... the system can use the configuration for whichever rebirth the player is currently on. This approach makes adding or changing progression much easier.

## 🧠 What I Focused On While Building It

This project wasn't just about making individual features work — I also tried to think about how the systems would behave when requirements changed. For example:

- Can I add a new button without rebuilding the generator?
- Can I change a probability without rewriting the field system?
- Can I change a rebirth requirement without rewriting the UI logic?
- Can I add additional progression without duplicating large amounts of code?

Designing around these questions made the project more configurable and easier to expand.

## 🛠️ Technical Skills Demonstrated

- Luau
- Roblox Studio
- ModuleScripts
- RemoteEvents
- Client / Server Architecture
- DataStores
- GUI Scripting
- TweenService
- Attributes
- Procedural Generation
- Weighted Probability
- Spatial Calculations
- Dynamic UI Updates
- Player Progression Systems
- System Integration
- Debugging

## 📈 What This Project Demonstrates

Button Simulator gave me experience building systems that interact with one another rather than only creating isolated scripts. The project demonstrates my ability to:

- Build configurable gameplay systems
- Create procedural systems
- Work with weighted probability
- Implement persistent player data
- Build progression systems
- Connect gameplay logic with UI
- Use modular scripting
- Work with client/server communication
- Design systems with future changes in mind
- Debug and connect multiple systems together

## 📌 Project Status

Button Simulator is an incomplete project that I stopped working on before turning it into a fully finished game. However, many of the systems shown above were implemented and functional.

I consider it a larger experimental project and a demonstration of the systems I was able to design and build while learning Roblox development.

## 💰 Project Availability

The current Button Simulator project is available for sale if you're interested in continuing development or using its existing systems. DM me for details.

## 🎯 My Development Focus

I currently focus primarily on Roblox scripting and gameplay systems. I can script functionality around assets provided by the client, but I do not currently specialize in:

- 3D modeling
- UI/UX design
- Map building
- Artwork
- VFX creation
- Animation creation

My focus is scripting and functionality.
