<script>
export default {

};
</script>

<template>
    <section id="myBtn">
        <button class="btn" type="button">
            <slot />
        </button>
    </section>
</template>

<style scoped lang="scss">
#myBtn {
    .btn {
        @apply w-16 h-16 bg-orange-400 text-white rounded-full  hover:bg-orange-300;
    }
}
</style>