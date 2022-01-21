<template lang="html">
  <div class="">
    <p>WHITE</p>
    <Board ref = "board" @moverequest = "RequestMove"/>
  </div>

</template>

<script>

import Board from "./Board.vue"
export default {
  components:{
    Board
  },
  mounted(){
    this.keepUpdated()

  },
  methods:{
    RequestMove(move){
      var url = "http://localhost:3080/move"
      var body = JSON.stringify(move)
      var Http = new XMLHttpRequest()
      Http.open('post',url,true)
      Http.setRequestHeader('Content-Type','text/plain')
      Http.send(body)
    },
    keepUpdated(){
      var url = "http://localhost:3080/update"
      var Http = new XMLHttpRequest()
      Http.onreadystatechange = () =>{
        if (Http.readyState == 4){
          //TODO: handle update

          this.$nextTick(()=>{
            //this.keepUpdated()
          })
        }
      }
      Http.open('get',url,true)
      Http.setRequestHeader('Content-Type','text/plain')
      Http.send()
    }
  },

}
</script>

<style lang="css" scoped>
</style>
