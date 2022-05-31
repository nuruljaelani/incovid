<template>
  <div>
    <div ref="jabar" class="flex flex-col mx-auto max-w-5xl px-0 md:px-4 py-4 md:py-10 lg:py-16 space-y-4 md:space-y-6 lg:space-y-10">
      <div class="flex flex-col">
        <p class="text-lg md:text-xl lg:text-2xl font-semibold text-gray-700">
          Informasi kasus terkini Covid-19 di Jawa Barat & Nasional
        </p>
        <p class="text-base text-gray-600">
          Update Terakhir {{ last_date }}
        </p>
      </div>
      <div class="grid grid-cols-4 gap-4 md:gap-6 lg:gap-8">
        <div class="bg-blue-300 rounded drop-shadow-md flex flex-col p-4 space-y-4">
          <p class="text-white font-medium text-base lg:text-lg">
            Total terkonfirmasi
          </p>
          <div class="flex flex-col">
            <p class="text-gray-800 font-medium">
              Jawa Barat
            </p>
            <p class="font-semibold text-2xl md:text-3xl lg:text-4xl text-blue-800">
              {{ prov.jumlah_kasus }}
            </p>
          </div>
          <div class="flex flex-col">
            <p class="text-gray-800 font-medium">
              Indonesia
            </p>
            <p class="font-semibold text-2xl md:text-3xl lg:text-4xl text-blue-800">
              {{ nas.jumlah_positif }}
            </p>
          </div>
        </div>
        <div class="bg-green-300 rounded drop-shadow-md flex flex-col p-4 space-y-4">
          <p class="text-white font-medium text-base lg:text-lg">
            Sembuh
          </p>
          <div class="flex flex-col">
            <p class="font-medium text-gray-800">
              Jawa Barat
            </p>
            <p class="font-semibold text-xl md:text-2xl lg:text-4xl text-green-800">
              {{ prov.jumlah_sembuh }}
            </p>
          </div>
          <div class="flex flex-col">
            <p class="text-gray-800 font-medium">
              Indonesia
            </p>
            <p class="font-semibold text-2xl md:text-3xl lg:text-4xl text-green-800">
              {{ nas.jumlah_sembuh }}
            </p>
          </div>
        </div>
        <div class="bg-yellow-300 rounded drop-shadow-md flex flex-col p-4 space-y-4">
          <p class="text-white font-medium text-base lg:text-lg">
            Dirawat
          </p>
          <div class="flex flex-col">
            <p class="font-medium text-gray-800">
              Jawa Barat
            </p>
            <p class="font-semibold text-xl md:text-2xl lg:text-4xl text-yellow-800">
              {{ prov.jumlah_dirawat }}
            </p>
          </div>
          <div class="flex flex-col">
            <p class="text-gray-800 font-medium">
              Indonesia
            </p>
            <p class="font-semibold text-2xl md:text-3xl lg:text-4xl text-yellow-800">
              {{ nas.jumlah_dirawat }}
            </p>
          </div>
        </div>
        <div class="bg-red-300 rounded drop-shadow-md flex flex-col p-4 space-y-4">
          <p class="text-white font-medium text-base lg:text-lg">
            Meninggal
          </p>
          <div class="flex flex-col">
            <p class="font-medium text-gray-800">
              Jawa Barat
            </p>
            <p class="font-semibold text-xl md:text-2xl lg:text-4xl text-red-800">
              {{ prov.jumlah_meninggal }}
            </p>
          </div>
          <div class="flex flex-col">
            <p class="text-gray-800 font-medium">
              Indonesia
            </p>
            <p class="font-semibold text-2xl md:text-3xl lg:text-4xl text-red-800">
              {{ nas.jumlah_meninggal }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProvNasional',
  data () {
    return {
      prov: [],
      nas: [],
      last_date: null
    }
  },
  created () {
    this.getDataProvinsi()
    this.getDataNasional()
  },
  methods: {
    async getDataProvinsi () {
      const prov = await this.$axios.$get('/api/prov')
      this.prov = prov.list_data[1]
      this.last_date = prov.last_date
    },
    async getDataNasional () {
      const nasional = await this.$axios.$get('/api/update')
      this.nas = nasional.update.total
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
