<script>
export default {
    Array: ['+', '-', '*', '/'],
    data() {
        return {
            numA: 0,
            numB: 0,
            result: `
            <div>我是結果</div>`,
        };
    },
}
</script>

<template>
    <section id="myBtn">
        <button class="btn" type="button">
            <slot name="placeA" />
        </button>
        <div>
            <slot name="placeB" />
        </div>
        <div>
            {<slot name="result" />}
        </div>
    </section>
</template>

<style></style>