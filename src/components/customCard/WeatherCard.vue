<script>
export default {
    props: {
        weatherPlace: {
            type: Object,
        }
    }
};
</script>
<template>
    <div>
        <div class="w-full">
            <img src="" alt="">
        </div>
        <div class="p-5">
            區域:<span>{{ weatherPlace.locationName }}</span>
            氣溫:<span>{{ weatherPlace.weatherElement[2].time[0].parameter.parameterName }}C</span>
            體感: <span>{{ weatherPlace.weatherElement[3].time[0].parameter.parameterName }}</span>
            天氣: <span>{{  weatherPlace.weatherElement[0].time[0].parameter.parameterName }}</span>
        </div>
    </div>
</template>
<style></style>