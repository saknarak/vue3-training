<template>
  <h1 class="bg-white text-black dark:(bg-black text-white)">
    WELCOME {{ store.profile?.displayName }}
  </h1>
  <div class="dark">
    <h1 class="bg-white text-black dark:(bg-black text-white)">
      WELCOME {{ store.profile?.displayName }}
    </h1>
  </div>
  <div class="flex flex-row flex-wrap">
    <div class="h-20 w-full sm:(w-1/2) lg:(w-1/3) rounded-lg bg-yellow-100"></div>
    <div class="h-20 w-full sm:(w-1/2) lg:(w-1/3) rounded-lg bg-blue-100"></div>
    <div class="h-20 w-full lg:(w-1/3) rounded-lg bg-red-100"></div>
  </div>
  <input type="text" required pattern="^[0-9]+$" class="my-input">
  <div class="text-red-500">
    TEXT: {{ text }}
  </div>
  <button class="btn">
    BUTTON1
  </button>
  <button class="btn">
    BUTTON2
  </button>
  <div>Last Login: {{ store.profile?.lastLogin }}</div>

  <!-- <div>{{ store }}</div> -->
</template>
<script>
import { store } from '../store/store.js'
export default {
  data() {
    return {
      store,
      text: '',
    }
  },
  created() {
    this.evtSource = new EventSource('/api/data')
    this.evtSource.onmessage = this.onEventMessage
  },
  beforeUnmount() {
    this.evtSource.close()
  },
  methods: {
    onEventMessage(evt) {
      console.log(evt.data)
      let obj = JSON.parse(evt.data)
      console.log(obj)
      this.text = obj.ts
    },
  },
}
</script>
<style>
.xxx {
  background-color: yellow;
}
.xxx:hover {
  border: 1px solid red;
}
.my-input {
  @apply p-1 bg-blue-400 invalid:(bg-red-300);
}
.btn {
  @apply py-2 px-4 font-semibold rounded-lg shadow-md bg-green-300;
  .text {
    @apply text-pink-200;
  }
}
</style>
