# Tutorial: How to Create a Simple Quest (Chest)

Quests in TibiaCore are usually implemented using **Actions** and **Unique IDs (UIDs)**.

## Step 1: Place a Chest on the Map
1.  Open your map in RME.
2.  Place a chest (or any container).
3.  Assign it a **Unique ID** (e.g., `5000`). Make sure this ID is not used by any other item on the map.

---

## Step 2: Create the Quest Script
1.  Navigate to `data/actions/scripts/quests/` (create the directory if it doesn't exist).
2.  Create a file named `my_first_quest.lua`.
3.  Add the following code:

```lua
function onUse(player, item, fromPosition, target, toPosition, isHotkey)
    -- Storage to track if the player already completed the quest
    local storage = 45001

    if player:getStorageValue(storage) == -1 then
        player:addItem(3031, 100) -- Add 100 Gold Coins
        player:sendTextMessage(MESSAGE_EVENT_ADVANCE, "You have found 100 gold coins!")
        player:setStorageValue(storage, 1) -- Mark as completed
    else
        player:sendTextMessage(MESSAGE_EVENT_ADVANCE, "It is empty.")
    end
    return true
end
```

---

## Step 3: Register the Action
1.  Open `data/actions/actions.xml`.
2.  Add a new entry linking the chest's Unique ID to the script:

```xml
<action uniqueid="5000" script="quests/my_first_quest.lua" />
```

---

## Step 4: Reload or Restart
*   Use the talkaction: `/reload actions`.
*   Alternatively, restart the server.
