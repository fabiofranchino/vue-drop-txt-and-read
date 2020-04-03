<template>
  <div class="drop" 
    :class="getClasses" 
    @dragover.prevent="dragOver" 
    @dragleave.prevent="dragLeave"
    @drop.prevent="drop($event)">

      <div class="md" v-html="md" v-if="textSource"></div>
      <h1 v-if="wrongFile">Wrong file type</h1>
      <h1 v-if="!textSource && !isDragging && !wrongFile">Drop <label for="uploadmymarkdownfile">(or pick)</label> a markdown file</h1>

      <input type="file" id="uploadmymarkdownfile" @change="requestUploadFile" />

  </div>
</template>



<script>
import marked from 'marked'

export default {
  name: 'DropAnImage',
  data(){
    return{
      isDragging:false,
      wrongFile:false,
      textSource:null
    }
  },
  computed:{
    getClasses(){
      return {isDragging: this.isDragging}
    },
    md(){
      return marked(this.textSource)
    }
  },
  methods:{
    dragOver(){
      this.isDragging = true
    },
    dragLeave(){
      this.isDragging = false
    },
    drop(e){
      let files = e.dataTransfer.files
      this.process(files)
    },

    requestUploadFile(){
      var src = this.$el.querySelector('#uploadmymarkdownfile')
      let files = src.files
      this.process(files)
    },

    process(files){
      this.wrongFile = false

      // allows only 1 file
      if (files.length === 1) {

        let file = files[0]

        // allows text only
        if (file.type.indexOf('text/') >= 0) {

          var reader = new FileReader()
          reader.onload = f => {
            this.textSource = f.target.result
            this.isDragging = false
          }

          // this is the method to read a text file content
          reader.readAsText(file)
        }else{
          this.wrongFile = true
          this.textSource = null
          this.isDragging = false
        }
      }
    }

    
  }
}
</script>



<style scoped>
.drop{
  width: 100%;
  height: 100%;
  background-color: #eee;
  border:10px solid #eee;

  display: flex;
  align-items: center;
  justify-content: center;

  padding: 1rem;
  transition: background-color .2s ease-in-out;

  font-family: sans-serif;
}

.isDragging{
  background-color: #999;
  border-color: #fff;
}

.md{
  width: 100%;
  height: 100%;
  object-fit: contain;
  resize: none;
  overflow: hidden;
  overflow-y: auto;
}

input[type="file"]{
  display: none;
}

label{
  text-decoration: underline;
}
</style>
