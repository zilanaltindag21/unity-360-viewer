RICOH Theta X Camera - Findings: 
This document summarizes testing of the Ricoh Theta X camera with different resolutions and file sizes. The goal is to evaluate image quality, metadata availability, and compatibility with Unity’s 360° viewer pipeline.

Camera Specifications: 
Supports image resolutions: 5.5 k / 11k
File formats: JPEG, RAW (DNG), MP4

Metadata: EXIF (GPS, orientation, timestamp, camera settings)

Tested different resolution images: 

5.5k (15mp) - 4.4mb     Good detail, faster load in Unity
11k  (60mp) - 10.9mb    Excellent detail, slower load in Unity 

Metadata Findings: EXIF data includes GPS coordinates, orientation, timestamp, and camera settings. Metadata extraction works consistently across resolutions.

Connectivity: Camera connects reliably to the Ricoh Theta mobile app (Android/iOS).
Images and videos can be viewed, transferred, and managed via the phone app.
Direct connection to a laptop (via USB or Wi‑Fi) is unreliable as camera fails to be recognized as a storage device.

Recommendations:
Use 5.5k resolution when capturing images. 
