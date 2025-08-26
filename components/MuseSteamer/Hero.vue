<template>
  <!-- Hero -->
  <section class="relative overflow-hidden">
    <div class="absolute inset-0 bg-[radial-gradient(ellipse_at_top,rgba(99,102,241,.25),transparent_60%)]"></div>
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 py-16 lg:py-24 relative">
      <div class="grid lg:grid-cols-2 gap-10 items-center">
        <div>
          <PageHero
            title="MuseSteamer AI Multimodal Video Generation in One Click"
            subtitle="Transform a single image and a prompt into voiced, silent, or VFX videos. Achieve cinematic quality, master-level camera moves, and native-level Chinese speech accuracyall in minutes."
          />
          <div class="mt-8 flex flex-wrap items-center gap-4">
            <a href="#try" class="inline-flex items-center gap-2 rounded-2xl bg-gradient-to-r from-[#6209F6] via-[#DC8AF6] to-[#83D0FB] px-5 py-2.5 font-medium shadow-sm hover:opacity-90 transition">Start Creating</a>
            <a href="#features" class="inline-flex items-center gap-2 rounded-2xl border border-white/10 px-5 py-2.5 font-medium hover:bg-white/5 transition">Explore Features</a>
          </div>
          <ul class="mt-6 grid sm:grid-cols-3 gap-3 text-sm text-slate-300">
            <li class="rounded-xl border border-white/10 bg-white/5 px-3 py-2">🎬 Cinematic Quality</li>
            <li class="rounded-xl border border-white/10 bg-white/5 px-3 py-2">🎥 Professional Camera Moves</li>
            <li class="rounded-xl border border-white/10 bg-white/5 px-3 py-2">🗣️ Native Chinese Speech Fidelity</li>
          </ul>
        </div>
        <div class="relative">
          <div class="rounded-2xl border border-white/10 bg-gradient-to-br from-slate-900 to-slate-800/60 p-3 shadow-2xl ring-1 ring-white/10">
            <div class="aspect-video w-full overflow-hidden rounded-xl bg-slate-900">
              <video id="previewVideo" class="h-full w-full object-cover" muted controls playsinline poster="" src="https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4"></video>
            </div>
            <div class="mt-3 flex items-center justify-between text-xs text-slate-400">
              <span>Live Preview (placeholder)</span>
              <span>720P / 1080P · Audio / Silent</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

