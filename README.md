
**hafetch**

A Neofetch-inspired terminal-style dashboard card for Home Assistant, styled with the [Catppuccin](https://github.com/catppuccin/catppuccin) color palette.

---

### 📸 Screenshot

`screenshot.png`
(Place this file in the same directory as the README)

---

### 📟 Sample Output

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

### ⚙️ Requirements

* Home Assistant
* [TailwindCSS Template Card](https://github.com/usernein/tailwindcss-template-card) (install via HACS)

Entities you can replace:

* `sensor.ram_usage`, `sensor.cpu_usage`, `sensor.cpu_temp`, `sensor.disk_array_usage`, `sensor.disk_cache_usage`
* `media_player.tv_display`, `automation.auto_lighting`, `switch.feature_neon`
* `light.wall_lamp`, `light.strip_livingroom`, `light.desk_strip`, `light.rgb_ball`

---

### 🧩 How to Use

1. Install the TailwindCSS Template Card from HACS
2. Add a new card from the UI → select **TailwindCSS Template Card**
3. Paste the following into the card content:

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
      <div>  - <span class="text-[#cba6f7]">CPU Temp</span>: {{ states('sensor.cpu_temp') }}°C</div>
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
