<script setup>
import { reactive, computed, watch } from 'vue'

const profile = reactive({
    firstName: '',
    lastName: '',
    age: 18
})

const fullName = computed(() => {
    const fn = profile.firstName.trim()
    const ln = profile.lastName.trim()
    return (fn || ln) ? `${fn} ${ln}`.trim() : '-'
})

watch(() => profile.age, (newValue, oldValue) => {
    console.log(`Возраст: ${oldValue} -> ${newValue}`)
})
</script>

<template>
 <div>
    <h2>Профиль (reactive)</h2>
    
    <label>
        Имя:
        <input v-model="profile.firstName" placeholder="Иван" />
    </label>
    
    <label>
        Фамилия:
        <input v-model="profile.lastName" placeholder="Иванов" />
    </label>
    
    <label>
        Возраст:
        <input type="number" v-model.number="profile.age" min="0" />
    </label>
    
    <p>Полное имя: <strong>{{ fullName }}</strong></p>
    <pre>JSON: {{ profile }}</pre>
 </div>
</template>