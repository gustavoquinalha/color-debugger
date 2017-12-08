<template lang="html">
  <div class="container container-content" :style="{ backgroundColor: color1.hex, color: color2.hex}">
    <div @click="toggleShowLeft" class="open" v-show="!showLeft" v-cloak>
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-plus-square"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect><line x1="12" y1="8" x2="12" y2="16"></line><line x1="8" y1="12" x2="16" y2="12"></line></svg>
    </div>
    <!-- leftside -->
     <transition name="slide-fade">
    <div class="left-side container column padding-top-30" v-show="showLeft" v-cloak :style="{ backgroundColor: color1.hex}">
      <div @click="toggleShowLeft" class="close">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-minus-square"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect><line x1="8" y1="12" x2="16" y2="12"></line></svg>
      </div>

      <div class="block-form container column margin-bottom-20">
        <label for="">Font-size:</label>
        <div class="container align-items-center">
          <input type="number" v-model="fontSize" name="" value="" style="width: 50px">
          <div class="flex-grow-1 margin-left-10">
            <input type="range"class="range-style" min="10" max="100" step="2" v-model="fontSize">
          </div>
        </div>
      </div>

      <div class="block-form container column margin-bottom-20">
        <label for="">Line-height:</label>
        <div class="container align-items-center">
          <input type="number" v-model="lineHeight" name="" value="" style="width: 50px">
        <div class="flex-grow-1 margin-left-10">
            <input type="range"class="range-style" min="10" max="200" step="2" v-model="lineHeight">
        </div>
        </div>
      </div>

      <div v-show="slider === 2" v-cloak>
        <div class="block-form container column margin-bottom-20">
          <label for="">Paraghaph font-size:</label>
          <div class="container align-items-center">
            <input type="number" v-model="pSize" name="" value="" style="width: 50px">
            <div class="flex-grow-1 margin-left-10">
              <input type="range"class="range-style" min="10" max="100" step="2" v-model="pSize">
            </div>
          </div>
        </div>

        <div class="block-form container column margin-bottom-20">
          <label for="">Paraghaph line-height:</label>
          <div class="container align-items-center">
            <input type="number" v-model="plineHeight" name="" value="" style="width: 50px">
          <div class="flex-grow-1 margin-left-10">
              <input type="range"class="range-style" min="10" max="200" step="2" v-model="plineHeight">
          </div>
          </div>
        </div>
      </div>

      <div class="block-form container column margin-bottom-20">
        <label for="">Text:</label>
        <textarea name="name" rows="5" width="100%" v-model="yourText"></textarea>
      </div>


      <div class="block-form container column margin-bottom-40">
        <label for="">Text-align:</label>
        <select class="" name="" v-model="textAlign">
          <option :value="x" v-for="x in textsA">{{x}}</option>
        </select>
      </div>

      <div class="block-form container column margin-bottom-20">
        <label for="">Color 1:</label>
          <input type="text" v-model="color1.hex" name="" value="" class="margin-bottom-10">
          <Slider v-model="color1" />
      </div>

      <div class="block-form container column margin-bottom-20">
        <label for="">Color 2:</label>
          <input type="text" v-model="color2.hex" name="" value="" class="margin-bottom-10">
          <Slider v-model="color2"/>
      </div>
    </div>
  </transition>
    <!-- leftside -->



    <div class="right-side container align-center" :class="{'bg-padding-style': slider === 3}">

      <div class="arrow-block container align-center">
        <div class="prev-arrow" @click="slider = 1" :class="{ 'opa' : slider === 1}">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-arrow-left"><line x1="20" y1="12" x2="4" y2="12"></line><polyline points="10 18 4 12 10 6"></polyline></svg>
        </div>

        <div class="next-arrow" @click="slider = 2" :class="{ 'opa' : slider === 2}">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-arrow-right"><line x1="4" y1="12" x2="20" y2="12"></line><polyline points="14 6 20 12 14 18"></polyline></svg>
        </div>

        <div class="next-arrow" @click="slider = 3" :class="{ 'opa' : slider === 3}">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-monitor"><rect x="2" y="3" width="20" height="14" rx="2" ry="2"></rect><line x1="8" y1="21" x2="16" y2="21"></line><line x1="12" y1="17" x2="12" y2="21"></line></svg>
        </div>
      </div>

      <div class="bg-content-style" v-show="slider === 3" v-cloak :style="{ background: 'linear-gradient(30deg,' + color1.hex + ',' + color2.hex + ')'}">

      </div>

      <div class="content-right" :class="textAlign" v-show="slider === 1" v-cloak>
        <h1 :style="{fontSize: fontSize + 'px', lineHeight: lineHeight + 'px'}">{{yourText}} </h1>
      </div>

      <div class="content-right" :class="textAlign" v-show="slider === 2" v-cloak>
        <h1 :style="{fontSize: fontSize + 'px', lineHeight: lineHeight + 'px'}" class="margin-bottom-20">{{yourText}} </h1>
        <p :style="{fontSize: pSize + 'px', lineHeight: plineHeight + 'px', opacity: .5}">{{yourParagraph}} </p>
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
      slider: 1,
      fontSize: 60,
      lineHeight: 70,
      pSize: 20,
      plineHeight: 40,
      color1: {
        hex: '#1D194D'
      },
      color2: {
        hex: '#00ffa2'
      },
      yourText: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.',
      yourParagraph: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.',
      textAlign: 'text-align-left',
      textsA: ['text-align-left', 'text-align-center', 'text-align-right'],
      showLeft: true
    }
  },

  methods: {
    toggleShowLeft () {
      this.showLeft = !this.showLeft
    }
  }
}
</script>

<style lang="scss">
.content-right {
    flex-basis: 900px;
    box-sizing: border-box;
}
.vc-slider {
    max-width: 100%;
}
.bg-content-style {
  width: 100%;
  min-height: 100vh;
}
.bg-padding-style {
    padding: 0!important;
}
</style>
