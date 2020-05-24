<template>
    <div id="add-blog">
    <h3>Add a new Article</h3>
    <form v-if="!submitted">
        <label>Article Title:</label>
        <input type="text" v-model.lazy="blog.title" required/>
        <label>Article Content:</label>
        <textarea v-model.lazy="blog.content"></textarea>
        <div id="checkboxes">
            <label>Titans</label>
            <input type="checkbox" value="titans" v-model="blog.categories"/>
            <label>Gypsies</label>
            <input type="checkbox" value="gypsies" v-model="blog.categories"/>
            <label>Sphinx</label>
            <input type="checkbox" value="sphinx" v-model="blog.categories"/>
        </div>
        <label>Author</label>
        <select v-model="blog.author">
            <option v-for="author in authors">{{ author }}</option>
        </select>
        <button v-on:click.prevent="post">Add Article</button>
    </form>
    <div v-if="submitted">
        <h3>Article added successfully</h3>
    </div>
    <div id="preview">
        <h3>Preview Article</h3>
        <p>Article Title: {{ blog.title}}</p>
        <p>Article Content: </p>
        <p>{{ blog.content }}</p>
        <p>Article Content</p>
        <p>Article Categories:</p>
        <ul>
            <li v-for="category in blog.categories">{{ category }}</li>
        </ul>
        <p>Author: {{ blog.author }}</p>
    </div>
    </div>
</template>

<script>
import searchMixins from '../mixins/searchMixins';

export default {
  components: {
    
    },
  data () {
    return {
        blog:{
            title: "",
            content: "",
            categories: [],
            author: ""
        },
        authors:['Jocatins','Miss Lee','Sphinx', 'Gypsies'],
        submitted: false,
    }
},
    methods: {
        post: function(){
            this.$http.post('https://sphinx-blog.firebaseio.com/post.json',this.blog).then(function(data){
                console.log(data);
                this.submitted = true;
            });
        }
  },
    mixins: [searchMixins]
  }
</script>

<style scope>
#add-blog*{
    box-sizing:border-box;
}
#add-blog{
    margin: 20px auto;
    max-width: 500px;
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #ccc;
    margin: 30px 0;
}
h3{
    margin-top: 10px;
}
#checkboxes input{
    display: inline-block;
    margin-right: 10px;
}
#checkboxes label{
    display: inline-block;
}
</style>
