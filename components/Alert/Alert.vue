<template>
  <div
    class="border  text-sm rounded-lg p-4"
    :class="[colorClasses]"
    role="alert"
  >
    <div class="flex">
      <div class="ms-4">
        <h3 class="text-sm font-semibold">
          {{ title }}
        </h3>
        <div
          v-if="$slots.default"
          :class="[bodyClasses]"
        >
          <slot />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    icon: {
      type: Boolean,
      default: true,
    },
    type: {
      type: String,
      default: 'info',
    },
  },
  computed: {
    colorClasses() {
      switch (this.type) {
        case 'info':
          return 'bg-blue-50 border-blue-200 text-blue-800  dark:bg-blue-800/10 dark:border-blue-900 dark:text-blue-500'
        case 'error':
          return 'bg-red-50 border-red-200 text-red-800  dark:bg-red-800/10 dark:border-red-900 dark:text-red-500'
        default:
          return ''
      }
    },
    bodyClasses() {
      switch (this.color) {
        case 'info':
          return 'mt-2 text-sm text-blue-700 dark:text-blue-400'
        case 'error':
          return 'mt-2 text-sm text-red-700 dark:text-red-400'
        default:
          return ''
      }
    },
  },

}
</script>
