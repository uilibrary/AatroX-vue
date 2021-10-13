<script setup>
const props = defineProps({
    parentTitle: String,
    subParentTitle: String
})
</script>

<template>
    <div class="breadcrumb flex items-end border-b border-gray-300 pb-4 mb-6">
        <p class="text-xl mr-1 font-semibold mr-2 dark:text-white"> {{ props.parentTitle }} </p>
        <ul>
            <li class="border-r border-gray-400 inline pr-2 dark:text-gray-400"><a class="hover:text-gray-800" href=""> {{ props.parentTitle }}</a></li>
            <li class="inline pl-2 dark:text-gray-400"> {{ props.subParentTitle }}</li>
        </ul>
    </div>
</template>

