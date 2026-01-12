<template>
  <div class="selected-item">
    {{ item?.name || 'Ничего не выбрано' }}
  </div>
</template>

<script lang="ts" setup>
import { defineProps } from 'vue'
import { IItem } from '@/types'

defineProps<{ item: IItem | null }>()
</script>

<style lang="scss">
.selected-item {
  width: 25%;
  border: 2px solid black;
  border-radius: 10px;
  padding: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 2em;
}
</style>
