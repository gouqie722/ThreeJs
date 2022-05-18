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
  AxesHelper,
  PlaneGeometry,
  MeshLambertMaterial,
} from 'three';
export default {
  setup() {
    function init() {
      var scene = new Scene();
      var camera = new PerspectiveCamera(75, window.innerWidth / window.innerHeight, 1, 1000);
      var renderer = new WebGLRenderer();
      renderer.setSize(window.innerWidth, window.innerHeight);
      document.getElementsByClassName('lesson0')[0].appendChild(renderer.domElement);
      // 创建一个三维坐标轴
      var axes = new AxesHelper(50);
      // 修改坐标轴颜色
      // axes.setColors(0xff4400, 0xff1100, 0xff9900);
      scene.add(axes);
      var geometry = new BoxGeometry(8, 8, 8)
      var material = new MeshBasicMaterial({ color: 0x002288 });
      var cube = new Mesh(geometry, material);
      scene.add(cube);
      
      // 移动立方体的位置
      cube.position.x = 4;
      cube.position.y = 10;
      cube.position.z = 20;

      
      // 创建一个平面几何体
      var planeGeometry = new PlaneGeometry(100, 100);

      // 新建一个MeshLambertMaterial材质，这种材质可以接收并反射场景中各种光源发射出来的光线
      // 基础材质与它不同，各种光源对基础材质是没有作用的
      var planeMaterial = new MeshLambertMaterial({ color: 0x222222 });
      // 通过平面几何体对象和Lambert材质来新建一个地面网格对象
      var plane = new Mesh(planeGeometry, planeMaterial);

      plane.rotation.x = -0.5 * Math.PI;
      plane.position.set(15, 0, 0);
      scene.add(plane);

      // 设置相机位置
      camera.position.x = -30;
      camera.position.y = 45;
      camera.position.z = 35;
      
      // 把摄像机的方向对准场景的中心点，这样就可以看到X, Y, Z三个坐标轴
      camera.lookAt(scene.position);
      // cube.rotation.x += 0.5;
      // cube.rotation.y += 0.5;
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