
```markdown
# 🖥️ hafetch

**A Neofetch-inspired terminal dashboard card for Home Assistant**, themed with the [Catppuccin](https://github.com/catppuccin/catppuccin) color palette.

This card displays:
- System stats (RAM, CPU, disk, etc.)
- Lighting and media status
- Color-coded values and blinking terminal-style cursor
- Custom ASCII art
- Fully responsive with TailwindCSS Template Card

---

## 📸 Screenshot

![hafetch screenshot](screenshot.png)

---

## 🧪 Example Output

```

\[user\@homeassistant \~]\$ hafetch
\-------------------- OS: Home Assistant -------------------

* Ram Usage: 64°C
* CPU Usage: 5.7%
* CPU Temp: 48.8%
* Array Usage: 85.8%
* Cache Usage: 12.1%
  \---------------------- Lighting Status --------------------
* Pc Tv: on
* Auto Light: on
* Neon Light: on
* Wall Light: on • 100%
* Wall Strip: off
* Under Desk: off
* Glorb Ball: on • 100%
  \[user\@homeassistant \~]\$

````

---

## 🛠️ Dependencies

This card uses:

- **Home Assistant** with the following **placeholder entities** (replace with your own):
  - `sensor.ram_usage`
  - `sensor.cpu_usage`
  - `sensor.cpu_temp`
  - `sensor.disk_array_usage`
  - `sensor.disk_cache_usage`
  - `media_player.tv_display`
  - `automation.auto_lighting`
  - `switch.feature_neon`
  - `light.wall_lamp`
  - `light.strip_livingroom`
  - `light.desk_strip`
  - `light.rgb_ball`

- **Frontend requirement**:
  - [TailwindCSS Template Card](https://github.com/Geek-RCJ/TailwindCSS-Template-card) (via HACS)

---

## ⚙️ Setup

1. Install **TailwindCSS Template Card** from HACS
2. Add a card in Home Assistant:
   ```yaml
   type: custom:tailwindcss-template-card
   content: |
     <!-- Paste the HTML/CSS from below -->
````

3. Replace all entity IDs with your actual devices/sensors.

---

## 🧩 Customization

* Swap the ASCII block in the `<pre>` section for your own logo or style
* Change colors to match your theme or devices
* Add/remove lines to reflect your setup

---

## 🔗 Credits

* Inspired by **Neofetch**
* Color palette by [Catppuccin](https://github.com/catppuccin/catppuccin)

```

---

✅ Place the `screenshot.png` file in the **root of the repo** (same directory as the `README.md`), and GitHub will automatically render it.

Would you like me to generate a matching `.gitignore`, `LICENSE`, or a sample release tag format for GitHub too?
```
