<template>
  <div class="about">
    <div class="weather">
      <input type="text" v-model="postcode">
      <button @click="getData">住所入力</button>
      <p>Adress:{{adress}}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: ["city"],
  data() {
    return {
      postcode: '',
      adress: ''
    };
  },
  methods: {
    async getData(){
      const item = await axios.get(
        `https://apis.postcode-jp.com/api/v4/postcodes/${this.postcode}?apiKey=JSROs8akSxHGYQ4KL4Tc9CXY2pXTc0dXrAay9kG`
      );
      // レスポンス（受け取った情報）の中から住所を取得
      // レスポンス内容確認
      console.log(item);

      // 住所代入
      // this.adress = 住所
    }
  }
};
</script>
