<template>
    <div class="box form">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Form for new task">
                <input type="text" class="input" placeholder="Which task do you want to start?" v-model="description">
            </div>
            <div class="column">
                <TimeTracker @whenTimeTrackerFinish="endTask" />
            </div>
        </div>
    </div>
</template>


<script lang="ts">
import { defineComponent } from 'vue';
import TimeTracker from './TimeTracker.vue'

export default defineComponent({
    name: 'AppForm',
    emits: ['whenSaveTask'],
    data () {
        return {
            description: ''
        }
    },
    components: {
        TimeTracker
    },
    methods: {
        endTask(totalTime: number) : void {
            this.$emit('whenSaveTask', {
                total: totalTime,
                description: this.description
            } )
            this.description = ''
        }
    }
});
</script>

<style>
    .form{
        background-color: var(--bg-primario);
        color: var(--texto-primario);
    }

    .box {
        border-radius: 0px !important;
    }
</style>