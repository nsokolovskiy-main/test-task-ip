<template>
  <div class="container__wrapper">
    <div class="container">
      <div
        v-for="(item, index) in data"
        :key="index"
        class="container__item"
        @click="onClick(item)"
      >
        {{ item.name }}
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { IItem, TItems } from '@/types'

import { defineProps, defineEmits } from 'vue'

defineProps<{ data?: TItems }>()

const emit = defineEmits(['onClickItem'])

function onClick(value: IItem) {
  emit('onClickItem', value)
}
</script>

<style lang="scss">
.container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 10px;
  padding: 20px;

  &__wrapper {
    height: 100%;
    border: 2px solid black;
    border-radius: 10px;
  }

  &__item {
    border: 1px solid black;
    border-radius: 5px;
    padding: 10px;
    cursor: pointer;
    transition: background 0.2s;

    &:hover {
      background: rgb(255, 229, 208);
    }
  }
}
</style>
