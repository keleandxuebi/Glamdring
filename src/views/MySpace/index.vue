<template>
    <div>
        <Pop></Pop>
        <h3 class="h3">MySpace {{ msg }}</h3>
        <div>
            <a v-link="'aop'">user</a>
        </div>
        <router-view class="view" transition="expand" transition-mode="out-in"></router-view>
    </div>
</template>
<script>
// import Vue from 'vue';
import Pop from '../../components/ui/Header.vue';
import { getMySpace } from '../../store/MySpace/actions';
import { getSpaceData } from '../../store/MySpace/getters';
import Store from '../../config/store-config';

export default {
    Store,
    components: { Pop }, // 麻痹的用自定义不解析？？？？
    data () {
        return {
            headerTitle: 'MySpace',
            backFlag: true,
            optFlag: true,
            msg: '紫微宸居'
        };
    },
    events: {
        headerBackHandler: function () {
            window.history.back();
        },
        headerOptHandler: function () {
            Store.router.go({name: 'foo'});
            console.log('my space headerOptions');
        }
    },
    route: {
        activate () {
            this.getMySpace();
            console.log('route', this);
        },
        canActivate () {
            console.log('canActivate');
        }
    },
    vuex: {
        getters: {
            spaces: getSpaceData
        },
        actions: {
            getMySpace
        }
    }
};

</script>
<style>
.h3 {
    position: relative; top: 44px;
    width: 100%; height: 100px;

}
</style>
