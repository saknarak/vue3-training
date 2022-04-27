<template>
  <ui-card>
    <form class="pt-3">
      <div class="flex flex-col px-3">
        <label for="username" class="h-8 leading-8">Username {{ lang }}</label>
        <input
          ref="username"
          type="text" id="username"
          :value="form.username"
          @input="$emit('update:form', { ...form, username: $event.target.value })"
          :disabled="busy"
          class="border-2 rounded-md h-10 px-2"
          @keyup.enter.ctrl="onUsernameKeyup"
        >
      </div>
      <div class="flex flex-col px-3">
        <label for="password" class="h-8 leading-8">Password {{ lock }}</label>
        <input
          ref="password"
          type="password" id="password" v-model="password" :disabled="busy"
          class="border-2 rounded-md h-10 px-2"
        >
      </div>
      <div class="flex flex-col px-3">
        <label for="password" class="h-8 leading-8">Type</label>
        <select
          v-model="type"
          class="border-2 rounded-md h-10 px-2"
        >
          <option
            v-for="({ value, text }, idx) in filteredTypeList"
            :key="value"
            :value="value"
          >
            {{ text }} {{ idx }}
          </option>
        </select>
      </div>
      <!-- <template v-for="n in 5" :key="n">
          <div>AAA</div>
          <div>BBB</div>
        </template> -->
      <!-- <div class="flex flex-col px-3">
          <label for="password" class="h-8 leading-8">Type</label>
          <select>
            <option
              v-for="(type2, code) in type2List"
              :key="code"
              :value="code"
            >
              {{ type2 }}
            </option>
          </select>
        </div> -->
      <div class="px-3 h-10 flex items-center gap-2">
        <input type="checkbox" id="remember" v-model="remember" :disabled="busy" class="w-5 h-5">
        <label for="remember">Remember username?</label>
      </div>
    </form>

    <template #title>
      Sign-in
    </template>
    <template #actions>
      <ui-button
        ref="signin"
        :disabled="lock || busy"
        @click="signin"
      >
        Sign-In
        <template #icon>
          <img src="../assets/logo.png" class="w-6 h-6">
        </template>
      </ui-button>
      <ui-button
        type="reset" :disabled="busy"
        class="border-red-600 bg-white text-black border-2 rounded-md"
        icon="clear"
      >
        <template #icon>
          <img src="../assets/logo.png" class="w-6 h-6">
        </template>
        Reset
      </ui-button>
    </template>
  </ui-card>
</template>

<script>
// import { store } from '../store/store.js'
import { mapState } from 'pinia'
import { useAppStore } from '../store/app-store'
export default {
  props: {
    form: {
      type: Object,
      default() {
        return {
          username: '',
          password: '',
          remember: false,
        }
      },
    },
  },
  emits: [
    'success',
    'error',
    'update:form',
  ],
  data() {
    return {
      // store,
      password: '',
      remember: false,
      ok: true,
      busy: false,
      type: 'S',
      typeList: [
        { value: 'S', text: 'Student' },
        { value: 'T', text: 'Teacher' },
        { value: 'P', text: 'Parent' },
      ],
      type2List: {
        S: 'Student',
        T: 'Teacher',
        P: 'Parent',
      },
    }
  },

  computed: {
    ...mapState(useAppStore, ['lang']),
    lock() {
      return !this.username || !this.password
    },
    filteredTypeList() {
      return this.typeList.filter(x => x.value !== 'P')
    },
  },

  created() {
    // console.log('created')
    // let n = 1
    // clearInterval(this.timer)
    // this.timer = setInterval(() => {
    //   console.log('oooookkkkkkk', n)
    // }, 1000)
  },
  mounted() {
    // document.getElementById('username').focus()
    this.$refs.username.focus()
  },
  beforeUnmount() {
    // clearInterval(this.timer)
  },

  methods: {
    signin() {
      // console.log('xxx')
      this.busy = true
      this.$emit('checking')
      setTimeout(() => {
        this.busy = false
        if (this.username === 'x') {
          this.$emit('error', {})
        } else {
          this.$emit('success', { id: 5, name: 'Somsak', username: this.username})
        }
      }, 3000)
    },
    onUsernameKeyup(evt) {
      // console.log('xxxx')
      // if (evt.code === 'Enter') {
      this.$refs.password.focus()
      // }
    },
  },
}
</script>
