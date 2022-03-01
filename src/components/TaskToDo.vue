<template>
    <BoxList>
        <div class="columns">
            <div class="column is-7">
                {{task.description  || "task without description"}}
            </div>
            <div class="column">
                <CronometroToDo :seconds="task.durationInSeconds"/>
            </div>
        </div>
    </BoxList>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import CronometroToDo from './CronometroToDo.vue'
import ITask from '../interfaces/ITask.js'
import BoxList from './BoxList.vue'

export default defineComponent({
    name: 'TaskToDo',

    components: { 
      CronometroToDo,
      BoxList 
    },

    props: {
        task: {
            type: Object as PropType<ITask>,
            required: true
        }
    }
})
</script>

<style scoped>
.box{
    background: #7a7a7a;
}

.box .column{
    color: #ffffff !important;
}

.column .is-flex .time-box .timer {
    color: #ffffff !important;
}
</style>
