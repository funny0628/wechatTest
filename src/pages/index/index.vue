<template>
  <div id="gameindex">
    <ul>
      <li @click="Todetail(item.name)" v-for="(item,index) in loljs" :key="index">
        <img :src="item.iconUrl" alt="">
        <p>{{item.name}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
import lol from '../../utils/lol/lol_duowan.js'
export default {
  data() {
    return {
      loljs:lol
    }
  },
  methods: {
    Todetail(name){
      wx.navigateTo({
        url: `/pages/logs/main?name=${name}`,
      })
    }
  }
}
</script>

<style >
#gameindex {
    width: 100vw;
    /* height: 100vh; */
    background-color:#596879;
}
#gameindex ul {
  width: 100%;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;


}
#gameindex ul li{
  width: 30%;
  height:2.666667rem;
  padding: .08rem;

}
#gameindex ul li img{
  width: 100%;
  height:80%;
}
#gameindex ul li p{
  text-align: center;
  overflow: hidden;
  white-space: nowrap;
  text-overflow:ellipsis;
  color:#fff;
}
</style>