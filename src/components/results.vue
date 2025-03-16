<script setup>
const props = defineProps({
    resultList: Array,
});
</script>

<template>
    <div class="container">
        <div class="wrapper">
            <h1>Statistics</h1>
            <p>{{ props.resultList }}</p>
        </div>
    </div>
</template>

<style scoped>
.wrapper {
  display: grid;
  place-items: center;
}
</style>