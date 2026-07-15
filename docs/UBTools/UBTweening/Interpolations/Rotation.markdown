---
title:  Rotation
parent: Interpolations
nav_order: 1
---

![Rotation](.\Assets\Rotation.gif)

There is two ways to interpolate the rotation of a transform :
- `UBTween`.[Rotation](https://github.com/dlupon/UBTweening/wiki/Rotation#Rotation) will take the shorstest path to the target Rotation. It's not possible to make roation of more than 180d.
- `UBTween`.[ExactRotation](https://github.com/dlupon/UBTweening/wiki/Rotation#exactrotation-) will be able to make rotation of more than 180d.

# Supported Objects:

| Target  | Value changed (Ref Global) | Value changed (Ref Local)|
| ------------- | ------------- | ------------- |
| `Transform`  | `Transform.rotation`  | `Transform.localRotation`  |
| `RectTransform`  | `RectTransform.rotation` | `RectTransform.localRotation`  |






# Rotation

## Use Current Rotation As Start :
``` cs
UBTween.Rotation(
    transform,                                  // Target Object
    Quaternion.AngleAxis(90f, Vector3.forward), // End Rotation
    1f);                                        // Duration
```
Using ``float`` will use ``UBTween.RotationAxis`` by default, (you can change the value to suit your needs):
``` cs
UBTween.Rotation(
    transform,  // Target Object
    90f,        // Target Angle
    1f);        // Duration
```

![Rotation 90 To -90](.\Assets\Rotation0.gif)





## Specify Start Rotation :
```cs
UBTween.Rotation(
    transform,                                      // Target Object
    Quaternion.AngleAxis(90f, Vector3.forward),     // Start Rotation
    Quaternion.AngleAxis(-90f, Vector3.forward),    // End Rotation
    1f);                                             // Duration
```
Using ``float`` will use ``UBTween.RotationAxis`` by default, (you can change the value to suit your needs):
``` cs
UBTween.Rotation(
    transform,      // Target Object
    90f,            // Start Angle
    -90f,           // End Angle
    1f);            // Duration
```






# ExactRotation :

```
UBTween.ExactRotation(
    transform,              // Target Object
    transform.rotation,     // Start Rotation
    360f,                   // Angle
    Vector3.up,             // Axis
    1f);                    // Duration
```

```cs
UBTween.ExactRotation(
    transform,      // Target Object
    360f,           // Angle
    Vector3.up,     // Axis
    1f);            // Duration
```






# Referencial :
It's possible to whether translate the local rotation or the global position by using the `Ref` Enum.

| Target | Value changed (Ref Global) | Value changed (Ref Local)|
| ------------- | ------------- | ------------- |
| `Transform`  | `Transform.position`  | `Transform.localPosition`  |
| `RectTransform`  | `RectTransform.position` | `RectTransform.localPosition`  |






### From Current
``` cs
UBTween.Position(
    transform,                  // Target Object
    new Vector3(0f, 1f, 0f),    // End Position
    1f,                         // Duration
    Ref.Global);                // Ref
```






### From Specific Start
``` cs
UBTween.Position(
    transform,                  // Target Object
    new Vector3(-1f, .5f, 0f),  // Start Position
    new Vector3(1f, .5f, 0f),   // End Position
    1f,                         // Duration
    Ref.Local);                 // Referencial
```






# Gif Code :
``` cs
UBTween.Sequence sequence = new UBTween.Sequence()
{
    // 0f To 180f
    UBTween.ExactRotation(transform, 180f, .5f)
        .SetEase(EaseType.InBack),

    UBTween.ExactRotation(transform, 180f, 360f, 1f)
        .SetEase(EaseType.OutElastic)
        .SetDelay(.5f),

}.Start().SetLoop();
```