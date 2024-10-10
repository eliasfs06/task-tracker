<template>
    <div class="is-flex is-align-items-center">
        <FormTracker :timeInSeconds="timeInSeconds" />
        <div class="button-container">
            <button class="button" @click="start" :disabled="trakcerIsRunning">
                <span>play</span>
            </button>
            <button class="button" @click="end" :disabled="!trakcerIsRunning">
                <span>stop</span>
            </button>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import FormTracker from './FormTracker.vue'

export default defineComponent({
    name: 'TimeTracker',
    emits: ['whenTimeTrackerFinish'],
    components: {
        FormTracker
    },
    data () {
        return {
            timeInSeconds: 0,
            tracker: 0,
            trakcerIsRunning : false
        }
    },
    methods: {
        start () {
            this.tracker = setInterval(() => {
                this.timeInSeconds += 1;
            }, 1000)
            this.trakcerIsRunning = true
        },
        end () {
            clearInterval(this.tracker)
            this.trakcerIsRunning = false;
            this.$emit('whenTimeTrackerFinish', this.timeInSeconds)
            this.timeInSeconds = 0
        }
    }
});
</script>

<style>
    .button-container{
       margin-left: 25px; 
    }
</style>