<template>
    <div class="container mt-3">
        <div>
            <div class="row">
                <div class="col-12">
                    <h1 class="float-left">#{{ $route.params.id }}</h1>
                    <nuxt-link to="/hashtag" class="button--grey float-right">Back</nuxt-link>
                </div>
            </div>
            <div class="row">
                <Card v-for="post in posts" :key="post.id" :post="post" />
            </div>
        </div>
    </div>
</template>

<script>
import axios from '@nuxtjs/axios'
import Card from '@/components/Card'

export default {
    components: {
        Card
    },
    data() {
        return {
            route: this.$nuxt.$route.params.id,
            posts: [],
        }
    },

    async asyncData({ $axios, route }) {
        let {data} = await $axios.get(`https://www.instagram.com/explore/tags/${route.params.id}/?__a=1`)

        return {posts: data.graphql.hashtag.edge_hashtag_to_media.edges}
    },
    head() {
        return {
            title: `#${this.route}`
        }
    }
}
</script>
