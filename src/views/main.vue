<template>
    <div>
        <Go></Go>
        <!--
        <h1 class="title" v-text="message" v-on:click="greet"></h1>
        -->
        <!-- use v-link directive for navigation. -->
        <div class="main">
            <!-- 具名路由 同时支持 router.go({name: 'one_piece', params: {barID: 001}) -->
            <a v-link="'home'">Home</a>
            <a v-link="{ path: '/foo', activeClass: 'custom-active-class' }">Go to Foo</a>
            <a v-link="{ name: 'one_piece', params: {barID: '001'} }">Go to Bar: One Piece</a>
            <a v-link="{ path: '/user/boyang' }">Go to User: Boyang</a>
            <a v-link="{ name: 'mySpace'}">My Space</a>
        </div>
        <!-- use router-view element as route outlet -->
        <!-- important -->
        <!-- and the classname also can be rename  -->
        <router-view class="view" transition="expand" transition-mode="out-in"></router-view>
    </div>
</template>
<script>
import store from '../config/store-config';
import Go from '../components/ui/Header.vue';

export default {
    components: { Go }, // 麻痹的用自定义不解析？？？？
    store
};
</script>
<style>
.main {
    position: absolute; top: 44px; left: 0;
    width: 100%; height: 100%;
    z-index: 1;
}
.view {
    position: absolute; top: 0; left: 0;
    width: 100%; height: 100%;
    z-index: 99;
}
/* 必需 */
.expand-transition {
    transition: all .3s ease;
    background-color: #eee;
    overflow: hidden;
}
/* .expand-enter 定义进入的开始状态 */
/* .expand-leave 定义离开的结束状态 */
.expand-enter, .expand-leave {
    height: 0;
    padding: 0 10px;
    opacity: 0;
}
</style>
