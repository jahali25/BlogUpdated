<template>
<div class="posts">
    <div class="post" v-for="post in posts" :key="post.id">
        <div class="info">
            <h2>{{post.title}}</h2>
            <p>Posted on {{post.date}}, at {{post.time}}</p>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'PostList',
    props: {
        posts: Array
    }
}
</script>
