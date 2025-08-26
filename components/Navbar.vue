<template>
  <header>
    <nav
      class="fixed top-0 left-0 w-full z-50 backdrop-blur-md shadow-md bg-banana-dark-bg/80"
    >
      <div class="max-w-7xl mx-auto px-4">
        <div class="flex items-center justify-between h-20">
          <!-- Logo -->
          <div class="flex-shrink-0">
            <NuxtLink to="/">
              <span class="text-banana-primary-yellow text-2xl lg:text-3xl font-bold">Nano Banana 🍌</span>
            </NuxtLink>
          </div>

          <!-- PC端导航 -->
          <div class="hidden lg:flex items-center flex-grow space-x-4 ml-6">
            <template v-for="(section, index) in sections" :key="index">
              <div
                @click="handleNavClick(section.href || section.id)"
                class="relative text-banana-text-light hover:text-banana-primary-yellow transition-all cursor-pointer px-4 py-2.5 rounded-lg hover:shadow-lg whitespace-nowrap"
              >
                <span
                  v-if="section.badge"
                  :class="[
                    'absolute text-[10px] leading-none bg-banana-secondary-blue text-white rounded-full px-2 py-1 min-w-fit inline-flex items-center justify-center whitespace-nowrap',
                    {
                      '-top-2 left-1/2 -translate-x-1/2': section.badgePosition === 'center',
                      '-top-2 -left-1': section.badgePosition === 'left',
                      '-top-2 -right-1': section.badgePosition === 'right',
                    }
                  ]"
                >
                  {{ section.badge }}
                </span>
                {{ section.name }}
              </div>
            </template>
          </div>

          <!-- 用户信息区域 - PC端 -->
          <div class="hidden lg:flex items-center space-x-4 flex-shrink-0">
            <!-- 添加Personal Center和Credits -->
            <!-- <template v-if="isSignedIn">
              <NuxtLink
                to="/profile"
                class="relative text-blue-navtext hover:text-blue-dark transition-all cursor-pointer px-4 py-2.5 rounded-lg hover:bg-blue-medium/10 hover:shadow-lg hover:shadow-blue-medium/20 whitespace-nowrap"
              >
                Personal Center
              </NuxtLink>
              <div class="relative text-blue-navtext transition-all px-4 py-2.5 rounded-lg hover:bg-blue-medium/10 hover:shadow-lg hover:shadow-blue-medium/20 whitespace-nowrap cursor-pointer">
                <div class="flex items-center gap-2">
                  <span class="text-blue-dark">Credits:</span>
                  <span class="text-blue-dark font-medium">{{ credits }}</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-5 h-5 text-blue-dark">
                    <path d="M10.464 8.746c.227-.18.497-.311.786-.394v2.795a2.252 2.252 0 01-.786-.393c-.394-.313-.546-.681-.546-1.004 0-.323.152-.691.546-1.004zM12.75 15.662v-2.824c.347.085.664.228.921.421.427.32.579.686.579.991 0 .305-.152.671-.579.991a2.534 2.534 0 01-.921.42z" />
                    <path fill-rule="evenodd" d="M12 2.25c-5.385 0-9.75 4.365-9.75 9.75s4.365 9.75 9.75 9.75 9.75-4.365 9.75-9.75S17.385 2.25 12 2.25zM12.75 6a.75.75 0 00-1.5 0v.816a3.836 3.836 0 00-1.72.756c-.712.566-1.112 1.35-1.112 2.178 0 .829.4 1.612 1.113 2.178.502.4 1.102.647 1.719.756v2.978a2.536 2.536 0 01-.921-.421l-.879-.66a.75.75 0 00-.9 1.2l.879.66c.533.4 1.169.645 1.821.75V18a.75.75 0 001.5 0v-.81a4.124 4.124 0 001.821-.749c.745-.559 1.179-1.344 1.179-2.191 0-.847-.434-1.632-1.179-2.191a4.122 4.122 0 00-1.821-.75V8.354c.29.082.559.213.786.393l.415.33a.75.75 0 00.933-1.175l-.415-.33a3.836 3.836 0 00-1.719-.755V6z" clip-rule="evenodd" />
                  </svg>
                </div>
              </div>
            </template> -->
            <!-- 用户头像区域 -->
            <div>
              <UserMenu />
            </div>
          </div>

          <!-- 移动端菜单按钮 -->
          <button
            @click="isOpen = !isOpen"
            class="lg:hidden text-banana-text-light p-2 rounded-md hover:bg-banana-card-bg transition-colors"
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

      <!-- 移动端菜单，使用懒加载 -->
      <Transition name="slide-fade">
        <div
          v-if="isOpen"
          class="lg:hidden fixed top-0 left-0 w-full h-screen overflow-y-auto bg-banana-dark-bg/95 backdrop-blur-sm z-[100]"
        >
          <!-- 关闭按钮 -->
          <button
            @click="isOpen = false"
            class="fixed top-4 right-4 text-banana-text-light p-2 rounded-full hover:bg-banana-card-bg transition-colors z-[101]"
          >
            <svg
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

          <!-- 滚动内容区域 -->
          <div class="pt-16 px-4 pb-8">
            <!-- 导航链接 -->
            <div class="space-y-2 mb-6">
              <template v-for="(section, index) in sections" :key="index">
                <div
                  @click="() => { handleNavClick(section.href || section.id); isOpen = false; }"
                  class="relative block text-banana-text-light hover:text-banana-primary-yellow text-base transition-all cursor-pointer px-4 py-2.5 rounded-lg hover:bg-banana-card-bg hover:shadow-lg whitespace-nowrap mt-3"
                >
                  <span
                    v-if="section.badge"
                    :class="[
                      'absolute text-[10px] leading-none bg-banana-secondary-blue text-white rounded-full px-2 py-1 min-w-fit inline-flex items-center justify-center whitespace-nowrap',
                      {
                        '-top-2 left-1/2 -translate-x-1/2': section.badgePosition === 'center',
                        '-top-2 -left-1': section.badgePosition === 'left',
                        '-top-2 -right-1': section.badgePosition === 'right',
                      }
                    ]"
                  >
                    {{ section.badge }}
                  </span>
                  {{ section.name }}
                </div>
              </template>
              <!-- <NuxtLink
                v-if="isSignedIn"
                to="/profile"
                class="block text-blue-navtext hover:text-blue-dark text-base py-2 transition-colors"
                @click="() => { isOpen = false; }"
              >
                Personal Center
              </NuxtLink> -->
            </div>

            <!-- 移动端用户菜单 -->
            <UserMenu :isMobile="true" :onCloseMobileNav="() => isOpen = false" />
          </div>
        </div>
      </Transition>
    </nav>
  </header>
</template>

<script setup lang="ts">
import { ref, watch, onUnmounted, onMounted } from "vue";
import { useNavigation } from "~/utils/navigation";
import { useClerkAuth } from '~/utils/authHelper';
import { useRouter, useRoute } from 'vue-router';
import { useUserStore } from '~/stores/user';

// 状态管理
const isOpen = ref(false);
const { isSignedIn } = useClerkAuth();
const router = useRouter();
const route = useRoute();
const userStore = useUserStore();
const credits = ref(0);

// 监听用户信息变化
watch(() => userStore.userInfo, (newUserInfo) => {
  if (newUserInfo) {
    credits.value = newUserInfo.free_limit + newUserInfo.remaining_limit || 0;
  } else {
    credits.value = 0;
  }
}, { immediate: true });

// 获取用户信息
const getUserInfo = async () => {
  try {
    const userData = await userStore.fetchUserInfo();
    if (userData) {
      credits.value = userData.free_limit + userData.remaining_limit || 0;
    }
  } catch (error) {
    console.error("获取用户信息失败:", error);
  }
}

// 使用导航工具
const { activeSection, sections, handleNavClick, handleScroll, executeScroll } =
  useNavigation();

onMounted(async () => {
  // 只重置overflow，不改变滚动位置
  document.body.style.overflow = "";

  // 添加滚动事件监听
  window.addEventListener("scroll", handleScroll);

  // 如果用户已登录，获取用户信息
  if (isSignedIn) {
    await getUserInfo();
  }

  // 初始检查 sessionStorage 中是否有目标锚点
  const targetSection = sessionStorage.getItem("targetSection");
  if (targetSection && route.path === '/') {
    // 清除目标锚点
    sessionStorage.removeItem("targetSection");
    // 延迟执行滚动操作，确保DOM已加载完成
    setTimeout(() => {
      executeScroll(targetSection);
    }, 300);
  }
});

// 监听菜单打开状态，控制body滚动
watch(isOpen, (newValue) => {
  if (newValue) {
    document.body.style.overflow = "hidden";
  } else {
    document.body.style.overflow = "";
  }
});

// 组件卸载时恢复body滚动并移除事件监听
onUnmounted(() => {
  document.body.style.overflow = "";
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
/* 导航栏动画 */
.nav-enter-active,
.nav-leave-active {
  transition: all 0.3s ease;
}

.nav-enter-from,
.nav-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}

/* 覆盖hover效果 */
.hover-text-theme:hover {
  color: var(--baby-coral) !important;
}
</style> 