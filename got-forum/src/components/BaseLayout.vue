<template>
  <div class="grid">
    <div>
      <slot name="one"></slot>
    </div>
    <div>
      <slot name="two"></slot>
    </div>
  </div>
</template>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  border: 1px solid black;
}
</style>
