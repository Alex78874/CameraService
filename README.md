Original at -> https://github.com/LugicalDev/CameraService

## What changes :
### LockCameraPanningPart
```lua
--> @LockCameraPanningPart: locks panning based on the look vector of a part.
function CameraService:LockCameraPanningPart(lockXAxis: boolean, lockYAxis: boolean, Part: BasePart) 
	assert(Part:IsA("BasePart"), "[CameraService] 3rd parameter should be a BasePart for :LockCameraPanning()")
	
	local lookVector = -Part.CFrame.LookVector
	local angle = Vector2.new(
		math.atan2(lookVector.X, lookVector.Z),
		math.asin(-lookVector.Y)
	)

	--> Set up the camera orientation
	self.atX = angle.X or 0
	self.atY = angle.Y or 0

	--> Lock if necessary
	self.xLock = lockXAxis
	self.yLock = lockYAxis
end
```
Exemple of usage:
```lua
local MenuCamera = workspace:WaitForChild("MenuCamera")
CameraService_Module.SetCameraHost(CameraService_Module, MenuCamera)
CameraService_Module:LockCameraPanning(true, true, MenuCamera)
```
