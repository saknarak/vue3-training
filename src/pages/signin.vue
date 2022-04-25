<template>
  <div>
    <form>
      <div>
        Sign-in busy={{ busy }}
      </div>
      <div>
        <label for="username" class="text-red-500 ">Username</label>
        <input
          type="text" id="username" v-model="username" :disabled="busy"
          class="px-10 py-5 pl-0 text-pink-500 border-2 rounded-lg"
        >
        {{ username }}
      </div>
      <div>
        <label for="password">Password</label>
        <input type="text" id="password" v-model="password" :disabled="busy">
        {{ password }}
      </div>
      <div>
        <input type="checkbox" id="remember" v-model="remember" :disabled="busy">
        <label for="remember">Remember username?</label>
        {{ remember }}
      </div>
      <div>
        <button type="button" :disabled="lock || busy" @click="signin">
          Sign-In {{ lock }}
        </button>
        <button type="reset" :disabled="busy">
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
      // console.log('xxx')
      this.busy = true
      setTimeout(() => {
        this.busy = false
      }, 3000)
    },
  },
}
</script>
