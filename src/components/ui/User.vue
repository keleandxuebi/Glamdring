<template>
    <div>
        <Pop></Pop>
        <p>username: <b>{{ $route.params.username }}</b></p>
        <h1>Hello, ShangBoyang</h1>
    </div>
</template>
<script>
import Pop from '../../components/ui/Header.vue';
export default {
    components: { Pop }, // 麻痹的用自定义不解析？？？？
    data () {
        console.log('Hello User');
        return {

        };
    }
};
</script>
<style media="screen">

</style>
