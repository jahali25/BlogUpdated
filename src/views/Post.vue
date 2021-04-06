<template>
<div class="post">
    <div class="find">
      <div class="form">
        <input v-model="findTitle" placeholder="Search">
        <div class="suggestions" v-if="suggestions.length > 0">
          <div class="suggestion" v-for="s in suggestions" :key="s.id" @click="selectItem(s)">
            {{s.title}}
          </div>
        </div>
      </div>
    </div>
    <div class="display" v-if="findItem">
    <div class="info">
            <h2>{{findItem.title}}</h2>
            <img :src="getImage(findItem)" />
            <p>{{findItem.paragraphs}}</p>
            <p>Posted on {{findItem.date}}, at {{findItem.time}}</p>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'Post',
    data() {
        return {
          posts: [],
          findTitle: '',
          findItem: null,
        }
    },
    computed: {
      suggestions() {
        let posts = this.posts.filter(item => item.title.toLowerCase().startsWith(this.findTitle.toLowerCase()));

        return posts.sort((a, b) => a.title > b.title);
      }
    },
    created() {
      this.posts = this.$root.$data.posts;
    },
    methods: {
      selectItem(item) {
        this.findTitle = "";
        this.findItem = item;
      },
      getImage(item) {
        if (typeof(item.image) == "string") {
          return "/images/" + item.image;
        }
        return item.image;
      }
    }
}
</script>

<style scoped>
/* Suggestions */
.suggestions {
  width: 200px;
  border: 1px solid #ccc;
}

.suggestion {
  min-height: 20px;
}

.suggestion:hover {
  background-color: #5BDEFF;
  color: #fff;
}
</style>
