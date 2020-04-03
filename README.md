# Vue.js component to drag&drop text and markdown with on-the-fly source reader

This is a follow-up of my previous example about drag&drop images using Vue.js.
They are examples about how to allow users drop images in the browser in a Vue app.
There are two components:

- `DropText` to read and show generic text files
- `DropMarkdown` to render markdown files using marked

## Usage

```html
<template>
  <div id="app">
      <DropText />
  </div>
</template>

<script>
import DropAnImage from './components/DropText.vue'

export default {
  components: {
    DropText
  }
}
</script>
```



# Development

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
