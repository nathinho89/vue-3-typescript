<script setup lang="ts">
import {
    onMounted,
    ref 
} from 'vue'
import fetchCount from '../services/fetchCount'

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
        <button @click="incCount(2)">
            Inc.
        </button> 
    </div>
</template>