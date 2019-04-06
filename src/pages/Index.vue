<template>
  <Layout :background="$page.allBlogPost.edges[inx].node.image">
    <h1>{{$page.allBlogPost.edges[inx].node.title}}</h1>
    <div v-html="$page.allBlogPost.edges[inx].node.content" />
  </Layout>

</template>

<page-query>
  query Post {
    allBlogPost (sortBy: "index", order: ASC){
      edges {
        node {
          title
          content
          image
        }
      }
    }
  }
</page-query>


<script>
    export default {
        name: "Home",
        data: function () {
            return {
                inx: 0
            }
        },
    }
</script>

<style scoped>

</style>