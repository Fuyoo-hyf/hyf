<template>
  <div>
    <div v-if="cardobj.types == 1" class="card">
      <div>升级</div>
      <div class="card_li">
        <div v-for="item in cardobj.ins" :key="item.index" class="li_xl bg_sj"></div>
      </div>
    </div>

    <div v-if="cardobj.types == 2" class="card">
      <div class="card_li">
        <div v-for="item in cardobj.out.y" :key="item.index" class="li_xl bg_y"></div>
        <div v-for="item in cardobj.out.g" :key="item.index" class="li_xl bg_g"></div>
        <div v-for="item in cardobj.out.r" :key="item.index" class="li_xl bg_r"></div>
        <div v-for="item in cardobj.out.b" :key="item.index" class="li_xl bg_b"></div>
      </div>
      <div class="card_li">=></div>
      <div class="card_li">
        <div v-for="item in cardobj.ins.y" :key="item.index" class="li_xl bg_y"></div>
        <div v-for="item in cardobj.ins.g" :key="item.index" class="li_xl bg_g"></div>
        <div v-for="item in cardobj.ins.r" :key="item.index" class="li_xl bg_r"></div>
        <div v-for="item in cardobj.ins.b" :key="item.index" class="li_xl bg_b"></div>
      </div>
    </div>

    <div v-if="cardobj.types == 'sc'" class="sccard">
      <div>积分：{{cardobj.ins}}</div>
      <div>黄：{{cardobj.out.y}}</div>
      <div>绿：{{cardobj.out.g}}</div>
      <div>红：{{cardobj.out.r}}</div>
      <div>黑：{{cardobj.out.b}}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cardobj: {
      types: "",
      ins: {},
      out: {},
    },
  },

  data() {
    return {};
  },

  created() {},

  methods: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  color: #42b983;
}
.card {
  /* width: 7vw; */
  width: 7.7rem;
  height: 18vh;
  display: flex;
  justify-content: space-around;
  border: 1px solid black;
  box-sizing: border-box;
}
.sccard {
  width: 7.7rem;
  height: 18vh;
  border: 1px solid black;
  box-sizing: border-box;
  line-height: 20px;
}
.card_li {
  height: 100px;
  width: 20%;
}
.li_xl {
  width: 10px;
  height: 10px;
  margin-bottom: 15px;
}
.bg_y {
  background-color: yellow;
}
.bg_g {
  background-color: greenyellow;
}
.bg_r {
  background-color: red;
}
.bg_b {
  background-color: black;
}
.bg_sj{
  background-color: cadetblue;
}
</style>
