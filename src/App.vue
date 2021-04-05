<template>
  <div class="layout desktop">
    <div 
      v-for="(name, i) in blockNames" :key="i"
      @click="getRandomColorScheme()"
      :style="{ gridArea: name, backgroundColor: colorScheme[i] }"
    >
      {{ i + 1 }}
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      blockNames: ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i'],
      colorScheme: []
    }
  },
  methods: {
    getRandomColorScheme() {
      this.colorScheme = Array(9).fill('').map(
        () => `rgb(${~~(Math.random() * 255)}, ${~~(Math.random() * 255)}, ${~~(Math.random() * 255)})`
      )
    }
  },
  created() {
    this.getRandomColorScheme()
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
.layout {
  display: grid;
  margin: 0;
  padding: 2vh 2vw;
  box-sizing: border-box;
  gap: 10px;
  width: 96vw;
  min-height: 96vh;
  grid-template-rows: repeat(6, 1fr);
  grid-template-columns: repeat(2, 1fr);
  grid-template-areas: 
    "a a"
    "c d"
    "b b"
    "g g"
    "e h"
    "f i";
  transition: all 0.6s ease;
}
.layout > div {
  display: flex;
  justify-content: center;
  align-items: center;
  
}
@media (min-width: 600px) {
  .desktop {
    grid-template-rows: 10fr 10fr 5fr 3fr 4fr;
    grid-template-columns: repeat(12, 1fr);
    grid-template-areas: 
      "a a a a a a b b b b b b"
      "a a a a a a c c c d d d"
      "e e e g g g g g g h h h"
      "f f f g g g g g g h h h"
      "f f f g g g g g g i i i";
  }
}

</style>
