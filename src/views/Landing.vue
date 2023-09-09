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
      getTimeUrl: 'https://port-0-mapleback-jvvy2blmc9o5ey.sel5.cloudtype.app/getTime',
      time: "00:00:00"
    }
  },
  mounted() {
    this.timeEvent = setInterval(() => {
      this.checkTime()
    }, 100);
  },
  beforeDestroy() {
    clearInterval(this.timeEvent);
  },
  methods: {
    checkTime() {
      // const date = new Date();
      // this.time = `${date.getHours()}:${date.getMinutes()}:${date.getSeconds()}`;
      let date = '';

      fetch(this.getTimeUrl, { method: 'GET' }).then((result) => {
        console.log(result)
        date = result.toString().split(' ')[4];
      });

      this.time = date;
    },
    checkName() {
      const commonWorld = 'https://maplestory.nexon.com/N23Ranking/World/Total?c=%EA%B0%80%EC%B8%A0&w=0';
      const rebootWorld = 'https://maplestory.nexon.com/N23Ranking/World/Total?c=%EA%B0%80%EC%B8%A0&w=254';
    }
  }
}
</script>