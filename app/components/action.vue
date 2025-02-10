<template>
    <div>
        <h4>{{ data.data.name }}</h4>
        <p>{{ data.data.description }}</p>
        <span v-for="outcome in data.data.outcomes">
            <p>{{ outcome.text }}</p>
        </span>
    </div>
</template>

<script>
    export default {
        props: {
            data: {
                type: Object,
            }
        },
    }
</script>

<style scoped>

</style>