<template>
    <Layout>
        <g-image :src="$page.blogPost.image"/>
        <h1>{{$page.blogPost.title}}</h1>
        <div v-html="$page.blogPost.content" />
    </Layout>

</template>

<page-query>
    query Post ($path: String!) {
        blogPost(path: $path){
            title
            content
            image
        }
    }
</page-query>

<script>
    export default {
        name: "Post"
    }
</script>

<style scoped>

</style>