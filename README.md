
360° Image Viewer in Unity (WebGL Compatible)

This project allows users to view 360° panoramic images interactively in Unity and deploy the experience as a WebGL-based website. It supports mouse-based navigation and is designed for lightweight, immersive viewing.



## Project Overview

- Load equirectangular 360° images into Unity
- Display them using a panoramic skybox
- Enable mouse drag and right-click rotation
- Build and deploy as a WebGL application

---

## 🛠 Prerequisites

- Unity 2021.3 LTS or newer
- WebGL Build Support (install via Unity Hub)
- 360° panoramic image (2:1 aspect ratio, e.g., 4096×2048)

---

## 🖼 Step 1: Load 360° Image into Unity

1. **Import your image**  
   Drag your `.jpg` or `.png` 360° image into the Unity `Assets` folder.

2. **Create a Skybox Material**  
   - Right-click in Assets → `Create > Material`
   - Name it `Skybox360`
   - Set Shader to `Skybox/Panoramic`
   - Assign your image to the `Texture` slot
   - Set Mapping to `Latitude-Longitude Layout`
   - Set Image Type to `360 Degree`

3. **Apply the Skybox**  
   - Go to `Window > Rendering > Lighting`
   - In the `Environment` tab, assign `Skybox360` to `Skybox Material`

---

## Step 2: Enable Mouse Interaction

# 2.1 Add Mouse Look Script

Create a new C# script called `MouseLook.cs` and attach it to the `Main Camera`.

```csharp
using UnityEngine;

public class MouseLook : MonoBehaviour
{
    public float sensitivity = 2.0f;
    public float smoothing = 2.0f;

    private Vector2 velocity;
    private Vector2 frameVelocity;

    void Update()
    {
        if (Input.GetMouseButton(1)) // Right-click to rotate
        {
            Vector2 mouseDelta = new Vector2(Input.GetAxis("Mouse X"), Input.GetAxis("Mouse Y"));
            mouseDelta *= sensitivity * smoothing;
            frameVelocity = Vector2.Lerp(frameVelocity, mouseDelta, 1f / smoothing);
            velocity += frameVelocity;

            transform.localRotation = Quaternion.AngleAxis(-velocity.y, Vector3.right);
            transform.localRotation *= Quaternion.AngleAxis(velocity.x, Vector3.up);
        }
    }
}
