<template>
    <div class="box form-task">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário de criação de uma nova tarefa">
                <input 
                    type="text" 
                    class="input" 
                    placeholder="Qual tarefa deseja iniciar?"
                    v-model="description">
            </div>
            <div class="column">
                <timer-counter @if-timer-stopped="stopTask"></timer-counter>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TimerCounter from './TimerCounter.vue'

export default defineComponent({
    name: 'FormTask',
    components:{
        TimerCounter
    },
    emits: ['whenTaskSaved'],
    data(){
        return {
            description: ''
        }
    },
    methods:{
        stopTask(elapsedTime: number) : void {
            this.$emit('whenTaskSaved',{
                durationInSeconds: elapsedTime,
                description: this.description
            });
            this.description = '';
        }
    },
});
</script>

<style>
.form-task{
    color: var(--text-primary);
    background-color: var(--bg-primary);
}
</style>