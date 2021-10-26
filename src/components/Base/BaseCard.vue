<script setup>
const props = defineProps({
    noPadding: Boolean,
})
</script>
<template>
    <div class="card flex flex-col bg-white dark:bg-gray-800 dark:text-white">
        <slot name="cardHeader" />
        <div class="card-body" :class="props.noPadding ? 'noPadding' : ''">
            <slot />
        </div>
    </div>
</template>

<style lang="scss" scoped>
.card {
    border-radius: 10px;
    box-shadow: 0 4px 20px 1px rgb(0 0 0 / 6%), 0 1px 4px rgb(0 0 0 / 8%);
    // box-shadow:rgb(149 157 165 / 20%) 0px 8px 24px;

    .card-body {
        -webkit-box-flex: 1;
        -ms-flex: 1 1 auto;
        flex: 1 1 auto;
        padding: 1.25rem;
        &.noPadding {
            padding: 0 !important;
        }
    }
}
</style>
