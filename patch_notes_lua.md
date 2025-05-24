<p align="center">
  <img width="80%" src="./BZCC.png">
</p>

# Lua Updates

| Item | Change | Description |
|--------------|--------------|-------------|
| New Image Functions | Addition | Added LuaMission functions: bool `IFace_IsActive(Name n)`, bool `IFace_IsVisible(Name n)`. These return the Active or Visible status of a given UI element name. Also added `IFace_SetImage(Name n, Name image)`, sets the given UI element name's BG Image. Also added `IFace_SetImageRect(Name n, x0, y0, (opt x1), (opt y1))`  These set the BG image's texture coordinates. The x1 and y1 are optional, if not specified it uses the UI element's `Size()` parameter to auto-calculate the end x1/y1. |
| New Path Functions | Addition | Added LuaMission functions: bool `CreatePath(string name, float x, float z)`, int, bool `AddPathPoint(string , float x, float z)`, bool `RenamePath(string oldname, string newname)`, bool `RemovePath(string name)`, int, bool `RemovePathPoint(string name, int Point)`, bool `SetPathPoint(string name, int point, float x, float z)`. These allow scripts to modify Paths points on a map. The boolean versions return true if it was successful, false if the path specified doesn't exist. The int versions return two different parameters: the number of paths left, and a boolean if successful. If not successful, the number of paths returned will be -1 for an invalid path, or -2 for an invalid point. Success will return the number of points, or 0 if it removed the only point left and the path was removed. |
| New Weapon Functions | Addition | Added LuaMission function bool `GetUseSelectWeapon(Handle h)` and `SetUseSelectWeapon(Handle h, bool set)`. These allow the script to get/set the UseSelectWeapon flag, used to determine if a unit respects WeaponMask. |
| New UI Fade/Menu Functions | Addition | Added LuaMission Functions: `IFace_FadeIn(ConstName n)`, `IFace_FadeOut(ConstName n)`, and bool `IFace_IsMenuMode()`. These trigger a start FadeIn/out of the specified UI element. `IFace_IsMenuMode()` will return true if the IFACE is currently in MenuScale. |
| New Map Boundary Functions | Addition | Added ScriptUtil functions: `GetTerrainMinX()`, `GetTerrainMaxX()`, `GetTerrainMinY()`, `GetTerrainMaxY()`, `GetTerrainMinZ()`, `GetTerrainMaxZ()`. These return the size of the map boundaries. |
| `GetCargo() `| Addition | Added ScriptUtils/LuaMission function `GetCargo(handle h)`. This returns the handle that is being carried by h, if it exists. nil if not tugging anything. |
| `SetPowered()` | Addition | Added Lua function `SetPowered(handl h, int powered)`. Allows scripts to override the powered state of an object. -1 = default, 0 = off, 1 = on. |
| `SetTeamNameForStat()` | Addition | Fixed Lua function `SetTeamNameForStat()` not working in MP end games scores screen. |
| `SetSelected()` | Addition | Added LuaMission callback `SetSelected(Handle h, bool set)`. This is a parallel to "bool IsSelected(Handle h)". |
| `IsUndeployed()` | Addition | Added `IsUndeployed(h)`, `IsDeploying(h)`, and `IsUndeploying(h)` callbacks to LuaMission. These allow scripts to detect these states, similar to `IsDeployed(h)`. |
| `GetGameVersion()` | Addition | Added Lua function int `GetGameVersion()`. This returns the game's version build #. |
| `GetTerrainHeight()` | Addition | Added Lua function float `GetTerrainHeight(pos)`, (pos can be a handle, vector, matrix, path point, like other GetPosition functions). This returns the literal Terrain Height from the map, ignoring buildings or other collide-able objects at the location. |
| `SetAnimationFrame()` | Addition | Added Lua function float `SetAnimationFrame(handle, name, frame)`. This is a parallel to GetAnimationFrame, but lets you pass in a specific key frame to set the animation to. |
| `GetSessionPlayerID() `| Addition | Added Lua function int `GetSessionPlayerID(team)`. This returns a unique ID for a specific player, valid for this game session only. |
| `IsObjectiveOn()` | Addition | Added Lua functions: bool `IsObjectiveOn(Handle, team)`, `SetObjectiveOn(Handle, Team)`, `SetObjectiveOff(Handle, Team)`, bool `IsObjectiveToUser(Handle)`. These work similarly to the existing `SetObjectiveOn()`, but allow per-team control. Also added a Get parallel to tell if an object is currently Objectified to a specific Team. |
| `GetVarItemStr()` | Addition | Added `GetVarItemStr()` and `GetVarItemInt()` to AIP Lua callbacks. They mirror the functionality of their LuaMission counterparts. |
| `StartEarthQuake()` | Addition | Added to LuaMission function `StartEarthQuake(float magnitude, float volume = -1.0)` and `UpdateEarthQuake(float magnitude, float volume = -1.0)` an optional volume parameter. This is a volume between 0.0 and 1.0. Default value of -1.0 is unchanged, and uses the scale of the earthquake to control the volume (magnitudes > 1.0 always are at full volume) |
| AudioHandle | Addition | Added to LuaMission Function `AudioHandle StartAudio2D(string filename, number Volume, number Pan, number Rate, bool Loop = false, bool IsMusic = false, bool isVoice = false, bool isNonShellSFX = false)`, 2 new volume level booleans as input arguments. |
| `SetCirclePos()` | Addition | Added LuaMission function `SetCirclePos(const Vector centerPos, const float Radius, const float Angle, Vector &NewPos)`. This function already existed, but wasn't exposed to scripts. It calculates a radial position from a central point, at the given radius (distance) and angle. |
| `GetLockstepTurn() `| Addition | Added LuaMission function long `GetLockstepTurn()`, this returns the turn count from the game. |
| `ChatMessageSent()` | Addition | Added LuaMission function: `ChatMessageSent()` ScriptUtils callback function. Function passes in the timestep it was sent on, and also filter to only run on Chat sent to HASH_ID_ALL. |
| GetIsAssault() | Addition | Added LuaMission function `GetIsAssault(Handle h)`, and `SetIsAssault(Handle h, bool isAssault)`. These allow scripts to get and set the isAssault flag on a handle. |
| `BuildExplosion()` | Addition | Added LuaMission function `BuildExplosion(odf, location, owner)`. This function resembles the one from BZ1's TRO expansion, allowing scripts to spawn Explosions at a given location. |
| `FlagDrop()` | Addition | Added FlagDrop(Handle flag, Handle holder) ScriptUtils function. |
| `ObjectKilled/RemoveObject() `| Fix | Fixed several Lua functions not working correctly when being called in `ObjectKilled/RemoveObject()`: `GetEjectRatio, SetEjectRatio, GetDistance, IsWithin, GetNearestObject, GetNearestVehicle, GetNearestBuilding, GetNearestEnemy, GetNearestPerson, CountUnitsNearObject GetCurrentCommand, GetCurrentWho, HoppedOutOf, GetHealth, GetCurHealth, GetMaxHealth, GetAmmo, GetCurAmmo, GetMaxAmmo, GetWhoShotMe, GetLastEnemyShot, GetLastFriendShot, GetFront, GetTug, IsDeployed, GetVelocity, GetScavengerCurScrap, GetScavengerMaxScrap, GetCategoryTypeOverride, GetCategoryType, IsFollowing, WhoFollowing, GetOwner, GetRemainingLifespan, GetIndependence, GetGroup, GetWeaponMask, GetLifeSpan, GetCurrentCommandWhere, GetOmega, IsCraftButNotPerson, IsCraftOrPerson, IsBuilding, IsPowerup, GetCanSnipe, GetLookFront, IsPowered, GetEmitterMask`. |
| Require | Fix | LuaMission: Fixed `#require` not working correctly out of the box. |
| `AllowRandomTracks()` | Fix | Fixed LuaMission function `AllowRandomTracks()` not working. |
| `GetPositionNear()` | Fix | Fixed LuaMission `GetPositionNear()` not working properly for off-map spawns. If all the tries fail, just return a random position. |
| ScriptUtils | Fix | Fixed CTF Flag Carrier staying highlighted if they are sniped/hopped out. |
| `GetVarItemStr()` | Fix | Fixed LuaMission `GetVarItemStr()` not working properly. |
| `CountUnitsNearObject()` | Fix | Fixed LuaMission `CountUnitsNearObject()` not working when a Handle is passed in. |
| `GetPositionNear()` | Fix | Fixed LuaMission `GetPositionNear()` path point not being optional as intended. |
| `GetNextRandomVehicleODF()` | Fix | Fixed LuaMission `GetNextRandomVehicleODF()` not using it's return parameters. |
| `Damage()` | Fix | Fixed LuaMission `Damage()` function not working with large values. |
| `ReplaceObject()` | Fix | Fixed LuaMission `ReplaceObject()` possibly crashing when an object's Label length is too long. |
| `PostLoad()` | Fix | Fixed LuaMission missing call to `PostLoad() ` function. |
| `EjectKillRetCodes` | Fix | Fixed LuaMission missing `EjectKillRetCodes` table. |
| Decoda | Fix | Fixed Decoda not being able to hook into LuaMission. |
| LuaMission | Fix | Fixed a bad return value in one of the Vector math functions. |
| `SetUseSelectWeapon()` | Removal | Removed LuaMission `SetUseSelectWeapon()` function, did not work and would cause Bad Assets. |
| `SetAIP()`→`SetPlan()` | Rename | LuaMission: Changed name of `SetAIP()` to `SetPlan()` to match the BZ2/BZCC function name. `SetAIP()` still exists and is the backwards compatibility name for BZ1/BZ98R scripts ported over. |