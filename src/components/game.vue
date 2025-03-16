<script setup>
import { ref, reactive, onMounted, onUnmounted } from 'vue';

const emit = defineEmits([
    'changeModalState',
    'sendResult'
]);

const props = defineProps({
    gameParams: Object,
});

const local = reactive({
    timeRemainder: 0,
    targetRemainder: 0,
    params: Object,
    targetVisibility: false,
    hideTarget: false,
});

const positions = ref([]);

onMounted(() => {
    local.params = {...props.gameParams};

for (let i = 0; i < local.params.amount; i++) {
    positions.value.push({left: 0, top: 0, display: 'block'});
}
});

onUnmounted(() => {
    positions.value = new Array;
});

function timer() {
    generator();

    local.timeRemainder = 100;
    local.targetRemainder = 0;
    local.targetVisibility = true;

    restoreVisibillity();

    const timerIntervalID = setInterval(() => {
        if (local.timeRemainder < 1) {
            emit('sendResult', {optios: local.params, res: local.timeRemainder});
            local.targetVisibility = false;
            clearInterval(timerIntervalID);
            emit('changeModalState', true);
        } else {
            if (local.targetRemainder === Number(local.params.amount)) {
                emit('sendResult', {optios: local.params, res: local.timeRemainder});
                local.targetVisibility = false;
                local.timeRemainder = 0;
                clearInterval(timerIntervalID);
                emit('changeModalState', true);
            } else {
                local.timeRemainder -= 1;
                generator();
            }
        }
    }, Number(local.params.speed));
}

function moveTarget() {
        local.positionX = Math.floor(Math.random() * 515);
        local.positionY = Math.floor(Math.random() * 550);
}

function generator() {
    for(let i = 0; i < local.params.amount; i++) {
        positions.value[i].left = `${Math.floor(Math.random() * 515)}px`;
        positions.value[i].top = `${Math.floor(Math.random() * 550)}px`;
    }
}

function targetClick(index) {
    local.timeRemainder += 5;
    positions.value[index].display = 'none';
    local.targetRemainder++;
}

function restoreVisibillity() {
    for (let i = 0; i < local.params.amount; i++) {
        positions.value[i].display = 'block';
    }
}
</script>

<template>
    <div class="container">
        <div class="wrapper">
            <h1>Game</h1>
            <div class="game__field">
                <div 
                v-if="local.targetVisibility"
                v-for="item in Number(local.params.amount)"
                class="target"
                :style="[positions[item - 1], {transform: `scale(${local.params.size})`}]"
                @click="targetClick(item - 1)">Click</div>
            </div>
            <div class="timer__sect">
                <div class="timer__box">
                    <p>Time :</p>
                    <p>{{ local.timeRemainder }}</p>
                </div>
            </div>
            <div class="play__btn">
                <button @click="timer">Play</button>
            </div>
        </div>
    </div>
</template>

<style scoped>
.wrapper {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: auto 60rem auto;
  row-gap: 4rem;
}

.game__field {
    width: 600px;
    height: 100%;

    margin: 0 auto;

    border: 3px dashed var(--font-color);
    border-radius: 1rem;

    position: relative;
}

.target {
    padding: 0.75rem 1.75rem;
    background: var(--accent-color);
    border-radius: 0.75rem;

    font-size: 1.8rem;
    font-weight: 500;
    letter-spacing: -.02rem;
    color: var(--card-border-color);
    text-align: center;

    cursor: pointer;

    position: absolute;
    left: 0;
    top: 0;

    transform: scale(1);
    transition: 0.5s;
}

.play__btn {
    display: flex;
    justify-content: center;
}

.timer__sect {
    display: flex;
    justify-content: center;
}

.timer__box {
    width: 90px;
    height: fit-content;

    display: flex;
    justify-content: space-between;
}
</style>