<template>
  <div>
    <h1>메이플스토리 시간</h1>
    <h2>{{ time }}</h2>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      timeEvent: null,
      getTimeUrl: 'https://port-0-mapleback-jvvy2blmc9o5ey.sel5.cloudtype.app/getTime',
      // getTimeUrl: 'http://127.0.0.1:3000',
      time: ''
    }
  },
  async mounted() {
    this.timeEvent = setInterval(() => {
      this.checkTime()
    }, 100);
  },
  beforeDestroy() {
    clearInterval(this.timeEvent);
  },
  methods: {
    async checkTime() {
      let date = '';

      const { status, data } = await axios.get(this.getTimeUrl);
      if (status === 200) {
        date = data.toString().split(' ')[4];
      }
      else {
        clearInterval(this.timeEvent);
        return;
      }

      this.time = date;
    },
    checkName() {
      const commonWorld = 'https://maplestory.nexon.com/N23Ranking/World/Total?c=%EA%B0%80%EC%B8%A0&w=0';
      const rebootWorld = 'https://maplestory.nexon.com/N23Ranking/World/Total?c=%EA%B0%80%EC%B8%A0&w=254';
    }
  }
}
</script>