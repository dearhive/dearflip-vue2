# DearFlip Vue 2 Integration

A simple integration of DearFlip PDF FlipBook with Vue 2. [Demo](https://dearhive.github.io/dearflip-vue2/)

## Overview

This project demonstrates how to use the DearFlip PDF FlipBook viewer within a Vue 2 application. DearFlip provides a realistic book-like page flip experience for PDFs and images.

## Setup

1. Download the DearFlip library from [https://dearflip.com/](https://dearflip.com/)
2. Extract the downloaded ZIP file
3. Copy the `dflip` folder to your project's root directory
4. Make sure your project structure looks like:
   ```
   /
   ├── dflip/
   │   ├── css/
   │   ├── js/
   │       └── libs/
   │   ├── sound/
   │   └── images
   ├── index.html
   └── README.md
   ```

## Usage

### 1. Include Required Files

In your HTML file, include the necessary CSS and JavaScript files:

```html
<link rel="stylesheet" href="dflip/css/dflip.min.css">
<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
<script src="dflip/js/libs/jquery.min.js"></script>
<script src="dflip/js/dflip.min.js"></script>
```

### 2. Create a DearFlip Viewer Component

Register a Vue component that will serve as the wrapper for the DearFlip viewer:

```javascript
Vue.component('dear-flip-viewer', {
  template: `
    <div class="dear-flip-viewer">
      <div ref="flipbook" data-option="dflipOptions" class="df-element"></div>
    </div>
  `,
  props: {
    options: {
      type: Object,
      default: () => ({})
    }
  },
  mounted() {
    this.initFlipbook();
  },
  methods: {
    initFlipbook() {
      window.dFlipLocation = "/dflip/";
      window.dflipOptions = this.options;
    }
  }
});
```

### 3. Use the Component in Your Vue Instance

```javascript
new Vue({
  el: '#app',
  data: {
    flipbookOptions: {
      source: '/pdf/your-pdf-file.pdf',
      // Add any custom options here
    }
  }
});
```

### 4. Add the Component to Your HTML

```html
<div id="app">
  <dear-flip-viewer :options="flipbookOptions"></dear-flip-viewer>
</div>
```

## Configuration Options

DearFlip supports various configuration options that can be passed through the `flipbookOptions` object:

```javascript
flipbookOptions: {
  // PDF source
  source: '/pdf/your-pdf-file.pdf',
  
  // General settings
  webgl: true,           // Use WebGL rendering
  
  // UI controls
  autoEnableOutline: false,  // Auto enable outline
  autoEnableThumbnail: false,  // Auto enable thumbnails
  
  // Page settings
  duration: 800,          // Page turn duration in ms
  
  // ... more options
}
```

For a complete list of options, please refer to the [DearFlip documentation](https://dearflip.com/documentation/).

## Browser Compatibility

DearFlip works with modern browsers that support WebGL, including:
- Chrome
- Firefox
- Safari
- Edge

## License

This integration example is for demonstration purposes. Make sure to purchase an appropriate license for DearFlip before using it in production.

Visit [https://dearflip.com/](https://dearflip.com/) for more information about DearFlip and licensing options. 