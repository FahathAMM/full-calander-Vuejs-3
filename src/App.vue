<template>
  <Header />
  <div class="container mx-auto">
    <Calendar />
  </div>
</template>

<script>
import Calendar from './components/calender.vue'
import Header from './components/Header.vue'
export default {
  components: {
    Calendar,
    Header
  }
}
</script>

<style>
</style>