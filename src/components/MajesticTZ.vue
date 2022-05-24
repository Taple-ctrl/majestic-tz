<template>
  <div class="main-drill-pos-external" v-if="showdrill" @mousedown="DownMouse()" @mouseup="UpMouse()" @wheel.prevent="Wheel">
    <div class="main-drill-pos-internal">
      <div class="main-drill">
        <div :style="{'right': rundrillNumber + 'vw'}" class="drill">
          <div :style="{'background': 'rgb(178, 34, 34,'+ hotdrill +')'}" class="drillHot"></div>
        </div>
        <div class="main-content">
          <div class="border-box" v-for="(BorderBox, index) in BorderBoxs" :key="index">
            <div class="border-spring"></div>
            <div :style="{'gap':  `${BorderBoxs[index].BlockGap}vw`}" class="border-tower-list">
              <div :style="{'transform': `rotate(${BorderBoxs[index].BlockTransformTop}deg)`}" class="border-tower"></div>
              <div :style="{'transform': `rotate(${BorderBoxs[index].BlockTransformBottom}deg)`}" class="border-tower"></div>
            </div>
          </div>
        </div>
        <div class="additional-background">
          <div class="additional-background-darkgray">1</div>
          <div class="additional-background-gray">1</div>
        </div>
      </div>      
    </div>
  </div>
</template>

<script>

export default ({
    data() {
        return {
          BorderBoxs: [
            {
              BlockGap: '0',
              BlockTransformTop:0,
              BlockTransformBottom:0
            },
            {
              BlockGap: '0',
              BlockTransformTop:0,
              BlockTransformBottom:0
            },
            {
              BlockGap: '0',
              BlockTransformTop:0,
              BlockTransformBottom:0
            },
            {
              BlockGap: '0',
              BlockTransformTop:0,
              BlockTransformBottom:0
            },
            {
              BlockGap: '0',
              BlockTransformTop:0,
              BlockTransformBottom:0
            }
          ],
          showdrill: true,
          hotdrill:0,
          interval: null,
          hitdrilldropInterval: null,
          rundrillNumber:23,
          Blocks: [1,1,1,1,1],
          BlockResist: 0
        };
    },
    methods: {
      Wheel(ev){
      if(ev.deltaY < 0) {
        if(this.rundrillNumber > 20.3){
          this.rundrillNumber = this.rundrillNumber - 0.1
        }else{
          if(this.Blocks[0] == 1){
            console.log('бурим 1 блок');
          }else{
            if(this.rundrillNumber > 16.7){
              this.rundrillNumber = this.rundrillNumber - 0.1
            }else{
              if(this.Blocks[1] == 1){
                console.log('бурим 2 блок');
              }else{
                if(this.rundrillNumber > 13.29999999999991){
                  this.rundrillNumber = this.rundrillNumber - 0.1
                }else{
                  if(this.Blocks[2] == 1){
                    console.log('бурим 3 блок');
                  }else{
                    if (this.rundrillNumber > 9.79999999999991) {
                      this.rundrillNumber = this.rundrillNumber - 0.1
                    }else{
                      if(this.Blocks[3] == 1){
                        console.log('бурим 4 блок');
                      }else{
                        if(this.rundrillNumber > 6.29999999999991){
                          this.rundrillNumber = this.rundrillNumber - 0.1
                        }else{
                          if(this.Blocks[4] == 1){
                            console.log('бурим 5 блок');
                          }else{
                            this.rundrillNumber = this.rundrillNumber - 0.1
                            if(this.rundrillNumber < 2){
                              alert('Вы пропилили')
                              this.showdrill = false;
                              clearInterval(this.interval)
                            }
                          }
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        }
      } else {
        this.rundrillNumber = this.rundrillNumber + 0.1
      }
      },
      DownMouse(){
        this.interval = setInterval(this.incrementSeconds, 30)
        clearInterval(this.hitdrilldropInterval)
      },
      UpMouse(){
        clearInterval(this.interval)
        this.hitdrilldropInterval = setInterval(this.CollingDrill, 30)
      },
      incrementSeconds(){
        this.hotdrill = this.hotdrill + 0.01
        if(this.hotdrill >= 1){
          alert('Бур сломан')
          this.showdrill = false;
          clearInterval(this.interval)
        }
        if(this.rundrillNumber > 20.3){
          return
        }else if(this.Blocks[0] == 1){
          this.BlockResist++
          if(this.BlockResist == 100){
            console.log(this.Blocks[0]);
            this.Blocks[0] = 0;
            this.BorderBoxs[0].BlockGap = 1;
            this.BorderBoxs[0].BlockTransformTop = 358;
            this.BorderBoxs[0].BlockTransformBottom = 2;
          }
        }else if(this.rundrillNumber > 16.7){
            return
        }else if(this.Blocks[1] == 1){
          this.BlockResist++
          if(this.BlockResist == 200){
            console.log('2 блок сломан');
            console.log(this.Blocks[1]);
            this.Blocks[1] = 0;
            this.BorderBoxs[1].BlockGap = 1;
            this.BorderBoxs[1].BlockTransformTop = 2;
            this.BorderBoxs[1].BlockTransformBottom = 2;
          }
        }else if(this.rundrillNumber > 13.29999999999991){
            return
        }else if(this.Blocks[2] == 1){
          this.BlockResist++
          if(this.BlockResist == 300){
            console.log('3 блок сломан');
            console.log(this.Blocks[1]);
            this.Blocks[2] = 0;
            this.BorderBoxs[2].BlockGap = 1;
            this.BorderBoxs[2].BlockTransformTop = 0;
            this.BorderBoxs[2].BlockTransformBottom = 2;
          }
        }else if(this.rundrillNumber > 9.79999999999991){
            return
        }else if(this.Blocks[3] == 1){
          this.BlockResist++
          if(this.BlockResist == 400){
            console.log('4 блок сломан');
            console.log(this.Blocks[1]);
            this.Blocks[3] = 0;
            this.BorderBoxs[3].BlockGap = 1;
            this.BorderBoxs[3].BlockTransformTop = 355;
            this.BorderBoxs[3].BlockTransformBottom = 2;
          }
        }else if(this.rundrillNumber > 6.29999999999991){
            return
        }else if(this.Blocks[4] == 1){
          this.BlockResist++
          if(this.BlockResist == 500){
            console.log('5 блок сломан');
            console.log(this.Blocks[1]);
            this.Blocks[4] = 0;
            this.BorderBoxs[4].BlockGap = 1;
            this.BorderBoxs[4].BlockTransformTop = 358;
            this.BorderBoxs[4].BlockTransformBottom = 2;
          }
        }
      },
      CollingDrill(){
        if(this.hotdrill > 0){
          this.hotdrill = this.hotdrill - 0.06
        }
      }
    }
});

</script>

<style scoped lang="scss">
.main-drill-pos-external{
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: flex-end;
  .main-drill-pos-internal{
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
              background-image: url(./assets/spring.png);
            }
            .border-tower-list{
              display: flex;
              flex-direction: column;
              .border-tower{
                width: 100%;
                background: radial-gradient(circle, rgba(181,180,182,1) 41%, rgba(163,161,163,1) 70%);;
                height: 4.7vw;
              }
            }
          }
        }
        .additional-background{
          width: 100%;
          .additional-background-darkgray{
            width: 100%;
            height: 3vw;
            background: #727072;
          }
          .additional-background-gray{
            width: 100%;
            height: 2vw;
            background: #8d8b8d;
          }
        }
        
    }
  }
}

</style>
