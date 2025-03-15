<script setup></script>

<template>
    <div class="modal__cont">
        <div class="container">
            <div class="wrapper">
                <div class="result__cont"></div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.modal__cont {
    width: 100vw;
    height: 100%;

    background-color: var(--modal-background-color);
    backdrop-filter: blur(10px);

    display: grid;
    place-items: center;

    position: absolute;
    z-index: 10;
}

.container {
    width: 400px;
}

.result__cont {
    width: 100%;
    height: 100%;

    display: grid;
    grid-template-columns: 1fr;
}
</style>