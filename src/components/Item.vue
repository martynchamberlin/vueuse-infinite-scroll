<template>
  <div
    class="item"
    v-text="`#${text}`" />
</template>

<script lang="ts" setup>
defineProps({
  text: String
});
</script>

<style>
.item {
  width: 400px;
  height: 200px;
  border-radius: 4px;
  background: rgba(0, 0, 0, .1);
  margin: 0 0 20px 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 40px;
  opacity: .2;
}
</style>
