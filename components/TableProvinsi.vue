<template>
  <div>
    <div ref="prov" class="bg-gray-100">
      <div class="mx-auto max-w-5xl px-4 py-4 md:py-10 lg:py-16 flex flex-col space-y-4 md:space-y-8">
        <div class="flex flex-col">
          <p class="text-lg md:text-xl lg:text-2xl font-semibold text-gray-700">
            Kasus Covid-19 per Provinsi
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
                  Provinsi
                </td>
                <td class="font-medium py-2 px-4 border">
                  Total Kasus
                </td>
                <td class="font-medium py-2 px-4 border">
                  Sembuh
                </td>
                <td class="font-medium py-2 px-4 border">
                  Dirawat
                </td>
                <td class="font-medium py-2 px-4 border">
                  Meninggal
                </td>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(prov, index) in provs" :key="index">
                <td class="py-2 px-4 border">
                  {{ index + 1 }}
                </td>
                <td class="py-2 px-4 border">
                  {{ prov.key }}
                </td>
                <td class="py-2 px-4 border">
                  {{ prov.jumlah_kasus }}
                </td>
                <td class="py-2 px-4 border">
                  {{ prov.jumlah_sembuh }}
                </td>
                <td class="py-2 px-4 border">
                  {{ prov.jumlah_dirawat }}
                </td>
                <td class="py-2 px-4 border">
                  {{ prov.jumlah_meninggal }}
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      provs: null,
      vaks: null
    }
  },
  created () {
    this.getData()
  },
  methods: {
    async getData () {
      const data = await this.$axios.$get('/api/prov')
      this.provs = data.list_data
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
