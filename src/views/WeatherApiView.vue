<script>
export default{
    data() {
        return{
            weatherData:[],
        }
    },
    mounted() {
        fetch('https://opendata.cwa.gov.tw/api/v1/rest/datastore/F-C0032-001?Authorization=CWA-326309B5-F15E-4530-99FC-C08A10B33A2A')
    },
}
</script>
<template>
    <div>

    </div>
</template>

<style>
</style>