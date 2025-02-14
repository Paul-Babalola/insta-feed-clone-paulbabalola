<template>
    <div>
      <div v-for="(post, index) in posts" :key="index" class="body">
        <!-- Post Header -->
        <div class="profile">
          <div class="profileinfo">
            <img :src="post.userImage" alt="Profile" class="pimage" />
            <div>
              <p class="username">{{ post.username }}</p>
              <p class="location">{{ post.location }}</p>
            </div>
          </div>
          <i class="fas fa-ellipsis-h cursor-pointer text-gray-500 icon"></i>
        </div>
  
        <!-- Post Image -->
        <img :src="post.image" alt="Post Image" class="image" loading="lazy" />
  
        <!-- Actions -->
        <div class="icons">
          <div class="iconic">
            <i 
              :class="post.liked ? 'fas fa-heart text-red-500' : 'far fa-heart'" 
              class="text-2xl cursor-pointer icon1"
              @click="toggleLike(index)"
            ></i>
            <i class="far fa-comment text-2xl cursor-pointer icon2" @click="toggleComments(index)"></i>
            <i class="far fa-paper-plane text-2xl cursor-pointer icon3"></i>
          </div>
          <i class="far fa-bookmark text-2xl cursor-pointer"></i>
        </div>
  
        <!-- Likes -->
        <p class="likes">{{ post.likes }} likes</p>
  
        <!-- Caption -->
        <div class="caption">
          <p class="captiontext">
            <span class="captioninfo">{{ post.username }}</span> {{ post.caption }}
          </p>
          <p v-if="post.comments.length" class="viewcomments" @click="toggleComments(index)">
            View all {{ post.comments.length }} comments
          </p>
        </div>
  
        <!-- Comments -->
        <div v-if="post.showComments" class="comments-section">
          <div v-for="(comment, idx) in post.comments" :key="idx" class="comment">
            <span class="font-semibold">{{ comment.username }}</span> {{ comment.comment }}
          </div>
        </div>
  
        <!-- Add Comment -->
        <div class="addcomment">
          <i class="far fa-smile text-xl text-gray-500 icon5"></i>
          <input type="text" v-model="newComment[index]" placeholder="Add a comment..." class="commenttext" />
          <div class="post" @click="addComment(index)">Post</div>
        </div>
      </div>
      
      <div ref="scrollTrigger" class="loading">Loading more posts...</div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        posts: [
          {
            userImage: require("@/assets/pb.jpg"),
            username: "Johnny Storm",
            location: "Lagos, Nigeria",
            image: require("@/assets/hp.png"),
            likes: 120,
            caption: "Loving the vibes!",
            comments: [
              { username: "Judy123", comment: "Nice shot!" },
              { username: "johnny_b", comment: "Awesome!" }
            ],
            liked: false,
            showComments: false,
          }
        ],
        newComment: [],
      };
    },
    methods: {
      toggleLike(index) {
        const post = this.posts[index];
        post.liked = !post.liked;
        post.likes += post.liked ? 1 : -1;
      },
      toggleComments(index) {
        this.posts[index].showComments = !this.posts[index].showComments;
      },
      addComment(index) {
        if (this.newComment[index]?.trim()) {
          this.posts[index].comments.push({ username: "Johnny Storm", comment: this.newComment[index] });
          this.newComment[index] = "";
        }
      },
      loadMorePosts() {
        setTimeout(() => {
          this.posts.push({
            userImage: require("@/assets/pic.jpg"),
            username: "Ryan Reynolds",
            location: "Abuja, Nigeria",
            image: require("@/assets/hp.png"),
            likes: 950,
            caption: "Another great day!",
            comments: [],
            liked: false,
            showComments: false,
          });
        }, 1000);
      }
    },
    mounted() {
      const observer = new IntersectionObserver((entries) => {
        if (entries[0].isIntersecting) {
          this.loadMorePosts();
        }
      });
      observer.observe(this.$refs.scrollTrigger);
    }
  };
  </script>
  
  <style scoped>
  .body {
    position: relative;
      background-color: #fff;
      border: 1px solid #dbdbdb;
      margin-top: 6rem;
      margin-left: 7rem;
      width: 45rem;
      padding: auto;
  }

  .profile {
      padding: 1rem 2rem;
      display: flex;
      align-items: center;
  }

  .profileinfo {
    cursor: pointer;
      display: flex;
      align-items: center;
  }

  .pimage {
      height: 40px;
      width: 40px;
      border-radius: 50%;
      margin-right: 1rem;
  }

  .username {
      margin-top: 0.2rem;
      font-weight: 600;
  }

  .location {
      margin-top: -0.8rem;
      font-size: 0.8rem;
      color: #8e8e8e;
  }

  .icon {
      font-size: 1.2rem;
      margin-left: auto;
      margin-top: -1rem;
      cursor: pointer;
  }

  .image {
      width: 100%;
      height: 100%;
  }
  
  .icons {
      display: flex;
      padding: 0rem 1rem;
      justify-content: space-between;
      font-size: 1.5rem;
      cursor: pointer;
  }

  .iconic {
      display: flex;
      size: 80%;
      margin-bottom: 1rem;
  }

  .icon1, .icon2, .icon3 {
      margin-right: 0.8rem;
  }

  .likes {
      font-weight: 600;
      padding: 0rem 1rem;
      cursor: pointer;
  }

  .caption {
      padding: 0rem 1rem;
  }

  .captiontext {
      font-weight: 300;
      margin-top: 0.5rem;
  }

  .captioninfo {
      font-weight: 600;
      cursor: pointer;
  }

  .viewcomments {
      color: #8e8e8e;
      margin-top: 0.5rem;
      cursor: pointer;
  }

    .comments-section {
        padding: 0rem 1rem;
        margin-bottom: 1rem;
    }

    .font-semibold {
  font-weight: bold;
  margin-right: 0.5rem;
  cursor: pointer;
}
    
    
  .addcomment {
      padding: 0rem 1rem;
      display: flex;
      align-items: center;
      margin-bottom: 1rem;
  }

  .commenttext {
      border: none;
      padding: 0.5rem;
      width: 100%;
      font-size: 1rem;
  }

  .post {
      color: #0095f6;
      font-weight: 500;
      cursor: pointer;
  }

  .icon5 {
      margin-right: 0.5rem;
      font-size: 1.5rem;
      cursor: pointer;
  }

  .loading {
  text-align: center;
  padding: 1rem;
  color: gray;
}


@keyframes pop {
  0% { transform: scale(1); }
  50% { transform: scale(1.2); }
  100% { transform: scale(1); }
}

.animate-pop {
  animation: pop 0.3s ease-in-out;
}

.text-red-500 {
  color: red;
}

@media screen and (max-width: 1024px) {
  .body {
    width: 60%;
    margin: 6rem 1rem;
  }

  .profile {
    padding: 1rem;
  }

  .icons {
    padding: 0.5rem;
  }

  .commenttext {
    font-size: 0.9rem;
  }
}

@media screen and (max-width: 768px) {
  .body {
    width: 95%;
    margin: 6rem 1rem;
  }

  .pimage {
    height: 35px;
    width: 35px;
  }

  .username {
    font-size: 0.9rem;
  }

  .location {
    font-size: 0.7rem;
  }

  .icon {
    font-size: 1rem;
  }

  .icons {
    font-size: 1.3rem;
  }

  .iconic {
    margin-bottom: 0.5rem;
  }

  .likes,
  .caption,
  .viewcomments {
    font-size: 0.9rem;
  }

  .commenttext {
    font-size: 0.85rem;
  }

  .post {
    font-size: 0.9rem;
  }
}

@media screen and (max-width: 480px) {
  .body {
    width: 100%;
    margin: 2rem auto;
  }

  .profile {
    padding: 0.8rem;
  }

  .pimage {
    height: 30px;
    width: 30px;
    margin-right: 0.5rem;
  }

  .username {
    font-size: 0.85rem;
  }

  .location {
    font-size: 0.7rem;
  }

  .icon {
    font-size: 0.9rem;
  }

  .icons {
    font-size: 1.2rem;
  }

  .iconic {
    margin-bottom: 0.3rem;
  }

  .likes,
  .caption,
  .viewcomments {
    font-size: 0.85rem;
  }

  .commenttext {
    font-size: 0.8rem;
  }

  .post {
    font-size: 0.85rem;
  }
}



</style>  