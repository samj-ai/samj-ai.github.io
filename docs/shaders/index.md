---
layout: default
title: Gallery of Light and Shade
nav_order: 1
has_children: false
---

# Gallery of Light and Shade

What can you do with shaders? All this can be yours ... !

<div class="shader-gallery">
  <div class="shader-grid" id="shader-grid">
    <!-- Shader items will be inserted here by JavaScript -->
  </div>
</div>

<style>
  .shader-gallery {
    margin: 2rem 0;
  }

  .shader-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 1.5rem;
  }

  .shader-item {
    border-radius: 8px;
    overflow: hidden;
    background: var(--color-bg-secondary, #f8f9fa);
    box-shadow: 0 4px 15px rgba(0,0,0,0.08);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  .shader-item:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.12);
  }

  .shader-canvas-container {
    position: relative;
    padding-top: 100%; /* Square aspect ratio */
    overflow: hidden;
  }

  .shader-canvas-container .glslCanvas {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  .shader-info {
    padding: 1rem;
  }

  .shader-title {
    margin: 0 0 0.5rem 0;
    font-size: 1.1rem;
    color: var(--color-text-primary, #333);
  }

  .shader-description {
    margin: 0;
    color: var(--color-text-secondary, #555);
    font-size: 0.9rem;
  }

  .shader-actions {
    display: flex;
    justify-content: space-between;
    margin-top: 1rem;
  }

  .shader-button {
    background: var(--color-btn-primary-bg, #4a5568);
    color: var(--color-btn-primary-text, white);
    border: none;
    padding: 0.4rem 0.8rem;
    border-radius: 4px;
    font-size: 0.8rem;
    cursor: pointer;
    transition: background 0.2s;
  }

  .shader-button:hover {
    background: var(--color-btn-primary-hover-bg, #2d3748);
  }

  .fullscreen-modal {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.85);
    z-index: 1000;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    padding: 2rem;
  }

  .fullscreen-modal.active {
    display: flex;
  }

  .fullscreen-container {
    width: 80%;
    max-width: 800px;
  }

  .fullscreen-actions {
    margin-top: 1rem;
    display: flex;
    justify-content: flex-end;
  }

  .close-button {
    background: #f44336;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    cursor: pointer;
  }
</style>

<!-- Fullscreen Modal -->
<div id="fullscreen-modal" class="fullscreen-modal">
  <div class="fullscreen-container">
    <div id="fullscreen-shader"></div>
    <div class="fullscreen-actions">
      <button class="close-button" onclick="closeFullscreen()">Close</button>
    </div>
  </div>
</div>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    // Collection of shaders
    const shaders = [
      {
        title: "Simple Gradient",
        description: "A basic RGB gradient based on coordinates",
        code: `
#ifdef GL_ES
precision mediump float;
#endif

uniform vec2 u_resolution;

void main() {
    vec2 st = gl_FragCoord.xy/u_resolution.xy;
    vec3 color = vec3(st.x, st.y, 0.5);
    gl_FragColor = vec4(color, 1.0);
}
        `
      },
      {
        title: "Pulsing Colors",
        description: "Animated color cycling with sine waves",
        code: `
#ifdef GL_ES
precision mediump float;
#endif

uniform vec2 u_resolution;
uniform float u_time;

void main() {
    vec2 st = gl_FragCoord.xy/u_resolution.xy;
    vec3 color = vec3(0.0);
    
    color = vec3(abs(sin(u_time)), 0.5, abs(cos(u_time)));
    color *= vec3(st.x, st.y, 1.0);
    
    gl_FragColor = vec4(color, 1.0);
}
        `
      },
      {
        title: "Concentric Circles",
        description: "Animated rings using distance fields",
        code: `
#ifdef GL_ES
precision mediump float;
#endif

uniform vec2 u_resolution;
uniform float u_time;

void main() {
    vec2 st = gl_FragCoord.xy/u_resolution.xy;
    st = st * 2.0 - 1.0;
    st.x *= u_resolution.x/u_resolution.y;
    
    float d = length(st);
    float pct = smoothstep(0.3, 0.31, d) - smoothstep(0.4, 0.41, d);
    pct += smoothstep(0.1, 0.11, d) - smoothstep(0.2, 0.21, d);
    
    vec3 color = vec3(pct) * vec3(sin(u_time) * 0.5 + 0.5, cos(u_time * 0.8) * 0.5 + 0.5, sin(u_time * 0.3) * 0.5 + 0.5);
    
    gl_FragColor = vec4(color, 1.0);
}
        `
      },
      {
        title: "Star Pattern",
        description: "Animated star pattern using polar coordinates",
        code: `
#ifdef GL_ES
precision mediump float;
#endif

uniform vec2 u_resolution;
uniform float u_time;

void main() {
    vec2 st = gl_FragCoord.xy/u_resolution.xy;
    st = st * 2.0 - 1.0;
    st.x *= u_resolution.x/u_resolution.y;
    
    float angle = atan(st.y, st.x);
    float radius = length(st);
    
    float f = cos(angle * 5.0 + u_time) * 0.5 + 0.5;
    f = 1.0 - smoothstep(f, f + 0.02, radius);
    
    gl_FragColor = vec4(f * vec3(0.9, 0.4, 0.1), 1.0);
}
        `
      }
    ];

    // Create the shader grid
    const shaderGrid = document.getElementById('shader-grid');
    
    // Create shader items
    shaders.forEach((shader, index) => {
      const shaderItem = document.createElement('div');
      shaderItem.className = 'shader-item';
      
      shaderItem.innerHTML = `
        <div class="shader-canvas-container">
          <div id="shader-canvas-${index}" class="shader-canvas"></div>
        </div>
        <div class="shader-info">
          <h3 class="shader-title">${shader.title}</h3>
          <p class="shader-description">${shader.description}</p>
          <div class="shader-actions">
            <button class="shader-button view-code-btn" data-index="${index}">View Code</button>
            <button class="shader-button fullscreen-btn" data-index="${index}">Fullscreen</button>
          </div>
        </div>
      `;
      
      shaderGrid.appendChild(shaderItem);
      
      // Initialize the shader editor after a short delay to ensure DOM is ready
      setTimeout(() => {
        try {
          window.editors = window.editors || [];
          
          const editor = new GlslEditor(`#shader-canvas-${index}`, {
            canvas_size: 300,
            canvas_draggable: false,
            theme: 'monokai',
            multipleBuffers: false,
            menu: false,
            lineNumbers: false
          });
          
          editor.setContent(shader.code.trim());
          window.editors[index] = editor;
          
          console.log(`Initialized shader ${index} successfully`);
        } catch (error) {
          console.error(`Failed to initialize shader ${index}:`, error);
        }
      }, 500);
    });
    
    // Add event listeners for buttons
    document.addEventListener('click', function(event) {
      // View Code button
      if (event.target.classList.contains('view-code-btn')) {
        const index = event.target.dataset.index;
        const editor = window.editors[index];
        const container = event.target.closest('.shader-item').querySelector('.shader-canvas-container');
        
        // Toggle code view
        if (editor) {
          const codeView = container.querySelector('.CodeMirror');
          if (codeView) {
            if (getComputedStyle(codeView).display === 'none' || codeView.style.display === 'none') {
              codeView.style.display = 'block';
              event.target.textContent = 'Hide Code';
            } else {
              codeView.style.display = 'none';
              event.target.textContent = 'View Code';
            }
          }
        }
      }
      
      // Fullscreen button
      if (event.target.classList.contains('fullscreen-btn')) {
        const index = event.target.dataset.index;
        showFullscreen(index);
      }
    });
  });
  
  // Global variable for fullscreen editor
  let fullscreenEditor = null;
  
  // Function to show fullscreen shader
  function showFullscreen(index) {
    const shader = window.shaders ? window.shaders[index] : document.querySelectorAll('.shader-item')[index];
    const shaderCode = window.editors[index].getContent();
    const modal = document.getElementById('fullscreen-modal');
    
    modal.classList.add('active');
    document.body.style.overflow = 'hidden';
    
    // Initialize the fullscreen editor if it doesn't exist
    if (!fullscreenEditor) {
      fullscreenEditor = new GlslEditor('#fullscreen-shader', {
        canvas_size: 600,
        canvas_draggable: false,
        theme: 'monokai',
        multipleBuffers: false,
        menu: false,
        lineNumbers: true
      });
    }
    
    // Set the shader code
    fullscreenEditor.setContent(shaderCode);
  }
  
  // Function to close fullscreen
  function closeFullscreen() {
    const modal = document.getElementById('fullscreen-modal');
    modal.classList.remove('active');
    document.body.style.overflow = '';
  }
</script>