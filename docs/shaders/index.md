---
layout: default
title: Gallery of Light and Shade
nav_order: 1
has_children: false
---

# Gallery of Light and Shade

What can you do with shaders? All this can be yours ... !

<body>
    <div id="glsl_editor"></div>
</body>
<script type="text/javascript">
    const glslEditor = new GlslEditor('#glsl_editor', { 
        canvas_size: 500,
        canvas_draggable: true,
        theme: 'monokai',
        multipleBuffers: true,
        watchHash: true,
        fileDrops: true,
        menu: true
    });
</script>