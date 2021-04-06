<template>
<div class="postList">
    <div class="posts" v-if="!foundItem">
        <div class="post" v-for="post in posts" :key="post.id" @click="selectPost(post)">
            <div class="info">
                <h2>{{post.title}}</h2>
                <p>Posted on {{post.date}}, at {{post.time}}</p>
            </div>
        </div>
    </div>
    <div class="singlePost" v-else>
        <div class="postInfo" @click="deselectPost">
            <h2>{{foundItem.title}}</h2>
            <div class="postBody" v-for="para in foundItem.paragraphs" :key="para">
                <p>{{para}}</p>
            </div>
            <p>Posted on {{foundItem.date}}, at {{foundItem.time}}</p>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'PostList',
    props: {
        posts: Array
    },
    data(){
        return {
            foundItem: null,
        }
    },
    methods: {
        selectPost(post) {
            this.foundItem = post;

        },
        deselectPost () {
            this.foundItem = null;
        }
    }
}
</script>
