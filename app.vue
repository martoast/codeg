<template>
  <div>
    <Hero/>
    <Mission id="mission" />
    <Banner :images="[
      '/1.jpeg',
      '/2.jpeg',
      '/3.jpeg',
      '/4.jpeg',
    ]"/>
    <!-- <LogoCloud/> -->
    <Events id="events"/>
    <Blog/>
    <Contact id="contact"/>
    <Footer/>
  </div>
</template>

<script setup lang="ts">
useSeoMeta({
  title: 'Comunidad para el Desarrollo Generacional',
  ogTitle: 'Comunidad para el Desarrollo Generacional',
  description: 'Inspirando líderes, transformando comunidades',
  ogDescription: 'Inspirando líderes, transformando comunidades',
  ogImage: '/logo.jpg',
  twitterCard: 'summary_large_image',
})
</script>
