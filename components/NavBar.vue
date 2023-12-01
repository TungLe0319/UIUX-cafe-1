<script setup lang="ts">
import { onBeforeUnmount, onMounted, ref } from 'vue'
import Button from './Globals/Button.vue'

const navTransform = ref('translateY(0)')
const Y = ref(0)
let lastScrollPosition = 0

const route = useRoute()
route.path

function handleScroll() {
  const scrollY = window.scrollY;


  Y.value = scrollY

  // Adjust the threshold value (200) based on your specific requirement
  const scrollThreshold = 200;

  navTransform.value =
    scrollY > lastScrollPosition && scrollY > scrollThreshold
      ? 'translateY(-100%)'
      : 'translateY(0)';

  lastScrollPosition = scrollY;
}

function handleIndicator(el: HTMLElement) {
  const indicator = document.querySelector('.nav-indicator') as HTMLElement
  const items = document.querySelectorAll('.nav-item')

  items.forEach((item) => {
    item.classList.remove('is-active')
    item.removeAttribute('style')
  })

  indicator.style.width = `${el.offsetWidth}px`
  indicator.style.left = `${el.offsetLeft}px`

  const activeColor = el.getAttribute('active-color')
  if (activeColor !== null) {
    indicator.style.backgroundColor = activeColor
    el.style.color = activeColor
  }

  el.classList.add('is-active')
}

interface HTMLElementWithActiveClass extends HTMLElement {
  classList: DOMTokenList & {
    contains(token: string): boolean
  }
}
// Function to setup listeners
function setupIndicatorListeners() {
  const items: NodeListOf<HTMLElement> = document.querySelectorAll('.nav-item')
  const indicator: HTMLElement | null
    = document.querySelector('.nav-indicator')

  items.forEach((item: HTMLElement) => {
    if (item.getAttribute('href') === route.path) {
      item.classList.add('is-active')
      handleIndicator(item)
    }
    item.addEventListener('click', e =>
      handleIndicator(e.target as HTMLElement))
    if ((item as HTMLElementWithActiveClass).classList.contains('is-active'))
      handleIndicator(item)
  })
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)

})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll)
})




const isOpen = ref(false)



</script>

<template>
  <div ref="nav"
    class="fixed top-0 z-50 transition-all flex flex-col items-center   w-full  lg:justify-center gap-4 lg:gap-0 bg-transparent backdrop-blur-lg p-2 text-gray-900 shadow-md  duration-300 ease-in-out"
    :style="{ transform: navTransform }">
  
      <div class="text-center p-2" :class="{ 'text-8xl': Y <= 400, 'text-3xl': Y > 200 }" transition="font-size">
        <h1>
          <span class="font-bold">Y</span>
          <span class="font-light">u</span>
          <span class="font-bold">n </span>
          <span class="font-light">C</span>
          <span class="font-bold">a</span>
          <span class="font-light">f</span>
          <span class="font-bold">e</span>
        </h1>
      </div>
      <div class="flex w-full items-center lg:justify-center justify-end">
        <Button class="bg-transparent lg:hidden block" label="Open" @click="isOpen = true">
          <Icon name="solar:hamburger-menu-linear" class="text-4xl" />
        </Button>
        <!-- OPEN & NAV BUTTONS -->
        <div class=" lg:hidden bloc lg:text-4xl font-bold p-2 text-center w-full ">
          Cafe
        </div>
        <div class="relative hidden w-fit overflow-hidden lg:inline-flex">
          <NuxtLink href="/" class="nav-item " active-color="red">
            Hours & Locations
          </NuxtLink>
          <NuxtLink href="/" class="nav-item" active-color="red">
            Menus
          </NuxtLink>
          <NuxtLink href="/" class="nav-item " active-color="red">
            Catering
          </NuxtLink>
          <NuxtLink href="/" class="nav-item" active-color="red">
            About
          </NuxtLink>
          <NuxtLink href="/" class="nav-item " active-color="red">
            Shop
          </NuxtLink>
          <NuxtLink href="/" class="nav-item bg-emerald-500 !px-4 " active-color="red">
            Order Online
          </NuxtLink>
          <!-- <span class="nav-indicator" /> -->
          <!-- OPEN & NAV BUTTONS -->
        </div>
        <USlideover v-model="isOpen" :ui="{
          background: 'dark:bg-white',

        }">
          <div class="  flex flex-col items-center h-full  justify-between ">
            <!-- CLOSE & NAV BUTTONS -->
            <div class="flex flex-col w-full items-center justify-center text-black text-6xl">
              <div class="flex w-full justify-start">
                <Button color="gray" @click="isOpen = false">
                  <Icon name="material-symbols:cancel-rounded" class="text-5xl text-black" />
                </Button>
              </div>
              <NuxtLink href="/" class="nav-item is-active" active-color="red">
                Home
              </NuxtLink>
              <NuxtLink href="/contact" class="nav-item" active-color="red">
                Contact</NuxtLink>
            </div>
            <!-- CLOSE & NAV BUTTONS -->
            <!-- ======================================== -->
            <!-- ACTION BUTTONS -->
            <div class="flex flex-col items-center  space-y-8 justify-center w-full pb-24 text-3xl ">
              <Button
                class="  rounded-full border-2 border-[var(--auburn)] text-[var(--auburn)]    hover:text-[var(--auburn)] bg-transparent   flex items-center justify-center gap-2 ">
                <Icon name="uis:schedule" class="text-5xl" />
                <span class="">Schedule Now</span>
              </Button>
              <Button
                class=" rounded-full  border-2 border-[var(--auburn)] text-[var(--auburn)]  bg-transparent flex items-center justify-center gap-2 ">
                <Icon name="carbon:star-review" class="text-5xl" />
                <span class="text-3xl">Review us on google</span>
              </Button>
              <Button class=" rounded-full  bg-[var(--auburn)]   shadow-md flex items-center justify-center gap-2">
                <Icon name="material-symbols:call" class="text-5xl" />
                <span>1-208-921-232</span>
              </Button>
            </div>
            <!-- ACTION BUTTONS -->
          </div>
        </USlideover>
      </div>
  
  </div>
</template>

<style scoped>
.text-8xl {
  font-size: 8rem;
  transition: font-size 0.75s ease;
  /* Adjust the transition duration and timing function as needed */
}

.text-3xl {
  font-size: 3rem;
  transition: font-size 0.75s ease;
  /* Adjust the transition duration and timing function as needed */
}





.nav-item {
  @apply transition-all duration-300 ease-in-out p-1 font-bold relative mx-2;

}

.nav-item:before {
  content: "";
  position: absolute;
  bottom: -6px;
  left: 0;
  width: 100%;
  height: 5px;
  background-color: #801616;
  border-radius: 8px 8px 0 0;
  opacity: 0;
  transition: 0.3s;
}

.nav-item:not(.is-active):hover:before {
  opacity: 1;
  bottom: 0;
}

.nav-indicator {
  position: absolute;
  left: 0;
  bottom: 0;
  height: 4px;
  transition: 0.4s;
  height: 5px;
  z-index: 1;
  border-radius: 8px 8px 0 0;
}

@media (max-width: 580px) {
  .nav {
    overflow: auto;
  }
}
</style>
