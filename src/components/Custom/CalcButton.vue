<script>
export default {
    props: {
        calcType: {
            type: Array,
        },
        numA: {
            type: Number,
        },
        numB: {
            type: Number,
        },
    },
    emit:['finalMath'],
    data() {
        return {
            type: this.calcType ?? [],
            result: 0,
        }
    },
    methods: {
        enterCalc(type) {
            if (this.numA.toString().trim() === '' || this.numB.toString().trim() === '') return;
            switch (type) {
                case '+':
                    this.result = this.numA + this.numB;
                    break;
                case '-':
                    this.result = this.numA - this.numB;
                    break;
                case '*':
                    this.result = this.numA * this.numB;
                    break;
                case '/':
                    this.result = this.numA / this.numB;
                    break;
            }
            this.$emit('finalMath',this.result);
        },
    }
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
        <button v-for="item in calcType" :key="item.id" class="btn" type="button" @click="enterCalc(item)">
            {{ item }}
        </button>
    </section>
</template>

<style></style>