<template>
  <div>HEADER</div>
  <router-view />
  <div>FOOTER</div>
  <div id="dialog">
  </div>
</template>
<script>
import axios from 'axios'
import { store } from '../store/store.js'

export default {
  async beforeRouteEnter(from, to, next) {
    let token = localStorage.getItem('token')
    if (!token) {
      return next('/signin')
    }
    // GET PROFILE
    let { data } = await axios.get('/api/profile', {
      headers: {
        Authorization: `Bearer ${token}`,
      },
    })
    if (!data.profile) {
      return next('/signin')
    }
    store.profile = data.profile
    next()
  },
}
</script>
