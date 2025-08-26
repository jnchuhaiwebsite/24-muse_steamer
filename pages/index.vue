<template>
  <div>
    <Hero />
    <!-- <div class="container text-center">
      <a href="#" class="btn btn-primary">Start Creating Your First Video &rarr;</a>
    </div> -->

    <Advantages />
    <Examples />
    <About />
    <HowItWorks />
    <Pricing />
    <Faq />
  </div>
</template>

<script setup lang="ts">
import Hero from '~/components/MuseSteamer/Hero.vue'
import About from '~/components/MuseSteamer/About.vue'
import Advantages from '~/components/MuseSteamer/Advantages.vue'
import Examples from '~/components/MuseSteamer/Examples.vue'
import HowItWorks from '~/components/MuseSteamer/HowItWorks.vue'
import Pricing from '~/components/MuseSteamer/Pricing.vue'
import Faq from '~/components/MuseSteamer/Faq.vue'

useSeoMeta({
  title: 'MuseSteamer AI | The Ultimate AI Video Generator for Cinematic Content',
  description: 'Developed by Baidu, MuseSteamer AI transforms your images into stunning videos with cinematic quality, master-level cinematography, and perfectly synchronized dialogue.',
  keywords: 'Baidu AI, MuseSteamer, AI video generator, text to video, image to video AI, create AI video, cinematic AI, AI for marketing, video creation tool, multimodal AI',
})
</script>
