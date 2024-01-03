<script>
export default {

};
</script>

<template>
    <section id="numBtn">
        <button class="num" type="button">
            <slot />
        </button>
    </section>
</template>

<style scoped lang="scss">
#myBtn {
    .num {
        @apply w-16 h-16 bg-orange-400 text-white rounded-full  hover:bg-[red];
    }
}
</style>