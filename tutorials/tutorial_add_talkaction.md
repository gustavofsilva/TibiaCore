# Tutorial: How to Add a Custom Talkaction (Command)

Talkactions are custom commands players or staff can type (e.g., `!online`, `/ban`).

## Step 1: Create the Lua Script
All talkaction scripts are located in `data/talkactions/scripts/`.

1.  Navigate to `data/talkactions/scripts/`.
2.  Create a file named `my_command.lua`.
3.  Add the following code:

```lua
function onSay(player, words, param)
    player:sendTextMessage(MESSAGE_STATUS_CONSOLE_BLUE, "Hello! You executed the custom command: " .. words)
    player:getPosition():sendMagicEffect(CONST_ME_MAGIC_BLUE)
    return true
end
```

---

## Step 2: Register the Talkaction
You must register your script in `data/talkactions/talkactions.xml`.

1.  Open `data/talkactions/talkactions.xml`.
2.  Add a new entry:

```xml
<!-- player command starts with ! -->
<talkaction words="!hello" script="my_command.lua" />

<!-- staff command starts with / -->
<talkaction words="/hello" group="2" acctype="4" script="my_command.lua" />
```

### Parameters:
*   `words`: The text that triggers the command.
*   `script`: The name of the file in `data/talkactions/scripts/`.
*   `group`: Required group level (e.g., 2 for GMs).
*   `acctype`: Required account type level.

---

## Step 3: Reload or Restart
To apply the changes:
*   Use the talkaction: `/reload talkactions`.
*   Alternatively, restart the server.
