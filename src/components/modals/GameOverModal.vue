<script setup>
    const emit = defineEmits([
        'changeModalState',
        'unlockBtn'
    ]);

    const props = defineProps({
        resultVal: Number,
    });

    function sendRespond() {
        emit('changeModalState', false);
        emit('unlockBtn', false);
    }
</script>

<template>
    <div class="modal__cont">
        <div class="container">
            <div class="wrapper">
                <div class="result__cont">
                    <h1 class="modal__title">Game Over</h1>
                    <div class="modal__message">
                        <h3>Your result is :</h3>
                        <p>{{ props.resultVal }}</p>
                    </div>
                    <div class="modal__btn">
                        <button
                        @click="sendRespond">OK</button>
                    </div>
                </div>
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

    position: fixed;
    z-index: 10;
}

.container {
    width: 400px;
}

.wrapper {
    display: grid;
    align-items: stretch;
}

.result__cont {
    width: 100%;

    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: auto 1fr auto;
}

.modal__title {
    margin: 0 auto;
}

.modal__message {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 1rem;
}

.modal__message h3 {
    font-weight: 500;
}

.modal__btn {
    display: flex;
    justify-content: center;
}
</style>