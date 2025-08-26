<template>
  <header>
    <nav
      class="fixed top-0 left-0 w-full z-50 backdrop-blur-md"
      style="background-color: rgba(13, 17, 23, 0.8); border-bottom: 1px solid var(--border-color);"
    >
      <div class="max-w-7xl mx-auto px-4">
        <div class="flex items-center justify-between h-20">
          <!-- Logo -->
          <div class="flex-shrink-0">
            <NuxtLink to="/">
              <span class="gradient-text" style="font-size: 1.5rem; font-weight: 700;">MuseSteamer AI</span>
            </NuxtLink>
          </div>

          <!-- PC端导航 -->
          <div class="hidden lg:flex items-center flex-grow space-x-4 ml-6">
            <a href="#about-musesteamer" class="nav-link">About</a>
            <a href="#features" class="nav-link">Advantages</a>
            <a href="#live-examples" class="nav-link">Examples</a>
            <a href="#how-it-works" class="nav-link">How It Works</a>
            <!-- <a href="#pricing" class="nav-link">Pricing</a> -->
          </div>

          <!-- 用户信息区域 - PC端 -->
          <div class="hidden lg:flex items-center space-x-4 flex-shrink-0">
            <div>
              <UserMenu />
            </div>
          </div>

          <!-- 移动端菜单按钮 -->
          <button
            @click="isOpen = !isOpen"
            class="lg:hidden p-2 rounded-md transition-colors"
            style="color: var(--text-muted-color);"
          >
            <svg
              v-if="!isOpen"
              class="w-6 h-6"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16"
              />
            </svg>
            <svg
              v-else
              class="w-6 h-6"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M6 18L18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>

      <!-- 移动端菜单 -->
      <Transition name="slide-fade">
        <div
          v-if="isOpen"
          class="lg:hidden fixed top-0 left-0 w-full h-screen overflow-y-auto backdrop-blur-sm z-[100]"
          style="background-color: rgba(13, 17, 23, 0.95);"
        >
          <button
            @click="isOpen = false"
            class="fixed top-4 right-4 p-2 rounded-full transition-colors z-[101]"
            style="color: var(--text-muted-color);"
          >
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
          <div class="pt-20 px-4 pb-8 text-center">
            <a href="#about-musesteamer" @click="isOpen = false" class="mobile-nav-link">About</a>
            <a href="#features" @click="isOpen = false" class="mobile-nav-link">Advantages</a>
            <a href="#live-examples" @click="isOpen = false" class="mobile-nav-link">Examples</a>
            <a href="#how-it-works" @click="isOpen = false" class="mobile-nav-link">How It Works</a>
            <a href="#pricing" @click="isOpen = false" class="mobile-nav-link">Pricing</a>
          </div>
        </div>
      </Transition>
    </nav>
  </header>
</template>

<script setup lang="ts">
import { ref, watch, onUnmounted } from "vue";

const isOpen = ref(false);

watch(isOpen, (newValue) => {
  if (newValue) {
    document.body.style.overflow = "hidden";
  } else {
    document.body.style.overflow = "";
  }
});

onUnmounted(() => {
  document.body.style.overflow = "";
});
</script>

<style scoped>
.nav-link {
  color: var(--text-muted-color);
  text-decoration: none;
  font-weight: 600;
  transition: color 0.3s ease;
  padding: 0.5rem 1rem;
}
.nav-link:hover {
  color: #83D0FB;
}

.mobile-nav-link {
  display: block;
  color: var(--text-muted-color);
  text-decoration: none;
  font-weight: 600;
  padding: 1rem;
  transition: color 0.3s ease, background-color 0.3s ease;
  border-radius: 8px;
}
.mobile-nav-link:hover {
  color: white;
  background-color: var(--card-color);
}

.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.3s ease-out;
}
.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(-20px);
  opacity: 0;
}
</style> 