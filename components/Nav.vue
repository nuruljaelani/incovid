<template>
  <div>
    <div class="bg-white shadow-xl drop-shadow-md">
      <nav class="mx-auto px-0 md:px-4 max-w-5xl py-4 flex items-center justify-between">
        <p class="text-2xl text-emerald-500 font-bold">
          Inco
        </p>
        <div class="flex space-x-4 lg:space-x-8">
          <button type="button" @click="$emit('scrollToJabar')">
            Kumulatif Jabar & Nasional
          </button>
          <button type="button" @click="$emit('scrollToProv')">
            Data Per Provinsi
          </button>
          <button type="button" @click="$emit('scrollToRs')">
            Data Rumah Sakit
          </button>
        </div>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NavComp'
}
</script>

<style lang="scss" scoped>

</style>
