<script setup></script>

<template>
    <div class="wall" id="position__1">
        <div class="container"></div>
    </div>
    <div class="wall" id="position__2">
        <div class="container"></div>
    </div>
</template>

<style scoped>
.wall {
    width: fit-content;
    height: fit-content;

    background: transparent;
    left: 50%;
    transform: translateX(-50%);

    position: absolute;
    z-index: 8;
}

.container {
    height: 70px;
}

#position__1 {
    top: 2%;
}

#position__2 {
    top: 91%;
}
</style>