<template>
  <section class="the-event">
    <p class="is-inline container-time"><span class="time-stamp">{{getTimeEvent(day.starts)}} HS</span></p>
    <p class="container-name"><span class="name-label" v-html="day.name"></span></p>
    <div v-for="(person,i) in day.with" class="the-person" :key="`person${i}`">
      <p class="font-secondary is-500">{{person.name}}</p>
      <p class="has-text-primary font-secondary is-italic">({{person.org}})<span v-if="person.from"> - {{person.from}}</span></p>
    </div>
    <div v-if="day.subtitle">
      <p class="the-subtitle" v-html="day.subtitle"></p>
    </div>
  </section>
</template>

<script>
export default {
  props: ["day"],
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
.the-event{
  margin-bottom: 15px;
}

.container-time{
  padding-bottom: 1px;
  border-bottom: 2px solid #ffa700;
  // margin-bottom: 10px;
}
.the-person{
  line-height: 1.4rem;
  margin-bottom: 4px;
}
.the-subtitle{
  margin-top: 5px;
  font-style: italic;
  font-size:0.8rem;
  line-height: 1.1rem;
}
.name-label{
  background-color:#243978;
  color: #FFF;
  font-weight: 600;
  padding: 1px 2px;
  line-height: 1.5rem;
  font-size: 0.9rem;
}
.container-name{
  margin-bottom: 10px;
  margin-top: 8px;
}
.time-stamp{
  font-weight: 600;
}
</style>