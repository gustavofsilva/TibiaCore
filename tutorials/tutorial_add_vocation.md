# Tutorial: How to Add or Modify Vocations

Vocations define player classes, including their health/mana gain, capacity, and skill multipliers.

## Modifying Vocations
Vocations are defined in `data/XML/vocations.xml`.

1.  Open `data/XML/vocations.xml`.
2.  Locate the vocation you want to edit.

### Vocation Parameters:
*   `id`: Unique identifier.
*   `name`: Display name.
*   `gainhp`: HP gained per level.
*   `gainmana`: Mana gained per level.
*   `gaincap`: Capacity gained per level.
*   `attackspeed`: Delay between auto-attacks in milliseconds (smaller = faster).
*   `basespeed`: Movement speed at level 1.

### Skill Multipliers:
Multipliers define how fast a vocation learns skills (lower is faster).
*   `id="0"`: Fist Fighting.
*   `id="1"`: Club Fighting.
*   `id="2"`: Sword Fighting.
*   `id="3"`: Axe Fighting.
*   `id="4"`: Distance Fighting.
*   `id="5"`: Shielding.
*   `id="6"`: Fishing.

---

## Adding a New Vocation
To add a new vocation (e.g., a custom promotion):
1.  Copy an existing `<vocation>` block in `vocations.xml`.
2.  Assign it a unique `id`.
3.  Set `fromvoc="X"`, where X is the ID of the base vocation it promotes from.
4.  Configure the gains and skill multipliers.
5.  If you want it to be a promotion, you must also configure the promotion system in `NPC` scripts or specialized Lua scripts.
