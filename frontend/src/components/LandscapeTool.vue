<script setup lang="ts">
import type { Tool } from '../types/ToolTypes'
import benchIcon from '@/assets/tool-icon.png'

defineProps<{
  tool: Tool
}>()

const onImageError = (event: Event) => {
  const target = event.target as HTMLImageElement;
  target.src = benchIcon; // Set to benchIcon if the image fails to load
}
</script>

<template>
  <div class="landscape-tool" :title="tool.description">
    <div class="landscape-tool-header">
      <img 
        class="landscape-tool-icon" 
        :src="tool.icon_url || benchIcon" 
        @error="onImageError" 
        alt="tool.name" 
      />
      <div class="landscape-tool-name"> {{ tool.name }} </div>
    </div>
  </div>
</template>

<style scoped>

.landscape-tool-icon {
  width: 36px;
  height: 36px;
  border-radius: 8px;
}

.landscape-tool {
  padding-left: 2px;
  margin-left: 5px;
  border-radius: 8px;
  background-color: white;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  width: 60px;
  height: 60px;
  margin: 0.3em;
}

.landscape-tool-header {
  padding: 0.25rem;
}

.landscape-tool-name {
  font-size: 10px;
  font-weight: bold;
  color: black;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
} 
</style>
