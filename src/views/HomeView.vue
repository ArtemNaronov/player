<template>
  <div class="home container">
    <nav class="breadcrumb" aria-label="breadcrumbs">
      <ul>
        <li><a href="#">Enaza Music</a></li>
        <li><a href="#">E Каталог</a></li>
      </ul>
    </nav>
    <h1>Каталог</h1>
    <div class="albums__list">
      <AlbumItem :item="album" :people="getPerson(album.peopleIds)" v-for="(album, index) in albums" :key="index" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import AlbumItem from '@/components/albumItem.vue'

export default {
    name: "HomeView",
    data() {
        return {
            limit: 10,
            albums: [],
            people: []
        };
    },
    mounted() {
        this.getList();
    },
    methods: {
        async getList() {
            try {
                let response = await axios(`https://api.mobimusic.kz/?method=product.getNews&page=1&limit=${this.limit}`, {
                    method: "GET"
                });
                this.albums = response.data.collection.album;
                this.people = response.data.collection.people;
            }
            catch (error) {
                console.error(error);
            }
        },
        getPerson(item) {
          let thisPeople = []
          item.forEach(el => {
            thisPeople.push(this.people[el])
          });
          console.log(thisPeople);
          return thisPeople
        }
    },
    components: { AlbumItem }
}
</script>

<style lang="scss" scoped>
.albums__list {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
</style>