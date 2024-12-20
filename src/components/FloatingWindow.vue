<template>
  <div class="pointer-events-none !fixed !inset-0 !z-[9999]">
    <vue-draggable-resizable
      :w="200"
      :h="200"
      :x="20"
      :y="20"
      :parent="false"
      :draggable="true"
      :resizable="true"
      :drag-handle="'.drag-handle'"
      class="!pointer-events-auto rounded-lg shadow-lg"
    >
      <div class="flex h-full flex-col overflow-hidden rounded-lg border border-gray-200 bg-[#fafafa]">
        <div class="drag-handle flex cursor-move items-center justify-between border-b border-gray-200 px-4 py-2">
          <h3 class="text-sm font-medium text-gray-700">浮动窗口</h3>
          <button class="text-gray-400 hover:text-gray-600" @click="handleClose">
            <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
        <div class="flex-1 p-4">
          <p class="text-sm text-gray-600">这是一个可拖拽和调整大小的浮动窗口示例。</p>
        </div>
      </div>
    </vue-draggable-resizable>
  </div>
</template>

<script setup lang="ts">
import 'vue-draggable-resizable/style.css'
import eventBus from '../utils/eventBus'

const handleClose = () => {
  eventBus.emit('showToast', {
    message: '模拟关闭',
    type: 'success',
  })
}
</script>

<style>
@import 'vue-draggable-resizable/style.css';

.handle {
  border: none !important;
  background: transparent !important;
}

.handle-tm,
.handle-bm {
  width: 100%;
  left: 0;
  margin-left: 0;
}

.handle-ml,
.handle-mr {
  height: 100%;
  top: 0;
  margin-top: 0;
}

.handle-tl,
.handle-tr,
.handle-bl,
.handle-br {
  width: 20px;
  height: 20px;
  margin: 0;
  z-index: 1;
}
.vdr {
  border: none !important;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(20px);
}

@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.bg-gradient-to-r {
  background-size: 150% 150%;
  animation: gradient 10s ease infinite;
}

@keyframes pulse {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

@keyframes border-flow {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.animate-border-flow {
  background-size: 200% 200%;
  animation: border-flow 3s linear infinite;
}
</style>
