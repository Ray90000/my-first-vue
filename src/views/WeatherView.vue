<script>
// import background from '@/assets/image/01.jpg';
import weatherCard from '@/components/customCard/WeatherCard.vue';
export default {
    components: {
        weatherCard,
    },
    data() {
        return {
            weatherData: [],
            list: [{ id: 1 }, { id: 2 }]
            // background,
        }
    },
    mounted() {
        const weatherApi = 'https://opendata.cwa.gov.tw/api/v1/rest/datastore/F-C0032-001?Authorization=CWA-D0593B54-0F6B-405E-85A3-B88FC368785E';
        fetch(weatherApi)
            .then(res => res.json())
            .then(data => {
                this.weatherData = data.records.location;
            })
            .catch(err => console.err('獲取天氣數據失敗', err))
    },
    methods: {
        logdata() {
            console.log(this.weatherData);
        },
    },
    // component() {

    // },
}
</script>
<template>
    <div class="flex flex-col ">
        <weatherCard v-for="item in weatherData" :key="item.id" :weather-place="item"></weatherCard>
    </div>
    
</template>
<style>
/* .weather {
    background-size: cover;
    background-position: center;
    width: 50vw;
} */
</style>
  