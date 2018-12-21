<template>
    <div>
        <swiper class="swiperWrapper" :options="swiperOption" ref="mySwiper" v-if="showSwiper">
            <!-- slides -->
            <swiper-slide class="swiperSlide" v-for="item of swiperList" :key="item.id">
                <img :src="item.picUrl" alt="">
            </swiper-slide>
           
            <!-- Optional controls -->
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
</template>

<script>
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
    name: 'Swiper',
    components: {
        swiper,
        swiperSlide
    },
    props:{
        swiperList: Array
    },
    data() {
        return {
            swiperOption: {
                pagination: {
                    el: '.swiper-pagination'
                },
                autoplay: {
                    disableOnInteraction: false,
                },

                loop:true
            }
        }
    },
    computed: {
      swiper() {
        return this.$refs.mySwiper.swiper
      },
      showSwiper () {
        return this.swiperList.length
      }
    },
    mounted() {
        
    },
}
</script>

<style lang="stylus" scoped>
    >>> .swiper-pagination
        bottom 2px
        .swiper-pagination-bullet
            background #FFF
            opacity .3
            transition width .3s
        .swiper-pagination-bullet-active
            opacity .7
            width 20px
            border-radius 5px 
    .swiperWrapper
        width 100%
        .swiperSlide
            width 100%
            height 0
            padding-bottom 40%
            overflow hidden
            img 
                width  100%
</style>


