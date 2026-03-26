# Tutorial: How to Add a New Monster

This guide explains how to create and register a new monster in TibiaCore.

## Step 1: Create the Monster XML File
All monsters are defined in XML files located in `data/monster/`.

1.  Navigate to `data/monster/`.
2.  Create a new file, for example, `my_monster.xml`.
3.  Add the following template:

```xml
<?xml version="1.0"?>
<monster name="My Monster" nameDescription="a my monster" race="blood" experience="1000" speed="40" manacost="0">
  <health now="1500" max="1500" />
  <look type="34" head="0" body="0" legs="0" feet="0" corpse="4025" />
  <flags>
    <flag summonable="0" />
    <flag attackable="1" />
    <flag hostile="1" />
    <flag illusionable="0" />
    <flag convinceable="0" />
    <flag pushable="0" />
    <flag canpushitems="1" />
    <flag canpushcreatures="1" />
    <flag targetdistance="1" />
    <flag runonhealth="300" />
  </flags>
  <attacks attack="40" skill="60">
    <attack name="melee" min="-50" max="-120" chance="100" />
    <attack name="fire" min="-100" max="-200" range="7" radius="3" target="1" chance="15">
      <attribute key="shootEffect" value="fire" />
      <attribute key="areaEffect" value="firearea" />
    </attack>
  </attacks>
  <defenses armor="20" defense="30" />
  <immunities>
    <immunity fire="1" />
    <immunity poison="1" />
  </immunities>
  <loot>
    <item id="3031" countmax="100" chance="800" /> <!-- Gold Coin -->
    <item id="3035" countmax="2" chance="100" /> <!-- Platinum Coin -->
  </loot>
</monster>
```

### Key Parameters:
*   `name`: The display name of the monster.
*   `experience`: XP awarded on kill.
*   `look type`: The appearance (Sprite ID).
*   `loot`: Define items by ID and their drop chance (1000 = 100%).

---

## Step 2: Register the Monster
The server won't recognize your monster until it's registered in `data/monster/monsters.xml`.

1.  Open `data/monster/monsters.xml`.
2.  Add a new entry pointing to your file:
    ```xml
    <monster name="My Monster" file="my_monster.xml" />
    ```

---

## Step 3: Reload or Restart
To apply the changes:
*   If the server is running, use the talkaction: `/reload monsters`.
*   Alternatively, restart the server.
