<template>
    <div class="is-flex is-align-items-centeris-justify-content-space-between">
        <CronometroToDo :seconds="seconds"/>
        <button @click="startCount()" class="button" :disabled="timerTrack">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button @click="endCount()" class="button" :disabled="!timerTrack">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import CronometroToDo from './CronometroToDo.vue'

    export default defineComponent({
        name: 'TimerToDo',
        emits: ['finishTimeTracker'],
        components: { 
            CronometroToDo 
        },
        data(){
            return{
                seconds: 0,
                cronometro: 0,
                timerTrack: false
            }
        },

        methods: {
            startCount(){
                // 1 seg = 1000 ms
                this.cronometro = setInterval(() => {
                    // console.log('increment seconds')
                    this.seconds += 1
                }, 1000)
                // console.log('start')
                //enable stop
                this.timerTrack = true
            },

            endCount(){
                clearInterval(this.cronometro)
                // console.log('end')

                // disable stop
                this.timerTrack = false
                //call event finish time tracker
                this.$emit('finishTimeTracker', this.seconds)
                this.seconds = 0
            }
        }
    })
</script>