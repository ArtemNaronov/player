<template>
    <div>
        <article class="media">
            <div class="media-right">
                <figure class="image is-64x64">
                    <img :src="track.coverUrl" alt="Image">
                </figure>
            </div>
            <div class="media-content">
                <div class="content">
                    <p>
                    <strong>John Smith</strong> <small>@johnsmith</small> <small>31m</small>
                    <br>
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.
                    </p>
                </div>
                {{track}}
            </div>
        </article>
    </div>
</template>

<script>
export default {
    props: {
        track: {
            type: Object
        }
    }
}
</script>

<style lang="scss" scoped>

</style>