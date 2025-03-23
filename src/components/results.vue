<script setup>
import { reactive } from 'vue';

const props = defineProps({
    resultList: Array,
});

const local = reactive({
    amountCondition: 'none',
    speedCondition: 'none',
    sizeCondition: 'none',
});
</script>

<template>
    <div class="container">
        <div class="wrapper">
            <h1>Statistics</h1>
            <div class="stat__cont">
                <div class="res__box">
                    <div class="table">
                        <div class="table__row table__title">
                            <div class="table__tile">
                                <p>Amount</p>
                            </div>
                            <div class="table__tile">
                                <p>Speed</p>
                            </div>
                            <div class="table__tile">
                                <p>Size</p>
                            </div>
                            <div class="table__tile">
                                <p>Total result</p>
                            </div>
                        </div>
                        <template v-for="(item) in props.resultList">
                            <div
                            v-if="(item.options.amount == local.amountCondition ||
                                item.options.speed == local.speedCondition ||
                                item.options.size == local.sizeCondition
                            ) || (
                                local.amountCondition === 'none' &&
                                local.speedCondition === 'none' &&
                                local.sizeCondition === 'none'
                            )"
                            class="table__row">
                                <div class="table__tile">
                                    <p>{{ item.options.amount }}</p>
                                </div>
                                <div class="table__tile">
                                    <p>{{ item.options.speed }}</p>
                                </div>
                                <div class="table__tile">
                                    <p>{{ item.options.size }}</p>
                                </div>
                                <div class="table__tile">
                                    <p>{{ item.res }}</p>
                                </div>
                            </div>
                        </template>
                    </div>
                </div>
                <div class="filter__box">
                    <div class="sort__cont">
                        <div class="sort__title">
                            <h3>Sort by amount</h3>
                        </div>
                        <div class="sort__params">
                            <div class="param__box">
                                <label for="amount">
                                    <input class="sort__radio" type="radio" name="amount" 
                                    value="5" v-model="local.amountCondition">
                                    5
                                </label>
                            </div>
                            <div class="param__box">
                                <label for="amount">
                                    <input class="sort__radio" type="radio" name="amount" 
                                    value="10" v-model="local.amountCondition">
                                    10
                                </label>
                            </div>
                            <div class="param__box">
                                <label for="amount">
                                    <input class="sort__radio" type="radio" name="amount" 
                                    value="15" v-model="local.amountCondition">
                                    15
                                </label>
                            </div>
                            <div class="param__box">
                                <label for="amount">
                                    <input class="sort__radio" type="radio" name="amount" 
                                    value="none" v-model="local.amountCondition">
                                    No filtering
                                </label>
                            </div>
                        </div>
                    </div>
                    <div class="sort__cont">
                        <div class="sort__title">
                            <h3>Sort by speed</h3>
                        </div>
                        <div class="sort__params">
                            <div class="param__box">
                                <label for="speed">
                                    <input class="sort__radio" type="radio" name="speed" 
                                    value="Low" v-model="local.speedCondition">
                                    Low
                                </label>
                            </div>
                            <div class="param__box">
                                <label for="speed">
                                    <input class="sort__radio" type="radio" name="speed" 
                                    value="Medium" v-model="local.speedCondition">
                                    Medium
                                </label>
                            </div>
                            <div class="param__box">
                                <label for="speed">
                                    <input class="sort__radio" type="radio" name="speed" 
                                    value="High" v-model="local.speedCondition">
                                    High
                                </label>
                            </div>
                            <div class="param__box">
                                <label for="speed">
                                    <input class="sort__radio" type="radio" name="speed" 
                                    value="none" v-model="local.speedCondition">
                                    No filtering
                                </label>
                            </div>
                        </div>
                    </div>
                    <div class="sort__cont">
                        <div class="sort__title">
                            <h3>Sort by size</h3>
                        </div>
                        <div class="sort__params">
                            <div class="param__box">
                                <label for="size">
                                    <input class="sort__radio" type="radio" name="size" 
                                    value="Little" v-model="local.sizeCondition">
                                    Little
                                </label>
                            </div>
                            <div class="param__box">
                                <label for="size">
                                    <input class="sort__radio" type="radio" name="size" 
                                    value="Medium" v-model="local.sizeCondition">
                                    Medium
                                </label>
                            </div>
                            <div class="param__box">
                                <label for="size">
                                    <input class="sort__radio" type="radio" name="size" 
                                    value="Large" v-model="local.sizeCondition">
                                    Large
                                </label>
                            </div>
                            <div class="param__box">
                                <label for="size">
                                    <input class="sort__radio" type="radio" name="size" 
                                    value="none" v-model="local.sizeCondition">
                                    No filtering
                                </label>
                            </div>
                        </div>
                    </div>
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
  row-gap: 4rem;
}

h3 {
    font-size: 2rem;
}

.stat__cont {
    width: 100%;
    height: 100%;

    display: grid;
    grid-template-columns: 3fr 1fr;
    grid-template-rows: 1fr;
    column-gap: 4rem;
}

.res__box {
    padding: 0 2rem;
}

.table {
    width: 100%;
    height: fit-content;

    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: auto auto;
}

.table__row {
    height: 8rem;

    /* border-top: 2px solid var(--font-color); */
    border-left: 2px solid var(--font-color);
    border-bottom: 2px solid var(--font-color);
    border-right: 2px solid var(--font-color);

    display: grid;
    grid-template-columns: repeat(3, 1fr) 2fr;
}

.table__row:first-child {
    border-top: 2px solid var(--font-color);
    /* border-bottom: 2px solid var(--font-color); */
}

.table__tile {
    border-right: 2px solid var(--font-color);

    display: grid;
    place-items: center;
}

.table__tile:last-child {
    border-right: none;
}

.table__title {
    /* border-bottom: none; */
    border-top-left-radius: 1rem;
    border-top-right-radius: 1rem;
}

.table__row:last-child {
    border-bottom-left-radius: 1rem;
    border-bottom-right-radius: 1rem;
}

.filter__box {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: repeat(3, auto);
    row-gap: 4rem;
}

.sort__cont {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: auto auto;
    row-gap: 2rem;
}

.sort__title {
    display: flex;
    justify-content: center;
}

.param__box {
    padding-left: 25%;
}

label {
    width: fit-content;
    margin-right: 0 auto;
}
</style>