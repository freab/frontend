<script>
	import { onMount } from 'svelte';
	import * as THREE from 'three';
	import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js';
	import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader.js';
	import { DRACOLoader } from 'three/examples/jsm/loaders/DRACOLoader.js';
	import { RectAreaLightHelper } from 'three/examples/jsm/helpers/RectAreaLightHelper.js'; // Optional: For debugging
  
	// Import the GLTF file using Vite's URL handling
	import modelUrl from '$lib/assets/WplusGplusLplusA.glb?url';
  
	let canvas;
  
	onMount(async () => {
	  // Scene
	  const scene = new THREE.Scene();
  
	  // Camera
	  const camera = new THREE.PerspectiveCamera(55, window.innerWidth / window.innerHeight, 0.1, 1000);
	  camera.position.set(0, 2, 5.5);
	 
  
	  // Renderer
	  const renderer = new THREE.WebGLRenderer({ canvas, antialias: true });
	  renderer.setSize(window.innerWidth, window.innerHeight);
	  renderer.setPixelRatio(window.devicePixelRatio);
  
	  // Orbit Controls
	  const controls = new OrbitControls(camera, renderer.domElement);
	  controls.enableDamping = true;
	  controls.dampingFactor = 0.05;
	  controls.autoRotateSpeed = 0.5;
	  controls.target.set(0, 0, 0);
  
	  // Lighting
	  const directionalLight = new THREE.DirectionalLight(0xffffff, 0.8);
	  directionalLight.position.set(5, 10, 5);
	  scene.add(directionalLight);
  
	  const ambientLight = new THREE.AmbientLight(0xffffff, 0.2);
	  scene.add(ambientLight);
  
	  // Add RectAreaLights at specified positions
	  const lightPositions = [
		new THREE.Vector3(0, 1.319, -0.614),
		new THREE.Vector3(1.127, 1.319, -0.269),
		new THREE.Vector3(-1.127, 1.319, -0.269),
		new THREE.Vector3(-0.656, 1.607, 0.282),
	  ];
  
	  lightPositions.forEach((position) => {
		const areaLight = new THREE.RectAreaLight(0xffffff, 5, 1, 1); // Color, intensity, width, height
		areaLight.position.copy(position);
		scene.add(areaLight);
  
	  });
  
	  // GLTF Loader with Draco Compression
	  const gltfLoader = new GLTFLoader();
	  const dracoLoader = new DRACOLoader();
	  dracoLoader.setDecoderPath('https://www.gstatic.com/draco/versioned/decoders/1.5.6/');
	  gltfLoader.setDRACOLoader(dracoLoader);
  
	  // Load GLTF Model
	  gltfLoader.load(
		modelUrl,
		(gltf) => {
		  const model = gltf.scene;
  
	
	     model.rotation.y = 1; 
  
		  // Add the model to the scene
		  scene.add(model);
		},
		undefined,
		(error) => {
		  console.error('Error loading GLTF model:', error);
		}
	  );
  
	  // Animation Loop
	  const animate = () => {
		requestAnimationFrame(animate);
		controls.update(); // Required for damping
		renderer.render(scene, camera);
	  };
	  animate();
  
	  // Handle Window Resize
	  const onWindowResize = () => {
		camera.aspect = window.innerWidth / window.innerHeight;
		camera.updateProjectionMatrix();
		renderer.setSize(window.innerWidth, window.innerHeight);
	  };
	  window.addEventListener('resize', onWindowResize);
  
	  // Cleanup
	  return () => {
		window.removeEventListener('resize', onWindowResize);
		renderer.dispose();
	  };
	});
  </script>
  
  <canvas bind:this={canvas} />