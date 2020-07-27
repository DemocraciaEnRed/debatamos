<template>
  <div>
    <Stage />
    <!-- <Head /> -->
    <Organiza />
    <Acerca />
    <Agenda />
    <Bios />
    <End />
  </div>
</template>

<script>
// import Head from "@/components/home/Head.vue"
import Stage from "@/components/home/Stage.vue"
import Organiza from "@/components/home/Organiza.vue"
import Acerca from "@/components/home/Acerca.vue"
import Agenda from "@/components/home/Agenda.vue"
import Bios from "@/components/home/Bios.vue"
import End from "@/components/home/End.vue"

export default {
  name: "Home",
  components: {
    // Head,
    Stage,
    Organiza,
    Acerca,
    Agenda,
    Bios,
    End
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