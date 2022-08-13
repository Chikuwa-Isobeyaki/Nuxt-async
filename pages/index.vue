<template>
  <section class="container">
      <!-- {{ users[0].id }}, {{ users[0].name }} -->
      <ul>
        <!-- データを追跡しやすいようにv-for:keyを設定。公式の方でも指定を推奨されている -->
        <li v-for="user in users" :key="user.id">
          {{ user.id }}, {{ user.name }}
        </li>
      </ul>
  </section>
</template>


<script>
const axios = require('axios')
let url = "https://jsonplaceholder.typicode.com/users"
export default {
  asyncData({ params }) {
    return axios.get(url)
      .then((res)=> {
        return { users: res.data }
      })
  }
}
</script>
