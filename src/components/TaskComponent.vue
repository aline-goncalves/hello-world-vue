<template>
    <box-component>
        <div class="columns">
            <div class="column is-7">
                {{ task.description || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <timer-component :timeInSeconds="task.durationInSeconds"></timer-component>
            </div>
        </div>
    </box-component>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import TimerComponent from './TimerComponent.vue';
import BoxComponent from './BoxComponent.vue';
import TaskInterface from '@/interfaces/TaskInterface';

export default defineComponent({
    name: 'TaskComponent',
    components: {
        TimerComponent,
        BoxComponent
    },
    props: {
        task:{
            type: Object as PropType<TaskInterface>,
            required: true
        }
    }
})
</script>