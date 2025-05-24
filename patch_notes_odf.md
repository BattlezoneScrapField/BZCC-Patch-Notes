<p align="center">
  <img width="80%" src="./BZCC.png">
</p>

# ODF Updates

| Class Type | Change |
|------------|----------------------|
| **ArtillaryClass** | |
| | Fixed Artillary class physics not interacting with hills like other flying units. Code copied from APC.cpp. Added ODF parameters [ArtillaryClass]::overWater = true, and altitudeLookahead = 0.25f. These parellel thier siblings in the other Flying unit classes. |
| **BomberBayClass** | |
| | Added ODF parameter to [BomberBayClass]::autoBuildBomber = true. If false, won't automatically spawn the Bomber when the bay is created. |
| **CameraPodClass** | |
| | Fixed CameraPods not exploding when the oldest one is removed. Added ODF Parameter [CameraPodClass]::explodeOnExpire = true. If false, it simply gets deleted when you place more then the limit of 10. |
| **CannonClass** | |
| | Added a 4th option to ODF parameter [CannonClass]::soundPerShot. If set to 3, it will play the sound only if the weapon is firing, and if the sound is not currently playing. |
| **ConstructionRigClass** | |
| | Added ODF parameter to [ConstructionRigClass]:: leftFootPiece = "lfoot", rightFootPiece = "rfoot". These allow modders to specify the model piece used for the feet. |
| | Added ODF parameter to [ConstructionRigClass]::DeathTimer = 5.0f, and ExplodeTimer = 0.4f. These work the same as their [WalkerClass] counter parts. This allows modders to match the death time with model animations for custom constructors. |
| | Added ODF parameter GroundInteractHeight to [ConstructionRigClass], works the same as Walker/LandCreature. |
| **CraftClass** | |
| | Added ODF parameter [CraftClass]::AimVarBase = 0.5f and [CraftClass]::AimVarSteer = 0.2f. These allow control over the aim variance an AI unit has that creates "wobbly aim". |
| | Added ODF parameter [CraftClass]::OffensiveProcessIsDistractableBySnipe = true. If this is false, AI won't try to harass a player that shot it with a Sniper shell. |
| | Added support for units to Recycle at Silos. Added ODF parameter [CraftClass]::CanRecycleAtSilo = false. If true, it will recycle at the nearest Recycler or Silo. If False, Recycler only. Added to [SiloClass]::recyclex = 4.0f and recycleZ = 5.0f to calibrate the Recycle point, same as Recyclers can do. |
| | Added ODF parameters [CraftClass]::DamageClassRatioLight = 0.5f, DamageClassRatioMedium = 0.25f, DamageClassRatioHeavy = 0.125f to control the Health thresholds at which the Damage Smoke states switch. |
| | Added ODF parameter [CraftClass]::useAvoidance = false. If this is true, it enables 1.2 style avoidance code. Also set Walkers and Walking construction rigs to default to Avoid type NONE. |
| | Added support to control the behavior of Carrier::TriggerSpecial() function. Added ODF parameter [CraftClass]::SpecialTriggerType = -1. Valid valids are: -1: Default (Trigger both Special and Pack), 0 = Trigger None, 1 = Trigger Special, 2 = Trigger Pack. This controls what hardpoint types are triggered when pressing the Fire Special keybind. Also added ODF parameter [PersonClass]::DeployTriggerType = -1. This parellels the same behavior and settings, but occurs when autoDeploy is true and the Deploy key is pressed for PersonClass objects. |
| **DeployableClass** | |
| | Added ODF parameter [DeployableClass]::deployToAttackAssault = true. If false, MorphTanks won't deploy to attack Assault targets. |
| | Changed [DeployableClass]/[TrackedDeployableClass] ODF parameter "switchWeaponsWhenDeployed", now reads ODF parameter "switchMask" from [DeployableClass] and [TrackedDeployableClass]. Moved SwitchMask logic from MorphTank to Deployable/TrackedDeployable. [MorphTankClass]::switchMask still overrides [DeployableClass]::switchMask. |
| **DispenserClass** | |
| | Added ODF parameter to [DispenserClass]::MaxFireHeight = 0.0f. If this is > 0, then the object won't dispense if the owner is higher than the specified height above ground or water. |
| **ExplosionClass** | |
| | Added ODF parameter to [ExplosionClass]::LockdownRadius = 0.0f, and LockdownTimer = 0.0f. If these are set, objects caught in this radius have Lockdown effect applied for the duration of the timer, same as if they got hit with EMP Lockdown. |
| | Fixed [ExplosionClass] lockdown feature not using the correct Range, and made it respect the FriendlyFire ODF parameter. |
| **ExtractorClass** | |
| | Added ODF parameter to [ExtractorClass], [SiloClass], [RecyclerClass], [ScavengerClass], and [ScavengerHClass] scrapAmount = 1. This is the amount of scrap given each scrapDelay interval. |
| **FactoryClass** | |
| | Added ODF parameters to [FactoryClass]::scaleVelX = 0.0f and scaleVelZ = 0.0f. These work similar to ScaleVelY, but for the X and Z axis. |
| **GameObjectClass** | |
| | Added ODF parameter [GameObjectClass]::AllowEffectsWhenHidden = false. If true, allows Effects to be shown even if the object is Hidden (Cloaking MorphTanks, fog of war, etc) |
| | Added new ODF parameter [GameObjectClass]::AllowLightsWhenHidden = false. If true, lights won't be suppressed for hidden objects (cloaking morphtanks, etc) |
| | Added support for Cockpit to have Init and Run animations. These work the same as InitAnimation and RunAnimation. Added ODF parameters [GameObjectClass]::InitAnimationCockpit = "", RunAnimationCockpit = "", InitAnimationIsLoopedCockpit = false, RunAnimationIsLoopedCockpit = true. |
| | Added ODF parameter to [GameObjectClass]::InspectRange = 100.0f. This is the range for using the i key to bring up the info on an object. |
| | Added ODF parameter [GameObjectClass]::canAITargetHidden = true. If this is set to false, and this object is both hidden and damped (Phantom VIR + RedField) the AI will not consider it a valid target. |
| **HoverCraftClass** | |
| | Fixed Hovercraft Terrain Lookahead always treating Buildings as terrain. Fixes Hovercraft not colliding properly with Buildings. Added ODF parameter [HoverCraftClass]::TerrainLookaheadSlopeThreshold = 0.1f. This allows the slope tolerance for building interaction to be calibrated. If the slope of a building is < tolerance, (vertical walls being 0.00001 ish) it won't try to do height elevation unless jumping. |
| | Added new ODF parameter [HoverCraftClass]::BZ1Physics = false. If true, it will use BZ1's physics code path. This overrides moreLike12Physics, and is overriden by flyingPhysics = true. |
| **Miscellaneous** | |
| | Added odf parameter RotationBias to draw_planar, draw_twirl, draw_twirl_trail. This works similar to other *bias parameters, a static value to which the random value is added to. |
| | Added ODF parameters HoverCraftClass::DamageSpeedRatioLight = 1.0, DamageSpeedRatioMedium = 1.0, and DamageSpeedRatioHeavy = 1.0. These control the speed ratios that are effected by Damage state, just like BZ1 does. BZ1 uses values of Light: 1.0, Medium 0.75, and Heavy 0.5. |
| | Added new map TRN parameter World::AtmosphericDenisty = 0.0f. This is used for Hovercraft wind resistance calculations. Added new ODF Parameter to HoverCraftClass::coeffDrag = 0.01f. This is the wind resistance drag this ship expereineces based on AtmosphericDensity. BZ1 used a value of 1.0. |
| | Fixed HoverCraft 1.2 and BZ1 physics not using LIFT_DAMP ODF parameter. |
| | Added ODF parameter to HoverCraftClass::PlayerVelocFrontMult = 1.03f and DeployedPlayerVelocFrontMult = 1.03f. This is used by the default Hovercraft physics path as a multiplier for Players. |
| | Added ODF parameter to WalkerClass::StrafeToSteer = true. If false, disables the turret Yaw movement and enables BZ1 style Walker physics that allow strafing. |
| | Added ODF parameter horizontalResistanceMult = 0.4f, this is the sideways movement resistance factor added. (0.0 is no resistance, 1.0 is 100% resistance). This was hardcoded before. |
| | Added ODF Parameters: rollStrafe = 0.0f, velocStrafe = 0.0f, omegaSpin = 5.0f, and alphaSteer = 3.0f. Also added AIvelocStrafe, AIrollStrafe, AIomegaSpin, AIalphaSteer, default to their non AI counterparts. |
| | Moved ODF parameters from HoverCraftClass to CraftClass::DamageSpeedRatioLight = 1.0, DamageSpeedRatioMedium = 1.0, and DamageSpeedRatioHeavy = 1.0. Added support for these to effect Walker, TrackedVehicle, Aircraft, APC, Artillary, Bomber, SAV class. Also fixed them not working correclty with MorphTanks. |
| **MorphTankClass** | |
| | Added canCollide to [MorphTankClass] ODF parameters. This allows modders to make a unit "phase shift" when morphing. |
| | Added ODF parameter HoverCraftClass::accelDragFull = 1.0f. Used by BZ1Physics = true code in Hovercaft. Also added support for accelDragFull and coeffDrag under [MorphTankClass]. Also switched Terrain::AtmosphericDensity to default to 1.0, and HoverCraft coeffDrag to default to 0.0. |
| **ObjectSpawnClass** | |
| | Added ODF parameter [ObjectSpawnClass]::spawnEmpty = true. If false, it won't spawn a ship as empty. |
| **OrdnanceClass** | |
| | Added ODF parameter [OrdnanceClass]::maxSpeedUsesGravity = false. If true, Grenades fall speed will be able to fall at increasing speed using gravity, like 1.2 behavior. False, they will not fall faster then shotSpeed. |
| | Added ODF Parameter [OrdnanceClass]::UseGravity = false. If true, it falls like a Grenade. GrenadeClass defaults to true. |
| **PersonClass** | |
| | Added new ODF Parameter to [PersonClass]::prioritizeGetIn = false. If true, pilots will try to GetIn empty ships, even if they have no base to go to. If there's no empty ships nearby, they will attack as normal. |
| **SatchelPackClass** | |
| | Added ODF parameter to [SatchelPackClass]::startUpright = false. If this is true, it spawns the object upright like BZ2 did. |
| **ScavengerClass** | |
| | Added ODF parameter [ScavengerClass] or [ScavengerHClass]::lockScrap = false. If this is set to True, it will prevent multiple scavengers on the same team from going after the same piece of scrap. |
| **ShieldUpgradeClass** | |
| | Added ODF parameter to [ShieldUpgradeClass]::noFirstPerson = true. If false, it enables the effect in first person view, overriding the default in shieldeffect.odf. If missing, the value in shieldeffect.odf is used. |
| **SprayBombClass** | |
| | Added ODF parameter to [SprayBombClass]::buildSprayOnExpire = false. If true, it builds it's payload when it expires, even if it doesn't hit anything. |
| **WalkerClass** | |
| | Added ODF parameter to [WalkerClass]::flattenTrackNormal = 0.0f. This re-enables the behavior of Walkers not tilting so far on steep terrain. BZ2 used a value of 2.0. Also made ConstructionRigs use the [HoverCraftClass] version of the same parameter. |
