<template>
  <div>
    <div class="inline fixed bottom-0 my-2 md:my-4 lg:my-6 right-0 mx-2 md:mx-4 lg:mx-6" :class="{ 'hidden' : invisible }">
      <button type="button" class="bg-red-400 w-4 h-4 md:w-8 md:h-8 flex items-center p-2 rounded-full justify-center" @click="$emit('scrollToTop')">
        <font-awesome-icon icon="arrow-up" class="text-white" />
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    invisible: {
      type: Boolean,
      default: true
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
