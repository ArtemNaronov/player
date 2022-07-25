<template>
    <div class="media">
        <div class="media-right" :class="{'card-loader': !item.coverUrl}">
            <img :src="item.coverUrl" alt="Image" v-if="item.coverUrl" />
            <span v-else></span>
        </div>
        <div class="media-content">
            <div class="">
                <h1>{{item.name}}</h1>
                <div class="content__info">
                    <span>Tatiana Culhane</span>
                    <span>Треков: {{item.trackCount}}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        item: {
            type: Object
        }
    },
    data() {
        return {
            imgLoad: false
        }
    }
}
</script>

<style lang="scss" scoped>
.media {
  margin-bottom: 44px;
    & img {
        width: 278px;
        height: 278px;
        border-radius: 13px;
    }
    & .content__info {
        display: flex;
        flex-direction: column;
    }
}

.card-loader {
  background-color: #fff;
  position: relative;
  border-radius: 2px;
  margin-bottom: 0;
  overflow: hidden;
    & span {
        width: 278px;
        height: 278px;
        display: block;
        background-color: #ddd6d6;
    }
  &:only-child {
    margin-top:0;
  }

  &:before {
    content: '';
    display: block;
    background-color: #ededed;
    box-shadow: -48px 78px 0 -48px #ededed, -51px 102px 0 -51px #ededed;
  }

  &:after {
    content: '';
    background-color: #333;
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    animation-duration: 0.6s;
    animation-iteration-count: infinite;
    animation-name: loader-animate;
    animation-timing-function: linear;
    background: -webkit-linear-gradient(left, rgba(255,255,255,0) 0%, rgba(255,255,255,0.6) 30%, rgba(255,255,255,0) 81%);
    background: -o-linear-gradient(left, rgba(255,255,255,0) 0%, rgba(255,255,255,0.6) 30%, rgba(255,255,255,0) 81%);
    background: linear-gradient(to right, rgba(255,255,255,0) 0%, rgba(255,255,255,0.6) 30%, rgba(255,255,255,0) 81%);
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#00ffffff', endColorstr='#00ffffff',GradientType=1 );
  }
}
 

// Loader animation
@keyframes loader-animate{
 0%{
    transform: translate3d(-100%, 0, 0);
  }
 100%{
    transform: translate3d(100%, 0, 0);
  }
}
</style>