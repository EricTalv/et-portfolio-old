<template >
<!--  <div id="canvas" class="mt-16 flex flex-col items-center"></div>-->

  <div class="canvasContainer flex flex-col items-center" >
    <canvas id="mainCanvas"></canvas>
  </div>

</template>

<script>
import  * as THREE from 'three';
export default {
  name: "Sphere.vue",

  mounted() {

    // Sphere Animation
    let camera, scene, renderer;
    let mesh;

    init();

    function init() {


      //  renderer.setSize(window.innerWidth / 2, window.innerHeight / 2);
      // container.appendChild(renderer.domElement);

      // Fetch canvas element
      var canvas = document.querySelector( '#mainCanvas' );

      // Render into canvas element
      var renderer = new THREE.WebGLRenderer({canvas});

      // Camera settings
      const fov = 45;
      const aspect = window.innerWidth / window.innerHeight;
      const near = 0.1;
      const far = 1000;

      // Create perpsective Camera
      var camera = new THREE.PerspectiveCamera(fov, aspect, near, far);

      // Set camera position
      camera.position.z = 150;

      // Create a scene, things will be drawn here
      var scene = new THREE.Scene();

      // Sphere geometry details
      var radius = 50;
      var segments = 15;
      var rings = 15;

      // Create the sphere
      var geometry = new THREE.SphereGeometry(radius, segments, rings);

      // Specify the spheres material
      var material = new THREE.MeshBasicMaterial({
        color: 0xe6e6e6,
        wireframe: true
      });

      // Create the Mesh
      var sphere = new THREE.Mesh(geometry, material);
      scene.add(sphere);


      var render = function() {
        requestAnimationFrame(render);

        // Update canvas size
        if (resizeRendererToDisplaySize(renderer)) {
          const canvas = renderer.domElement;
          camera.aspect = canvas.clientWidth / canvas.clientHeight;
          camera.updateProjectionMatrix();
        }

        // This will set the sphere into the correct aspect regardless of window size
        const canvas = renderer.domElement;
        camera.aspect = canvas.clientWidth / canvas.clientHeight;
        camera.updateProjectionMatrix();


        sphere.rotation.x += 0.0040;
        sphere.rotation.y += 0.0040;

        renderer.render(scene, camera);
      };

      render();
    }

    // a function that checks if the renderer's canvas is
    // not already the size it is being displayed as and if so set its size
    function resizeRendererToDisplaySize(renderer) {
      const canvas = renderer.domElement;
      const width = canvas.clientWidth;
      const height = canvas.clientHeight;
      const needResize = canvas.width !== width || canvas.height !== height;
      if (needResize) {
        renderer.setSize(width, height, false);
      }
      return needResize;
    }

    function animation( time ) {

      mesh.rotation.x = time / 2000;
      mesh.rotation.y = time / 1000;

      renderer.render( scene, camera );
    }
  }
}
</script>


<style>
 #mainCanvas {
   width: 80%;

 }

 @media (max-width: 540px) {
    #mainCanvas {
      width: 110%;
    }
 }
</style>
