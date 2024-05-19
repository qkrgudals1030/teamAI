### Postprocessing(후처리)

Postprocessing 개념
블러, 그림자, 밝기 및 대비, 색조, 도트 등의 효과를 넣어 렌더링하기 위해서는 후처리 과정이 필요함. 우리가 눈으로 보는 3D 렌더링 결과는 아래의 과정을 통해 보여짐.

### HueSaturation (색상, 채도)

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/c47cbe41-9da1-4724-80ec-d1e16c89a0f4)

```
// hue: 색조
// saturation: 채도
<EffectComposer disableNormalPass enabled={enabled}>
  <HueSaturation
    hue={hue}
    saturation={saturation}
  />
</EffectComposer>
```

### BrightnessContrast (밝기, 대비)

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/c4fd292f-51e0-476a-92c9-a042ac6e99c5)


```
// brightness: 밝기
// contrast: 대비
<EffectComposer disableNormalPass enabled={enabled}>
  <BrightnessContrast
    brightness={brightness}
    contrast={contrast}
  />
</EffectComposer>
```

### DotScreen (도트 패턴, 도트 크기)

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/fdb1b396-0948-41e1-88c0-f744e236ee96)

```
// angle: 도트 패턴의 방향
// scale: 도트 크기
<EffectComposer disableNormalPass enabled={enabled}>
  <DotScreen
    angle={angle}
    scale={scale}
  />
</EffectComposer>
```

### Bloom (빛의 효과)

![image](https://github.com/qkrgudals1030/teamAI/assets/50895124/b649ee48-2a7a-4f24-a2c9-11ce95a83688)

```
// intensity: 빛 반사 강도
// mipmapBlur: 빛 반사 사용 여부
// luminanceThreshold: 빛 반사 효과 적용될 최소 밝기 임계값
// luminanceSmoothing: 빛 반사 효과 적용될 최대 밝기 임계값
<EffectComposer disableNormalPass enabled={enabled}>
  <Bloom
    intensity={intensity}
    mipmapBlur={mipmapBlur}
    luminanceThreshold={luminanceThreshold}
    luminanceSmoothing={luminanceSmoothing}
  />
</EffectComposer>

```


