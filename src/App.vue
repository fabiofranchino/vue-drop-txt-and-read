<template>
  <div id="app">

    <div class="parent-wrapper">
      <DropText />
    </div>
    <div class="parent-wrapper">
      <DropMarkdown />
    </div>
    
  </div>
</template>

<script>
import DropText from './components/DropText.vue'
import DropMarkdown from './components/DropMarkdown.vue'

export default {
  name: 'app',
  components: {
    DropText, DropMarkdown
  }
}
</script>


<style>
*{
  box-sizing: border-box;
}

html, body, #app{
  width:100%;
  height:100%;
  padding: 0;
  margin: 0;
  overflow: hidden;
}
body{
  background-color: #fff;
  padding:1rem;
}

.parent-wrapper{
  margin-bottom:1rem;
  width:100%;
  height:50%; /* was 50% */

}
</style>