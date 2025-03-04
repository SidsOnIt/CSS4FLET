Flet Theme Manager

A dynamic styling library for Flet, the Python UI framework. ThemeManager adds live theme switching, group styling, and concurrent updates to Flet, making it easy to manage complex UIs without manual widget tweaking.

Live Updates: Instantly apply themes or style changes across all widgets.
Concurrent Processing: Uses ThreadPoolExecutor for fast, parallel updates.
Flexible Theming: Supports global themes, mode themes (e.g., light/dark), and group styles.
Error Handling: Gracefully handles widget quirks with logging.
Installation

Ensure Flet is installed: pip install flet
Copy theme_manager.py from this repo into your project directory.
Import and use it in your Flet app: from theme_manager import ThemeManager import flet as ft
Tagging Widgets for Updates

To apply styles with ThemeManager, tag your Flet controls using the data attribute with class or group keys. These tags determine which widgets get styled when you update themes or groups.

Use "class" to tag widgets for global style updates: ft.TextField(data={"class": "input"}) ft.ElevatedButton("Click", data={"class": "button"})
Use "group" to tag widgets for group-specific style updates: ft.TextField(data={"group": "input"}) ft.ElevatedButton("Click", data={"group": "button"})
Attach to multiple groups by listing them in "group" as a list or string: ft.TextField(data={"group": ["input", "interactive"]}) ft.ElevatedButton("Click", data={"group": "button interactive"})
Combine class and multiple groups for flexibility: ft.TextField(data={"class": "input", "group": ["input", "interactive"]}) ft.ElevatedButton("Click", data={"class": "button", "group": "button interactive"})
How It Works

ThemeManager traverses the control tree and applies styles to widgets based on their data tags.
"class" tags match global style updates (e.g., tm.update_style("bgcolor", "blue")).
"group" tags match group style updates (e.g., tm.update_group_style("button", "border_radius", 10)).
Widgets with multiple groups (e.g., "input interactive") receive styles from all matching groups.
Styles like bgcolor, border_radius, or shadow are applied only to tagged widgets with matching properties.
Notes

Performance: Optimized with caching (lru_cache) and threading.
Setup: Not a pip package—manually add theme_manager.py to your project.

Maintenance

I have left Flet for Flutter. You are free to assume this project and maintain it under a fork. I will not be maintaining this, but I didn’t want it to rot in my file store after all the time spent making it. If you assume this project, you must clearly indicate "Created by SGT Ian Tyler Speer" and then you can add "maintained by" or "improved by" with your name or whatever. I don’t really care—just tell me you forked it or published it and where, so I can put it on my resume and show potential employers I made it.

License

Use is free and unlimited for private or commercial use. For derivative works, or if it’s added to Flet itself, just give me credit: "Created by SGT Ian Tyler Speer". Same if you mod it to be a pip install—you must include "Created by SGT Ian Tyler Speer", then you can add "published by" or whatever with your name. I just want credit for this on my resume.

Contributing

Found a bug? Want more style properties? Open an issue or PR. This is a community gift—make it yours.

Credits

Crafted by SGT Ian Tyler Speer to bring dynamic styling to Flet. Born from the need to escape manual widget updates—enjoy the power.
