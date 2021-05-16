<template>
  <div id="app">
    <div class="container">
      <h2>Workshop 2</h2>
      <hr>
      <div v-if="!image">
        <input type="file" class="form-control" @change="onFileChange">
      </div>
      <div v-else>
        <img :src="image" class="img-fluid">
        <button class="btn btn-danger" @click="removeImage">Remove</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      image: ""
    }
  },
  methods: {
    onFileChange: function(e){
      console.log(e.target.files);
      var files = e.target.files
      if(!files.length)
        return
      this.createImage(files[0])
    },
    createImage(files){
      var reader = new FileReader();
      reader.onload = (e) => {
        this.image = e.target.result;
      }
      reader.readAsDataURL(files)
    },
    removeImage(){
      this.image = ""
    }
  },
}
</script>
