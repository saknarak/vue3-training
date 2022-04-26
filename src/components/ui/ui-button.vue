<template>
  <button
    type="button"
    class="h-10 w-30 bg-blue-600 text-white rounded-md"
  >
    {{ text }}
  </button>
</template>
<script>
export default {
  props: {
    text: {
      type: String,
      default: 'Button Text',
      // required: false,
    },
  },
  data() {
    return {
      // text: 'TEST',
    }
  },
}
</script>
