<template>
  <div class="rounded-lg shadow-gray-400 shadow-md bg-white">
    <div class="px-3 h-10 leading-10 bg-blue-900 text-white rounded-t-md text-xl">
      <slot name="title">
        TITLE
      </slot>
    </div>
    <div>
      <slot></slot>
    </div>
    <div class="p-3 flex gap-3 justify-center">
      <slot name="actions">
        ACTIONS
      </slot>
    </div>
  </div>
</template>
