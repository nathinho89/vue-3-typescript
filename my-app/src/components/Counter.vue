<script setup lang="ts">
import {
    onMounted,
    ref 
} from 'vue'
import fetchCount from '../services/fetchCount'
import ControlBtn from './ControlBtn.vue'

interface CountProps {
    limit: number;
    alertMessageOnLimit?: string;
}

const props = withDefaults(defineProps<CountProps>(), {
    alertMessageOnLimit: 'Count limit reached'
})

const count = ref<number | null>(null)

onMounted(() => {
  fetchCount((initialCount) => {
    count.value = initialCount;
  })
})

function incCount(inc: number) {
  if(count.value !== null) {
    if (count.value >= props.limit) {
        alert(props.alertMessageOnLimit)
    } else {
        count.value += inc
    }
  }
}
</script>

<template>
    <div>
        <p>{{ count }}</p>
        <ControlBtn 
          @inc-count="incCount"
          @reset-count="count = 0"/>
    </div>
</template>
