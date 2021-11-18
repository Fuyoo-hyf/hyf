<template>
  <div class="win">
    <!-- 桌面 -->
    <div class="game_table">
      <div class="card_h">
        <div
          class="fl"
          @click="getitem(item, index)"
          v-for="(item, index) in itemcards"
          :key="index"
        >
          <my-card :cardobj="item"></my-card>
        </div>
      </div>
      <div class="card_h">
        <div class="card fl" v-for="(item, index) in sccards" :key="index">
          <my-card :cardobj="item"></my-card>
        </div>
      </div>
    </div>

    <!-- 第一人称操作 -->
    <div class="plantplom flex">
      <div class="flex_a">
        <div v-for="item in p1.itemcard" :key="item.index" class="fl">
          <my-card :cardobj="item"></my-card>
        </div>
        <!-- <div class="card fl"></div> -->
      </div>
      <div class="card flexone">
        <img src="./assets/demopeo.png" alt="" />
      </div>
    </div>

    <div class="card p2">
      <img src="./assets/demopeo.png" alt="" />
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import myCard from "./components/card.vue";

export default {
  name: "App",
  components: {
    myCard,
  },
  data() {
    return {
      peoples: [],
      itemcards: [],
      sccards: [],
      nowpeo: "p1",
      p1: {
        nm: "",
        itemcard: [],
        sccard: [],
      },
      p2: {},
    };
  },
  created() {
    this.ingame();
  },
  methods: {
    ingame() {
      // var that = this;
      this.p1 = new this.cre_player("p1");
      this.p2 = new this.cre_player("p2");
      // this.peoples.push(p1)
      // this.peoples.push(p2)
      this.readyplay();
      console.log(this.itemcards, "itemcards");
      console.log(this.sccards, "sccards");
    },

    // 开始内容准备
    readyplay() {
      let that = this;
      // start
      this.p1.y = 2;
      this.p2.y = 1;
      this.p2.g = 1;

      this.p1.itemcard.push(new this.cre_itemcard(1, 2));
      this.p1.itemcard.push(new this.cre_itemcard(2, { y: 2 }));
      this.p2.itemcard.push(new this.cre_itemcard(1, 2));
      this.p2.itemcard.push(new this.cre_itemcard(2, { y: 2 }));

      for (var i = 0; i < 5; i++) {
        this.itemcards.push(new this.cre_itemcard());
        this.sccards.push(new that.cre_sccard());
      }
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

    cre_itemcard(types, ins, out = {}) {
      // types:1 升级卡
      // 可指定生成卡片参数为空时随机生成道具卡
      if (types) {
        this.types = types;
        this.ins = ins;
        this.out = out;
      } else {
        // 随机生成交易卡或升级卡
        if (parseInt(Math.random() * 4)) {
          this.types = 2;
          let suiji = () => parseInt(Math.random() * 2);
          ins = { y: suiji(), g: suiji(), r: suiji(), b: suiji() };
          out = { y: suiji(), g: suiji(), r: suiji(), b: suiji() };
          this.ins = ins;
          this.out = out;
        } else {
          this.types = 1;
          this.ins = parseInt(Math.random() * 2 + 2);
        }
      }
    },

    // 创建积分卡
    cre_sccard() {
      var ins = parseInt(Math.random() * 21 + 10);
      var out = {};
      out.y = parseInt(Math.random() * 4);
      out.g = parseInt(Math.random() * 4);
      out.r = parseInt(Math.random() * 4);
      out.b = parseInt(Math.random() * 4);
      this.ins = ins;
      this.out = out;
      this.types = "sc";
    },

    // 点击获取道具卡
    getitem(item, index) {
      this[this.nowpeo].itemcard.push(item);
      console.log(index, "索引");
      this.itemcards.splice(index, 1);
      this.itemcards.push(new this.cre_itemcard());
    },
  },
};
</script>

<style>
.win {
  position: absolute;
  height: 100vh;
}

.game_table {
  position: fixed;
  width: 80%;
  height: 60vh;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
  border: 2px solid black;
}

.plantplom {
  position: fixed;
  width: 100%;
  height: 18vh;
  bottom: 0;
  border: 1px solid black;
  box-sizing: border-box;
}

.card_h {
  height: 18vh;
}

.flex {
  display: flex;
}

.fl {
  float: left;
}

.flex_a {
  flex: 12;
}

.flexone {
  flex: 1;
}

.card {
  width: 7.7rem;
  height: 18vh;
  border: 1px solid black;
  box-sizing: border-box;
}

.p1 {
  position: fixed;
  /* left: 0; */
  right: 0;
  bottom: 0;
  /* margin: auto; */
}

.p2 {
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  margin: auto;
}

img {
  width: 100%;
  height: 100%;
}
</style>
