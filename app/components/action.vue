<template>
    <div class="py-4 w-max-300">
        <h4>{{ data.data.name }}</h4>
        <p class="outcome">{{ data.data.description }}</p>
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
.outcome {
    padding: 0px;
}

</style>