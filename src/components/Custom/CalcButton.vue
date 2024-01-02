<script>
export default {
    
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