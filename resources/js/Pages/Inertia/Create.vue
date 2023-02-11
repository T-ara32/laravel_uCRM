<script setup>
import { reactive } from "vue";
import { Inertia } from "@inertiajs/inertia"

defineProps({
  errors: Object
})

const form = reactive({
  title: null,
  contents: null
})

const submitFunction = () => {
  Inertia.post('/inertia', form)
}
</script>
<template>
  <form @submit.prevent="submitFunction">
    <input name="title" type="text" v-model="form.title"><br>
    <div v-if="errors.title">{{ errors.title }}</div>
    <input name="contents" type="text" v-model="form.contents"><br>
    <div v-if="errors.contents">{{ errors.contents }}</div>
    <button>送信</button>
  </form>
</template>
