---
title:  UBTweening
parent: UBTools
---

<img alt="UBTweening" src="https://github.com/user-attachments/assets/db7a3a4a-d8d3-426e-8118-e35c951a3f93" />

# UnBocal Tweening System
v1.0
{: .label .label-blue }

# The wiki is still under construction

Made by **UnBocal** - **LUPON Dylan**

**Unity 2022.3.62f2 or greater.**

*Small tweening system made for Unity inspired by [**DoTween**](https://dotween.demigiant.com/documentation.php)* and the [**Ama Motion Automatiser**](https://github.com/TasDeNeige/AmaMotionAutomatiser).

# What Is It :

The UBTweening System (for Un Bocal Tweening System) is an coroutine based interpolation manager. It can be used to make simple animations from code.

I wanted to make my own tweening system, since i used to make all my juiciness with tweens.

# Compatibility & Installation :
You can download the plugin [here](https://github.com/dlupon/UBTweening) on the github page.
This plugin was made for **Unity 2022.3.62f2** or greater.

# How To Use :

## Import :
The UBTweening System is for moment only usable through scripts.

Before doing anything, you need to get the `UnBocal.Tweening` namespace.
```cs
using UnBocal.Tweening;
```

***
<br>

## Method General Structure :
Each interpolation method is static and can be called from the UBTween class.

Here is an exemple of a tween interpolating the [[Position]] :
``` cs
// Interpolate The Transform Position From Current Position To The Target Position In 1 Second
UBTween.Position(transform, transform.position, Vector3.up, 1f);

// An Other Way Of  Doing The Same Action
UBTween.Position(transform, Vector3.up, 1f);
```

***
<br>


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