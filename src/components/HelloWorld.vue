<template>
  <div class="main-drill-pos1" v-if="showdrill" @mousedown="test1()" @mouseup="test2()">
    <div class="main-drill-pos2">
      <div class="main-drill">
        <div :style="{'right': rundrillNumber + 'vw'}" class="drill">
          <div :style="{'background': 'rgb(178, 34, 34,'+ hotdrill +')'}" class="drillHot"></div>
        </div>
        <div class="main-content">
          <div class="border-box">
            <div class="border-spring"></div>
            <div :style="{'gap': BlockGap[0] + 'vw'}" class="border-tower-list">
              <div :style="{'transform': 'rotate(' + BlockTransform[0] + 'deg)'}" class="border-tower"></div>
              <div :style="{'transform': 'rotate(' + BlockTransform[1] + 'deg)'}" class="border-tower"></div>
            </div>
          </div>
          <div class="border-box">
            <div class="border-spring"></div>
            <div :style="{'gap': BlockGap[1] + 'vw'}" class="border-tower-list">
              <div :style="{'transform': 'rotate(' + BlockTransform[2] + 'deg)'}" class="border-tower"></div>
              <div :style="{'transform': 'rotate(' + BlockTransform[3] + 'deg)'}" class="border-tower"></div>
            </div>
          </div>
          <div class="border-box">
            <div class="border-spring"></div>
            <div :style="{'gap': BlockGap[2] + 'vw'}" class="border-tower-list">
              <div :style="{'transform': 'rotate(' + BlockTransform[4] + 'deg)'}" class="border-tower"></div>
              <div :style="{'transform': 'rotate(' + BlockTransform[5] + 'deg)'}" class="border-tower"></div>
            </div>
          </div>
          <div class="border-box">
            <div class="border-spring"></div>
            <div :style="{'gap': BlockGap[3] + 'vw'}" class="border-tower-list">
              <div :style="{'transform': 'rotate(' + BlockTransform[6] + 'deg)'}" class="border-tower"></div>
              <div :style="{'transform': 'rotate(' + BlockTransform[7] + 'deg)'}" class="border-tower"></div>
            </div>
          </div>
          <div class="border-box">
            <div class="border-spring"></div>
            <div :style="{'gap': BlockGap[4] + 'vw'}" class="border-tower-list">
              <div :style="{'transform': 'rotate(' + BlockTransform[8] + 'deg)'}" class="border-tower"></div>
              <div :style="{'transform': 'rotate(' + BlockTransform[9] + 'deg)'}" class="border-tower"></div>
            </div>
          </div>
        </div>
        <div class="additional-background">
          <div class="additional-background--box1">1</div>
          <div class="additional-background--box2">1</div>
        </div>
      </div>      
    </div>
  </div>
</template>

<script>

export default ({
    data() {
        return {
          showdrill: true,
          check:false,
          hotdrill:0,
          interval: null,
          hitdrilldropInterval: null,
          rundrillNumber:23,
          Blocks: [1,1,1,1,1],
          BlockGap: [0,0,0,0,0],
          BlockTransform: [0,0,0,0,0,0,0,0,0,0],
          BlockResist: 0
        };
    },
    methods: {
      test1(){
        this.interval = setInterval(this.incrementSeconds, 100)
        clearInterval(this.hitdrilldropInterval)
      },
      test2(){
        clearInterval(this.interval)
        this.hitdrilldropInterval = setInterval(this.HotDrillDrop,100)
      },
      incrementSeconds(){
        this.hotdrill = this.hotdrill + 0.01
        if(this.hotdrill >= 1){
          console.log('Бур сломан');
          this.showdrill = false;
          clearInterval(this.interval)
        }
        if(this.rundrillNumber > 20.3){
          this.rundrillNumber = this.rundrillNumber - 0.1
          return
        }else if(this.Blocks[0] == 1){
          this.BlockResist++
          if(this.BlockResist == 100){
            console.log('1 блок сломан');
            console.log(this.Blocks[0]);
            this.Blocks[0] = 0;
            this.BlockGap[0] = 1;
            this.BlockTransform[0] = 358;
            this.BlockTransform[1] = 2;
          }
        }else if(this.rundrillNumber > 16.7){
            this.rundrillNumber = this.rundrillNumber - 0.1
            return
        }else if(this.Blocks[1] == 1){
          this.BlockResist++
          if(this.BlockResist == 200){
            console.log('2 блок сломан');
            console.log(this.Blocks[1]);
            this.Blocks[1] = 0;
            this.BlockGap[1] = 1;
            this.BlockTransform[2] = 358;
            this.BlockTransform[3] = 2;
          }
        }else if(this.rundrillNumber > 13.29999999999991){
            this.rundrillNumber = this.rundrillNumber - 0.1
            return
        }else if(this.Blocks[2] == 1){
          this.BlockResist++
          if(this.BlockResist == 300){
            console.log('3 блок сломан');
            console.log(this.Blocks[1]);
            this.Blocks[2] = 0;
            this.BlockGap[2] = 1;
            this.BlockTransform[4] = 358;
            this.BlockTransform[5] = 2;
          }
        }else if(this.rundrillNumber > 9.79999999999991){
            this.rundrillNumber = this.rundrillNumber - 0.1
            return
        }else if(this.Blocks[3] == 1){
          this.BlockResist++
          if(this.BlockResist == 400){
            console.log('4 блок сломан');
            console.log(this.Blocks[1]);
            this.Blocks[3] = 0;
            this.BlockGap[3] = 1;
            this.BlockTransform[6] = 358;
            this.BlockTransform[7] = 2;
          }
        }else if(this.rundrillNumber > 6.29999999999991){
            this.rundrillNumber = this.rundrillNumber - 0.1
            return
        }else if(this.Blocks[4] == 1){
          this.BlockResist++
          if(this.BlockResist == 500){
            console.log('5 блок сломан');
            console.log(this.Blocks[1]);
            this.Blocks[4] = 0;
            this.BlockGap[4] = 1;
            this.BlockTransform[8] = 358;
            this.BlockTransform[9] = 2;
          }
        }else if(this.rundrillNumber > 2){
            this.rundrillNumber = this.rundrillNumber - 0.1
            return
        }else{
          console.log('вы пропилили');
          this.showdrill = false;
          clearInterval(this.interval)
        }
      },
      HotDrillDrop(){
        if(this.hotdrill > 0){
          this.hotdrill = this.hotdrill - 0.06
        }
      }
    },
    computed: {

    }
    
});

</script>

<style scoped lang="scss">
.main-drill-pos1{
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: flex-end;
  .main-drill-pos2{
    display: flex;
    align-items: flex-end;
    .main-drill{
        width: 25vw;
        height: 25vw;
        background: #1c1a1e;
        border-radius: 100%;
        display: flex;
        justify-content: space-between;
        flex-direction: column;
        align-items: center;
        overflow: hidden;
        .drill{
          width: 24vw;
          height: 1vw;
          background: #a7a7a7;
          position: relative;
          top: 50%;
          z-index: 2;
          .drillHot{
            width: 100%;
            height: 100%;
          }
        }
        .main-content{
          display: flex;
          gap: 0.5vw;
          position: relative;
          top: -1.4vw;
          .border-box{
            width: 3vw;
            height: 19vw;
            background: gray;
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            padding: 0.4vw;
            box-sizing: border-box;
            .border-spring{
              width: 100%;
              height: 100%;
              background: black;
            }
            .border-tower-list{
              display: flex;
              flex-direction: column;
              .border-tower{
                width: 100%;
                background: white;
                height: 4.7vw;
              }
            }
          }
        }
        .additional-background{
          width: 100%;
          .additional-background--box1{
            width: 100%;
            height: 3vw;
            background: #727072;
          }
          .additional-background--box2{
            width: 100%;
            height: 2vw;
            background: #8d8b8d;
          }
        }
        
    }
  }
}

</style>
