<script setup>
import { Link } from '@inertiajs/vue3';
import { ref } from 'vue'

const newTitle = ref('')
const newContents = ref('')
</script>

<template>
  Inertiaテスト<br>
  <a href="/">aタグ経由</a><br>
  <Link href="/">Link経由です</Link><br>
  <Link :href="route('inertia.index')">名前付きルートの確認です</Link><br>
  <Link :href="route('inertia.show', { id: 1 })">ルートパラメータのテストです</Link>

  <div class="mb-8">
    <input type="text" name="newTitle" v-model="newTitle">{{ newTitle }}<br>
    <input type="text" name="newContents" v-model="newContents">{{ newContents }}<br>
    <Link as="button" method="post" :href="route('inertia.store')"
    :data="{
      title: newTitle,
      content: newContents
    }">DB保存テスト</Link>
  </div>
</template>
