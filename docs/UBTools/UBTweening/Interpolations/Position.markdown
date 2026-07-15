---
title:  Position
parent: Interpolations
nav_order: 0
---

![Position](.\Assets\Position.gif)

`UBTween.Position` interpolates the position of an object.

# Supported Objects:

| Target  | Value changed (Ref Global) | Value changed (Ref Local)|
| ------------- | ------------- | ------------- |
| `Transform`  | `Transform.position`  | `Transform.localPosition`  |
| `RectTransform`  | `RectTransform.position` | `RectTransform.localPosition`  |






# Use Current Position As Start :
``` cs
UBTween.Position(
    transform,                  // Target Object
    new Vector3(0f, 1f, 0f),    // End Position
    1f);                        // Duration
```
![Position](.\Assets\Position0.gif)






# Specify Start Position :
``` cs
UBTween.Position(
    transform,                  // Target Object
    new Vector3(-1f, .5f, 0f),  // Start Position
    new Vector3(1f, .5f, 0f),   // End Position
    1f);                        // Duration
```
![Position](.\Assets\Position1.gif)






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