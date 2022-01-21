<template lang="html">
  <div class="face piece"  ref = "face"  >

  </div>
</template>

<script>
export default {
  props:[
    'position',
  ],
  data(){
    return {
      x:2,
      y:0,
    }
  },
  mounted(){


    document.getElementById(this.position).appendChild(this.$refs.face)


  },
  methods:{
    generateStyle(){

    }
  }
}
</script>

<style lang="css" scoped>

  .face{
    position: absolute;
    width:2em;
    height:2em;
    background: #0000;
    background-image: url("../assets/pieces.png");
    background-size:200px;
  }
</style>
