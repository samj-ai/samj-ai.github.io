---
layout: default
title: Gallery of Light and Shade
nav_order: 1
has_children: false
---

# Gallery of Light and Shade

What can you do with shaders? All this can be yours ... !

<div id="glsl_editor" style="width: 500px; height: 500px;"></div>

<script type="text/javascript">
document.addEventListener('DOMContentLoaded', function() {
  // Make sure the library is loaded
  if (typeof GlslEditor === 'undefined') {
    console.error('GlslEditor library not loaded!');
    return;
  }
  
  try {
    const glslEditor = new GlslEditor('#glsl_editor', {
      canvas_size: 500,
      canvas_draggable: true,
      theme: 'monokai',
      multipleBuffers: true,
      watchHash: true,
      fileDrops: true,
      menu: true
    });
    
    // Set initial shader code
    glslEditor.setContent(`
#ifdef GL_ES
precision mediump float;
#endif

uniform vec2 u_resolution;
uniform float u_time;

void main() {
    vec2 st = gl_FragCoord.xy/u_resolution.xy;
    vec3 color = vec3(st.x, st.y, abs(sin(u_time)));
    gl_FragColor = vec4(color, 1.0);
}
    `);
    
    console.log('GlslEditor initialized successfully');
  } catch(e) {
    console.error('Error initializing GlslEditor:', e);
  }
});
</script>