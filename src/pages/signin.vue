<route lang="yaml">
meta:
  layout: public
</route>

<template>
  <div class="flex flex-col gap-4 justify-center items-center min-h-screen">
    <div class="w-20 h-20 bg-pink-300 flex justify-center items-center rounded-md">
      LOGO
    </div>
    <signin-box
      v-model:form="form"
      @success="signinSuccess"
      @error="singinError"
    >
    </signin-box>
    <div>FOOTER {{ isValid }}</div>
  </div>

  <div v-if="busy" class="fixed top-0 bottom-0 left-0 right-0 opacity-80 bg-gray-400">
    Please wait...
  </div>
</template>

<script-backup>
import { reactive, computed } from 'vue'

export default {
  props: {

  },
  setup() {
    const form = reactive({
      username: 'somchai',
      password: '',
      remember: false,
    })
    const isValid = computed(() => form.username !== '' &&
        form.password !== '')
    const signinSuccess = function(user) {
      console.log('user=', user)
      console.log(form.username)
    }
    const singinError = function(err) {
      console.log('err=', err)
      // TODO:
    }
    return {
      disabled: {
        type: Boolean,
      },
      form,
      isValid,
      signinSuccess,
      singinError,
    }
  },
  data() {
    return {
      a: 1,
      b: 2,
    }
  }
}
</script-backup>

<script setup>
import { ref, defineProps, reactive, computed } from 'vue'

// syntax sugar
defineProps({
  disabled: {
    type: Boolean,
    default: true,
  },
})

const busy = ref(false)

const form = reactive({
  username: 'somchai',
  password: '',
  remember: false,
})

const isValid = computed(() => form.username !== '' &&
        form.password !== '')

const signinSuccess = function(user) {
  console.log('user=', user)
  console.log(form.username)
}
const singinError = function(err) {
  console.log('err=', err)
  // TODO:
}
</script>
