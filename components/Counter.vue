<script setup lang="ts">
const counterStore = useCounterStore();

onMounted(() => {
  handleFetchCount();
});

function handleFetchCount() {
  counterStore.fetchCount().catch((e) => alert("Error"));
}

function handleIncrement() {
  counterStore.incrementCount().catch((e) => alert(e.message));
}
</script>

<template>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-4 my-10">
    <p class="p-2 rounded-xl text-center">Count: {{ counterStore.count }}</p>
    <button
      @click="handleFetchCount"
      class="bg-sky-500 text-white p-2 rounded-xl"
    >
      Refetch Count
    </button>
    <button
      @click="handleIncrement"
      class="bg-sky-500 text-white p-2 rounded-xl"
    >
      Increment Count
    </button>
  </div>
</template>
