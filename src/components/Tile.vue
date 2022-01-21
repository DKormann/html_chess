<template lang="html">
  <div class="tile"
  @mouseup= "mouseup"
  @mousedown = "mousedown">


  </div>
</template>

<script>
export default {
  props:[
    'position',

  ],
  data(){
    return {
      start:null
    }
  },

  methods:{
    alert(x){
      alert(x)
    },
    mousedown(){
      this.$emit('mousedownmessage',this.position)
    },
    mouseup (){
      this.$emit('mouseupmessage',this.position)
    }
  }
}
</script>
<style scoped src = "../css/Board.css"></style>
