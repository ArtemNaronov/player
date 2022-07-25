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
            page: 1,
            albums: [],
            people: []
        };
    },
    mounted() {
        this.getList();
        this.onScroll()
    },
    methods: {
        async getList() {
            try {
                let response = await axios(`https://api.mobimusic.kz/?method=product.getNews&page=${this.page}&limit=10`, {
                    method: "GET"
                });
                let albums = response.data.collection.album;

                for(let key in albums) {
                  this.albums.push(albums[key])
                }
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
        },
        onScroll() {
          window.onscroll = () => {
            let bottomOfWindow = document.documentElement.scrollTop + window.innerHeight === document.documentElement.offsetHeight;
            if(bottomOfWindow) {
              this.page += 1;
              this.getList();
            }
          };
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