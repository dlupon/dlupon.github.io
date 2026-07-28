---
title:  How To Use
parent: UBTweening
nav_order: 0
---

# How To Use :

## Import :
The UBTweening System is for moment only usable through scripts.

Before doing anything, you need to get the `UnBocal.Tweening` namespace.
```cs
using UnBocal.Tweening;
```




## Method General Structure :
Each interpolation method is static and can be called from the UBTween class.

Here is an exemple of a tween interpolating the [[Position]] :
``` cs
// Interpolate The Transform Position From Current Position To The Target Position In 1 Second
UBTween.Position(transform, transform.position, Vector3.up, 1f);

// An Other Way Of  Doing The Same Action
UBTween.Position(transform, Vector3.up, 1f);
```




## Controls :
To control the behavior of an interpolation you can use the controls method at the end of the instruction such as :

### [[SetDelay]]`(float duration)` :
To add a delay before the execution of the interpolation.
``` cs
// Start Interpolate After delay seconds
UBTween.Position(transform, Vector3.up, 1f)
    .SetDelay(1f);
```
> *Note that for the moment, the start position will be the position of the transform at the moment where the method is called.*
<br>


### [[SetEase]]`(EaseType ease)` :
To ease the interpolation and give it a little style. :]
``` cs
// Ease The Interpolation
UBTween.Position(transform, Vector3.up, 1f)
    .SetEase(EaseType.InOutExpo);
```
<br>



### [[SetCurve]]`(AnimationCurve curve)`
To ease the interpolation following a curve.
``` cs
// Ease The Interpolation Based On A Curve
UBTween.Position(transform, Vector3.up, 1f)
    .SetCurve(curve);
```
<br>

### [[SetLoop]]`()` 
To loop the interpolation.
``` cs
// Every 
UBTween.Position(transform, targetPosition, 1f)
    .SetLoop()
```
<br>

## And you can combine them !
``` cs
// Start Interpolate After delay seconds
UBTween.Position(transform, Vector3.up, 1f)
    .SetDelay(1f)
    .SetEase(EaseType.InOutExpo)
```

***
<br>

## Callbacks :
You have three callbacks possible :

### [[OnStart]]`(UnityAction method)` :
Will be called when the interpolation starts (After the delay).
``` cs
UBTween.Position(transform, Vector3.up, 1f)
    .OnStart(method);
```
<br>

### [[OnLoop]]`(UnityAction method)` :
Will be called at the end of every loop.
``` cs
UBTween.Position(transform, Vector3.up, 1f)
    .SetLoop()
    .OnLoop(method);
```
<br>

### [[OnFinished]]`(UnityAction method)` : 
Will be called when the interpolation stops.
``` cs
UBTween.Position(transform, Vector3.up, 1f)
    .OnFinished(method);
```
<br>