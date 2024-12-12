# Element 5 Documentation

## Scene 1

This code creates the ground in the scene and configures the colour and material of it.

I changed the colours of the ground in the diffusecolour section, which is represented in RGB format

```js
function createGround(scene: Scene) {
    let ground = MeshBuilder.CreateGround(
      "ground",
      { width: 3, height: 3 },
      scene
    );
    var groundMaterial = new StandardMaterial("groundMaterial", scene);
    groundMaterial.backFaceCulling = false;
    ground.material = groundMaterial;
    groundMaterial.diffuseColor = new Color3(20, 1, 0.5);
    return ground;
  }
```

this code creates a cylinder in the scne and configures the size, material, position and colour of it

I changed the size of the cylinder and the colour of it

```js
 function createCylinder(scene: Scene) {
    let cylinder = MeshBuilder.CreateCylinder(
      "cylinder",
      { height: 1.5, diameter: 0.9 },
      scene
    );
    cylinder.position.x = 1;
    cylinder.position.y = 1;
    cylinder.position.z = 1;
  
    var texture = new StandardMaterial("reflective", scene);
    texture.ambientTexture = new Texture("/workspaces/babylonJSdev/babylonProj/multi/assets/reflectivity.jpg", scene);
    texture.diffuseColor = new Color3(1, 1, 300);
    cylinder.material = texture;
    return cylinder;
  }
```
## Scene 2

In the code below I have created a cylinder object and have configured its size, diameter, position and the texture / colour

```js
function createCylinder(scene: Scene) {
    let cylinder = MeshBuilder.CreateCylinder(
      "cylinder",
      { height: 20, diameter: 1.4 },
      scene
    );
    cylinder.position.x = 1;
    cylinder.position.y = 1;
    cylinder.position.z = 1;
  
    var texture = new StandardMaterial("reflective", scene);
    texture.ambientTexture = new Texture("./assets/reflectivity.png", scene);
    texture.diffuseColor = new Color3(200, 1, 1);
    cylinder.material = texture;
    return cylinder;
  }
```

The code below creates a sphere mesh. I made it so the sphere is very large and intersects with the cylinder. The sphere is also a very blindign white because i configured the light intensity to be 10X the standard.

```js
function createSphere(scene: Scene) {
    let sphere = MeshBuilder.CreateSphere(
      "sphere",
      { diameter: 7, segments: 32 },
      scene,
    );
    sphere.position.y = 2;
    return sphere;
  }
```

```js
function createLight(scene: Scene) {
    const light = new HemisphericLight("light", new Vector3(0, 1, 0), scene);
    light.intensity = 10;
    return light;
  }
```

## Scene 3

For scene 3 i created a sphere object and made it large again. I also created a donut shape called a Torus which does not intersect with the sphere
I increased the torus' diameter slightly higher so it was larger
```js
 function createTorus(scene: Scene) {
    let torus = MeshBuilder.CreateTorus(
      "torus",
      { diameter: 0.9, thickness: 2, tessellation: 10 },
      scene
    );
    torus.position.x = -1;
    torus.position.y = 2;
    torus.position.z = 1;
  
    var texture = new StandardMaterial("reflective", scene);
    texture.ambientTexture = new Texture("./assets/reflectivity.png", scene);
    texture.diffuseColor = new Color3(1, 1, 1);
    torus.material = texture;

    return torus;
  }
```

to prevent the intersection of the torus and sphere i offset the sphere on the X-axis by 5

```js
function createSphere(scene: Scene) {
    let sphere = MeshBuilder.CreateSphere(
      "sphere",
      { diameter: 10, segments: 32 },
      scene,
    );
    sphere.position.y = 1;
    sphere.position.x = 5;
    return sphere;
  }
  
```

## Scene 4

For this scene i created a much smaller sphere than before and set it to be slightly higher on the y-axis too.

```js
function createSphere(scene: Scene) {
    let sphere = MeshBuilder.CreateSphere(
      "sphere",
      { diameter: 1, segments: 32 },
      scene,
    );
    sphere.position.y = 1.5;
    return sphere;
  }
```

I also created a tube object and offset it from the sphere by a large amount.
I also set its colour to be pink via RGB values

```js
function createTube(scene: Scene) {
    const myPath = [
      new Vector3(3.85, 2.85, 2.85),
      new Vector3(5.35, 1.35, 1.35),
    ];
  
    const tube = MeshBuilder.CreateTube(
      "tube",
      { path: myPath, radius: 0.7, sideOrientation: Mesh.DOUBLESIDE },
      scene
    );
  
    var texture = new StandardMaterial("reflective", scene);
    texture.ambientTexture = new Texture("./assets/reflectivity.png", scene);
    texture.diffuseColor = new Color3(3, 0, 2);
    tube.material = texture;
    return tube;
  }
  ```