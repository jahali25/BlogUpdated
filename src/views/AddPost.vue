<template>
<div class="addPage">
    <h1>Blog Post</h1>
    <p>This is the page to add blog posts</p>
    <div class="add">
        <div class="form">
            <input v-model="title" placeholder="Title of the blog post" @change="postChanged">
            <p></p>
            <input v-model="date" placeholder="Date of the blog post" @change="postChanged">
            <p></p>
            <input v-model="time" placeholder="Time of the blog post" @change="postChanged">
            <p></p>
            <button @click="upload">Upload</button>
            <textarea class = "post" name="Post" v-model="post"
            placeholder="Type the blog post here" @change="postChanged"> </textarea>

        </div>
    </div>
    <div class="submitted" v-if="beenPosted">
        <h2>Congrats! We posted your post</h2>
    </div>

</div>
</template>

<script>
    export default {
        name: 'AddPost',
        data() {
            return {
                title: "",
                post: "",
                items: [],
                date: "",
                time: "",
                beenPosted: false,
            }
        },
        computed: {

        },
        created() {
            this.getItems();
        },
        methods: {
            postChanged() {
                if (this.beenPosted) {
                    this.beenPosted = false;
                }
            },
            getItems() {
                this.items = this.$root.$data.posts;
            },
            upload() {
                const ids = this.items.map((item) => {
                    return item.id;
                });
                let maxId = Math.max(...ids);
                maxId += 1;
                let newPost = {
                    id: maxId,
                    title: this.title,
                    paragraphs: [this.post],
                    date: this.date,
                    time: this.time,
                };
                console.log(newPost);
                this.$root.$data.posts.push(newPost);
                this.getItems();
                this.title = '';
                this.post = '';
                this.beenPosted = true;
            }
        },

    }
</script>
