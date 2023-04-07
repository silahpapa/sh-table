<script setup lang="ts">
import {computed, onMounted, reactive, ref} from 'vue'
import {doGet} from 's-apis'
import {showToast,confirmRequest} from 's-alert'
defineProps<{ msg: string }>()

let posts = ref([])

onMounted(async () => {
  const response = await doGet('https://jsonplaceholder.typicode.com/posts')
  posts.value = response.data
  showToast('testing','success','top-start',3000)
  confirmRequest('testing','are you sure kapss','Red alder',[{user_id:23}])
})

</script>
<template>
  <div class="container">
    <div class="row">
      <table class="table table-bordered">
        <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">title</th>
          <th scope="col">Body</th>
          <th scope="col">Action</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="post in posts" :key="post.id">
          <th scope="row">{{post.id}}</th>
          <td>{{post.title}}</td>
          <td>{{post.body}}</td>
          <td>edit</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style scoped>
</style>
