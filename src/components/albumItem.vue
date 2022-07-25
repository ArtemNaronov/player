<template>
    <router-link :to="'/catalog/' + item.id" class="albums__list__item">
        <img :src="item.coverUrl" alt="">
        <span class="albums__list__item__title">
            {{item.name}} • {{item.year}}
        </span>
        <span class="albums__list__item__artist">{{people[0].name}}</span>
        <span class="albums__list__item__count">
            Треков: {{item.trackCount}} 
        </span>
      </router-link>
</template>

<script>
export default {
    props: {
        item: {
            type: Object
        },
        people: {
            type: Array
        }
    }
}
</script>

<style scoped lang="scss">
.albums__list__item {
    width: 20%;
    display: flex;
    flex-direction: column;

    & img {
        border-radius: 20px;
    }

    &__title {
        font-weight: 700;
        font-size: 19px;
        line-height: 120%;
        color: #4F4F4F;
        margin-top: 15px;
    }
    &__artist,
    &__count {
        font-weight: 400;
        font-size: 15px;
        line-height: 120%;
        color: #A7A7A7;
    }
    &__count {        
        margin-top: 10px;
    }
}
</style>