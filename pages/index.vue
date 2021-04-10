<template>
  <div class="container">
    <div id="canvas" class="mt-16 flex flex-col items-center"></div>

   <div class="intro flex flex-col items-center">
     <div class="paragraph-container">
       <p class="intro-text">
         I am Eric Talviste
       </p>
       <p class="intro-text">
         I develop websites, music and create digital art.
       </p>
     </div>
   </div>
  </div>
</template>

<script>

import baffle from 'baffle';
import  * as THREE from 'three';

export default {

  mounted() {


    // Baffle Animation
    let b = baffle('.intro-text');

    b.reveal(1500);

    // Sphere Animation
    let camera, scene, renderer;
    let geometry, material, mesh;

    init();

    function init() {
      var scene = new THREE.Scene();
      var camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 1000);

      var container = document.getElementById( 'canvas' );

      var renderer = new THREE.WebGLRenderer();
      renderer.setSize(window.innerWidth / 2, window.innerHeight / 2);
      container.appendChild(renderer.domElement);

      var radius = 50;
      var segments = 15;
      var rings = 15;

      var geometry = new THREE.SphereGeometry(radius, segments, rings);
      var material = new THREE.MeshBasicMaterial({
        color: 0xe6e6e6,
        wireframe: true
      });

      var cube = new THREE.Mesh(geometry, material);
      scene.add(cube);

      camera.position.z = 150;

      var render = function() {
        requestAnimationFrame(render);

        cube.rotation.x += 0.0050;
        cube.rotation.y += 0.0050;

        renderer.render(scene, camera);
      };

      render();

    }

    function animation( time ) {

      mesh.rotation.x = time / 2000;
      mesh.rotation.y = time / 1000;

      renderer.render( scene, camera );

    }
  }

}
</script>


<style lang="scss">
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

  .mybutton {
    &:hover {
      background-color: red;
    }
  }

</style>
