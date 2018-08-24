## Simple tool for notifying users of a workshop mod update

Useful for mods where users often save a game (e.g. when they want to resume later or after customizing
it to their needs) and then continue playing on their save. This tool will notify them if an update has
been pushed to Steam Workshop and the table they're on currently is outdated.

### How to use

#### Setup (once):
1. Paste or include the VersionCheck.ttslua script on some inconspicuous object (like a Go piece), it will be hidden anyway.
2. Read your update count on mod workshop page, it's the XX in "XX Change Notes (view)" on the lower right side of
   your mod gallery/description panel. Paste that number under *current_version* variable value on 1st line of the script.
1. Read your mod WorkshopID from the link to it, e.g. with "https://steamcommunity.com/sharedfiles/filedetails/?id=862644552"
   it would be **862644552**. Paste that number under *workshop_id* variable value on 1st line of the script.

#### When updating your mod:
1. Increase the *current_version* variable on 1st line of the script by 1.
2. Save&Play, confirm that a "Ready to push" broadcast shows
3. Update your mod normally
4. Reload, confirm that it now shows green "Up to date" in chat

#### How do I know if it works?
Just save a table of your mod, push an update to the workshop and load (now outdated) save you created before. You should
get a broadcast that this save is outdated.
