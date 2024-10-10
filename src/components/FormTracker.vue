<template>
    <section>
        <strong class="tracker">{{ totalTime }}</strong>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'FormTracker',
    props: {
        timeInSeconds: {
            type: Number,
            default: 0
        }
    },
    computed: {
        totalTime () : string {
            return new Date(this.timeInSeconds * 1000).toISOString().substr(11,8);
        }
    }
})
</script>
<style scoped>
    .tracker {
        color: black;
        background-color: #ffffff;
        border-radius: 10px;
        padding: 5px;
    }
</style>