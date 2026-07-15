---
title:  Position
parent: Interpolations
nav_order: 0
---

![Position](https://github.com/user-attachments/assets/f5c45999-fa11-49e5-a842-812702f93520)

`UBTween.Position` interpolates the position of an object.

# Supported Objects:

| Target  | Value changed (Ref Global) | Value changed (Ref Local)|
| ------------- | ------------- | ------------- |
| `Transform`  | `Transform.position`  | `Transform.localPosition`  |
| `RectTransform`  | `RectTransform.position` | `RectTransform.localPosition`  |

***
<br>

# Use Current Position As Start :
``` cs
UBTween.Position(
    transform,                  // Target Object
    new Vector3(0f, 1f, 0f),    // End Position
    1f);                        // Duration
```
![PositionCurrentToUp](https://github.com/user-attachments/assets/83dbe49d-2f0f-4c2c-b465-0a8553fed969)

***
<br>

# Specify Start Position :
``` cs
UBTween.Position(
    transform,                  // Target Object
    new Vector3(-1f, .5f, 0f),  // Start Position
    new Vector3(1f, .5f, 0f),   // End Position
    1f);                        // Duration
```
![PositionLeftToRight](https://github.com/user-attachments/assets/62916863-8ef3-4df0-8cdf-28395ede546d)


***
<br>

# Referencial:
It's possible to whether translate the local position or the global position by using the `Ref` Enum.

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
    // Going Up
    UBTween.Position(transform, Vector3.zero, Vector3.up, duration, Ref.Local) // Going Up
        .SetEase(EaseType.OutExpo),

    // Going Down
    UBTween.Position(transform, Vector3.up, Vector3.zero, duration, Ref.Local) // Going Down
        .SetDelay(duration)
        .SetEase(EaseType.OutBounce),
}.Start().SetLoop();
```