### 3D地球

先上效果图

![image](https://github.com/xswei/ThreeJS_demo/blob/master/examples/01/pic.jpg)


- 画球
- 贴图


### 画球

使用THREE的Sphere绘制：

```js
var sphere = new THREE.SphereGeometry(r,40,40);

```


### 贴图

在球面上贴上地图图片即可，首先使用预先准备好的图片创建一个纹理材质：

```js

var loader = new THREE.TextureLoader();
loader.load("../images/Earth.png",(t)=>{
	let material = new THREE.MeshBasicMaterial({
		map:t
	});
	s.add(new THREE.Mesh(sphere,material));
})

```

loader是一个纹理加载器，调用loader的load方法，并传入加载成功时的回调函数，在回调函数中创建使用纹理的材质，然后创建mesh对象，将其加入到场景中。

### 图片尺寸问题

在使用图片作为纹理时，要注意图片的宽高必须要为2的整数次幂。比如128，256，512...，如果尺寸不符合这个要求，则会出现`THREE.WebGLRenderer: image is not power of two (4004x2000)`这种警告并且会由three自动调整。

### 其他问题

在从外部文件加载纹理时候，要注意使用http协议，也就是要开服务器。


Next:[地理坐标和三维空间坐标](https://github.com/xswei/ThreeJS_demo/tree/master/examples/02)


