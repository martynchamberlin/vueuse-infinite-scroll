<template>
  <div>
  <h1><code>getMoreItems()</code> call count: {{ count }}</h1>

  <p><strong>Bug described:</strong> every time you scroll to the bottom of the movelist, the <code>getMoreItems()</code> gets called twice when it should only be called once. This results in the <code>count</code> variable increasing by <em>two</em>. Note that this is only reproducible when the callback passed to <code>useInfiniteScroll</code> resolves asynchronously.</p>
</div>

  <div
    class="scroll-outer"
    ref="scrollContainer">
     <Item
       v-for="(item, index) in items"
       :key="index" />
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import Item from './components/Item.vue';
import { useInfiniteScroll } from '@vueuse/core';

const items = ref(new Array(3));
const count = ref(0)
const scrollContainer = ref();

function getMoreItems() {
  count.value++;
  return new Promise((resolve) => {
    setTimeout(() => {
      items.value.push(...new Array(3));
      resolve();
    }, 400);
  });
}

onMounted(() => {
  useInfiniteScroll(scrollContainer.value, getMoreItems);
});
</script>


<style scoped>
button {
  font-weight: bold;
}

.scroll-outer {
  max-height: 250px;
  overflow: auto;
  background: rgba(255, 255, 255, .1);
  padding: 20px;
}

code {
  background: rgba(0, 0, 0, .03);
  border-radius: 4px;
  padding: 1px;
}
</style>
