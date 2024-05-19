### 카메라 (Camera) /그림자 (shadow)

#### Perspective Camera 
![chrome-capture-2024-5-19](https://github.com/wonder21c/teamAI/assets/50861700/3df7ac6f-f8e9-4f2d-82cc-6141586e9c6a)

#### App.jsx
```
import './App.css'
import { Canvas } from '@react-three/fiber'
import MyElement3D from './Component/MyElement3D'

function App() {
  return (
    <>
      {/* 기본 카메라 : Perspective Camera */}
      {/* 카메라 렌즈 화각 : 75도
          카메라 위치 : 7, 7, 0 
      
      
      */}
      <Canvas camera = {{
        fov: 130,
        position: [7, 7, 0],
        near: 0.1,
        far: 20
      }} >
        <MyElement3D/>
      </Canvas>   
    </>
  )
}

export default App
```

#### MyElement3D.jsx
```
import { Environment, OrbitControls, useHelper } from "@react-three/drei";
import { useFrame, useThree } from "@react-three/fiber";
import { useEffect, useRef } from "react";
import * as THREE from "three"
import {RectAreaLightUniformsLib} from "three/examples/jsm/lights/RectAreaLightUniformsLib"
import {RectAreaLightHelper} from "three/examples/jsm/helpers/RectAreaLightHelper"

RectAreaLightUniformsLib.init()

const torusGeometry = new THREE.TorusGeometry(0.4, 0.1, 32, 32)
const torusMaterial = new THREE.MeshStandardMaterial({
    color: "#9b59b6",
    roughness: 0.5,
    metalness: 0.9
})

function MyElement3D() {
    useFrame((state) => {
        const time = state.clock.elapsedTime
        const smallSpherePivot = state.scene.getObjectByName("smallSpherePivot")

        smallSpherePivot.rotation.y = THREE.MathUtils.degToRad(time * 50)

        const target = new THREE.Vector3()
        smallSpherePivot.children[0].getWorldPosition(target)
        state.camera.position.copy(target)
        
        const ghostSpherePivot = state.scene.getObjectByName("ghostSpherePivot")
        ghostSpherePivot.rotation.y = THREE.MathUtils.degToRad(time * 50 + 30)
        ghostSpherePivot.children[0].getWorldPosition(target)
        state.camera.lookAt(target)
    })

    const light = useRef()
    useHelper(light, RectAreaLightHelper)

    // 카메라 객체 가져오기
    const {camera} = useThree()
    // useControls({
    //     positionZ: {
    //         value: 0, min: -10, max: 10, step: 0.1,
    //         onchange: (v) => camera.position.z = v
    //     },
    //     targetZ: {
    //         value: 0, min: -10, max: 10, step: 0.1,
    //         onchange: (v) => camera.lookAt(0, 0, v)
    //     }
    // })

    return (
        <>
            {/* <OrbitControls /> */}

            <rectAreaLight 
                color={"#ffffff"}
                intensity={20}
                width={1}
                height={3}

                ref={light}
                position={[0, 5, 0]}
                rotation-x={THREE.MathUtils.degToRad(-90)}
            />

            <mesh rotation-x={THREE.MathUtils.degToRad(-90)}>
                <sphereGeometry args={[1.5, 64, 64, 0, Math.PI]} />

                <meshStandardMaterial 
                    color={"#ffffff"}
                    roughness={0.1}
                    metalness={0.5}
                />
            </mesh>

            <mesh rotation-x={THREE.MathUtils.degToRad(-90)}>
                <sphereGeometry args={[1.5, 64, 64, 0, Math.PI]} />
                <meshStandardMaterial 
                    color={"#ffffff"}
                    roughness={0.1}
                    metalness={0.2}
                />
            </mesh>

            {new Array(10).fill().map((item, index) => {
                return (
                    <group key={index} rotation-y={THREE.MathUtils.degToRad(45 * index)}>
                        <mesh 
                            geometry={torusGeometry}
                            material={torusMaterial}
                            position={[3, 0.5, 0]}
                        />
                    </group>
                )
            })}

            <axesHelper />

            <group name="smallSpherePivot">
                <mesh position={[3, 0.5, 0]}>
                    <sphereGeometry args={[0.3, 32, 32]} />

                    <meshStandardMaterial 
                        color={"e74c3c"}
                        roughness={0.2}
                        metalness={0.5}
                    />
                </mesh>
            </group>

            <group name="ghostSpherePivot">
                <object3D position={[3, 0.5, 0]} />
            </group>
        </>
    )
}

export default MyElement3D
```

#### Orthographic Camera
![123123](https://github.com/qkrgudals1030/teamAI/assets/50861700/06928890-dc09-4a1f-b760-25554a5271ef)

#### App.jsx
```
import './App.css'
import { Canvas } from '@react-three/fiber'
import MyElement3D from './Component/MyElement3D'

function App() {
  return (
    <>
      {/* 기본 카메라 : Perspective Camera */}
      {/* 카메라 렌즈 화각 : 75도
          카메라 위치 : 7, 7, 0 
      
      
      */}
      <Canvas 
        orthographic
        camera = {{
          near: 0.1,
          far: 20,
          position: [7, 7, 0],
          zoom: 100
      }} >
        <MyElement3D/>
      </Canvas>   
    </>
  )
}

export default App

```

### pointLight 

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/664dfd16-1eb1-4c0c-be6f-a3f675bed135)


```
<pointLight 
  castShadow 
  color='#ffffff' 
  intensity={10} 
  position={[0, 5, 0]} 
/>
```
### DirectionalLight

조명 요소에 castShadow 옵션을 주어 그림자 생성 활성화해주어야 함.

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/495f87f6-6f96-48bd-887c-6bf58ca2245f)

```
<directionalLight
  ref={light}
  castShadow
  color={0xffffff}
  intensity={0.9}
  position={[0, 5, 0]}
  target-position={[0, 0, 0]}
/>

```

### spotLight

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/88af3b3b-c219-49ba-bace-c78f412eb332)

```
<spotLight
  shadow-mapSize={[1024 * 4, 1024 * 4]}
  castShadow
  color='#ffffff'
  intensity={20}
  position={[0, 5, 0]}
  angle={THREE.MathUtils.degToRad(60)}
/>
```


### AccumulativeShadows(정적그림자)

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/7cb8231c-dad9-4aca-88d6-c61632a8ae66)

```
<AccumulativeShadows
  position={[0, 0.01, 0]} // 그림자가 표현될 평면 메시의 위치 좌표
  scale={10} // 그림자가 표현될 평면 메시의 크기
  color='#000000' // 그림자 색상
  opacity={0.7} // 그림자 투명도
  alphaTest={1} // 그림자에 대한 픽셀의 알파값이 설정값보다 작을 때만 표현
  frames={60} // 처음 렌더링될 때의 프레임 수 (초기에 그림자가 페이드인 되는 속도)
>
  <RandomizedLight
    radius={0.5} // 그림자 경계도
    ambient={0.21} // Ambient Occlusion 에 대한 속성값, 값이 작아질 수록 그림자와 반사가 약해짐.
    intensity={1.5} // 광원 강도
    position={[5, 3, 0]} /// 광원 위치 좌표
  />

  <RandomizedLight
    amount={4} // 광원의 개수 (기본값: 8)
    radius={0.5} // 그림자 경계도
    ambient={0.21} // Ambient Occlusion 에 대한 속성값, 값이 작아질 수록 그림자와 반사가 약해짐.
    intensity={1.5} // 광원 강도
    position={[-5, 3, 0]} /// 광원 위치 좌표
  />
</AccumulativeShadows>
```


### 동적그림자

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/f73ac2d4-68a7-4c6c-ac83-88825c65514e)


```
<AccumulativeShadows
  ...
  frames={Infinity}
  temporal  // 그림자를 부드럽게 함.
  blend={30}  // 그림자의 부드러움 정도
  ...
>
  <RandomizedLight
    radius={0.5}
    ambient={0.21}
    intensity={1.5}
    position={[5, 3, 0]}
  />
</AccumulativeShadows>

```


#### softshadows

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/630f3171-a77d-4eec-978f-f2e912e44bcd)


```
const config = useControls({
  size: { value: 25, min: 0, max: 100 }, // 광원의 크기
  focus: { value: 0, min: 0, max: 10 }, // 깊이 포커스
  samples: { value: 10, min: 1, max: 100, step: 1 }, // 그림자 샘플링 수
});


<SoftShadows {...config} />
```

#### ContactShadows (그림자 표현 X)

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/3047e6fa-caaa-40b2-9e00-eddeea57bd64)

```
<ContactShadows
  position={[0, 0, 0]} // 그림자가 표현될 평면 메시의 위치 좌표
  scale={10} // 그림자가 표현될 평면 메시의 크기
  resolution={512} // 그림자 이미지 크기
  color='#000000' // 그림자 색상
  opacity={0.4} // 그림자 투명도
  blur={0.5} // 그림자 흐림도
  // frames={1} // 1: 정적 그림자
/>
```






