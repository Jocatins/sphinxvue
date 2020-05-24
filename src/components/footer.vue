<template>
    <div>
        <footer>
        <p>{{ copyright }}</p>
        </footer>
    </div>
</template>
<script>

export default {
    data(){
        return{
            copyright: 'Copyright 2046 @titanSpace Explorations'
        }
    }
}
</script>

<style scoped>
footer{
    background: #222;
    padding: 6px;
}
p{
    color: #eee;
    text-align: center;
}
</style>