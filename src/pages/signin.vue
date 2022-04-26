<template>
  <div class="flex flex-col gap-4 justify-center items-center min-h-screen">
    <div class="w-20 h-20 bg-pink-300 flex justify-center items-center rounded-md">
      LOGO
    </div>
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
