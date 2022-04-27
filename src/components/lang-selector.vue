<template>
  <select v-model="store.lang">
    <option value="th">
      ไทย
    </option>
    <option value="en">
      English
    </option>
  </select>
</template>
<script>
// tree shaking
import { store } from '../store/store.js'

export default {
  data() {
    return {
      store,
    }
  },
}
</script>
