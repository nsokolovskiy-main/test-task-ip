<template>
  <div class="block-items">
    <div v-if="selectedLength === 0" class="block-items__empty">
      Ничего не выбрано
    </div>
    <div v-else class="block-items__items">
      <div
        v-for="(item, index) in selected"
        :key="index"
        class="block-items__item"
      >
        {{ item.name }}
      </div>
    </div>
    <div class="block-items__footer">
      Выбрано: {{ selected.length }} / {{ count }}
    </div>
  </div>
</template>

<script lang="ts" setup>
import { computed, defineProps, withDefaults } from 'vue'
import { TItems } from '@/types'

const props = withDefaults(
  defineProps<{ selected?: TItems; count: number }>(),
  {
    selected: () => [],
    count: 0,
  }
)

const selectedLength = computed(() => {
  return props.selected?.length
})
</script>

<style lang="scss">
.block-items {
  width: 25%;
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  align-items: start;
  gap: 40px;
  border: 2px solid black;
  border-radius: 10px;
  padding: 20px;

  &__items {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: 10px;
    width: 100%;
  }

  &__item {
    border: 1px solid black;
    border-radius: 5px;
    padding: 10px;
  }
}
</style>
