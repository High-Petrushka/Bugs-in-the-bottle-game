<script setup>
const props = defineProps({
    resultList: Array,
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
                        <div 
                        v-for="(item) in props.resultList"
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
                    </div>
                </div>
                <div class="filter__box"></div>
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
    border-bottom: 2px solid var(--font-color);
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
    border-bottom: none;
    border-top-left-radius: 1rem;
    border-top-right-radius: 1rem;
}

.table__row:last-child {
    border-bottom-left-radius: 1rem;
    border-bottom-right-radius: 1rem;
}
</style>