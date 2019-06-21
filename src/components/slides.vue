<template>
    <div class="slides">
        <div class="slides">
          <span class="button-left" v-on:click="goToPrev">&#10094;</span>
          <span class="button-right" v-on:click="goToNext">&#10095;</span>

            <div v-bind:style="{ marginLeft: '-'+slidesInnerMarginLeft+'px', width: innerWidth+'px'}" class="slides-inner">
                <!-- v-bind:style  เป็นการกำหนดสไตล์โดยใช้ java script ใน htmlของvue -->
                <slider v-for="(slide,index) in slides" :key="index" :margin-left="slidesInnerMarginLeft" :client-width="innerWidth"  :index="index" v-bind:style="{ width: singleWidth+ 'px'}" v-bind:slide="slide">
                  <img slot="media" v-if="slide.show && (slide.type === 'img')" class="lazy" v-lazyload :data-src="slide.src" width="100px" height="100px" alt="A city skyline."/>
                  <iframe slot="media" v-else-if="slide.show && (slide.type === 'video')" width="100px" height="100px" v-lazyload :data-src="slide.src" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                  <h3 slot="text">{{slide.text}}</h3>
                  <p slot="text1">{{slide.text1}}</p>
                </slider>
           </div>
           <div class="navigation">
             <!-- v-bind:class ="[index === currentIndex? คือเงื่อนไข่if-else ถ้าเงื่อนไขถูกก็จะเท่ากับcurrentถ้าผิดก็จะเท่ากับ'''" -->
               <span class="nav-number" v-bind:class="[index === currentIndex ? 'current': '']" v-on:click="goToSlideIndex(index)" v-for="(slide,index) in slides" :key="index" ></span>
        </div>
        <!-- <div class="image">
        </div> -->
    </div>
    </div>
</template>

<script>
import Slider from './Slider'
import lazyload from '../directives/lazyload'
export default {
  name: 'Slides',
  props: {
    itemPerSlide: {
      type: null,
      default: 3
    }
  },
  components: {
    Slider
  },
  directives: {
    lazyload
  },
  data () {
    return {
      slides: [
        {
          src: 'https://cdn.fazwaz.com/uploads/unitType/gallery/5caec4305a3a60588d266d9f/5caec45a5a3a6051a43bff70/medium.jpg',
          show: false,
          text: 'phuket',
          text1: 'live in phuket',
          type: 'img'
        },
        {
          src: 'https://www.youtube.com/embed/P0jQzro9bzw',
          show: false,
          text: 'j',
          type: 'video'
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5acc3c5f37497d0a284cdcf6/5acc3d9537497d09a60b0dc3/medium.jpg',
          show: false,
          text: 'b',
          type: 'img'
        },
        {
          src: 'https://www.youtube.com/embed/UC3yJysj0M0',
          show: false,
          text: 'c',
          type: 'video'
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/property/gallery/5b1f48f737497d20314f1832/5b1f4b1f37497d1f6e3b36b4/medium.jpg',
          show: false,
          text: 'd',
          type: 'img'
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/property/gallery/5caebb565a3a60483f49852c/5caec35b5a3a60483c704fdf/medium.jpg',
          show: false,
          text: 'e',
          type: 'img'
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5c331d5f0759c233da561c23/5cd534202a6f6c030672bea3/medium.jpg',
          show: false,
          text: 'f',
          type: 'img'
        },

        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5c331d5f0759c233da561c23/5cd534112a6f6c02f076d1f3/medium.jpg',
          show: false,
          text: 'g',
          type: 'img'
        },

        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5c331d5f0759c233da561c23/5cd534172a6f6c0314587823/medium.jpg',
          show: false,
          text: 'h',
          type: 'img'
        },

        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5c331d5f0759c233da561c23/5cd534162a6f6c03134f0713/medium.jpg',
          show: false,
          text: 'i',
          type: 'img'
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5c331d5f0759c233da561c23/5cd534152a6f6c02f5102ff3/medium.jpg',
          show: false,
          text: 'j',
          type: 'img'
        }

      ],
      innerWidth: 0,
      singleWidth: 0,
      currentIndex: 0
    }
  },
  mounted () {
    // เป็นการดักelementที่เสร็จสมบูรณ์เข้ามาในฟังก์ชันได้
    this.$nextTick(function () {
      this.slides.map((val, index) => {
        if (index <= (this.itemPerSlide - 1)) {
          val.show = true
        }
      })
      let singleWidth = this.$el.clientWidth / this.itemPerSlide
      this.singleWidth = singleWidth // เวลาจะเรียกใช้สิ่งต่างๆที่vueมีต้องใช้this
      this.innerWidth = singleWidth * this.slides.length
    })
  },
  computed: {
    slidesInnerMarginLeft () {
      return this.currentIndex * this.singleWidth
    }
  },
  methods: {
    goToPrev () {
      //  เป็นการกำหนด this.currentIndexเท่ากับหน้าแรก
      if (this.currentIndex === 0) {
        this.currentIndex = this.slides.length - 1
        this.slides[this.currentIndex].show = true
        // คือthis.slides.length=4
        return
      }
      this.currentIndex--
      this.slides[this.currentIndex].show = true
    },
    goToNext () {
      if (this.currentIndex === this.slides.length - 1) {
        this.currentIndex = 0
        return
      }
      this.currentIndex++
      if (this.slides[(this.currentIndex + this.itemPerSlide) - 1]) {
        this.slides[(this.currentIndex + this.itemPerSlide) - 1].show = true
      }
    },
    goToSlideIndex (index) {
      this.currentIndex = index
      this.slides.map((val, i) => {
        if ((i >= (this.currentIndex)) && (i <= (this.currentIndex + this.itemPerSlide) - 1)) {
          val.show = true
        }
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.slides{
    overflow: hidden;
    text-align: center;
    /* padding-top: 1200px; */
    position: relative;
}
/* slowslide */
.slides-inner {
    transition: margin 0.6s ease-out;
}

.nav-number {
  cursor: pointer;
  height: 15px;
  width: 15px;
  margin: 0 2px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  transition: background-color 0.6s ease;
}
.button-left,.button-right {
  cursor: pointer;
  height: 25px;
  width: 25px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  position: absolute;
  margin-top: 45px;
  box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.2);
}
.button-right{
  right: 5px;
}
.button-left{
  left: 5px;
}
.nav-number.current{
    color:white;
    background-color:black;
}
</style>
