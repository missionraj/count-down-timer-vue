<template>
    <div>
        <div class="count">
            {{count}} 
        </div>
        <div class="tag"> <strong> {{ label }} </strong> </div>
    </div>
</template>

<script setup lang="ts">

const props = defineProps<{
  count: string
  label: string
}>()


</script>

<style scoped>
    .count { 
        font-size: 4rem;
        font-weight: 700;
        line-height: 1.6;
    }

</style>