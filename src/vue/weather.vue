<template>
  <h2>weather</h2>
  <dl>
    <dt>天气</dt>
    <dd v-cloak> {{ weather }}</dd>
    <dt>温度</dt>
    <dd v-cloak>{{ temp }}</dd>
  </dl>
</template>
<script>
  export default {
    data(){
      return {
        weather:"",
        temp:"",
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
          //增加判断
            if (response.body['HeWeather data service 3.0'][0].status === 'ok'){
              this.$set('data',response.body['HeWeather data service 3.0'][0]);
              this.$set('weather',this.data.now.cond.txt)
              this.$set('temp',this.data.now.tmp + '°')
            }
            },(response) => {
              console.log("数据错误")
            })
      }
    }
  }
</script>
<style>
[v-cloak]{
  display:none;
}
</style>
