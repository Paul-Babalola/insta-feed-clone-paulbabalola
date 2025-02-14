<template>
    <aside class="right">
      <!-- Profile Section -->
      <div class="flex items-center justify-between">
        <div class="profilewhole">
          <img src="../assets/pb.jpg" alt="Profile" class="profile">
          <div class="profileinfo">
            <p class="username">Johnny Storm</p>
            <p class="name">Jstorm</p>
          </div>
        </div>
      </div>
  
      <!-- Suggested for You -->
      <div class="mt-5">
        <div class="suggest">
          <p class="suggestions">Suggestions For You</p>
          <button class="button2">See All</button>
        </div>
        <div v-for="(user, index) in suggestedUsers" :key="index" class="flex items-center justify-between mt-3">
          <div class="profilewholey">
            <img :src="user.image" alt="User" class="profile">
            <div class="profileinfos">
              <p class="username">{{ user.username }}</p>
              <p class="name">{{ user.mutual }} mutual friends</p>
            </div>
            <button class="button">Follow</button>
          </div>
        </div>
      </div>
  
      <!-- Trending Hashtags -->
      <!-- <div class="mt-6">
        <p class="text-gray-500 text-sm font-semibold">Trending Hashtags</p>
        <ul class="mt-2">
          <li v-for="(hashtag, index) in trendingHashtags" :key="index" class="text-blue-500 text-sm cursor-pointer hover:underline">
            #{{ hashtag }}
          </li>
        </ul>
      </div> -->
  
      <!-- Footer Links -->
      <div class="footer">
        <p class="mb-1">About • Help • Press • API • Jobs • Privacy • Terms</p>
        <p>© 2025 Instagram from Meta</p>
      </div>
    </aside>
  </template>
  
  <script>
  export default {
    name: "InstagramSidebar",
    data() {
      return {
        suggestedUsers: [
          { username: "alex_doe", mutual: 12, image: require("@/assets/8888433.jpg")  },
          { username: "emma_123", mutual: 8, image: require("@/assets/pic.jpg")  },
          { username: "johnny_b", mutual: 5, image: require("@/assets/tree.jpg")  }
        ],
        trendingHashtags: ["VueJS", "WebDev", "Design", "CodingLife"]
      };
    }
  };
  </script>
  
  <style scoped>
  .right {
    position: fixed;
    top: 13%;
    right: 3%;
    background-color: #f9f9f9;
    padding: 1rem;
    height: 60vh;
    width: 300px;
    overflow-y: auto;
    border-radius: 0px;
  }
  .profilewhole{
    display: flex;
    align-items: center;
    }
    
    .profilewholey{
        display: flex;
        align-items: center;
        justify-content: space-evenly;
    }
    
    .profile {
        height: 50px;
        width: 50px;
        border-radius: 50%;
    }

    .profileinfo{
        margin-left: 1rem;
        display: inline;
    }

    .suggest{
        display: flex;
        justify-content: space-between;
    }
    .button2{
        font-size: 0.7rem;
        font-weight: 200;
        margin-top: 0.7rem;
        background-color: #f9f9f9;
        color: #000000;
        border: none;
        height: 1.5rem;
        padding: 0.3rem 0.5rem;
        border-radius: 5px;
        cursor: pointer;
        margin-left: 1rem;
        display: inline-flex;
    }
    .suggestions{
        color: gray;
        font-size: 0.9rem;
        font-weight: 200;
    }

    .username{
        font-size: 1rem;
        font-weight: 600;

    }
    .name{
        margin-top: -0.8rem;
        font-size: 0.8rem;
        color: gray;
    }

    .button{
        background-color: white;
        color: #0095f6;
        border: none;
        padding: 0.3rem 0.5rem;
        border-radius: 5px;
        cursor: pointer;
        margin-left: 1rem;
        display: inline-flex;
    }

.footer{
    margin-top: 1rem;
    color: gray;
    font-size: 0.8rem;
    font-weight: 200;
}

@media screen and (max-width: 1024px) {
  .right {
    width: 250px;
    right: 2%;
  }
}

@media screen and (max-width: 768px) {
  .right {
    position: static;
    width: 100%;
    height: auto;
    background-color: white;
    padding: 1rem;
    border-top: 1px solid #dbdbdb;
    visibility: hidden;
  }
  
  .profilewhole {
    justify-content: center;
  }

  .profilewholey {
    justify-content: space-between;
    width: 100%;
  }

  .button {
    margin-left: auto;
  }

  .footer {
    text-align: center;
    margin-top: 1.5rem;
  }
}

@media screen and (max-width: 425px) {
  .right {
    padding: 0.5rem;
  }

  .profile {
    height: 40px;
    width: 40px;
  }

  .username {
    font-size: 0.9rem;
  }

  .name {
    font-size: 0.7rem;
  }

  .button {
    padding: 0.2rem 0.4rem;
    font-size: 0.8rem;
  }

  .button2 {
    padding: 0.2rem 0.4rem;
    font-size: 0.7rem;
  }

  .suggestions {
    font-size: 0.8rem;
  }
}

@media screen and (max-width: 375px) {
  .right {
    padding: 0.5rem;
  }

  .profileinfo {
    margin-left: 0.5rem;
  }

  .profilewholey {
    flex-wrap: wrap;
    justify-content: center;
    text-align: center;
  }

  .button {
    margin-top: 0.5rem;
  }

  .footer {
    font-size: 0.7rem;
  }
}


  </style>
  