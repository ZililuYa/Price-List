<template>
  <div class="index">
    <div class="index-title">
        服务器风采
    </div>
    <div class="img">
        <img @click="click" v-for="i in arr" :key="i" :src="i" alt="">
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: ["/static/img/1.jpg"]
      // arr: []
    };
  },
  methods: {
    click() {
      console.log(1);
      document.getElementById("qun").click();
    }
  }
};
</script>
<style>
.img {
  width: 100%;
  text-align: center;
}
.img img {
  width: 80%;
  border-radius: 20px;
  transition: all 0.6s;
  margin-bottom: 64px;
  cursor: pointer;
}
.img img:hover {
  box-shadow: 0 2px 20px #000;
  transform: scale(1.005);
}
</style>
