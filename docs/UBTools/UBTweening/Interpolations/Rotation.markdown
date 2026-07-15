---
title:  Rotation
parent: Interpolations
nav_order: 1
---

![Rotation](https://github.com/user-attachments/assets/560e9f1a-e785-49c3-9fad-7555316c2296)

There is two ways to interpolate the rotation of a transform :
- `UBTween`.[Rotation](https://github.com/dlupon/UBTweening/wiki/Rotation#Rotation) will take the shorstest path to the target Rotation. It's not possible to make roation of more than 180d.
- `UBTween`.[ExactRotation](https://github.com/dlupon/UBTweening/wiki/Rotation#exactrotation-) will be able to make rotation of more than 180d.

# Supported Objects:

| Target  | Value changed (Ref Global) | Value changed (Ref Local)|
| ------------- | ------------- | ------------- |
| `Transform`  | `Transform.rotation`  | `Transform.localRotation`  |
| `RectTransform`  | `RectTransform.rotation` | `RectTransform.localRotation`  |

***
<br>

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

![Rotation 90 To -90](https://github.com/user-attachments/assets/274026be-8a24-4bed-9caa-4a600025e5a1)

***


<br>

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

***
<br>

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

***
<br>

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


***
<br>

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