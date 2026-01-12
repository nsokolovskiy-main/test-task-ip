<template>
  <main class="main">
    <slot></slot>
  </main>
</template>

<style lang="scss">
.main {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 20px;
  height: 100%;
}
</style>
