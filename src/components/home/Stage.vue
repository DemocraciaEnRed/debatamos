<template>
  <div class="hero is-small-with-navbar">
    <img src="@/assets/line-white.svg" class="the-linea" alt="">
    <div class="hero-body">
      <div class="container">
        <!-- <p class="is-inline is-600 is-size-5" style="position: fixed; bottom: 0; left: 0;background-color: blue; color: white; padding: 5px 15px;">Hora: {{this.now}}</p> -->

        <section v-if="showtime">

        <div class="columns is-centered">
          <div class="column is-6">
            <img src="@/assets/logo-wide.svg" class="image is-hidden-touch" alt />
            <img src="@/assets/logo-mobile.svg" class="image is-hidden-desktop" alt />
          </div>
        </div>
        <br>
        <div class="tile is-ancestor">
          <div class="tile is-parent">
            <div class="tile is-child">
            <div class="videoWrapper">
             <iframe width="853" height="480" :src="`https://www.youtube.com/embed/${streamId}?start=21018`" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            </div>
            </div>
            <div class="tile is-child is-4 slido-container">
              <iframe src="https://app.sli.do/event/equou7pj" height="100%" width="100%" style="height:100%"></iframe>
            </div>
          </div>
        </div>
        <p class="has-text-primary font-secondary is-size-4 is-italic"><i class="fas fa-arrow-up"></i>&nbsp;Hacé tu pregunta a las y los expositores, participá activamente de la conversación en vivo <i class="fas fa-arrow-up is-hidden-touch"></i> </p>
        <coming-next :now="now"/>
        </section>
        <section v-else>
          <div class="columns is-centered">
            <div class="column is-8">
              <img src="@/assets/logo-wide.svg" class="image is-hidden-touch" alt />
              <img src="@/assets/logo-mobile.svg" class="image is-hidden-desktop" alt />
            </div>
          </div>
          <br>
          <div class="columns is-centered" v-if="!afterShowtime">
            <div class="column is-11">
              <div class="columns is-centered is-vcentered">
                <div class="column is-3">
                  <img src="@/assets/info-column.svg" class="image is-centered lainfo" alt />
                </div>
                <div class="column is-3 is-offset-1">
                  <a href="https://preguntarparaacordar.typeform.com/to/tCYJb6WE" target="_blank">

                  <img
                    src="@/assets/participa-button.svg"
                    class="image elboton is-centered animate__animated animate__pulse animate__infinite"
                    alt
                  />
                  </a>
                </div>
              </div>
            </div>
          </div>
        </section>
    </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import ComingNext from '../stage/ComingNext.vue'

export default {
  name: "Head",
  data() {
    return {
      streamId: '0uCZ5ujYq60',
      // streamId: '-2oUSyu2tEk',
      // streamId: 'GOJHd0CI1p4',
      now: new Date(),
      // now: new Date(Date.UTC(2020,6,31,2,0,0)),
      starts: new Date(Date.UTC(2020,6,31,3,0,0)),
      ends: new Date(Date.UTC(2020,7,1,3,0,0)),
      intervalId: null,
    }
  },
  components: {
    ComingNext
  },
  mounted: function(){
    this.intervalId = setInterval(this.updateTime, 30000);
    // this.intervalId = setInterval(this.updateTime, 50);
  },
  beforeDestroy() {
    if (this.intervalId) clearInterval(this.intervalId);
  },
  methods: {
    updateTime: function(){
      this.now = new Date()
      // this.now = this.addMinutes(Math.floor(Math.random() * 10) + 5)
      // this.now = this.addSeconds(Math.floor(Math.random() * 30) + 10)
      // this.now = this.addSeconds(30)
    },
    addMinutes(minutes) {
      return new Date(this.now.getTime() + minutes*60000);
    },
    addSeconds(seconds) {
      return new Date(this.now.getTime() + seconds*1000);
    }
  },
  computed: {
    showtime: function () {
      let desde = new Date(Date.UTC(2020, 6, 31, 3, 0, 0));
      let hasta = new Date(Date.UTC(2020, 6, 31, 20, 30, 0));
      if (desde <= this.now && this.now < hasta) return true;
      return false;
    },
    afterShowtime: function () {
      let desde = new Date(Date.UTC(2020, 6, 31, 20, 30, 0));
      if (desde <= this.now) return true;
      return false;
    },
  }
};
</script>

<style lang="scss" scoped>
.hero{
  background-color: #eae7e7;
  position: relative;
}
.the-linea{
  z-index: 1;
  position: absolute;
  height:100%;
  right:0;
}
.hero-body{
  z-index:10;
}
.elboton{
  width:100%;
  max-width: 200px;
}
.lainfo{
  width:100%;
  max-width: 250px;
}
.videoWrapper {
  position: relative;
  padding-bottom: 56.25%; /* 16:9 */
  height: 0;
}
.videoWrapper iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
.slido-container{
   @media only screen and (max-width: 1024px) {
      height: 560px !important;
    }
}
</style>