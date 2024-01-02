<script>
export default {
    porps: {
        calcType: {
            type: Array,
            default: '',
        },
        numA: {
            type: Array,
            default: '',
        },
        numB: {
            type: Array,
            default: '',
        },
    },
    data() {
        return {
            type: this.calcType ?? [],
        }
    },
};
</script>

<template>
    <section id="myBtn">
        <!-- <button class="btn" type="button">
            <slot name="placeA" />
        </button>
        <div>
            <slot name="placeB" />
        </div>
        <div>
            {<slot name="result" />}
        </div> -->
        <button v-for="item in type" :key="item.id" class="btn" type="button">
            {{ item }}
        </button>
    </section>
</template>

<style></style>