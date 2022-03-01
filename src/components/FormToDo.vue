<template>
    <div class="box">
        <div class="columns">
            <div 
            class="column is-8" 
            role="form" 
            aria-label="Formulário para criação de uma nova tarefa">
                <input 
                type="text" 
                class="input"
                placeholder="start a task"
                v-model="description">
            </div>
            <div class="column">
                <TimerToDo @finishTimeTracker="timeFinish"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TimerToDo from './TimerToDo.vue'

    export default defineComponent({
        name: 'FormToDo',
        emits: ['whenSavingTask'],

        components: { 
            TimerToDo 
        },

        data(){
            return{
                // binding input task 
                description: '',
            }
        },

        methods: {
            timeFinish (isOver: number) : void {
                // getting time passed by @finishTimeTracker
                console.log('time', isOver)
                // getting binding input task 
                console.log('task description', this.description)

                this.$emit('whenSavingTask', {
                    durationInSeconds: isOver,
                    description: this.description
                })

                this.description = ''
            } 
        }
    })
</script>