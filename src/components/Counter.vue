<script setup>
import { ref, watch } from 'vue'

const count = ref(0)

function inc() {
    count.value = count.value + 1
}

watch(count, (newVal, oldVal) => {
    console.log(`count изменился: ${oldVal} -> ${newVal}`)
})
</script>

<template>
    <div>
        <h2>Счетчик (ref)</h2>
        <p>Текущее значение:<strong>{{ count }}</strong></p>
        <button @click="inc">Увеличить на +1</button>
    </div>
</template>