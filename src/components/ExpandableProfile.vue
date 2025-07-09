<template>
  <div class="profile-container">
    <div class="header" @click="toggle">
      <div
          :class="['name-block', namePosition]"
          :style="namePosition === 'left'
            ? { marginLeft: randomMargin + 'px' }
            : { marginRight: randomMargin + 'px' }"
      >
        <div class="name">{{ data.firstName }}</div>
        <div class="surname-row">
          <template v-if="namePosition === 'left'">
            <div class="surname">{{ data.lastName }}</div>
            <div class="svg-arrow-header" @click.stop="toggle">
              <svg width="20" height="20" viewBox="0 0 100 100">
                <polygon points="10,25 90,25 50,100" fill="#d6dec9"/>
              </svg>
            </div>
          </template>
          <template v-else>
            <div class="svg-arrow-header" @click.stop="toggle">
              <svg width="20" height="20" viewBox="0 0 100 100">
                <polygon points="10,25 90,25 50,100" fill="#d6dec9"/>
              </svg>
            </div>
            <div class="surname">{{ data.lastName }}</div>
          </template>
        </div>
      </div>
    </div>

    <transition name="expand">
      <div v-if="isOpen" class="details">
        <div class="text-block">
          <div class="text-top">{{ data.textTop }}</div>
        </div>

        <div class="slider" @wheel.prevent="onWheel">
          <div class="svg-arrow left" @click.stop="handlePrev" v-if="data.images.length > 1">
            <svg width="24" height="24" viewBox="0 0 100 100">
              <polygon points="75,10 75,90 10,50" fill="#d6dec9"/>
            </svg>
          </div>

          <div
              class="slider-window"
              ref="windowEl"
              @touchstart="onTouchStart"
              @touchend="onTouchEnd"
              @touchmove.prevent
          >
            <transition :name="slideTransition">
              <img
                  :key="currentImage"
                  :src="data.images[currentImage]"
                  alt="photo"
                  class="slide-image"
                  @load="updateHeight"
              />
            </transition>
          </div>

          <div class="svg-arrow right" @click.stop="handleNext" v-if="data.images.length > 1">
            <svg width="24" height="24" viewBox="0 0 100 100">
              <polygon points="25,10 25,90 90,50" fill="#d6dec9"/>
            </svg>
          </div>
        </div>

        <div class="text-block">
          <div class="text-middle" v-if="data.textMiddle.length > 0">
            {{ data.textMiddle }}
          </div>
        </div>

        <div class="text-block">
          <div class="text-bottom" style="margin-top: 2rem">
            {{ data.linkText }}
            <a :href="data.linkUrl" target="_blank" class="text-link">{{ data.linkAnchor }}</a>
          </div>
          <div class="text-bottom" v-if="data.siteText.length">
            {{ data.siteText }}
            <a :href="data.siteUrl" target="_blank" class="text-link">{{ data.siteAnchor }}</a>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup>
import {ref, defineProps, computed, watch, nextTick, onMounted} from 'vue'

const props = defineProps({
  namePosition: {
    type: String,
    default: 'left',
    validator: val => ['left', 'right'].includes(val)
  },
  data: {
    type: Object,
    required: true
  }
})

const {data, namePosition} = props
const isOpen = ref(false)
const currentImage = ref(0)
const direction = ref('next')
const windowEl = ref(null)

const slideTransition = computed(() => direction.value === 'next' ? 'slide-next' : 'slide-prev')

function toggle() {
  isOpen.value = !isOpen.value
}

function handleNext() {
  direction.value = 'next'
  currentImage.value = (currentImage.value + 1) % data.images.length
  nextTick(updateHeightForCurrent)
}

function handlePrev() {
  direction.value = 'prev'
  currentImage.value = (currentImage.value - 1 + data.images.length) % data.images.length
  nextTick(updateHeightForCurrent)
}

function onWheel(e) {
  (e.deltaY > 0 ? handleNext : handlePrev)(e)
}

function updateHeight(event) {
  // Use rendered height, not naturalHeight
  const imgEl = event.target
  if (windowEl.value && imgEl) {
    const height = imgEl.getBoundingClientRect().height
    windowEl.value.style.height = height + 'px'
  }
}

function updateHeightForCurrent() {
  if (!windowEl.value) return
  const img = windowEl.value.querySelector('img')
  if (img) {
    const height = img.getBoundingClientRect().height
    windowEl.value.style.height = height + 'px'
  }
}

// При открытии адаптируем высоту после рендера
watch(isOpen, async opened => {
  if (opened) {
    await nextTick()
    updateHeightForCurrent()
  }
})

const randomMargin = ref(0)

function preloadImages(imageUrls) {
  imageUrls.forEach(src => {
    const img = new Image()
    img.src = src
  })
}

onMounted(() => {
  const step = 7
  const max = 22
  randomMargin.value = Math.floor(Math.random() * ((max / step) + 1)) * step

  preloadImages(data.images)
})

const touchStartX = ref(0)
const touchEndX = ref(0)
const swipeThreshold = 50

function onTouchStart(e) {
  touchStartX.value = e.changedTouches[0].clientX
}

function onTouchEnd(e) {
  touchEndX.value = e.changedTouches[0].clientX
  handleSwipe()
}

function handleSwipe() {
  const diff = touchEndX.value - touchStartX.value
  if (Math.abs(diff) > swipeThreshold) {
    if (diff > 0) {
      handlePrev()
    } else {
      handleNext()
    }
  }
}
</script>

<style scoped>
.profile-container {
  width: 100%;
  max-width: 360px;
  margin-bottom: 6rem;
}

.header {
  width: 100%;
}

.name-block {
  display: flex;
  flex-direction: column;
  font-family: "FirstNue", sans-serif;
  font-size: 48px;
  color: var(--color-green-light);
  cursor: pointer;
}

.name-block.left {
  align-items: flex-start;
}

.name-block.right {
  align-items: flex-end;
}

.surname-row {
  display: inline-flex;
  align-items: center;
}

.surname {
}

.svg-arrow-header {
  width: 16px;
  height: 16px;
  margin: 0 15px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  user-select: none;
}

.details {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.text-block {
  font-family: "FirstNue", sans-serif;
  color: var(--color-green-light);
  font-size: 16px;
  width: 93%;
}

.text-top {
  margin-block: 2rem;
}

.text-middle {
  margin-top: 2rem;
  white-space: pre-line;
}

.text-bottom {

}

.text-link {
  text-decoration: underline;
  color: inherit;
}

.expand-enter-active,
.expand-leave-active {
  transition: max-height 0.3s ease;
  overflow: hidden;
}

.expand-enter-from,
.expand-leave-to {
  max-height: 0;
}

.expand-enter-to,
.expand-leave-from {
  max-height: 1000px;
}

.slider {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 93%;
  overflow: hidden;
  background-color: #fff;
}

.slider-window {
  width: 100%;
  position: relative;
  transition: height 0.3s ease;
  overflow: hidden;
}

.slide-next-enter-active,
.slide-next-leave-active,
.slide-prev-enter-active,
.slide-prev-leave-active {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  transition: transform 300ms ease;
}

.slide-next-enter-from {
  transform: translateX(100%);
}

.slide-next-enter-to {
  transform: translateX(0);
}

.slide-next-leave-from {
  transform: translateX(0);
}

.slide-next-leave-to {
  transform: translateX(-100%);
}

.slide-prev-enter-from {
  transform: translateX(-100%);
}

.slide-prev-enter-to {
  transform: translateX(0);
}

.slide-prev-leave-from {
  transform: translateX(0);
}

.slide-prev-leave-to {
  transform: translateX(100%);
}

.slide-image {
  width: 100%;
  display: block;
  object-fit: contain;
}

.svg-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 20px;
  height: 20px;
  cursor: pointer;
  user-select: none;
  z-index: 1;
}

.svg-arrow.left {
  left: 0.5rem;
}

.svg-arrow.right {
  right: 0.5rem;
}
</style>
