<template>
    <div class="track">
        <article class="media">
            <div class="media-right">
                <figure class="image is-64x64">
                    <img :src="track.coverUrl" alt="Image">
                </figure>
            </div>
            <div class="media-content">
                {{track.name}}
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
    .track {
        width: 30%;
    }
</style>