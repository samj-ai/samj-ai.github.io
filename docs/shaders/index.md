---
layout: default
title: Gallery of Light and Shade
nav_order: 1
has_children: false
---

# Gallery of Light and Shade

What can you do with shaders? All this can be yours ... !

# Testing Multiple Shaders in One Page

Below are two different GLSL fragments, each in its own widget.

### 1. A simple gradient:

{% include shader_widget.html shader_code="{% raw %}
#ifdef GL_ES
precision mediump float;
#endif

uniform float u_time;
void main() {
  vec2 uv = gl_FragCoord.xy / 300.0;
  gl_FragColor = vec4(uv, 0.5 + 0.5*sin(u_time), 1.0);
}
{% endraw %}" %}

---

### 2. Pulsing circle:

{% include shader_widget.html shader_code="{% raw %}
#ifdef GL_ES
precision mediump float;
#endif

uniform float u_time;
void main() {
  vec2 uv = (gl_FragCoord.xy - vec2(300.0, 150.0)) / 150.0;
  float r = length(uv);
  float pulse = 0.5 + 0.5 * sin(u_time * 4.0);
  float circle = smoothstep(pulse*0.8, pulse*0.82, r);
  gl_FragColor = vec4(vec3(1.0 - circle), 1.0);
}
{% endraw %}" %}