<template>
  <div class="mt-32">
    <Hero />
    <!-- <div class="container text-center">
      <a href="#" class="btn btn-primary">Start Creating Your First Video &rarr;</a>
    </div> -->
    <HowItWorks />
    <About />
    <Advantages />
    <Examples />


    <PricingPlans />
    <Faq />
  </div>
</template>

<script setup lang="ts">
import Hero from '~/components/MuseSteamer/Hero.vue'
import About from '~/components/MuseSteamer/About.vue'
import Advantages from '~/components/MuseSteamer/Advantages.vue'
import Examples from '~/components/MuseSteamer/Examples.vue'
import HowItWorks from '~/components/MuseSteamer/HowItWorks.vue'
// import Pricing from '~/components/MuseSteamer/Pricing.vue'
import Faq from '~/components/MuseSteamer/Faq.vue'
import { useSeo } from '~/composables/useSeo';
import PricingPlans from '~/components/PricingPlans.vue'

useSeo({
  title: 'MuseSteamer AI - Audio Enabled AI Image to Video Generator',
  description: 'Baidu MuseSteamer AI video generator. Create professional AI videos with cinematic visuals and natural voices in minutes.',
})
</script>
