<template>
  <section class="">
      <div class="bio-data has-text-centered">
        <img :src="`/bios/${bio.picture}`" class="image speaker-avatar" :alt="bio.name">
        <p class="the-name">{{bio.name}}</p>
        <hr class="expert-hr">
        <p class="the-org">{{bio.org}}</p>
        <p class="the-event">{{bio.event}}</p>
        <p class="the-bio font-oswald has-text-justified">{{bio.bio}}</p>
      </div>
  </section>
</template>

<script>
export default {
  props: ['bio'],
  data() {
    return {

    };
  },
  methods: {
   
  },
};
</script>

<style lang="scss" scoped>
.bio-container{
  margin: 1rem !important;
  background-color: rgb(211, 93, 24);
  margin-top: 60px !important;
  &:first-child{
    @media only screen and (max-width: 1024px) {
      margin-bottom: 100px !important;
    }
  }
  &.orange{
  background-color: #e97e24;
  color: #FFF;
  .expert-hr{
    background-color: #FFF;
  }

  }
  &.light{
  background-color: #eae7e7;
  color: #243978;
  .expert-hr{
    background-color: #243978;
  }
  }
  &.grey{
  background-color: #b3b3b3;
  color: #243978;
  .expert-hr{
    background-color: #243978;
  }
  }
  &.blue{
  background-color: #243978;
  color: #FFF;
  .expert-hr{
    background-color: #FFF;
  }
  }
}
.bio-data{
  padding: 2rem 2.5rem;
  .the-name{
    // text-transform: uppercase;
    font-weight:600;
    font-size: 1.4rem;
  }
  .the-org{
    font-size: 0.75rem;
    font-weight: 600;
  }
  .the-event{
    font-size: 0.75rem;
    font-weight: 600;
    margin-bottom: 10px;
  }
  .the-bio{
    // font-weight: 400;
    font-size: 0.9rem;
    line-height: 1.3rem;
  }
}
.expert-hr{
  margin: 2px auto 10px;
  width: 100px;
}

.speaker-avatar{
  border-radius: 300px;
  width: 180px;
  max-height: 180px;
  margin: -90px auto 10px;
}
.the-name{

}
</style>