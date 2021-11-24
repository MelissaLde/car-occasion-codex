<template>
  <div id="app">
    <the-nav
      :brand-list-filters="brandListFilters"
      @filter-change="carFilter"
    />

    <the-main-layout :car-list="filterCarList" />

    <the-footer />
  </div>
</template>

<script>
import TheNav from '@/components/core/TheNav'
import TheFooter from '@/components/core/TheFooter'
import TheMainLayout from '@/components/core/TheMain'

export default {
  name: 'App',

  components: { TheMainLayout, TheFooter, TheNav },

  data: () => ({
    brandListFilters: [
      {
        id: 1,
        name: 'Citroen',
        announcement: 236,
      },
      {
        id: 2,
        name: 'Peugeot',
        announcement: 179,
      },
      {
        id: 3,
        name: 'Renault',
        announcement: 196,
      },
      {
        id: 4,
        name: 'Volkswagen',
        announcement: 78,
      },
    ],

    filterCarList: [],
    filterPricesList: [],
  }),

  computed: {
    carlist() {
      const carsDataBase = Array(100)
        .fill(null)
        .map((item, index) => {
          const { brand, model, image } = this.getRandomBrand()

          return {
            id: index,
            infosList: {
              brand: brand,
              model: model,
              price: this.getRandomPrice(),
              energy: this.getRandomEnergy(),
              year: this.getRandomYears(),
              kilometer: this.getRandomKilometers(),
            },
            image: image,
          }
        })
      return carsDataBase
    },
  },

  created() {
    this.filterCarList = this.carlist
    this.filterPricesList = this.carlist
  },

  methods: {
    getRandomPrice() {
      return Math.floor(Math.random() * (50000 - 10000))
    },

    getRandomYears() {
      return Math.floor(Math.random() * (2021 - 1970) + 1970)
    },

    getRandomKilometers() {
      return Math.floor(Math.random() * (250000 - 999))
    },

    getRandomEnergy() {
      const energyList = ['Gasoiline', 'Diesel', 'Hybrid', 'Electric']
      const randomEnergy =
        energyList[Math.floor(Math.random() * energyList.length)]

      return randomEnergy
    },

    getRandomBrand() {
      const modelList = {
        Suzuki: [
          {
            modelName: 'Swift',
            image:
              'https://cdn.motor1.com/images/mgl/GVA01/s1/2017-suzuki-swift.jpg',
          },
          {
            modelName: 'Vitara',
            image:
              'https://static.moniteurautomobile.be/imgcontrol/images_tmp/clients/moniteur/c680-d465/content/medias/images/cars/suzuki/vitara/suzuki--vitara-5p--2015/suzuki--vitara-5p--2015-m-1.jpg',
          },
        ],
        Peugeot: [
          {
            modelName: '207',
            image:
              'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS77_7cBdNlzijUEg_LHY6QNVKsvp61C_cE-w&usqp=CAU',
          },
          {
            modelName: '208',
            image:
              'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQCIKwOtlRbdCVqllZCWowaDlNzBQxOrxaDuA&usqp=CAU',
          },
        ],
        Renault: [
          {
            modelName: 'Clio 3',
            image:
              'data:image/jpeg;base64,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',
          },
          {
            modelName: 'Clio 4',
            image:
              'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRTH_-EpMgU_LEdHH2OAB95cXEzuEzhWPdFBBJS52zWGGRInbZPt8RZS-gkjf4Ce30qkdg&usqp=CAU',
          },
        ],
        Citroen: [
          {
            modelName: 'C3',
            image:
              'https://sslphotos.jato.com/PHOTO400/SSCF/CITROEN/C3/2021/5HA.JPG',
          },
          {
            modelName: 'C4',
            image:
              'http://mavoitur.com/photo/10-03-2018-14-01-11_66698_image.jpg',
          },
        ],
        Nissan: [
          {
            modelName: 'Ariya',
            image:
              'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQL734WeANHZxAdH7AtJRb9m1CBNYB7wueI7J8t890sOn4SDKMi0-iO5Cu7o4r87uGQd3k&usqp=CAU',
          },
          {
            modelName: 'Micra',
            image:
              'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQKfj44jJv-vF-itCyZKmfs8jUjEPd9I9DlqO57JWRmmALBehxM-vF3byq2oMip_oTg73k&usqp=CAU',
          },
        ],
        Ford: [
          {
            modelName: 'Focus',
            image:
              'https://sf1.autojournal.fr/wp-content/uploads/autojournal/2020/06/0a2e6b66882e0ba94bc4d51a.jpg',
          },
          {
            modelName: 'Fiesta',
            image:
              'https://1.bp.blogspot.com/-WVkRsLiYw_o/W_XCcUoi_qI/AAAAAAAAYas/QINkDZdue9oxKI8jizyslUBJffvJ6QdaQCLcBGAs/s1600/ford-fiesta-bleu-azur-chrome-blue.jpg',
          },
        ],
        Hyundai: [
          {
            modelName: 'Tucson',
            image:
              'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQATMFE6eL_jf9IGBueZBm_N5nR7cm0hBdAQA&usqp=CAU',
          },
          {
            modelName: 'i20',
            image: 'http://www.zylinders.com/photos/Hyundai%20i20%202018.jpg',
          },
        ],
        Volkswagen: [
          {
            modelName: 'Golf',
            image:
              'https://cdn.motor1.com/images/mgl/kjgvP/s4/2020-volkswagen-golf-gtd.jpg',
          },
          {
            modelName: 'Polo',
            image:
              'https://www.garagecorsini.com/public/img/big/20180726172152jpg_5b7fd74f7eefd.jpg',
          },
        ],
        Mercedes: [
          {
            modelName: 'Benz Classe A Berline',
            image:
              'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT1BjIFQING18AnCtk6K8no-wz-eJpUeG-1I1zjW1GHYvey8qhDwzRtN_Jj_fEgRU1N60Q&usqp=CAU',
          },
          {
            modelName: 'Benz GLA',
            image:
              'https://cdn.motor1.com/images/mgl/nRXJk/s1/2020-mercedes-benz-gla.jpg',
          },
        ],
        DS: [
          {
            modelName: 'DS9',
            image:
              'https://sf2.autojournal.fr/wp-content/uploads/autojournal/2020/06/DS_DS9_2020_be473.jpg',
          },
          {
            modelName: 'DS5',
            image:
              'https://www.largus.fr/images/images/nouvelle-ds5-2015--01.jpg',
          },
        ],
      }

      const energyList = [
        'Suzuki',
        'Peugeot',
        'Renault',
        'Citroen',
        'Nissan',
        'Ford',
        'Hyundai',
        'Volkswagen',
        'Mercedes',
        'DS',
      ]

      const randomBrand =
        energyList[Math.floor(Math.random() * energyList.length)]

      return {
        brand: randomBrand,
        model:
          modelList[randomBrand][
            Math.floor(Math.random() * modelList[randomBrand].length)
          ].modelName,
        image:
          modelList[randomBrand][
            Math.floor(Math.random() * modelList[randomBrand].length)
          ].image,
      }
    },

    carFilter(userFilters) {
      this.filterCarList = this.carlist.filter((car) => {
        if (!userFilters.selectedModels)
          return (
            car.infosList.brand.toLowerCase() ===
            userFilters.selectedBrand.toLowerCase()
          )
        else {
          return (
            car.infosList.brand.toLowerCase() ===
              userFilters.selectedBrand.toLowerCase() &&
            car.infosList.model.toLowerCase() ===
              userFilters.selectedModels.toLowerCase()
          )
        }
      })
    },

    pricesFilter(userFilters) {
      this.filterPricesList = this.carlist.filter(
        (car) =>
          car.infosList.price >= userFilters.pricesMin &&
          car.infosList.price <= userFilters.pricesMax
      )
    },
  },
}
</script>
