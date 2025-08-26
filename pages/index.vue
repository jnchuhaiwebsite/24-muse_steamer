<template>
  <div class="bg-slate-950 text-slate-100">

    <main>
      <MuseSteamerHeader />
      <MuseSteamerHero />
      <MuseSteamerGenerator />
      <MuseSteamerAdvantages />
      <MuseSteamerUseCases />
      <MuseSteamerHowItWorks />
      <MuseSteamerFaq />
      <MuseSteamerPricing />
      <MuseSteamerCta />
    </main>
  </div>
</template>

<script setup lang="ts">
import MuseSteamerHeader from '~/components/MuseSteamer/Header.vue'
import MuseSteamerHero from '~/components/MuseSteamer/Hero.vue'
import MuseSteamerGenerator from '~/components/MuseSteamer/Generator.vue'
import MuseSteamerAdvantages from '~/components/MuseSteamer/Advantages.vue'
import MuseSteamerUseCases from '~/components/MuseSteamer/UseCases.vue'
import MuseSteamerHowItWorks from '~/components/MuseSteamer/HowItWorks.vue'
import MuseSteamerFaq from '~/components/MuseSteamer/Faq.vue'
import MuseSteamerPricing from '~/components/MuseSteamer/Pricing.vue'
import MuseSteamerCta from '~/components/MuseSteamer/Cta.vue'

useHead({
  title: 'MuseSteamer AI - Multimodal Video Generation in One Click',
  meta: [
    { name: 'description', content: 'Turn a single image and a prompt into voiced, silent, or VFX videos. Cinematic quality, professional camera moves, and native-level Chinese speech fidelityall in minutes.' },
    { name: 'theme-color', content: '#6209F6' },
    { property: 'og:title', content: 'MuseSteamer AI - Multimodal Video Generation in One Click' },
    { property: 'og:description', content: 'From an image + prompt to voiced, silent, or VFX videos with cinematic fidelity and professional camera moves.' },
    { property: 'og:type', content: 'website' },
    { property: 'og:url', content: 'https://www.example.com/' },
    { property: 'og:image', content: 'https://www.example.com/og-cover.jpg' },
    { name: 'twitter:card', content: 'summary_large_image' },
    { name: 'twitter:title', content: 'MuseSteamer AI - Multimodal Video Generation in One Click' },
    { name: 'twitter:description', content: 'Create cinematic videos from an image + promptvoiced, silent, or VFXin minutes.' },
    { name: 'twitter:image', content: 'https://www.example.com/og-cover.jpg' },
  ],
  link: [
    { rel: 'canonical', href: 'https://www.example.com/' }
  ],
  style: [
    { innerHTML: 'html { scroll-behavior: smooth; }' }
  ],
  script: [
    {
      type: 'application/ld+json',
      innerHTML: JSON.stringify({
        "@context":"https://schema.org",
        "@type":"SoftwareApplication",
        "name":"MuseSteamer AI",
        "applicationCategory":"MultimediaApplication",
        "operatingSystem":"Web",
        "description":"Multimodal video generationvoiced, silent, or VFXwith cinematic quality and master-level camera moves.",
        "offers":{
          "@type":"AggregateOffer",
          "offerCount":"3",
          "lowPrice":"29",
          "highPrice":"199",
          "priceCurrency":"USD"
        }
      })
    }
  ]
})
</script>
