<template>
    <a 
    class="button"
    @click="$emit('click')"
    >
        {{ text }}
    </a>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: {
            type: String,
            default: ''
        }
    }
}
</script>

<style scoped>
</style>