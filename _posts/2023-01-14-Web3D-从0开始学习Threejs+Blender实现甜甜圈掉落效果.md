---
author: Demi_YuHongJun
comments: true
date: 2023-01-13 06:42:32+00:00
layout: post
title: Web3D-从0开始学习Threejs+Blender实现甜甜圈掉落效果
description: Web3D-从0开始学习Threejs+Blender实现甜甜圈掉落效果
keywords: javascript
categories:
- frontend
- javascript
tags:
- javascript
---
* 目录
{:toc}
---

Web3D-从0开始学习Threejs+Blender实现甜甜圈掉落效果| 大帅老猿threejs特训

> ![threejs开发特训营作业封面.jpg](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/dca88cca81814d029daf41ba32259316~tplv-k3u1fbpfcp-watermark.image?)

## 前言

最近大帅邀请胖达老师带来了元宇宙实战特训，具体讲解了如何使用Blender进行3D建模、添加动画以及如何在Threejs中展示、控制3D模型，让我特别感慨，原来一些看似复杂的3D项目可以如此简单的实现。

###  Web3D 简介

##### Web3D的主要展示方式:

1. 浏览器直接渲染：电脑浏览器、移动端浏览器（包括微信浏览器） 微信小程序；
2. 服务端渲染（服务端运行，效果好，运营成本高）；将3D画面像素推流到前端浏览器/小程序展示；

##### 3D近几年流行的相关概念：
1. 数字孪生：三维实景模型 + 多系统监控/告警数据，实现远程监管（监控、管理）;
2. VR：把人装进虚拟环境
3. AR：把虚拟装进现实

##### 浏览器运行3D的方案

ActiveX插件：	IE、Chrome老版本、Firefox老版本，已过时；

Flash：		时代王者，官方已停止维护；

WebGL：	浏览器原生支持（IE11基本支持，其它浏览器基本都支持）

WebGPU:	性能高，目前还未得到操作系统和浏览器的广泛支持；

##### 可实现发布WebGL到浏览器运行的方案（从重到轻）：

Unity引擎：	wasm webgl     空包：20m+ 	（不支持ie11低版本chrome及Firefox及国产化）

CocosCreator：	webgl	          空包：6m+		（不支持ie11及低版本chrome及firefox）

threejs:		webgl               库大小：1m-	（开源，IE11均支持）

babylonjs:	webgl               库大小：4m+	（微软开源，中文资料相对较少）


### 今天我们就来了解Three.js

提到 Three.js，不得不先提 OpenGL 和 WebGL，OpenGL 是一个跨平台的3D/2D的绘图标准（规范），WebGL（Web Graphics Library）是一种3D绘图协议。

WebGL允许把JavaScript和OpenGL 结合在一起运用，但使用WebGL原生的API来写3D程序非常的复杂，同时需要相对较多的数学知识，对于开发者来说学习成本非常高。

Three.js是基于webGL的封装的一个易于使用且轻量级的3D库，Three.js对WebGL提供的接口进行了非常好的封装，简化了很多细节，大大降低了学习成本，极大地提高了性能，功能也非常强大。

（1）[Three.js官网](https://threejs.org/) 

（2）[Three.js 的 github 地址](https://github.com/mrdoob/three.js/) 

##### 起步阶段先从简单开始，直接引用 Three.js，学会最基本的 Three.js 的使用方法

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <script src="js/three.min.js"></script>
  <script>
    // 创建场景
    const scene = new THREE.Scene(); 
    // 创建相机，PerspectiveCamera(透视相机)，参数（视野角度,长宽比,进截面,远截面）
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000); 
    // 渲染器
    const renderer = new THREE.WebGLRenderer();
    // 设置渲染器的宽高
    renderer.setSize( window.innerWidth, window.innerHeight );
    // 将renderer（渲染器）的dom元素（renderer.domElement）添加到我们的HTML文档中
    document.body.appendChild( renderer.domElement );

    // demo--立方体
    const geometry = new THREE.BoxGeometry( 1, 1, 1 ); // BoxGeometry 立方体对象
    const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );  // MeshBasicMaterial 其中的一种材质，设置颜色绿色
    const cube = new THREE.Mesh( geometry, material ); // 创立一个网格对象
    scene.add( cube ); // 将网格对象添加到场景中
    camera.position.z = 5; 
    
    // 
    function animate() {
      requestAnimationFrame( animate ); // 创建了一个使渲染器能够在每次屏幕刷新时对场景进行绘制的循
      cube.rotation.x += 0.01; // 使正方体能动起来
      cube.rotation.y += 0.01; // 使正方体能动起来
      renderer.render( scene, camera ); 
    }
    animate();
  </script>
</body>
</html>
```
##### 使用 npm 来开发并测试
（1）[获取项目代码](https://github.com/YCYTeam/YCY-TrainingCamp-S2)
（2）安装依赖

	```
	npm install
	```
（3）开发主要代码 day01_直播代码.js

```
import * as THREE from 'three';
import { OrbitControls } from "three/examples/jsm/controls/OrbitControls";
import { GLTFLoader } from "three/examples/jsm/loaders/GLTFLoader";
import { RGBELoader } from 'three/examples/jsm/loaders/RGBELoader';

let mixer;

const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.01, 10);
const renderer = new THREE.WebGLRenderer({ antialias: true });
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

camera.position.set(0.3, 0.3, 0.5);

const controls = new OrbitControls(camera, renderer.domElement);

// scene.background = new THREE.Color(0.6, 0.6, 0.6);

// const ambientLight = new THREE.AmbientLight(0xffffff, 0.2);
// scene.add(ambientLight);

const directionLight = new THREE.DirectionalLight(0xffffff, 0.4);
scene.add(directionLight);

// const boxGeometry = new THREE.BoxGeometry(1,1,1);
// const boxMaterial = new THREE.MeshBasicMaterial({color: 0x00ff00});
// const boxMesh = new THREE.Mesh(boxGeometry, boxMaterial);
// scene.add(boxMesh);

let donuts;
new GLTFLoader().load('../resources/models/donuts.glb', (gltf) => {

    console.log(gltf);
    scene.add(gltf.scene);
    donuts = gltf.scene;

    // gltf.scene.traverse((child)=>{
    //     console.log(child.name);
    // })

    mixer = new THREE.AnimationMixer(gltf.scene);
    const clips = gltf.animations; // 播放所有动画
    clips.forEach(function (clip) {
        const action = mixer.clipAction(clip);
        action.loop = THREE.LoopOnce;
        // 停在最后一帧
        action.clampWhenFinished = true;
        action.play();
    });

})

new RGBELoader()
    .load('../resources/sky.hdr', function (texture) {
        scene.background = texture;
        texture.mapping = THREE.EquirectangularReflectionMapping;
        scene.environment = texture;
        renderer.outputEncoding = THREE.sRGBEncoding;
        renderer.render(scene, camera);
});

function animate() {
    requestAnimationFrame(animate);

    renderer.render(scene, camera);

    controls.update();

    if (donuts){
        donuts.rotation.y += 0.01;
    }

    if (mixer) {
        mixer.update(0.02);
    }
}

animate();
```
（4）执行 npm run start ，打开 http://localhost:3000/

成果展示

## 结束语

虽然这个案例比较简单，但是它能够让我们了解程序开发和美术资源是如何协作的，我们可以学习到3D模型如何在Threejs中被使用，相信能够帮助大家打开Threejs的大门。当然胖达老师后面的课程中有讲到更为复杂的元宇宙场景如何实现，以及如何载入人物模型控制其运动，更加能够激起大家的兴趣，以后有空再和大家分享。

https://juejin.cn/post/7188100244574306365 

https://segmentfault.com/a/1190000043333703

https://zhuanlan.zhihu.com/p/598882324

https://blog.csdn.net/xindy138/article/details/128679003?spm=1001.2014.3001.5501