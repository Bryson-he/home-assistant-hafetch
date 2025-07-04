<h1>hafetch</h1>
<p>A Neofetch-inspired terminal-style dashboard card for Home Assistant, styled with the <a href="https://github.com/catppuccin/catppuccin">Catppuccin</a> palette.</p>

<h2>Screenshot</h2>
<p>
  <img src="screenshot.png" alt="Hafetch Screenshot" width="600">
</p>

<h2>Example Output</h2>
<pre>
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
</pre>

<h2>Instructions</h2>
<ol>
  <li>Install <a href="https://github.com/usernein/tailwindcss-template-card">TailwindCSS Template Card</a> from HACS</li>
  <li>Restart Home Assistant if required</li>
  <li>Add a new card in your dashboard and select <strong>TailwindCSS Template Card</strong> from the list</li>
  <li>Paste the code below into the card content</li>
  <li>Replace the entities in the template with your own sensors/lights/media players</li>
</ol>

<h2>Code</h2>
<pre><code>&lt;div class="font-mono text-sm p-4 rounded-xl w-full overflow-x-auto" style="background-color:#1e1e2e; color:#cdd6f4;"&gt;
  &lt;div class="grid grid-cols-[auto_1fr] gap-6"&gt;
    &lt;pre class="leading-tight whitespace-pre-wrap text-[#89b4fa]"&gt;
      ...ASCII block...
    &lt;/pre&gt;
    &lt;div class="text-base"&gt;
      &lt;div&gt;&lt;span class="text-[#89dceb]"&gt;[user@homeassistant ~]$&lt;/span&gt; hafetch&lt;/div&gt;
      &lt;div class="text-[#f9e2af]"&gt;-------------------- &lt;span class="text-[#a6e3a1]"&gt;OS: Home Assistant&lt;/span&gt; -------------------&lt;/div&gt;
      &lt;div&gt;  - &lt;span class="text-[#f9e2af]"&gt;Ram Usage&lt;/span&gt;: {{ states('sensor.ram_usage') | round(0) }}°C&lt;/div&gt;
      &lt;div&gt;  - &lt;span class="text-[#f38ba8]"&gt;CPU Usage&lt;/span&gt;: {{ states('sensor.cpu_usage') }}%&lt;/div&gt;
      &lt;div&gt;  - &lt;span class="text-[#cba6f7]"&gt;CPU Temp&lt;/span&gt;: {{ states('sensor.cpu_temp') }}°C&lt;/div&gt;
      &lt;div&gt;  - &lt;span class="text-[#89b4fa]"&gt;Array Usage&lt;/span&gt;: {{ states('sensor.disk_array_usage') }}%&lt;/div&gt;
      &lt;div&gt;  - &lt;span class="text-[#94e2d5]"&gt;Cache Usage&lt;/span&gt;: {{ states('sensor.disk_cache_usage') }}%&lt;/div&gt;
      &lt;div class="text-[#f9e2af]"&gt;---------------------- &lt;span class="text-[#a6e3a1]"&gt;Lighting Status&lt;/span&gt; --------------------&lt;/div&gt;
      &lt;div&gt;- &lt;span class="text-[#89b4fa]"&gt;Pc Tv&lt;/span&gt;: {{ states('media_player.tv_display') }}&lt;/div&gt;
      &lt;div&gt;- &lt;span class="text-[#a6e3a1]"&gt;Auto Light&lt;/span&gt;: {{ states('automation.auto_lighting') }}&lt;/div&gt;
      &lt;div&gt;- &lt;span class="text-[#f5c2e7]"&gt;Neon Light&lt;/span&gt;: {{ states('switch.feature_neon') }}&lt;/div&gt;
      &lt;div&gt;- &lt;span class="text-[#fab387]"&gt;Wall Light&lt;/span&gt;: 
        {% if is_state('light.wall_lamp', 'on') %}
          on • {{ (state_attr('light.wall_lamp', 'brightness') | float * 100 / 255) | round(0) }}%
        {% else %}
          off
        {% endif %}
      &lt;/div&gt;
      &lt;div&gt;- &lt;span class="text-[#f9e2af]"&gt;Wall Strip&lt;/span&gt;: 
        {% if is_state('light.strip_livingroom', 'on') %}
          on • {{ (state_attr('light.strip_livingroom', 'brightness') | float * 100 / 255) | round(0) }}%
        {% else %}
          off
        {% endif %}
      &lt;/div&gt;
      &lt;div&gt;- &lt;span class="text-[#cba6f7]"&gt;Under Desk&lt;/span&gt;: 
        {% if is_state('light.desk_strip', 'on') %}
          on • {{ (state_attr('light.desk_strip', 'brightness') | float * 100 / 255) | round(0) }}%
        {% else %}
          off
        {% endif %}
      &lt;/div&gt;
      &lt;div&gt;- &lt;span class="text-[#94e2d5]"&gt;Glorb Ball&lt;/span&gt;: 
        {% if is_state('light.rgb_ball', 'on') %}
          on • {{ (state_attr('light.rgb_ball', 'brightness') | float * 100 / 255) | round(0) }}%
        {% else %}
          off
        {% endif %}
      &lt;/div&gt;
      &lt;div&gt;&lt;span class="text-[#89dceb]"&gt;[user@homeassistant ~]$ &lt;/span&gt;&lt;span class="cursor"&gt;&amp;nbsp;&lt;/span&gt;&lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;

&lt;style&gt;
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
&lt;/style&gt;
</code></pre>

<h2>Credits</h2>
<ul>
  <li>Inspired by <a href="https://github.com/dylanaraps/neofetch">Neofetch</a></li>
  <li>Styled with the <a href="https://github.com/catppuccin/catppuccin">Catppuccin</a> color palette</li>
  <li>Powered by <a href="https://github.com/usernein/tailwindcss-template-card">TailwindCSS Template Card</a></li>
</ul>
