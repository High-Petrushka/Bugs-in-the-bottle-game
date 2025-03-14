<script setup>
import { reactive, onMounted, onUnmounted } from 'vue';

const emit = defineEmits([
    'sendSettings',
]);

const props = defineProps({
    savedParams: Object,
});

const local = reactive({
    newParams: {
        amount: String,
        speed: String,
        size: String,
    },
});

function copyObj() {
    local.newParams = {...props.savedParams}
    console.log(local.newParams);
}

onMounted(() => {
    console.log("Mounted");

    copyObj(props.savedParams, local.newParams);
});

onUnmounted(() => {
    emit('sendSettings', local.newParams);
})
</script>

<template>
    <div class="container">
        <div class="wrapper">
            <h1>Settings</h1>
            <div class="settings-box">
                <h3>Target amount</h3>
                <h3>Target speed</h3>
                <h3>Target size</h3>

                <div class="param-box">
                    <input
                    type="radio"
                    name="amount"
                    class="param"
                    id="amount__1"
                    value="5" 
                    v-model="local.newParams.amount"
                    checked>
                </div>
                <div class="param-box">
                    <input 
                    type="radio" 
                    name="speed"
                     class="param"
                      id="speed__1"
                      value="5000" 
                      v-model="local.newParams.speed"
                      checked>
                </div>
                <div class="param-box">
                    <input 
                    type="radio" 
                    name="size" 
                    class="param" 
                    id="size__1"
                    value="1"
                    v-model="local.newParams.size"
                    checked>
                </div>

                <div class="param-box">
                    <input
                    type="radio"
                    name="amount"
                    class="param"
                    id="amount__2"
                    value="10"
                    v-model="local.newParams.amount">
                </div>
                <div class="param-box">
                    <input 
                    type="radio" 
                    name="speed" 
                    class="param" 
                    id="speed__2"
                    value="3000"
                    v-model="local.newParams.speed">
                </div>
                <div class="param-box">
                    <input 
                    type="radio" 
                    name="size" 
                    class="param" 
                    id="size__2"
                    value="1.5"
                    v-model="local.newParams.size">
                </div>

                <div class="param-box">
                    <input
                    type="radio"
                    name="amount"
                    class="param"
                    id="amount__3"
                    value="15"
                    v-model="local.newParams.amount">
                </div>
                <div class="param-box">
                    <input 
                    type="radio" 
                    name="speed" 
                    class="param" 
                    id="speed__3"
                    value="1000"
                    v-model="local.newParams.speed">
                </div>
                <div class="param-box">
                    <input 
                    type="radio" 
                    name="size" 
                    class="param" 
                    id="size__3"
                    value="2"
                    v-model="local.newParams.size">
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.wrapper {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: auto 1fr;
  row-gap: 40px;
}

.settings-box {
    width: 100%;

    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(4, 1fr);
    gap: 20px;
}

h3 {
    margin: 0 auto;
}

.param-box {
    padding: 0 8rem;

    position: relative;
}

.param {
    appearance: none;

    width: 100%;
    height: 100%;

    border: 2px solid var(--accent-color);
    border-radius: 0.75rem;

    cursor: pointer;
    transition: 0.35s ease-out;
}

.param:checked {
    background: var(--accent-color);
}

.param:checked::before {
    color: var(--card-border-color);
}

#amount__1::before {
    content: '5';

    font-size: 1.8rem;
    font-weight: 500;
    line-height: 1.7;
    letter-spacing: -.02rem;

    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

#amount__2::before {
    content: '10';

    font-size: 1.8rem;
    font-weight: 500;
    line-height: 1.7;
    letter-spacing: -.02rem;

    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

#amount__3::before {
    content: '15';

    font-size: 1.8rem;
    font-weight: 500;
    line-height: 1.7;
    letter-spacing: -.02rem;

    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

#speed__1::before {
    content: 'Low';

    font-size: 1.8rem;
    font-weight: 500;
    line-height: 1.7;
    letter-spacing: -.02rem;

    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

#speed__2::before {
    content: 'Medium';

    font-size: 1.8rem;
    font-weight: 500;
    line-height: 1.7;
    letter-spacing: -.02rem;

    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

#speed__3::before {
    content: 'High';

    font-size: 1.8rem;
    font-weight: 500;
    line-height: 1.7;
    letter-spacing: -.02rem;

    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

#size__1::before {
    content: 'Little';

    font-size: 1.8rem;
    font-weight: 500;
    line-height: 1.7;
    letter-spacing: -.02rem;

    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

#size__2::before {
    content: 'Medium';

    font-size: 1.8rem;
    font-weight: 500;
    line-height: 1.7;
    letter-spacing: -.02rem;

    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

#size__3::before {
    content: 'Large';

    font-size: 1.8rem;
    font-weight: 500;
    line-height: 1.7;
    letter-spacing: -.02rem;

    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}
</style>