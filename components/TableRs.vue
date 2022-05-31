<template>
  <div>
    <div ref="rs" class="mx-auto max-w-5xl px-4 py-4 md:py-10 lg:py-16 mb-4 md:mb-10 flex flex-col space-y-4 md:space-y-8">
      <div class="flex flex-col">
        <p class="text-lg md:text-xl lg:text-2xl font-semibold text-gray-700">
          Daftar Rumah Sakit rujukan Covid-19 di Indonesia
        </p>
      </div>
      <div class="bg-white rounded-md shadow h-96 overflow-auto">
        <table class="border w-full">
          <thead class="bg-red-200 sticky top-0">
            <tr>
              <td class="font-medium py-2 px-4 border">
                No
              </td>
              <td class="font-medium py-2 px-4 border">
                Wilayah
              </td>
              <td class="font-medium py-2 px-4 border">
                Nama Rumah Sakit
              </td>
              <td class="font-medium py-2 px-4 border">
                Tipe
              </td>
              <td class="font-medium py-2 px-4 border">
                Alamat
              </td>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(rs, index) in hospital" :key="index">
              <td class="py-2 px-4 border">
                {{ index + 1 }}
              </td>
              <td class="py-2 px-4 border">
                {{ rs.wilayah }}
              </td>
              <td class="py-2 px-4 border">
                {{ rs.nama }}
              </td>
              <td class="py-2 px-4 border">
                {{ rs.tipe }}
              </td>
              <td class="py-2 px-4 border">
                {{ rs.alamat }}
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      hospital: null
    }
  },
  created () {
    this.getData()
  },
  methods: {
    async getData () {
      const data = await this.$axios.$get('/api/rs')
      this.hospital = data
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
