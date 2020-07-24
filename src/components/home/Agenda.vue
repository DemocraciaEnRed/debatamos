<template>
   <section class="section section-agenda">

     <h1 class="title is-2 has-text-centered the-title">AGENDA</h1>
     <br>
    <div class="container the-agenda">
      <div class="columns is-centered">
        <div class="column is-1 is-hidden-touch">
         <img src="@/assets/line-balls.svg" class="" alt="">
        </div>
        <div class="column is-12-mobile is-4-tablet is-3-desktop has-text-centered-mobile">
          <event :day="calendar.agenda[0]"></event>
          <event :day="calendar.agenda[1]"></event>
        </div>
        <div class="column is-12-mobile is-4-tablet is-3-desktop has-text-centered-mobile">
          <event :day="calendar.agenda[2]"></event>
          <event :day="calendar.agenda[3]"></event>
        </div>
        <div class="column is-12-mobile is-4-tablet is-3-desktop has-text-centered-mobile">
          <event :day="calendar.agenda[4]"></event>
          <event :day="calendar.agenda[5]"></event>
        </div>
        <div class="column is-1 is-hidden-touch">
          &nbsp;
        </div>
      </div>
    </div>
    <img src="@/assets/agenda-lines-top-right.svg" class="line-top" alt="">
    <img src="@/assets/agenda-lines-bottom-left.svg" class="line-bottom" alt="">
    <img src="@/assets/agenda-ball-bottom-right.svg" class="ball-right" alt="">
  </section>
</template>

<script>
import calendar from "@/data/calendar";
import Event from "../agenda/Event"

export default {
  components: {
    Event
  },
  data(){
    return {
      calendar: calendar
    }
  },
  methods: {
    getTimeEvent: function(eventStarts) {
      if (eventStarts.getMinutes() == "0") {
        return eventStarts.getHours();
      }
      return `${eventStarts.getHours()}.${eventStarts.getMinutes()}`;
    }
  }
}
</script>

<style lang="scss" scoped>
.the-title{
  position: relative;
  z-index: 10
}
.line-top{
  position: absolute;
  right: 0;
  top: 0;
  z-index: 0;
}
.line-bottom{
  position: absolute;
  left: 0;
  bottom: 0;
  z-index: 0;
}
.ball-right{
  position: absolute;
  right: 0;
  bottom: 0;
  z-index: 0;
}
.line-balls{
  position: absolute;
  left: 20px;
  top: 50px;
  opacity: 0.5
}
.section-agenda{
  position: relative; 
  background-color: #eae7e7;
  // margin-bottom: 3rem;
}
.the-agenda{
  z-index: 10;
}
</style>