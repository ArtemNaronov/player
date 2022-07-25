<template>
    <div class="container">
        <nav class="breadcrumb" aria-label="breadcrumbs">
        <ul>
            <li><a href="#">Enaza Music</a></li>
            <li><a href="/">E Каталог</a></li>
            <li><a href="#">{{album.name}}</a></li>
        </ul>
        </nav>
        <MainAlbum :item='album' />
        <div class="track__list">
            <TrackItem v-for="(track, index) in tracks" :track="track" :key="index" />
        </div>
    </div>   
</template>

<script>
import axios from 'axios'
import MainAlbum from '../components/mainAlbum.vue'
import TrackItem from '@/components/trackItem.vue';
export default {
    data() {
        return {
            id: this.$route.params.id,
            album: [],
            tracks: []
        };
    },
    mounted() {
        this.getAlbum();
    },
    methods: {
        async getAlbum() {
            try {
                let response = await axios(`https://api.mobimusic.kz/?method=product.getCard&productId=${this.id}`, {
                    method: "GET"
                });
                this.album = response.data.collection.album[this.id];
                this.tracks = response.data.collection.track;
                console.log(response.data.collection);
            }
            catch (error) {
                console.error(error);
            }
        }
    },
    components: { MainAlbum, TrackItem }
}
</script>

<style lang="scss" scoped>
.track__list {
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
}
</style>