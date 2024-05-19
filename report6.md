### 광원 (Light)


#### 실습: R3F(Three.js)에서 제공하는 광원
![녹음 2024-05-19 163544](https://github.com/qkrgudals1030/teamAI/assets/50951220/43724420-2c2b-47ba-b5cd-9003db23eba6)


```
import { OrbitControls } from "@react-three/drei";
import { useFrame } from "@react-three/fiber";
import * as THREE from "three"

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
    })
  
    return (
        <>
            <OrbitControls />

            <ambientLight color="#ffffff" intensity={5} />

            <mesh rotation-x={THREE.MathUtils.degToRad(-90)}>
                <planeGeometry args={[10, 10]} />
                
                <meshStandardMaterial 
                    color={"#2c3e50"}
                    roughness={0.5}
                    metalness={0.5}
                    side={THREE.DoubleSide}
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

            {new Array(8).fill().map((item, index) => {
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

            <group name="smallSpherePivot">
                <mesh position={[3, 0.5, 0]}>
                    <sphereGeometry args={[0.3, 32, 32]} />
                    
                    <meshStandardMaterial 
                        color={"#e74c3c"}
                        roughness={0.2}
                        metalness={0.5}
                    />
                </mesh>
            </group>
        </>
    )
}

export default MyElement3D
```

#### ambientLight
![녹음 2024-05-19 164339](https://github.com/qkrgudals1030/teamAI/assets/50951220/9f06f2dc-7d41-4414-9d9d-1ef73c39730e)

```
import { OrbitControls } from "@react-three/drei";
import { useFrame } from "@react-three/fiber";
import * as THREE from "three"

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
    })
  
    return (
        <>
            <OrbitControls />

            {/* intensity : 조명의 강도 */}
            <ambientLight color="#ff0000" intensity={10} />

            <mesh rotation-x={THREE.MathUtils.degToRad(-90)}>
                <planeGeometry args={[10, 10]} />
                
                <meshStandardMaterial 
                    color={"#2c3e50"}
                    roughness={0.5}
                    metalness={0.5}
                    side={THREE.DoubleSide}
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

            {new Array(8).fill().map((item, index) => {
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

            <group name="smallSpherePivot">
                <mesh position={[3, 0.5, 0]}>
                    <sphereGeometry args={[0.3, 32, 32]} />
                    
                    <meshStandardMaterial 
                        color={"#e74c3c"}
                        roughness={0.2}
                        metalness={0.5}
                    />
                </mesh>
            </group>
        </>
    )
}

export default MyElement3D

```

#### HemisphereLight
![녹음 2024-05-19 164712](https://github.com/qkrgudals1030/teamAI/assets/50951220/232a6396-57a7-4e18-bab7-3b92569aa2ee)

```
import { OrbitControls } from "@react-three/drei";
import { useFrame } from "@react-three/fiber";
import * as THREE from "three"

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
    })
  
    return (
        <>
            <OrbitControls />

            {/* 첫번째는 하늘에서 비추는 빛의 색상
                두번째는 땅에서 비추는 빛의 색상
                세번째는 빛의 세기 */}
            <hemisphereLight args={["00f", "#f00", 2]} />

            <mesh rotation-x={THREE.MathUtils.degToRad(-90)}>
                <planeGeometry args={[10, 10]} />
                
                <meshStandardMaterial 
                    color={"#2c3e50"}
                    roughness={0.5}
                    metalness={0.5}
                    side={THREE.DoubleSide}
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

            {new Array(8).fill().map((item, index) => {
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

            <group name="smallSpherePivot">
                <mesh position={[3, 0.5, 0]}>
                    <sphereGeometry args={[0.3, 32, 32]} />
                    
                    <meshStandardMaterial 
                        color={"#e74c3c"}
                        roughness={0.2}
                        metalness={0.5}
                    />
                </mesh>
            </group>
        </>
    )
}

export default MyElement3D

```

#### directionalLight
![녹음 2024-05-19 164956](https://github.com/qkrgudals1030/teamAI/assets/50951220/729aac64-04b7-40f4-892a-67245d8e98db)

```
import { OrbitControls, useHelper } from "@react-three/drei";
import { useFrame, useThree } from "@react-three/fiber";
import { useEffect, useRef } from "react";
import * as THREE from "three"

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
        
        smallSpherePivot.children[0].getWorldPosition(light.current.target.position)
    })

    const light = useRef()

    useHelper(light, THREE.DirectionalLightHelper)
  
    const {scene} = useThree()

    // 광원의 타겟을 장면에 추가
    useEffect(() => {
        scene.add(light.current.target)

        return () => {
            scene.remove(light.current.target)
        }
    }, [light])

    return (
        <>
            <OrbitControls />

            {/* position : 광원의 위치
                target-position : 광원이 향하는 방향의 목표 위치 */}
            <directionalLight 
                ref={light}
                color={"#0xffffff"}
                intensity={1}
                position={[5, 5, 0]}
                target-position={[1, 0, 0]}
            />

            <mesh rotation-x={THREE.MathUtils.degToRad(-90)}>
                <planeGeometry args={[10, 10]} />
                
                <meshStandardMaterial 
                    color={"#2c3e50"}
                    roughness={0.5}
                    metalness={0.5}
                    side={THREE.DoubleSide}
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

            {new Array(8).fill().map((item, index) => {
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

            <group name="smallSpherePivot">
                <mesh position={[3, 0.5, 0]}>
                    <sphereGeometry args={[0.3, 32, 32]} />
                    
                    <meshStandardMaterial 
                        color={"#e74c3c"}
                        roughness={0.2}
                        metalness={0.5}
                    />
                </mesh>
            </group>
        </>
    )
}

export default MyElement3D

```


#### pointLight
![녹음 2024-05-19 165354](https://github.com/qkrgudals1030/teamAI/assets/50951220/1c9d20ce-763b-4610-ba4e-2b54e3102eab)

```
import { OrbitControls, useHelper } from "@react-three/drei";
import { useFrame, useThree } from "@react-three/fiber";
import { useEffect, useRef } from "react";
import * as THREE from "three"

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
       
        smallSpherePivot.children[0].getWorldPosition(light.current.position)
    })

    const light = useRef()

    useHelper(light, THREE.PointLightHelper, 0.5)

    return (
        <>
            <OrbitControls />

        	{/* distance : 점 광원 효과 범위 */}
            <pointLight 
                ref={light}
                color={"#ffffff"}
                intensity={2}
                position={[0, 5, 0]}
                distance={0}
            />

            <mesh rotation-x={THREE.MathUtils.degToRad(-90)}>
                <planeGeometry args={[10, 10]} />
                
                <meshStandardMaterial 
                    color={"#2c3e50"}
                    roughness={0.5}
                    metalness={0.5}
                    side={THREE.DoubleSide}
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

            {new Array(8).fill().map((item, index) => {
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

            <group name="smallSpherePivot">
                <mesh position={[3, 0.5, 0]}>
                    <sphereGeometry args={[0.3, 32, 32]} />
                    
                    <meshStandardMaterial 
                        color={"#e74c3c"}
                        roughness={0.2}
                        metalness={0.5}
                    />
                </mesh>
            </group>
        </>
    )
}

export default MyElement3D
```

#### spotLight
![녹음 2024-05-19 165628](https://github.com/qkrgudals1030/teamAI/assets/50951220/f5082b06-9752-4a3d-933e-fcc5a071f7e9)

```
import { OrbitControls, useHelper } from "@react-three/drei";
import { useFrame, useThree } from "@react-three/fiber";
import { useEffect, useRef } from "react";
import * as THREE from "three"

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
       
        smallSpherePivot.children[0].getWorldPosition(light.current.target.position)
    })

    const light = useRef()
    
    useHelper(light, THREE.SpotLightHelper)

    const { scene } = useThree()

    useEffect(() => {
        scene.add(light.current.target)

        return () => {
            scene.remove(light.current.target)
        }
    }, [light])

    return (
        <>
            <OrbitControls />

            {/* penumbra : 빛의 감쇠율 */}
            <spotLight 
                ref={light}
                color={"0xffffff"}
                intensity={1}
                position={[0, 5, 0]}
                target-position={[0, 0, 0]}
                distance={0}
                angle={THREE.MathUtils.degToRad(30)}
                penumbra={0.1}
            />

            <mesh rotation-x={THREE.MathUtils.degToRad(-90)}>
                <planeGeometry args={[10, 10]} />
                
                <meshStandardMaterial 
                    color={"#2c3e50"}
                    roughness={0.5}
                    metalness={0.5}
                    side={THREE.DoubleSide}
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

            {new Array(8).fill().map((item, index) => {
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

            <group name="smallSpherePivot">
                <mesh position={[3, 0.5, 0]}>
                    <sphereGeometry args={[0.3, 32, 32]} />
                    
                    <meshStandardMaterial 
                        color={"#e74c3c"}
                        roughness={0.2}
                        metalness={0.5}
                    />
                </mesh>
            </group>
        </>
    )
}

export default MyElement3D
```

#### rectAreaLight
```
import { Environment, OrbitControls, useHelper } from "@react-three/drei";
import { useFrame, useThree } from "@react-three/fiber";
import { useEffect, useRef } from "react";
import * as THREE from "three"
import {RectAreaLightUniformsLib} from "three/examples/jsm/lights/RectAreaLightUniformsLib"
import {RectAreaLightHelper} from "three/examples/jsm/helpers/RectAreaLightHelper"

const torusGeometry = new THREE.TorusGeometry(0.4, 0.1, 32, 32)
const torusMaterial = new THREE.MeshStandardMaterial({
    color: "#9b59b6",
    roughness: 0.5,
    metalness: 0.9
})

// 초기화
RectAreaLightUniformsLib.init()

function MyElement3D() {
    useFrame((state) => {
        const time = state.clock.elapsedTime
        const smallSpherePivot = state.scene.getObjectByName("smallSpherePivot")

        smallSpherePivot.rotation.y = THREE.MathUtils.degToRad(time * 50)      
    })

    const light = useRef()
    useHelper(light, RectAreaLightHelper)

    return (
        <>
            <OrbitControls />

            <Environment 
                blur={0.05}
                background
                files={"././public/images/blue_photo_studio_4k.hdr"}
            />

            <rectAreaLight 
                ref={light}
                color="#ffffff"
                intensity={30}
                width={2}
                height={5}
                position={[0, 5, 0]}
                rotation-x={THREE.MathUtils.degToRad(-90)}
            /> 

            <mesh rotation-x={THREE.MathUtils.degToRad(-90)}>
                <planeGeometry args={[10, 10]} />
                
                <meshStandardMaterial 
                    color={"#2c3e50"}
                    roughness={0.5}
                    metalness={0.5}
                    side={THREE.DoubleSide}
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

            {new Array(8).fill().map((item, index) => {
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

            <group name="smallSpherePivot">
                <mesh position={[3, 0.5, 0]}>
                    <sphereGeometry args={[0.3, 32, 32]} />
                    
                    <meshStandardMaterial 
                        color={"#e74c3c"}
                        roughness={0.2}
                        metalness={0.5}
                    />
                </mesh>
            </group>
        </>
    )
}

export default MyElement3D
```

#### Environment
```
import { Environment, OrbitControls, useHelper } from "@react-three/drei";
import { useFrame, useThree } from "@react-three/fiber";
import { useEffect, useRef } from "react";
import * as THREE from "three"
import {RectAreaLightUniformsLib} from "three/examples/jsm/lights/RectAreaLightUniformsLib"
import {RectAreaLightHelper} from "three/examples/jsm/helpers/RectAreaLightHelper"

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

    return (
        <>
            <OrbitControls />

            <Environment 
                blur={0.05}
                background
                files={"././public/images/blue_photo_studio_4k.hdr"}
            />
            <mesh rotation-x={THREE.MathUtils.degToRad(-90)}>
                <planeGeometry args={[10, 10]} />
                
                <meshStandardMaterial 
                    color={"#2c3e50"}
                    roughness={0.5}
                    metalness={0.5}
                    side={THREE.DoubleSide}
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

            {new Array(8).fill().map((item, index) => {
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

            <group name="smallSpherePivot">
                <mesh position={[3, 0.5, 0]}>
                    <sphereGeometry args={[0.3, 32, 32]} />
                    
                    <meshStandardMaterial 
                        color={"#e74c3c"}
                        roughness={0.2}
                        metalness={0.5}
                    />
                </mesh>
            </group>
        </>
    )
}

export default MyElement3D
```
