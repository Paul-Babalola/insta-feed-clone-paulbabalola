<template>
    <header class="top">
      <!-- Instagram Logo -->
      <div class="logo"><img src="../assets/logo.png"></div>
      
      <!-- Search Bar -->
      <div class="relative">
        <input 
          type="text" 
          placeholder="Search" 
          class="search"
        />
      </div>
      
      <!-- Navigation Icons -->
      <div class="right">
  <font-awesome-icon :icon="['fas', 'home']" class="icons" />
  <i class="far fa-paper-plane text-xl cursor-pointer icons"></i>
  <!-- <i class="far fa-compass text-xl cursor-pointer icons"></i> -->

  <!-- Boxed Cross Icon -->
  <i class="far fa-plus-square text-xl cursor-pointer icons"></i>


  <i class="far fa-heart text-xl cursor-pointer icons"></i>
  <img src="../assets/pb.jpg" class="profile" alt="Profile" />
</div>

    </header>
  </template>

<style scoped>
.top {
  position: fixed;
  top: 0;
  width: 79%;
  z-index: 1000;
  background-color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0rem 8rem;
  border-bottom: 1px solid #dbdbdb;
  margin-bottom: 90rem;
}

.logo img {
  height: 60px;
  cursor: pointer;
}

.search {
  padding: 0.3rem;
  border-radius: 5px;
  border: 1px solid #dbdbdb;
  width: 250px;
}

.icons {
  font-size: 1.5rem;
  color: #262626;
  margin-right: 1rem;
  cursor: pointer;
}

.profile {
  height: 30px;
  width: 30px;
  border-radius: 50%;
  cursor: pointer;
}

.right {
  margin-right: -4rem;
  display: flex;
  align-items: center;
justify-content: space-between;
}

@media (max-width: 1024px) {
  .top {
    padding: 0.5rem 7rem;
  }
  .search {
    margin-left: -40%;
    width: 170px;
  }
  .logo img {
    margin-left: -80%;
    height: 50px;
  }
  .icons {
    font-size: 1rem;
  }
.right {
    margin-right: -3rem;
  }
}

/* Small Tablets & Large Phones */
@media (max-width: 768px) {
  .top {
    padding: 0.5rem 5rem;
  }
  .logo img {
    height: 50px;
  }
  .search {
    width: 150px;
  }
  .icons {
    font-size: 1rem;
  }
  .profile {
    height: 30px;
    width: 30px;
  }
  .right {
    margin-right: -0rem;
  }

}

/* Small Phones (Portrait Mode) */
@media (max-width: 480px) {
  .top {
    padding: 0.5rem 2.4rem;
  }
  .logo img {
    margin-left: 0.2rem;
    height: 50px;
  }
  .search {
    visibility: hidden;
    margin-left: 1rem;
    width: 120px;
  }
  .profile {
    margin-left: -10rem;
    height: 28px;
    width: 28px;
  }
  .icons {
    visibility: hidden;
    font-size: 1.2rem;
  }
}

/* Extra Small Phones */
@media (max-width: 375px) {
  .top {
    padding: 0.5rem 2.2rem;
  }
  .search {
    width: 100px;
  }
  .icons {
    visibility: hidden;
    font-size: 1rem;
  }
  .profile {
    height: 28px;
    width: 28px;
  }
}

</style>