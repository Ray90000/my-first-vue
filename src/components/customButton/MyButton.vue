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
        padding: 10px 20px;
        @apply border-black border-[3px] py-[5px] px-[10px] hover:bg-[red];
    }
}
</style>