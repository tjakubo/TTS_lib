## Persistent data management for separate modules
Provides a simple framework to register multiple save/load functions for different parts of your code.
Each module can register a function to be called on save and function to be called on load, data deserialized from
last save function will be passed to load function.
Returning a string in the load function prints it to the screen for simple result reporting.

*Defines onSave function - you have to process all persistent data through this lib*
*Warning:* Redefining onSave after this library is included *will silently break the module*
*If you're not using EventSub, also defines onLoad (and redefining it later will break it)*

**Access table:** ``SaveManager``

### Example usage
```lua
-- One part of our code deals with e.g. players

-- Save current player count
function playerModuleSave()
    return #Player.getPlayers()
end
-- Load with saved data (called onLoad)
-- first argument is whatever save function returned last time (already decoded)
function playerModuleLoad(playerCount)
    -- do stuff with it
    -- returning a string prints in onLoad
    return 'Player module loaded - last player count: ' .. playerCount
end
-- Register our "module"
SaveManager.Register(playerModuleSave, playerModuleLoad)


-- Another part of code could deal with something totally different and also need persistent data
-- Just use above template again to have a separate saving/loading module with no interference between them
```

### Full interface
``Register(Function onSaveHandler, Function onLoadHandler)``  
**Effect:** 
  * Calls ``onSaveHandler`` every few seconds (along with TTS onSave), stores any data it returns internally (one result only).
  * Calls ``onLoadHandler`` onLoad passing last save data ``onSaveHandler`` returned.
**Return:** nil
