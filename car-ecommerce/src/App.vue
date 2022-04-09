<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->

        <div class='container mt-5'>
            <!-- ソートメニュー -->
            <div class="d-flex">
              <div class="mx-2">
                  <select class="form-select" aria-label="Default select example" v-model="category">
                      <option selected value="Category">Category</option>
                      <option value="Tesla">Telsa</option>
                      <option value="Porsche">Porsche</option>
                      <option value="Toyota">Toyota</option>
                      <option value="Honda">Honda</option>
                      <option value="Mazda">Mazda</option>
                      <option value="Mercedes-Benz">Mercedes-Benz</option>
                      <option value="Lexus">Lexus</option>
                      <option value="Lamborghini">Lamborghini</option>
                      <option value="Audi">Audi</option>
                      <option value="BMW">BMW</option>
                  </select>
              </div>
      
              <div>
                  <select class="form-select" aria-label="Default select example" v-model="sortedBy">
                      <option selected value="Sort By">Sort by:</option>
                      <option value="1">Price: Low to High</option>
                      <option value="2">Price: High to Low</option>
                      <option value="3">Newest Arrivals</option>
                  </select>
              </div>
    </div>
            <!-- 商品画像 -->
            <div class="d-flex flex-wrap pt-4">

              <!-- ここにv-forで繰り返し表示 -->
              <div v-for="carItem in sorted" v-bind:key="carItem.title">
                <item-card v-bind:car-item="carItem"></item-card>
              </div>

            </div>
            
        </div>
  </div>
</template>

<script>
import ItemCard from './components/ItemCard.vue'

export default {
  name: 'App',
  components: {
    ItemCard,
  },
  data() {
    return {
      sortedBy: "Sort By",
      category: "Category",
      items: [
        {
          title: 'Model 3',
          category: 'Tesla',
          price: 48490,
          date: "2020-09-04",
          img: "https://media.istockphoto.com/photos/electric-sports-car-the-tesla-model-3-picture-id1277254968?k=6&m=1277254968&s=612x612&w=0&h=4j3WhZQD95BJyqOnML2sDatX9SFQomJclLyd5bbV3FU=",
        },
        {
          title: 'Model X',
          category: 'Tesla',
          price: 89990,
          date: "2017-08-08",
          img: "https://media.istockphoto.com/photos/tesla-model-x-travelling-on-the-freeway-in-silicon-valley-picture-id1191552504?k=6&m=1191552504&s=612x612&w=0&h=NWHap01jKkYzC5BT-9gaKYr8phGeO1ZUYHnGPLQ5RUM=",
        },
        {
          title: 'Model S',
          category: 'Tesla',
          price: 82990,
          date: "2019-04-01",
          img: "https://media.istockphoto.com/photos/tesla-model-s-on-the-highway-picture-id582261244?k=6&m=582261244&s=612x612&w=0&h=LwYAD7oI6Xy9gsRM7OZ10Nsq-ehGsSmLcbPwQEmZBpg=",
        },
        {
          title: 'Model Y',
          category: 'Tesla',
          price: 48190,
          date: "2020-02-02",
          img: "https://media.istockphoto.com/photos/tesla-model-y-in-austin-texas-at-360-bridge-picture-id1272025387?k=6&m=1272025387&s=612x612&w=0&h=o_W18f-pFNdHsSpdaNejXSS7G8XnWfayhinzZVWhQU8=",
        },
        {
          title: 'Cayenne',
          category: 'Porsche',
          price: 67500,
          date: "2017-12-20",
          img: "https://media.istockphoto.com/photos/porsche-cayenne-picture-id1138819485?k=6&m=1138819485&s=612x612&w=0&h=uSPCZUofVb5ComBHUpH5qZ5QB7B1WWcKFxNzm53W2ME=",
        },
        {
          title: 'Macan',
          category: 'Porsche',
          price: 52100,
          date: "2019-07-12",
          img: "https://media.istockphoto.com/photos/porsche-macan-gts-crossover-suv-picture-id508107322?k=6&m=508107322&s=612x612&w=0&h=syLuqvZng-mEbqJblhY3q6wWxcUlaijknWO9ea90CJo=",
        },
        {
          title: 'Camry',
          category: 'Toyota',
          price: 24425,
          date: "2015-06-29",
          img: "https://media.istockphoto.com/photos/toyota-camry-in-motion-picture-id905266220?k=6&m=905266220&s=612x612&w=0&h=8iRQyhjJYVn_ppC6x3LTLGzG0P67NyCvuQqxvO40ryI=",
        },
        {
          title: 'Accord',
          category: 'Honda',
          price: 24800,
          date: "2018-10-02",
          img: "https://media.istockphoto.com/photos/honda-accord-in-the-city-picture-id649004692?k=6&m=649004692&s=612x612&w=0&h=7WnRBZcLQ6-Y2FrKKVxya3nwJ6U-CLeZUuk-D5RVlu8=",
        },
        {
          title: 'Civic',
          category: 'Honda',
          price: 20650,
          date: "2015-04-04",
          img: "https://media.istockphoto.com/photos/new-honda-civic-front-picture-id458119929?k=6&m=458119929&s=612x612&w=0&h=h8uh7Bqgw2l1Hhg2TmX05VSBnp2cxrjpTBtvPYpKiD4=",
        },
        {
          title: 'CX-5',
          category: 'Mazda',
          price: 26940,
          date: "2012-11-03",
          img: "https://media.istockphoto.com/photos/new-2018-mazda-cx5-red-cx5-suv-car-japanese-car-moving-vehicle-picture-id1069236296?k=6&m=1069236296&s=612x612&w=0&h=CO2YJA51esFD2an-sKkhusVifvwTwhBXR3ebxD6h3Fg=",
        },
        {
          title: 'GLECoupe',
          category: 'Mercedes-Benz',
          price: 76500,
          date: "2020-02-05",
          img: "https://media.istockphoto.com/photos/mercedesbenz-gle-43-4matic-coupe-picture-id894961460?k=6&m=894961460&s=612x612&w=0&h=aKbMi31eXuJOSVEKlesIzsJlLM6QhUe0k_5V-FJvH0M=",
        },
        {
          title: 'CLA',
          category: 'Mercedes-Benz',
          price: 378500,
          date: "2019-06-09",
          img: "https://media.istockphoto.com/photos/mercedes-benz-cla-picture-id472122163?k=6&m=472122163&s=612x612&w=0&h=IIRhsoWfMXXy6b_aTMtSA2dgSTPK4pSD-_M5vh8OY6M=",
        },
        {
          title: 'GLA250',
          category: 'Mercedes-Benz',
          price: 37280,
          date: "2017-05-02",
          img: "https://media.istockphoto.com/photos/mercedesbenz-gla-2020-test-drive-day-picture-id1297389811?k=6&m=1297389811&s=612x612&w=0&h=NOPBUppwL9aFKKoha3phbhpHUw6hYSdsW5NlFejp4RU=",
        },
        {
          title: 'RX350',
          category: 'Lexus',
          price: 45175,
          date: "2015-01-01",
          img: "https://media.istockphoto.com/photos/hybrid-suv-lexus-nx-on-the-road-picture-id657915058?k=6&m=657915058&s=612x612&w=0&h=DGCgfv-pBE75oOUktrX_WpGSadnEmRcm5iPfa49BOQw=",
        },
        {
          title: 'NX300',
          category: 'Lexus',
          price: 37510,
          date: "2018-09-12",
          img: "https://media.istockphoto.com/photos/lexus-nx-200t-car-picture-id480681192?k=6&m=480681192&s=612x612&w=0&h=Ne9_r4aioLH_jpiK41fHpTr-ADdKsHcFMOOPXT9DGp8=",
        },
        {
          title: 'Urus',
          category: 'Lamborghini',
          price: 218000,
          date: "2021-08-16",
          img: "https://media.istockphoto.com/photos/lamborghini-urus-picture-id1184360237?k=6&m=1184360237&s=612x612&w=0&h=cDC3bjJCG9fZC8VpJnuoK73du-hKLnij-14eKHxuLyA=",
        },
        {
          title: 'Aventador',
          category: 'Lamborghini',
          price: 393695,
          date: "2020-09-11",
          img: "https://media.istockphoto.com/photos/lamborghini-aventador-lp-7504-superveloce-picture-id1083962000?k=6&m=1083962000&s=612x612&w=0&h=VBYRfp0408ZHqDTdJ69pIJP7z_zhj2T7z8OB-28adSU=",
        },
        {
          title: 'A3',
          category: 'Audi',
          price: 33500,
          date: "2019-05-08",
          img: "https://media.istockphoto.com/photos/audi-a3-sportback-on-a-street-picture-id1255388367?k=6&m=1255388367&s=612x612&w=0&h=nh2TLu9W-68-3_PgN1-0qkXYaw4mfFZviKY1sY_fjJ8=",
        },
        {
          title: 'X3',
          category: 'BMW',
          price: 43000,
          date: "2018-03-11",
          img: "https://media.istockphoto.com/photos/-picture-id1206921084?k=6&m=1206921084&s=612x612&w=0&h=o8ETeAQHAuzOerMorNWxPnDpyhSyrxiy6vvIQ8TLd4Y=",
        },
        {
          title: '2Series',
          category: 'BMW',
          price: 37500,
          date: "2019-01-15",
          img: "https://media.istockphoto.com/photos/coupe-competition-picture-id1187329409?k=6&m=1187329409&s=612x612&w=0&h=qDHLX8yA8WVGmEwFU8k56z72uobZfcGkHH14zzpLPc4=",
        }
      ]
    }
  },
  computed: {
    sorted: function(){
      // SortHeaderで指定した属性でfilterしたitems配列を返す->v-forでレンダリング
      let res = this.items;

      // filter
      if (this.category !== "Category"){
        res = this.items.filter(item => item.category === this.category);
      }
    
      // sort
      if (this.sortedBy==="1"){
        // low to high
        res.sort((a, b) => a.price - b.price);
      } else if (this.sortedBy==="2"){
        // high to low
        res.sort((a, b) => b.price - a.price);
      } else if (this.sortedBy==="3"){
        // newest arrivals
        // dateはStringで定義されている
        res.sort((a, b) => {
          let date1 = new Date(a.date);
          let date2 = new Date(b.date);
          return date2 - date1;
        })
      }
      return res;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
