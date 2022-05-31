<template>
  <div>
    <Nav @scrollToProv="scrollIntoProv" @scrollToRs="scrollIntoRs" @scrollToJabar="scrollIntoJabar" />
    <div class="h-[10rem] bg-mycol">
      <div class="flex mx-auto max-w-5xl px-0 md:px-4 items-center ">
        <div class="flex flex-col w-1/2 space-y-4 lg:space-y-8">
          <div>
            <p class="text-xl md:text-2xl lg:text-3xl font-semibold">
              Portal Informasi Covid-19 Jawa Barat
            </p>
            <p class="text-xl md:text-2xl lg:text-3xl font-semibold">
              Nasional & Internasional
            </p>
          </div>
          <div>
            <p>Media Informasi Covid-19. Menampilkan data perkembangan kasus terkini covid-19 Provinsi Jawa Barat, Nasional dan Internasional.</p>
          </div>
        </div>
        <div class="w-1/2">
          <img src="~/assets/images/DrawKit Vector Illustration Health & Medical (3).png" alt="">
        </div>
      </div>
    </div>
    <ProvNasional ref="kumulatif" />
    <TableProvinsi ref="provinsi" />
    <TableRs ref="hospital" />
    <ButtonToTop :invisible="invisible" @scrollToTop="scrollTop" />
    <footer class="text-center py-4 md:py-6 bg-gray-100">
      <p>&copy; 2022 | Nurul Jaelani</p>
    </footer>
  </div>
</template>

<script>
import ProvNasional from '../components/ProvNasional.vue'
import TableProvinsi from '../components/TableProvinsi.vue'
import Nav from '~/components/Nav.vue'
import ButtonToTop from '~/components/ButtonToTop.vue'
import TableRs from '~/components/TableRs.vue'
export default {
  name: 'IndexPage',
  components: { Nav, ProvNasional, TableProvinsi, ButtonToTop, TableRs },
  data () {
    return {
      options: null,
      invisible: true,
      isBrowser: null
    }
  },
  created () {
    this.options = {
      block: 'start',
      behavior: 'smooth',
      inline: 'start'
    }

    this.isBrowser = typeof window !== 'undefined'

    if (this.isBrowser) {
      // eslint-disable-next-line nuxt/no-globals-in-created
      window.addEventListener('scroll', this.toggleVisible)
    }
  },
  methods: {
    scrollIntoProv () {
      // eslint-disable-next-line dot-notation
      this.$refs.provinsi.$refs.prov.scrollIntoView(this.options)
    },
    scrollIntoJabar () {
      // eslint-disable-next-line dot-notation
      this.$refs.kumulatif.$refs.jabar.scrollIntoView(this.options)
    },
    scrollIntoRs () {
      // eslint-disable-next-line dot-notation
      this.$refs.hospital.$refs.rs.scrollIntoView(this.options)
    },
    toggleVisible () {
      const scrolled = document.documentElement.scrollTop
      if (scrolled > 300) {
        this.invisible = false
      } else if (scrolled <= 300) {
        this.invisible = true
      }
    },
    scrollTop () {
      if (this.isBrowser) {
        window.scrollTo({
          top: 0,
          behavior: 'smooth'
        })
      }
    }
  }
}
</script>
