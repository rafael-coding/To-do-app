<template>
     <div class="box has-text-weight-bold">
         <!-- slot = render content inside the component -->
         <slot> </slot>
     </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'BoxList',
}) 
</script>

<style scoped>
.box {
  background: #767676;
  color: #ffffff;
}
</style>