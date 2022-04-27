<template>
  <select v-model="lang" @change="setLang">
    <option value="th">
      ไทย
    </option>
    <option value="en">
      English
    </option>
  </select>
</template>
<script>
export default {
  data() {
    let language = localStorage.getItem('lang') || 'th'
    return {
      lang: language,
    }
  },
  methods: {
    setLang() {
      console.log('lang=', this.lang)
      localStorage.setItem('lang', this.lang)
    },
  },
}
</script>
