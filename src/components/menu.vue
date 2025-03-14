<script setup>
import { reactive } from 'vue';

const emit = defineEmits([
    'changePage',
]);

// Sending the desired page number to the "App"
function sendPage(page) {
    emit('changePage', page);
}
</script>

<template>
    <section class="container">
        <nav class="menu">
            <div class="link-box">
                <p
                class="link"
                @click="sendPage(0)">Settings</p>
            </div>
            <div class="link-box">
                <p
                class="link"
                @click="sendPage(1)">Game</p>
            </div>
            <div class="link-box">
                <p
                class="link"
                @click="sendPage(2)">Statistics</p>
            </div>
        </nav>
    </section>
</template>

<style scoped>
.menu {
    width: 100%;
    height: fit-content;

    background: var(--card-color);
    border: 2px solid var(--card-border-color);
    border-radius: 1rem;

    box-shadow: 3px 5px 10px rgba(2, 2, 2, 0.56);

    padding: 1.75rem 2.5rem;

    display: flex;
    align-items: center;
    justify-content: space-around;
}

.link-box {
    width: fit-content;
    position: relative;
}

.link {
    cursor: pointer;
}

.link::before {
    content: '';

    width: 0%;
    height: 3px;

    background: var(--font-color);
    border-radius: 10rem;

    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);

    transition: 0.35s;
}

.link-box:hover>.link::before {
    width: 100%;
}
</style>