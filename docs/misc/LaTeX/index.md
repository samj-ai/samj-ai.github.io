---
layout: default
title: Gallery of Light and Shade
---

# Gallery of Light and Shade

What can you do with shaders? All this and more...!

<div class="shader-grid">
  <!-- Individual shader entries will go here -->
  <div class="shader-item">
    <h2>My First Shader</h2>
    <div id="shader1" class="glsl-editor"></div>
    <p>Description of this amazing shader</p>
  </div>
  
  <!-- More shader items -->
</div>

<script>
  // Initialize the shader editors after the page loads
  document.addEventListener('DOMContentLoaded', function() {
    const shader1 = new GlslEditor('#shader1', {
      canvas_size: 300,
      canvas_draggable: true,
      theme: 'monokai',
      multipleBuffers: false,
      menu: false
    });
    
    // Set the initial shader code
    shader1.setContent(`
      #ifdef GL_ES
      precision mediump float;
      #endif

      uniform vec2 u_resolution;
      uniform float u_time;

      void main() {
        vec2 st = gl_FragCoord.xy/u_resolution.xy;
        st.x *= u_resolution.x/u_resolution.y;
        
        vec3 color = vec3(0.0);
        color = vec3(st.x, st.y, abs(sin(u_time)));
        
        gl_FragColor = vec4(color, 1.0);
      }
    `);
    
    // Initialize more shaders here
  });
</script>

<style>
  .shader-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 2rem;
    margin: 2rem 0;
  }
  
  .shader-item {
    padding: 1rem;
    border-radius: 8px;
    background: #f5f5f5;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  }
</style>