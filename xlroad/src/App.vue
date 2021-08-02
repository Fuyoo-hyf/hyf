<template>
  <div class="win">
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {};
  },
  created(){
    var p1=new this.cre_player("p1")
    var p1=new this.cre_player("p2")

    // start
    p1.y=2
    p2.y=1
    p2.g=1
  },
  methods: {
    cre_player(nm){
      this.nm=nm
      this.y=0
      this.g=0
      this.r=0
      this.b=0
    },

    cre_itemcard(type,ins,out){
      this.type=type
      this.ins=ins
      this.out=out
    }
  }
}
</script>

<style>
.win{
  position: absolute;
  height: 100vh;
}
</style>
