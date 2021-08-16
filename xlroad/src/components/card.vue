<template>
  <div class="card">
    <div class="card_li">
      <div class="li_xl bg_y"></div>
      <div class="li_xl bg_g"></div>
      <div class="li_xl bg_r"></div>
      <div class="li_xl bg_b"></div>
    </div>
    <div class="card_li">=></div>
    <div class="card_li">
      <div class="li_xl bg_y"></div>
      <div class="li_xl bg_g"></div>
      <div class="li_xl bg_r"></div>
      <div class="li_xl bg_b"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cardobj: {
      types: "",
      ins: "",
      out: "",
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
  width: 7vw;
  height: 120px;
  display: flex;
  justify-content: space-around;
  border: 1px solid black;
  box-sizing: border-box;
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
</style>
