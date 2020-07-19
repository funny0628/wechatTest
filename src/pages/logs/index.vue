<template>
  <div id="detaillol">
    <div class="swiper">
      <swiper style="color='#fff'">
        <block v-for="(item,index) in loldetail.bgs" :key="index">
          <swiper-item>
            <image :src="item"></image>
          </swiper-item>
        </block>
      </swiper>
    </div>
    <div class="bottom">
      <div class="left">
        <p class="skill">{{loldetail.title}}</p>
        <p class="name">{{loldetail.name}}</p>
        <p class="power">
          <span v-for="(itm,idx) in loldetail.tags" :key="idx">{{itm}}</span>
        </p>
        <div class="Ability">
          <p>
            <span class="title">生存能力:</span>
           <span class="jineng"><progress stroke-width="12" :percent="loldetail.Ability.life" activeColor="#1eca6b" backgroundColor="#363c3c"/></span>
          </p>
          <p>
            <span class="title">物理攻击:</span>
            <span class="jineng"><progress stroke-width="12" :percent="loldetail.Ability.physical" activeColor="#f2c500" backgroundColor="#363c3c"/></span>
          </p>
          <p>
            <span class="title">魔法攻击:</span>
            <span class="jineng"><progress stroke-width="12" :percent="loldetail.Ability.magic" activeColor="#f59d00" backgroundColor="#363c3c"/></span>
          </p>
          <p>
           <span class="title">操作难度:</span>
           <span class="jineng"><progress stroke-width="12" :percent="loldetail.Ability.difficulty" activeColor="#cb8cff" backgroundColor="#363c3c"/></span>
          </p>
        </div>
      </div>
      <div class="right">
        <p class="desc">{{loldetail.story}}</p> 
      </div>
    </div>

  </div>
</template>

<script>
import allLol from '../../utils/lol/lol_details_duowan.js'
export default {
  data() {
    return {
      all_Lol:allLol,
      loldetail:{}

    }
  },
  onLoad(query){
    let data = this.all_Lol.filter(item => item.name === query.name)
    this.loldetail = data[0]   
    wx.setNavigationBarTitle({
      title: `${this.loldetail.title} - ${this.loldetail.name}`
    }) 
  }
}
</script>

<style>
#detaillol {
  width: 100vw;
  min-height:100vh;
  background-color: #343434;
  
}
#detaillol  .swiper image {
  height: 150px;
  width: 100%;
  color: #fff;
}
#detaillol .bottom {
  padding: 8px 5px;
  box-sizing: border-box;
  color: #fff;
  font-size: 16px;
  display: flex;

}
#detaillol .bottom .left {
  flex: 1;
}
#detaillol .bottom .skill {
  line-height: 32px;
}
#detaillol .bottom .name {
  font-size: 18px;
  font-weight: 700;
  line-height: 40px;

}
#detaillol .bottom .power {
  display: flex;
}
#detaillol .bottom .power span{
  font-size: 13px;  
  padding: 3px;
  background-color: #099d7e;
  border-radius: 3px;
  margin-right: 5px;
}
#detaillol .bottom .Ability{
 font-size: 13px;
 margin: 5px;
}
#detaillol .bottom .Ability p{
  display: flex;
  height: 26px;
  line-height: 26px;
  margin-top: 3px;
  align-items: center;

}
#detaillol .bottom .Ability p .title{
  flex: 1;
}
#detaillol .bottom .Ability p .jineng{
  height: 16px;
 flex: 1.6;

}


#detaillol .bottom .right {
  flex: 1;
  font-size: 14px;

}
</style>
