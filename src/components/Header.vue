<script>
import Button from './Button.vue'

export default {
    name: "Header",
    props: {
        title: {
            type: String,
            default: 'Default header value'
        },
        showAddTask: Boolean,
    },
    components: {
        Button,
    },
    emits: ['delete-task']
}
</script>

<template>
    <header>
        <h1>{{ title }}</h1>
        <Button 
        @btn-click="$emit('toggle-add-task')" 
        :text="showAddTask ? 'Close' : 'Add task'" 
        :color="showAddTask ? '#ff375f' : '#34c759 '" 
        />
    </header>
</template>

<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>