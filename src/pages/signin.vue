<template>
  <div>
    <form>
      <div>
        Sign-in busy={{ busy }}
      </div>
      <div>
        <label for="username">Username</label>
        <input type="text" id="username" v-model="username">
        {{ username }}
      </div>
      <div>
        <label for="password">Password</label>
        <input type="text" id="password" v-model="password">
        {{ password }}
      </div>
      <div>
        <input type="checkbox" id="remember" v-model="remember">
        <label for="remember">Remember username?</label>
        {{ remember }}
      </div>
      <div>
        <button type="button" :disabled="lock" @click="signin">
          Sign-In {{ lock }}
        </button>
        <button type="reset">
          Reset
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
      remember: false,
      ok: true,
      busy: false,
    }
  },

  computed: {
    lock() {
      return this.username === '' || this.password === ''
    },
  },

  // created() {
  //   console.log('created')
  //   let n = 1
  //   setInterval(() => {
  //     this.username = 'somsak' + n
  //     n++
  //     this.remember = !this.remember
  //     console.log('oooookkkkkkk')
  //   }, 1000)
  // },

  methods: {
    signin() {
      this.busy = true
      setTimeout(() => {
        this.busy = false
      }, 3000)
    },
  },
}
</script>
