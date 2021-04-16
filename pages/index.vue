<template>
  <div class="content-container container mx-auto h-screen" >
<!--    Welcome Section start -->
  <sphere></sphere>
   <div class="flex flex-col items-center">
     <div class="intro-container p-7 text-xs sm:text-sm md:text-base">
         <small class="intro-text text-gray-600">
           <p>
              Estonia, Tallinn
           </p>
         </small>
       <p class="intro-text">
         I am Eric Talviste.
       </p>
       <p class="intro-text">
         I develop websites, music and create digital art.
       </p>
       <hr class="my-3">
       <div class="nav flex justify-between">
         <a href="">
           <p class="nav-item text-gray-800">
             portfolio
           </p>
         </a>
         <a href="">
           <p class="nav-item text-gray-800">
             about
           </p>
         </a>
         <a href="">
           <p class="nav-item text-gray-800">
             contact
           </p>
         </a>
       </div>
     </div>
   </div>
    <!--    Welcome Section End -->

  </div>
</template>

<script>

import baffle from 'baffle';

export default {

  mounted() {

    // Baffle Animation
    let introText = baffle('.intro-text');
    introText.reveal(1000);

    let navItem = baffle('.nav-item');
    navItem.reveal(3500);

  }

}
</script>


<style lang="scss">
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
  .nav {
    a {
      p {
        transition: all .5s;
        &:hover {
          color: whitesmoke;
        }
      }
    }
  }

</style>
