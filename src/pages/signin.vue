<template>
  <div class="flex justify-center items-center min-h-screen">
    <signin-box
      @success="signinSuccess"
      @error="singinError"
    ></signin-box>
  </div>

  <div v-if="busy" class="fixed top-0 bottom-0 left-0 right-0 opacity-80 bg-gray-400">
    Please wait...
  </div>
</template>

<script>
export default {
  methods: {
    signinSuccess(user) {
      console.log('user=', user)
    },
    singinError(err) {
      console.log('err=', err)
      // TODO:
    },
  },

}

</script>
