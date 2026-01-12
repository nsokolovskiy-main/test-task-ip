<template>
  <div class="content">
    <LayoutHeader>
      <BlockSelectedItems
        :selected="selectedItems"
        :count="MAX_SELECTED_ITEMS"
      />
      <BlockSelectedItem :item="selectedItem" />
    </LayoutHeader>
    <LayoutMain>
      <ContainerItems :data="DATA_USER" @on-click-item="onClickUserItem" />
      <ContainerItems :data="DATA_SHOP" @on-click-item="onClickShopItem" />
    </LayoutMain>
  </div>
</template>

<script lang="ts" setup>
import { ref, reactive } from 'vue'
import type { Ref, Reactive } from 'vue'
import { IItem, TItems } from '@/types'

import {
  LayoutHeader,
  LayoutMain,
  BlockSelectedItems,
  BlockSelectedItem,
  ContainerItems,
} from './components/'

import { dataUserItems, dataShopItems } from './data'

// Статичные данные, которые не могут меняться
const DATA_USER = dataUserItems
const DATA_SHOP = dataShopItems
// Все числовые константы лучше выносить в отдельную переменную
const MAX_SELECTED_ITEMS = 6

// Массив выбранных вещей
const selectedItems: Reactive<TItems> = reactive([])

function onClickUserItem(value: IItem) {
  const valueIndex = selectedItems.findIndex((item) => item.id === value.id)

  // аналог valueIndex !== -1
  if (~valueIndex) {
    selectedItems.splice(valueIndex, 1)
  } else if (selectedItems.length < MAX_SELECTED_ITEMS) {
    selectedItems.push(value)
  }
}

// Конкретная выбранная вещь
const selectedItem: Ref<IItem | null> = ref(null)

function onClickShopItem(value: IItem) {
  selectedItem.value = value
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: calc(100vh - 48px);
  padding: 16px;
}

.content {
  display: flex;
  flex-direction: column;
  max-width: 1000px;
  margin: 0 auto;
  height: 100%;
  gap: 20px;
}
</style>
