---
title:  How To Use
parent: UBPooling
nav_order: 0
---

# How To Use :

## Import :

Before doing anything, you need to get the `UnBocal.Pooling` namespace.
```cs
using UnBocal.Pooling;
```

## Compatibilities And Basic Knowleges : 

The UBPooling System can be used on prefabs and components. It can instantiate object, store them and pull them when needed.

The pooling will be automatic as long as you use the provided methodes.

## Initialize Pool : 

Let's say, we have a bullet prefab that contains the ``Bullet`` ``MonoBehaviour``.

``` cs
using UnityEngine;

public class Bullet : MonoBehaviour
{
  // [Some Code]
}
```  

Calling ``static`` ``Init`` will initialize the bullet prefab pool.
```cs
UBPoolObject<Bullet>.Init(_prefab); // Initialize Pool
```

This method also allow you to get an empty ``Wrapper``.
``` cs
UBPoolObject<Bullet> pooledBullet;
UBPoolObject<Bullet>.Init(_prefab, out pooledBullet); // Initialize Pool And Get Wrapper Instance
```

*Calling ``static`` ``Init`` several time won't create more pools.*

## Wrapper : 

### Properties :

`UBPoolObject<Bullet> pooledbullet` is a wrapper that can contain a reference of a instance.

An empty ``wrapper`` has no instance. But it doesn't mean that it's not connected to the pool.

A filled ``wrapper`` contains an instance that has been pull out of the pool.

If needed, calling ``static`` ``Init`` will create a empty ``Wrapper``.
``` cs
UBPoolObject<Bullet> pooledBullet;
UBPoolObject<Bullet>.Init(_prefab, out pooledBullet); // Initialize Pool And Get Wrapper Instance
``` 

Calling ``GetInstance`` will create a filled ``Wrapper``. 
``` cs
UBPoolObject<Bullet> poolObject = UBPoolObject<Bullet>.GetInstancePrefab(_prefab);
```

``isEmpty`` tells if the ``Wrapper`` is empty of filled
```cs
public bool isEmpty { get; }
// filled = false
// empty  = true
```
 

In a filled ``Wrapper``, we have acces to the `Prefab`, `Instance`, `GameObject`, `Transform` and `RectTransform` (*if the instance contains one*)

``` cs
public T prefab { get; }
public T instance { get; }

public GameObject gameObject { get; }
public Transform transform { get; }
public RectTransform rectTransform { get; }
```


``stored`` is a callback invoked when the instance is pul back in the pool.
``` cs
public Action stored { get; }
```

### Methods :

``GetInstance`` gets an instance from the pool.
``` cs
public void GetInstance(Transform parent = null);
```

``Store`` empties the wrapper and store the instance in the pool.
``` cs
public void Store();
```

## Instatiate :
Now that the pool is Initialized, it's time to get new instances.

Calling ``static`` ``GetInstancePrefab`` will pull out an instance from the pool and create a ``Wrapper``.
``` cs
public static UBPoolObject<Bullet> GetInstancePrefab(Bullet prefab, Transform parent = null)
```

If a ``Wrapper`` already exist, calling ``GetInstance`` from it empties it, pull out an instance from the ``Wrapper`` and stores it in the ``Wrapper``.
``` cs
public bool GetInstance(Transform parent = null)
```


## Store A Pooled object

There is two ways of putting back an instance in the pool.

From the ``Wrapper``.
```cs
public void Store()
```

From the static class.
```cs
UBPoolObject<Bullet>.Store(poolObject);
```

If the ``Wrapper`` contains an valid instance, it will store it in the pool and call the ``stored`` callback.
``` cs
public Action stored { get; } // called when the Instance has been stored
```

## Listen Pool From The Pooled Class

It is possible to listen from the pooled Class when the current object is put in or pull out of the pool.

It is also possible to store the instance from the instance it-self.

The class juste need to implement the ``I_UBPoolObjectListener`` interface.

```
public interface I_UBPoolObjectListener
{
    public void OnPulled(Action storeMethod);

    public void OnStored();
}
```

``storeMethod`` is an event that, when invoked will store the current instance in the pool.