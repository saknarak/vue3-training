<template>
  <div>HEADER</div>
  <router-view />
  <div>FOOTER</div>
  <div id="dialog">
  </div>
</template>
<script>
export default {
  beforeRouteEnter(from, to, next) {
    let token = localStorage.getItem('token')
    if (!token) {
      return next('/signin')
    }

    // TODO: get profile

    next()
    ///
    // TODO: get user profile
  },
}
</script>
