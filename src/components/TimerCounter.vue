<template>
    <section class="is-flex is-align-items-center is-justify-content-space-between">
        <timer-component :time-in-seconds="timeInSeconds"></timer-component>
        <base-button 
            buttonIcon="fas fa-play" 
            @wasClicked="start" 
            buttonName="play" 
            :wasDesabled="timerRunning">
        ></base-button>
        <base-button 
            buttonIcon="fas fa-stop" 
            @wasClicked="stop" 
            buttonName="stop" 
            :wasDesabled="!timerRunning">
        ></base-button>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import BaseButton from './BaseButton.vue';
import TimerComponent from './TimerComponent.vue';

export default defineComponent({
    name: 'TimerCounter',
    emits: ['ifTimerStopped'],
    components: { TimerComponent, BaseButton },
    data() {
        return {
            timeInSeconds: 0,
            timer: 0,
            timerRunning: false
        }
    },
    methods: {
        start() {
            console.log('starting');
            this.timerRunning = true;
            this.timer = setInterval(() => {
                this.timeInSeconds += 1;
            }, 1000);
        },
        stop() {
            console.log('stopping');
            this.timerRunning = false;
            clearInterval(this.timer);
            this.$emit('ifTimerStopped', this.timeInSeconds);
            this.timeInSeconds = 0;
        }
    },
})
</script>