<template>
    <div class="gr-header">
        <span class="left" v-show="backFlag" @click="backHandler">返回</span>
        {{title}}
        <span class="right" v-show="optFlag" @click="optionHandler">分享</span>
    </div>
</template>
<script>
export default {
    name: 'grHeader',
    data () {
        // console.log(this.$parent.headerTitle);
        return {
            title: this.$parent.headerTitle || 'Glamdring Header',
            backFlag: this.$parent.backFlag,
            optFlag: this.$parent.optFlag
        };
    },
    methods: {
        backHandler () {
            window.history.back();
        },
        optionHandler () {
            this.$dispatch('headerOptHandler');
            // console.log('option');
        }
    }
};
</script>
<style>
.gr-header {
    position: absolute; top: 0; left: 0;
    width: 100%; height: 44px;
    line-height: 44px;
    text-align: center;
    background: #ff6600; color: #fff;
}
.gr-header span.left {
    position: absolute; left: 0; top: 0;
    display: block;
    width: 50px; height: 44px;
}
.gr-header span.right {
    position: absolute; right: 0; top: 0;
    display: block;
    width: 50px; height: 44px;
}
</style>
