<template>
    <div class="recommend">
        <scroll  class="recommend-content" :data="list" ref="scroll">
            <div>
                <p>pfsdfsdfsdlakjflkj</p>
                <p>pfsdfsdfsdlakjflkj</p>
            </div>
        </scroll>
    </div>
</template>

<script>
import Scroll from '@/base/scroll/scroll'
export default {
    name: 'Recommend',
    components: {
        Scroll
    },
    data() {
        return {
            list:[]
        }
    },
    mounted() {
        this.$refs.scroll.refresh()
    },
}
</script>

<style lang="stylus" scoped>
.recommend
    position: fixed
    width: 100%
    top: 88px
    bottom: 0
    .recommend-content
        height: 100%
        overflow: hidden
</style>

