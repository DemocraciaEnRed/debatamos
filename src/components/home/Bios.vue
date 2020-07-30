<template>
  <section class="section section-bios">
    <div class="container">
      <h1 class="title is-2 has-text-centered the-title">PARTICIPANTES</h1>
      <br />
      <div class="columns is-centered">
        <div class="column is-9">
          <div class="tile is-ancestor" v-for="i in [1,3,5,7,9,11,13,15,17]" :key="i">
            <div class="tile is-parent">
              <Bio :bio="bios[i-1]" class="tile is-child bio-container" :class="colors[i-1]" />
              <Bio :bio="bios[i]" class="tile is-child bio-container" :class="colors[i]" />
            </div>
          </div>
          <div class="tile is-ancestor">
            <div class="tile is-parent">
              <Bio :bio="bios[18]" class="tile is-child bio-container" :class="colors[18]" />
              <!-- <Bio :bio="bios[16]" class="tile is-child bio-container" :class="colors[17]" /> -->
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import bios from "@/data/bios";
import Bio from "../bios/Bio";

export default {
  components: {
    Bio,
  },
  data() {
    return {
      bios: bios,
      colors: [
        'orange',
        'light',
        'grey',
        'blue',
        'light',
        'orange',
        'grey',
        'blue',
        'light',
        'grey',
        'orange',
        'blue',
        'grey',
        'light',
        'orange',
        'light',
        'blue',
        'grey',
        'orange',
        'blue',
        'orange',
        'light',
        'grey',
        'blue',
      ]
    };
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
.section-bios {
  position: relative;
  background: url('../../assets/bg-bios.svg');
  background-size: cover;
  background-repeat: repeat-y;
  // background-color: #eae7e7;
  // margin-bottom: 3rem;
}
</style>