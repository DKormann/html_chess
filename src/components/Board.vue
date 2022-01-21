<template lang="html">

  <div class="root">
    <div class="board">

      <div class = "row" v-for = "l in [0,1,2,3,4,5,6,7]" :key='l' :id = "l">
        <Tile
          v-for = "k in [0,1,2,3,4,5,6,7]" :key = "k"
          :class = "getcolor(k,l)"
          :id = "k+','+l"
          :position = "k+','+l"
          @mouseupmessage = "mouseup"
          @mousedownmessage = "mousedown"
          @click = "alert(33)"
        />
      </div>

      <Piece position = "0,3" class = "whitepiece Q"/>
      <Piece position = "0,4" class = "whitepiece K"/>
      <Piece position = "0,0" class = "whitepiece R"/>
      <Piece position = "0,7" class = "whitepiece R"/>
      <Piece position = "0,2" class = "whitepiece B"/>
      <Piece position = "0,5" class = "whitepiece B"/>
      <Piece position = "0,1" class = "whitepiece N"/>
      <Piece position = "0,6" class = "whitepiece N"/>
      <Piece position = "1,0" class = "whitepiece P"/>
      <Piece position = "1,1" class = "whitepiece P"/>
      <Piece position = "1,2" class = "whitepiece P"/>
      <Piece position = "1,3" class = "whitepiece P"/>
      <Piece position = "1,4" class = "whitepiece P"/>
      <Piece position = "1,5" class = "whitepiece P"/>
      <Piece position = "1,6" class = "whitepiece P"/>
      <Piece position = "1,7" class = "whitepiece P"/>

      <Piece position = "7,3" class = "blackpiece Q"/>
      <Piece position = "7,4" class = "blackpiece K"/>
      <Piece position = "7,0" class = "blackpiece R"/>
      <Piece position = "7,7" class = "blackpiece R"/>
      <Piece position = "7,2" class = "blackpiece B"/>
      <Piece position = "7,5" class = "blackpiece B"/>
      <Piece position = "7,1" class = "blackpiece N"/>
      <Piece position = "7,6" class = "blackpiece N"/>
      <Piece position = "6,0" class = "blackpiece P"/>
      <Piece position = "6,1" class = "blackpiece P"/>
      <Piece position = "6,2" class = "blackpiece P"/>
      <Piece position = "6,3" class = "blackpiece P"/>
      <Piece position = "6,4" class = "blackpiece P"/>
      <Piece position = "6,5" class = "blackpiece P"/>
      <Piece position = "6,6" class = "blackpiece P"/>
      <Piece position = "6,7" class = "blackpiece P"/>

    </div>

  </div>
</template>

<script>
import Tile from "./Tile"
import Piece from "./Piece"
export default {
  components:{
    Tile,
    Piece,
  },
  data(){
    return {
      start:null,
      lastDown:null,
    }
  },
  methods:{
    getcolor(k,l){
      if ((k+l)%2 == 0){
        return 'black'
      }
      return 'white'
    },

    mouseup(position){
      if (position == this.lastDown ){
        if (this.start!=null){
          this.move(this.start,position)

        }
        this.start = position
      }else{
        this.move(this.lastDown,position)
        this.start = null
      }
    },
    mousedown(position){
      this.lastDown = position
    },
    move(start,end){
      // alert(start+"->"+end)
      var startTile = document.getElementById(start)
      var endTile = document.getElementById(end)
      if(startTile.childElementCount>0 && endTile.childElementCount<1){
        var piece = startTile.children[0]
        endTile.appendChild(piece)

      }
        this.start = end

    },


  }
}
</script>

<style lang="css" scoped src = "../css/Board.css">
</style>
