---
title:  Scale
parent: Interpolations
nav_order: 2
---

![Scaling](https://github.com/user-attachments/assets/e5177acf-bbe5-478e-8e72-341ada64d080)


`UBTween.Scale` interpolates the scale of an object.

# Supported Objects:

| Target  | Value changed |
| ------------- | ------------- |
| `Transform`  | `Transform.localScale`  |
| `RectTransform`  | `RectTransform.localScale` |

***
<br>

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

![ScalingUp](https://github.com/user-attachments/assets/d3e63d45-512d-490e-a2e8-da2d11db0b1b)

***
<br>

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

![ScalingDown](https://github.com/user-attachments/assets/ebbbcf66-a423-46fc-9135-6a99d4027ff9)


***
<br>

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