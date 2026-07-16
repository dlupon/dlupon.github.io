---
title:  Scale
parent: Interpolations
nav_order: 2
---

![Scale](.\Assets\Scale.gif)


`UBTween.Scale` interpolates the scale of an object.

# Supported Objects:

| Target  | Value changed |
| ------------- | ------------- |
| `Transform`  | `Transform.localScale`  |
| `RectTransform`  | `RectTransform.localScale` |






# Use Current Scale As Start :
``` cs
UBTween.Scale(
    transform,      // Target Object
    Vector3.zero,   // End Scale
    1f);            // Duration
```

Using float will set all the axis to that number :
``` cs
UBTween.Scale(
    transform,  // Target Object
    0f,         // End Scale
    1f);        // Duration
```

![Scale_0](.\Assets\Scale_0.gif)






# Specify Start Scale :
```cs
UBTween.Scale(
    transform,          // Target Object
    Vector3.zero,       // Start Scale
    Vector3.one * 2,    // End Scale
    1f);                // Duration
```

Using float will set all the axis to that number :
```cs
UBTween.Scale(
    transform,  // Target Object
    0f,         // Start Scale
    2f,         // End Scale
    1f);        // Duration
```

![Scale_0](.\Assets\Scale_1.gif)






# Gif Code :
``` cs
UBTween.Sequence sequence = new UBTween.Sequence()
{
    UBTween.Scale(transform, scale, 1)
        .SetEase(EaseType.OutExpo),

    UBTween.Scale(transform, scale, Vector3.one, 1)
        .SetEase(EaseType.OutElastic)
        .SetDelay(1f)
}.SetLoop().Start();   
```