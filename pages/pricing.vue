<template>
  <div class="min-h-screen bg-banana-dark-bg text-banana-text-light">
    <main class="w-full mx-auto bg-banana-dark-bg rounded-lg max-w-7xl min-h-screen">
      <!-- 页面标题区域 -->
      <section>
        <div class="container mx-auto px-4">
          <PageHero 
            class="mt-20 mb-16"
            title="Nano Banana AI Pricing"
            subtitle="Unlock the full power of Nano Banana with a plan that scales with your ambition. No hidden fees, cancel anytime."
          />
        </div>
      </section>

      <!-- 加载状态 -->
      <section v-if="pending" class="flex justify-center items-center py-20 w-full" aria-live="polite">
        <div
          class="animate-spin rounded-full h-12 w-12 border-t-2 border-b-2 border-purple-500"
          aria-label="Loading pricing plans"
        ></div>
      </section>

      <!-- 定价方案区域 -->
      <section
        v-else
        class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-6 lg:gap-8 max-w-7xl mx-auto place-items-stretch"
        aria-label="Pricing plans"
      >
        <!-- 循环渲染套餐卡片 -->
        <article
          v-for="(plan, index) in planData"
          :key="index"
          :class="[
            'relative bg-banana-card-bg rounded-xl p-6 flex flex-col h-full',
            plan.is_popular
              ? 'border-2 border-banana-primary-yellow shadow-2xl scale-105 z-10'
              : 'border border-banana-border-color shadow-lg hover:shadow-2xl hover:-translate-y-1 transition-all duration-300',
            plan.price === 0 ? 'hidden md:flex' : 'flex'
          ]"
          :aria-labelledby="`plan-${index}-title`"
        >
          <!-- 热门标签 -->
          <div
            v-if="plan.is_popular"
            class="absolute -top-4 left-1/2 transform -translate-x-1/2 px-4 py-2 bg-gradient-to-r from-banana-primary-yellow to-banana-secondary-blue text-banana-dark-bg text-sm font-semibold rounded-full z-20 shadow-lg"
            aria-label="Most popular plan"
          >
            ⭐ Most Popular
          </div>

          <!-- 套餐标题 -->
          <header class="text-center mb-6">
            <h3 
              :id="`plan-${index}-title`"
              class="text-2xl font-bold text-banana-text-light mb-3"
            >
              {{ plan.name }}
            </h3>
            <p class="text-banana-text-muted text-sm leading-relaxed" v-html="plan.description"></p>
          </header>

          <!-- 价格信息 -->
          <div class="mb-6 text-center">
            <div class="bg-gradient-to-br from-banana-dark-bg to-gray-900 rounded-xl p-6 border border-banana-border-color shadow-sm">
              <div class="inline-flex items-baseline gap-2">
                <span class="text-4xl font-bold text-banana-primary-yellow">${{ plan.price }}</span>
                <span v-if="plan.price === 9.9" class="text-xl text-banana-primary-yellow/50 line-through">$12</span>
                <span v-if="plan.price === 29.9" class="text-xl text-banana-primary-yellow/50 line-through">$33</span>
                <span v-if="plan.price === 69.9" class="text-xl text-banana-primary-yellow/50 line-through">$74</span>
                <span class="text-sm text-banana-text-muted font-medium bg-banana-card-bg px-3 py-1 rounded-full shadow-sm">one-time</span>
              </div>
            </div>
          </div>

          <!-- 操作按钮 -->
          <div class="mb-8">
            <button
              @click="plan.code ? handleUpgradePlan(plan) : null"
              :disabled="upgradingPlanId === plan.code"
              :class="[
                'w-full py-4 px-6 rounded-xl font-semibold text-base flex items-center justify-center transition-all duration-300 transform hover:scale-105',
                getButtonClass(plan),
              ]"
              :aria-describedby="`plan-${index}-title`"
            >
              <div v-if="upgradingPlanId === plan.code" class="animate-spin rounded-full h-5 w-5 border-t-2 border-b-2 border-current mr-2" aria-hidden="true"></div>
              {{ plan.button_text }}
            </button>
          </div>

          <!-- 功能特性列表 -->
          <section class="flex-grow" :aria-label="`${plan.name} plan features`">
            <ul class="space-y-4">
              <li
                v-for="(feature, fIndex) in getPlanFeatures(plan)"
                :key="fIndex"
                class="flex items-start text-banana-text-muted"
              >
                <span class="mr-3 text-green-500 font-bold text-lg flex-shrink-0 mt-0.5" aria-hidden="true">✅</span>
                <span class="text-sm leading-relaxed" v-html="feature"></span>
              </li>
            </ul>
          </section>
        </article>
      </section>

      <!-- How Credits Work Section -->
      <section class="mt-20 py-12 bg-banana-card-bg rounded-xl border border-banana-border-color shadow-lg">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8">
          <div class="text-center mb-12">
            <h2 class="text-3xl font-bold text-banana-text-light sm:text-4xl">How Do Credits Work?</h2>
            <p class="mt-4 text-lg text-banana-text-muted">
              Credits are the universal currency for creating in Nano Banana AI. Use them for various actions like generating images or accessing advanced features. Your credit balance is deducted based on your usage.
            </p>
            <div class="mt-6 inline-block bg-banana-dark-bg px-4 py-2 rounded-lg border border-banana-border-color">
              <p class="text-base font-medium text-banana-primary-yellow">Example: 1 Standard Image Generation = 1 Credit.</p>
            </div>
          </div>
        </div>
      </section>

      <!-- FAQ Section -->
      <section class="mt-16 py-12">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8">
          <div class="text-center mb-12">
            <h2 class="text-3xl font-bold text-banana-text-light sm:text-4xl">Frequently Asked Questions</h2>
          </div>
          <div class="max-w-7xl mx-auto grid md:grid-cols-2 gap-6">
            <div v-for="(faq, index) in faqs" :key="index" class="bg-banana-card-bg rounded-lg p-6 border border-banana-border-color transition-all duration-300 hover:border-banana-primary-yellow">
              <h3 class="font-semibold text-lg text-banana-text-light flex items-start">
                <span class="text-banana-primary-yellow font-bold mr-3">{{ String(index + 1).padStart(2, '0') }}</span>
                <span>{{ faq.question }}</span>
              </h3>
              <p class="mt-4 text-banana-text-muted pl-8">{{ faq.answer }}</p>
            </div>
          </div>
        </div>
      </section>
      
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref, watch, computed } from "vue";
import { getSubPlans, payOrder } from "~/api/index";
import { useClerkAuth } from '~/utils/authHelper';
import { useSeo } from '~/composables/useSeo';
import { useAsyncData } from 'nuxt/app';
import PageHero from '~/components/PageHero.vue';

// FAQ data
const faqs = ref([
  {
    question: 'Is this a one-time payment? Are there any other fees?',
    answer: 'Absolutely. This is a one-time payment for the credits themselves. There are no subscription fees, monthly charges, or any hidden costs involved.'
  },
  {
    question: 'Do the purchased credits expire?',
    answer: 'No, they don\'t. All credits you purchase are valid forever. You can use them whenever you like, with no time restrictions.'
  },
  {
    question: 'How are credits consumed?',
    answer: 'A standard image generation consumes one credit. We may introduce more advanced features in the future, like ultra-high-resolution upscaling, which might have different credit costs. The cost of any action will be clearly displayed before you confirm it.'
  },
  {
    question: 'What if I run out of credits?',
    answer: 'You can always return to this page to purchase more credit packages. You can buy any package as many times as you need, and the credits will be added to your existing balance.'
  },
  {
    question: 'Where can I check my remaining credits?',
    answer: 'Once you\'re logged in, your remaining credit balance will always be prominently displayed on your personal account dashboard or within the creation interface.'
  },
  {
    question: 'What payment methods are supported?',
    answer: 'We use Stripe as our payment processing partner. Through Stripe, we securely accept all major credit cards, such as Visa, MasterCard, and American Express. Your payment information is handled directly by Stripe, and we do not store any sensitive card details.'
  }
]);

// 定义套餐数据类型
interface PricingPlan {
  name: string;
  description: string;
  price: number;
  code: string;
  button_text: string;
  is_popular: boolean;
  features: string | string[];
}

// 设置SEO
useSeo({
  title: 'Nano Banana AI Image Editing Plans',
  description: 'Explore simple Nano Banana pricing. Get unlimited AI image editing and find the plan that fits you best.',
});

// 引入auth认证
const {
  isSignedIn
} = useClerkAuth();

// 用户状态
const upgradingPlanId = ref<string | null>(null);

// 使用useAsyncData获取套餐数据
const { data, pending, error } = await useAsyncData('pricingPlans', async () => {
  try {
    const response = await getSubPlans();
    return response.data as PricingPlan[];
  } catch (err) {
    console.error('Error fetching pricing plans:', err);
    throw err;
  }
}, {
  // immediate: true
});

// 监听数据变化
watch(data, (newData) => {
  console.log('Pricing data updated:', newData);
});

// 计算属性：确保data有值时才返回
const planData = computed(() => {
  return data.value || [];
});

// 获取套餐特性列表
const getPlanFeatures = (plan: PricingPlan): string[] => {
  if (!plan.features) return [];
  // 如果特性是字符串，按逗号分割
  if (typeof plan.features === 'string') {
    return plan.features.split(',').map((feature: string) => feature.trim());
  }
  // 如果已经是数组，直接返回
  return Array.isArray(plan.features) ? plan.features : [];
};

  // 获取按钮样式
const getButtonClass = (plan: PricingPlan): string => {
    return "bg-banana-primary-yellow text-banana-dark-bg hover:opacity-90";
  if (plan.price === 0) {
    return "bg-banana-border-color text-banana-text-muted cursor-not-allowed";
  } else if (plan.is_popular) {
    return "bg-banana-primary-yellow text-banana-dark-bg hover:opacity-90";
  } else {
    return "bg-banana-secondary-blue text-white hover:opacity-90";
  }
};

// 处理升级计划
const handleUpgradePlan = async (plan: PricingPlan) => {
  // 如果没有登录，则提示登录并触发登录
  if (!isSignedIn.value) {
    try {
      const loginBtn = document.querySelector('#bindLogin') as HTMLElement;
      if (loginBtn) {
        loginBtn.click();
      }
    } catch (error) {
      console.error("Failed to find login:", error);
    }
    return;
  }

  upgradingPlanId.value = plan.code;
  try {
    const response = (await payOrder({ price_id: plan.code })) as any;
    if (response.code === 200 && response.data?.url) {
      window.location.href = response.data.url;
    } else {
      throw new Error(response.msg || "Failed to create payment order");
    }
  } catch (error) {
    console.error("Payment failed:", error);
  } finally {
    upgradingPlanId.value = null;
  }
};
</script>

<style scoped>
.hover-theme:hover {
  background-color: var(--theme-primary-hover) !important;
  color: #fff !important;
}

.text-theme {
  color: #ec2657;
}
</style> 