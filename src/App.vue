<template>
  <div id="app">
    <div class="container">
      <div>{{percentage}} %</div>
      <div class="pbar">
        <div class="progress" :style="{'width': percent + '%'}"></div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data(){
    return{
      percent: 10
    }
  },
  created(){
    var intval = setInterval(() => {
      console.log(">>>" + this.percent);
      if(this.percent < 100)
        this.percent += 0.1;
      else
        clearInterval(intval);
    }, 10);
  },
  computed:{
    percentage(){
      return this.percent.toFixed();
    }
  }
}
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
.container{
  text-align: center;
  font-size:2rem;
}
.pbar{
  position: relative;
  overflow: hidden;
  width: 300px;
  height: 20px;
  border:1px solid blue;
  border-radius: 15px;
  box-shadow: 2px 2px 2px grey;
}
.progress{
  position: absolute;
  width: 50%;
  height: 100%;
  border-radius: 15px;
  background-color: cornflowerblue;
  /* background-image: linear-gradient(blue, white); */
  /* background-image: linear-gradient(135deg, white 25%, transparent 25%,
                      transparent 50%, white 50%,
                      white 75%, transparent 75%, transparent);
  background-size: 20px 20px; */
  animation: animate-stripes 3s linear infinite;
}

@keyframes animate-stripes {
  0% { background-position: 0px, 0px;}
  100% { background-position: 60px, 0px;}
}

</style>
