<template>
<div v-theme="'wide'" id="show-blogs">
    <h1>List of Blogs Titles</h1>
    <input type="text" v-model="search" placeholder="search"/>
    <div v-for="blog in filteredBlogs"class="single-blog">
        <h2 v-rainbow>{{ blog.title | to-uppercase }}</h2>        
    </div>
</div>
</template>

<script>

import searchMixins from '../mixins/searchMixins';
export default {

  data () {
    return {
        blogs: [],
        search: ""
    }
    },
    methods: {
},
created(){
    this.$http.get('https://sphinx-blog.firebaseio.com/post/')
    .then(function(data){
        console.log(data);
        this.blogs = data.body.slice(0,10);
    })
},
    computed: {
    },
    filters: {
        toUppercase(value){
            return value.toUpperCase();
        }
    },
    directives: {
        'rainbow': {
            bind(el, binding, vnode){
                el.style.color = "#" + Math.random().toString(16).slice(2,8);
            }
        }
    },
    mixins: [searchMixins]
}
</script>

<style scoped>
#show-blogs{
    max-width: 800px;
    margin: 0 auto;
}
.single-blog{
    padding: 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: orchid;
    
}
</style>
