<template>
    <div class="recommend" >
        <scroll  class="recommend-content" :data="discList" ref="scroll">
            <div>
                <header-swiper class="slider-wrapper" :swiperList="recommends"></header-swiper>
                <div class="recommend-list">
                    <h1 class="list-title">热门歌单推荐</h1>
                    <ul>
                        <li class="item">
                            <div class="icon">
                                <img src="http://p.qpic.cn/music_cover/NaYDCjF6oFDyCBFMbYpoK1q2LhZHf7lUYxONJpn7NhX7BZsqCsgSEQ/600?n=1 alt=" width="60" height="60">
                            </div>
                            <div class="text">
                                <h2 class="name">叶洛洛</h2>
                                <p class="desc">清甜可爱：想把这些声音抱回家！</p>
                            </div>
                        </li>
                    </ul>
                </div>
            </div>
        </scroll>
    </div>
</template>

<script>
import Scroll from '@/base/scroll/scroll'
import HeaderSwiper from '@/base/swiper/swiper'
import axios from 'axios'
import {getRecommend, getDiscList} from '../../api/recommend'
import {ERR_OK} from '../../api/config'

export default {
    name: 'Recommend',
    data() {
        return {
            recommends:[1,2,3,4,5,6,7,8,9,10],   // swiper data
            discList: []     // list data
        }
    },
    mounted() {
        this._getRecommend()
        // this._getDiscList()
        this.$refs.scroll.refresh()
    },
    methods: {
        _getRecommend() {
            getRecommend().then((res) => {
                if (res.code === ERR_OK) {
                    this.recommends = res.data.slider      //swiper
                }
            })
        },
        _getDiscList() {
            getDiscList().then((res) => {
                console.log(res)
                if (res.code === ERR_OK) {
                    console.log(res.data.list)
                    this.discList = res.data.list            // list
                }
            })
        },
    },
    components: {
        Scroll,
        HeaderSwiper
    },
}
</script>

<style lang="stylus" scoped>
@import "../../common/stylus/variable.styl"
.recommend
    position: fixed
    width: 100%
    top: 88px
    bottom: 0
    .recommend-content
        height: 100%
        overflow: hidden
        .slider-wrapper
            width: 100%
            height 0
            padding-bottom 40%
            overflow: hidden
            background rgba(11,11,11,.3)
        .recommend-list
            .list-title
                height: 65px
                line-height: 65px
                text-align: center
                font-size: $font-size-medium
                color: $color-theme
            .item
                display: flex
                box-sizing: border-box
                align-items: center
                padding: 0 20px 20px 20px
                .icon
                    flex: 0 0 60px
                    width: 60px
                    padding-right: 20px
                .text
                    display: flex
                    flex-direction: column
                    justify-content: center
                    flex: 1
                    line-height: 20px
                    overflow: hidden
                    font-size: $font-size-medium
                    .name
                        margin-bottom: 10px
                        color: $color-text
                    .desc
                        color: $color-text-d
</style>

