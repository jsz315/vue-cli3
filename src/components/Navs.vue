<template>
    <div class="navs">
        <div class="nav" v-for="item in navs" :key="item.id">
            <img class="nav-img" :src="item.url">
            <div class="nav-tip">{{item.name}}</div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'Navs',
    props: {
        say: {
            type: Function
        }
    },
    data () {
        return {
            msg: 'son',
            navs: ""
        }
    },
    computed: {

    },
    beforeMount(){
        console.log("son beforeMount");
    },
    mounted(){
        console.log("son mounted");
        this.$axios.post("/api/navs", {
            name: 'jsz'
        }).then(res=>{
            this.navs = res.data;
            // var list = [];
            // for(var i = 0; i < 10; i++){
            //     var obj = res.data[i];
            //     obj.url = res.data[i + 1].url;
            //     list.push(obj);
            // }
            // console.log(JSON.stringify(list));
            // this.navs = list;
        })

    },
    created(){
        console.log("son created");
    },
    // beforeRouteupdate(to, from, next){
    //     console.log("beforeRouteupdate");
    //     console.log(to);
    //     next();
    // },
    methods: {
        
    }
}
</script>

    <!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
.navs{
    font-size: 0;
    .nav{
        width: 120px;
        margin: 15px;
        text-align: center;
        display: inline-block;
    }
    .nav-img{
        width: 100%;
    }
    .nav-tip{
        color: rgb(133, 133, 133);
        font-size: 18px;
    }
}
</style>
