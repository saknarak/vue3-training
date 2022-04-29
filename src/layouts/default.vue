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
    axios.defaults.headers.common.Authorization = `Bearer ${token}`
    // axios.defaults.headers.common['X-Powered-By'] = 'Somsak'

    let { data } = await axios.get('/api/profile')
    if (!data.profile) {
      return next('/signin')
    }
    store.profile = data.profile
    next()
  },

  created() {
    this.tokenTimer = setInterval(async () => {
      let token = localStorage.getItem('token')
      let newToken = await axios.post('/api/auth/token')
      if (newToken && newToken !== token) {
        localStorage.setItem('token', newToken)
        axios.defaults.headers.common.Authorization = `Bearer ${newToken}`
      }
    }, 5 * 60 * 1000)
  },
  beforeUnmount() {
    clearInterval(this.tokenTimer)
  },
}
</script>
