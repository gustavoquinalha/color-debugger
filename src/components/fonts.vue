<template lang="html">
  <div class="container container-content" :style="{ backgroundColor: color1.hex, color: color2.hex}">
    <div @click="toggleShowLeft" class="open" v-show="!showLeft" v-cloak>
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-plus-square"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect><line x1="12" y1="8" x2="12" y2="16"></line><line x1="8" y1="12" x2="16" y2="12"></line></svg>
    </div>
    <!-- leftside -->
     <transition name="slide-fade">
    <div class="left-side container column padding-top-30" v-show="showLeft" v-cloak :style="{ backgroundColor: color1.hex}">
<div class="fixed-left">
  <div @click="toggleShowLeft" class="close">
    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-minus-square"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect><line x1="8" y1="12" x2="16" y2="12"></line></svg>
  </div>

  <div class="block-form container column margin-bottom-20 margin-top-30">
    <!-- <label for="">Font-size:</label> -->
    <div class="container align-items-center">
      <input type="number" v-model="fontSize" name="" value="" style="width: 50px">
      <div class="flex-grow-1 margin-left-10">
        <input type="range"class="range-style" min="10" max="100" step="2" v-model="fontSize">
      </div>
    </div>
  </div>

  <div class="block-form container column margin-bottom-20">
    <!-- <label for="">Line-height:</label> -->
    <div class="container align-items-center">
      <input type="number" v-model="lineHeight" name="" value="" style="width: 50px">
    <div class="flex-grow-1 margin-left-10">
        <input type="range"class="range-style" min="10" max="200" step="2" v-model="lineHeight">
    </div>
    </div>
  </div>

  <div>
    <div class="block-form container column margin-bottom-20">
      <!-- <label for="">Paraghaph font-size:</label> -->
      <div class="container align-items-center">
        <input type="number" v-model="pSize" name="" value="" style="width: 50px">
        <div class="flex-grow-1 margin-left-10">
          <input type="range"class="range-style" min="10" max="100" step="2" v-model="pSize">
        </div>
      </div>
    </div>

    <div class="block-form container column margin-bottom-20">
      <!-- <label for="">Paraghaph line-height:</label> -->
      <div class="container align-items-center">
        <input type="number" v-model="plineHeight" name="" value="" style="width: 50px">
      <div class="flex-grow-1 margin-left-10">
          <input type="range"class="range-style" min="10" max="200" step="2" v-model="plineHeight">
      </div>
      </div>
    </div>
  </div>

  <div class="block-form container column margin-bottom-20">
    <!-- <label for="">Text:</label> -->
    <textarea name="name" rows="5" width="100%" v-model="yourText"></textarea>
  </div>


  <div class="block-form container column margin-bottom-40">
    <!-- <label for="">Text-align:</label> -->
    <select class="" name="" v-model="textAlign">
      <option :value="x" v-for="x in textsA">{{x}}</option>
    </select>
  </div>

  <div class="block-form container column margin-bottom-20">
      <input type="text" v-model="color1.hex" name="" value="" class="margin-bottom-10">
      <Slider v-model="color1" />
  </div>

  <div class="block-form container column margin-bottom-20">
      <input type="text" v-model="color2.hex" name="" value="" class="margin-bottom-10">
      <Slider v-model="color2"/>
  </div>


</div>
    </div>
  </transition>
    <!-- leftside -->



    <div class="right-side container column align-center">

      <div class="content-full container column align-center size margin">
        <div class="container wrap align-center" style="width: 100%">
          <div class="flex-basis-300 container column flex-grow-1 block-content-colors">
            <label for="">Background</label>
            <h1>{{color1.hex}}</h1>
              <input type="text" v-model="color1.hex" name="" value="" class="margin-bottom-10">
              <Slider v-model="color1"  class="margin-bottom-20"/>
              <input type="range" class="range-style" min="0" max="255" v-model="color1.rgba.r">
              <input type="range" class="range-style" min="0" max="255" v-model="color1.rgba.g">
              <input type="range" class="range-style" min="0" max="255" v-model="color1.rgba.b">
              <input type="range" class="range-style" min="0" max="255" v-model="color1.rgba.a">
          </div>

          <div class="flex-basis-300 container column flex-grow-1 block-content-colors">
            <label for="">Text</label>
            <h1>{{color2.hex}}</h1>
              <input type="text" v-model="color2.hex" name="" value="" class="margin-bottom-10">
              <Slider v-model="color2" class="margin-bottom-20"/>
              <input type="range" class="range-style" min="0" max="255" v-model="color2.rgba.r">
              <input type="range" class="range-style" min="0" max="255" v-model="color2.rgba.g">
              <input type="range" class="range-style" min="0" max="255" v-model="color2.rgba.b">
              <input type="range" class="range-style" min="0" max="255" v-model="color2.rgba.a">
          </div>
        </div>
        <div class="container align-center">
          <button type="button" name="button" class="btn" :style="{ backgroundColor: color2.hex, color: color1.hex}" @click="reverseColor">Reverse</button>
        </div>
      </div>

      <div class="content-full container align-center size margin">
        <div class="content-right text-align-left flex-grow-1">
          <div class="container align-items-start margin-bottom-50">
            <div class="container column margin-right-20">
              <button type="button" name="button" class="btn btn-size" :style="{ backgroundColor: color2.hex, color: color1.hex}" @click="fontSize++">A+</button>
              <button type="button" name="button" class="btn btn-size" :style="{ backgroundColor: color2.hex, color: color1.hex}" @click="fontSize--">A-</button>
            </div>
            <div class="flex-grow-1 container column">
              <h1 :style="{fontSize: fontSize + 'px', lineHeight: lineHeight + 'px'}" class="margin-bottom-20">Lorem Ipsum dolor sit ameno.</h1>
              <label for="">Font-size</label>
              <input type="range"class="range-style" min="10" max="100" step="2" v-model="fontSize">
              <label for="">Line-height</label>
              <input type="range"class="range-style" min="10" max="100" step="2" v-model="lineHeight">
            </div>
          </div>

          <div class="container align-items-start">
            <div class="container column margin-right-20">
              <button type="button" name="button" class="btn btn-size" :style="{ backgroundColor: color2.hex, color: color1.hex}" @click="pSize++">A+</button>
              <button type="button" name="button" class="btn btn-size" :style="{ backgroundColor: color2.hex, color: color1.hex}" @click="pSize--">A-</button>
            </div>
            <div class="flex-grow-1 container column">
              <p :style="{fontSize: pSize + 'px', lineHeight: plineHeight + 'px', opacity: .5}">Lorem Ipsum dolor sit ameno.</p>
              <label for="">Font-size</label>
              <input type="range"class="range-style" min="10" max="100" step="2" v-model="pSize">
              <label for="">Line-height</label>
              <input type="range"class="range-style" min="10" max="100" step="2" v-model="plineHeight">
            </div>
          </div>
        </div>
      </div>

      <div class="content-full container align-center">
        <div class="content-right" :class="textAlign">
          <h1 :style="{fontSize: fontSize + 'px', lineHeight: lineHeight + 'px'}">{{yourText}} </h1>
        </div>
      </div>

      <div class="content-full container align-center">
        <div class="content-right" :class="textAlign">
          <h1 :style="{fontSize: fontSize + 'px', lineHeight: lineHeight + 'px'}" class="margin-bottom-20">{{yourText}} </h1>
          <p :style="{fontSize: pSize + 'px', lineHeight: plineHeight + 'px', opacity: .5}">{{yourParagraph}} </p>
        </div>
      </div>

      <div class="content-full container align-center">
        <div class="content-right" :class="textAlign">
          <h1 :style="{fontSize: fontSize + 'px', lineHeight: lineHeight + 'px'}" class="margin-bottom-20">{{yourText}} </h1>
          <p :style="{fontSize: pSize + 'px', lineHeight: plineHeight + 'px', opacity: .5}">{{yourParagraph}} </p>
          <button type="button" name="button" class="btn btn-text margin-top-20" :style="{ backgroundColor: color2.hex, color: color1.hex, fontSize: fontSize / 3 + 'px'}">Lorem ipsum</button>
        </div>
      </div>

      <div class="content-full container wrap align-center">
        <div class="content-multiple" :class="textAlign">
          <h1 :style="{fontSize: fontSize / 1.5 + 'px', lineHeight: lineHeight / 1.5 + 'px'}" class="margin-bottom-20">{{yourText}} </h1>
          <p :style="{fontSize: pSize / 1.2 + 'px', lineHeight: plineHeight / 1.2 + 'px', opacity: .5}">{{yourParagraph}} </p>
        </div>
        <div class="content-multiple" :class="textAlign">
          <h1 :style="{fontSize: fontSize / 1.5 + 'px', lineHeight: lineHeight / 1.5 + 'px'}" class="margin-bottom-20">{{yourText}} </h1>
          <p :style="{fontSize: pSize / 1.2 + 'px', lineHeight: plineHeight / 1.2 + 'px', opacity: .5}">{{yourParagraph}} </p>
        </div>
      </div>

      <div class="content-full container column align-center">
        <div class="content-multiple" :class="textAlign">
          <h1 :style="{fontSize: fontSize + 'px', lineHeight: lineHeight + 'px'}" class="margin-bottom-20">{{yourText}} </h1>
          <p :style="{fontSize: pSize + 'px', lineHeight: plineHeight + 'px', opacity: .5}">{{yourParagraph}} </p>
          <p :style="{fontSize: pSize + 'px', lineHeight: plineHeight + 'px', opacity: .5}">{{yourParagraph}} </p>
        </div>
        <div class="content-multiple" :class="textAlign">
          <h1 :style="{fontSize: fontSize / 1.5 + 'px', lineHeight: lineHeight / 1.5 + 'px'}" class="margin-bottom-20">{{yourText}} </h1>
          <p :style="{fontSize: pSize / 1.2 + 'px', lineHeight: plineHeight / 1.2 + 'px', opacity: .5}">{{yourParagraph}} </p>
        </div>
      </div>

      <div class="content-full container align-center" style="padding: 0; margin: 0">
        <div class="bg-content-style" v-cloak :style="{ background: 'linear-gradient(30deg,' + color1.hex + ',' + color2.hex + ')'}">
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import { Slider } from 'vue-color'
export default {
  name: 'fonts',
  components: {
    Slider
  },
  data () {
    return {
      red: 255,
      green: 128,
      blue: 0,
      alpha: 100,

      slider: 1,
      fontSize: 60,
      lineHeight: 70,
      pSize: 20,
      plineHeight: 30,
      color1: {
        hex: '#1D194D',
        rgba: {
          r: 29,
          g: 25,
          b: 77,
          a: 1
        },
        a: 1
      },
      color2: {
        hex: '#00ffa2',
        rgba: {
          r: 0,
          g: 255,
          b: 162,
          a: 1
        },
        a: 1
      },
      yourText: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.',
      yourParagraph: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident.',
      textAlign: 'text-align-left',
      textsA: ['text-align-left', 'text-align-center', 'text-align-right'],
      showLeft: false
    }
  },

  methods: {
    toggleShowLeft () {
      this.showLeft = !this.showLeft
    },
    reverseColor () {
      const newColor1 = this.color1.hex
      const newColor2 = this.color2.hex

      this.color1.hex = newColor2
      this.color2.hex = newColor1
    }
  },
  computed: {
    alphaBasic: function () {
      return this.alpha / 100
    },
    rgba: function () {
      return `RGBA(${this.red},${this.green},${this.blue},${this.alphaBasic})`
    }
  }
}
</script>

<style lang="scss">
.content-multiple{
  flex-basis: 300px;
  flex-grow: 1;
  padding: 50px;
  box-sizing: border-box;
}
.vc-slider-swatch-picker--active {
  transform: scaleY(1.3)!important;
  border: 1px solid rgba(255,255,255,.5)
}
.vc-slider-swatch-picker {
  height: 50px!important;
}
.content-right {
    flex-basis: 1200px;
    box-sizing: border-box;
}
.vc-slider {
    max-width: 100%;
    width: 100%!important;
}
.bg-content-style {
    width: 100%;
    min-height: 100vh;
}
.bg-padding-style {
    padding: 0!important !important;
}

.block-content-colors {
    padding: 20px;
    box-sizing: border-box;
    input {
        margin-top: 10px;
    }
}
</style>
