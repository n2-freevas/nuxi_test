<script lang="ts">
  function getRandIntStr(num: number): string{
    return (Math.floor(Math.random() * (num - 1)) + 1).toString();
  }
  export default {
    data(){
        return{
          gAnimKey: "p4",
          gAnimDur: "d1",
          yAnimKey: "p4",
          yAnimDur: "d2",
          rAnimKey: "p4",
          rAnimDur: "d3",
        }
      },
      methods:{
          gAnimEnd(){
            let _k = "p" + getRandIntStr(8)
            let _d = "d" + getRandIntStr(3)
            if(this.gAnimKey == _k){
              this.gAnimEnd()
            }else{
              this.gAnimKey = _k
            }
            this.gAnimDur = _d
            console.log("g", this.gAnimKey, this.gAnimDur)
          },
          yAnimEnd(){
            let _k = "p" + getRandIntStr(8)
            let _d = "d" + getRandIntStr(3)
            if(this.yAnimKey == _k){
              this.yAnimEnd()
            }else{
              this.yAnimKey = _k
            }
            this.yAnimDur = _d
            console.log("y", this.yAnimKey, this.yAnimDur)
          },
          rAnimEnd(){
            let _k = "p" + getRandIntStr(8)
            let _d = "d" + getRandIntStr(3)
            if(this.rAnimKey == _k){
              this.rAnimEnd()
            }else{
              this.rAnimKey = _k
            }
            this.rAnimDur = _d
            console.log("r", this.rAnimKey, this.rAnimDur)
          }
      },
  }


</script>

<template>
  
  <header>
    <div class="n2-logo">
        <a href="/">
          <img src="~assets//img/n2-icon-black.svg" alt="" />
        </a>
    </div>
  </header>
  <main>
    <slot/>
  </main>
  <div id="bg">
    <div id="greenR" class="R" :class="[gAnimKey, gAnimDur]" v-on:animationend="gAnimEnd"></div>
    <div id="yellowR" class="R" :class="[yAnimKey, yAnimDur]" v-on:animationend="yAnimEnd"></div>
    <div id="redR"  class="R" :class="[rAnimKey, rAnimDur]" v-on:animationend="rAnimEnd"></div>
  </div>
    <!-- <N2Clock/> -->
</template>


<style scoped lang="scss">
  header {
    box-shadow: gray 0px 2px 3px;
    position: fixed;
    top:0;
    left:0;
    width:100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 50px;
    z-index: 100;
    .n2-logo {
        padding: 10px;
        img {
            height: 30px;
        }
    }
  }
  main{
    z-index: 1;
    max-width: 85%;
    margin: 100px auto;
    position: relative;
  }
  #bg{
    z-index: 0;
    position: fixed;
    bottom:0;
    right:0;
    // animation: bgA 10s infinite;
    // transform-origin: center;
    // @keyframes bgA {
    //   0%{
    //     transform: rotateZ(0deg);
    //   }
    //   100%{
    //     transform: rotateZ(360deg);
    //   }
    // }
    .R{
      border-radius: 50%;
      position: absolute;
      opacity: 0.7;
      &.p1{animation: p1A ease-in-out forwards;}
      @keyframes p1A {
        0%{
          transform: rotateZ(0deg) translate(0px, 0px);
          scale: 1;
          opacity: 0.7;
        }
        50%{
          transform: rotateZ(180deg) translate(0px, 0px);
          scale: 0.8;
          opacity: 0.7;
        }
        100%{
          transform: rotateZ(360deg) translate(0px, 0px);
          scale: 1;
          opacity: 0.7;
        }
      }
      &.p2{animation: p2A ease-in-out forwards;}
      @keyframes p2A {
        0%{
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
        50%{
          transform: rotateZ(180deg) translate(25px, 25px);
          scale: 0.9;
          opacity: 0.7;
        }
        100%{
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
      }
      &.p3{animation: p3A ease-in-out forwards;}
      @keyframes p3A {
        0%{
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
        50%{
          transform: rotateZ(90deg) translate(-10px, 25px);
          scale: 1.1;
          opacity: 0.4;
        }
        100%{
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
      }
      &.p4{animation: p4A ease-in-out forwards;}
      @keyframes p4A {
        0%{
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
        50%{
          transform: rotateZ(10deg) translate(40px, 20px);
          scale: 1;
          opacity: 0.7;
        }
        100%{
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
      }
      &.p5{animation: p5A ease-in-out forwards;}
      @keyframes p5A {
        0%{
          
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
        50%{
          transform: rotateZ(-50deg) translate(20px, -20px);
          scale: 1.2;
          opacity: 0.7;
        }
        100%{
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
      }
      &.p6{animation: p6A 3s ease-in-out forwards;}
      @keyframes p6A {
        0%{
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
        50%{
          transform: rotateZ(30deg) translate(-10px, 5px);
          scale: 1.2;
          opacity: 0.9;
        }
        100%{
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
      }
      &.p7{animation: p7A ease-in-out forwards;}
      @keyframes p7A {
        0%{
          transform: rotateZ(0deg) translate(0, 0);
          scale:1;
          opacity: 0.7;
        }
        50%{
          transform: rotateZ(-120deg) translate(5px, -5px);
          scale:1;
          opacity: 0.7;
        }
        100%{
          transform: rotateZ(0deg) translate(0, 0);
          scale:1;
          opacity: 0.7;
        }
      }
      &.p8{animation: p8A ease-in-out forwards;}
      @keyframes p8A {
        0%{
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
        50%{
          transform: rotateZ(210deg) translate(-5px, 5px);
          scale: 0.7;
          opacity: 0.5;
        }
        100%{
          transform: rotateZ(0deg) translate(0, 0);
          scale: 1;
          opacity: 0.7;
        }
      }
      &.d1{animation-duration: 4s;}
      &.d2{animation-duration: 5s;}
      &.d3{animation-duration: 6s;}
    }
    #greenR{
      bottom: 0px;
      right: 80px;
      --size: 200px;
      transform-origin: 45% 53%;
      background: rgb(40, 255, 151);
      // /transform-origin: ;
      width: var(--size);
      height: var(--size);
    }
    #yellowR{
      bottom: 50px;
      right: 20px;
      --size: 250px;
      transform-origin: 60% 40%;
      background: rgb(255, 226, 61);
      width: var(--size);
      height: var(--size);
      animation-delay: 0.3s;
    }
    #redR{
      bottom: -50px;
      right: 0px;
      --size: 200px;
      transform-origin: 55% 45%;
      background: rgb(255, 71, 71);
      width: var(--size);
      height: var(--size);
      animation-delay: 0.5s;
    }
  }
</style>
