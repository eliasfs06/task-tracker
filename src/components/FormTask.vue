<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">{{ task.description || 'Task' }}</div>
            <div class="column">
                <FormTracker :timeInSeconds="task.total"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import ITasks from '@/interfaces/ITasks';
import { defineComponent, PropType } from 'vue';
import FormTracker from './FormTracker.vue';

export default defineComponent({
    name: 'FormTask',
    components: {
    FormTracker
    },
    props: {
        task: {
            type: Object as PropType<ITasks>,
            required: true
        }
    }
})
</script>

<style scoped>
    .box {
        background: #91c2b2;
        color: black;
        border-radius: 10px !important;
    }
</style>
