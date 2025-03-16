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
        speed: '1000',
        size: '0.8',
    },
    showModal: false,
    userResults: [],
    curResult: 0,
});

// Changing current page by the mutation of the "page" variable
function pageChanger(page) {
    local.page[0] = page;
}

function saveParams(newParams) {
    local.settings = {...newParams};
}

function modalAction(state) {
    local.showModal = state;
}

function takeResult(resInfo) {
    switch (resInfo.options.speed) {
        case '1000':
            resInfo.options.speed = 'Low';
            break;
        case '800':
            resInfo.options.speed = 'Medium';
            break;
        case '500':
            resInfo.options.speed = 'High';
            break;
    }

    switch (resInfo.options.size) {
        case '0.8':
            resInfo.options.size = 'Little';
            break;
        case '1':
            resInfo.options.size = 'Medium';
            break;
        case '1.2':
            resInfo.options.size = 'Large';
            break;
    }
 
    local.userResults.push(resInfo);
    local.curResult = resInfo.res;
}
</script>

<template>
    <Menu 
    @changePage="pageChanger"/>
    <Settings v-if="local.page[0] === 0"
    :savedParams="local.settings"
    @sendSettings="saveParams"/>
    <Game v-if="local.page[0] === 1"
    :gameParams="local.settings"
    @change-modal-state="modalAction"
    @sendResult="takeResult"/>
    <Results v-if="local.page[0] === 2"
    :resultList="local.userResults"/>
    <GameOverModal v-if="local.showModal"
    :resultVal="local.curResult"
    @change-modal-state="modalAction"/>
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
