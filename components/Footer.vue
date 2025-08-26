<template>
  <footer class="relative bg-banana-dark-bg text-banana-text-muted py-8 md:py-12 pt-8 border-t border-banana-border-color/30 mobile-footer">
    <div class="max-w-6xl mx-auto px-4 mobile-padding">
      
      <!-- 友情链接区域 -->
      <!-- <div class="mb-8" v-if="partnerSites && partnerSites.length > 0">
        <div class="text-banana-text-light font-medium mb-4 text-left text-sm md:text-lg">Partner Sites</div>
        <div class="flex flex-wrap gap-x-6 gap-y-2">
          <a v-for="(item,index) in partnerSites" :key="index" 
             :href="item.url" 
             target="_blank" 
             rel="noopener noreferrer" 
             class="text-banana-text-muted hover:text-banana-primary-yellow transition-colors text-sm">
            {{ item.name }}
          </a>
        </div>
      </div> -->

      <!-- 分割线 -->
      <!-- <div class="w-full h-px bg-banana-border-color/30 mb-8" v-if="partnerSites && partnerSites.length > 0"></div> -->

      <!-- 主要内容区域 -->
      <div class="flex flex-col md:flex-row gap-8 md:gap-16 mobile-footer-links">
        <!-- Logo 和描述 -->
        <div class="flex-1">
          <div class="flex flex-col items-start text-left">
            <p class="text-banana-primary-yellow text-2xl md:text-3xl font-bold mb-4">Nano Banana 🍌</p>
            <p class="text-sm text-banana-text-muted max-w-xl mb-4">
              Nano Banana AI is the state-of-the-art AI suite, functioning as a premier image Editor generator and a groundbreaking video generator to transform your prompts into both breathtaking art and cinematic clips.
            </p>
            <div class="flex flex-col items-start gap-2 text-sm text-gray-500">
              <p>© 2025 Nano Banana All rights reserved.</p>
              <div>
                <p class="text-banana-text-muted text-sm">
    
                  <a href="mailto:support@nano-banana-ai.net" class="text-banana-text-light hover:text-banana-primary-yellow transition-colors">support@nano-banana-ai.net</a>
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- 导航链接和法律条款 -->
        <div class="flex-1 flex flex-col sm:flex-row gap-6 md:gap-8 md:justify-end">
          <!-- 导航链接 -->
          <!-- <div class="flex-1 text-center sm:text-left">
            <div class="text-banana-text-light font-medium mb-4 text-sm md:text-lg">Resources</div>
            <div class="flex flex-col gap-2 items-center sm:items-start">
              <template v-for="(section, index) in footerSections" :key="index">
                <div v-if="section.href && section.openInNewTab" 
                  @click="handleLinkClick(section.href, section.openInNewTab)"
                  class="text-banana-text-muted hover:text-banana-primary-yellow transition-colors cursor-pointer flex items-center gap-2 justify-center sm:justify-start">
                  <span>{{ section.name }}</span>
                  <div class="flex items-center gap-1">
                    <span v-if="section.showBeta" class="bg-banana-secondary-blue/50 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      Beta
                    </span>
                    <span v-if="section.badge" class="bg-red-500 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      {{ section.badge }}
                    </span>
                  </div>
                </div>
                <NuxtLink v-else-if="section.href" :to="section.href" 
                  class="text-banana-text-muted hover:text-banana-primary-yellow transition-colors flex items-center gap-2 justify-center sm:justify-start">
                  <span>{{ section.name }}</span>
                  <div class="flex items-center gap-1">
                    <span v-if="section.showBeta" class="bg-banana-secondary-blue/50 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      Beta
                    </span>
                    <span v-if="section.badge" class="bg-red-500 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      {{ section.badge }}
                    </span>
                  </div>
                </NuxtLink>
                <div v-else @click.prevent="handleNavClick(section.id)" 
                  class="text-banana-text-muted hover:text-banana-primary-yellow transition-colors cursor-pointer flex items-center gap-2 justify-center sm:justify-start">
                  <span>{{ section.name }}</span>
                  <div class="flex items-center gap-1">
                    <span v-if="section.showBeta" class="bg-banana-secondary-blue/50 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      Beta
                    </span>
                    <span v-if="section.badge" class="bg-red-500 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      {{ section.badge }}
                    </span>
                  </div>
                </div>
              </template>
            </div>
          </div> -->
          
          <!-- Products 部分 - 只在有内容时显示 -->
          <!-- <div v-if="productsSections && productsSections.length > 0" class="flex-1 text-center sm:text-left">
            <div class="text-banana-text-light font-medium mb-4 text-sm md:text-lg">Products</div>
            <div class="flex flex-col gap-2 items-center sm:items-start">
              <template v-for="(section, index) in productsSections" :key="index">
                <div v-if="section.href && section.openInNewTab" 
                  @click="handleLinkClick(section.href, section.openInNewTab)"
                  class="text-banana-text-muted hover:text-banana-primary-yellow transition-colors cursor-pointer flex items-center gap-2 justify-center sm:justify-start">
                  <span>{{ section.name }}</span>
                  <div class="flex items-center gap-1">
                    <span v-if="section.showBeta" class="bg-banana-secondary-blue/50 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      Beta
                    </span>
                    <span v-if="section.badge" class="bg-red-500 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      {{ section.badge }}
                    </span>
                  </div>
                </div>
                <NuxtLink v-else-if="section.href" :to="section.href" 
                  class="text-banana-text-muted hover:text-banana-primary-yellow transition-colors flex items-center gap-2 justify-center sm:justify-start">
                  <span>{{ section.name }}</span>
                  <div class="flex items-center gap-1">
                    <span v-if="section.showBeta" class="bg-banana-secondary-blue/50 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      Beta
                    </span>
                    <span v-if="section.badge" class="bg-red-500 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      {{ section.badge }}
                    </span>
                  </div>
                </NuxtLink>
                <div v-else @click.prevent="handleNavClick(section.id)" 
                  class="text-banana-text-muted hover:text-banana-primary-yellow transition-colors cursor-pointer flex items-center gap-2 justify-center sm:justify-start">
                  <span>{{ section.name }}</span>
                  <div class="flex items-center gap-1">
                    <span v-if="section.showBeta" class="bg-banana-secondary-blue/50 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      Beta
                    </span>
                    <span v-if="section.badge" class="bg-red-500 text-white text-xs font-semibold rounded-full px-1.5 py-0.5">
                      {{ section.badge }}
                    </span>
                  </div>
                </div>
              </template>
            </div>
          </div> -->

          <!-- 法律条款 -->
          <div class="flex-1 text-center md:text-right">
            <div class="text-banana-text-light font-medium mb-4 text-sm md:text-lg">Legal</div>
            <div class="flex flex-col gap-2 items-center md:items-end">
              <NuxtLink to="/subsidiary/privacy-policy" class="text-banana-text-muted hover:text-banana-primary-yellow transition-colors">Privacy Policy</NuxtLink>
              <NuxtLink to="/subsidiary/terms-of-service" class="text-banana-text-muted hover:text-banana-primary-yellow transition-colors">Terms of Service</NuxtLink>
            </div>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useNavigation } from '~/utils/navigation'
import { getFriendLinkList } from '~/api'
import { useAsyncData } from 'nuxt/app'

interface PartnerSite {
  url: string
  name: string
}

const { activeSection, sections, handleNavClick, handleScroll, footerSections, productsSections } = useNavigation()

// 处理链接点击，支持新标签页打开
const handleLinkClick = (href: string, openInNewTab?: boolean) => {
  if (openInNewTab) {
    window.open(href, '_blank', 'noopener,noreferrer');
  }
};

// 服务端请求友情链接
const { data: partnerSites, error } = await useAsyncData('partnerSites', async () => {
  const res = await getFriendLinkList()
  if (res.code === 200) {
    return res.data as PartnerSite[]
  }
  return []
})
</script>

<style scoped>
/* 导航链接悬停效果 */
a {
  position: relative;
}

a::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 1px;
  background-color: theme('colors.banana.secondary-blue');  /* 使用Tailwind配置的颜色 */
  transition: width 0.3s ease;
}

a:hover::after {
  width: 100%;
}

footer a:focus {
  outline: none !important;
  box-shadow: none !important;
}

/* 确保标签在小屏幕上也能正确显示 */
@media (max-width: 640px) {
  .flex.items-center.justify-between {
    flex-wrap: wrap;
  }
  
  .flex.items-center.gap-2.ml-2 {
    margin-left: 0;
    margin-top: 0.25rem;
  }
}
</style> 