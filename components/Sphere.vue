<template>
  <div id="canvas" class="mt-16 flex flex-col items-center"></div>
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

        cube.rotation.x += 0.0040;
        cube.rotation.y += 0.0040;

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

