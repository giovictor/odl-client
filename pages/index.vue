<template>
  <main>
    <home></home>
    <about></about>
    <gallery></gallery>
    <contact></contact>
    <footer-section></footer-section>
  </main>
</template>

<script>
import Home from '@/components/sections/Home'
import About from '@/components/sections/About'
import Gallery from '@/components/sections/Gallery'
import Contact from '@/components/sections/Contact'
import FooterSection from '@/components/sections/Footer'

export default {
  components: {
    Home,
    About,
    Gallery,
    Contact,
    FooterSection
  }
}
</script>

<style>

</style>
