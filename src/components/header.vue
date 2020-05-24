<template>
    <nav>
        <ul>
            <li><router-link to="/" exact>Article</router-link></li>
            <li><router-link to="/add" exact>Create Article</router-link></li>
        </ul>
        </nav>
</template>

<script>
export default {
    
}
</script>
<style scoped>
ul{
    list-style-type: none;
    text-align: center;
    margin: 0;
}
li{
    display: inline-block;
    margin: 0 10px;
}
a{
    color: black;
    text-decoration: none;
    padding: 6px 8px;
    border-radius: 10px;
}
nav{
    background: orchid;
    padding: 14px 0;
    margin-bottom: 40px;
}
.router-link-active{
    background:palegoldenrod;
    color: orchid;
}
</style>
