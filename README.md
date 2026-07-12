# 2026_06_24_unity_hexa_chess_mirror_phone

> Phone version of the Hexa Chess XR Game.

Note that Mirror isn't designed to work across different scenes,
let alone across separate projects.

However, the player prefab network does work cross project.

It is for phone but my code is design for XR. 
So they are a dependency to those tools:
["com.unity.xr.interaction.toolkit"](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@3.0/manual/index.html)   
["open.xr"](https://docs.unity3d.com/Packages/com.unity.xr.openxr@1.17/manual/index.html)    


```
        public static void GetWorldToLocal_DirectionalPoint(in Vector3 worldPosition, in Quaternion worldRotation, in Vector3 positionReference, in Quaternion rotationReference, out Vector3 localPosition, out Quaternion localRotation)
        {
            localRotation = Quaternion.Inverse(rotationReference) * worldRotation;
            localPosition = Quaternion.Inverse(rotationReference) * (worldPosition - positionReference);
        }

        public static void GetLocalToWorld_DirectionalPoint(in Vector3 localPosition, in Quaternion localRotation, in Vector3 positionReference, in Quaternion rotationReference, out Vector3 worldPosition, out Quaternion worldRotation)
        {
            /// I need to verify the commutativity of this code. 
            /// I think it was ok then had a bug in a game link to this methode and thr commutative property
            worldRotation = rotationReference * localRotation;
            worldPosition = (rotationReference * localPosition) + (positionReference);
        }
```
