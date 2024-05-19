### 3D 모델 / 애니메이션

#### 모델 애니메이션 여러개를 같이 사용

# 결과 실행 영상


https://github.com/qkrgudals1030/teamAI/assets/50895748/ca7b1a9e-c015-4160-9005-0e5ed75063db


```
import { Environment, OrbitControls, useAnimations, useGLTF } from "@react-three/drei";
import { useControls } from "leva";
import { useEffect, useState } from "react";

function MyElement3D() {
    const model = useGLTF("././models/model.glb")
    const animations = useAnimations(model.animations, model.scene)

    const {actionName} = useControls({
        actionName: {
            value: animations.names[1],
            options: animations.names
        }
    })

    useEffect(() => {
        const action = animations.actions[actionName]
        action.reset().fadeIn(0.5).play()

        return () => {
            action.fadeOut(0.5)
        }
    }, [actionName])

    const [height, setHeight] = useState(0)

    useEffect(() => {
        let minY = Infinity, maxY = -Infinity

        model.scene.traverse((item) => {
            if(item.isMesh) {
                const geomBbox = item.geometry.boundingBox

                if(minY > geomBbox.min.y) minY = geomBbox.min.y
                if(maxY < geomBbox.max.y) maxY = geomBbox.max.y
            }
        })

        const h = maxY - minY

        setHeight(h)

        console.log(h)
    }, [model.scene])

    return (
        <>
            <OrbitControls />

            <Environment preset="sunset" />

            <primitive 
                object={model.scene} 
                scale={5}
                position-y={-(height/2) * 5}
            />
        </>
    )
}

export default MyElement3D
```
