<p align="center">
  <img width="80%" src="./BZCC.png">
</p>

# Patch Notes
A centralized repository for tracking patch notes, version updates, and changelogs across Battlezone Combat Commander.

Some of the following changes were separately categorized, and you can view them here:
- **[Read updates to Lua](patch_notes_lua.md)**
- **[Read updates to ODFs](patch_notes_odf.md)**
- **[Read updates to game files](patch_notes_files.md)**

## Changelog - Build 2.0.186.0:
- Attempt to make VarScope DeleteItem more robust against CRC Collisions. (NODELETE crash)
- Fixed Construction Rigs walking around to the front of a building to Upgrade it.
- Fixed units having slightly jittery movement in Multiplayer unless they were Targeted.
- Fixed ODF feature NavIsDropped = true not working correctly in Multiplayer.
- Fixed QuakeBlast not working correctly in Multiplayer.
- Fixed QuakeBlast not expiring if magnitude and quakeTime were 0, also fixed crash if quakeTime was 0.
- Fixed Shell Music trying to stop "mire22_4.wav" when the Instant Action launch button is pressed when no map is selected. Made the Instant Action Launch button hidden until a map is Selected.
- Fixed Addon preview image appearing White when no Addon is selected.
- Fixed several missing items in game.bakeassets command (Explosions, detailTexture, AIP scav/cons/service units), and fixed it not taking geometryScale / cockpitScale / shotScale into account when building msh files.
- Fixed command mesh.load not taking shotScale into account.
- Fixed crash when extremely long messages print to the Log file.
- Fixed warping Scavengers in Multiplayer caused by Silo class objects not being flagged as important in render culling.
- Fixed TeamHazards not updating if the object's Perceived Team was changed.
- Fixed warping in AI when they change strafe direction in Multiplayer.
- Fixed GunTowerProcess not being able to use Lockon and Chargegun type weapons.
- Minor optimization for Scavenger class objects with DoDrop = true.
- Made HoverCraft with FlyingPhysics = true and SAV class unit's Altitude Lookahead more consistent with APC/Bomber/Artillary.
- Fixed Service Trucks continuously trying to give Gun Towers ammo.
- Fixed several AI classes not taking friendly relationship into account when targeting a unit. This fixes Friendly AI continuing to fire on a ship after a player snipes and hops into it. (or it changes teams/PTeam)
- Fix for AI Pathing: AI doesn't try to displace destination node by collisionRadius. This fixes AI having severe problems reaching their destination on units with large collision radius.
- Restored original AI Avoidance code. This was present in the original game, and helps AI navigate around each other/obstacles.
- Fixed CameraPod objects not spinning after they've landed.
- Fixed Recyclers not fully supporting CategoryTypeOverride ODF feature. Several places in code still expected Recycler to be in BaseSlot 1. Code now checks all 9 BaseSlot items for the first Recycler object it finds.
- Fixed camera getting stuck in the Factory or Satellite view if their Pilot died while logged into it.
- Fixed CommVehicle / CommVehicleH leaving the player stuck in Satellite view when destroyed.
- Fixed DeployBuilding/DeployBuildingH (Recyclers) sometimes not setting the correct Height, which caused some adjacent terrain squares to not be build-able despite them being marked Green.
- Fixed Player driving DeployBuilding/DeployBuildingH not working correctly. Added [DeployBuildingClass] / [DeployBuildingHClass]::maxDeployDist = 25.0f. This is the distance tolerance used by DoExtraBuildZoneCheck.
- Fix for Recycler "double scrap" cost bug in Multiplayer. Ensure that the Recycler is not already building something before it starts the build/charges scrap.
- Fixed Scrap sometimes spawning on top of Gun Tower / Spire when they are destroyed.
- Fixed Scavengers sometimes choosing the wrong terrain tile when deploying on a Pool.
- Fixed edge case in Deployable/TrackedDeployable where the Player cancelling Deploy before the object slid into place could fail to call FinishUndeploy, which could leave a Pool locked from StartDeploy.
- Added factory dropoff and flag stands to the list of pre-loaded ODFs. This prevents custom recycler factions from triggering "uh-oh, late loading ..." messages when there are custom factions on the map in Multiplayer.
- Fixed APCs deleting the player if the script set the player as one of the APC's deployed soldier objects.
- Fixed Armory charging double scrap if you tried to order another powerup while one was already building.
- Fixed LaserMissile and LaserPopper class weapons not working for Pilots.
- Fixed a few places where the initial shot of a weapon didn't take TPS into account when creating the interpolated position. (ChargeGun, SalvoLauncher, TargetingGun)
- Fixed Terrain Textures with Alpha layers not working correctly on layers 1-3.
- Fixed Editor Object picker not being able to interact with objects that didn't have any geometry/invisible mesh.
- Fixed Editor Object picker not being able to interact with objects under ground through wireframe modes.
- Fixed Editor alignment when placing Tunnel Corner and T Junctions in Align mode.
- Fixed Editor Ctr+Z needing to be pressed twice when undoing buildings that didn't modify terrain.
- Fixed foliage appearing black in Pathing Editor.
- Fixed BZ1 HGT file import not working correctly. Also added the ability to import BZ98R HG2 files.
- Added Editor Pathing view improvements: Move path points/objects relative to "grab point", rotate selected object using right mouse, show object orientations.
- Editor Pathing view now shows path names.
- Fixed Damage Smoke being visible in Satellite mode on units that are Hidden.
- Fixed Sky parameter stars.speed not working.
- Fixed several UI Errors not specifying which Control is causing the error. (Slider var out of range, Align not found, Poll interval must not be negative) Also updated Log message about missing Images and bad Parameters from DIAG to WARN.
- Fixed game not logging an Error about missing Sprite names.
- Fixed FFA Team Chat not working correctly in-shell after the Host pressed Launch.
- Fixed MeshRead crashing when trying to load some XSI models. (engine flame meshes)
- Improved FBX reading for ASCII FBX files.
- Fixed FBX MeshRead not working around invalid points, causing some vertecies in custom collisionMeshs to not work correctly.
- Fixed APC class not respecting avoidType setting in the ODF.
- Fixed Pathing not scaling properly on maps with Meters Per Grid that didn't evenly divide by 4.
- Fixed items in Command Panel not being Localized properly.
- Fixed Factory/Armory Dropoff nav name not being Localized properly.
- Fixed Shell becoming unresponsive/disappearing if you clicked Cancel when downloading mods while joining a Multiplayer Game.
- Fixed Single Player menu Tech/Mail lists crashing if more then 3 items were in them.
- AIP DefendArea / ClearArea plans now are able to target custom faction Recyclers other then ISDF/Scion.
- Fixed AIP LuaCondition not passing in the correct Time.
- Fixed AIP DefendArea/ClearArea not taking ProvideNames into account for targetType.
- Fixed AIP Build Dependency Check not working on Team 15.
- Fixed missing Alpha channel on vsmoke2.tga used in effects.
- Fixed draw_tracer render appearing "bent" in chaingun/pummel/splinter bullets.
- Fixed EffectFlags on ISDF buildings being incorrect, causing effect driven lights to not properly interact with IsPowered state.
- Fixed tunnel pathing for ibbseg2 odf.
- Scion07: Fixed underground Lava tiles causing damage to buildings.
- ISDF14: Fixed build area around the closest pool to player's base not allowing you to build.
- Fixed UI missing BackStarField on Mods menu and Single Player Debrief screens.
- Fixed LuaMission GetVarItemStr() not working properly.
- Fxied LuaMission CountUnitsNearObject() not working when a Handle is passed in.
- Fixed LuaMission GetPositionNear() path point not being optional as intended.
- Fixed LuaMission missing EjectKillRetCodes table.
- Fixed LuaMission GetNextRandomVehicleODF() not using it's return parameters.
- Fixed LuaMission missing call to PostLoad() function.
- Fixed LuaMission Damage() function not working with large values.
- Fixed LuaMission ReplaceObject() possibly crashing when an object's Label length is too long.
- Fixed Decoda not being able to hook into LuaMission.
- Fixed MPI not spawning the proper Enemy units when using a custom faction. Also made spawning code no longer rely on path points (TankEnemy1, TankEnemy2, TankEnemy3, SentryEnemy1, SentryEnemy2, SentryEnemy3, turretEnemy1, turretEnemy2, ScavengerEnemy) now it spawns Enemy units around the Recycler, the samw way the Player's units are spawned.
- Added ODF parameter [CraftClass]::AimVarBase = 0.5f and [CraftClass]::AimVarSteer = 0.2f. These allow control over the aim variance an AI unit has that creates "wobbly aim".
- Added ODF parameter [ScavengerClass] or [ScavengerHClass]::lockScrap = false. If this is set to True, it will prevent multiple scavengers on the same team from going after the same piece of scrap.
- Added ODF parameter [CraftClass]::OffensiveProcessIsDistractableBySnipe = true. If this is false, AI won't try to harass a player that shot it with a Sniper shell.
- Added support for units to Recycle at Silos. Added ODF parameter [CraftClass]::CanRecycleAtSilo = false. If true, it will recycle at the nearest Recycler or Silo. If False, Recycler only. Added to [SiloClass]::recyclex = 4.0f and recycleZ = 5.0f to calibrate the Recycle point, same as Recyclers can do.
- Added support for Editor Environmental export to export the terrain in .FBX format.
- Added ODF parameter [GameObjectClass]::AllowEffectsWhenHidden = false. If true, allows Effects to be shown even if the object is Hidden (Cloaking MorphTanks, fog of war, etc)
- Added ODF parameters [CraftClass]::DamageClassRatioLight = 0.5f, DamageClassRatioMedium = 0.25f, DamageClassRatioHeavy = 0.125f to control the Health thresholds at which the Damage Smoke states switch.
- Added ScriptUtils/LuaMission function GetCargo(handle h). This returns the handle that is being carried by h, if it exists. nil if not tugging anything.
- Added commandline arg for mod makers: /disablemipmaps, if this is set, when generating DDS files, the game will not generate mip maps for them.
- Added ODF parameter [OrdnanceClass]::maxSpeedUsesGravity = false. If true, Grenades fall speed will be able to fall at increasing speed using gravity, like 1.2 behavior. False, they will not fall faster then shotSpeed.

## Changelog - Build 2.0.186.1
- Fixed Editor Environ selection/export crashing on large exports: limited export size to sane / possible range.
- Fixed dying in Factory Panel leaving the user stuck. (again)
- Fuxed Addon image preview being White when no item is selected after deactivating an addon mod.
- Fixed Pathing Display bounding boxes for buildings overlapping tunnel segments.
- Fixed LuaMission GetCargo() crashing.
- Fixed Shift+F10 not working with EDITOR / BZVIEW cheats active.
- Fixed Bullets with 0 velocity getting a degenerate matrix.

## Changelog - Build 2.0.186.2
- Fix for Factory Panel not working. Moved Factory Panel and Comm Panel user tests to PoweredBuilding terminal functions.

## Changelog - Build 2.0.187.0:
- Fixed code reference to UI elements EscapePlay.Absolute and EscapePlay.Leveling not matching the cfg changes in BZCC. These are supposed to be hidden in Multiplayer game modes.
- Fixed LocalAmmo displaying the wrong ammo count for weapons in the first slot. If there were grouped weapons, it would not iterate over all of them, causing it to think some were in the first slot.
- Fixed UI Checklist mouse wheel scrolling being inverted.
- Fixed UI Edit element caret position being off if iface.shellexpandfont is set to false.
- Fixed UI SysBtnClose, used in Windows with Style TitleBar / ThinTitleBar, not rendering properly. Added Style "TitleCloseBtn" to enable the Close button on a TitleBar. Also added to Window the command TitleColorGroup("DEFAULT"), which allows the customization of the color group used by TitleBar / ThinTitleBar on Window elements.
- Fixed UI Ticker text not being drawn in the correct position. Added PauseTimer(0) to control how long the text pauses in the middle.
- Fixed UI Timer not having pollInterval setup on first run.
- Fixed UI Menu not being able to calibrate each menu AddItem() via an ItemConfig() before it. Also added an optional second Text parameter to AddItem() parameter.
- Fixed Weapon Icon not updating when switching weapons.
- Added Foreground color to the colors adjusted by BasePanel light element. This allows support for it to be a Gauge, or other UI element type and be colored correctly.
- Fixed Movie Player using WRAP instead of CLAMP drawing mode. This fixes pixels along the edges being drawn from the opposite side. Noticeable on movies that are lower resolution.
- Fixed Mod list truncating. Changed mod download into a two stage event, first it Downloads the config mod, then reads and downloads the list of Asset Packages from the mod's ini. This fixes Mods with > 9 Asset Packages failing to join in GOG vs Steam. Also made it not que items that are already ready.
- Added a UI function ImageScaled(). This works the same as Image() but takes floating point percentages (0.0 ... 1.0) for the start and end x / z positions.
- Fixed missing Localization of the word "Players" in the Loading menu when it lists Waiting On # Players.
- Fixed Mod switching not properly switching to the My Documents AppendToMyDocs() sub folder. This fixes Campaign progression not being updated on mod switch.
- Fixed UI Background using WRAP instead of CLAMP. Fixes the edges of background images being drawn on the opposite side.
- Added support for LoadBar to be configurable by cfg. bzshell_loadbar.cfg is loaded. It looks for a UI element called LoadBar, with sub elements LoadPercent, LoadText, LoadTextWaiting, LoadTextSkip. It uses var loadbar.loadratio for the Gauage/Percent.
- Fixed implementation of iface.shellresx / iface.shellresy feature. Mods can once again set the base resolution used by the cfg system.
- Fixed Single Player menu always thinking a premission movie existed, causing it to stop the music in mods with continuous shell music between main and singleplayer menus.
- Fixed Single Player debrief text used in SucceedMission() / FailMission() being limited to 14 characters. Files with longer file names simply showed a blank debrief screen. Bumped up to 64 characters.
- Fixed Error about BZN Loading failure message not specifying the info about which ODF file failed to load. It was passing in the classlabel as the odf name.
- Fixed Server Browser crashing if the data was currupted.
- Fixed IsAudioPlaying internally zeroing out the Handle.
- Added Lua function SetPowered(handl h, int powered). Allows scripts to override the powered state of an object. -1 = default, 0 = off, 1 = on.
- Fixed Lua function SetTeamNameForStat() not working in MP end games scores screen.
- Fixed Satellite/Editor minimap mouse clicking becoming stuck if a Camera() sequence is triggered while clicking on the minimap. Activate() clears the button click state.
- Fixed Construction Rigs accumulating velocity while deployed (from collisions, explosions, etc) and applying it all at once as soon as they undeployed.
- Fixed Hovercraft Terrain Lookahead always treating Buildings as terrain. Fixes Hovercraft not colliding properly with Buildings. Added ODF parameter [HoverCraftClass]::TerrainLookaheadSlopeThreshold = 0.1f. This allows the slope tolerance for building interaction to be calibrated. If the slope of a building is < tolerance, (vertical walls being 0.00001 ish) it won't try to do height elevation unless jumping.
- Fixed Person class items with animated turret pieces glitching/jittering.
- Fixed Tag Cannon leader round accumulating shotTimer when trigger is held. Fixes incorrect fire rates for Leader Round when holding the trigger for long periods of time.
- Fixed Turret Compass icons flickering if the turret is perfectly aligned (pressing Deploy key in a turrettank/walker). 
- Fixed Water below height 0 not applying Damage to TrackedVehicles/Walkers. Added TRN parameter [NormalView]::WaterDamageBelowHeightZero = true. If false, it restores the original behavior of not doing Damage to TrackedVehicles/Walkers.
- Fixed Person class hopping out of a Turreted vehicle not applying the facing direction velocity. Also added to ODFs: [CraftClass]::HopoutVelocityX = 0.0f, HopoutVelocityY = 3.0f, HopoutVelocityZ = 12.0f. These allow modders to calibrate the hopout velocity of a craft.
- Added support for Person class to use Chunks. Defaults to UseVehicleCrashOnDeath = false, and numChunks = 0.
- Slight optimization to Seeker mines. If the mine has a search radius of 0, it skips all the object searching.
- Fixed Tug animation state not being preserved in the map BZN load. Also fixed missing implementation of Cockpit deploy animations in Tugs.
- Added new render type: draw_billboard. This works similar to draw_sprite but allows for scrolling textures. The draw_billboard parameters: startHeight = startRadius, finishHeight = finishRadius, textureRateX = 1.0f, textureRateY = 1.0f, textureSpeedX = 0.0f, textureSpeedY = 0.0f, spriteCenter.x = 0.0f, spritecenter.y = 0.0f, followCamera = false, textureHorizontal = false.
- Improve the performance of CollisionArray::BoxTest with high-poly collision meshes by testing for bounding sphere overlap before iterating through poly faces. Fixes lag on load with lots of objects that useCollisionMeshForPathing = 1.
- Fixed ShieldTower objects not applying the odf feature ForceMass into account when applying orddrag/ordpush.
- Fixed Bomber Bay not requiring power to reload bomber.
- Fixed Popper TeamFilter not working if it was set to target Friendly units.
- Added ODF parameter to [BomberBayClass]::autoBuildBomber = true. If false, won't automatically spawn the Bomber when the bay is created.
- Added ODF parameters to [FactoryClass]::scaleVelX = 0.0f and scaleVelZ = 0.0f. These work similar to ScaleVelY, but for the X and Z axis.
- Fixed items with a Deploy/undeploy and loop animation not working correctly after a save/load. It would think it had to re-play the deploy animation on Load of a saved game.
- Added settings to GamePrefs to control the color of the Ground reticle. These work similar to CockpitRadarColor parameters. gameprefs.GroundSpriteColorR = 0.0f, gameprefs.GroundSpriteColorG = 0.2f, gameprefs.GroundSpriteColorB = 1.0f.
- Fixed Lights not properly starting out in the OFF state when first placing a building/loading a map if the building is Unpowered.
- Fixed Water Fog/Physics/Damage occurring if the player is under ground, under the water. This fixes issues with Water related effects occurring in Tunnels that went under water.
- Fixed some occurrences of Terrain out of world tiles being the wrong size.
- Fixed Rain not using tranPeriod when first starting. This makes rain properly transition on instead of snapping on after OffPeriod runs the first time.
- Fixed mouse cursor not scaling with the rest of the UI. It now scales the same  way colorize.tga scales. It will look for versions of the cursor image with _x1_5, _x2_0, _x2_5, _x3_0, _x3_5, _x4_0, _x4_5, and _x5_0 appended.
- Added ODF property to [KingOfHillClass]::isHidden = true. If false, it won't be invisible to users.
- Fixed Plants dying animations not preserving the rotation of the plant object. Also preserves the rendering flags like 2-sided during death animations.
- Fixed Blink In explosion occuring at the Out position.
- Added a 4th option to ODF parameter [CannonClass]::soundPerShot. If set to 3, it will play the sound only if the weapon is firing, and if the sound is not currently playing.
- Fixed AssaultTank not playing it's Killed_Msg VO.
- Fixed Building Collision sound not working correctly. It was always playing the Terrain collision sound.
- Fixed Minelayers not respecting Chatty Units in MP option.
- Added support for Person class to have Strafe animations. Anim names: strafe, strafeC, strafeA. It plays the animation forward when strafing right, backwards when strafing left.
- Fixed stepSound not working for Person class.
- Fixed ChargeGun Flash effects and Recoil not working correctly. FlashName no longer becomes permenantly stuck on. FlashName/Recoil now play for each shot. Fixed chargeSound being cutoff if holdRate is 0. Made soundPerShot work for Chargegun class. Added ChargeEffectName = "", a render effect while the gun is charging.
- Fixed Planar Renders not preserving their original rotation if rotationRate was 0.
- Fixed Bolt and Trail renders using wrong initial matrix for segments when being emitted vertically.
- Fixed draw_tracer renders being culled from camera before they were fully out of view. Now takes length into consideration instead of just origin point.
- Fixed draw_planar renders not rendering correctly on structures/underground tunnels. Also added an OverWater = false parameter to draw_planar render and simulateOverWater = false to sim_dust render.
- Added odf parameter RotationBias to draw_planar, draw_twirl, draw_twirl_trail. This works similar to other *bias parameters, a static value to which the random value is added to.
- Fixed sim_dust renders z-fighting with terrain (trail, bolt). 
- Fixed draw_twirl_trail not using correct emit_veloc if the emitDelay was greater then emitLife. Also fixes the first particle of a draw_twirl_trail having 0 velociy.
- Fixed flashTime not working correctly at different TPS rates. Made flashTime default to 0.1, so it stays consistent.
- Added new ODF parameter [GameObjectClass]::AllowLightsWhenHidden = false. If true, lights won't be suppressed for hidden objects (cloaking morphtanks, etc)
- Added support for Cockpit to have Init and Run animations. These work the same as InitAnimation and RunAnimation. Added ODF parameters [GameObjectClass]::InitAnimationCockpit = "", RunAnimationCockpit = "", InitAnimationIsLoopedCockpit = false, RunAnimationIsLoopedCockpit = true.
- Added support for setting the load BG image in IA/MP map inf files. Added parameter [Description]::mapLoadTga = "intro.tga". Defaults to intro.tga if not specified.
- Made Escape menu Load Game delete button have style OUTLINE so it matches the others.
- Fixed in-game Score screen background overlapping Time message.
- Fixed bug in Shell if using GOG joins via command line -connect, leaving the main menu and multiplayer menu both active at the same time. ShellMulti now fades out ShellMain if it's somehow still active.
- Expanded the Single Player mission description window to fill the space available.
- Fixed draw_geom renders being culled from camera before they were fully out of view. Now takes model bonding box instead into consideration instead of just origin point.
- Fixed the Ammo bar on Team Panel covering up the bottom half of the "C" for Commander icon.
- Fixed MP lobby list squishing the bottom most entry if the list is full.
- Fixed readability of MP End Game score screen. Added black backdrop and rollover highlight.
- Fixed error in console related to obsolete unpn commands when creating a game in Multiplayer.
- Added Team chat option buttons to non-team play to support Team chat in ST FFA mode.
- Fixed readability of the most recent chat message in MP Escape Menu. Added style NOSELECTION to the chatbox.

## Changelog - Build 2.0.187.1

- Fixed crash in WeaponMine SetPerceivedTeam in GameObject::LoadAll().
- Fixed game crashing if the LoadBar.cfg is not present.

## Changelog - Build 2.0.188.0
- Fixed incorrect scaling of Loadbar after a mission load/restart from in-game
- Fixed workshop items not downloading asset packages if they are not subscribed.
- Added ODF parameter [CraftClass]::useAvoidance = false. If this is true, it enables 1.2 style avoidance code. Also set Walkers and Walking construction rigs to default to Avoid type NONE.
- Fixed MorphTank Cockpit animations not updating correctly when morphed.
- Fixed aiAddHealth and aiAddAmmo causing doubled addHealth and addAmmo on AI units. Made aiAddHealth / aiAddAmmo default to 0. This also fixes them not working with ODF inheritance.
- Fixed Recoil not working on Detonator (MDM gun) weapons. Also fixed Recoil not working on Launchers, and TorpedoLauncher.
- Added PositionBias to particle emitters. [ExplosionClass]::particlePosBias# = "0.0 0.0 0.0", and draw_emit emitPosBias = "0.0 0.0 0.0". This works similar to other bias features, a basis position offset to which posVariance is added to.
- Added feature to draw_sphere and draw_geom, pitchVar = 0.0, yawVar = 0.0, rollVar = 0.0. These are random variance added to the addPitch/addYaw/addRoll values.
- Added ODF parameter to [ConstructionRigClass]:: leftFootPiece = "lfoot", rightFootPiece = "rfoot". These allow modders to specify the model piece used for the feet.
- Added ODF parameter to [SatchelPackClass]::startUpright = false. If this is true, it spawns the object upright like BZ2 did.
- Added ODF parameter to [WalkerClass]::flattenTrackNormal = 0.0f. This re-enables the behavior of Walkers not tilting so far on steep terrain. BZ2 used a value of 2.0. Also made ConstructionRigs use the [HoverCraftClass] version of the same parameter.
- Fixed WeaponMines not using hp_fire hardpoint.
- Added ODF parameter to [SprayBombClass]::buildSprayOnExpire = false. If true, it builds it's payload when it expires, even if it doesn't hit anything.
- Fixed [CraftClass]::ModeText not working with ODF inheritance.
- Fixed PilotClass not working with ODF inheritance.
- Fixed DamageEffect# not working with ODF inheritance.
- Added ODF parameter to [ConstructionRigClass]::DeathTimer = 5.0f, and ExplodeTimer = 0.4f. These work the same as their [WalkerClass] counter parts. This allows modders to match the death time with model animations for custom constructors.
- Added ODF parameter to [DispenserClass]::MaxFireHeight = 0.0f. If this is > 0, then the object won't dispense if the owner is higher than the specified height above ground or water.
- Fixed ejectRatio not working if WantBotKillMEssages() is set in the Lua Mission script.
- Fixed InitialShotDelay not working as expected. Fixed first shot firing if the trigger is released before InitialShotDelay has elapsed.
- Made Missile class (and derived) respect TargetHidden and TargetInteractable ODF features. Effects: LaserMissile, ThermalMissile, ImageLauncher, ThermalLauncher, and MultiLauncher. Also made MultiLauncher respect TeamFilter.
- Added ODF property to [SeekerClass]::LiftSpring = 2.0f. This allows modders to control the speed it goes up/down.
- Added ODF property to [OrdnanceClass]::InheritVelocity = false. If this is true, the ordnance inherits the velocity of the craft that fired it.
- Added ODF property to [CannonClass]::raveFlash = false. If true, it produces the flash effect used by gtechno. Changed the hard coded effect to use this ODF value instead.
- Fixed SatchelPack having shotDelay under the wrong Header. It was copied from DispenserClass, now properly reads from under [SatchelPackClass].
- Fixed BZVIEW cheat not working.
- Made Screenshots save in PNG format.
- Added to UI ConfigureSystem function CreateFontScaled(name, filename, base, step), for example CreateFontScaled("MyFont", "bgmm", 10, 8).
- Fixed missing Localization of ModeText# items.
- Added support for hp_pack and hp_hand to have unique icons.
- Fixed Capture The Flag related functions not working correctly if TeamPlay is off.
- Fixed in-game Scores Background appearing after closing Escape menu if the gameprefs option for scoreboard Background is disabled.
- Added ODF parameter [ObjectSpawnClass]::spawnEmpty = true. If false, it won't spawn a ship as empty.
- Added command line arg /loclogging. If this is set, it will log missing Localization items to the Log file.
- Added command line arg /positionmultonload 0.0f. This works like adjustheightonload, but scales all the positions of all objects and path points on a map by the specified float.
- Fixed Comet/Wasp not exploding with the Boom like it did in BZ2.
- Fixed Scion Antenna/Overseer hologram being included in the bullet collision mesh. Now bullets properly pass through the hologram in the center.
- Fixed typo in Rocket Bomb (A) damage to Stasis shield.
- Fixed ISDF Gun Tower terminal having the glow flag applied. This fixes it being blacked out/visible through fog.
- Fixed missing RequireText on apwreck.
- Fixed incorrect provideCount on Scion Archer.
- Fixed missing stepSound on Scion Constructor.
- Fixed dust not appearing under ISDF Stasis vehicle / Interceptor.
- Fixed collision and editor placement alignment on ISDF Wall Guntower.
- Slightly optimized Flamethrower render FX. (reduced particle count from 500 to 300).
- Fixed incorrect emit hard point name on Comet Torpedo. Fixes FX not working.
- Fixed Flash Burst flooding sound channels (from 15 sound channels to 3), made a much shorter sound for it.
- Fixed chunk explosion damage not scaling with Armor/Shield values.
- Switched Laser Render from draw_bolt to draw_trail so they animate properly.
- Fixed incorrect renderCount in Pummel flash fx.
- Fixed old Fury model being too shiny.
- Fixed Normal/Specular materials not working on Powerup models. Made only the inner faces use Emissive flag.
- Fixed Material settings for pbatun07, it now matches the rest of the tunnels.
- Updated Cursor image to be able to scale with the UI. Cursor is also now at 60 FPS instead of 15.
- Fixed Tracked / Walker explosions having some particles flying abnormally high/far.
- Fixed several weapon FX renders that pointed to vsmoke_interface.tga as a texture. This is a hardcoded texture used for the scrolling effect in the background of UI windows. This caused any addon mod that wanted to customize the UI texture, to also inadvertently change some weapon FX. Made a copy of vsmoke_interface.tga, named vsmoke3.tga and pointed stock render Fx to use that.
- Fixed incorrect blend mode on some explosions that used ring.tga, that caused black squares around it on the ground.
- Slightly improved Scion Matriarch movement physics.
- Fixed MP Lobby "My Mod" string being cutoff when there was still plenty of space available.
- ISDF Mission 5: Fixed ISDF Power Plant not having the correct ambient sound.
- ISDF Mission 11: Fixed fbrecy1 not having the correct values for Health.
- ISDF Mission 14: Fixed lava damaging the ISDF Wrecked Carrier. IF the mission went on too long, it would get destroyed.
- ISDF Mission 14: Fixed the Burns object sliding down into the Wreckage. Made the Scion Hauler pickup Burns at the mission start instead of just sitting next to it.
- Fixed snow/rain fx snapping on in ISDF 10, Chill, DM Bane, and MPI Island, they now properly transition on.
- Fixed incorrect Dome UVSpeed on ISDF08, fixes the top of the Sky pinching.
- Split MP option for Friendly Fire into two options: Friendly Fire, and Player Friendly Fire. Also moved them to Game Options menu. Now Hosts can set AI Friendly Fire separately from Player Friendly Fire.
- Split up bzgame_init.cfg into 4 new cfgs: bzgame_init_color.cfg, bzgame_init_cursor.cfg, bzgame_init_font.cfg, and bzgame_init_sound.cfg. These 4 are called from the root bzgame_init.cfg. This allows Addon mods to choose which part(s) they want to modify, without overriding other Addon mods that modify different parts.

## Changelog - Build 2.0.189.0:
- Fixed ISDF05 mission stall if the player stopped the Constructor build process. Prevents the user from interacting with Recycler while building.
- Added LuaMission callback SetSelected(Handle h, bool set). This is a parallel to "bool IsSelected(Handle h)".
- Made new Cursor image "cursorHD.tga", and made a compatible version of cursor.tga for existing addons / non-scaling cursors to use.
- Fixed some localization translations incorrectly translating "..." trailing periods as "#".
- Fixed [FactoryClass]::scaleVelX / scaleVelZ not being applied correctly in combination with MultVelXZ.
- Added support for Powerup class to use Chunks. Defaults to UseVehicleCrashOnDeath = false, and numChunks = 0.
- Fixed broken implementation of AIWeaponMaskVsCombat and AIWeaponMaskVsAssault. Note: These features only work if UseSelectWeapon = true.
- Fixed Person class objects not appearing when first placed in the Editor.
- Fixed AllowOffMapFiring code not updating the weapon's origin position in Multiplayer.
- Fixed Water Reflections not rendering properly when Shadows were set to Low / None.
- Fixed Radar minimap user direction line indicator not scaling with the rest of the minimap in HUD scale.
- Increased max FOV to 135. This allows proper aspect ratio for ultra wide resolutions.
- Fixed Single Player Camera sequences not taking FOV into account. Fixes cut scenes in missions appearing zoomed in with widescreen resolutions.
- Fixed missing Localization of the object name in the Target camera.
- Fixed missing Localization of the object name in chat messages when objects die.
- Fixed CameraPods not exploding when the oldest one is removed. Added ODF Parameter [CameraPodClass]::explodeOnExpire = true. If false, it simply gets deleted when you place more then the limit of 10.
- Added support for forward/neutral/reverse animations to TrackedVehicle class.
- GunTowerProcess that use ChargeGuns now randomize the charge level, like other AI types do.
- Fixed FactoryPanel/Satellite Panel getting stuck if the user has the Escape Menu up. Made ViewManager::SimClearCurrentView() able to deactivate the desired view even if it's not on the top of the view stack.
- Fixed PersonClass Explode() not working properly in Multiworld.

## Changelog - Build 2.0.189.1:
- Fixed the new raveFlash setting not working for MachineGunClass.
- Fixed TargetCamera not taking FOV into account.

## Changelog - Build 2.0.190.0:
- Fixed ISDF Recycler not playing it's Deplyed message VO, like the Scion Recycler does.
- Fixed several UVMapping errors on the Scion Dower, also fixed some vertecies that caused visible tearing in the corners when built alongside other buildings.
- Fixed typo in the name for assault Lightning (gbolt_a) DM only weapon.
- Fixed incorrect name of Fury MissileTank in Editor Object List. The Scion Lancer Was listed as "Fury Archer", now lists it as "Fury MissileTank", to parellel ISDF MissileTank.
- Added IsUndeployed(h), IsDeploying(h), and IsUndeploying(h) callbacks to LuaMission. These allow scripts to detect these states, similar to IsDeployed(h).
- Fixed DeathMatch 1-shot kill mode not triggering when sniping AI Bot Ships.
- Fixed Deathmatch Craft Only mode not killing AI Bot Pilots.
- Fixed Deathmatch counting Gun Towers as empty ships for players. Fixes CTF:FlagFort GunTower Walls being deleted after players hop in and out of them.
- Fixed Deathmatch Rabbit mode spamming if the Rabbit player hopped out of their ship, or when there's only one Rabbit. Also fixed getting negative Score from Team 0 objects in Rabbit mode.
- Fixed Multiplayer Instant / Instant Action stalling when trying to switch to Siege AIP before the AI built a CommBunker.
- Fixed Water Damage not applying to SprayBuilding class objects.
- Fixed TugProcess not using the CashOut Task to recycle. It now behaves the same as all the other units when ordered to Recycle.
- Fixed Hovercraft Physics applying Water Physics when the hovercraft was well above water.
- Added the user's position x y z coordinates to the Histogram.
- Fixed the script function KillPilot(h) not working on Person class objects.
- Terrain GetHeightAndNormal better handles interactions with Water, properly screening out water Below terrain and collision mesh ceilings screen out terrain and water above them. (fixes bugs in tunnels under water)
- Fix Attempt for AIPs "stealing" scavengers as idle while they were in mid-deploy. It now omits Scavengers that are in the Deploying() state in CollectField and CollectPool plans.
- Fixed TurretTank and Artillary not using LIFT_SPRING when Deploying.
- Added FlattenTrackNormal parameter for: [AirCraftClass], [PersonClass], [TrackedVehicleClass], [TorpedoClass]. Also added [HoverCraftClass]::flattenTrackNormalDeployed = 1.0f. This is the track normal used while in the Deployed state, for DeployableClass and derived.
- Fixed line-of-sight failing for Archers on steep slopes.
- Fixed Deployed / Packed VO message not playing in Multiplayer.
- Made Pilot Login properly clear the temp campaign switchSide variable. Fixes issue with backing out of mission Debrief after switch causing a new pilot to switch Sides.
- Fixed Extractor/Silo/Scavenger/ScavengerH InitDelay so that it starts at the beginning of the object's life, not when the scrapbar reaches that particular segment.
- Fixed Taunts not appearing at the start of Instant Action.
- Fixed MP Scoreboard Toggle not working properly after opening and closing the Escape menu.
- Fixed Editor Environmental tab Undo events being able to delete the Player, if the user spawned a ship via the Environment tab and hopped into it, then pressed Ctr+Z.
- Fixed Editor Environmental tab not undoing the Terrain changes made when undoing placement of a Terrain object.
- Fixed PlayerManager::BootInit using potentially uninitialized Localization strings. Random translations appeared in Console when joining/leaving MP games during Mod Restart.
- Fixed ChatLine being able to send blank strings. This fixes when people go to instinctively hit Enter to cancel a Chat message without typing anything sending a blank message to everyone.
- Fixed Damage Smoke not displaying on Remote Players in some instances.
- Fixed the /nick command being able to duplicate someone's name by adding spaces at the end.
- Fixed Hovercraft with moreLike12Physics = true not transitioning engine sound properly. Also added [HoverCraftClass]::maxThrottleRatio = 1.0f. This is the max base thottle clamp before being multiplied by the various ThrottleMult* parameters (airborne, overland, overwater variations). Fixes Throttle being able to get too large.
- Fixed [CraftClass] xplSnipe, xplChunk, and xplCrash not working properly with ODF Inheritance.
- Added ODF Parameter [OrdnanceClass]::UseGravity = false. If true, it falls like a Grenade. GrenadeClass defaults to true.
- Fixed Script ObjectKilled() function not triggering for Torpedo and Powerup class objects.
- Fixed hard lockup in CheckPlayerName() when 3+ people used the same /nick command.
- Added launch argument /verboseLogging, if set, this enables the SOBJECT LOST / ORDNANCE LOST that bloats log files in MP games.
- Fixed Host Migration not working properly with different TPS rates set on the recieving client causing the game to continuously resync.
- Fixed game.debugaip not working without vid.framerate also being enabled. Split them into separate items. Also fixed game.framerate not working.
- Fixed MorphTanks being able to fire a weapon while still Deploying/Undeploying if it picked up a new powerup.
- Fixed [DeployableClass]::canAttackWhenDeployed / canAttackWhenUndeployed not working if use13Aim = false.
- Fixed [DeployableClass]::DeployAtAltitude not working with ODF inheritance.
- Fixed APCs not deploying Soldiers after using CMD_RESCUE.
- Fixed AIP Deploy plan and initial AIP Recycler deployment not using baseDir. Added AIP parmeter "buildHeading = -1" to Deployer plans. Valid values are -1, or 0 - 3.
- Fixed PersonClass with canDetect and canInteract set to true not appearing in Attack/Service menus and Satellite mouse over selection.
- Fixed /nobodyhome triggering in Multiplayer map load.
- Fixed /info chat command not properly displaying the team group in Teamplay games.
- Fixed GamePrefs.ini GameBasePortNumber not being used in some places. Fixes hosts using different ports for games not working properly.
- Fixed visual stutter when Targeting an AI unit.
- Fixed ConstructionRigProcess Demolish task being able to Delete the Player.
- Fixed /nick and SetObjectiveName() being able to set %n where the UI and rest of the code displayed it as %d.
- Added GamePrefs.ini setting EnableServerLaunchedMessage = true. If true, it enables the "Server Has Launched!" message, if false, disables it.
- Fixed aspect ratio of MissionRequest popups if the Escape menu is not already up.
- Fixed changing Volume settings not updating all sounds that are currently playing.
- Fixed Loading Bar not scaling correctly during Network Sync state.

## Changelog - Build 2.0.191:
- Added ODF parameter to [ExtractorClass], [SiloClass], [RecyclerClass], [ScavengerClass], and [ScavengerHClass] scrapAmount = 1. This is the amount of scrap given each scrapDelay interval.
- Fixed Deployable, and DeployBuilding, not clearing omega/velocity while Deployed. This fixes Script functions like GetVelocity() and GetOmega() returning incorrect values on these objects in certain states.
- Fixed Skinned Cockpit models crashing the game.
- Fixed Skinned Cockpit models not using Chrome mesh in MorphTank class with useChrome set to true.
- Fixed Console Font sometimes being set to UI Scale x5_0.
- Fixed Clients having a password set via defaultPassword in *Prefs.ini causing join failing on sessions that didn't have a password.
- Fixed Clients failing to join a game running a different mod causing the MP lobby list to break.
- Restored a bunch of Gameprefs options that were previously in BZ2 1.3: Play_MapRadarHeight, Play_MapRadarWidth, Play_MapRadarXMult, Play_MapRadarXDiff, Play_MapRadarYMult, Play_MapRadarYDiff, Play_CockpitRadarColorR, Play_CockpitRadarColorG, Play_CockpitRadarColorB, Edit_MapRadarHeight, Edit_MapRadarWidth, Edit_MapRadarXMult, Edit_MapRadarXDiff, Edit_MapRadarYMult, Edit_MapRadarYDiff, Play_CockpitRadarHeight, Play_CockpitRadarWidth, Play_CockpitRadarXMult, Play_CockpitRadarXDiff, Play_CockpitRadarYMult, Play_CockpitRadarYDiff, Play_CockpitRadarXSIScale. Also added several new options: Play_CockpitTimerPosX, Play_CockpitTimerPosY, TargetViewWidthMult, TargetViewHeightMult, TargetViewXMult, TargetViewXDiff, TargetViewYMult, TargetViewYDiff, GroundSpriteColorR, GroundSpriteColorG, GroundSpriteColorB. See comments above them in Gameprefs.ini for details. Updated Gameprefs.ini with new (and old) options. Commented out the lines in the stock bzgame_init.cfg. The .cfg versions can still be used, just as they could before these GamePrefs options were removed.
- Added Command line argument /modid, if this is set to a workshop ID number, it will initialize the game's launch.ini to that mod, activating it on startup.
- Fixed minor texture bug on Chill.

## Changelog - Build 2.0.192:
- Fixed initialShotDelay fixes missed from TorpedoaLuncher and MultiLauncher.
- Fixes for RADAR Scale and HUD scale issues. Radar is now rendered at the correct size, and UI is now scaled properly when Reflections/Shadows are on Low.
- Fixed Unit names not using ObjectiveName when being localized in Network ChatMessage (order panel, unit killed chat msg) and Target Camera.
- Flipped grenade "maxSpeedUsesGravity" default to false (1.3 behavior). Now opts in to restore original 1.2 behavior.
- Fixed Scrapbar priority not taking into account the new scrapAmount variable.
- Tweaked new Torpedo and Powerup ObjectKilled() functions to only be called if WantBotKillMessages() is enabled.
- Also tweaked DLL's ObjectKilled function to filter out Powerups when doing score stuff.
- Clarified names of new split Friendly Fire option, now AI Friendly Fire and Player Friendly Fire.
- More F7 bug logging.
- Fixed SetTeam() script function not working properly on items that generate Power and have ScrapHold. (Recycler, RecyclerVehicle, RecyclerVehicleH, Scavenger, ScavengerH, Silo)
- Fixed bzgame_keys.cfg not being executed in the correct scale mode.
- Fixed Factory Panel not taking weaponGroup# into account when showing weapon customization groups.
- Fixed several Lua functions not working correctly when being called in ObjectKilled/RemoveObject(): GetEjectRatio, SetEjectRatio, GetDistance, IsWithin, GetNearestObject, GetNearestVehicle, GetNearestBuilding, GetNearestEnemy, GetNearestPerson, CountUnitsNearObject GetCurrentCommand, GetCurrentWho, HoppedOutOf, GetHealth, GetCurHealth, GetMaxHealth, GetAmmo, GetCurAmmo, GetMaxAmmo, GetWhoShotMe, GetLastEnemyShot, GetLastFriendShot, GetFront, GetTug, IsDeployed, GetVelocity, GetScavengerCurScrap, GetScavengerMaxScrap, GetCategoryTypeOverride, GetCategoryType, IsFollowing, WhoFollowing, GetOwner, GetRemainingLifespan, GetIndependence, GetGroup, GetWeaponMask, GetLifeSpan, GetCurrentCommandWhere, GetOmega, IsCraftButNotPerson, IsCraftOrPerson, IsBuilding, IsPowerup, GetCanSnipe, GetLookFront, IsPowered, GetEmitterMask.
- Fixed TurretTankProcess not respecting subAttackClass "ADS" weapon range setting.
- Fixed ISDF Turret Tank not using weaponRange when considering when to attack. This fixes Turrets shooting and falling short after being upgraded to a different gun.
- Added ODF flag [GameObjectClass]::canScoutObjectify = true, if false, scout can't objectify.
- Fixed Torpedoes not being able to hit buildings.
- Fixed Dropoff Nav not being localized to a player after they join and it already exists.
- Fixed Editor Blend mode's speed not being as responsive as they should have been.
- When a saved game fails to load, it now lists the full file path of the saved game instead of truncating it.
- Added new EjectKillRetCodes return DoEjectRatio (return value 5). If the LuaScript returns this, it will fallback to the game's default ejectRatio behavior.
- Added new map TRN parameter [NormalView]::waterUnderground = true. If this is false, water fog/physics won't apply under water if the water is below terrain (i.e. tunnels under a river). Also added [NormalView]::UseWaterHeightUnderground = true. If this is false, Hovercraft will not use the water height if the water is below Terrain.
- Added Lua function int GetGameVersion(). This returns the game's version build #.
- Added Lua function float GetTerrainHeight(pos), (pos can be a handle, vector, matrix, path point, like other GetPosition functions). This returns the literal Terrain Height from the map, ignoring buildings or other collide-able objects at the location.
- Added Lua function float SetAnimationFrame(handle, name, frame). This is a parallel to GetAnimationFrame, but lets you pass in a specific key frame to set the animation to.
- Added Lua function int GetSessionPlayerID(team). This returns a unique ID for a specific player, valid for this game session only.
- Added Lua functions: bool IsObjectiveOn(Handle, team), SetObjectiveOn(Handle, Team), SetObjectiveOff(Handle, Team), bool IsObjectiveToUser(Handle). These work similarly to the existing SetObjectiveOn(), but allow per-team control. Also added a Get parallel to tell if an object is currently Objectified to a specific Team.
- Added [DeployableClass]::switchWeaponsWhenDeployed = false, if this is true, it swaps between combat/assault just like MorphTank does.
- Fixed AIUtil AbleToHit() not skipping itself when doing line of sight check. Fixes Gun Spire trying to shoot through objects if the bullet passes through one of it's own arms first.
- Updated missing .cfg message to reference BZCC instead of BZ2 / validate files instead of reinstalling.
- Added canCollide to [MorphTankClass] ODF parameters. This allows modders to make a unit "phase shift" when morphing.
- Fixed ImageLauncher not being able to lock onto objects with origins below terrain. Line of Sight check now uses Center of Mass instead of world position. Fixes Shadower not being able to lock onto some buildings (Extractors).
- Made ImageLauncher respect needLOS ODF flag, if this is false it will skip the line of sight check when locking on.
- Added ODF parameter [DeployableClass]::deployToAttackAssault = true. If false, MorphTanks won't deploy to attack Assault targets.
- Added TurretTankT, a Tracked version of TurretTank. This class supports attacking in Undeployed state based on canAttackWhenUndeployed, and also supports [TurretTankTClass]::turretWhenUndeployed = false, if true, it's turret is free during all deploy states. If deployToAttackAssault is true, it will deploy when attacking isAssault targets (buildings).
- Added the following from DeployableClass to TrackedDeployableClass: scanTeamLimitDeployed, switchWeaponsWhenDeployed, canAttackWhenUndeployed, canAttackWhenDeployed, deployToAttackAssault.
- Fixed Plants not being interact-able in the Editor after they've been shot/burned down.
- Fixed incorrect translation of Satchel Charge in German.
- Several fixes to demo01.bzn mission script. Intro Cutscene now works properly, fixed animation keyframe bug in ISDF Dropship Landing animation. Fixed units spawning on top of the DropShip. Fixed Non Commander mode triggering the player to go to the dropship too early. Fixed player's starting loadout to match the original Demo mission. Fixed missing mission Fail objectives if you take too long.
- LuaMission: Fixed a bad return value in one of the Vector math functions.
- LuaMission: Fixed #require not working correctly out of the box.

## Changelog - Build 2.0.192.1:
- Fixed Prefs ini file reading to work properly doing RESTART (Mod switch, etc) and the file(s) are missing the parameters. Reset the initial defaults on RESTART before loading the Prefs ini files.
- Changed [DeployableClass]/[TrackedDeployableClass] ODF parameter "switchWeaponsWhenDeployed", now reads ODF parameter "switchMask" from [DeployableClass] and [TrackedDeployableClass]. Moved SwitchMask logic from MorphTank to Deployable/TrackedDeployable. [MorphTankClass]::switchMask still overrides [DeployableClass]::switchMask.
- Fixed TurretTankT being able to shoot while deploying/undeploying. Now behaves like other Deployable classes.
- Fixed TurretTankT not being included in various places with other Turrets. (AIP logic, GOTO spread out logic, etc)
- Removed some logging related to the HUD scale bug that was fixed.
- Tweaks to F7 logging to help identify the past and current values of the varsys keybind.
- Fixed a crash in FactoryPanel if the weapon powerup pointed to an invalid ODF.

## Changelog - Build 2.0.192.2:
- Fix for F7 bug: fixed buffer underflow stomping over team array in TeamPanel.

## Changelog - Build 2.0.192.3:
- Fix for Enemy Navs being visible: Fixed missing scanTeamLimit filter on TurretCraft (GunTowers).

## Changelog - Build 2.0.193:
- Made Path Display (Shift+F9) able to pan using the Camera keybinds (default arrow keys)
- Unit Task::AbleToHit uses the target's collision radius instead of bounding sphere radius. Improves first shot accuracy against terrain owning objects like buildings.
- HoverCraft Terrain Lookahead only applies the GetIntersection result if it hits a game object. This restores the original vehicle handling over terrain.
- Fixed Duplicate Asset check not working for Addon Mods, Config Mods and Asset Packages.
- Made Path Display hide the Editor UI if it is active. This improves the visibility of using the Pathing Editor.
- Fixed Radar Ping (blip01.wav) getting stuck infinite looping in the Editor if the Editor is opened at the same time as the ping is triggered.
- Fixed FFA mode being able to reserve too many F Slots.
- Fixed Crash on loading maps that have pre-placed Factory/Armories who's Dropoff navs have been removed.
- Added ScriptUtil functions: GetTerrainMinX(), GetTerrainMaxX(), GetTerrainMinY(), GetTerrainMaxY(), GetTerrainMinZ(), GetTerrainMaxZ(). These return the size of the map boundaries.
- Added GetVarItemStr() and GetVarItemInt() to AIP Lua callbacks. They mirror the functionality of their LuaMission counterparts.
- Increased the size of the Server Message string from 128 to 256. Hosts can now put a bit more description into their games.
- Fixed Scion Dropoff Nav default locations being too close to the building, compared to BZ2. This should also help improve units pathing away from Scion Recycler pad.
- Fixed Instant Action never being able to trigger Late Game AIP. The code to trigger it was nested inside the old "Pilot" mode code.

## Changelog - Build 2.0.194:
- Made Cockpit Radar mesh support reading FBX.
- Added several hardcoded values from CockpitRadar to Gameprefs.ini: Play_CockpitRadarDist = 8.0f, Play_CockpitRadarNear = 6.0f, Play_CockpitRadarFar = 10.0f, Play_CockpitRadarFOV = 9.0f, Play_CockpitRadarAngle = 30.0f, Play_CockpitRadarCameraWidth = 640, Play_CockpitRadarCameraHeight = 480. Also added new parameter: Play_CockpitRadarScale = 0.75f. This is the scale of the radar itself, separate from the model scale. They all have a gameprefs. counterpart command in console as well.
- Fixed CockpitRadar camera behaving incorrectly if the user is aiming straight down.
- Enabled SchematicView (Pathing Editor) in Full Screen mode.
- SessionManager sends LoadBar WaitingOn string to Clients. This allows clients to see who is waiting on Loading in SyncJoin.
- Fixed Input Sliders not saving changes while in-game. CFG called shell.options.deactivate but that command didn't exist in-game. Added it so it now does something.
- Removed the commandline /f7logging, as this bug is now fixed.
- Added new parameter to CFG IVCiewer: SetModelRotationLimits(min, max). This allows the CFG to enable looking "under" a model, if desirable.
- Expanded visible Console char limit from 128 to 256.
- Possible Fix for Commands getting stuck on a Player's unit after it's been Sniped.
- Added support for UI CFGs to have two more self notification callbacks: OnEvent("Control::StartFadeOutSelf"), and OnEvent("Control::FinishFadeOutSelf").
- Added an optional input argument to the commands shell.instant.openextras and shell.instant.closeextras to toggle if it uses FadeIn or Activate when switching menus (0 = Activate/Deactivate, 1 = FadeIn/FadeOut). Made default FadeIn on OpenExtras for consistency.
- Added ODF parameter to [ShieldUpgradeClass]::noFirstPerson = true. If false, it enables the effect in first person view, overriding the default in shieldeffect.odf. If missing, the value in shieldeffect.odf is used.
- Added new classlabel "minelayerT" to the game, a Tracked version of Minelayer. Uses [MineLayerTClass] all the same parameters as [MineLayerClass] uses. Uses AI Names "MineLayerTFriend" and "MineLayerTEnemy".
- Fixed MorphTankClass not updating the CRC of the Engine Sounds when loading them from the ODF. ODF Inheritance would always use the [HoverCraftClass] sound, even if you specified a different sound under MorphTankClass. Also added missing [MorphTankClass]::soundJump parameter.
- DeployBuilding / DeployBuildingH: Fixed buildMatrix being able to get the wrong height if SetConstructionMatrix was called on the object's position while it was in mid-build. Clean up the BuildEffect when a new command to deploy is issued. Fixes AI Recyclers re-deploying on the same spot on AIP change getting the wrong height.
- Added new ODF Parameter to [PersonClass]::prioritizeGetIn = false. If true, pilots will try to GetIn empty ships, even if they have no base to go to. If there's no empty ships nearby, they will attack as normal.
- Fixed SAV, Bomber, and Hovercraft with FlyingPhysics not using LIFT_SPRING on their euler.v.y componants like APCs do, instead of using fixed hardcoded clamps. Fixes units getting stuck on high cliffs.
- Fixed AIP CanBuild() not also checking if Factory and Armory classes are IsBusy().
- Fixed missing translations in CommandPanel::RequirePopup for LimitClass and TeamLimitClass items. Also added "Busy" string when it is busy building an item. Also added a space before "Squad", so it doesn't have to be included in the localization. (french was missing the space anyway)
- Fixed RecycleTask not properly handling Scavenger or ScavengerH. I'm not sure RecycleTask (the old BZ1 scavenger AI) is even used by anything in stock.
- Fixed FlashEffect not working for TorpedoLauncher.
- Fixed flickering with large DrawPlanar renders.
- Fixed missing localization of chat printed "Only %d seconds left to sync join" message.
- Fixed missing Localization of "Leave by chat command" string.
- Added new bits to EffectFlags bitmask: bit 11 (2048) IsDeploying, and bit 12 (4096) IsUndeployed.
- Fixed Artillary class physics not interacting with hills like other flying units. Code copied from APC.cpp. Added ODF parameters [ArtillaryClass]::overWater = true, and altitudeLookahead = 0.25f. These parellel thier siblings in the other Flying unit classes.
- Fixed Scoin Archer interacting with hills, use accelJump of 150 like ISDF APC.
- Added VFX to Scion Archer when Deployed.
- Fixed hierarchy on Scion Archer model. Fixes camera not working properly when being driven by the player.
- Fixed AIWeaponMaskVsCombat and AIWeaponMaskVsAssault not working if useSelectWeapon = false.
- Fixed mod description getting left with stale data if the mod's des file is missing. Clear the listbox before filling it.
- Added to AIP Servicer plans: ServiceAllies = true. If false, it won't try to service allies or send units to allied team's service bays.
- Fixed NULL pointer crash when picking up a weapon if it's altName was non existent. Properly sets altClass to this, the same as if altName was missing from the ODF.
- Fixed AppendToMyDocs not updating default pilot/saved folder directory. Fixes mods that use AppendToMyDocs that don't specify a custom directory for these.
- Fixed [BuildingClass]::insideReverbIndex not working for TurretCraft (Gun Towers).
- Fixed TurretCraft triggering terrain collision sound when colliding with Craft. Made Craft GroundCheck() return pbHitBldg if IsBuilding() or IsTurretCraft().
- Fixed UnitTask not Including TurretCraft (Gun Towers) in TrackedVehicle high skill aimVar modulation vs Buildings.
- Made Lua Errors for AIPs print to Console / Messages box to make them more obvious.
- Fixed Silo not being considered powered, like Extractor. Fixes certain effectFlags not working correctly for SiloClass.
- Fixed /nobodyhome not reading the terrain name from the mission file if available. (bzns saved that point to another terrain file)
- Fixed incorrect view distance after returning from Satellite or Editor views, Terrain Class visibility range was being set after entering the new view.
- Terrain performance optimizations: MapCluster computes height extents using terrain height values instead of full vertex positions, TerrainQuadTree updates bounds in a faster, simpler way when positioning the shared empty (flat) quadtree, TerrainQuadTree skips rendering if no solid terrain triangle within the extents could possibly face the camera.
- Made MP Lobby Shell Team Listboxes use a DisplayTeamIndex list, instead of the real team index list. Uses civar0 to show who's on what team for players not on a valid TeamGroup. Also highlights them red to indicate they're not on a valid team.
- Fix for spelling error in ODF for BuildingClass::ambientSoundWhenUnpowered. Left old spelling for backwards compatability, so both work now.
- Made Stock Scion Matriarch and Kiln/Forge Dropoff nav positions closer to their BZ2 locations. Changes in the remastered model's hp_vehicle location caused these positions to change between BZ2 and BZCC.
- Added missing mesh g_fflash.xsi. This is used for muzzle effect flashes with flash.tga.
- Fixed Popper Fire Explosion not taking Armor/Shield values into account.
- Fixed WaitingOn Message in Loading screen being cutoff too early.
- Fixed missing BackStarField.tga call in Single Player and Instant Action Debrief screens.
- Fixed Command Panel buttons not being fully click-able in Satellite mode. Parent window needs to be wide enough to encompass the entire button. Adjusted Command Panel Action Item, and BasePanel width to better correspond to the Command Panel button widths. Also adjusted Team Panel to better anchor off of Group Panel. Converted BasePanel to use DefineControlTypes, like CommandPanel and GroupPanel, and made BasePanel use Align for easy adjustment, and aligned them to fit the wider space of the CommandPanel Action Item bar.
- Strategy / Deathmatch: Added new map TRN parameters under [DLL]: FriendlySpawnpointMaxAllyRange = 100.0f, FriendlySpawnpointMinEnemyRange = 400.0f, and RandomSpawnpointMinEnemyRange = 450.0f. These allow maps to calibrate the min/max distances used to control Player spawning. Smaller maps may need smaller numbers to work reliably. (Where two spawns are within 400m of each other). Added parameters to ST:Rock to fix spawning issues.
- StrategyCTF: Code updates ported over from Strategy DLL: Fixed FFA Alliances not working properly, Fixed Scoring not working the same as Strategy, Copied over new Spawnpoint distance parameters, Fixed a couple of TPS bugs in timers in the CTF part of code.
- MPI / Instant Action: Increased the spawn distance for starting ships, should help prevent Turrets from blocking AI Recycler deploying.
- Fix for AIPs stealing Scavengers (again), also check for IsDeployed(). DeployBuildings switch to IsDeployed() during the BuildEffect stage.
- Fixed CommVehicle and CommVehicleH not being flagged as Important in WorldPart. (render culling code)
- Fixed AIPCollectFieldPoolPlan casting from GameObject* to (potentially unsafely) Scavenger *, to casting it as Craft *.
- Fixed Duplicate GetTextLabel of "GoodbyeAllStr" in LeaveByChatCommand(), since that string is already been localized and cached just use the cached translation string.
- Fixed Torpedo physics not interacting properly with Buildings (for real this time).
- Fixed CommandPanel not properly localizing objects by their current name, was using ODFname. Fixes SetObjectiveName() not showing up properly in CommandPanel.
- Fixed backwards if statement on Hovercraft using TerrainClass::s_WaterUnderground flag. Fixes hovercraft not slowing down in water-tunnels in DM Flagfort.
- Fixed Windshield splat not using the correct sort distance. Fixes the splats rendering behind terrain.
- Updated documentation in bzgame_init_fonts for CreateFontRedux().
- Fixed LuaMission function AllowRandomTracks() not working.
- Added to LuaMission function StartEarthQuake(float magnitude, float volume = -1.0) and UpdateEarthQuake(float magnitude, float volume = -1.0) an optional volume parameter. This is a volume between 0.0 and 1.0. Default value of -1.0 is unchanged, and uses the scale of the earthquake to control the volume (magnitudes > 1.0 always are at full volume)
- Added to LuaMission Function AudioHandle StartAudio2D(string filename, number Volume, number Pan, number Rate, bool Loop = false, bool IsMusic = false, bool isVoice = false, bool isNonShellSFX = false), 2 new volume level booleans as input arguments.
- Added LuaMission function bool GetUseSelectWeapon(Handle h) and SetUseSelectWeapon(Handle h, bool set). These allow the script to get/set the UseSelectWeapon flag, used to determine if a unit respects WeaponMask.
- LuaMission: Changed name of SetAIP() to SetPlan() to match the BZ2/BZCC function name. SetAIP() still exists and is the backwards compatibility name for BZ1/BZ98R scripts ported over.
- Added .material for white list in Addon type mods.

## Changelog - Build 2.0.194.1:
- Fix attempt for MP Lobby player list, again

## Changelog - Build 2.0.194.2:
- Fixed ReshufflePlayersNotOnTeamgroups() not working for Hidden players. This fixes hidden players not getting properly shuffled down when there's an open slot in the Team.
- Fixed Hidden Players not showing up in Team List, was using alpha of 0 on the color, whoops.

## Changelog - Build 2.0.194.3:
- Fix for crash on DoCrunchTeams() if player(s) are Hidden.
- Fix for Team voice chat not working in FFA pre-game shell.
- Fix attempt for Team chat/voice not working for players who are Hidden.
- Made /poweruser display the team number next to the team index, and race, when using /info, like so: (index:team) PlayerName (race). Also made it display (index:team) for /list.
- Added ODF parameter to [ExplosionClass]::LockdownRadius = 0.0f, and LockdownTimer = 0.0f. If these are set, objects caught in this radius have Lockdown effect applied for the duration of the timer, same as if they got hit with EMP Lockdown.

## Changelog - Build 2.0.194.4:
- Fixed a team comparison check in ReshufflePlayersNotOnTeamgroups().
- Fix for DisplayTeamIndex not using the correct g_pNetPlayerInfo index for valid teamGroup detection.

## Changelog - Build 2.0.194.5:
- Fixed DisplayTeamIndex list not properly counting player slots. Sort players Not on a team onto the teamslots after OffensiveMaxTeamNums.
- Fixed ReshufflePlayersNotOnTeamgroups() not working properly. Don't skip out on teams when counting who wants to be on a team.

## Changelog - Build 2.0.195:
- Fixed loading of .trn files not working correctly.
- Fixed lag spike when first selecting vehicles in the MP Vehicles selection list.
- Fixed Players not on a valid Team having Give/Take command buttons visible.
- Fixed Players not on a valid Team not properly filtering the VehicleList by the Commander's race selection.
- Fixed Team/Voice chat not working for Players not on a valid Team.
- Fixed not being able to select a Player not on a valid Team in the Team Listboxes.
- Fixed SetEjectRatio script function triggering Bad Assets. Added ejectRatio member variable to Craft.
- Fix for MP Lobby TeamPanel staying open on occasion when Extra Options is opened. Delay TeamPage update if ExtrasOpen is true.
- Fix for Extra Options button appearing incorrectly after leaving Game Options if there is no Extra Options cfg set. Update svar7's contents and show/hide buttons appropriately in CloseExtras() as well as ProcessNetVab().
- Moved isHidden flag from [KingOfTheHillClass] to [GameObjectClass], allowing items like SoundCubes to be hidden except in Editor view.
- Fixed AIPs interrupting Construction Rigs mid-build: Made FindConstructionRig() skip rigs that are currently Deployed building something. Also Planners Upgrade checks construction rig idle by using IsIdleRig() instead of IsIdle().
- Fixed Logout button in SatellitePanel not working when using view.satellite.
- Fixed Bush class not rendering properly. Deformation_Lattice enables dynamic buffer so plants that use it will sway. Also added Save/Load/SaveShow/LoadShow so the Swaying variable is properly saved/loaded in Multiworld.
- Fixed LuaMission GetPositionNear() not working properly for off-map spawns. If all the tries fail, just return a random position.
- Fixed CTF Flag Carrier staying highlighted if they are sniped/hopped out. Added FlagDrop(Handle flag, Handle holder) ScriptUtils function.
- Made GunTower wall version unable to Bailout, just like regular Gun Towers. Fixes GunTowers on CTF:FlagFort being bailed out by players.
- Restored missing 3D Sound Level (master volume) setting to Sound Options UI.
- IA/ST/MPI: Slight optimization to StartingVehicles code. Made min/max radius both constants, instead of multiplying to get the max every call. Also reduced Strategy StartingVehicles max distance to fix Turrets spawning on cliffs.
- Added LuaMission function SetCirclePos(const Vector centerPos, const float Radius, const float Angle, Vector &NewPos). This function already existed, but wasn't exposed to scripts. It calculates a radial position from a central point, at the given radius (distance) and angle.
- Added LuaMission function long GetLockstepTurn(), this returns the turn count from the game.
- Added LuaMission function: ChatMessageSent() ScriptUtils callback function. Function passes in the timestep it was sent on, and also filter to only run on Chat sent to HASH_ID_ALL.
- Added LuaMission function GetIsAssault(Handle h), and SetIsAssault(Handle h, bool isAssault). These allow scripts to get and set the isAssault flag on a handle.
- Added LuaMission function BuildExplosion(odf, location, owner). This function resembles the one from BZ1's TRO expansion, allowing scripts to spawn Explosions at a given location.
- Fixed [ExplosionClass] lockdown feature not using the correct Range, and made it respect the FriendlyFire ODF parameter.
- Fixed HandleWaitingOnMessage() waitMsg char length being too long. U8 is 256 max. Also expanded UI so the list of players can now reach across the whole screen.
- MPVehicles preloads the ODF as well as the model, this helps with slow downs when first selecting the vehicle.
- Removed the left over bits from long depreciated bzgame_moves.cfg / commands. Also Commented out unused variable in GamePrefs.ini.
- Fixed typo in scrapbar cfg.
- Removed LuaMission SetUseSelectWeapon() function, did not work and would cause Bad Assets.

## Changelog - Build 2.0.196:
- Improved Error messages for ICGauge items.
- TeamPanel: Colorize the Health of allies using GetHealthColor() if hull%d is a gauge item. Otherwise color it like the GroupPanel lights.
- BasePanel: Colorize the light based on GetHealthColor() if it is a Gauge, otherwise color it like the GroupPanel lights. Added variables control.base.health1 ... control.base.health9, these are floating point values 0.0f - 1.0f, for use in UI Gauges. Added variable control.base.healthRatio1 ... control.base.healthRatio9, these are 0 - 100 ints for displaying Health % in UI text.
- Fixed Howitzer class not having point-space interaction with Enemy objects while Deployed.
- Fixed ICMenu items not sizing properly with boarder/bevel.
- Only give Single Player mission achievements if using the Stock campaign. If using a custom pilots folder, or AppendToMyDocs from a mod, don't give achievements.
- ShellHandler: Single Player menu pre-loads the tech and mail geoms to prevent lag hiccup when first selecting them.
- Commands network.session.autorefreshon and network.session.autorefreshoff now work.
- Tweaked behavior of Satellite: Satellite mode now aligns to the player's ship when Centered on the Player. Allow ship movement controls while in Satellite if using Remote Satellite. Disable movement controls while not Centered on the Player, or if logged into a Terminal as a Person. Allow Jump Control while Cursor is active.
- AIP Planners::LoadPlans() IdleAllCraft() skips Idling DeployBuilding / DeployBuildingH / Scavenger / ScavengerH that are currently Deployed. Fixes AIP switching causing Recyclers / Scavs to abort thier deploying mid-build.
- Tweaks to Rain: Rain direction can now be negative (fall upwards, or stationary). When stationary (or near-stationary) it will appear randomly around the player in 3x3x3 cubes in world-space.  When falling (or rising) the original 3x1x3 semi-camera-locked (y coordinate) cubes are used.
- Added an optional argument to command shell.multi.enter to control if it fades in or not. This parellels the same option for instant.openextras and instant.closeextras.
- Added optional argument to options.graphics.pageactivate to control if it uses FadeIn() or Activate(), similar to instant.openextras and closeextras.
- Tripmine: Add AI to objects spawned by tripmine. Fixes tripmine spawned ships/guntowers not working correctly.
- GeomRenderClass supports meshes with multiple render groups. Fixes some meshes with multiple materials not rendering properly (though they will still only use one texture applied)
- Fixed AI utility function MayHitFriends() getting a bogus shot radius when the weapon's ordnance class was actually a game object class (Dispenser, SatchelPack, TorpedoLauncher). In that case, it tried to read GameObjectClass member variable m_SecurityCheck05, which is a hash value generated from the network game version and important gameplay values. The resulting value could be extremely large or invalid (NaN) and produce unexpected results when checking if the shot would hit something important.
- ProcessMesh() tolerates missing vertex normals, logging a warning and setting the values to zero instead of failing an assert and aborting.
- Properly restore mouse clipping after closing a Windows modal dialog (Path Dialog, Object Dialog, Save/Load Requestor).
- Pathing Editor: Center the Path and Object modal dialogs within the game window.
- Fixed some map TRNs having invalid music track numbers (there is no track 1, tracks start at 2). Also fixed Scion02 not having any music.
- BasePanel update: Changed the health light to use the new control.base.health# values in a full gauge.
- GroupPanel: Consolidate the position into the Define control type.
- Added ODF property [GameObjectClass]::shareRadarWithAllies = true. If false, this unit won't share it's radar with Allied (blue) teams. This property is under [GameObjectClass] but only effects objects with Scanners: Craft, PoweredBuilding, Extractor, and TurretCraft.
- PathDisplay: Now uses Arrow Keys to pan view, just like Editor and Satellite view. Also freezes user while in Pathing View.
- Fixed IsLoginSlotValid() going out of range. Also made max Pilots a defined constant.
- Fixed VehicleList not being properly initialized due to recent teamlist changes: NetCommands: ConformBitmaskToCommanderRace() calls SetTeamplayOn() after reading NetIVarContents[3], as Team::GetTeamBlock() below relies on that.
- Fixed bug caused by bad fix for AI Re-deploying Recyclers. Redid Fix: DeployBuildingProcess / DeployBuildingHProcess: Skip DropGoto() if it is already Deployed. AIP Planners::LoadPlans() skips ordering AI Recycler to Deploy if it is already Deploying. Also tweaked GetRecycler() to return a GameObject* instead of a Recycler* as it can return both vehicle and building forms.
- Fixed AI always ejecting 100% of time, bug introduced with the DoEjectRatio code refactor. Now properly uses ejectRatio by default.

## Changelog - Build 2.0.197:
- Satellite View: Fixed clicking minimap not triggering off CenterOnPlayer mode. Fixed CommVehicle/CommVehicleH triggering CenterOnPlayer mode.
- Added new ODF parameter [HoverCraftClass]::BZ1Physics = false. If true, it will use BZ1's physics code path. This overrides moreLike12Physics, and is overriden by flyingPhysics = true.
- Added ODF parameters HoverCraftClass::DamageSpeedRatioLight = 1.0, DamageSpeedRatioMedium = 1.0, and DamageSpeedRatioHeavy = 1.0. These control the speed ratios that are effected by Damage state, just like BZ1 does. BZ1 uses values of Light: 1.0, Medium 0.75, and Heavy 0.5.
- Added new map TRN parameter World::AtmosphericDenisty = 0.0f. This is used for Hovercraft wind resistance calculations. Added new ODF Parameter to HoverCraftClass::coeffDrag = 0.01f. This is the wind resistance drag this ship expereineces based on AtmosphericDensity. BZ1 used a value of 1.0.
- Added ODF parameter HoverCraftClass::accelDragFull = 1.0f. Used by BZ1Physics = true code in Hovercaft. Also added support for accelDragFull and coeffDrag under [MorphTankClass]. Also switched Terrain::AtmosphericDensity to default to 1.0, and HoverCraft coeffDrag to default to 0.0.
- Fixed HoverCraft 1.2 and BZ1 physics not using LIFT_DAMP ODF parameter.
- Changed Hovercraft soundJump to use a ramping on/off instead of instant on/off.
- Added ODF parameter to HoverCraftClass::PlayerVelocFrontMult = 1.03f and DeployedPlayerVelocFrontMult = 1.03f. This is used by the default Hovercraft physics path as a multiplier for Players.
- Fixed SoundFly not using Ambient sound volume. ("amb_wind.wav" by default)
- Added ODF parameter GroundInteractHeight to [ConstructionRigClass], works the same as Walker/LandCreature.
- ParticleEmitters: Revamped the built-in dust/spray system:
The system still uses dusttrail.odf for ground, and spraypuff.odf for water.
Created a new odf to calibrate the dust system, "sprayeffect.odf". It contains [DustEffect] and [SprayEffect], each of which can contain the following new ODF valies:
    ParticleDensity = 2.0. // Density of particles, based on the craft's velocity. Default for DustEffect is 2.0, SprayEffect is 1.0.
    IdleParticleDensity = 1.0 // Density when not moving.
    particlePosBias = "0.0 0.0 0.0" // Particle position bias vector. Same as [ExplosionClass]
    particlePosVar = "0.0 0.0 0.0" // Particle position variance. Same as [ExplosionClass]
    particleVelocity = "0.0 0.0 0.0" // Particle Velocity Variance. Same as [ExplosionClass]
    particleBias = "0.0 0.0 0.0" // Particle Velocity bias. Same as [ExplosionClass]
    particleInherit = "0.0 0.0 0.0" // Particle velocity Inherit. Same as [ExplosionClass]
    particleVelocityMult = "0.0 0.0 0.0" // Particle Velocity Multiplier. This is a new behavior that was specific to water spray, now exposed to ODF. This adds the value, multiplied by the craft's speed.
This new ODF allows modders to calibrate the built-in dust system just like other particle Emitters systems.
- Added Velocity Mult setting to EmitRenderClass "emitVelocMult" and ExplosionClass "particleVelocMult". Multiplies the velocity based on the speed of the emitter.
- Added ODF Flags to [PersonClass]::JetpackFallDamp = 0.5f. This is the falling damping applied to pilots while falling. Also added JetpackControlMagScale = 2.5f. This is a multiplier for the additional damping applied while movement keys are pressed while falling. Also added useBZ1Jetpack = false. If true, it uses BZ1's jetpack drag curve, instead of BZ2's linear drag. BZ1 used a JetpackFallDamp of 0.1 and JetpackControlMagScale of 0.0.
- Added support for Strafe Animations in Walker and ConstructionRig.
- Added ODF parameter to WalkerClass::StrafeToSteer = true. If false, disables the turret Yaw movement and enables BZ1 style Walker physics that allow strafing.
- - Added ODF parameter horizontalResistanceMult = 0.4f, this is the sideways movement resistance factor added. (0.0 is no resistance, 1.0 is 100% resistance). This was hardcoded before.
- - Added ODF Parameters: rollStrafe = 0.0f, velocStrafe = 0.0f, omegaSpin = 5.0f, and alphaSteer = 3.0f. Also added AIvelocStrafe, AIrollStrafe, AIomegaSpin, AIalphaSteer, default to their non AI counterparts.
- Reverted Log Error about missing image files in IControl::SetImage(), it caused lots of spam about missing Icons.
- If commandline argument /odfwarnings is enabled, it will complain about missing Group Icons and Wireframes any time it preloads the ODF. Wireframe warning excludes CLASS_PERSON, and unpiloted ships. GroupIcon warning excludes items that cannot be grouped.
- Downgraded missing INF from ERR to WARN.
- Fixed several incorrect Localization entries for French items in Editor UI, and Bailout command.

## Changelog - Build 2.0.198:
- Added ODF parameter to [GameObjectClass]::InspectRange = 100.0f. This is the range for using the i key to bring up the info on an object.
- Added map TRN parameter [NormalView]::ReticleInteractRange = 0.0f. If this is > 0, it is used to clamp the reticle interaction range used in Reticle::FindReticleObject() while not in Satellite View. This value is clamped to not exceed visibilityRange.
- Added map TRN parameter [NormalView]::waterDensity = 1.0f. This is used by Hovercraft instead of AtmosphericDensity when the craft is under water.
- Made TrackedVehicle's WindDragCoef effected by the new map TRN AtmosphericDensity parameter.
- Fixed incorrect diffuse texture for Dark6.tga. (was using old bz2 texture)
- Added the new TRN properties for DM Flagfort's water to behave as expected.
- Added LuaMission functions: bool IFace_IsActive(Name n), bool IFace_IsVisible(Name n). These return the Active or Visible status of a given UI element name. Also added IFace_SetImage(Name n, Name image), sets the given UI element name's BG Image. Also added IFace_SetImageRect(Name n, x0, y0, (opt x1), (opt y1))  These set the BG image's texture coordinates. The x1 and y1 are optional, if not specified it uses the UI element's Size() parameter to auto-calculate the end x1/y1.
- Changed Map TRN parameter [NormalView]WaterUnderground and UseWaterHeightUnderground from single parameters, to WaterUnderground1 ... WaterUnderground15, and UseWaterHeightUnderground1 ... UseWaterHeightUnderground15, one for each Water Layer. This allows much finer control over the behavior on a per water layer basis, instead of a map wide basis.
- Moved ODF parameters from HoverCraftClass to CraftClass::DamageSpeedRatioLight = 1.0, DamageSpeedRatioMedium = 1.0, and DamageSpeedRatioHeavy = 1.0. Added support for these to effect Walker, TrackedVehicle, Aircraft, APC, Artillary, Bomber, SAV class. Also fixed them not working correclty with MorphTanks.
- Reverted "SoundFly not using Ambient sound volume", back to using Engine Volume.
- Revert "MPVehicles preloads the ODF as well as the model, this helps with slow downs when first selecting the vehicle."

## Changelog - Build 2.0.199:
- Fixed divide by zero crash caused by new GetPerformance() health ratio function. Now ensures it never returns 0 as a multiplier.
- Fixed a couple of references to BZ2 > BZCC in Error popups.
- Fixed French Localization of the Texture apply to all layers buttons.
- Fixed incorrect planet referenced in Scion06 briefing.
- Changed "Center Recycler" keybind to "Center Base", it now cycles base slot items, instead of just the Recycler.
- Added commands control.satellite.player and control.satellite.recycler, which trigger the parellel keybinds. Added Center Base and Center Player buttons to SatellitePanel UI, and also set them to use style "RIGHTTAB".
- Added varsys integer control.satellite.wireframe. This enables the user to toggle Wireframe view while in Satellite. Satellite remembers what view was active when it was entered, and restores it on exit, so it should be compatible with things like SITE Camera, etc.
- Added support to control the behavior of Carrier::TriggerSpecial() function. Added ODF parameter [CraftClass]::SpecialTriggerType = -1. Valid valids are: -1: Default (Trigger both Special and Pack), 0 = Trigger None, 1 = Trigger Special, 2 = Trigger Pack. This controls what hardpoint types are triggered when pressing the Fire Special keybind. Also added ODF parameter [PersonClass]::DeployTriggerType = -1. This parellels the same behavior and settings, but occurs when autoDeploy is true and the Deploy key is pressed for PersonClass objects.
- Added LuaMission functions: bool CreatePath(string name, float x, float z), int, bool AddPathPoint(string , float x, float z), bool RenamePath(string oldname, string newname), bool RemovePath(string name), int, bool RemovePathPoint(string name, int Point), bool SetPathPoint(string name, int point, float x, float z). These allow scripts to modify Paths points on a map. The boolean versions return true if it was successful, false if the path specified doesn't exist. The int versions return two different parameters: the number of paths left, and a boolean if successful. If not successful, the number of paths returned will be -1 for an invalid path, or -2 for an invalid point. Success will return the number of points, or 0 if it removed the only point left and the path was removed.
- Fully Revert "MPVehicles preloads the ODF as well as the model, this helps with slow downs when first selecting the vehicle.", even model loading caused lag.

## Changelog - Build 2.0.200:
- Fixed divide by zero in Walker forward/reverse velocity.
- Fixed divide by zero in Person forward/reverse velocity.
- Fixed divide by zero in Artillary forward/reverse velocity.
- Fixed divide by zero in APC soldierCount.
- Fixed the Escape Menu not remembering the current IFace::MenuScale and Vid Status InMenu settings on entry, and restoring them on exit. This preserves custom scripted UI element's aspect ratio when using EnterMenuMode() when going in and out of the Escape menu.
- Tweaked isHidden ODF flag to not also set damped (use canDetect for that).
- Added ODF parameter [GameObjectClass]::canAITargetHidden = true. If this is set to false, and this object is both hidden and damped (Phantom VIR + RedField) the AI will not consider it a valid target.
- Added Teamfilter, targetHidden, targetInteractable settings to ProximityMineClass. Works like the ones for the other classes.
- Added LuaMission Functions: IFace_FadeIn(ConstName n), IFace_FadeOut(ConstName n), and bool IFace_IsMenuMode(). These trigger a startFadeIn/out of the specified UI element. IFace_IsMenuMode() will return true if the IFACE is currently in MenuScale.
- Fixed ViewSatellite leaving steering control set on entry, when entering from Remote Satellite/Shift+F10 mode.