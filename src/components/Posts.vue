<template>
  <div>
      <ul>
          <div v-for="post in posts" :key="post.id">
              <div v-if="post.id%2 != '0' ">
                <li>
                    <p><strong>Id: </strong> {{ post.id }}</p>
                    <p><strong>UserId: </strong> {{ post.userId }}</p>
                    <p><strong>Title: </strong> {{ post.title }}</p>
                    <p><strong>Body: </strong> {{ post.body}}</p>
                    </li>
             </div>
          </div>
      </ul>
      <button @click="triggerFetch">Posts</button>
 </div>
</template>

<script>
export default 
{ 
    name: "Posts",
    data() {
        return {
            posts: [],
            users: [],
            comments: [],
            postURI: "https://jsonplaceholder.typicode.com/posts",
            userURI: "https://jsonplaceholder.typicode.com/users",
            commentsURI: "https://jsonplaceholder.typicode.com/comments" 
            };
        },
        methods: {
            fetchPosts: function() {
                this.$http.get(this.postURI).then((result) => {
                    this.posts = result.data;    
                    console.log(this.posts)
                });
            },
            fetchUser: function(){
                this.$http.get(this.userURI).then((result) => {
                    console.log(result.data);
                })
            },
            fetchComments: function(){
                this.$http.get(this.commentsURI).then((result) => {
                    console.log(result.data);
                })
            },
            triggerFetch: function(){
                this.fetchPosts()
                this.fetchUser()
                this.fetchComments()
                
            }
        },
};
</script>

<style>

</style>