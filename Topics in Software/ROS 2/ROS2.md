# Service - Client:
- **Resource folder** contains an empty file with the package name. Used to index and locate package
- **Custom service definition:** accepts filename parameter. 
	- Created in **CMake** with `rosidl_default_generators` but can be used by **Python**, cannot be created in an `ament_python` package
	- Add `srv` folder and the custom service structure inside. Eg of custom service called `PlayAudio`:
``` text
string filename 
--- 
bool success 
string message
```
- Calling the service: `ros2 service call /play_audio go2_audio_interfaces/srv/PlayAudio "{filename: 'your_audio_file.wav'}"` 
- **Include custom service in files:**
``` cpp
#include <[package]/srv/[name of service]>
```

