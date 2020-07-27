<template>
  <section>
    <br />
    <div class="columns">
      <div class="column is-1 is-hidden-touch">
        <img src="@/assets/line-balls.svg" class width="25" style="margin-right:10px;" />
      </div>
      <div class="column is-11" v-if="showWillStart">
        <h1 class="title is-2 is-700">¡El evento comienza Viernes 31/07 a las 10.30Hrs!</h1>
        <h1 class="subtitle is-4">Consultá la agenda, ¡Te esperamos para el vivo!</h1>
        <a href="https://preguntarparaacordar.typeform.com/to/tCYJb6WE" target="_blank">
          <img
            src="@/assets/participa-button.svg"
            class="image elboton animate__animated animate__pulse animate__infinite"
            alt
          />
        </a>
      </div>
      <div class="column is-11" v-if="soonWeWillStart">
        <h1 class="title is-2 is-700">¡Comenzaremos muy pronto!</h1>
        <h1 class="subtitle is-4">¡Quedate en linea!</h1>
        <a href="https://preguntarparaacordar.typeform.com/to/tCYJb6WE" target="_blank">
          <img
            src="@/assets/participa-button.svg"
            class="image elboton animate__animated animate__pulse animate__infinite"
            alt
          />
        </a>
      </div>
      <div class="column is-11" v-if="showEnded">
        <h1 class="title is-2 is-700">¡Gracias a todas y todos!</h1>
        <h1 class="subtitle is-4">¡Por habernos acompañado en este gran evento!</h1>
      </div>
      <div class="column is-4" v-if="happeningNow != null">
        <h1 class="title is-2 is-700">EN VIVO</h1>
        <event :day="calendar.agenda[happeningNow]"></event>
      </div>
      <div class="column is-offset-1 is-4" v-if="happeningNext != null">
        <h1 class="title is-2 is-700">Próximamente</h1>
        <event :day="calendar.agenda[happeningNext]"></event>
      </div>
    </div>
  </section>
</template>
<script>
import calendar from "@/data/calendar";
import Event from "../agenda/Event.vue";

export default {
  props: ["now"],
  data() {
    return {
      // now: new Date(),
      starts: new Date(Date.UTC(2020, 6, 31, 3, 0, 0)),
      ends: new Date(Date.UTC(2020, 6, 31, 2, 59, 59)),
      calendar: calendar,
    };
  },
  components: {
    Event,
  },
  // mounted: function () {
  //   this.intervalId = setInterval(this.updateTime, 500);
  // },
  // beforeDestroy() {
  //   if (this.intervalId) clearInterval(this.intervalId);
  // },
  methods: {
  //   updateTime: function () {
  //     // this.now = new Date();
  //     this.now = this.addMinutes(Math.floor(Math.random() * 10) + 5)
  //   },
  //   addMinutes(minutes) {
  //     return new Date(this.now.getTime() + minutes*60000);
  // }
  },
  computed: {
    happeningNow: function () {
      if (!this.calendar) return null;
      let indexHappeningNow = this.calendar.agenda.findIndex((event) => {
        if (event.starts <= this.now && this.now < event.ends) return true;
        return false;
      });
      if (indexHappeningNow == -1) return null;
      return indexHappeningNow;
    },
    happeningNext: function () {
      if (this.happeningNow == null) return null;
      if (this.happeningNow + 1 < this.calendar.agenda.length)
        return this.happeningNow + 1;
      return null;
    },
    showWillStart: function () {
      let hasta = new Date(Date.UTC(2020, 6, 31, 12, 0, 0));
      if (this.now < hasta) return true;
      return false;
    },
    soonWeWillStart: function () {
      let desde = new Date(Date.UTC(2020, 6, 31, 12, 0, 0));
      let hasta = new Date(Date.UTC(2020, 6, 31, 13, 30, 0));
      if (desde <= this.now && this.now < hasta) return true;
      return false;
    },
    showEnded: function () {
      let desde = new Date(Date.UTC(2020, 6, 31, 18, 30, 0));
      if (desde <= this.now) return true;
      return false;
    },
  },
};
</script>

<style lang="scss" scoped>
.elboton {
  width: 200px;
}
// .coming-next{
//   background-color: #FFF;
//   padding: 25px;
//   // max-height: 800px;
// }
// .the-time {
//   text-align: center;
//   margin-bottom: 10px;
//   // font-weight: 800;
// }
// .media-left {
//   width: 35px;
// }
// .type-icon {
//   width: 20px;
//   display: inline;
//   margin: 15px 5px;
// }
// .type-text {
//   text-transform: uppercase;
//   letter-spacing: 1px;
//   font-weight: 300;
//   font-size: 0.8rem;
//   // margin-left: -1px;
//   margin-top: 2px;
// }
// .title-text {
//   font-weight: 600;
//   font-size: 1.2rem;
//   line-height: 1.5rem;
//   margin-bottom: 6px;
//   margin-top: 3px;
// }
// .who-text {
//   font-size: 0.9rem;
//   margin-bottom: 4px;
// }
// .icon-twitter {
//   width: 20px;
//   border-radius: 4px;
//   vertical-align: top;
//   margin-right: 4px;
// }
// .hashtag-text{
//   font-size:0.9rem;
// }
// .who-org{
//   font-size:0.9rem;
//   // white-space: nowrap;
//   color: rgb(100, 100, 100);
// }
// .custom-hr{
//   background-color: #000;
//   height: 1px;
//   width: 35%;
// }
</style>