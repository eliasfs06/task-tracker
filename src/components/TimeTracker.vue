<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <FormTracker :timeInSeconds="timeInSeconds" />
        <button class="button" @click="start" :disabled="trakcerIsRunning">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="end" :disabled="!trakcerIsRunning">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
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
