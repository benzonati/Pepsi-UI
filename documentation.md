# Library v0.32 Documentation

This library provides a robust and customizable GUI creation system for Roblox. It includes functions for creating windows, tabs, sections, and various UI elements like toggles, sliders, dropdowns, and more.

---

## Table of Contents
1. [CreateWindow](#createwindow)
2. [CreateTab](#createtab)
3. [CreateSection](#createsection)
4. [AddLabel](#addlabel)
5. [AddToggle](#addtoggle)
6. [AddTextbox](#addtextbox)
7. [AddSlider](#addslider)
8. [AddButton](#addbutton)
9. [AddKeybind](#addkeybind)
10. [AddDropdown](#adddropdown)
11. [AddSearchBox](#addsearchbox)
12. [AddColorpicker](#addcolorpicker)
13. [AddPersistence](#addpersistence)
14. [CreateDesigner](#createdesigner)
15. [Shared Functions](#shared-functions)

---

## CreateWindow
Creates a new window for the GUI.

### Syntax
```lua
CreateWindow(Options) -> Window
```

### Options
- **Name** (`string`): The name of the window. Default: `"Window Name"`.
- **Theme** (`JSON`): Custom theme for the window.
- **Themeable** (`boolean`): Whether the window is themeable. Default: `true`.
- **Background** (`string | number | table`): Background settings for the window.
  - **Asset** (`string | number`): Asset ID for the background.
  - **Transparency** (`number`): Transparency of the background.
  - **Visible** (`boolean | number`): Visibility of the background.

### Example
```lua
local Window = Library.CreateWindow({
    Name = "My Window",
    Themeable = true,
    Background = {
        Asset = "rbxassetid://13337",
        Transparency = 0.5,
        Visible = true
    }
})
```

---

## CreateTab
Creates a new tab within a window.

### Syntax
```lua
CreateTab(Options) -> Tab
```

### Options
- **Name** (`string`): The name of the tab.
- **Image** (`string | number`): Icon for the tab.

### Example
```lua
local Tab = Window.CreateTab({
    Name = "Main Tab",
    Image = "rbxassetid://133337"
})
```

---

## CreateSection
Creates a new section within a tab.

### Syntax
```lua
CreateSection(Options) -> Section
```

### Options
- **Name** (`string`): The name of the section.
- **Side** (`string`): The side of the tab where the section will be placed (`"Left"` or `"Right"`).

### Example
```lua
local Section = Tab.CreateSection({
    Name = "Settings",
    Side = "Left"
})
```

---

## AddLabel
Adds a label to a section.

### Syntax
```lua
AddLabel(Options) -> Label
```

### Options
- **Text** (`string`): The text displayed in the label.
- **Flag** (`string`): A unique identifier for the label.
- **UnloadValue** (`any`): Value to set when the label is unloaded.
- **UnloadFunc** (`function`): Function to call when the label is unloaded.

### Example
```lua
local Label = Section.AddLabel({
    Text = "Welcome!",
    Flag = "WelcomeLabel"
})
```

---

## AddToggle
Adds a toggle switch to a section.

### Syntax
```lua
AddToggle(Options) -> ToggleInfo
```

### Options
- **Name** (`string`): The name of the toggle.
- **Value** (`boolean`): Default state of the toggle.
- **Callback** (`function`): Function to call when the toggle state changes.
- **Flag** (`string`): A unique identifier for the toggle.
- **Keybind** (`table`): Keybind settings for the toggle.

### Example
```lua
local Toggle = Section.AddToggle({
    Name = "Enable Feature",
    Value = false,
    Callback = function(NewValue)
        print("Toggle state:", NewValue)
    end,
    Flag = "FeatureToggle"
})
```

---

## AddTextbox
Adds a textbox to a section.

### Syntax
```lua
AddTextbox(Options) -> Textbox
```

### Options
- **Name** (`string`): The name of the textbox.
- **Value** (`string | number`): Default value of the textbox.
- **Callback** (`function`): Function to call when the text changes.
- **Placeholder** (`string`): Placeholder text.
- **Type** (`string`): Type of input (`"number"` or `"string"`).

### Example
```lua
local Textbox = Section.AddTextbox({
    Name = "Username",
    Value = "",
    Placeholder = "Enter your username",
    Callback = function(NewValue)
        print("Username:", NewValue)
    end
})
```

---

## AddSlider
Adds a slider to a section.

### Syntax
```lua
AddSlider(Options) -> Slider
```

### Options
- **Name** (`string`): The name of the slider.
- **Value** (`number`): Default value of the slider.
- **Min** (`number`): Minimum value.
- **Max** (`number`): Maximum value.
- **Callback** (`function`): Function to call when the slider value changes.

### Example
```lua
local Slider = Section.AddSlider({
    Name = "Volume",
    Value = 50,
    Min = 0,
    Max = 100,
    Callback = function(NewValue)
        print("Volume set to:", NewValue)
    end
})
```

---

## AddButton
Adds a button to a section.

### Syntax
```lua
AddButton(Options) -> Buttons
```

### Options
- **Name** (`string`): The name of the button.
- **Callback** (`function`): Function to call when the button is pressed.

### Example
```lua
local Button = Section.AddButton({
    Name = "Click Me",
    Callback = function()
        print("Button clicked!")
    end
})
```

---

## AddKeybind
Adds a keybind to a section.

### Syntax
```lua
AddKeybind(Options) -> Keybind
```

### Options
- **Name** (`string`): The name of the keybind.
- **Value** (`EnumItem`): Default keybind (e.g., `Enum.KeyCode.F`).
- **Callback** (`function`): Function to call when the keybind is pressed.

### Example
```lua
local Keybind = Section.AddKeybind({
    Name = "Toggle Menu",
    Value = Enum.KeyCode.F,
    Callback = function()
        print("Menu toggled!")
    end
})
```

---

## AddDropdown
Adds a dropdown menu to a section.

### Syntax
```lua
AddDropdown(Options) -> Dropdown
```

### Options
- **Name** (`string`): The name of the dropdown.
- **List** (`table | Instance | Enum`): List of items for the dropdown.
- **Callback** (`function`): Function to call when an item is selected.

### Example
```lua
local Dropdown = Section.AddDropdown({
    Name = "Select Item",
    List = {"Option 1", "Option 2", "Option 3"},
    Callback = function(SelectedValue)
        print("Selected:", SelectedValue)
    end
})
```

---

## AddSearchBox
Adds a search box to a section.

### Syntax
```lua
AddSearchBox(Options) -> SearchBox
```

### Options
- **Name** (`string`): The name of the search box.
- **List** (`table | Instance | Enum`): List of items to search through.
- **Callback** (`function`): Function to call when a search result is selected.

### Example
```lua
local SearchBox = Section.AddSearchBox({
    Name = "Search",
    List = {"Apple", "Banana", "Cherry"},
    Callback = function(SelectedValue)
        print("Selected:", SelectedValue)
    end
})
```

---

## AddColorpicker
Adds a color picker to a section.

### Syntax
```lua
AddColorpicker(Options) -> Colorpicker
```

### Options
- **Name** (`string`): The name of the color picker.
- **Value** (`Color3`): Default color.
- **Callback** (`function`): Function to call when the color changes.

### Example
```lua
local Colorpicker = Section.AddColorpicker({
    Name = "Pick Color",
    Value = Color3.new(1, 0, 0),
    Callback = function(NewColor)
        print("Selected color:", NewColor)
    end
})
```

---

## AddPersistence
Adds a persistence feature to a section.

### Syntax
```lua
AddPersistence(Options) -> Persistence
```

### Options
- **Name** (`string`): The name of the persistence feature.
- **Value** (`string`): Default file name.
- **Callback** (`function`): Function to call when the file is saved or loaded.

### Example
```lua
local Persistence = Section.AddPersistence({
    Name = "Save Settings",
    Value = "MySettings",
    Callback = function(FilePath, FileName)
        print("Settings saved to:", FilePath)
    end
})
```

---

## CreateDesigner
Creates a designer for customizing the GUI.

### Syntax
```lua
CreateDesigner(Options) -> Designer
```

### Options
- **Background** (`string | number | table`): Background settings for the designer.
- **Image** (`string | number`): Icon for the designer.
- **Info** (`string | table`): Additional information displayed in the designer.

### Example
```lua
local Designer = Window.CreateDesigner({
    Background = {
        Asset = "rbxassetid://13337",
        Transparency = 0.5
    },
    Info = "Customize your GUI here!"
})
```

---

## Shared Functions
Shared utility functions provided by the library.

### Functions
- **updatecolors**: Re-applies all colors from the designer.
- **Wait**: Waits for a specified time (only if the library is not unloaded).
- **removeSpaces**: Removes spaces from a string.
- **Color3ToHex**: Converts a `Color3` to a hex string.
- **Color3FromHex**: Converts a hex string to a `Color3`.
- **textToSize**: Calculates the size of a text string.
- **Instance_new**: Creates a new instance with syn.protect_gui applied.

### Example
```lua
local HexColor = Library.Subs.Color3ToHex(Color3.new(1, 0, 0))
print("Hex Color:", HexColor)
```

---

This documentation provides a comprehensive guide to using the library. For further assistance, refer to the examples or explore the library's source code.
