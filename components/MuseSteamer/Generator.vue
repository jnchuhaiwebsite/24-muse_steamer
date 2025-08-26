<template>
  <section id="try" class="border-t border-white/10 bg-slate-950">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 py-14">
      <h2 class="text-2xl sm:text-3xl font-semibold tracking-tight" id="features">Create with MuseSteamer</h2>
      <p class="mt-2 text-slate-400">Left: form Right: preview. Duration and audio options auto-link to the selected model.</p>

      <div class="mt-8 grid lg:grid-cols-2 gap-8">
        <!-- Left: Form -->
        <form class="space-y-6" @submit.prevent="onGenerate">
          <!-- Image -->
          <div>
            <label for="image" class="block text-sm font-medium text-slate-200">1) Upload Image</label>
            <div class="mt-2 rounded-2xl border border-dashed border-white/15 bg-white/5 p-4 hover:border-[#6209F6]/40 transition">
              <div class="flex items-center gap-4">
                <input id="image" type="file" accept="image/png,image/jpeg,image/webp" class="hidden" @change="onFileChange" ref="imageInput" />
                <button type="button" @click="imageInput?.click()" class="inline-flex items-center gap-2 rounded-xl bg-slate-800 px-3 py-2 text-sm hover:bg-slate-700 focus:outline-none focus:ring-2 focus:ring-[#6209F6]">Choose File</button>
                <span class="text-xs text-slate-400">Supports JPG/PNG/WebP, ≤10MB, ≥512px recommended</span>
              </div>
              <div v-if="fileName" class="mt-3 flex items-center gap-3 text-sm text-slate-300">
                <img :src="thumbSrc" alt="preview" class="h-12 w-12 rounded-lg object-cover ring-1 ring-white/10"/>
                <div class="flex-1 truncate">{{ fileName }}</div>
                <button type="button" @click="removeImage" class="rounded-lg border border-white/10 px-2 py-1 text-xs hover:bg-white/5">Remove</button>
              </div>
              <p v-if="imageError" class="mt-1 text-xs text-rose-400">{{ imageError }}</p>
            </div>
          </div>

          <!-- Prompt -->
          <div>
            <label for="prompt" class="block text-sm font-medium text-slate-200">2) Prompt</label>
            <textarea v-model="prompt" rows="4" placeholder="Two colleagues discuss a product launch in a glass-walled room. Start wide, push to medium. Confident tone, brisk pace."
              class="mt-2 w-full resize-y rounded-2xl border border-white/10 bg-slate-900/60 px-4 py-3 text-sm placeholder:text-slate-500 focus:outline-none focus:ring-2 focus:ring-[#6209F6]"></textarea>
            <p v-if="promptError" class="mt-1 text-xs text-rose-400">{{ promptError }}</p>
          </div>

          <!-- Model -->
          <div>
            <span class="block text-sm font-medium text-slate-200">3) Choose Model</span>
            <div class="mt-3 grid gap-3 text-sm">
              <label class="group grid grid-cols-[auto,1fr,auto] items-center gap-3 rounded-2xl border border-white/10 bg-white/[.03] p-3 hover:border-[#6209F6]/40 transition cursor-pointer">
                <input type="radio" name="model" value="turboAudio" v-model="currentModel" />
                <div>
                  <div class="font-medium text-slate-100">MuseSteamer-2.0-Turbo-I2V-Audio
                    <span class="ml-2 rounded-md border border-white/10 px-1.5 py-0.5 text-[10px] text-sky-200">Recommended</span>
                  </div>
                  <p class="text-xs text-slate-400 mt-0.5">720P with audio, 5s/10s; multi-speaker, A/V sync, cinematic camera moves.</p>
                  <div class="mt-2 flex flex-wrap gap-1.5">
                    <span class="rounded-md border border-white/10 bg-white/5 px-1.5 py-0.5 text-[10px]">720P</span>
                    <span class="rounded-md border border-white/10 bg-white/5 px-1.5 py-0.5 text-[10px]">Audio</span>
                    <span class="rounded-md border border-white/10 bg-white/5 px-1.5 py-0.5 text-[10px]">5s/10s</span>
                    <span class="rounded-md border border-white/10 bg-white/5 px-1.5 py-0.5 text-[10px]">Multi-speaker</span>
                  </div>
                </div>
                <div class="text-right text-xs text-slate-400">
                  <div>1280×720</div>
                  <div>Audio</div>
                </div>
              </label>

               <label class="group grid grid-cols-[auto,1fr,auto] items-center gap-3 rounded-2xl border border-white/10 bg-white/[.03] p-3 hover:border-[#6209F6]/40 transition cursor-pointer">
                <input type="radio" name="model" value="turbo" v-model="currentModel" />
                <div>
                  <div class="font-medium text-slate-100">MuseSteamer-2.0-Turbo-I2V</div>
                  <p class="text-xs text-slate-400 mt-0.5">720P silent, 5s only; film-grade quality and complex camera moves.</p>
                </div>
                <div class="text-right text-xs text-slate-400">
                  <div>1280×720</div>
                  <div>Silent</div>
                </div>
              </label>

              <label class="group grid grid-cols-[auto,1fr,auto] items-center gap-3 rounded-2xl border border-white/10 bg-white/[.03] p-3 hover:border-[#6209F6]/40 transition cursor-pointer">
                <input type="radio" name="model" value="pro" v-model="currentModel" />
                <div>
                  <div class="font-medium text-slate-100">MuseSteamer-2.0-Pro-I2V</div>
                  <p class="text-xs text-slate-400 mt-0.5">1080P dynamic video; higher fidelity and stronger expressiveness.</p>
                </div>
                <div class="text-right text-xs text-slate-400">
                  <div>1920×1080</div>
                  <div>Silent</div>
                </div>
              </label>

              <label class="group grid grid-cols-[auto,1fr,auto] items-center gap-3 rounded-2xl border border-white/10 bg-white/[.03] p-3 hover:border-[#6209F6]/40 transition cursor-pointer">
                <input type="radio" name="model" value="lite" v-model="currentModel" />
                <div>
                  <div class="font-medium text-slate-100">MuseSteamer-2.0-Lite-I2V</div>
                  <p class="text-xs text-slate-400 mt-0.5">High throughput and cost efficiency; ideal for batch generation.</p>
                </div>
                <div class="text-right text-xs text-slate-400">
                  <div>1280×720</div>
                  <div>Silent</div>
                </div>
              </label>
            </div>
          </div>

          <!-- Duration -->
          <div>
            <span class="block text-sm font-medium text-slate-200">4) Duration</span>
            <div class="mt-2 flex flex-wrap gap-2 items-center">
              <button 
                v-for="dur in [5, 10]" 
                :key="dur" 
                type="button" 
                @click="setDuration(dur)"
                :class="['durBtn rounded-xl px-3 py-1.5 text-sm border', 
                  duration === dur ? 'border-[#6209F6] bg-[#6209F6]/20' : 'border-white/10 hover:bg-white/5'
                ]"
              >{{ dur }}s</button>
              <span v-if="durHint" class="text-xs text-slate-400">{{ durHint }}</span>
            </div>
          </div>

          <!-- Submit -->
          <div class="pt-2 flex items-center gap-3">
            <button id="genBtn" type="submit" class="inline-flex items-center gap-2 rounded-2xl bg-gradient-to-r from-[#6209F6] via-[#DC8AF6] to-[#83D0FB] px-5 py-2.5 font-medium shadow-sm hover:opacity-90 transition">
              <span>Generate Video</span>
            </button>
            <span class="text-xs text-slate-400">You must own rights to uploaded assets Results are commercially usable One-time credits <span class="text-slate-200">never expire</span></span>
          </div>
        </form>

        <!-- Right: Preview -->
        <div class="space-y-4">
          <div class="rounded-2xl border border-white/10 bg-white/[.03] p-3">
            <div class="flex items-center justify-between">
              <div class="text-sm text-slate-300">Preview</div>
              <div class="text-xs text-slate-400">{{ previewMeta }}</div>
            </div>
            <div class="mt-3 overflow-hidden rounded-xl ring-1 ring-white/10">
              <div v-if="generationState === 'idle'" class="aspect-video grid place-items-center bg-slate-900/60">
                <div class="text-center text-slate-400 text-sm">Upload an image and enter a prompt, then generate to preview here.</div>
              </div>
              <div v-if="generationState === 'processing'" class="aspect-video grid place-items-center bg-slate-900/60">
                 <div class="flex flex-col items-center gap-2">
                  <svg class="h-5 w-5 animate-spin" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"/><path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8v4a4 4 0 00-4 4H4z"/></svg>
                  <div class="text-sm text-slate-300">Generating {{ progress }}%</div>
                  <div class="h-1 w-48 rounded bg-slate-700"><div class="h-1 rounded bg-[#6209F6]" :style="{width: progress + '%'}"></div></div>
                </div>
              </div>
              <div v-if="generationState === 'completed'" class="aspect-video bg-black">
                <video :src="outVideoSrc" class="h-full w-full object-cover" controls playsinline></video>
              </div>
              <div v-if="generationState === 'failed'" class="aspect-video grid place-items-center bg-rose-950/40">
                <div class="text-center">
                  <div class="font-medium text-rose-200">Generation failed</div>
                  <div class="text-sm text-rose-300">{{ errorMessage }}</div>
                </div>
              </div>
            </div>
            <div class="mt-3 flex items-center gap-3 text-sm">
               <button v-if="generationState === 'completed'" @click="downloadVideo" class="rounded-xl border border-white/10 px-3 py-1.5 hover:bg-white/5">Download</button>
              <button v-if="generationState === 'completed'" @click="copyLink" class="rounded-xl border border-white/10 px-3 py-1.5 hover:bg-white/5">Copy Link</button>
              <button v-if="generationState === 'completed'" @click="clearPreview" class="rounded-xl border border-white/10 px-3 py-1.5 hover:bg-white/5">Clear Preview</button>
              <span v-if="generationState === 'idle'" class="text-slate-400 text-xs">Do not close the page while generating; your result will appear here automatically.</span>
            </div>
          </div>

          <!-- History -->
           <div class="rounded-2xl border border-white/10 bg-white/[.02] p-3">
            <div class="text-sm text-slate-300">Recent Renders</div>
            <div v-if="history.length === 0" class="mt-2 text-xs text-slate-400">No records yet</div>
            <div v-else class="mt-2 grid sm:grid-cols-2 gap-3">
              <button v-for="item in history" :key="item.id" @click="loadHistory(item)" class="flex items-center gap-3 rounded-xl border border-white/10 bg-white/5 p-2 text-left hover:bg-white/10">
                <img :src="item.cover" class="h-12 w-20 rounded-md object-cover ring-1 ring-white/10" alt="cover"/>
                <div class="flex-1">
                  <div class="text-xs text-slate-200 truncate">{{ item.model }}</div>
                  <div class="text-[11px] text-slate-400">{{ item.res }} {{ item.audio ? 'Audio' : 'Silent' }} {{ item.duration }}s</div>
                </div>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, computed, watch } from 'vue'

// Refs for form inputs
const imageInput = ref<HTMLInputElement | null>(null)
const imageFile = ref<File | null>(null)
const fileName = ref('')
const thumbSrc = ref('')
const imageError = ref('')
const prompt = ref('')
const promptError = ref('')
const currentModel = ref('turboAudio')
const duration = ref(5)
const durHint = ref('')

// Refs for generation state
type GenerationState = 'idle' | 'processing' | 'completed' | 'failed'
const generationState = ref<GenerationState>('idle')
const progress = ref(0)
const outVideoSrc = ref('')
const errorMessage = ref('')

// History
interface HistoryItem {
  id: string
  cover: string
  model: string
  duration: number
  res: string
  audio: boolean
}
const history = ref<HistoryItem[]>([])

const previewMeta = computed(() => {
  const res = currentModel.value === 'pro' ? '1920×1080' : '1280×720'
  const audio = currentModel.value === 'turboAudio' ? 'Audio' : 'Silent'
  return `${res} ${audio} ${duration.value}s`
})

watch(currentModel, (newModel) => {
  if (newModel === 'turbo' || newModel === 'lite') {
    duration.value = 5
  }
  
  if (newModel === 'turbo') durHint.value = 'Turbo (silent) supports 5s only';
  else if (newModel === 'turboAudio') durHint.value = 'Turbo-Audio supports 5s/10s with audio';
  else if (newModel === 'pro') durHint.value = 'Pro supports 1080P (5s/10s)';
  else if (newModel === 'lite') durHint.value = 'Lite is ideal for batching; defaults to 5s';
  else durHint.value = ''
})

function setDuration(newDuration: number) {
  if (currentModel.value === 'turbo' && newDuration !== 5) {
    durHint.value = 'Turbo (silent) supports 5s only';
    return;
  }
  if (currentModel.value === 'turboAudio' && ![5, 10].includes(newDuration)) {
    durHint.value = 'Turbo-Audio supports 5s/10s';
    return;
  }
   if (currentModel.value === 'lite' && newDuration !== 5) {
    durHint.value = 'Lite is ideal for batching; defaults to 5s';
    return;
  }
  
  duration.value = newDuration
  durHint.value = ''
}

function onFileChange(e: Event) {
  imageError.value = ''
  const target = e.target as HTMLInputElement
  const file = target.files?.[0]
  if (!file) return

  if (!['image/jpeg', 'image/png', 'image/webp'].includes(file.type)) {
    imageError.value = 'Only JPG/PNG/WebP are supported'
    return
  }
  if (file.size > 10 * 1024 * 1024) {
    imageError.value = 'File exceeds 10MB limit'
    return
  }
  
  imageFile.value = file
  fileName.value = file.name
  thumbSrc.value = URL.createObjectURL(file)
}

function removeImage() {
  if (imageInput.value) {
    imageInput.value.value = ''
  }
  imageFile.value = null
  fileName.value = ''
  thumbSrc.value = ''
  imageError.value = ''
}

function onGenerate() {
  promptError.value = ''
  imageError.value = ''
  if (!imageFile.value) {
    imageError.value = 'Please upload an image first'
    return
  }
  if (!prompt.value.trim()) {
    promptError.value = 'Prompt cannot be empty'
    return
  }

  generationState.value = 'processing'
  progress.value = 0
  
  const tick = setInterval(() => {
    progress.value = Math.min(100, progress.value + Math.floor(Math.random() * 12) + 6)
    if (progress.value >= 100) {
      clearInterval(tick)
      const demoUrl = 'https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4'
      outVideoSrc.value = demoUrl
      generationState.value = 'completed'
      
      addHistory({
        id: Date.now().toString(),
        cover: thumbSrc.value || 'https://images.unsplash.com/photo-1526318472351-c75fcf070305?q=80&w=480&auto=format&fit=crop',
        model: currentModel.value,
        duration: duration.value,
        res: currentModel.value === 'pro' ? '1920×1080' : '1280×720',
        audio: currentModel.value === 'turboAudio'
      })
    }
  }, 450)
}

function addHistory(item: HistoryItem) {
  history.value.unshift(item)
  if (history.value.length > 6) {
    history.value.pop()
  }
}

function downloadVideo() {
  const a = document.createElement('a')
  a.href = outVideoSrc.value
  a.download = `MuseSteamer_${currentModel.value}_${duration.value}s.mp4`
  a.click()
}

async function copyLink() {
  try {
    await navigator.clipboard.writeText(outVideoSrc.value)
    alert('Link copied')
  } catch (err) {
    console.error('Failed to copy: ', err)
  }
}

function clearPreview() {
  generationState.value = 'idle'
  outVideoSrc.value = ''
}

function loadHistory(item: HistoryItem) {
    outVideoSrc.value = 'https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4';
    generationState.value = 'completed';
}
</script>

