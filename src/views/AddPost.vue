<template>
<div class="addPage">
    <h1>Blog Post</h1>
    <p>This is the page to add blog posts</p>
    <div class="add">
        <div class="form">
            <input v-model="title" placeholder="Title of the blog post">
            <p></p>
            <input type="file" name="photo" @change="fileChanged">
            <p></p>
            <button @click="upload">Upload</button>
            <p>Note, the </p>
            <textarea class = "post" name="Post" v-model="post"
            placeholder="Type the blog post here"> </textarea>

          </div>
          <!-- <div class="upload" v-if="addItem">
            <h2>{{addItem.title}}</h2>
            <img :src="addItem.path" />
            <p>{{addItem.description}}</p>
        </div> -->
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
                file: null,
                items: [],
            }
        },
        computed: {

        },
        created() {
            this.getItems();
        },
        methods: {
            fileChanged(event) {
              this.file = event.target.files[0];
              console.log(this.file);
            },
            getItems() {
                this.items = this.$root.$data.posts;
            },
            upload() {
                const ids = this.items.map((item) => {
                    return item.id;
                });
                let maxId = Math.max(...ids);
                console.log(this.file);
                //let myActiveObject = new ActiveXObject("Scripting.FileSystemObject");
                //let file = myActiveObject.GetFile(this.file);
                let file = this.file;
                console.log(typeof(file));
                //let filename = file.name;
                //new FileUpload(file, '/images/' + filename);
                maxId += 1;
                let newPost = {
                    id: maxId,
                    title: this.title,
                    image: file,
                    paragraphs: [this.post],
                    date: "January 1, 1996",
                    time: "1:00 AM",
                };
                console.log(newPost);
                this.$root.$data.posts.push(newPost);
                this.getItems();

            }
        },

    }
</script>
