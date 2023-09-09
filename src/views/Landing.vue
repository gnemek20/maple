<template>
  <div>
    <h1>메이플스토리 시간</h1>
    <h2>{{ time }}</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      timeEvent: null,
      time: "00:00:00"
    }
  },
  mounted() {
    // this.timeEvent = setInterval(() => {
    //   this.checkTime()
    // }, 100);

    const mapleRank = 'https://maplestory.nexon.com/N23Ranking/World/Total';
    const xmlHttp = new XMLHttpRequest();
    xmlHttp.open('HEAD', mapleRank, false);
    xmlHttp.setRequestHeader('Content-Type', 'text/html');
    xmlHttp.send('');

    console.log(xmlHttp.getResponseHeader("Date"));
  },
  beforeDestroy() {
    clearInterval(this.timeEvent);
  },
  methods: {
    checkTime() {
      const date = new Date();
      this.time = `${date.getHours()}:${date.getMinutes()}:${date.getSeconds()}`;
    },
    checkName() {
      const commonWorld = 'https://maplestory.nexon.com/N23Ranking/World/Total?c=%EA%B0%80%EC%B8%A0&w=0';
      const rebootWorld = 'https://maplestory.nexon.com/N23Ranking/World/Total?c=%EA%B0%80%EC%B8%A0&w=254';
    }
  }
}
</script>