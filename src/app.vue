<template>
  <router-view />
  <div id="app-dialog">
  </div>
</template>
<script>
import { mapActions } from 'pinia'

export default {
  methods: {
    ...mapActions(store, ['saveStudent']),
    async doSaveStudent() {
      await this.saveStudent()
    },
  },
}
</script>
