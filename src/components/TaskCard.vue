<script setup>
const props = defineProps({
    index: Number,
    title: String,
    description: String
})
const emit = defineEmits(['remove'])

const handleRemove = () => {
    emit('remove', { index: props.index })
}
</script>

<template>
  <div class="task">
    <h2>{{ title }}</h2>
    <p>{{ description }}</p>
    <button @click="handleRemove">Remove</button>
  </div>
</template>

<style scoped>
.task {
  width: 25rem;
  background-color: rgba(255, 255, 255, 0.08);
  margin-bottom: 1rem;
  padding: 1rem;
  border-radius: 4px;
}
.task h2 {
  margin: 0;
}
.task button {
  display: block;
  margin-left: auto;
  height: 2rem;
  background-color: #fe6601;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>