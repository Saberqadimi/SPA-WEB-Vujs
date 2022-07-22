<template>
  <div class="container mt-5">
    <div class="row">
    
        <div v-if="loading" class="spinner-border text-primary" role="status">
          <span class="visually-hidden">Loading...</span>
        </div>
      <div v-else class="col-md-4 g-3" v-for="user in users" :key="user.id">
        <UserCardView :user="user" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import { ref } from 'vue'
import UserCardView from '@/components/users/CardView.vue'
export default {
  name: 'UserIndex',

  components: { UserCardView },
  setup() {
    const users = ref([])
    const loading = ref(true)

    function getUsers() {
      axios
        .get('https://jsonplaceholder.typicode.com/users')
        .then(function (response) {
          // handle success
          users.value = response.data
          loading.value = false
        })
        .catch(function (error) {
          // handle error
          console.log(error)
        })
    }

    getUsers()

    return { users }
  },
}
</script>

<style></style>
