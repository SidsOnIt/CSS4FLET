# ThemeManager Class Manual

## Overview

The ThemeManager is a powerful theme management class for Flet applications, allowing dynamic styling and theming across your entire application with support for global themes, mode-based themes, and group-based styling.

## Key Features

- Global theme application
- Multiple mode themes (light, dark, custom)
- Group-based styling
- Dynamic theme toggling
- Concurrent theme application
- Logging and error handling

## Installation and Setup

### Prerequisites
- Python 3.7+
- Flet library
- Logging module

### Importing the Class
```python
from theme_manager import ThemeManager
import flet as ft
```

## Initialization

```python
def main(page: ft.Page):
    theme_manager = ThemeManager(page)
```

## Theme Configuration Methods

### 1. Global Theme
Sets a base theme applied to all controls:
```python
global_theme = {
    "padding": 10,
    "border_radius": 8,
    "font_family": "Roboto"
}
theme_manager.set_global_theme(global_theme)
```

### 2. Mode Themes
Define multiple themes that can be toggled:
```python
mode_themes = {
    'light': {
        'bgcolor': '#ffffff',
        'color': '#000000'
    },
    'dark': {
        'bgcolor': '#2c2c2c',
        'color': '#ffffff'
    }
}
theme_manager.load_mode_themes(mode_themes)
```

### 3. Group Themes
Apply styles to specific control groups:
```python
group_themes = {
    'button': {
        'color': '#ffffff',
        'border_radius': 50
    },
    'input': {
        'bgcolor': 'black',
        'border_radius': 5
    }
}
theme_manager.load_group_themes(group_themes)
```

## Core Methods

### Applying Themes

1. **Apply a Specific Theme**
```python
theme_manager.apply_theme('dark')  # Apply dark mode theme
```

2. **Toggle Between Themes**
```python
theme_manager.toggle_theme()  # Cycle through available themes
```

3. **Update Global Style**
```python
theme_manager.update_style('color', '#ff0000')  # Change color globally
```

### Group Theme Management

1. **Update Group Style**
```python
theme_manager.update_group_style('button', 'color', '#00ff00')
```

2. **Toggle Group**
```python
theme_manager.toggle_group('interactive')  # Enable/disable group styling
```

## Complete Loading Example

```python
def main(page: ft.Page):
    theme_manager = ThemeManager(page)
    
    # Load themes from your theme configuration
    theme_manager.loader(
        global_theme=global_theme(),
        mode_themes=mode_themes(),
        group_themes=group_themes(),
        initial_theme='dark'
    )
```

## Control Styling

To apply styles to controls, use the `data` attribute:

```python
button = ft.ElevatedButton(
    "Click Me", 
    data={'class': ['button', 'interactive']}
)
```

## Advanced Features

- Concurrent theme application
- Automatic style validation
- Flexible group and mode theming
- Logging for theme-related operations

## Performance Considerations

- Uses a thread pool for efficient theme application
- Supports up to 32 concurrent theme updates
- Minimizes UI blocking during theme changes

## Error Handling

- Logs warnings for invalid theme configurations
- Gracefully handles theme application errors
- Provides fallback mechanisms

## Limitations

- Requires manual configuration of control classes
- Some complex styling might require custom implementation
- Performance may vary with large numbers of controls

## Best Practices

1. Define themes in separate configuration files
2. Use consistent naming for style classes
3. Validate themes before loading
4. Handle potential theme application errors

## Cleanup

Always call cleanup when no longer needed:
```python
theme_manager.cleanup()
```

## Compatibility

- Compatible with Flet 0.8.0+
- Works with most Flet control types
- Supports dynamic theme updates

## Troubleshooting

- Ensure controls have `data` attribute for group/class styling
- Check logging output for theme application errors
- Verify theme dictionaries match expected structure

## License and Contribution

[Include your project's license and contribution guidelines]
```

## Example Theme Configuration File
```python
# themes.py
import flet as ft

def global_theme():
    return {
        "padding": 10,
        "border_radius": 8,
        "font_family": "Roboto"
    }

def mode_themes():
    return {
        'light': {...},
        'dark': {...}
    }

def group_themes():
    return {
        'button': {...},
        'input': {...}
    }

def get_theme():
    return [
        global_theme(),
        mode_themes(),
        group_themes()
    ]
```

## Version History

- v1.0.0: Initial release
- v1.1.0: Added group theme toggling
- v1.2.0: Improved concurrent theme application

## Contributing

Contributions are welcome! Please submit pull requests or file issues on the project repository.

Maintenance

I have left Flet for Flutter. You are free to assume this project and maintain it under a fork. I will not be maintaining this, but I didn’t want it to rot in my file store after all the time spent making it. If you assume this project, you must clearly indicate "Created by SGT Ian Tyler Speer" and then you can add "maintained by" or "improved by" with your name or whatever. I don’t really care—just tell me you forked it or published it and where, so I can put it on my resume and show potential employers I made it.

License

Use is free and unlimited for private or commercial use. For derivative works, or if it’s added to Flet itself, just give me credit: "Created by SGT Ian Tyler Speer". Same if you mod it to be a pip install—you must include "Created by SGT Ian Tyler Speer", then you can add "published by" or whatever with your name. I just want credit for this on my resume.

Contributing

Found a bug? Want more style properties? Open an issue or PR. This is a community gift—make it yours.

Credits

Crafted by SGT Ian Tyler Speer to bring dynamic styling to Flet. Born from the need to escape manual widget updates—enjoy the power.
