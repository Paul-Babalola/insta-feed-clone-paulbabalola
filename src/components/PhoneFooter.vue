<template>
<div class="top">
        <div class="right">
  <font-awesome-icon :icon="['fas', 'home']" class="icons" />
  <i class="far fa-paper-plane text-xl cursor-pointer icons"></i>
  <i class="far fa-plus-square text-xl cursor-pointer icons"></i>

  <i class="far fa-compass text-xl cursor-pointer icons"></i>

  <!-- Boxed Cross Icon -->


  <i class="far fa-heart text-xl cursor-pointer icons"></i>
  <!-- <img src="../assets/pb.jpg" class="profile" alt="Profile" /> -->
</div>
</div>
</template>

<style scoped>
.top {
  position: fixed;
  top: 0;
  width: 100%;
  height: 1%;
  z-index: 1000;
  background-color: white;
  display: flex;
  align-items: center;
  padding: 1.2rem 1rem;
  border-bottom: 1px solid #dbdbdb;
  margin-top: 194%;
  visibility: hidden;
}


.icons {
    
  font-size: 1.5rem;
  color: #262626;
  cursor: pointer;
}

.right {
    margin-left: 0.7rem;
  display: flex;
justify-content: space-evenly;
  width: 80%;
}

@media (min-width: 376px) and (max-width: 480px) {
  .top {
    visibility: visible;
  }

  
}

@media (max-width: 375px) {
  .top {
    visibility: visible;
  }

}


</style>