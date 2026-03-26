# Tutorial: How to Add a New Spell

Spells in TibiaCore are split into **Instant Spells** (e.g., `exura`) and **Runes** (e.g., `sudden death`).

## Step 1: Create the Lua Script
All spell scripts are located in `data/spells/scripts/`.

1.  Navigate to `data/spells/scripts/`.
2.  Create a file, for example, `my_fire_spell.lua`.
3.  Add the following template:

```lua
local combat = Combat()
combat:setParameter(COMBAT_PARAM_TYPE, COMBAT_FIREDAMAGE)
combat:setParameter(COMBAT_PARAM_EFFECT, CONST_ME_FIREAREA)
combat:setArea(createCombatArea(AREA_CIRCLE3X3))

function onGetFormulaValues(player, level, magicLevel)
    local min = (level / 5) + (magicLevel * 1.5) + 10
    local max = (level / 5) + (magicLevel * 2.5) + 20
    return -min, -max
end

combat:setCallback(CALLBACK_PARAM_LEVELMAGICVALUE, "onGetFormulaValues")

function onCastSpell(creature, variant)
    return combat:execute(creature, variant)
end
```

---

## Step 2: Register the Spell
You must register the spell in `data/spells/spells.xml`.

1.  Open `data/spells/spells.xml`.
2.  Add a new entry:

```xml
<instant name="My Fire Spell" words="exori flam area" level="20" mana="50" prem="1" range="3" casterTargetOrDirection="1" blockwalls="1" exhaustion="2000" group="attack" groupcooldown="2000" script="my_fire_spell.lua">
    <vocation name="Sorcerer" />
    <vocation name="Master Sorcerer" />
</instant>
```

---

## Step 3: Reload or Restart
To apply changes:
*   Use the talkaction: `/reload spells`.
*   Alternatively, restart the server.
