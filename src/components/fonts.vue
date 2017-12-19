<template lang="html">
  <div class="container container-content" :style="{ backgroundColor: `rgba(${color1.rgba.r},${color1.rgba.g},${color1.rgba.b},${color1.rgba.a})`, color: `rgba(${color2.rgba.r},${color2.rgba.g},${color2.rgba.b},${color2.rgba.a})`}">
    <div @click="toggleShowLeft" class="open" v-show="!showLeft" v-cloak>
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-plus-square">
        <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
        <line x1="12" y1="8" x2="12" y2="16"></line>
        <line x1="8" y1="12" x2="16" y2="12"></line>
      </svg>
    </div>
    <!-- leftside -->
    <transition name="slide-fade">
      <div class="left-side container column padding-top-30" v-show="showLeft" v-cloak :style="{ backgroundColor: `rgba(${color1.rgba.r},${color1.rgba.g},${color1.rgba.b},${color1.rgba.a})`}">
        <div class="fixed-left">
          <div @click="toggleShowLeft" class="close">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-minus-square">
              <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
              <line x1="8" y1="12" x2="16" y2="12"></line>
            </svg>
          </div>



          <div class="block-form container column margin-bottom-20 margin-top-50">
            <textarea name="name" rows="5" width="100%" v-model="yourText"></textarea>
          </div>


          <div class="block-form container column margin-bottom-40">
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
            <Slider v-model="color2" />
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
            <Slider v-model="color1" class="margin-bottom-20" />
            <input type="range" class="range-style" min="0" max="255" v-model="color1.rgba.r" :change="changeColor(color1)">
            <input type="range" class="range-style" min="0" max="255" v-model="color1.rgba.g" :change="changeColor(color1)">
            <input type="range" class="range-style" min="0" max="255" v-model="color1.rgba.b" :change="changeColor(color1)">
            <input type="range" class="range-style" min="0" max="1" step="0.1" v-model="color1.rgba.a" :change="changeColor(color1)">
          </div>

          <div class="flex-basis-300 container column flex-grow-1 block-content-colors">
            <label for="">Text</label>
            <h1>{{color2.hex}}</h1>
            <Slider v-model="color2" class="margin-bottom-20" />
            <input type="range" class="range-style" min="0" max="255" v-model="color2.rgba.r" :change="changeColor(color2)">
            <input type="range" class="range-style" min="0" max="255" v-model="color2.rgba.g" :change="changeColor(color2)">
            <input type="range" class="range-style" min="0" max="255" v-model="color2.rgba.b" :change="changeColor(color2)">
            <input type="range" class="range-style" min="0" max="1" step="0.1" v-model="color2.rgba.a" :change="changeColor(color2)">
          </div>
        </div>
        <div class="container align-center">
          <button type="button" name="button" class="btn" :style="{ backgroundColor: color2.hex, color: color1.hex}" @click="reverseColor">Reverse</button>
        </div>
      </div>

      <!-- <div class="container align-center size margin">
        <div class="text-align-left flex-grow-1">

          <div class="container align-items-center margin-bottom-50">
            <div class="margin-right-10">
              {{fontSize}}px
            </div>
            <div class="container column margin-right-20">
              <button type="button" name="button" class="btn btn-size" :style="{ backgroundColor: color2.hex, color: color1.hex}" @click="fontSize++">A+</button>
              <button type="button" name="button" class="btn btn-size" :style="{ backgroundColor: color2.hex, color: color1.hex}" @click="fontSize--">A-</button>
            </div>
            <div class="flex-grow-1 container column">
              <h1 :style="{fontSize: fontSize + 'px'}">Lorem Ipsum dolor sit ameno.</h1>
              <label for="">Font-size</label>
              <input type="range" class="range-style" min="10" max="100" step="2" v-model="fontSize">
            </div>
          </div>

          <div class="container align-items-center margin-bottom-50">
            <div class="margin-right-10">
              {{pSize}}px
            </div>
            <div class="container column margin-right-20">
              <button type="button" name="button" class="btn btn-size" :style="{ backgroundColor: color2.hex, color: color1.hex}" @click="pSize++">A+</button>
              <button type="button" name="button" class="btn btn-size" :style="{ backgroundColor: color2.hex, color: color1.hex}" @click="pSize--">A-</button>
            </div>
            <div class="flex-grow-1 container column">
              <p :style="{fontSize: pSize + 'px'}">Lorem Ipsum dolor sit ameno.</p>
              <label for="">Font-size</label>
              <input type="range" class="range-style" min="10" max="100" step="2" v-model="pSize">
            </div>
          </div>
        </div>
      </div> -->

      <div class="container min-height align-center size margin container-size-headings">
        <div class="text-style flex-basis-1200 text-align-left">

          <div class="margin-top-20">
            <small>{{heading1}} px</small>
            <h1 :style="{fontSize: heading1 + 'px'}" class="margin-bottom-20">H1. {{yourText}} </h1>
            <input type="range" class="range-style" min="10" max="100" step="2" v-model="heading1">
          </div>

          <div class="margin-top-20">
            <small>{{heading2}} px</small>
            <h2 :style="{fontSize: heading2 + 'px'}" class="margin-bottom-20">H2. {{yourText}} </h2>
            <input type="range" class="range-style" min="10" max="100" step="2" v-model="heading2">
          </div>

          <div class="margin-top-20">
            <small>{{heading3}} px</small>
            <h3 :style="{fontSize: heading3 + 'px'}" class="margin-bottom-20">H3. {{yourText}} </h3>
            <input type="range" class="range-style" min="10" max="100" step="2" v-model="heading3">
          </div>

          <div class="margin-top-20">
            <small>{{heading4}} px</small>
            <h4 :style="{fontSize: heading4 + 'px'}" class="margin-bottom-20">H4. {{yourText}} </h4>
            <input type="range" class="range-style" min="10" max="100" step="2" v-model="heading4">
          </div>

          <div class="margin-top-20">
            <small>{{heading5}} px</small>
            <h5 :style="{fontSize: heading5 + 'px'}" class="margin-bottom-20">H5. {{yourText}} </h5>
            <input type="range" class="range-style" min="10" max="100" step="2" v-model="heading5">
          </div>

          <div class="margin-top-20">
            <small>{{heading6}} px</small>
            <h6 :style="{fontSize: heading6 + 'px'}" class="margin-bottom-20">H6. {{yourText}} </h6>
            <input type="range" class="range-style" min="10" max="100" step="2" v-model="heading6">
          </div>

          <div class="margin-top-20">
            <small>{{paraghaph}} px</small>
            <p :style="{fontSize: paraghaph + 'px'}" class="margin-bottom-20">p. {{yourText}} </p>
            <input type="range" class="range-style" min="10" max="100" step="2" v-model="paraghaph">
          </div>

        </div>
      </div>

      <div class="container min-height align-center size margin">
        <div class="text-style flex-basis-1000" :class="textAlign">
          <div class="">
            <h1 :style="{fontSize: heading1 + 'px'}" class="margin-bottom-20">{{yourText}} </h1>
          </div>
          <div class="margin-top-30">
            <p :style="{fontSize: paraghaph + 'px'}">{{yourParagraph}} </p>
          </div>
        </div>
      </div>

      <div class="container min-height align-center" :style="{ color: `rgba(${color1.rgba.r},${color1.rgba.g},${color1.rgba.b},${color1.rgba.a})`, backgroundColor: `rgba(${color2.rgba.r},${color2.rgba.g},${color2.rgba.b},${color2.rgba.a})`}">
        <div class="text-style flex-basis-1000" :class="textAlign">
          <div class="">
            <h1 :style="{fontSize: heading1 + 'px'}" class="margin-bottom-20">{{yourText}} </h1>
          </div>
          <div class="margin-top-30">
            <p :style="{fontSize: paraghaph + 'px'}">{{yourParagraph}} </p>
          </div>
        </div>
      </div>

      <div class="container min-height align-center reset" >
        <div class="text-style flex-basis-700 text-align-left">
          <div class="">
            <h1 :style="{fontSize: heading1 + 'px'}" class="margin-bottom-20">{{yourText}} </h1>
          </div>
          <div class="">
            <p :style="{fontSize: paraghaph + 'px'}">{{yourParagraph}} </p>
          </div>
          <div class="margin-top-20">
            <button type="button" name="button" class="btn" :style="{ backgroundColor: color1.hex, color: color2.hex}">LOREM IPSUM</button>
          </div>
        </div>
      </div>

      <div class="container align-center container-size-headings reset">
        <div class="text-style flex-basis-1200 text-align-left">

          <div class="margin-top-20">
            <h1 :style="{fontSize: heading1 + 'px'}" class="margin-bottom-20">H1. {{yourText}} </h1>
          </div>

          <div class="margin-top-20">
            <h2 :style="{fontSize: heading2 + 'px'}" class="margin-bottom-20">H2. {{yourText}} </h2>
          </div>

          <div class="margin-top-20">
            <h3 :style="{fontSize: heading3 + 'px'}" class="margin-bottom-20">H3. {{yourText}} </h3>
          </div>

          <div class="margin-top-20">
            <h4 :style="{fontSize: heading4 + 'px'}" class="margin-bottom-20">H4. {{yourText}} </h4>
          </div>

          <div class="margin-top-20">
            <h5 :style="{fontSize: heading5 + 'px'}" class="margin-bottom-20">H5. {{yourText}} </h5>
          </div>

          <div class="margin-top-20">
            <h6 :style="{fontSize: heading6 + 'px'}" class="margin-bottom-20">H6. {{yourText}} </h6>
          </div>

          <div class="margin-top-20">
            <p :style="{fontSize: paraghaph + 'px'}" class="margin-bottom-20">p. {{yourText}} </p>
          </div>

        </div>
      </div>


      <div class="container min-height align-center container-size-headings reset">
        <div class="text-style flex-basis-1200 text-align-left">

          <div class="block-heading-paragraph">
            <h1 :style="{fontSize: heading1 + 'px'}" class="margin-bottom-20">{{yourText}} </h1>
            <p :style="{fontSize: paraghaph + 'px'}" class="margin-bottom-20">{{yourParagraph}} </p>
          </div>

          <div class="block-heading-paragraph">
            <h2 :style="{fontSize: heading2 + 'px'}" class="margin-bottom-20">{{yourText}} </h2>
            <p :style="{fontSize: paraghaph + 'px'}" class="margin-bottom-20">{{yourParagraph}} </p>
          </div>

          <div class="block-heading-paragraph">
            <h3 :style="{fontSize: heading3 + 'px'}" class="margin-bottom-20">{{yourText}} </h3>
            <p :style="{fontSize: paraghaph + 'px'}" class="margin-bottom-20">{{yourParagraph}} </p>
          </div>

          <div class="block-heading-paragraph">
            <h4 :style="{fontSize: heading4 + 'px'}" class="margin-bottom-20">{{yourText}} </h4>
            <p :style="{fontSize: paraghaph + 'px'}" class="margin-bottom-20">{{yourParagraph}} </p>
          </div>

          <div class="block-heading-paragraph">
            <h5 :style="{fontSize: heading5 + 'px'}" class="margin-bottom-20">{{yourText}} </h5>
            <p :style="{fontSize: paraghaph + 'px'}" class="margin-bottom-20">{{yourParagraph}} </p>
          </div>

          <div class="block-heading-paragraph">
            <h6 :style="{fontSize: heading6 + 'px'}" class="margin-bottom-20">{{yourText}} </h6>
            <p :style="{fontSize: paraghaph + 'px'}" class="margin-bottom-20">{{yourParagraph}} </p>
          </div>

        </div>
      </div>

      <div class="container align-center container-size-headings reset padding-bottom-50">
        <button type="button" name="button" class="btn" :style="{ backgroundColor: color2.hex, color: color1.hex}">EXPORT</button>
      </div>




    </div>
  </div>
</template>

<script>
  import {
    Slider
  }
  from 'vue-color'
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

        heading1: 40,
        heading2: 32,
        heading3: 28,
        heading4: 24,
        heading5: 20,
        heading6: 16,
        paraghaph: 18,

        slider: 1,
        fontSize: 40,
        pSize: 20,
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
        yourText: 'Lorem Ipsum is simply dummy text of the printing.',
        yourParagraph: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident.',
        textAlign: 'text-align-center',
        textsA: ['text-align-left', 'text-align-center', 'text-align-right'],
        showLeft: false
      }
    },

    methods: {
      toggleShowLeft () {
        this.showLeft = !this.showLeft
      },
      reverseColor () {
        const newColor1 = this.color1.rgba
        const newColor2 = this.color2.rgba
        this.color1.rgba = newColor2
        this.color2.rgba = newColor1
      },
      rgbaToHexa (rgba) {
        const hex = `#${('0' + parseInt(rgba.r).toString(16)).slice(-2)}${('0' + parseInt(rgba.g).toString(16)).slice(-2)}${('0' + parseInt(rgba.b).toString(16)).slice(-2)}`
        return hex
      },
      changeColor (color) {
        color.hex = this.rgbaToHexa(color.rgba)
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
  .container-size-headings {
    width: 100%
  }
  .reset {
    background: #fff;
    color: #000
  }

  p {
    opacity: .5
  }

  .block-heading-paragraph {
    margin-top: 100px;
    margin-bottom: 50px;
  }

  .min-height {
    min-height: 100vh
  }

  .text-style {
    h1 {
      line-height: 1.1
    }
    p {
      line-height: 1.1
    }
  }

  .content-multiple {
    flex-basis: 300px;
    flex-grow: 1;
    padding: 50px;
    box-sizing: border-box;
  }

  .vc-slider-swatch-picker--active {
    transform: scaleY(1.3)!important;
    border: 1px solid rgba(255, 255, 255, .5)
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
