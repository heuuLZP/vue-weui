<template>
  <h2>weather</h2>
  <dl>
    <dt>天气</dt>
    <dd> {{ weather }}</dd>
    <dt>温度</dt>
    <dd>{{ temp }}°</dd>
  </dl>
</template>
<script>
  export default {
    data(){
      return {
        weather:"未知",
        temp:0,
        apiURL:"https://api.heweather.com/x3/weather?cityid=CN101010100&key=bac728ec43314d76bf2c85e7fa0675d8",
        data:{}
      }
    },

    ready(){
      this.getData();
    },

    methods:{
      getData(){
        this.$http.get(this.apiURL)
          .then((response) => {
            this.$set('data',response.body['HeWeather data service 3.0'][0]);
            this.$set('weather',this.data.now.cond.txt)
            this.$set('temp',this.data.now.tmp)
            })
      }
    }
  }
</script>
<style>
</style>
