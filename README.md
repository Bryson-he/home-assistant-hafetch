# hafetch

A Neofetch-inspired terminal dashboard card for Home Assistant, themed with the [Catppuccin](https://github.com/catppuccin/catppuccin) palette.

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

## Code

Paste this into a `custom:tailwindcss-template-card` in your dashboard (replace sensors/lights with your own):

```html
<div class="font-mono text-sm p-4 rounded-xl w-full overflow-x-auto" style="background-color:#1e1e2e; color:#cdd6f4;">
  <div class="grid grid-cols-[auto_1fr] gap-6">
    <pre class="leading-tight whitespace-pre-wrap text-[#89b4fa]">
                      ......                      
                    ..........                    
                  ..............                  
                 ................                 
               ....................               
             ........................             
           ............    ............           
         ............        ............         
       ..............        ..............       
     ................        ................     
    ...................    ...................    
  .....................    .....................  
 ......................    ...................... 
.......................    ........     ..........
.......................    .......       .........
.......................    ......         ........
.......................    ......        .........
..........     ........    ....        ...........
.........        ......    ..     ................
........         ......         ..................
.........        ......       ....................
..............     ....      .....................
................     ..    .......................
..................         .......................
....................       .......................
 .....................     ...................... 
</pre>

    <div class="text-base">
      <div><span class="text-[#89dceb]">[user@homeassistant ~]$</span> hafetch</div>
      <div class="text-[#f9e2af]">-------------------- <span class="text-[#a6e3a1]">OS: Home Assistant</span> -------------------</div>
      <div>  - <span class="text-[#f9e2af]">Ram Usage</span>: {{ states('sensor.ram_usage') | round(0) }}°C</div>
      <div>  - <span class="text-[#f38ba8]">CPU Usage</span>: {{ states('sensor.cpu_usage') }}%</div>
      <div>  - <span class="text-[#cba6f7]">CPU Temp</span>: {{ states('sensor.cpu_temp') }}%</div>
      <div>  - <span class="text-[#89b4fa]">Array Usage</span>: {{ states('sensor.disk_array_usage') }}%</div>
      <div>  - <span class="text-[#94e2d5]">Cache Usage</span>: {{ states('sensor.disk_cache_usage') }}%</div>
      <div class="text-[#f9e2af]">---------------------- <span class="text-[#a6e3a1]">Lighting Status</span> --------------------</div>
      <div>- <span class="text-[#89b4fa]">Pc Tv</span>: {{ states('media_player.tv_display') }}</div>
      <div>- <span class="text-[#a6e3a1]">Auto Light</span>: {{ states('automation.auto_lighting') }}</div>
      <div>- <span class="text-[#f5c2e7]">Neon Light</span>: {{ states('switch.feature_neon') }}</div>
      <div>- <span class="text-[#fab387]">Wall Light</span>: 
        {% if is_state('light.wall_lamp', 'on') %}
          on • {{ (state_attr('light.wall_lamp', 'brightness') | float * 100 / 255) | round(0) }}%
        {% else %}
          off
        {% endif %}
      </div>
      <div>- <span class="text-[#f9e2af]">Wall Strip</span>: 
        {% if is_state('light.strip_livingroom', 'on') %}
          on • {{ (state_attr('light.strip_livingroom', 'brightness') | float * 100 / 255) | round(0) }}%
        {% else %}
          off
        {% endif %}
      </div>
      <div>- <span class="text-[#cba6f7]">Under Desk</span>: 
        {% if is_state('light.desk_strip', 'on') %}
          on • {{ (state_attr('light.desk_strip', 'brightness') | float * 100 / 255) | round(0) }}%
        {% else %}
          off
        {% endif %}
      </div>
      <div>- <span class="text-[#94e2d5]">Glorb Ball</span>: 
        {% if is_state('light.rgb_ball', 'on') %}
          on • {{ (state_attr('light.rgb_ball', 'brightness') | float * 100 / 255) | round(0) }}%
        {% else %}
          off
        {% endif %}
      </div>
      <div><span class="text-[#89dceb]">[user@homeassistant ~]$ </span><span class="cursor">&nbsp;</span></div>
    </div>
  </div>
</div>

<style>
@keyframes blink-caret {
  0%, 100% { background-color: transparent; }
  50% { background-color: #cdd6f4; }
}

.cursor {
  display: inline-block;
  width: 10px;
  height: 1em;
  animation: blink-caret 0.75s step-end infinite;
}
</style>
```

---

## Instructions

1. Install **TailwindCSS Template Card** from HACS
2. Add a new TailwindCSS card
3. Replace all entity IDs with your own sensors/lights/media players
4. Customize the ASCII block in the `<pre>` tag if you'd like

---

## Credits

- Inspired by [Neofetch](https://github.com/dylanaraps/neofetch)
- Styled with the [Catppuccin](https://github.com/catppuccin/catppuccin) color palette
