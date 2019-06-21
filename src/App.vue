<template>
  <div id="app">
    <slides :item-per-slide="2" :height="150" :slides="data1"/>
    <slides :item-per-slide="2" height="200" :slides="data"/>

  </div>
</template>

<script>
import Slides from './components/slides.vue'

export default {
  name: 'app',
  components: {
    Slides
  },
  data(){
    return {
      data: [
        {
          src: 'https://cdn.fazwaz.com/uploads/unitType/gallery/5caec4305a3a60588d266d9f/5caec45a5a3a6051a43bff70/medium.jpg',
          type: 'img',
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5acc3c5f37497d0a284cdcf6/5acc3d9537497d09a60b0dc3/medium.jpg',
          type: 'img'
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/property/gallery/5b1f48f737497d20314f1832/5b1f4b1f37497d1f6e3b36b4/medium.jpg',
          type: 'img'
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/property/gallery/5caebb565a3a60483f49852c/5caec35b5a3a60483c704fdf/medium.jpg',
          type: 'img'
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5c331d5f0759c233da561c23/5cd534202a6f6c030672bea3/medium.jpg',
          type: 'img'
        },

        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5c331d5f0759c233da561c23/5cd534112a6f6c02f076d1f3/medium.jpg',
          type: 'img'
        },

        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5c331d5f0759c233da561c23/5cd534172a6f6c0314587823/medium.jpg',
          type: 'img'
        },

        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5c331d5f0759c233da561c23/5cd534162a6f6c03134f0713/medium.jpg',
          type: 'img'
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5c331d5f0759c233da561c23/5cd534152a6f6c02f5102ff3/medium.jpg',
          type: 'img'
        }

      ],
      data1: [
        {
          src: 'https://cdn.fazwaz.com/uploads/unitType/gallery/5caec4305a3a60588d266d9f/5caec45a5a3a6051a43bff70/medium.jpg',
          type: 'img',
          description: 'a'
        },
        {
          src: 'https://www.youtube.com/embed/P0jQzro9bzw',
          type: 'video',
          description: 'b'
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/unit/gallery/5acc3c5f37497d0a284cdcf6/5acc3d9537497d09a60b0dc3/medium.jpg',
          type: 'img',
           description: 'c'
        },
        {
          src: 'https://www.youtube.com/embed/UC3yJysj0M0',
          type: 'video',
           description: 'd'
        },
        {
          src: 'https://cdn.fazwaz.com/uploads/property/gallery/5b1f48f737497d20314f1832/5b1f4b1f37497d1f6e3b36b4/medium.jpg',
          type: 'img',
           description: 'e'
        }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
