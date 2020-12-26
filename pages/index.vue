<template>
  <main>
    <home></home>
    <about></about>
    <gallery></gallery>
    <contact></contact>
  </main>
</template>

<script>
import Home from '@/components/home'
import About from '@/components/about'
import Gallery from '@/components/gallery'
import Contact from '@/components/contact'

export default {
  components: {
    Home,
    About,
    Gallery,
    Contact
  }
}
</script>

<style>

</style>
