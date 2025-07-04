# hafetch

A Neofetch-inspired terminal dashboard card for Home Assistant, themed using the [Catppuccin](https://github.com/catppuccin/catppuccin) color palette.

This card displays:
- System statistics (RAM, CPU, disk usage)
- Smart TV and automation states
- Light on/off status and brightness
- A terminal-style layout with blinking cursor
- Customizable ASCII art logo

---

## Screenshot

![screenshot](screenshot.png)

---

## Example Output

```
[user@homeassistant ~]$ hafetch
-------------------- OS: Home Assistant -------------------
  - Ram Usage: 64°C
  - CPU Usage: 5.7%
  - CPU Temp: 48.8%
  - Array Usage: 85.8%
  - Cache Usage: 12.1%
---------------------- Lighting Status --------------------
- Pc Tv: on
- Auto Light: on
- Neon Light: on
- Wall Light: on • 100%
- Wall Strip: off
- Under Desk: off
- Glorb Ball: on • 100%
[user@homeassistant ~]$
```

---

## Dependencies

This dashboard card requires:

### Home Assistant entities (replace with your own):

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

### Frontend

- [TailwindCSS Template Card](https://github.com/Geek-RCJ/TailwindCSS-Template-card) (install via HACS)

---

## Setup

1. Install the TailwindCSS Template Card through HACS
2. Create a new card in your dashboard:
   ```yaml
   type: custom:tailwindcss-template-card
   content: |
     <!-- Paste the HTML/CSS code from hafetch here -->
   ```
3. Replace all placeholder entity IDs with your actual Home Assistant sensors/devices.

---

## Customization

- Edit the `<pre>` block to use your own ASCII logo
- Adjust sensor names and formatting to fit your setup
- Change colors using Tailwind utility classes or Catppuccin references

---

## Credits

- Inspired by Neofetch
- Styled with the Catppuccin color palette
