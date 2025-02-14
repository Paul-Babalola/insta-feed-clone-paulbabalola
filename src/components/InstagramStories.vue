<template>
    <div>
      <!-- Instagram Stories -->
      <div class="stories-container">
        <div class="stories">
          <div v-for="(story, index) in stories" :key="index" class="story">
            <img :src="story.userImage" alt="Story" class="story-image" @click="viewStory(story)" />
            <p class="story-username">{{ story.username }}</p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        stories: [
          { userImage: require("@/assets/pb.jpg"), username: "Johnny" },
          { userImage: require("@/assets/pic.jpg"), username: "Ryan" },
          { userImage: require("@/assets/pb.jpg"), username: "Emily" },
          { userImage: require("@/assets/pic.jpg"), username: "James" }
        ]
      };
    },
    methods: {
      viewStory(story) {
        console.log(`Viewing ${story.username}'s story`); // You can later replace this with a modal
      }
    }
  };
  </script>
  
  <style scoped>
  /* Instagram Stories Section */
  .stories-container {
    margin-top: 6rem;
    margin-bottom: -4rem;
    display: flex;
    background-color: #fff;
      border: 1px solid #dbdbdb;
      width: 45rem;
    justify-content: center;
    margin-left: 7rem;
    align-content: center;
  }
  
  .stories {
    display: flex;
    overflow-x: auto;
    margin-top: 1rem;
    white-space: nowrap;
    gap: 10px;
    width: 80%;
    padding-bottom: 10px;
    scroll-snap-type: x mandatory;
    -webkit-overflow-scrolling: touch;
  }
  
  .story {
    text-align: center;
    cursor: pointer;
    scroll-snap-align: start;
  }
  
  .story-image {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    border: 3px solid red;
    padding: 3px;
    transition: transform 0.3s ease-in-out;
  }
  
  .story-image:hover {
    transform: scale(1.1);
  }
  
  .story-username {
    font-size: 0.8rem;
    margin-top: 5px;
  }
  
  @media screen and (max-width: 1024px) {
    .stories-container {
        width: 60%;
        margin: 6rem 1rem;
        margin-bottom: -4rem;
        }
    
    .stories {
      width: 80%;
    }
  
    .story-image {
      width: 50px;
      height: 50px;
    }
  }

  /* Responsive Design */
  @media screen and (max-width: 768px) {
    .stories {
      width: 80%;
    }

    .stories-container{
        width: 95%;
    margin: 6rem 1rem;
    margin-bottom: -4rem;
    }
  
    .story-image {
      width: 50px;
      height: 50px;
    }
  }
  
  @media screen and (max-width: 480px) {

    .stories-container{
        width: 100%;
    margin: 2rem auto;
    margin-top: 4rem;
  }

    .stories {
      width: 80%;
    }
  
    .story-image {
      width: 45px;
      height: 45px;
    }
  
    .story-username {
      font-size: 0.7rem;
    }
  }
  </style>
  