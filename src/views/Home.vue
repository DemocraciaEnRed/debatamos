<template>
  <div>
    <Head />
    <Organiza />
    <Acerca />
    <Agenda />
  </div>
</template>

<script>
import Head from "@/components/home/Head.vue"
import Organiza from "@/components/home/Organiza.vue"
import Acerca from "@/components/home/Acerca.vue"
import Agenda from "@/components/home/Agenda.vue"

export default {
  name: "Home",
  components: {
    Head,
    Organiza,
    Acerca,
    Agenda
  }
};
</script>

<style lang="scss" scoped>
.hero{
  background-color: #eae7e7;
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
</style>