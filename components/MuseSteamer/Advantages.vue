<template>
  <!-- Advantages -->
  <section id="advantages" class="border-t border-white/10 bg-slate-950">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 py-16">
      <h2 class="text-2xl sm:text-3xl font-semibold tracking-tight">Why Choose MuseSteamer AI?</h2>
      <div class="mt-8 grid md:grid-cols-2 lg:grid-cols-3 gap-4">
        <!-- Card -->
        <article class="rounded-2xl border border-white/10 bg-white/[.03] p-4">
          <div class="flex items-center justify-between">
            <h3 class="text-lg font-medium">Optimized for Chinese Content</h3>
            <span class="text-[10px] rounded border border-white/10 px-1.5 py-0.5 text-indigo-300">Chinese-Native</span>
          </div>
          <p class="mt-1 text-xs text-slate-400">Native Chinese Optimization</p>
          <ul class="mt-3 space-y-1.5 text-sm text-slate-300">
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Massive Chinese corpora training for native-level speech</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Context-aware emotion delivery</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Natural, fluent expressions in Chinese</span></li>
          </ul>
        </article>

        <article class="rounded-2xl border border-white/10 bg-white/[.03] p-4">
          <div class="flex items-center justify-between">
            <h3 class="text-lg font-medium">Cinematic Fidelity & Human-like Characters</h3>
            <span class="text-[10px] rounded border border-white/10 px-1.5 py-0.5 text-indigo-300">Cinematic</span>
          </div>
          <p class="mt-1 text-xs text-slate-400">Film-Grade Realism</p>
          <ul class="mt-3 space-y-1.5 text-sm text-slate-300">
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>End-to-end character generation</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Audio-visual dual-attention fusion</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Realistic 3D faces with nuanced expressions</span></li>
          </ul>
        </article>

        <article class="rounded-2xl border border-white/10 bg-white/[.03] p-4">
          <div class="flex items-center justify-between">
            <h3 class="text-lg font-medium">Master-Level Camera Work</h3>
            <span class="text-[10px] rounded border border-white/10 px-1.5 py-0.5 text-indigo-300">Pro Camera</span>
          </div>
          <p class="mt-1 text-xs text-slate-400">Professional Cinematography</p>
          <ul class="mt-3 space-y-1.5 text-sm text-slate-300">
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Fine-tuned on pro cinematography datasets</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Dozens of controllable camera grammars</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Precise text-to-visual alignment</span></li>
          </ul>
        </article>

        <article class="rounded-2xl border border-white/10 bg-white/[.03] p-4">
          <div class="flex items-center justify-between">
            <h3 class="text-lg font-medium">Audio-Visual Co-Generation</h3>
            <span class="text-[10px] rounded border border-white/10 px-1.5 py-0.5 text-indigo-300">A/V CoGen</span>
          </div>
          <p class="mt-1 text-xs text-slate-400">One-Pass Content Creation</p>
          <ul class="mt-3 space-y-1.5 text-sm text-slate-300">
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Image + prompt to complete A/V scene</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Multi-speaker dialogue & ambient audio</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>One-click instead of pipeline work</span></li>
          </ul>
        </article>

        <article class="rounded-2xl border border-white/10 bg-white/[.03] p-4">
          <div class="flex items-center justify-between">
            <h3 class="text-lg font-medium">Latent Multi-Modal Planner</h3>
            <span class="text-[10px] rounded border border-white/10 px-1.5 py-0.5 text-indigo-300">LMMP</span>
          </div>
          <p class="mt-1 text-xs text-slate-400">Multi-Role Interaction</p>
          <ul class="mt-3 space-y-1.5 text-sm text-slate-300">
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Plans roles, emotions, and logic in latent space</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Keeps visuals & audio consistent</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Authentic multi-actor interactions</span></li>
          </ul>
        </article>

        <article class="rounded-2xl border border-white/10 bg-white/[.03] p-4">
          <div class="flex items-center justify-between">
            <h3 class="text-lg font-medium">Millisecond A/V Sync</h3>
            <span class="text-[10px] rounded border border-white/10 px-1.5 py-0.5 text-indigo-300">A/V Sync</span>
          </div>
          <p class="mt-1 text-xs text-slate-400">Precision Lip-Sync</p>
          <ul class="mt-3 space-y-1.5 text-sm text-slate-300">
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Lip, expression, and gestures aligned to audio</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Stable under side-view & occlusion</span></li>
            <li class="flex gap-2"><span class="mt-1 text-indigo-300">✔</span><span>Boosted immersion & realism</span></li>
          </ul>
        </article>
      </div>
    </div>
  </section>
</template>

