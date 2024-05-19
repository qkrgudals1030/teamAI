### 재질 (Material) 1

#### 실행화면

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/16d3158f-8c45-462a-8182-acf516e08a7f)

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/478fac32-d602-4de9-a4cf-b179f7eb5f06)

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/c9d052d0-12e9-45a4-931a-e66c31609f01)

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/613b77e9-85f9-40ea-9f88-50744a591711)

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/626ad1ee-446f-4a3e-bb42-80311722d177)

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/79a1d8fe-088c-4954-80bc-e102670f7b64)


#### meshBasicMaterial
```
import { OrbitControls } from "@react-three/drei";
import { useEffect, useRef } from "react";
import * as THREE from "three"

function MyElement3D() {
    const mesh1 = useRef()
    const mesh2 = useRef()

    useEffect(() => {
        mesh2.current.material = mesh1.current.material
    }, [])

    return (
        <>
            <OrbitControls />

            <ambientLight intensity = {0.2} />

            <directionalLight position = {[0, 1, 0]} />
            <directionalLight position = {[1, 2, 8]} intensity = {0.7} />

            <mesh 
                ref = {mesh1}
                position = {[0.7, 0, 0]}
            >
                <boxGeometry />

                {/* 
                visible : 보이는지 안보이는지 true/false
                transparent : 재질 투명 효과 true/false
                opacity : 투명도 (1 : 불투명, 0 : 투명) - transparent가 true일때만 작동
                depthTest : 렌더링 되고 있는 Mesh의 픽셀을 depthBuffer 값을 활용하여 검사할 것인지
                depthWrite : 렌더링 되고 있는 Mesh의 픽셀에 대한 Z 값을 depthBuffer에 기록할 것인지
                side : Mesh를 구성하고 있는 면 중, 어느 면을 렌더링 할 것인지 (기본값 : FrontSide)
                */}
                <meshBasicMaterial 
                    color = "yellow" 
                    wireframe = {false}
                    visible={true}
                    transparent = {true}
                    opacity = {0.5}
                    depthTest = {true}
                    depthWrite = {true}
                    side = {THREE.DoubleSide}
                />
            </mesh>

            <mesh 
                ref = {mesh2}
                position = {[-0.7, 0, 0]}
            >
                <torusGeometry args={[0.5, 0.2]} />
            </mesh>
        </>
    )
}

export default MyElement3D
```

#### meshLambertMaterial
```
import { OrbitControls } from "@react-three/drei";
import { useEffect, useRef } from "react";
import * as THREE from "three"

function MyElement3D() {
    const mesh1 = useRef()
    const mesh2 = useRef()

    useEffect(() => {
        mesh2.current.material = mesh1.current.material
    }, [])

    return (
        <>
            <OrbitControls />

            <ambientLight intensity = {0.2} />

            <directionalLight position = {[0, 1, 0]} />
            <directionalLight position = {[1, 2, 8]} intensity = {0.7} />

            <mesh 
                ref = {mesh1}
                position = {[0.7, 0, 0]}
            >
                <boxGeometry />

                {/* 
                visible : 보이는지 안보이는지 true/false
                transparent : 재질 투명 효과 true/false
                opacity : 투명도 (1 : 불투명, 0 : 투명) - transparent가 true일때만 작동
                depthTest : 렌더링 되고 있는 Mesh의 픽셀을 depthBuffer 값을 활용하여 검사할 것인지
                depthWrite : 렌더링 되고 있는 Mesh의 픽셀에 대한 Z 값을 depthBuffer에 기록할 것인지
                side : Mesh를 구성하고 있는 면 중, 어느 면을 렌더링 할 것인지 (기본값 : FrontSide)
                */}
                <meshLambertMaterial
                    color = "#d25383" 
                    wireframe = {false}
                    visible={true}
                    transparent = {true}
                    opacity = {1}
                    depthTest = {true}
                    depthWrite = {true}
                    side = {THREE.FrontSide}

                    // 재질 자체에서 검출하는 속성값 (기본 : 검정색 - 어떤 색상도 검출 X)
                    // 위 색이랑 섞임
                    emissive={0x666600}
                />
            </mesh>

            <mesh 
                ref = {mesh2}
                position = {[-0.7, 0, 0]}
            >
                <torusGeometry args={[0.5, 0.2]} />
            </mesh>
        </>
    )
}

export default MyElement3D
```

#### meshPhongMaterial

```
import { OrbitControls } from "@react-three/drei";
import { useEffect, useRef } from "react";
import * as THREE from "three"

function MyElement3D() {
    const mesh1 = useRef()
    const mesh2 = useRef()

    useEffect(() => {
        mesh2.current.material = mesh1.current.material
    }, [])

    return (
        <>
            <OrbitControls />

            <ambientLight intensity = {0.2} />

            <directionalLight position = {[0, 1, 0]} />
            <directionalLight position = {[1, 2, 8]} intensity = {0.7} />

            <mesh 
                ref = {mesh1}
                position = {[0.7, 0, 0]}
            >
                <boxGeometry />

                {/* 
                visible : 보이는지 안보이는지 true/false
                transparent : 재질 투명 효과 true/false
                opacity : 투명도 (1 : 불투명, 0 : 투명) - transparent가 true일때만 작동
                depthTest : 렌더링 되고 있는 Mesh의 픽셀을 depthBuffer 값을 활용하여 검사할 것인지
                depthWrite : 렌더링 되고 있는 Mesh의 픽셀에 대한 Z 값을 depthBuffer에 기록할 것인지
                side : Mesh를 구성하고 있는 면 중, 어느 면을 렌더링 할 것인지 (기본값 : FrontSide)
                emissive : 재질 자체에서 검출하는 속성값 (기본 : 검정색 - 어떤 색상도 검출 X)
                 color 색이랑 섞임
                */}
                <meshPhongMaterial
                    wireframe = {false}
                    visible={true}
                    transparent = {true}
                    opacity = {1}
                    depthTest = {true}
                    depthWrite = {true}
                    side = {THREE.FrontSide}

                    emissive = {0x666600}
                    color = {0xff0000} 

                    // specular : 광원에 의해 반사되는 색상 값
                    // shininess : specular의 반사 정도 조절
                    specular = {0xffff00}
                    shininess = {100}

                    // flatShading : mesh를 평평하게 렌더링할 지 여부
                    flatShading = {true}
                />
            </mesh>

            <mesh 
                ref = {mesh2}
                position = {[-0.7, 0, 0]}
            >
                <torusGeometry args={[0.5, 0.2]} />
            </mesh>
        </>
    )
}

export default MyElement3D
```

#### meshStandardMaterial
```
import { OrbitControls } from "@react-three/drei";
import { useControls } from "leva";
import { useEffect, useRef } from "react";
import * as THREE from "three"

function MyElement3D() {
    const mesh1 = useRef()
    const mesh2 = useRef()

    useEffect(() => {
        mesh2.current.material = mesh1.current.material
    }, [])

    const {roughness, metalness} = useControls({
        roughness: {value: 0, min: 0, max: 1, step: 0.01},
        metalness: {value: 0, min: 0, max: 1, step: 0.01}
    })

    return (
        <>
            <OrbitControls />

            <ambientLight intensity = {0.2} />

            <directionalLight position = {[0, 1, 0]} />
            <directionalLight position = {[1, 2, 8]} intensity = {0.7} />

            <mesh 
                ref = {mesh1}
                position = {[0.7, 0, 0]}
            >
                <boxGeometry />

                <meshStandardMaterial 
                    visible={true}
                    transparent = {true}
                    opacity = {0.5}
                    depthTest = {true}
                    depthWrite = {true}
                    side = {THREE.FrontSide}

                    emissive = {0x00000}
                    flatShading = {false}

                    color = {0xff0000} 
                    wireframe = {false}

                    // meshStandardMaterial 고유 특성
                    roughness = {roughness}
                    metalness = {metalness}
                />
            </mesh>

            <mesh 
                ref = {mesh2}
                position = {[-0.7, 0, 0]}
            >
                <torusGeometry args={[0.5, 0.2]} />
            </mesh>
        </>
    )
}

export default MyElement3D
```

### meshPhysicalMaterial
```
import { OrbitControls } from "@react-three/drei";
import { useEffect, useRef } from "react";
import { useControls } from "leva";
import * as THREE from "three"

function MyElement3D() {
    const mesh1 = useRef()
    const mesh2 = useRef()

    useEffect(() => {
        mesh2.current.material = mesh1.current.material
    }, [])

    const {roughness, metalness, clearcoat, clearcoatRoughness, transmission, thickness, ior} = useControls({
        roughness: {value: 0, min: 0, max: 1, step: 0.01},
        metalness: {value: 0, min: 0, max: 1, step: 0.01},
        clearcoat: {value: 0, min: 0, max: 1, step: 0.01}, 
        clearcoatRoughness: {value: 0, min: 0, max: 1, step: 0.01},
        transmission: {value: 0, min: 0, max: 1, step: 0.01},
        thickness: {value: 0, min: 0, max: 1, step: 0.01},
        ior: {value: 1.5, min: 0, max: 2.333, step: 0.01}
    })

    return (
        <>
            <OrbitControls />

            <ambientLight intensity = {0.2} />

            <directionalLight position = {[0, 1, 0]} />
            <directionalLight position = {[1, 2, 8]} intensity = {0.7} />

            <mesh 
                ref = {mesh1}
                position = {[0.7, 0, 0]}
            >
                <torusKnotGeometry args = {[0.5, 0.15, 256, 128]} />
              
                <meshPhysicalMaterial 
                    visible={true}
                    transparent = {true}
                    opacity = {0.5}
                    depthTest = {true}
                    depthWrite = {true}
                    side = {THREE.DoubleSide}
                    emissive = {0x00000}
                    flatShading = {false}
                    roughness = {roughness}
                    metalness = {metalness}

                    color = {0xffffff} 
                    wireframe = {false}

                    // meshPhysicalMaterial 고유 속성
                    // clearcoat : 코팅된 광택 있는 층
                    // clearcoatRoughness :  clearcoat 표면의 거칠기
                    clearcoat = {clearcoat}
                    clearcoatRoughness = {clearcoatRoughness}

                    // meshPhysicalMaterial 유리에 사용되는 고유 속성
                    // transmission : 유리투명도
                    // thickness : 유리 두께
                    // ior : 유리 굴절률
                    transmission = {transmission}
                    thickness = {thickness}
                    ior = {ior}
                />
            </mesh>

            <mesh 
                ref = {mesh2}
                position = {[-0.7, 0, 0]}
            >
                <torusGeometry args={[0.5, 0.2]} />
            </mesh>
        </>
    )
}

export default MyElement3D
```

#### meshDepthMaterial
```
import { OrbitControls } from "@react-three/drei";
import { useEffect, useRef } from "react";
import { useControls } from "leva";
import * as THREE from "three"

function MyElement3D() {
    const mesh1 = useRef()
    const mesh2 = useRef()

    useEffect(() => {
        mesh2.current.material = mesh1.current.material
    }, [])

    const {roughness, metalness, clearcoat, clearcoatRoughness, transmission, thickness, ior} = useControls({
        roughness: {value: 0, min: 0, max: 1, step: 0.01},
        metalness: {value: 0, min: 0, max: 1, step: 0.01},
        clearcoat: {value: 0, min: 0, max: 1, step: 0.01}, 
        clearcoatRoughness: {value: 0, min: 0, max: 1, step: 0.01},
        transmission: {value: 0, min: 0, max: 1, step: 0.01},
        thickness: {value: 0, min: 0, max: 1, step: 0.01},
        ior: {value: 1.5, min: 0, max: 2.333, step: 0.01}
    })

    return (
        <>
            <OrbitControls />

            <ambientLight intensity = {0.2} />

            <directionalLight position = {[0, 1, 0]} />
            <directionalLight position = {[1, 2, 8]} intensity = {0.7} />

            <mesh 
                ref = {mesh1}
                position = {[0.7, 0, 0]}
            >
                <torusKnotGeometry args = {[0.5, 0.15, 256, 128]} />
              
                <meshDepthMaterial />
            </mesh>

            <mesh 
                ref = {mesh2}
                position = {[-0.7, 0, 0]}
            >
                <torusGeometry args={[0.5, 0.2]} />
            </mesh>
        </>
    )
}

export default MyElement3D
```
#### App.jsx
```
import './App.css'
import { Canvas } from '@react-three/fiber'
import MyElement3D from './Component/MyElement3D'

function App() {
  return (
    <>
      {/* camera로부터 거리가 3.5인 픽셀지점은 그 값을 0으로 할당, 
          camera로부터 거리가 6인 지점은 2를 할당 */}
      <Canvas camera = {{near: 3.5, far: 6}} >
        <MyElement3D/>
      </Canvas>   
    </>
  )
}

export default App
```
![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/b35608c1-b19a-43af-88de-4ef588ccf07f)

#### meshMatcapMaterial
```
import { OrbitControls, useTexture } from "@react-three/drei";
import { useEffect, useRef } from "react";
import { useControls } from "leva";
import * as THREE from "three"

function MyElement3D() {
    const mesh1 = useRef()
    const mesh2 = useRef()

    useEffect(() => {
        mesh2.current.material = mesh1.current.material
    }, [])

    // matcap 이미지 불러오기
    const matcap = useTexture("././public/images/matcap.jpg")

    return (
        <>
            <OrbitControls />

            <ambientLight intensity = {0.2} />

            {/* meshMatcapMaterial은 광원을 필요로 하지 않는다. */}
            {/* <directionalLight position = {[0, 1, 0]} />
            <directionalLight position = {[1, 2, 8]} intensity = {0.7} /> */}

            <mesh 
                ref = {mesh1}
                position = {[0.7, 0, 0]}
            >
                <torusKnotGeometry args = {[0.5, 0.15, 256, 128]} />

                {/* <meshDepthMaterial/> */}
                {/* flatShading : 각진 면으로 표현 */}
                <meshMatcapMaterial matcap={matcap} 
                    flatShading = {true}
                />
                
            </mesh>

            <mesh 
                ref = {mesh2}
                position = {[-0.7, 0, 0]}
            >
                <torusGeometry args={[0.5, 0.2]} />
            </mesh>
        </>
    )
}

export default MyElement3D
```
![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/7b68771b-418a-4ed2-a3b2-e50ee09ca5e3)

#### meshToonMaterial
```
import { OrbitControls, useTexture } from "@react-three/drei";
import { useEffect, useRef } from "react";
import { useControls } from "leva";
import * as THREE from "three"

function MyElement3D() {
    const mesh1 = useRef()
    const mesh2 = useRef()

    useEffect(() => {
        mesh2.current.material = mesh1.current.material
    }, [])

    // tone 불러오기
    const texture = useTexture("././public/images/threeTone.jpg")
    // 색상 보관이 이루어지지 않도록 함. 
    texture.minFilter = THREE.NearestFilter
    texture.magFilter = THREE.NearestFilter

    return (
        <>
            <OrbitControls />

            <ambientLight intensity = {0.2} />

            {/* meshMatcapMaterial은 광원을 필요로 하지 않는다. */}
            {/* <directionalLight position = {[0, 1, 0]} />
            <directionalLight position = {[1, 2, 8]} intensity = {0.7} /> */}

            <mesh 
                ref = {mesh1}
                position = {[0.7, 0, 0]}
            >
                <torusKnotGeometry args = {[0.5, 0.15, 256, 128]} />

                <meshToonMaterial gradientMap={texture} color="cyan" />
                
            </mesh>

            <mesh 
                ref = {mesh2}
                position = {[-0.7, 0, 0]}
            >
                <torusGeometry args={[0.5, 0.2]} />
            </mesh>
        </>
    )
}

export default MyElement3D
```

# 재질 2


https://github.com/qkrgudals1030/teamAI/assets/50895748/646ada72-b340-4e3e-8222-2fe702385804


```
import { MeshWobbleMaterial, OrbitControls } from '@react-three/drei';

const Wobble = () => {
  return (
    <>
      <OrbitControls />

      <ambientLight intensity={0.2} />
      <directionalLight position={[0, 1, 0]} />
      <directionalLight position={[1, 2, 8]} intensity={0.7} />

      <mesh>
        <torusGeometry />
        <MeshWobbleMaterial
          factor={1} // 흔들림 정도
          speed={10} // 흔들림 속도
        />
      </mesh>
    </>
  );
};

export default Wobble;

```

#### MeshReflectorMaterial

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/89146bf8-8ee4-4bf2-a119-121ae61ce0b5)

```
import { MeshReflectorMaterial, OrbitControls } from '@react-three/drei';

const Reflector = () => {
  return (
    <>
      <OrbitControls />

      <ambientLight intensity={0.2} />
      <directionalLight position={[0, 1, 0]} />
      <directionalLight position={[1, 2, 8]} intensity={0.7} />

      <mesh position={[0, -0.6, 0]} rotation={[-Math.PI / 2, 0, 0]}>
        <planeGeometry args={[10, 10]} />
        <MeshReflectorMaterial
          blur={[300, 100]}
          resolution={2048}
          mixBlur={1}
          mixStrength={30}
          roughness={1}
          depthScale={0.7}
          minDepthThreshold={0.4}
          maxDepthThreshold={1.4}
          color='#777777'
          metalness={0.5}
        />
      </mesh>

      <mesh position={[0, 0, 0]}>
        <boxGeometry />
        <meshStandardMaterial color='cyan' />
      </mesh>
    </>
  );
};

export default Reflector;
```

### MeshRefractionMaterial

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/6790cb8e-0958-4981-b2ff-e167810f141a)


```
import { useLoader } from '@react-three/fiber';
import { CubeCamera, MeshRefractionMaterial, OrbitControls } from '@react-three/drei';
import { RGBELoader } from 'three-stdlib';

const Refraction = () => {
  const texture = useLoader(RGBELoader, './images/hdr/shanghai_bund_1k.hdr');

  return (
    <>
      <OrbitControls />

      <ambientLight intensity={0.2} />
      <directionalLight position={[0, 1, 0]} />
      <directionalLight position={[1, 2, 8]} intensity={0.7} />

      <CubeCamera resolution={1024} frames={1} envMap={texture}>
        {(texture) => (
          <mesh position={[0, -0.6, 0]} rotation={[-Math.PI / 2, 0, 0]}>
            <dodecahedronGeometry />
            <MeshRefractionMaterial
              envMap={texture}
              toneMapped={false}
              bounces={2}
              aberrationsStrength={0.03}
              ior={2.75}
              fresnel={1}
              color='white'
              fastChroma={true}
            />
          </mesh>
        )}
      </CubeCamera>
    </>
  );
};

export default Refraction;
```

### MeshTransmissionMaterial

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/8bdf83fc-d39e-4994-b114-5fd1fe8a2045)


```
import * as THREE from 'three';
import { MeshTransmissionMaterial, OrbitControls } from '@react-three/drei';
import { useControls } from 'leva';

const Transmission = () => {
  const config = useControls({
    transmissionSampler: false,
    backside: false,
    samples: { value: 10, min: 1, max: 32, step: 1 },
    resolution: { value: 2048, min: 256, max: 2048, step: 256 },
    transmission: { value: 1, min: 0, max: 1 },
    roughness: { value: 0.0, min: 0, max: 1, step: 0.01 },
    thickness: { value: 3.5, min: 0, max: 10, step: 0.01 },
    ior: { value: 1.5, min: 1, max: 5, step: 0.01 },
    chromaticAberration: { value: 0.06, min: 0, max: 1 },
    anisotropy: { value: 0.1, min: 0, max: 1, step: 0.01 },
    distortion: { value: 0.0, min: 0, max: 1, step: 0.01 },
    distortionScale: { value: 0.3, min: 0.01, max: 1, step: 0.01 },
    temporalDistortion: { value: 0.5, min: 0, max: 1, step: 0.01 },
    clearcoat: { value: 1, min: 0, max: 1 },
    attenuationDistance: { value: 0.5, min: 0, max: 10, step: 0.01 },
    attenuationColor: '#ffffff',
    color: '#c9ffa1',
    bg: '#839681',
  });

  return (
    <>
      <OrbitControls />

      <ambientLight intensity={0.2} />
      <directionalLight position={[0, 1, 0]} />
      <directionalLight position={[1, 2, 8]} intensity={0.7} />

      <mesh>
        <sphereGeometry args={[1.4, 128, 128]} />
        <MeshTransmissionMaterial {...config} background={new THREE.Color(config.bg)} />
      </mesh>

      <mesh scale={0.3}>
        <torusGeometry args={[0.5, 0.2, 32]} />
        <meshStandardMaterial />
      </mesh>
    </>
  );
};

export default Transmission;

```

### MeshDistortMaterial

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/cb0482b8-f5f5-4a60-9ed1-c220c82eb54d)

```
import { MeshDistortMaterial, OrbitControls } from '@react-three/drei';

const Distort = () => {
  return (
    <>
      <OrbitControls />

      <ambientLight intensity={0.2} />
      <directionalLight position={[0, 1, 0]} />
      <directionalLight position={[1, 2, 8]} intensity={0.7} />

      <mesh>
        <torusGeometry />
        <MeshDistortMaterial 
          distort={0.9} // 왜곡 정도
          speed={3}   // 왜곡 속도
        />
      </mesh>
    </>
  );
};

export default Distort;
```

### MeshDiscardMaterial(재질이 적용된 메시르 화면에 표시하지 않도록 함.)


```
import { MeshDiscardMaterial, OrbitControls } from '@react-three/drei';

const Discard = () => {
  return (
    <>
      <OrbitControls />

      <ambientLight intensity={0.2} />
      <directionalLight position={[0, 1, 0]} />
      <directionalLight position={[1, 2, 8]} intensity={0.7} />

      <mesh>
        <torusGeometry />
        <MeshDiscardMaterial />
      </mesh>
    </>
  );
};

export default Discard;

```

### shaderMaterial

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/1a92497f-64ff-4978-a864-e56b20496a97)

```
import * as THREE from 'three';
import { extend } from '@react-three/fiber';
import { OrbitControls, shaderMaterial } from '@react-three/drei';

const SimpleMaterial = new shaderMaterial(
  // [첫번째 인자] uColor라는 uniform을 정의하여 색상정보를 GPU에 전달
  {
    uColor: new THREE.Color(1, 0, 0),
  },

  // [두번째 인자] Vertex(꼭짓점) Shader: Geometry의 좌표값을 화면에 출력하기 위한 좌표로 변경하는 목적
  `
  varying vec2 vUv;

  void main() {
    vUv = uv;
    gl_Position = projectionMatrix * modelViewMatrix * vec4(position, 1.0);
  }
`,

  // [세번째 인자] Fragment shader: mesh가 화면에 픽셀 단위로 표시될 때 각 픽셀에 생상 값을 결정하는 목적
  // 버텍스 쉐이더에서 계산된 정보를 사용하여 각 픽셀의 색상을 결정함.
  `
  uniform vec3 uColor;
  varying vec2 vUv;

  void main() {
    gl_FragColor = vec4(vUv.y * uColor, 1.0);
  }
`
);

// SimpleMaterial를 태그 형태로 사용하기 위해서 R3F의 extend 함수를 사용함.
extend({ SimpleMaterial });

const Shader = () => {
  return (
    <>
      <OrbitControls />

      <ambientLight intensity={0.2} />
      <directionalLight position={[0, 1, 0]} />
      <directionalLight position={[1, 2, 8]} intensity={0.7} />

      <mesh>
        <boxGeometry />
        <simpleMaterial uColor={'red'} /> {/* jsx 에서는 소문자로 사용 */} {/* uColor를 전달할 수 있음 */}
      </mesh>
    </>
  );
};

export default Shader;
```
###Map, RoughnessMap
![녹음 2024-05-19 174947](https://github.com/qkrgudals1030/teamAI/assets/50951220/c6697a6f-690a-4020-9989-9a8aab9912cb)
```
import * as THREE from 'three';
import { OrbitControls, useTexture } from '@react-three/drei';

const Box = () => {
  // texture.map 으로 접근할 수 있으며, map은 원하는 이름으로 바꿔도 됨.
  const textures = useTexture({
    map: './images/texture/window/Glass_Window_004_basecolor.jpg',
    roughnessMap: './images/texture/window/Glass_Window_004_roughness.jpg',
  });

  return (
    <>
      <OrbitControls />

      <ambientLight intensity={0.2} />
      <directionalLight position={[0, 1, -8]} intensity={0.4} />
      <directionalLight position={[1, 2, 8]} intensity={0.4} />

      <mesh>
        <cylinderGeometry args={[2, 2, 3, 1024, 1024, true]} />
        <meshStandardMaterial
          side={THREE.DoubleSide} // 양면 렌더링
          
          // 색상 매핑
          map={textures.map} // 텍스처 색상 매핑
          
          // 거칠기 매핑
          roughnessMap={textures.roughnessMap} // 거칠기 텍스처 매핑
          roughnessMap-colorSpace={THREE.NoColorSpace} // 텍스처의 색상 공간 지정 (NoColorSpace: 텍스처의 색상 공간 변환을 비활성화 하여 원본 색상 값을 사용하도록 지시)
        />
      </mesh>
    </>
  );
};

export default Box;
'''





### 출처

https://velog.io/@3436rngus/R3FReact-Three-Fiber-Material











