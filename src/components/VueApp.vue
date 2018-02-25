<template>
 <div id="vue-app">
    <div id="bag" v-bind:class="{ burst: ended }"></div>
    <div id="bag-health">
      <div v-bind:style="{ width: health + '%' }"></div>
    </div>
    <div id="controls">
      <button v-on:click="punch" v-show="!ended">Punch</button>
      <button v-on:click="restart">Restart</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'VueApp',
    data(){
        return {
        health: 100,
        ended: false
        }
    },
    methods: {
        punch: function(){
            this.health -= 10;
            if ( this.health <= 0 ){
                this.ended = true;
            }
        },
        restart: function(){
            this.health = 100;
            this.ended = false;
        }
    }
}
</script>


<style scoped>
#bag{
    width: 200px;
    height: 500px;
    margin: 0 auto;
    background: url(../assets/img/bag.png) center no-repeat;
    background-size: 80%;
}

#bag.burst{
    background-image: url(../assets/img/bag-burst.png);
}

#bag-health{
    width: 200px;
    border: 2px solid #000;
    margin: 0 auto 20px auto;
}

#bag-health div{
    height: 20px;
    background: crimson
}

#controls{
    width: 120px;
    margin: 0 auto;
}
</style>
