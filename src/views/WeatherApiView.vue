<script>
import WeatherCards from '@/components/custom/WeatherCards.vue';

export default{
    components:{
        WeatherCards,    
    },
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
        <WeatherCards />
    </div>
</template>

<style>
</style>