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
#include !/TTS_lib/SaveManager/SaveManager

-- One part of our code deals with e.g. players
importantStuff = 'data'
function playerModuleSave()
    -- whatever is returned here will be passed to the load function
    return 'some ', {value = 'saved '}, importantStuff
end

-- Load with saved data (called onLoad)
function playerModuleLoad(savedThing, savedTable, importantThing)
    -- do stuff with it
    print('I\'ve read ' .. savedThing .. savedTable.value .. importantThing)
    -- if you return stuff here, it wil be printed on load (let users know something happened)
    return 'Player module restored some data, wooo'
end
-- Register our "module"
SaveManager.Register(playerModuleSave, playerModuleLoad)

-- Another part of code could deal with something totally different and also need persistent data
-- Just use above template again to have a separate saving/loading module with no interference between them

-- If you need a "free standing" onLoad function (you can't redefine onLoad or onSave), you can use
function SaveManager.userOnLoad()
    -- do stuff here
end
```

### Full interface
``Register(Function onSaveHandler, Function onLoadHandler)``  
**Effect:**
  * Calls ``onSaveHandler`` every few seconds (along with TTS onSave), stores any data it returns internally (one result only).
  * Calls ``onLoadHandler`` onLoad passing last save data ``onSaveHandler`` returned.
**Return:** nil

field: ``SaveManager.clearSaved``
**Effect:**
  * If set to true, ignores all saved data (save and load the game to purge it)

field: ``SaveManager.userOnLoad``
**Effect:**
  * If set to a function, it is called after loads like a normal onLoad function (no arguments)
