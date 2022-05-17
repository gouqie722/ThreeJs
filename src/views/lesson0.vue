<template>
  <div class="lesson0"></div>
</template>

<script>
import { onMounted } from '@vue/runtime-core'
import {
  PerspectiveCamera,
  Scene,
  WebGLRenderer,
  BoxGeometry,
  MeshBasicMaterial,
  Mesh,
} from 'three';
export default {
  setup() {
    function init() {
      var scene = new Scene();
      var camera = new PerspectiveCamera(75, window.innerWidth / window.innerHeight, 1, 1000);
      var renderer = new WebGLRenderer();
      renderer.setSize(window.innerWidth, window.innerHeight);
      document.getElementsByClassName('lesson0')[0].appendChild(renderer.domElement);
      console.log(camera, scene);
      var geometry = new BoxGeometry()
      var material = new MeshBasicMaterial({ color: 0x002299 });
      var cube = new Mesh(geometry, material);
      scene.add(cube);
      camera.position.z = 5;
      cube.rotation.x += 0.5;
      cube.rotation.y += 0.5;
      // cube.rotation.z += 0.1;
      renderer.render(scene, camera);
    }
    onMounted(() => {
      init()
    })
  }
}
</script>

<style>

</style>