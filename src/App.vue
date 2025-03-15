<script setup>
import Menu from './components/menu.vue';
import Settings from './components/settings.vue';
import Results from './components/results.vue';
import GameOverModal from './components/modals/GameOverModal.vue';

import { reactive } from 'vue';
import Game from './components/game.vue';

/*
Data type list:
var local.page = []int{}
*/

const local = reactive({
    page: [1],
    settings: {
        amount: 5,
        speed: 1000,
        size: 0.8,
    },
    showModal: false,
});

// Changing current page by the mutation of the "page" variable
function pageChanger(page) {
    local.page[0] = page;
}

function saveParams(newParams) {
    local.settings = {...newParams};
}
</script>

<template>
    <Menu 
    @changePage="pageChanger"/>
    <Settings v-if="local.page[0] === 0"
    :savedParams="local.settings"
    @sendSettings="saveParams"/>
    <Game v-if="local.page[0] === 1"
    :gameParams="local.settings"/>
    <Results v-if="local.page[0] === 2"/>
    <GameOverModal v-if="local.showModal"/>
</template>

<style scoped>
/* .wrapper {
    width: max(400px, 40%);
    height: 400px;

    margin: 0 auto;

    background: var(--card-color);
    border: 2px solid var(--card-border-color);
    border-radius: 1rem;

    backdrop-filter: blur(1rem);
    box-shadow: 3px 5px 10px rgba(2, 2, 2, 0.56);

    display: grid;
    place-items: center;
} */
</style>
