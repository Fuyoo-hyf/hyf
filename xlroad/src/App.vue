<template>
  <div class="win">
    <div class="card p1">
      <img src="./assets/demopeo.png" alt="">
    </div>
    <div class="card p2">
      <img src="./assets/demopeo.png" alt="">
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: "App",
  components: {},
  data() {
    return {
      peoples: [],
      itemcards: [],
      sccards: [],
    };
  },
  created() {
    this.ingame();
  },
  methods: {
    ingame() {
      let that = this;
      var p1 = new this.cre_player("p1");
      var p2 = new this.cre_player("p2");
      // this.peoples.push(p1)
      // this.peoples.push(p2)

      // start
      p1.y = 2;
      p2.y = 1;
      p2.g = 1;

      p1.itemcard.push(new this.cre_itemcard(1, 2));
      p1.itemcard.push(new this.cre_itemcard(2, { y: 2 }));
      p2.itemcard.push(new this.cre_itemcard(1, 2));
      p2.itemcard.push(new this.cre_itemcard(2, { y: 2 }));

      for (var i = 0; i < 5; i++) {
        this.itemcards.push(new this.cre_itemcard());
        this.sccards.push({
          card: new that.cre_sccard(),
        });
      }

      console.log(this.itemcards);
      console.log(this.sccards);
    },
    cre_player(nm) {
      this.nm = nm;
      this.y = 0;
      this.g = 0;
      this.r = 0;
      this.b = 0;
      this.itemcard = [];
      this.sc = 0;
    },

    cre_itemcard(type, ins, out) {
      // type:1 升级卡
      if (type) {
        this.type = type;
        this.ins = ins;
        this.out = out;
      } else {
        if (parseInt(Math.random() * 4)) {
          this.type = 2;
          let suiji = () => parseInt(Math.random() * 4);
          ins = { y: suiji(), g: suiji(), r: suiji(), b: suiji() };
          out = { y: suiji(), g: suiji(), r: suiji(), b: suiji() };
          this.ins = ins;
          this.out = out;
        } else {
          this.type = 1;
          this.ins = parseInt(Math.random() * 2 + 2);
        }
      }
    },

    cre_sccard() {
      var ins = parseInt(Math.random() * 21 + 10);
      var out = {};
      out.y = parseInt(Math.random() * 4);
      out.g = parseInt(Math.random() * 4);
      out.r = parseInt(Math.random() * 4);
      out.b = parseInt(Math.random() * 4);
      this.ins = ins;
      this.out = out;
    },
  },
};
</script>

<style>
.win {
  position: absolute;
  height: 100vh;
}

.card{
  width: 200px;
  height: 350px;
}

.p1{
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
}

.p2{
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
}

img{
  width: 100%;
  height: 100%;
}
</style>
