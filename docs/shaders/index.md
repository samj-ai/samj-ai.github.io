---
layout: default
title: Gallery of Light and Shade
nav_order: 1
has_children: false
---

# Gallery of Light and Shade

What can you do with shaders? All this can be yours…!

## Test widget

{% include glsl-widget-test.html id="test1" %}

## Rainbow Gradient

A simple gradient that shifts colors over time:

{% include glsl-widget.html 
   id="rainbow-gradient"
   width="600"
   height="400"
   code="
// Rainbow gradient shader
precision mediump float;

uniform float time;
uniform vec2 resolution;

void main() {
    vec2 uv = gl_FragCoord.xy / resolution.xy;
    
    // Simple color gradient based on position and time
    vec3 color = vec3(
        0.5 + 0.5 * sin(time + uv.x * 6.0),
        0.5 + 0.5 * sin(time + uv.y * 6.0),
        0.5 + 0.5 * sin(time + (uv.x + uv.y) * 6.0)
    );
    
    gl_FragColor = vec4(color, 1.0);
}
   "
%}

## Concentric Circles

Create a hypnotic pattern with animated circles:

{% include glsl-widget.html 
   id="concentric-circles"
   width="600"
   height="400"
   code="
// Concentric circles shader
precision mediump float;

uniform float time;
uniform vec2 resolution;

void main() {
    vec2 uv = gl_FragCoord.xy / resolution.xy;
    vec2 center = vec2(0.5, 0.5);
    
    // Calculate distance from center
    float dist = distance(uv, center);
    
    // Create rings based on distance and time
    float rings = sin(dist * 20.0 - time * 2.0) * 0.5 + 0.5;
    
    // Add some color variation
    vec3 color = vec3(rings * uv.x, rings * 0.5, rings * uv.y);
    
    gl_FragColor = vec4(color, 1.0);
}
   "
%}

## Plasma Effect

Create a classic plasma effect:

{% include glsl-widget.html 
   id="plasma-effect"
   width="600"
   height="400"
   code="
// Plasma effect shader
precision mediump float;

uniform float time;
uniform vec2 resolution;

void main() {
    vec2 uv = gl_FragCoord.xy / resolution.xy;
    
    // Create plasma pattern
    float v1 = sin((uv.x * 10.0) + time);
    float v2 = sin((uv.y * 10.0) + time);
    float v3 = sin((uv.x * 10.0) + (uv.y * 10.0) + time);
    float v4 = sin(sqrt(100.0 * ((uv.x - 0.5) * (uv.x - 0.5) + (uv.y - 0.5) * (uv.y - 0.5))) + time);
    
    // Combine patterns
    float plasma = (v1 + v2 + v3 + v4) / 4.0;
    
    // Map to colors
    vec3 color = vec3(
        sin(plasma * 3.14159 * 2.0) * 0.5 + 0.5,
        sin(plasma * 3.14159 * 2.0 + 2.094) * 0.5 + 0.5,
        sin(plasma * 3.14159 * 2.0 + 4.188) * 0.5 + 0.5
    );
    
    gl_FragColor = vec4(color, 1.0);
}
   "
%}