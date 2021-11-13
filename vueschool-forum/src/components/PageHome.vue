<template>
    <div>Howdy</div>
    <div v-for="thread in threads" v-bind:key="thread.id">
        <h2>{{ thread.title }}</h2>
        <div v-for="postId in thread.posts" :key="postId">
            <p>{{ getUser(getPost(postId).userId).name }}</p>
            <p>{{ getPost(postId).text }}</p>
        </div>
    </div>
</template>

<script>
import sourceData from '@/data.json';

export default {
    data() {
        return {
            threads: sourceData.threads,
            posts: sourceData.posts,
            users: sourceData.users,
        };
    },
    methods: {
        getPost(postId) {
            const post = this.posts.find((p) => p.id === postId);
            return post;
        },
        getUser(userId) {
            return this.users.find((u) => u.id === userId);
        },
    },
};
</script>
