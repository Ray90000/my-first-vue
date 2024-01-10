<script>
// import background from '@/assets/image/01.jpg';
import weatherCard from '@/components/customCard/WeatherCard.vue';
import weatherSlot from '@/components/customCard/WeatherSlot.vue';
export default {
    components: {
        weatherCard,
        weatherSlot,
    },
    data() {
        return {
            weatherData: [],
            //地區
            place: [
                {
                    id: 'all',
                    place: '全部'
                },
                {
                    id: 1,
                    place: '北部'
                },
                {
                    id: 2,
                    place: '中部'
                },
                {
                    id: 3,
                    place: '南部'
                },
                {
                    id: 4,
                    place: '東部'
                },
                {
                    id: 5,
                    place: '離島'
                },
            ],
            checkPlace: 'all',
            north: ['臺北市', '新北市', '基隆市', '桃園市', '新竹縣', '新竹市', '宜蘭縣'],
            mid: ['苗栗縣', '台中市', '彰化縣', '南投縣', '雲林縣'],
            south: ['嘉義市', '嘉義縣', '臺南市', '高雄市', '屏東縣', '澎湖縣'],
            east: ['花蓮縣', '臺東縣'],
            outside: ['金門縣', '連江縣']
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
    /*與methods相近，但是他可以欲處理你的資料，並且她有站存的功能，利用這個特點可以做所謂的分業功能
    因為我們是拿整包到這個頁面來，所以為了要做分業部分，我們無用在去重新拿取資料。
    在computed裡面要寫function但是不能帶數值近來，並且每個function一定要有return。
    */
    computed: {
        checkData() {
            return this.weatherData.filter((item) => {
                if (this.checkPlace === 'all') {
                    return true;
                } else if (this.checkPlace === 1) {
                    return this.north.includes(item.locationName);
                }else if (this.checkPlace === 2){
                    return this.mid.includes(item.locationName);
                }else if (this.checkPlace === 3){
                    return this.south.includes(item.locationName);
                }else if (this.checkPlace === 4){
                    return this.south.includes(item.locationName);
                }else if (this.checkPlace === 5){
                    return this.outside.includes(item.locationName);
                }
            })
        },
    },
    methods: {
    },
}
</script>
<template>
    <div>
        <weatherSlot v-for="item in place" :key="item.id" @click="checkPlace = item.id"
            :class="{ 'bg-orange-600 text-white': checkPlace == item.id }">
            {{ item.place }}
        </weatherSlot>
    </div>
    <div class="flex flex-col ">
        <weatherCard v-for="item in checkData" :key="item.id" :weather-place="item"></weatherCard>
    </div>
</template>
<style>
/* .weather {
    background-size: cover;
    background-position: center;
    width: 50vw;
} */
</style>
  