<script>
import sun from '@/assets/image/sunny.gif'
import cloud from '@/assets/image/sunny-could.gif'
import rain from '@/assets/image/rain.gif'
import thunder from '@/assets/image/thunder.gif'
export default {
    props: {
        weatherPlace: {
            type: Object,
        }
    },
    methods:{
        weatherImage(item){
            //轉數字
            const temperature = parseInt(item);
            let imageUrl = '';
            if(temperature <= 20){
                imageUrl = sun;
            }else if(temperature <= 60){
                imageUrl = cloud;
            }else if(temperature <= 70){
                imageUrl = rain;
            }else if(temperature <= 90){
                imageUrl = thunder;
            }
            return imageUrl
        },
    
    },
};
</script>
<template>
    <div>
        <div class="w-full">
            <img class="w-full h-[300px]" :src="weatherImage(weatherPlace.weatherElement[1].time[0].parameter.parameterName)" alt="">
        </div>
        <div class="p-5 w-[100%]">
            區域:<span>{{ weatherPlace.locationName }}</span>
            氣溫:<span>{{ weatherPlace.weatherElement[2].time[0].parameter.parameterName }}C</span>
            體感: <span>{{ weatherPlace.weatherElement[3].time[0].parameter.parameterName }}</span>
            天氣: <span>{{  weatherPlace.weatherElement[0].time[0].parameter.parameterName }}</span>
        </div>
    </div>
</template>
<style></style>