**Update Checker** automatically checks all supported Oxide plugins for updates on server start or on command. This is useful to see if you are using an outdated, older versions of plugins. It will also automatically check for updates every hour, or at the time configured. Update Checker also supports the Email API and Push API plugins for instant notifications.

## Permissions

- **updatechecker.use** -- Allows player to run the update check

## Commands

- **updates** -- Triggers the plugin update checking sequence.

## Configuration

```json
{
  "Ignored Plugins (Filenames of plugins which to ignore in version check)": [ ],
  "Settings": {
    "Auto Check Interval (in Minutes)": 60.0,
    "Use EmailAPI": false,
    "Use PushAPI": false
  }
}
```

The configuration file will update automatically if new options are added or removed. I'll do my best to preserve any existing settings and messages with each new version.

## Localization

The default messages are in the `UpdateChecker.json` file under the `oxide/lang/en directory`. To add support for another language, create a new language folder (ex. de for German) if not already created, copy the default language file to the new folder, and then customize the messages.

```json
{
  "Checking": "Checking for updates... This may take a few seconds. Please be patient.",
  "Outdated Plugin List": "Following plugins are outdated:\n{plugins}",
  "Outdated Plugin Info": "# {title} | Installed: {installed} - Latest: {latest} | {url}",
  "Resource Unavailable": "Following plugins are not accessible online at the moment, and therefore cannot be checked for updates: {plugins}",
  "Resource Release Unavailable": "Following plugins do not have a release version, and therefore cannot be checked for updates: {plugins}",
  "Resource Details Unavailable": "Following plugins have an improper version number else may not have a release version available, and therefore cannot be checked for updates: {plugins}"
}
```

## Plugin Developers

To add Update Checker support in your plugin if your plugin is still hosted on **oxidemod.org**, add the ResourceId variable and your plugin's ID from its URL, otherwise support will be handled automatically if your plugin is on **umod.org**.

**Example:** http://oxidemod.org/plugins/updatechecker.681/

### C# Example
```csharp
namespace Oxide.Plugins
{
    [Info("Title of Plugin", "Your Name", 0.1, ResourceId = 681)]
    [Description("This is what the plugin does")]
    public class PluginName : RustPlugin
    {
        // This is where your plugin will do its magic
    }
}
```

### JavaScript Example
```javascript
var PluginName = {
    Title : "Title of Plugin",
    Description : "This is what the plugin does",
    Author : "Your Name",
    Version : V(0, 1, 0),
    ResourceId : 681

    // This is where your plugin will do its magic
}
```

### Lua Example
```lua
PLUGIN.Title = "Title of Plugin"
PLUGIN.Description = "This is what the plugin does"
PLUGIN.Author = "Your Name"
PLUGIN.Version = V(0, 1, 0)
PLUGIN.ResourceId = 681

-- This is where your plugin will do its magic
```

### Python Example
```python
class PluginName:
    def __init__(self):
        self.Title = "Title of Plugin"
        self.Description = "This is what the plugin does"
        self.Author = "Your Name"
        self.Version = V(0, 1, 0)
        self.ResourceId = 681

    # This is where your plugin will do its magic
```
