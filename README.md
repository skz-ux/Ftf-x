local Players = game:GetService("Players")
local player = Players.LocalPlayer

local bloqueados = {
    ["nome"] = true,
    ["nome"] = true,
    ["nome"] = true,
    ["nome"] = true,
    ["nome"] = true,
    ["nome"] = true,
    ["nome"] = true,
    ["nome"] = true,
    ["nome"] = true,
    ["nome"] = true,
    ["nome"] = true,
    ["nome"] = true,
}

if bloqueados[player.Name] then
    player:Kick("Você não tem autorização para usar este script.")
    return
end

CoreGui = game:GetService("CoreGui")

if CoreGui:findFirstChild("FTFXEXECUTED") then
	return
end

Instance.new("BoolValue", CoreGui).Name = "FTFXEXECUTED"
ContextActionService = game:GetService("ContextActionService")
if not game:IsLoaded() then
	game.Loaded:Wait()
end

Players = game:GetService("Players")
RunService = game:GetService("RunService")
HttpService = game:GetService("HttpService")
Lighting = game:GetService("Lighting")
ReplicatedStorage = game:GetService("ReplicatedStorage")
UserInputService = game:GetService("UserInputService")

repo = "https://raw.githubusercontent.com/deividcomsono/Obsidian/main/"
Library = loadstring(game:HttpGet(repo .. "Library.lua"))()
ThemeManager = loadstring(game:HttpGet(repo .. "addons/ThemeManager.lua"))()
SaveManager = loadstring(game:HttpGet(repo .. "addons/SaveManager.lua"))()
Options = Library.Options

player = Players.LocalPlayer
playergui = player.PlayerGui
camera = workspace.CurrentCamera
map = ReplicatedStorage:WaitForChild("CurrentMap")






iswhitelisted = true
plusaccess = true
icon = "123805858047330"
plusicon = "86150877205669"
theicon = icon
scriptname = "SKZ 🇧🇷"




Window = Library:CreateWindow({
	Title = scriptname,
	Footer = "Version 1.0.1",
	NotifySide = "Right",
	MobileButtonsSide = "Left",
	Icon = theicon,
})

Tabs = {
	["Visual"] = Window:AddTab({
		Name = "Visual",
		Icon = "wallpaper",
		Description = "créditos: x67 / danger",
	}),
	["Gadgets"] = Window:AddTab({
		Name = "Gadgets",
		Icon = "computer",
		Description = "FTF gadgets",
	}),
	["Camera Views"] = Window:AddTab({
		Name = "Camera Views",
		Icon = "video",
		Description = "Beast and Survivor cameras",
	}),
	["Danger Settings"] = Window:AddTab({
		Name = "Danger Settings",
		Icon = "zap",
		Description = "Underhanded cheats lol",
	}),
	["Auto Farm"] = Window:AddTab({
		Name = "Auto Farm",
		Icon = "bot",
		Description = "Auto farms levels for u",
	}),
	["Esp Customization"] = Window:AddTab({
		Name = "Esp Customization",
		Icon = "palette",
		Description = "Customize visual stuff",
	}),
	["Gadget Customization"] = Window:AddTab({
		Name = "Gadget Customization",
		Icon = "palette",
		Description = "Customize your gadgets",
	}),
	["General Customization"] = Window:AddTab({
		Name = "General Customization",
		Icon = "palette",
		Description = "Customize visual stuff",
	}),
	["Trolling"] = Window:AddTab({
		Name = "Trolling",
		Icon = "angry",
		Description = "Fun",
	}),
	["Crosshair"] = Window:AddTab({
		Name = "Misc",
		Icon = "folder",
		Description = "Misc stuff",
	}),
	["UI Settings"] = Window:AddTab({
		Name = "UI Settings",
		Icon = "settings",
		Description = "Settings for the ui",
	}),
}

TabBoxes = {}

TabBoxes.Visual = {}
TabBoxes.Visual.Left = Tabs.Visual:AddLeftTabbox("Other Stuff")
TabBoxes.Visual.Right = Tabs.Visual:AddRightTabbox("Player ESP")

TabBoxes.Gadgets = {}
TabBoxes.Gadgets.Left = Tabs.Gadgets:AddLeftTabbox("Timers")
TabBoxes.Gadgets.Right = Tabs.Gadgets:AddRightTabbox("Progress Bars")

TabBoxes.EspCustomization = {}
TabBoxes.EspCustomization.Left = Tabs["Esp Customization"]:AddLeftTabbox("Player Esp")
TabBoxes.EspCustomization.Right = Tabs["Esp Customization"]:AddRightTabbox("Other")

TabBoxes.GadgetCustomization = {}
TabBoxes.GadgetCustomization.PcProgress = Tabs["Gadget Customization"]:AddLeftTabbox("PC Progress")
TabBoxes.GadgetCustomization.ExitProgress = Tabs["Gadget Customization"]:AddLeftTabbox("Exit Progress")
TabBoxes.GadgetCustomization.DoorProgress = Tabs["Gadget Customization"]:AddLeftTabbox("Door Progress")
TabBoxes.GadgetCustomization.GetupTimer = Tabs["Gadget Customization"]:AddRightTabbox("Getup Timer")
TabBoxes.GadgetCustomization.RunnerTimer = Tabs["Gadget Customization"]:AddRightTabbox("Runner Timer")
TabBoxes.GadgetCustomization.HealthTimer = Tabs["Gadget Customization"]:AddRightTabbox("Health Timer")
TabBoxes.GadgetCustomization.HeadstartTracker = Tabs["Gadget Customization"]:AddRightTabbox("HeadstartTracker")

GadgetCustomizationTabBox = Tabs["Gadget Customization"]:AddLeftTabbox("Walkspeed")
WalkspeedCustomization = GadgetCustomizationTabBox:AddTab("Walkspeed Detector")

DangerSettingsTabBox = Tabs["Danger Settings"]:AddLeftTabbox("Speed Settings")

Groupboxes = {}

Groupboxes.Visual = {}
Groupboxes.Visual.LeftGroupBox = TabBoxes.Visual.Left:AddTab("Other Esp")
Groupboxes.Visual.RightGroupBox = TabBoxes.Visual.Right:AddTab("Player ESP")

Groupboxes.Gadgets = {}
Groupboxes.Gadgets.Left = TabBoxes.Gadgets.Left:AddTab("Progress things")
Groupboxes.Gadgets.Right = TabBoxes.Gadgets.Right:AddTab("Timers")
Groupboxes.Gadgets.OtherGadgets = TabBoxes.Gadgets.Right:AddTab("Other Gadgets")

Groupboxes.EspCustomization = {}
Groupboxes.EspCustomization.PlayerEsp = TabBoxes.EspCustomization.Left:AddTab("Player")
Groupboxes.EspCustomization.Tracers = TabBoxes.EspCustomization.Left:AddTab("Tracers")
Groupboxes.EspCustomization.Skeleton = TabBoxes.EspCustomization.Left:AddTab("Skeleton")

Groupboxes.EspCustomization.PcAndTube = TabBoxes.EspCustomization.Right:AddTab("PC/Tube")
Groupboxes.EspCustomization.DoorEsp = TabBoxes.EspCustomization.Right:AddTab("Door")
Groupboxes.EspCustomization.BoxEsp = TabBoxes.EspCustomization.Right:AddTab("Box")

Groupboxes.GadgetCustomization = {}
Groupboxes.GadgetCustomization.PcProgress = TabBoxes.GadgetCustomization.PcProgress:AddTab("PC Progress")
Groupboxes.GadgetCustomization.ExitProgress = TabBoxes.GadgetCustomization.ExitProgress:AddTab("Exit Progress")
Groupboxes.GadgetCustomization.DoorProgress = TabBoxes.GadgetCustomization.DoorProgress:AddTab("Door Progress")
Groupboxes.GadgetCustomization.GetupTimer = TabBoxes.GadgetCustomization.GetupTimer:AddTab("Getup Timer")
Groupboxes.GadgetCustomization.RunnerTimer = TabBoxes.GadgetCustomization.RunnerTimer:AddTab("Runner Timer")
Groupboxes.GadgetCustomization.HealthTimer = TabBoxes.GadgetCustomization.HealthTimer:AddTab("Health Timer")
Groupboxes.GadgetCustomization.HeadstartTracker =
	TabBoxes.GadgetCustomization.HeadstartTracker:AddTab("Headstart Tracker")

Settings = {
	EspSettings = {
		PlayerEsp = {
			Enabled = false,
			ShowNames = false,
			ShowDistance = false,
			UseSkeletonEsp = false,
			UseCloneEsp = false,
			UseBoxEsp = false,
			UseRainbowEsp = false,
			SurvivorFillColor = Color3.fromRGB(0, 255, 0),
			BeastFillColor = Color3.fromRGB(255, 0, 0),
			SurvivorOutlineColor = Color3.fromRGB(0, 0, 0),
			BeastOutlineColor = Color3.fromRGB(0, 0, 0),
			BeastOutlineTransparancy = 0,
			SurvivorOutlineTransparancy = 0,
			SurvivorFillTransparancy = 0.5,
			BeastFillTransparancy = 0.5,
			TracerSettings = {
				Enabled = false,
				Thickness = 2,
				Color = Color3.new(0, 1, 0),
				FromBottom = true,
				Transparancy = 0,
			},
			SkeletonSettings = {
				Color = Color3.new(0, 1, 0),
				Thickness = 2,
				Transparency = 1,
			},
			BoxEsp = {
				Color = Color3.new(0, 1, 0),
				Thickness = 2,
				Transparency = 1,
			},
			d3esp = {
				Enabled = false,
				SurvivorFillColor = Color3.fromRGB(0, 255, 0),
				BeastFillColor = Color3.fromRGB(255, 0, 0),
			},
		},
		PcEsp = {
			Enabled = false,
			FillColor = Color3.fromRGB(0, 150, 255),
			OutlineColor = Color3.fromRGB(0, 0, 0),
			OutlineTransparency = 0.25,
			FillTransparency = 0.5,
		},
		TubeEsp = {
			Enabled = false,
			FillColor = Color3.fromRGB(13, 105, 172),
			OutlineColor = Color3.fromRGB(0, 0, 0),
			OutlineTransparency = 0.25,
			FillTransparency = 0.5,
		},
		ExitEsp = {
			Enabled = false,
			FillColor = Color3.fromRGB(85, 255, 127),
			OutlineColor = Color3.fromRGB(0, 0, 0),
			OutlineTransparency = 0.25,
			FillTransparency = 0.5,
		},
		DoorEsp = {
			Enabled = false,
			OpenColor = Color3.fromRGB(0, 255, 0),
			ClosedColor = Color3.fromRGB(255, 0, 0),
			OpenOutlineColor = Color3.fromRGB(0, 0, 0),
			ClosedOutlineColor = Color3.fromRGB(0, 0, 0),
			OutlineTransparency = 0.25,
			ClosedFillTransparency = 0.5,
			OpenFillTransparency = 0.5,
		},
	},
	GadgetSettings = {
		ProgressSettings = {
			PcProgress = {
				Enabled = false,
				TextColor = Color3.fromRGB(255, 255, 255),
				ProgressFill = Color3.fromRGB(255, 255, 255),
				BackgroundColor = Color3.fromRGB(32, 32, 32),
				ProgressTransparancy = 0.1,
				BackgroundTransparancy = 0.4,
				DisplaySeconds = false,
			},
			ExitProgress = {
				Enabled = false,
				TextColor = Color3.fromRGB(85, 255, 127),
				ProgressFill = Color3.fromRGB(85, 255, 127),
				BackgroundColor = Color3.fromRGB(32, 32, 32),
				ProgressTransparancy = 0.1,
				BackgroundTransparancy = 0.4,
				DisplaySeconds = false,
				DisplayOpener = false,
				OpenerTextColor = Color3.fromRGB(255, 255, 0),
			},
			DoorProgress = {
				Enabled = false,
				TextColor = Color3.fromRGB(133, 88, 0),
				ProgressFill = Color3.fromRGB(133, 88, 0),
				BackgroundColor = Color3.fromRGB(32, 32, 32),
				ProgressTransparancy = 0.1,
				BackgroundTransparancy = 0.4,
				DisplaySeconds = false,
				DisplayOpener = false,
				OpenerTextColor = Color3.fromRGB(255, 255, 0),
			},
			GetupTimer = {
				Enabled = false,
				NotHitColor = Color3.fromRGB(255, 0, 0),
				HitColor = Color3.fromRGB(34, 255, 0),
				WhenToHit = 0.5,
			},
			RunnerTimer = {
				Enabled = false,
				DisplaySeconds = false,
				Thread = nil,
				TextColor = Color3.fromRGB(255, 255, 255),
			},
			HealthTimer = {
				Enabled = false,
				DisplaySeconds = true,
				DisplayName = false,
				HighHpColor = Color3.fromRGB(0, 195, 255),
				LowHpColor = Color3.fromRGB(151, 0, 0),
				LowHp = 50,
				HighHpStrokeColor = Color3.fromRGB(0, 0, 0),
				LowHpStrokeColor = Color3.fromRGB(0, 0, 0),
			},
		},
		OtherGadgets = {
			HideBlack = false,
			WalkspeedDetector = {
				Enabled = false,
				UseAdvancedDetection = false,
				TextColor = Color3.fromRGB(255, 255, 255),
				StrokeColor = Color3.fromRGB(0, 0, 0),
				TextTransparency = 0,
				StrokeTransparency = 0,
			},
			HeadstartTracker = {
				Enabled = false,
				TextColor = Color3.fromRGB(255, 255, 255),
				StrokeColor = Color3.fromRGB(0, 0, 0),
				StrokeTransparancy = 0,
				TextTransparancy = 0,
				TrackerConnection = nil,
			},
		},
	},
}

SpeedSettings = {
	Enabled = false,

	SurvivorSpeed = 16,
	BeastSpeed = 17,
	RunnerSpeed = 26,
	FatigueSpeed = 3.4,
	CrawlSpeed = 8,

	SurvivorBoost = 1,
	BeastBoost = 1,
	RunnerBoost = 2,
	FatigueBoost = 1,
	CrawlBoost = 2,

	SurvivorJumpPower = 36,
	BeastJumpPower = 36,
	AllowJumpDuringRunner = false,

	Connection = nil,

	UseFatigueCheats = false,
	FatigueDelay = 0,
	FatigueDuration = 0.8,
	FatigueStartTime = nil,
	FatigueConnection = nil,
	FatigueBoostActive = false,
}
FogSettings = {
	Enabled = false,
	LightingFolder = nil,
	OriginalLightingElements = {},
}

WallhopSettings = {
	Enabled = false,
	SelectionBoxes = {},
}

BarrierSettings = {
	Enabled = false,
	OriginalTransparencies = {},
}

CameraSettings = {
	CameraSlots = {
		Beast = { Enabled = false, Player = nil, Position = Vector2.new(0.05, 0.1), Size = Vector2.new(0.25, 0.25) },
		Surv1 = { Enabled = false, Player = nil, Position = Vector2.new(0.32, 0.1), Size = Vector2.new(0.25, 0.25) },
		Surv2 = { Enabled = false, Player = nil, Position = Vector2.new(0.59, 0.1), Size = Vector2.new(0.25, 0.25) },
		Surv3 = { Enabled = false, Player = nil, Position = Vector2.new(0.05, 0.4), Size = Vector2.new(0.25, 0.25) },
		Surv4 = { Enabled = false, Player = nil, Position = Vector2.new(0.32, 0.4), Size = Vector2.new(0.25, 0.25) },
	},
	CameraGuis = {},
}

CrosshairSettings = {
	Enabled = false,
	Type = "Cross",
	Color = Color3.new(0, 1, 0),
	Thickness = 2,
	Size = 10,
	Gap = 5,
	Transparency = 0,
	OutlineEnabled = true,
	OutlineColor = Color3.new(0, 0, 0),
	OutlineThickness = 1,
	CenterDot = false,
	CenterDotSize = 3,
	CenterDotColor = Color3.new(1, 1, 1),
	DynamicCrosshair = false,
	DynamicSize = 15,
}
BushSettings = {
	Enabled = false,
	Cached = {},
}

ShadowSettings = {
	Enabled = false,
	OriginalState = true,
}

AutoFarmSettings = {
	Enabled = false,
	FarmAsSurvivor = false,
	DistanceConnection = nil,
	GotoComputersWithMostProg = false,
	AutoSave = false,
	LastActionTime = 0,
	ActionCooldown = 2,
	TeleportCooldown = 0.5,
	LastTeleportTime = 0,
}

TrollSettings = {
	AutoFatigue = {
		Enabled = false,
		Interval = 1,
		Connection = nil,
	},
	AutoAbility = {
		Enabled = false,
		Interval = 1,
		Connection = nil,
	},
	AutoUnrope = {
		Enabled = false,
		TargetPlayer = nil,
		Connection = nil,
	},
	RopedPlayers = {},
}

CameraConfigSettings = {
	ConfigFolder = "FTFX/CameraConfigs",
}

KillAuraSettings = {
	Enabled = false,
	TargetAll = true,
	TargetPlayer = nil,
	MaxDistance = 30,
	Connection = nil,
	LastHitTimes = {},
	HitCooldown = 0.5,
}

RopeHelperSettings = {
	Enabled = false,
	AutoRopeOnHit = false,
	ClickToRope = false,
	MaxDistance = 30,
	RopedPlayers = {},
	RagdollStates = {},
	RandomizePart = false,
	SelectedPart = "Torso",
	RopeDebounce = {},
	DebounceTime = 0,
}
PlayerConnections = {
	EspConnections = {},
	PcEsp = {},
	TubeEsp = {},
	ExitEsp = {},
	DoorEsp = {},
}

SpectateSettings = {
	Enabled = false,
	TargetPlayer = nil,
	ViewDied = nil,
	ViewChanged = nil,
}

FlopSettings = {
	Enabled = false,
	Delay = 1.5,
	XMultiplier = 1,
	YMultiplier = 0,
	ZMultiplier = 1,
	LastFlopTime = 0,
	FlopConnection = nil,
}

SkeletonUIs = {}
SkeletonConnections = {}

TracerLines = {}
TracerConnections = {}

BoxConnections = {}
BoxUIs = {}

previousValues = {}

HitPlayers = {}
GetupConnections = {}
GetupUis = {}
c = 28

computers = {}
exits = {}
doors = {}

objectProgress = {
	computers = {},
	doors = {},
	exits = {},
}

PlayerHealthUis = {}
PlayerHealths = {}
CapturedPlayers = {}

crosshairElements = {}

CapturedPlayerUIs = {}

runnerStates = {}

WalkspeedUIs = {}
WalkspeedTracking = {}

lastUpdate = 0
UPDATE_INTERVAL = 1 / 60

RankData = {
	["VIP"] = { Color = "#CC0000", Icon = "rbxassetid://1188562340" },
	["LEAD DEV"] = { Color = "#00FF33", Icon = "rbxassetid://18937953345" },
	["MAN"] = { Color = "#ff34c4", Icon = "rbxassetid://131476591459702" },
	["DEV"] = { Color = "#1E5CBA", Icon = "rbxassetid://18940006678" },
	["QA"] = { Color = "#F85E5E", Icon = "rbxassetid://18940008283" },
	["MOD"] = { Color = "#bc3fff", Icon = "rbxassetid://105155010224102" },
	["CON"] = { Color = "#1ABC9C", Icon = "rbxassetid://18940005647" },
}

RankList = { "None", "VIP", "LEAD DEV", "MAN", "DEV", "QA", "MOD", "CON" }

ThreeDESPObjects = {}

RainbowEspState = {
	Enabled = false,
	Hue = 0,
	Speed = 0.5,
	Connection = nil,
}

FontSettings = {
	Enabled = false,
	SelectedFont = Enum.Font.SourceSans,
	CachedTextObjects = {},
	Connections = {},
}

TextureSettings = {
	Enabled = false,
	SelectedTexture = Enum.Material.Plastic,
	CachedParts = {},
	OriginalMaterials = {},
	PerPartColors = {},
	UsePerPartColors = false,
	DefaultColor = Color3.fromRGB(163, 162, 165),
}

GreyAvatarSettings = {
	Enabled = false,
	OriginalColors = {},
	CachedCharacters = {},
}

BlackFogGammaSettings = {
	Enabled = false,
	GammaValue = 1,
	OriginalBrightness = nil,
	ColorCorrection = nil,
}

SoundBoosterSettings = {
	Enabled = true,
	HeartbeatVolume = 1,
	StepsVolume = 1,
	JumpsVolume = 1,
	CachedSounds = {},
	Connections = {},
}

ShaderSettings = {
	Enabled = false,
	CurrentShader = nil,
	ShaderData = {},
	SunFlareEnabled = false,
	MotionBlurEnabled = false,
	GlobalIlluminationEnabled = false,
	Technology = "ShadowMap",
}

shaderlight = {
	["yfbghj"] = Lighting.Ambient,
	["tgvbyd"] = Lighting.ClockTime,
	["ghuybhuyhj"] = Lighting.GeographicLatitude,
	["khnbfth"] = Lighting.Brightness,
	["hgyghkg"] = Lighting.ColorShift_Bottom,
	["yfbhjku"] = Lighting.ColorShift_Top,
	["ygyyfgvhbjytrt"] = Lighting.EnvironmentDiffuseScale,
	["sdfcddc"] = Lighting.EnvironmentSpecularScale,
	["hgnujuu7thgr"] = Lighting.GlobalShadows,
	["hyhnngtf"] = Lighting.OutdoorAmbient,
	["hdfr7thgr"] = Lighting.ExposureCompensation,
	["fhnchvhfjsd"] = 0,
	["ugtbbjhygt"] = 0,
	["tfbghuugbnjhg"] = 0,
	["fvrtccvghghj"] = Color3.fromRGB(255, 255, 255),
	["jnfdhbnfcvh"] = 0.4,
	["fvtyghj"] = 24,
	["ygbhnj"] = 0.95,
	["njnfg"] = 0,
	["jdfkd"] = 0.1,
	["fvgsdfg"] = 50,
	["sdkvkflv"] = 10,
	["hbjhd"] = 0.75,
	["gyhgtg"] = 0,
	["ygbhggv"] = 0,
	["jghbjhgyfd"] = Color3.fromRGB(255, 255, 255),
	["shdbsnjfc"] = 0,
	["skdjfkdm"] = 0,
	["sjdjncdjf"] = Color3.fromRGB(199, 199, 199),
	["efjdjfk"] = Color3.fromRGB(106, 112, 125),
	["sejfd"] = 0,
	["jddfjsd"] = 0,
}

backupLighting = {
	["ClockTime"] = Lighting.ClockTime,
	["Ambient"] = Lighting.Ambient,
	["Brightness"] = Lighting.Brightness,
	["ColorShift_Bottom"] = Lighting.ColorShift_Bottom,
	["ColorShift_Top"] = Lighting.ColorShift_Top,
	["EnvironmentDiffuseScale"] = Lighting.EnvironmentDiffuseScale,
	["EnvironmentSpecularScale"] = Lighting.EnvironmentSpecularScale,
	["GlobalShadows"] = Lighting.GlobalShadows,
	["OutdoorAmbient"] = Lighting.OutdoorAmbient,
	["ExposureCompensation"] = Lighting.ExposureCompensation,
	["FogEnd"] = Lighting.FogEnd,
	["FogColor"] = Lighting.FogColor,
	["FogStart"] = Lighting.FogStart,
	["GeographicLatitude"] = Lighting.GeographicLatitude,
	["Technology"] = Lighting.Technology,
}

shaderWL = {
	["dof"] = false,
	["cor"] = true,
	["sray"] = false,
	["bl"] = true,
	["blr"] = false,
	["tech"] = "ShadowMap",
}

ResolutionSettings = {
	Enabled = false,
	ResolutionScale = 1,
	Connection = nil,
}

function createR6Dummy(cf)
	local m = Instance.new("Model")
	m.Name = "R6Dummy"
	m.Parent = workspace

	local function p(n, s, c)
		local x = Instance.new("Part")
		x.Name = n
		x.Size = s
		x.CFrame = c
		x.Anchored = false
		x.CanCollide = false
		x.TopSurface = 0
		x.BottomSurface = 0
		x.Parent = m
		return x
	end

	local hrp = p("HumanoidRootPart", Vector3.new(2, 2, 1), cf)
	hrp.Transparency = 1
	local torso = p("Torso", Vector3.new(2, 2, 1), cf)
	local head = p("Head", Vector3.new(2, 1, 1), cf * CFrame.new(0, 1.5, 0))
	local la = p("Left Arm", Vector3.new(1, 2, 1), cf * CFrame.new(-1.5, 0, 0))
	local ra = p("Right Arm", Vector3.new(1, 2, 1), cf * CFrame.new(1.5, 0, 0))
	local ll = p("Left Leg", Vector3.new(1, 2, 1), cf * CFrame.new(-0.5, -2, 0))
	local rl = p("Right Leg", Vector3.new(1, 2, 1), cf * CFrame.new(0.5, -2, 0))

	local function m6(n, a, b, c0, c1)
		local j = Instance.new("Motor6D")
		j.Name = n
		j.Part0 = a
		j.Part1 = b
		j.C0 = c0
		j.C1 = c1
		j.Parent = a
	end

	m6("RootJoint", hrp, torso, CFrame.new(), CFrame.new())
	m6("Neck", torso, head, CFrame.new(0, 1, 0), CFrame.new(0, -0.5, 0))
	m6("Left Shoulder", torso, la, CFrame.new(-1, 0.5, 0), CFrame.new(0.5, 0.5, 0))
	m6("Right Shoulder", torso, ra, CFrame.new(1, 0.5, 0), CFrame.new(-0.5, 0.5, 0))
	m6("Left Hip", torso, ll, CFrame.new(-0.5, -1, 0), CFrame.new(0, 1, 0))
	m6("Right Hip", torso, rl, CFrame.new(0.5, -1, 0), CFrame.new(0, 1, 0))

	local d = Instance.new("Decal", head)
	d.Texture = "rbxasset://textures/face.png"
	d.Name = "face"

	local h = Instance.new("Humanoid")
	h.RigType = Enum.HumanoidRigType.R6
	h.Parent = m

	return m
end

function applyavatar(targetplayername, idorusername)
	local isid = typeof(idorusername) == "number"
	local description

	if isid then
		local success, desc = pcall(function()
			return Players:GetHumanoidDescriptionFromUserId(idorusername)
		end)
		if not success or not desc then
			Library:Notify("The player you're trying to change your avatar into doesn't exist!")
			return
		end
		description = desc
	else
		local success, actualuserid = pcall(function()
			return Players:GetUserIdFromNameAsync(idorusername)
		end)
		if not success or not actualuserid then
			Library:Notify("The player youre trying to change your avatar into doesnt exist!")
			return
		end
		local success2, desc = pcall(function()
			return Players:GetHumanoidDescriptionFromUserId(actualuserid)
		end)
		if not success2 or not desc then
			Library:Notify("Failed to get humanoid description!")
			return
		end
		description = desc
	end

	local doesplayerexist = Players:FindFirstChild(targetplayername)
	if not doesplayerexist then
		Library:Notify("Youre trying to change the avatar of a player thats not in the game!")
		return
	end

	local thechar = doesplayerexist.Character
	if not thechar then
		Library:Notify("The player youre trying to change the avatar of has no character!")
		return
	end

	local thehumanoid = thechar:FindFirstChild("Humanoid")
	if not thehumanoid then
		Library:Notify("Character has no humanoid!")
		return
	end

	for _, part in ipairs(thechar:GetChildren()) do
		if
			part:IsA("Accessory")
			or part:IsA("Hat")
			or part:IsA("Shirt")
			or part:IsA("Pants")
			or part:IsA("ShirtGraphic")
			or part:IsA("CharacterMesh")
			or part:IsA("BodyColors")
		then
			part:Destroy()
		end
	end

	local headpart = thechar:FindFirstChild("Head")
	if headpart then
		for _, child in ipairs(headpart:GetChildren()) do
			if child:IsA("Decal") or child:IsA("Texture") then
				child:Destroy()
			end
		end
	end

	local burnerrig = createR6Dummy(CFrame.new(10000, 10000, 10000))
	local burnerhumanoid = burnerrig:FindFirstChild("Humanoid")
	burnerhumanoid:ApplyDescription(description)
	task.wait(3)

	for _, part in ipairs(burnerrig:GetChildren()) do
		if part:IsA("Accessory") or part:IsA("Hat") then
			local cloned = part:Clone()
			cloned.Parent = thechar

			local handle = cloned:FindFirstChild("Handle")
			if handle then
				local attached = false
				local handleAttachment = handle:FindFirstChildOfClass("Attachment")
				if handleAttachment then
					local attachmentName = handleAttachment.Name
					for _, bodyPart in ipairs(thechar:GetChildren()) do
						if bodyPart:IsA("BasePart") then
							local matchingAttachment = bodyPart:FindFirstChild(attachmentName)
							if matchingAttachment and matchingAttachment:IsA("Attachment") then
								local weld = handle:FindFirstChild("AccessoryWeld")
								if not weld then
									weld = Instance.new("Weld")
									weld.Name = "AccessoryWeld"
									weld.Parent = handle
								end
								weld.Part0 = handle
								weld.Part1 = bodyPart
								weld.C0 = handleAttachment.CFrame
								weld.C1 = matchingAttachment.CFrame
								attached = true
								break
							end
						end
					end
				end
				if not attached and headpart then
					local weld = handle:FindFirstChild("AccessoryWeld")
					if not weld then
						weld = Instance.new("Weld")
						weld.Name = "AccessoryWeld"
						weld.Parent = handle
					end
					weld.Part0 = handle
					weld.Part1 = headpart
					weld.C0 = CFrame.new()
					weld.C1 = CFrame.new(0, headpart.Size.Y / 2, 0)
				end
			end
		elseif
			part:IsA("Shirt")
			or part:IsA("Pants")
			or part:IsA("ShirtGraphic")
			or part:IsA("CharacterMesh")
			or part:IsA("BodyColors")
		then
			part:Clone().Parent = thechar
		end
	end

	local burnerhead = burnerrig:FindFirstChild("Head")
	if burnerhead and headpart then
		local burnerMesh = burnerhead:FindFirstChildOfClass("SpecialMesh")
		local targetMesh = headpart:FindFirstChildOfClass("SpecialMesh")
		if burnerMesh then
			if targetMesh then
				pcall(function()
					targetMesh.MeshType = burnerMesh.MeshType
				end)
				pcall(function()
					targetMesh.MeshId = burnerMesh.MeshId
				end)
				pcall(function()
					targetMesh.TextureId = burnerMesh.TextureId
				end)
				pcall(function()
					targetMesh.Scale = burnerMesh.Scale
				end)
				pcall(function()
					targetMesh.Offset = burnerMesh.Offset
				end)
				pcall(function()
					targetMesh.VertexColor = burnerMesh.VertexColor
				end)
			else
				burnerMesh:Clone().Parent = headpart
			end
		end

		local foundFace = false
		for _, child in ipairs(burnerhead:GetChildren()) do
			if child:IsA("Decal") or child:IsA("Texture") then
				child:Clone().Parent = headpart
				foundFace = true
			end
		end

		if not foundFace and description.Face and description.Face ~= 0 then
			local faceDecal = Instance.new("Decal")
			faceDecal.Name = "face"
			faceDecal.Texture = "rbxassetid://" .. tostring(description.Face)
			faceDecal.Parent = headpart
		end
	end

	local r6ColorMap = {
		Head = description.HeadColor,
		Torso = description.TorsoColor,
		["Left Arm"] = description.LeftArmColor,
		["Right Arm"] = description.RightArmColor,
		["Left Leg"] = description.LeftLegColor,
		["Right Leg"] = description.RightLegColor,
	}
	for partName, color in pairs(r6ColorMap) do
		local targetPart = thechar:FindFirstChild(partName)
		if targetPart and targetPart:IsA("BasePart") and color then
			targetPart.Color = color
		end
	end

	local scaleNames = {
		"BodyDepthScale",
		"BodyHeightScale",
		"BodyWidthScale",
		"HeadScale",
		"BodyTypeScale",
		"BodyProportionScale",
	}
	for _, scaleName in ipairs(scaleNames) do
		local burnerScale = burnerhumanoid:FindFirstChild(scaleName)
		local targetScale = thehumanoid:FindFirstChild(scaleName)
		if burnerScale and targetScale and burnerScale:IsA("NumberValue") and targetScale:IsA("NumberValue") then
			targetScale.Value = burnerScale.Value
		elseif burnerScale and burnerScale:IsA("NumberValue") and not targetScale then
			local newScale = Instance.new("NumberValue")
			newScale.Name = scaleName
			newScale.Value = burnerScale.Value
			newScale.Parent = thehumanoid
		end
	end

	burnerrig:Destroy()
	Library:Notify("Avatar applied successfully!", 3)
end

local function ApplyGreyToCharacter(character)
	if not GreyAvatarSettings.Enabled then
		return
	end

	for _, part in ipairs(character:GetDescendants()) do
		if part:IsA("BasePart") and part.Name ~= "HumanoidRootPart" then
			if not GreyAvatarSettings.OriginalColors[part] then
				GreyAvatarSettings.OriginalColors[part] = {
					Color = part.Color,
					Material = part.Material,
				}
			end
			local grey = (part.Color.R + part.Color.G + part.Color.B) / 3
			part.Color = Color3.new(grey, grey, grey)
		elseif part:IsA("MeshPart") then
			if not GreyAvatarSettings.OriginalColors[part] then
				GreyAvatarSettings.OriginalColors[part] = {
					TextureID = part.TextureID,
				}
			end
			part.TextureID = ""
		end
	end

	for _, accessory in ipairs(character:GetChildren()) do
		if accessory:IsA("Accessory") then
			local handle = accessory:FindFirstChild("Handle")
			if handle then
				for _, child in ipairs(handle:GetDescendants()) do
					if child:IsA("BasePart") or child:IsA("MeshPart") then
						if not GreyAvatarSettings.OriginalColors[child] then
							GreyAvatarSettings.OriginalColors[child] = {
								Color = child.Color,
							}
						end
						local grey = (child.Color.R + child.Color.G + child.Color.B) / 3
						child.Color = Color3.new(grey, grey, grey)
					end
				end
			end
		end
	end

	local bodyColors = character:FindFirstChild("Body Colors")
	if bodyColors then
		if not GreyAvatarSettings.OriginalColors[bodyColors] then
			GreyAvatarSettings.OriginalColors[bodyColors] = {
				HeadColor = bodyColors.HeadColor,
				TorsoColor = bodyColors.TorsoColor,
				LeftArmColor = bodyColors.LeftArmColor,
				RightArmColor = bodyColors.RightArmColor,
				LeftLegColor = bodyColors.LeftLegColor,
				RightLegColor = bodyColors.RightLegColor,
			}
		end
		local grey = BrickColor.new("Medium stone grey")
		bodyColors.HeadColor = grey
		bodyColors.TorsoColor = grey
		bodyColors.LeftArmColor = grey
		bodyColors.RightArmColor = grey
		bodyColors.LeftLegColor = grey
		bodyColors.RightLegColor = grey
	end
end

local function StartGreyAvatar()
	for _, plr in ipairs(Players:GetPlayers()) do
		if plr ~= player and plr.Character then
			ApplyGreyToCharacter(plr.Character)
			GreyAvatarSettings.CachedCharacters[plr] = plr.CharacterAdded:Connect(function(char)
				task.wait(1)
				ApplyGreyToCharacter(char)
			end)
		end
	end

	ConnectionManager:AddGlobal(
		"GreyAvatarPlayerAdded",
		Players.PlayerAdded:Connect(function(plr)
			if plr ~= player then
				plr.CharacterAdded:Connect(function(char)
					task.wait(1)
					if GreyAvatarSettings.Enabled then
						ApplyGreyToCharacter(char)
					end
				end)
			end
		end)
	)
end

local function StopGreyAvatar()
	for part, originalData in pairs(GreyAvatarSettings.OriginalColors) do
		if part and part.Parent then
			if part:IsA("BasePart") or part:IsA("MeshPart") then
				if originalData.Color then
					part.Color = originalData.Color
				end
				if originalData.Material then
					part.Material = originalData.Material
				end
				if originalData.TextureID then
					part.TextureID = originalData.TextureID
				end
			elseif part:IsA("BodyColors") then
				part.HeadColor = originalData.HeadColor
				part.TorsoColor = originalData.TorsoColor
				part.LeftArmColor = originalData.LeftArmColor
				part.RightArmColor = originalData.RightArmColor
				part.LeftLegColor = originalData.LeftLegColor
				part.RightLegColor = originalData.RightLegColor
			end
		end
	end
	GreyAvatarSettings.OriginalColors = {}

	for _, conn in pairs(GreyAvatarSettings.CachedCharacters) do
		conn:Disconnect()
	end
	GreyAvatarSettings.CachedCharacters = {}
end

function UpdateBlackFogGamma()
	if not BlackFogGammaSettings.Enabled or not BlackFogGammaSettings.ColorCorrection then
		return
	end

	local gamma = BlackFogGammaSettings.GammaValue
	local brightness = (gamma - 1) * 0.5
	BlackFogGammaSettings.ColorCorrection.Brightness = brightness
	BlackFogGammaSettings.ColorCorrection.Contrast = gamma * 0.2
end

function StartBlackFogGamma()
	if not BlackFogGammaSettings.ColorCorrection then
		BlackFogGammaSettings.ColorCorrection = Lighting:FindFirstChild("BlackFogGammaCorrection")
		if not BlackFogGammaSettings.ColorCorrection then
			BlackFogGammaSettings.ColorCorrection = Instance.new("ColorCorrectionEffect")
			BlackFogGammaSettings.ColorCorrection.Name = "BlackFogGammaCorrection"
			BlackFogGammaSettings.ColorCorrection.Parent = Lighting
		end
		BlackFogGammaSettings.OriginalBrightness = BlackFogGammaSettings.ColorCorrection.Brightness
	end
	UpdateBlackFogGamma()
end

function StopBlackFogGamma()
	if BlackFogGammaSettings.ColorCorrection then
		if BlackFogGammaSettings.OriginalBrightness then
			BlackFogGammaSettings.ColorCorrection.Brightness = BlackFogGammaSettings.OriginalBrightness
			BlackFogGammaSettings.ColorCorrection.Contrast = 0
		end
	end
end

local function BoostCharacterSounds(character)
	if not SoundBoosterSettings.Enabled then
		return
	end

	for _, sound in ipairs(character:GetDescendants()) do
		if sound:IsA("Sound") then
			local soundName = sound.Name:lower()
			if not SoundBoosterSettings.CachedSounds[sound] then
				SoundBoosterSettings.CachedSounds[sound] = {
					OriginalVolume = sound.Volume,
					Type = nil,
				}

				if soundName:find("heartbeat") or soundName:find("heart") then
					SoundBoosterSettings.CachedSounds[sound].Type = "Heartbeat"
				elseif
					soundName:find("step")
					or soundName:find("footstep")
					or soundName:find("walk")
					or soundName:find("running")
				then
					SoundBoosterSettings.CachedSounds[sound].Type = "Steps"
				elseif soundName:find("jump") or soundName:find("land") then
					SoundBoosterSettings.CachedSounds[sound].Type = "Jumps"
				end
			end

			local soundData = SoundBoosterSettings.CachedSounds[sound]
			if soundData.Type == "Heartbeat" then
				sound.Volume = soundData.OriginalVolume * SoundBoosterSettings.HeartbeatVolume
			elseif soundData.Type == "Steps" then
				sound.Volume = soundData.OriginalVolume * SoundBoosterSettings.StepsVolume
			elseif soundData.Type == "Jumps" then
				sound.Volume = soundData.OriginalVolume * SoundBoosterSettings.JumpsVolume
			end
		end
	end
end

local function StartSoundBooster()
	for _, plr in ipairs(Players:GetPlayers()) do
		if plr.Character then
			BoostCharacterSounds(plr.Character)
		end
	end

	for _, sound in ipairs(workspace:GetDescendants()) do
		if sound:IsA("Sound") then
			local soundName = sound.Name:lower()
			if not SoundBoosterSettings.CachedSounds[sound] then
				SoundBoosterSettings.CachedSounds[sound] = {
					OriginalVolume = sound.Volume,
					Type = nil,
				}

				if soundName:find("heartbeat") or soundName:find("heart") then
					SoundBoosterSettings.CachedSounds[sound].Type = "Heartbeat"
					sound.Volume = sound.Volume * SoundBoosterSettings.HeartbeatVolume
				end
			end
		end
	end

	table.insert(
		SoundBoosterSettings.Connections,
		workspace.DescendantAdded:Connect(function(obj)
			if obj:IsA("Sound") and SoundBoosterSettings.Enabled then
				local soundName = obj.Name:lower()
				SoundBoosterSettings.CachedSounds[obj] = {
					OriginalVolume = obj.Volume,
					Type = nil,
				}

				if soundName:find("heartbeat") or soundName:find("heart") then
					SoundBoosterSettings.CachedSounds[obj].Type = "Heartbeat"
					obj.Volume = obj.Volume * SoundBoosterSettings.HeartbeatVolume
				end
			end
		end)
	)

	ConnectionManager:AddGlobal(
		"SoundBoosterHeartbeat",
		RunService.Heartbeat:Connect(function()
			if not SoundBoosterSettings.Enabled then
				return
			end

			for _, plr in ipairs(Players:GetPlayers()) do
				if plr.Character then
					BoostCharacterSounds(plr.Character)
				end
			end

			local beast = GetBeast()
			if beast then
				for _, sound in ipairs(beast:GetDescendants()) do
					if sound:IsA("Sound") then
						local soundName = sound.Name:lower()
						if soundName:find("heartbeat") or soundName:find("heart") then
							if not SoundBoosterSettings.CachedSounds[sound] then
								SoundBoosterSettings.CachedSounds[sound] = {
									OriginalVolume = sound.Volume,
									Type = "Heartbeat",
								}
							end
							sound.Volume = SoundBoosterSettings.CachedSounds[sound].OriginalVolume
								* SoundBoosterSettings.HeartbeatVolume
						end
					end
				end
			end
		end)
	)
end

local function StopSoundBooster()
	for sound, soundData in pairs(SoundBoosterSettings.CachedSounds) do
		if sound and sound.Parent then
			sound.Volume = soundData.OriginalVolume
		end
	end
	SoundBoosterSettings.CachedSounds = {}

	for _, conn in ipairs(SoundBoosterSettings.Connections) do
		conn:Disconnect()
	end
	SoundBoosterSettings.Connections = {}
end

local function UpdateSoundBoosterVolumes()
	if not SoundBoosterSettings.Enabled then
		return
	end

	for sound, soundData in pairs(SoundBoosterSettings.CachedSounds) do
		if sound and sound.Parent then
			if soundData.Type == "Heartbeat" then
				sound.Volume = soundData.OriginalVolume * SoundBoosterSettings.HeartbeatVolume
			elseif soundData.Type == "Steps" then
				sound.Volume = soundData.OriginalVolume * SoundBoosterSettings.StepsVolume
			elseif soundData.Type == "Jumps" then
				sound.Volume = soundData.OriginalVolume * SoundBoosterSettings.JumpsVolume
			end
		end
	end
end

local function LoadShaderPresets()
	local presets = {
		["morning"] = {
			["yfbghj"] = Color3.fromRGB(138, 138, 138),
			["tgvbyd"] = 6.5,
			["ghuybhuyhj"] = 41.7,
			["khnbfth"] = 2,
			["hgyghkg"] = Color3.fromRGB(0, 0, 0),
			["yfbhjku"] = Color3.fromRGB(0, 0, 0),
			["ygyyfgvhbjytrt"] = 0.25,
			["sdfcddc"] = 0.25,
			["hgnujuu7thgr"] = true,
			["hyhnngtf"] = Color3.fromRGB(138, 138, 138),
			["hdfr7thgr"] = 0.2,
			["fhnchvhfjsd"] = 0.02,
			["ugtbbjhygt"] = 0.1,
			["tfbghuugbnjhg"] = -0.2,
			["fvrtccvghghj"] = Color3.fromRGB(255, 255, 255),
			["jnfdhbnfcvh"] = 0.8,
			["fvtyghj"] = 24,
			["ygbhnj"] = 0.8,
			["njnfg"] = 0,
			["jdfkd"] = 0.1,
			["fvgsdfg"] = 50,
			["sdkvkflv"] = 15,
			["hbjhd"] = 0.75,
			["gyhgtg"] = 0.4,
			["ygbhggv"] = 0.3,
			["jghbjhgyfd"] = Color3.fromRGB(255, 248, 231),
			["shdbsnjfc"] = 0.31,
			["skdjfkdm"] = 0.25,
			["sjdjncdjf"] = Color3.fromRGB(199, 199, 199),
			["efjdjfk"] = Color3.fromRGB(106, 112, 125),
			["sejfd"] = 0.1,
			["jddfjsd"] = 0,
		},
		["midday"] = {
			["yfbghj"] = Color3.fromRGB(138, 138, 138),
			["tgvbyd"] = 14,
			["ghuybhuyhj"] = 41.7,
			["khnbfth"] = 2,
			["hgyghkg"] = Color3.fromRGB(0, 0, 0),
			["yfbhjku"] = Color3.fromRGB(0, 0, 0),
			["ygyyfgvhbjytrt"] = 0.25,
			["sdfcddc"] = 0.25,
			["hgnujuu7thgr"] = true,
			["hyhnngtf"] = Color3.fromRGB(138, 138, 138),
			["hdfr7thgr"] = 0,
			["fhnchvhfjsd"] = 0,
			["ugtbbjhygt"] = 0.1,
			["tfbghuugbnjhg"] = 0,
			["fvrtccvghghj"] = Color3.fromRGB(255, 255, 255),
			["jnfdhbnfcvh"] = 1,
			["fvtyghj"] = 24,
			["ygbhnj"] = 0.95,
			["njnfg"] = 0,
			["jdfkd"] = 0.1,
			["fvgsdfg"] = 50,
			["sdkvkflv"] = 10,
			["hbjhd"] = 0.75,
			["gyhgtg"] = 0.5,
			["ygbhggv"] = 0.4,
			["jghbjhgyfd"] = Color3.fromRGB(255, 255, 255),
			["shdbsnjfc"] = 0.364,
			["skdjfkdm"] = 0.25,
			["sjdjncdjf"] = Color3.fromRGB(199, 199, 199),
			["efjdjfk"] = Color3.fromRGB(106, 112, 125),
			["sejfd"] = 0,
			["jddfjsd"] = 0,
		},
		["afternoon"] = {
			["yfbghj"] = Color3.fromRGB(138, 138, 138),
			["tgvbyd"] = 15.5,
			["ghuybhuyhj"] = 41.7,
			["khnbfth"] = 2,
			["hgyghkg"] = Color3.fromRGB(0, 0, 0),
			["yfbhjku"] = Color3.fromRGB(0, 0, 0),
			["ygyyfgvhbjytrt"] = 0.25,
			["sdfcddc"] = 0.25,
			["hgnujuu7thgr"] = true,
			["hyhnngtf"] = Color3.fromRGB(138, 138, 138),
			["hdfr7thgr"] = 0.1,
			["fhnchvhfjsd"] = 0.01,
			["ugtbbjhygt"] = 0.15,
			["tfbghuugbnjhg"] = -0.1,
			["fvrtccvghghj"] = Color3.fromRGB(255, 252, 245),
			["jnfdhbnfcvh"] = 0.9,
			["fvtyghj"] = 24,
			["ygbhnj"] = 0.85,
			["njnfg"] = 0,
			["jdfkd"] = 0.15,
			["fvgsdfg"] = 50,
			["sdkvkflv"] = 12,
			["hbjhd"] = 0.75,
			["gyhgtg"] = 0.45,
			["ygbhggv"] = 0.35,
			["jghbjhgyfd"] = Color3.fromRGB(255, 248, 231),
			["shdbsnjfc"] = 0.32,
			["skdjfkdm"] = 0.25,
			["sjdjncdjf"] = Color3.fromRGB(199, 199, 199),
			["efjdjfk"] = Color3.fromRGB(106, 112, 125),
			["sejfd"] = 0.05,
			["jddfjsd"] = 0,
		},
		["evening"] = {
			["yfbghj"] = Color3.fromRGB(150, 112, 90),
			["tgvbyd"] = 17.5,
			["ghuybhuyhj"] = 41.7,
			["khnbfth"] = 2,
			["hgyghkg"] = Color3.fromRGB(0, 0, 0),
			["yfbhjku"] = Color3.fromRGB(255, 176, 131),
			["ygyyfgvhbjytrt"] = 0.25,
			["sdfcddc"] = 0.25,
			["hgnujuu7thgr"] = true,
			["hyhnngtf"] = Color3.fromRGB(150, 112, 90),
			["hdfr7thgr"] = 0.25,
			["fhnchvhfjsd"] = 0.05,
			["ugtbbjhygt"] = 0.2,
			["tfbghuugbnjhg"] = -0.3,
			["fvrtccvghghj"] = Color3.fromRGB(255, 231, 207),
			["jnfdhbnfcvh"] = 1.2,
			["fvtyghj"] = 32,
			["ygbhnj"] = 0.7,
			["njnfg"] = 0,
			["jdfkd"] = 0.2,
			["fvgsdfg"] = 50,
			["sdkvkflv"] = 15,
			["hbjhd"] = 0.8,
			["gyhgtg"] = 0.6,
			["ygbhggv"] = 0.4,
			["jghbjhgyfd"] = Color3.fromRGB(255, 207, 165),
			["shdbsnjfc"] = 0.42,
			["skdjfkdm"] = 0.3,
			["sjdjncdjf"] = Color3.fromRGB(225, 180, 150),
			["efjdjfk"] = Color3.fromRGB(255, 176, 131),
			["sejfd"] = 0.3,
			["jddfjsd"] = 0.1,
		},
		["night"] = {
			["yfbghj"] = Color3.fromRGB(85, 85, 127),
			["tgvbyd"] = 0,
			["ghuybhuyhj"] = 41.7,
			["khnbfth"] = 1,
			["hgyghkg"] = Color3.fromRGB(0, 0, 0),
			["yfbhjku"] = Color3.fromRGB(0, 0, 0),
			["ygyyfgvhbjytrt"] = 0.15,
			["sdfcddc"] = 0.15,
			["hgnujuu7thgr"] = true,
			["hyhnngtf"] = Color3.fromRGB(85, 85, 127),
			["hdfr7thgr"] = -0.2,
			["fhnchvhfjsd"] = -0.1,
			["ugtbbjhygt"] = 0.05,
			["tfbghuugbnjhg"] = -0.5,
			["fvrtccvghghj"] = Color3.fromRGB(200, 210, 255),
			["jnfdhbnfcvh"] = 0.4,
			["fvtyghj"] = 24,
			["ygbhnj"] = 1,
			["njnfg"] = 0,
			["jdfkd"] = 0.1,
			["fvgsdfg"] = 50,
			["sdkvkflv"] = 10,
			["hbjhd"] = 0.75,
			["gyhgtg"] = 0.3,
			["ygbhggv"] = 0.2,
			["jghbjhgyfd"] = Color3.fromRGB(170, 180, 210),
			["shdbsnjfc"] = 0.25,
			["skdjfkdm"] = 0.2,
			["sjdjncdjf"] = Color3.fromRGB(140, 150, 180),
			["efjdjfk"] = Color3.fromRGB(85, 85, 127),
			["sejfd"] = 0,
			["jddfjsd"] = 0.2,
		},
		["midnight"] = {
			["yfbghj"] = Color3.fromRGB(60, 60, 90),
			["tgvbyd"] = 0,
			["ghuybhuyhj"] = 41.7,
			["khnbfth"] = 0.5,
			["hgyghkg"] = Color3.fromRGB(0, 0, 0),
			["yfbhjku"] = Color3.fromRGB(0, 0, 0),
			["ygyyfgvhbjytrt"] = 0.1,
			["sdfcddc"] = 0.1,
			["hgnujuu7thgr"] = true,
			["hyhnngtf"] = Color3.fromRGB(60, 60, 90),
			["hdfr7thgr"] = -0.3,
			["fhnchvhfjsd"] = -0.15,
			["ugtbbjhygt"] = 0,
			["tfbghuugbnjhg"] = -0.6,
			["fvrtccvghghj"] = Color3.fromRGB(180, 190, 230),
			["jnfdhbnfcvh"] = 0.3,
			["fvtyghj"] = 24,
			["ygbhnj"] = 1,
			["njnfg"] = 0,
			["jdfkd"] = 0.05,
			["fvgsdfg"] = 50,
			["sdkvkflv"] = 8,
			["hbjhd"] = 0.7,
			["gyhgtg"] = 0.2,
			["ygbhggv"] = 0.15,
			["jghbjhgyfd"] = Color3.fromRGB(150, 160, 190),
			["shdbsnjfc"] = 0.2,
			["skdjfkdm"] = 0.15,
			["sjdjncdjf"] = Color3.fromRGB(120, 130, 160),
			["efjdjfk"] = Color3.fromRGB(60, 60, 90),
			["sejfd"] = 0,
			["jddfjsd"] = 0.3,
		},
	}

	return presets
end

shaderConnection = nil

local function ApplyShaderLighting()
	if not ShaderSettings.Enabled or not shaderlight then
		if shaderConnection then
			shaderConnection:Disconnect()
			shaderConnection = nil
		end

		Lighting.Ambient = backupLighting.Ambient
		Lighting.ClockTime = backupLighting.ClockTime
		Lighting.GeographicLatitude = backupLighting.GeographicLatitude
		Lighting.Brightness = backupLighting.Brightness
		Lighting.ColorShift_Bottom = backupLighting.ColorShift_Bottom
		Lighting.ColorShift_Top = backupLighting.ColorShift_Top
		Lighting.EnvironmentDiffuseScale = backupLighting.EnvironmentDiffuseScale
		Lighting.EnvironmentSpecularScale = backupLighting.EnvironmentSpecularScale
		Lighting.GlobalShadows = backupLighting.GlobalShadows
		Lighting.OutdoorAmbient = backupLighting.OutdoorAmbient
		Lighting.ExposureCompensation = backupLighting.ExposureCompensation
		Lighting.FogEnd = backupLighting.FogEnd
		Lighting.FogColor = backupLighting.FogColor
		Lighting.FogStart = backupLighting.FogStart

		if colorcor then
			colorcor.Enabled = false
		end
		if bloom then
			bloom.Enabled = false
		end
		if blur then
			blur.Enabled = false
		end
		if depth then
			depth.Enabled = false
		end
		if sray then
			sray.Enabled = false
		end

		return
	end

	if not shaderConnection then
		shaderConnection = RunService.Heartbeat:Connect(function()
			if not ShaderSettings.Enabled then
				return
			end

			Lighting.Ambient = shaderlight["yfbghj"]
			Lighting.ClockTime = shaderlight["tgvbyd"]
			Lighting.GeographicLatitude = shaderlight["ghuybhuyhj"]
			Lighting.Brightness = shaderlight["khnbfth"]
			Lighting.ColorShift_Bottom = shaderlight["hgyghkg"]
			Lighting.ColorShift_Top = shaderlight["yfbhjku"]
			Lighting.EnvironmentDiffuseScale = shaderlight["ygyyfgvhbjytrt"]
			Lighting.EnvironmentSpecularScale = shaderlight["sdfcddc"]
			Lighting.GlobalShadows = shaderlight["hgnujuu7thgr"]
			Lighting.OutdoorAmbient = shaderlight["hyhnngtf"]
			Lighting.ExposureCompensation = shaderlight["hdfr7thgr"]
			Lighting.FogEnd = math.huge
			Lighting.FogColor = Color3.fromRGB(255, 255, 255)
			Lighting.FogStart = math.huge

			local colorcor = Lighting:findFirstChild("ColorCorrectionEffect")
			local bloom = Lighting:findFirstChild("BloomEffect")
			local blur = Lighting:findFirstChild("BlurEffect")
			local depth = Lighting:findFirstChild("DepthOfFieldEffect")
			local sray = Lighting:findFirstChild("ScreenSpaceRayleighScatteringEffect")
			local cloud = Lighting:findFirstChild("Clouds")
			local atmosphere = Lighting:findFirstChild("Atmosphere")

			if colorcor then
				colorcor.Brightness = shaderlight["fhnchvhfjsd"]
				colorcor.Contrast = shaderlight["ugtbbjhygt"]
				colorcor.Saturation = shaderlight["tfbghuugbnjhg"]
				colorcor.TintColor = shaderlight["fvrtccvghghj"]
				colorcor.Enabled = shaderWL["cor"]
			end

			if bloom then
				bloom.Intensity = shaderlight["jnfdhbnfcvh"]
				bloom.Size = shaderlight["fvtyghj"]
				bloom.Threshold = shaderlight["ygbhnj"]
				bloom.Enabled = shaderWL["bl"]
			end

			if blur then
				blur.Size = shaderlight["njnfg"]
				blur.Enabled = shaderWL["blr"]
			end

			if depth then
				depth.FarIntensity = shaderlight["jdfkd"]
				depth.FocusDistance = shaderlight["fvgsdfg"]
				depth.InFocusRadius = shaderlight["sdkvkflv"]
				depth.NearIntensity = shaderlight["hbjhd"]
				depth.Enabled = shaderWL["dof"]
			end

			if cloud then
				cloud.Cover = shaderlight["gyhgtg"]
				cloud.Density = shaderlight["ygbhggv"]
				cloud.Color = shaderlight["jghbjhgyfd"]
			end

			if atmosphere then
				atmosphere.Density = shaderlight["shdbsnjfc"]
				atmosphere.Offset = shaderlight["skdjfkdm"]
				atmosphere.Color = shaderlight["sjdjncdjf"]
				atmosphere.Decay = shaderlight["efjdjfk"]
				atmosphere.Glare = shaderlight["sejfd"]
				atmosphere.Haze = shaderlight["jddfjsd"]
			end

			if sray then
				sray.Enabled = shaderWL["sray"]
			end
		end)
	end
end

local function StartResolutionScale()
	if ResolutionSettings.Connection then
		ResolutionSettings.Connection:Disconnect()
	end

	ResolutionSettings.Connection = RunService.RenderStepped:Connect(function()
		if not ResolutionSettings.Enabled then
			return
		end

		local cam = workspace.CurrentCamera
		if cam then
			cam.CFrame = cam.CFrame * CFrame.new(0, 0, 0, 1, 0, 0, 0, ResolutionSettings.ResolutionScale, 0, 0, 0, 1)
		end
	end)
end

local function StopResolutionScale()
	if ResolutionSettings.Connection then
		ResolutionSettings.Connection:Disconnect()
		ResolutionSettings.Connection = nil
	end
	ResolutionSettings.ResolutionScale = 1
end

function isTextObject(obj)
	return obj:IsA("StringValue") or obj:IsA("TextLabel") or obj:IsA("TextButton") or obj:IsA("TextBox")
end

function HasFontObject(obj)
	return obj:IsA("TextLabel") or obj:IsA("TextButton") or obj:IsA("TextBox")
end

function escapePattern(s)
	return (tostring(s):gsub("([^%w])", "%%%1"))
end

NameHiderSettings = {
	Enabled = false,
	MyName = player.Name,
	MyLevel = nil,
	MyIcon = nil,
	MyTag = nil,
	MyTagColor = nil,
	CustomPlayers = {},
	TextObjectCache = {},
	DirtyObjects = {},
	Connections = {},
	LastFrameUpdate = 0,
	UpdateInterval = 0.016,
	PlayerFrameCache = {},
}

function getPlayerData(plrName)
	if plrName == player.Name and NameHiderSettings.MyName then
		return NameHiderSettings.MyName,
			NameHiderSettings.MyLevel,
			NameHiderSettings.MyIcon,
			NameHiderSettings.MyTag,
			NameHiderSettings.MyTagColor
	end
	local d = NameHiderSettings.CustomPlayers[plrName]
	if d then
		return d.Name, d.Level, d.Icon, d.Tag, d.TagColor
	end
end

function hasPlayerName(text, playerName)
	if not text or text == "" then
		return false
	end
	local ok, _ = pcall(function()
		return string.find(text, playerName, 1, true) ~= nil
	end)
	return ok and string.find(text, playerName, 1, true) ~= nil
end

local function replaceInObject(obj)
	if not NameHiderSettings.Enabled then
		return
	end
	if not isTextObject(obj) then
		return
	end

	local function getText()
		if obj:IsA("StringValue") then
			return obj.Value
		end
		return obj.Text
	end

	local function setText(v)
		if obj:IsA("StringValue") then
			obj.Value = v
		else
			obj.Text = v
		end
	end

	local text = getText()
	if not text or text == "" then
		return
	end

	local changed = false
	for _, plr in ipairs(Players:GetPlayers()) do
		local newName = select(1, getPlayerData(plr.Name))
		if not newName then
			continue
		end
		if hasPlayerName(text, plr.Name) then
			local pattern = escapePattern(plr.Name)
			local ok, replaced = pcall(function()
				return (text:gsub(pattern, newName))
			end)
			if ok and replaced then
				text = replaced
				changed = true
			end
		end
	end

	if changed then
		setText(text)
	end
end

local function updatePlayerFrame(plr)
	if not NameHiderSettings.Enabled then
		return
	end

	local cached = NameHiderSettings.PlayerFrameCache[plr]
	if not cached then
		return
	end

	local newName, newLevel, newIcon, tag, tagColor = getPlayerData(plr.Name)
	if not newName then
		return
	end

	if cached.LastName == newName and cached.LastLevel == newLevel and cached.LastIcon == newIcon then
		return
	end

	local gui = playergui:FindFirstChildWhichIsA("ScreenGui", true) or playergui:FindFirstChild("ScreenGui")
	local namesFrame = gui and gui:FindFirstChild("PlayerNamesFrame")
	if not namesFrame then
		for _, g in ipairs(playergui:GetChildren()) do
			if g:IsA("ScreenGui") then
				namesFrame = g:FindFirstChild("PlayerNamesFrame") or namesFrame
			end
		end
	end
	if not namesFrame then
		return
	end
	local frame = namesFrame:FindFirstChild(plr.Name .. "PlayerFrame")
	if not frame then
		return
	end
	local nameLabel = frame:FindFirstChild("NameLabel")
	local levelLabel = frame:FindFirstChild("LevelLabel")
	local iconLabel = frame:FindFirstChild("IconLabel")
	if nameLabel then
		nameLabel.Text = newName
	end
	if levelLabel then
		if newLevel then
			levelLabel.Text = tostring(newLevel)
			frame.LayoutOrder = -newLevel
		else
			levelLabel.Text = ""
		end
	end
	if iconLabel then
		if newIcon then
			iconLabel.Image = newIcon
		elseif tag and RankData[tag] then
			iconLabel.Image = RankData[tag].Icon
		end
	end

	cached.LastName = newName
	cached.LastLevel = newLevel
	cached.LastIcon = newIcon
end

local function markDirty(obj)
	NameHiderSettings.DirtyObjects[obj] = true
end

local function addToCache(obj)
	if not isTextObject(obj) then
		return
	end
	if NameHiderSettings.TextObjectCache[obj] then
		return
	end
	local should = false
	local text = obj:IsA("StringValue") and obj.Value or obj.Text
	if text == "" then
		should = true
	end
	for _, plr in ipairs(Players:GetPlayers()) do
		if hasPlayerName(text, plr.Name) then
			should = true
			break
		end
	end
	if should then
		NameHiderSettings.TextObjectCache[obj] = true

		local conn = obj:GetPropertyChangedSignal(obj:IsA("StringValue") and "Value" or "Text"):Connect(function()
			markDirty(obj)
		end)
		table.insert(NameHiderSettings.Connections, conn)

		replaceInObject(obj)
	end
end

local function removeFromCache(obj)
	NameHiderSettings.TextObjectCache[obj] = nil
	NameHiderSettings.DirtyObjects[obj] = nil
end

local function scanContainer(container)
	pcall(function()
		for _, obj in ipairs(container:GetDescendants()) do
			addToCache(obj)
		end
	end)
end

local function connectDescendantSignals(container)
	pcall(function()
		table.insert(
			NameHiderSettings.Connections,
			container.DescendantAdded:Connect(function(obj)
				task.defer(addToCache, obj)
			end)
		)
		table.insert(NameHiderSettings.Connections, container.DescendantRemoving:Connect(removeFromCache))
	end)
end

local function hookChatFiltering()
	local chatEvents = ReplicatedStorage:FindFirstChild("DefaultChatSystemChatEvents")
		or ReplicatedStorage:FindFirstChild("Chat")
		or ReplicatedStorage
	local msgEvent = chatEvents and chatEvents:FindFirstChild("OnMessageDoneFiltering")
	if msgEvent and msgEvent:IsA("RemoteEvent") then
		msgEvent.OnClientEvent:Connect(function(data)
			if not NameHiderSettings.Enabled then
				return
			end
			if type(data) ~= "table" then
				return
			end
			local speaker = data.FromSpeaker or data.Speaker or data.SpeakerName or data.Username
			local message = data.Message or data.Text
			if not speaker or not message then
				return
			end
			local plr = Players:FindFirstChild(speaker)
			if not plr then
				return
			end
			local newName, _, _, tag, tagColor = getPlayerData(plr.Name)
			if not newName then
				local formatted = formatChatMessage and formatChatMessage(message, plr) or message
				if formatted and formatted ~= message then
					data.Message = formatted
				end
				return
			end
			local formatted = message
			if tag and tagColor then
				local c = tagColor:gsub("#", "")
				formatted = string.format("<font color='#%s'>[%s]</font> %s", c, tag, formatted)
			end
			data.Message = formatted
		end)
	end
end

function StartNameHider()
	if NameHiderSettings.Enabled then
		return
	end
	NameHiderSettings.Enabled = true

	for _, plr in ipairs(Players:GetPlayers()) do
		NameHiderSettings.PlayerFrameCache[plr] = {
			LastName = nil,
			LastLevel = nil,
			LastIcon = nil,
		}
	end

	scanContainer(workspace)
	scanContainer(CoreGui)
	scanContainer(playergui)
	connectDescendantSignals(workspace)
	connectDescendantSignals(CoreGui)
	connectDescendantSignals(playergui)
	hookChatFiltering()

	table.insert(
		NameHiderSettings.Connections,
		RunService.Heartbeat:Connect(function()
			local now = tick()
			if now - NameHiderSettings.LastFrameUpdate < NameHiderSettings.UpdateInterval then
				return
			end
			NameHiderSettings.LastFrameUpdate = now

			for obj in pairs(NameHiderSettings.DirtyObjects) do
				if not obj or not obj.Parent then
					removeFromCache(obj)
				else
					replaceInObject(obj)
				end
				NameHiderSettings.DirtyObjects[obj] = nil
			end

			for _, plr in ipairs(Players:GetPlayers()) do
				pcall(updatePlayerFrame, plr)
			end
		end)
	)
	for _, plr in ipairs(Players:GetPlayers()) do
		pcall(updatePlayerFrame, plr)
	end
end

function StopNameHider()
	NameHiderSettings.Enabled = false
	for _, c in ipairs(NameHiderSettings.Connections) do
		pcall(function()
			c:Disconnect()
		end)
	end
	NameHiderSettings.Connections = {}
	NameHiderSettings.TextObjectCache = {}
	NameHiderSettings.DirtyObjects = {}
	NameHiderSettings.PlayerFrameCache = {}
end

task.spawn(function()
	while true do
		for _, plr in ipairs(Players:GetPlayers()) do
			pcall(updatePlayerFrame, plr)
		end
		task.wait(0.1)
	end
end)
ConnectionManager = {
	PlayerConnections = {},
	GlobalConnections = {},
	PerPlayerConnections = {},
}

function ConnectionManager:AddGlobal(name, connection)
	if self.GlobalConnections[name] then
		self.GlobalConnections[name]:Disconnect()
	end
	self.GlobalConnections[name] = connection
end

function ConnectionManager:AddPerPlayer(zag, name, connection)
	if not self.PerPlayerConnections[zag] then
		self.PerPlayerConnections[zag] = {}
	end
	if self.PerPlayerConnections[zag][name] then
		self.PerPlayerConnections[zag][name]:Disconnect()
	end
	self.PerPlayerConnections[zag][name] = connection
end

function ConnectionManager:RemovePlayer(zag)
	if self.PerPlayerConnections[zag] then
		for _, conn in pairs(self.PerPlayerConnections[zag]) do
			conn:Disconnect()
		end
		self.PerPlayerConnections[zag] = nil
	end
end

function ConnectionManager:DisconnectAll()
	for _, conn in pairs(self.GlobalConnections) do
		if conn then
			conn:Disconnect()
		end
	end
	for _, playerConns in pairs(self.PerPlayerConnections) do
		for _, conn in pairs(playerConns) do
			if conn then
				conn:Disconnect()
			end
		end
	end
	self.GlobalConnections = {}
	self.PerPlayerConnections = {}
end

local function getmap()
	return map.Value
end
local function canPerformAction()
	local now = tick()
	if now - AutoFarmSettings.LastActionTime < AutoFarmSettings.ActionCooldown then
		return false
	end
	AutoFarmSettings.LastActionTime = now
	return true
end

local function canTeleport()
	local now = tick()
	if now - AutoFarmSettings.LastTeleportTime < AutoFarmSettings.TeleportCooldown then
		return false
	end
	AutoFarmSettings.LastTeleportTime = now
	return true
end

local function GetBeast()
	for _, v in Players:GetPlayers() do
		local char = v.Character or v.CharacterAdded:Wait()
		if char:FindFirstChild("BeastPowers") then
			return char
		end
	end
end

local function getRandomPositionOnPart(part)
	if not part then
		return nil
	end
	local size = part.Size
	local randomOffset = Vector3.new(
		math.random(-size.X / 2, size.X / 2) * 0.8,
		math.random(-size.Y / 2, size.Y / 2) * 0.8,
		math.random(-size.Z / 2, size.Z / 2) * 0.8
	)
	return part.Position + randomOffset
end

local function GetPartToRope()
	local partToRope = RopeHelperSettings.SelectedPart
	if RopeHelperSettings.RandomizePart then
		local parts = { "Head", "Torso", "Left Arm", "Right Arm", "Left Leg", "Right Leg" }
		partToRope = parts[math.random(1, #parts)]
	end
	return partToRope
end

local function AutoRopePlayer(TargetPlayer)
	local now = tick()
	if
		RopeHelperSettings.RopeDebounce[TargetPlayer]
		and now - RopeHelperSettings.RopeDebounce[TargetPlayer] < RopeHelperSettings.DebounceTime
	then
		return
	end

	local beast = GetBeast()
	if not beast then
		warn("No beast found")
		return
	end

	local Hammer = beast:FindFirstChild("Hammer")
	if not Hammer then
		warn("Beast doesn't have hammer")
		return
	end

	local HammerEvent = Hammer:FindFirstChild("HammerEvent")
	local TargetChar = TargetPlayer.Character
	if not TargetChar then
		warn("No character to rope")
		return
	end

	local partName = GetPartToRope()
	local targetPart = TargetChar:FindFirstChild(partName)
	if not targetPart then
		targetPart = TargetChar:FindFirstChild("Torso")
	end

	if not targetPart then
		warn("No valid part to rope")
		return
	end

	local tempStats = TargetPlayer:FindFirstChild("TempPlayerStatsModule")
	if not tempStats then
		return
	end

	local ragdoll = tempStats:FindFirstChild("Ragdoll")
	if not ragdoll or not ragdoll.Value then
		return
	end

	local args = {
		"HammerTieUp",
		targetPart,
		TargetChar:FindFirstChild("HumanoidRootPart").Position,
	}

	RopeHelperSettings.RopeDebounce[TargetPlayer] = now
	HammerEvent:FireServer(unpack(args))
end

local function canHitPlayer(plr)
	local now = tick()
	local lastHit = KillAuraSettings.LastHitTimes[plr] or 0
	if now - lastHit < KillAuraSettings.HitCooldown then
		return false
	end
	KillAuraSettings.LastHitTimes[plr] = now
	return true
end

local function getObjectPosition(object)
	if object:IsA("Model") then
		if object.PrimaryPart then
			return object.PrimaryPart.Position
		end
		local cf = object:GetPivot()
		if cf then
			return cf.Position
		end
		for _, child in pairs(object:GetDescendants()) do
			if child:IsA("BasePart") then
				return child.Position
			end
		end
	elseif object:IsA("BasePart") then
		return object.Position
	else
		for _, child in pairs(object:GetDescendants()) do
			if child:IsA("BasePart") then
				return child.Position
			end
		end
	end
	return Vector3.new(0, 0, 0)
end

local function findNearestObject(playerPosition, objectList)
	local nearestObject = nil
	local shortestDistance = math.huge
	for _, object in pairs(objectList) do
		if object.Parent then
			local objectPosition = getObjectPosition(object)
			local distance = (playerPosition - objectPosition).Magnitude
			if distance < shortestDistance then
				shortestDistance = distance
				nearestObject = object
			end
		end
	end
	return nearestObject, shortestDistance
end

local function getDistance(part1, part2)
	return (part1.Position - part2.Position).Magnitude
end

local function getIsTreeBush(Size)
	local x = Size.X
	local y = Size.Y
	local z = Size.Z

	if x >= 6 and x <= 14 then
		if y >= 7 and x <= 14 then
			if z >= 7 and z <= 14 then
				return true
			end
		end
	end

	return false
end

local function IsCaptured(plr)
	return plr:FindFirstChild("TempPlayerStatsModule"):FindFirstChild("Captured")
end

local function IsHit(Player)
	local tempStats = Player:WaitForChild("TempPlayerStatsModule")
	local ragdoll = tempStats:WaitForChild("Ragdoll")
	return ragdoll.Value
end

local function GetRopedPlayer()
	local beast = GetBeast()
	if not beast then
		return nil
	end

	local ropePart = beast:FindFirstChild("Part")
	if not ropePart then
		return nil
	end

	local ropeConstraint = ropePart:FindFirstChildOfClass("RopeConstraint")
	if not ropeConstraint then
		return nil
	end

	local attachment0 = ropeConstraint.Attachment0
	local attachment1 = ropeConstraint.Attachment1

	if not attachment0 or not attachment1 then
		return nil
	end

	local targetAttachment = attachment0.Parent ~= ropePart and attachment0 or attachment1
	if not targetAttachment then
		return nil
	end

	local targetPart = targetAttachment.Parent
	if not targetPart or not targetPart.Parent then
		return nil
	end

	local character = targetPart.Parent
	local plz = Players:GetPlayerFromCharacter(character)

	return plz, targetPart
end

local function HitPlayer(TargetPlayer)
	local beast = GetBeast()
	if not beast then
		return
	end
	local Hammer = beast:FindFirstChild("Hammer")
	if not Hammer then
		return
	end
	local HammerEvent = Hammer:FindFirstChild("HammerEvent")
	local HRP = TargetPlayer.Character and TargetPlayer.Character:FindFirstChild("HumanoidRootPart")
	if not HRP then
		return
	end
	HammerEvent:FireServer("HammerHit", HRP, HRP.Position)
end
local function StartKillAura()
	if KillAuraSettings.Connection then
		KillAuraSettings.Connection:Disconnect()
	end

	KillAuraSettings.Connection = RunService.Heartbeat:Connect(function()
		if not KillAuraSettings.Enabled then
			return
		end

		local myChar = player.Character
		if not myChar or not myChar:FindFirstChild("HumanoidRootPart") or not myChar:FindFirstChild("BeastPowers") then
			return
		end

		local myHrp = myChar.HumanoidRootPart

		for _, plr in pairs(Players:GetPlayers()) do
			if plr.Character then
				local targetHrp = plr.Character:FindFirstChild("HumanoidRootPart")
				if targetHrp and canHitPlayer(plr) then
					local distance = (myHrp.Position - targetHrp.Position).Magnitude
					if distance <= KillAuraSettings.MaxDistance then
						HitPlayer(plr)
					end
				end
			end
		end
	end)
end

local function Create3DBoxLines()
	local lines = {}
	for i = 1, 12 do
		local line = Drawing.new("Line")
		line.Visible = false
		line.Thickness = Settings.EspSettings.PlayerEsp.BoxEsp.Thickness
		line.Transparency = Settings.EspSettings.PlayerEsp.BoxEsp.Transparency
		lines[i] = line
	end
	return lines
end

local function Get3DBoxCorners(Character)
	local hrp = Character:FindFirstChild("HumanoidRootPart")
	if not hrp then
		return nil
	end

	local size = Character:GetExtentsSize()
	local cf = hrp.CFrame

	local corners = {
		cf * CFrame.new(-size.X / 2, -size.Y / 2, -size.Z / 2),
		cf * CFrame.new(size.X / 2, -size.Y / 2, -size.Z / 2),
		cf * CFrame.new(size.X / 2, size.Y / 2, -size.Z / 2),
		cf * CFrame.new(-size.X / 2, size.Y / 2, -size.Z / 2),
		cf * CFrame.new(-size.X / 2, -size.Y / 2, size.Z / 2),
		cf * CFrame.new(size.X / 2, -size.Y / 2, size.Z / 2),
		cf * CFrame.new(size.X / 2, size.Y / 2, size.Z / 2),
		cf * CFrame.new(-size.X / 2, size.Y / 2, size.Z / 2),
	}

	return corners
end

local function ProjectCornersToScreen(corners)
	local screenCorners = {}
	local cam = workspace.CurrentCamera

	if not cam then
		return nil
	end

	for i, corner in ipairs(corners) do
		local screenPos, onScreen = cam:WorldToViewportPoint(corner.Position)

		if not onScreen or screenPos.Z < 0 then
			return nil
		end

		screenCorners[i] = Vector2.new(screenPos.X, screenPos.Y)
	end

	return screenCorners
end

local function Get3DBoxColor(Character)
	local IsBeast = Character:FindFirstChild("BeastPowers")
	if IsBeast then
		return Settings.EspSettings.PlayerEsp.d3esp.BeastFillColor
	else
		return Settings.EspSettings.PlayerEsp.d3esp.SurvivorFillColor
	end
end

local function Update3DBox(lines, Character)
	if not lines or not Character then
		return
	end

	local cam = workspace.CurrentCamera
	if not cam then
		for _, line in ipairs(lines) do
			line.Visible = false
		end
		return
	end

	local corners = Get3DBoxCorners(Character)
	if not corners then
		for _, line in ipairs(lines) do
			line.Visible = false
		end
		return
	end

	local screenCorners = ProjectCornersToScreen(corners)
	if not screenCorners then
		for _, line in ipairs(lines) do
			line.Visible = false
		end
		return
	end

	local color = Get3DBoxColor(Character)

	lines[1].From = screenCorners[1]
	lines[1].To = screenCorners[2]

	lines[2].From = screenCorners[2]
	lines[2].To = screenCorners[3]

	lines[3].From = screenCorners[3]
	lines[3].To = screenCorners[4]

	lines[4].From = screenCorners[4]
	lines[4].To = screenCorners[1]

	lines[5].From = screenCorners[5]
	lines[5].To = screenCorners[6]

	lines[6].From = screenCorners[6]
	lines[6].To = screenCorners[7]

	lines[7].From = screenCorners[7]
	lines[7].To = screenCorners[8]

	lines[8].From = screenCorners[8]
	lines[8].To = screenCorners[5]

	lines[9].From = screenCorners[1]
	lines[9].To = screenCorners[5]

	lines[10].From = screenCorners[2]
	lines[10].To = screenCorners[6]

	lines[11].From = screenCorners[3]
	lines[11].To = screenCorners[7]

	lines[12].From = screenCorners[4]
	lines[12].To = screenCorners[8]

	for _, line in ipairs(lines) do
		line.Color = color
		line.Thickness = Settings.EspSettings.PlayerEsp.BoxEsp.Thickness
		line.Transparency = Settings.EspSettings.PlayerEsp.BoxEsp.Transparency
		line.Visible = true
	end
end
local function Add3DBoxEsp(Character)
	if ThreeDESPObjects[Character] then
		Remove3DBoxEsp(Character)
	end

	local lines = Create3DBoxLines()
	ThreeDESPObjects[Character] = lines
end

local function Remove3DBoxEsp(Character)
	local lines = ThreeDESPObjects[Character]
	if lines then
		for _, line in ipairs(lines) do
			line:Remove()
		end
		ThreeDESPObjects[Character] = nil
	end
end

local function UpdateAll3DBoxEsp()
	local cam = workspace.CurrentCamera
	if not cam then
		return
	end

	for Character, lines in pairs(ThreeDESPObjects) do
		if Character and Character.Parent then
			Update3DBox(lines, Character)
		else
			Remove3DBoxEsp(Character)
		end
	end
end
local function ApplyHighlightColors(Highlight, Character)
	local IsBeast = Character:FindFirstChild("BeastPowers")
	if IsBeast then
		Highlight.FillColor = Settings.EspSettings.PlayerEsp.BeastFillColor
		Highlight.OutlineColor = Settings.EspSettings.PlayerEsp.BeastOutlineColor
		Highlight.FillTransparency = Settings.EspSettings.PlayerEsp.BeastFillTransparancy
		Highlight.OutlineTransparency = Settings.EspSettings.PlayerEsp.BeastOutlineTransparancy
	else
		Highlight.FillColor = Settings.EspSettings.PlayerEsp.SurvivorFillColor
		Highlight.OutlineColor = Settings.EspSettings.PlayerEsp.SurvivorOutlineColor
		Highlight.FillTransparency = Settings.EspSettings.PlayerEsp.SurvivorFillTransparancy
		Highlight.OutlineTransparency = Settings.EspSettings.PlayerEsp.SurvivorOutlineTransparancy
	end
end

local function AddNormalEsp(Character)
	local highlight = Character:FindFirstChild("esp") or Instance.new("Highlight")
	highlight.Name = "esp"
	highlight.Parent = Character
	highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
	ApplyHighlightColors(highlight, Character)
end

local function AddCloneEsp(Character)
	local existingEsp = Character:FindFirstChild("esp")
	if existingEsp then
		existingEsp:Destroy()
	end

	local espModel = Instance.new("Model")
	espModel.Name = "esp"
	espModel.Parent = Character

	for _, part in pairs(Character:GetDescendants()) do
		if part:IsA("BasePart") and not part:IsDescendantOf(espModel) and part.Name ~= "HumanoidRootPart" then
			local clone = part:Clone()

			for _, child in pairs(clone:GetDescendants()) do
				if not (child:IsA("SpecialMesh") or child:IsA("Mesh") or child:IsA("CharacterMesh")) then
					child:Destroy()
				end
			end

			clone.Transparency = 0
			clone.Anchored = false
			clone.CanCollide = false
			clone.Massless = true
			clone.CastShadow = false
			clone.Parent = espModel

			part.LocalTransparencyModifier = 1

			local weld = Instance.new("Motor6D")
			weld.Part0 = part
			weld.Part1 = clone
			weld.C0 = CFrame.new()
			weld.C1 = CFrame.new()
			weld.Name = part.Name .. "_EspMotor"
			weld.Parent = part
		end
	end

	local highlight = Instance.new("Highlight")
	highlight.Name = "Highlight"
	highlight.Parent = espModel
	highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
	highlight.Adornee = espModel
	ApplyHighlightColors(highlight, Character)
end

local function AddPlayerEsp(Character)
	if Settings.EspSettings.PlayerEsp.d3esp.Enabled then
		Add3DBoxEsp(Character)
		return
	end

	if Settings.EspSettings.PlayerEsp.UseSkeletonEsp or Settings.EspSettings.PlayerEsp.UseBoxEsp then
		return
	end
	if Settings.EspSettings.PlayerEsp.UseCloneEsp then
		AddCloneEsp(Character)
	else
		AddNormalEsp(Character)
	end
end

local function RemovePlayerEsp(Character)
	Remove3DBoxEsp(Character)

	local esp = Character:FindFirstChild("esp")
	if esp then
		esp:Destroy()
	end
	for _, part in pairs(Character:GetDescendants()) do
		if part:IsA("BasePart") then
			part.LocalTransparencyModifier = 0
		end
	end
end

local function UpdatePlayerEsp()
	if Settings.EspSettings.PlayerEsp.d3esp.Enabled then
		UpdateAll3DBoxEsp()
		return
	end

	if Settings.EspSettings.PlayerEsp.UseSkeletonEsp or Settings.EspSettings.PlayerEsp.UseBoxEsp then
		return
	end
	for _, plr in pairs(Players:GetPlayers()) do
		if plr.Character then
			local highlight = plr.Character:FindFirstChildWhichIsA("Highlight", true)
			if highlight then
				ApplyHighlightColors(highlight, plr.Character)
			end
		end
	end
end

local function ReloadPlayerEsp()
	for _, plr in pairs(Players:GetPlayers()) do
		if plr.Character and plr ~= player then
			RemovePlayerEsp(plr.Character)
			if Settings.EspSettings.PlayerEsp.Enabled then
				if Settings.EspSettings.PlayerEsp.d3esp.Enabled then
					Add3DBoxEsp(plr.Character)
				elseif
					not Settings.EspSettings.PlayerEsp.UseSkeletonEsp and not Settings.EspSettings.PlayerEsp.UseBoxEsp
				then
					AddPlayerEsp(plr.Character)
				end
			end
		end
	end
end

RunService.RenderStepped:Connect(function()
	if Settings.EspSettings.PlayerEsp.Enabled and Settings.EspSettings.PlayerEsp.d3esp.Enabled then
		UpdateAll3DBoxEsp()
	end
end)

function UpdateRainbowEsp()
	if not RainbowEspState.Enabled or not Settings.EspSettings.PlayerEsp.Enabled then
		return
	end

	RainbowEspState.Hue = (RainbowEspState.Hue + RainbowEspState.Speed) % 360
	local rainbowColor = Color3.fromHSV(RainbowEspState.Hue / 360, 1, 1)

	Settings.EspSettings.PlayerEsp.SurvivorFillColor = rainbowColor
	Settings.EspSettings.PlayerEsp.BeastFillColor = rainbowColor
	Settings.EspSettings.PlayerEsp.d3esp.SurvivorFillColor = rainbowColor
	Settings.EspSettings.PlayerEsp.d3esp.BeastFillColor = rainbowColor

	UpdatePlayerEsp()
end

function StartRainbowEsp()
	if RainbowEspState.Connection then
		RainbowEspState.Connection:Disconnect()
	end

	RainbowEspState.Connection = RunService.Heartbeat:Connect(function()
		UpdateRainbowEsp()
	end)
end

function StopRainbowEsp()
	if RainbowEspState.Connection then
		RainbowEspState.Connection:Disconnect()
		RainbowEspState.Connection = nil
	end
end

local function StopPcEsp()
	for pc, conn in pairs(PlayerConnections.PcEsp) do
		if conn then
			conn:Disconnect()
		end
		local highlight = pc:FindFirstChildWhichIsA("Highlight")
		if highlight then
			highlight:Destroy()
		end
	end
	PlayerConnections.PcEsp = {}
end

local function StartPcEsp()
	StopPcEsp()
	local themap = map.Value
	if not themap then
		return
	end
	for _, v in pairs(themap:GetChildren()) do
		if v.Name == "ComputerTable" then
			local screen = v:FindFirstChild("Screen")
			if screen then
				local highlight = Instance.new("Highlight")
				highlight.OutlineColor = Settings.EspSettings.PcEsp.OutlineColor
				highlight.OutlineTransparency = Settings.EspSettings.PcEsp.OutlineTransparency
				highlight.FillTransparency = Settings.EspSettings.PcEsp.FillTransparency
				highlight.FillColor = screen.BrickColor.Color
				highlight.Parent = v
				PlayerConnections.PcEsp[v] = screen:GetPropertyChangedSignal("BrickColor"):Connect(function()
					highlight.FillColor = screen.BrickColor.Color
				end)
			end
		end
	end
end

local function StopTubeEsp()
	for tube, highlight in pairs(PlayerConnections.TubeEsp) do
		if highlight and highlight.Parent then
			highlight:Destroy()
		end
	end
	PlayerConnections.TubeEsp = {}
end

local function StartTubeEsp()
	StopTubeEsp()
	local themap = map.Value
	if not themap then
		return
	end
	for _, v in pairs(themap:GetChildren()) do
		if v.Name == "FreezePod" then
			local highlight = Instance.new("Highlight")
			highlight.OutlineColor = Settings.EspSettings.TubeEsp.OutlineColor
			highlight.OutlineTransparency = Settings.EspSettings.TubeEsp.OutlineTransparency
			highlight.FillTransparency = Settings.EspSettings.TubeEsp.FillTransparency
			highlight.FillColor = Settings.EspSettings.TubeEsp.FillColor
			highlight.Parent = v
			PlayerConnections.TubeEsp[v] = highlight
		end
	end
end

local function UpdateDoorEspColors()
	local doorsManager = workspace:FindFirstChild("DoorsManager")
	if not doorsManager then
		return
	end

	local openModel = doorsManager:FindFirstChild("Open")
	local closedModel = doorsManager:FindFirstChild("Closed")

	if openModel then
		local openHighlight = openModel:FindFirstChildWhichIsA("Highlight")
		if openHighlight then
			openHighlight.FillColor = Settings.EspSettings.DoorEsp.OpenColor
			openHighlight.OutlineColor = Settings.EspSettings.DoorEsp.OpenOutlineColor
			openHighlight.OutlineTransparency = Settings.EspSettings.DoorEsp.OutlineTransparency
			openHighlight.FillTransparency = Settings.EspSettings.DoorEsp.OpenFillTransparency
		end
	end

	if closedModel then
		local closedHighlight = closedModel:FindFirstChildWhichIsA("Highlight")
		if closedHighlight then
			closedHighlight.FillColor = Settings.EspSettings.DoorEsp.ClosedColor
			closedHighlight.OutlineColor = Settings.EspSettings.DoorEsp.ClosedOutlineColor
			closedHighlight.OutlineTransparency = Settings.EspSettings.DoorEsp.OutlineTransparency
			closedHighlight.FillTransparency = Settings.EspSettings.DoorEsp.ClosedFillTransparency
		end
	end
end

local function StopDoorEsp()
	local originalMap = getmap()

	for doorModel, conn in pairs(PlayerConnections.DoorEsp) do
		if conn then
			conn:Disconnect()
		end
	end

	local doorsManager = workspace:FindFirstChild("DoorsManager")
	if doorsManager and originalMap then
		local openModel = doorsManager:FindFirstChild("Open")
		local closedModel = doorsManager:FindFirstChild("Closed")

		if openModel then
			for _, door in pairs(openModel:GetChildren()) do
				if door:IsA("Model") then
					door.Parent = originalMap
				end
			end
		end

		if closedModel then
			for _, door in pairs(closedModel:GetChildren()) do
				if door:IsA("Model") then
					door.Parent = originalMap
				end
			end
		end
	end

	PlayerConnections.DoorEsp = {}

	if doorsManager then
		doorsManager:Destroy()
	end
end

local function DoorEsp()
	StopDoorEsp()
	local themap = map.Value
	if not themap then
		return
	end

	local OpenedGroup = Instance.new("Model")
	OpenedGroup.Parent = workspace
	OpenedGroup.Name = "DoorsManager"

	local Open = Instance.new("Model")
	Open.Parent = OpenedGroup
	Open.Name = "Open"

	local Closed = Instance.new("Model")
	Closed.Parent = OpenedGroup
	Closed.Name = "Closed"

	local openhl = Instance.new("Highlight")
	openhl.FillColor = Settings.EspSettings.DoorEsp.OpenColor
	openhl.OutlineColor = Settings.EspSettings.DoorEsp.OpenOutlineColor
	openhl.OutlineTransparency = Settings.EspSettings.DoorEsp.OutlineTransparency
	openhl.FillTransparency = Settings.EspSettings.DoorEsp.OpenFillTransparency
	openhl.Parent = Open

	local closedhl = Instance.new("Highlight")
	closedhl.FillColor = Settings.EspSettings.DoorEsp.ClosedColor
	closedhl.OutlineColor = Settings.EspSettings.DoorEsp.ClosedOutlineColor
	closedhl.OutlineTransparency = Settings.EspSettings.DoorEsp.OutlineTransparency
	closedhl.FillTransparency = Settings.EspSettings.DoorEsp.ClosedFillTransparency
	closedhl.Parent = Closed

	for _, v in pairs(themap:GetChildren()) do
		if v.Name == "SingleDoor" or v.Name == "DoubleDoor" then
			local trigger = v:FindFirstChild("DoorTrigger")
			if trigger then
				local actionsign = trigger:FindFirstChild("ActionSign")
				if actionsign then
					if actionsign.Value == 11 then
						v.Parent = Open
					else
						v.Parent = Closed
					end
					local conn = actionsign:GetPropertyChangedSignal("Value"):Connect(function()
						if actionsign.Value == 11 then
							v.Parent = Open
						else
							v.Parent = Closed
						end
					end)
					PlayerConnections.DoorEsp[v] = conn
				end
			end
		end
	end
end

local function UpdatePcEspColors()
	for pc, conn in pairs(PlayerConnections.PcEsp) do
		local highlight = pc:FindFirstChildWhichIsA("Highlight")
		if highlight then
			highlight.OutlineColor = Settings.EspSettings.PcEsp.OutlineColor
			highlight.OutlineTransparency = Settings.EspSettings.PcEsp.OutlineTransparency
			highlight.FillTransparency = Settings.EspSettings.PcEsp.FillTransparency
		end
	end
end

local function UpdateTubeEspColors()
	for tube, highlight in pairs(PlayerConnections.TubeEsp) do
		if highlight and highlight.Parent then
			highlight.OutlineColor = Settings.EspSettings.TubeEsp.OutlineColor
			highlight.OutlineTransparency = Settings.EspSettings.TubeEsp.OutlineTransparency
			highlight.FillTransparency = Settings.EspSettings.TubeEsp.FillTransparency
			highlight.FillColor = Settings.EspSettings.TubeEsp.FillColor
		end
	end
end

local function StopExitEsp()
	for exit, highlight in pairs(PlayerConnections.ExitEsp) do
		if highlight and highlight.Parent then
			highlight:Destroy()
		end
	end
	PlayerConnections.ExitEsp = {}
end

local function StartExitEsp()
	StopExitEsp()
	local themap = map.Value
	if not themap then
		return
	end
	for _, v in pairs(themap:GetChildren()) do
		if v.Name == "ExitDoor" then
			local highlight = Instance.new("Highlight")
			highlight.OutlineColor = Settings.EspSettings.ExitEsp.OutlineColor
			highlight.OutlineTransparency = Settings.EspSettings.ExitEsp.OutlineTransparency
			highlight.FillTransparency = Settings.EspSettings.ExitEsp.FillTransparency
			highlight.FillColor = Settings.EspSettings.ExitEsp.FillColor
			highlight.Parent = v
			PlayerConnections.ExitEsp[v] = highlight
		end
	end
end

local function UpdateExitEspColors()
	for exit, highlight in pairs(PlayerConnections.ExitEsp) do
		if highlight and highlight.Parent then
			highlight.OutlineColor = Settings.EspSettings.ExitEsp.OutlineColor
			highlight.OutlineTransparency = Settings.EspSettings.ExitEsp.OutlineTransparency
			highlight.FillTransparency = Settings.EspSettings.ExitEsp.FillTransparency
			highlight.FillColor = Settings.EspSettings.ExitEsp.FillColor
		end
	end
end

local function getCharacterParts(character)
	return {
		Head = character:FindFirstChild("Head"),
		Torso = character:FindFirstChild("Torso"),
		LeftArm = character:FindFirstChild("Left Arm"),
		RightArm = character:FindFirstChild("Right Arm"),
		LeftLeg = character:FindFirstChild("Left Leg"),
		RightLeg = character:FindFirstChild("Right Leg"),
	}
end

local function getSkeletonJoints()
	return {
		{ "Head", "Torso" },
		{ "Torso", "LeftArm" },
		{ "Torso", "RightArm" },
		{ "Torso", "LeftLeg" },
		{ "Torso", "RightLeg" },
	}
end

local function createSkeletonUI(character)
	if SkeletonUIs[character] then
		return SkeletonUIs[character]
	end

	local hrp = character:FindFirstChild("HumanoidRootPart")
	if not hrp then
		return
	end

	local parts = getCharacterParts(character)
	if not parts.Head or not parts.Torso then
		return
	end

	local lines = {}
	local joints = getSkeletonJoints()

	for _, joint in pairs(joints) do
		local line = Drawing.new("Line")
		line.Thickness = Settings.EspSettings.PlayerEsp.SkeletonSettings.Thickness
		line.Color = Settings.EspSettings.PlayerEsp.SkeletonSettings.Color
		line.Transparency = Settings.EspSettings.PlayerEsp.SkeletonSettings.Transparency
		line.Visible = false
		lines[joint[1] .. "_" .. joint[2]] = line
	end

	SkeletonUIs[character] = lines

	SkeletonConnections[character] = RunService.RenderStepped:Connect(function()
		if not character or not character.Parent or not character:FindFirstChild("HumanoidRootPart") then
			return
		end

		local cam = workspace.CurrentCamera
		local parts = getCharacterParts(character)

		for _, joint in pairs(joints) do
			local p1 = parts[joint[1]]
			local p2 = parts[joint[2]]
			local line = lines[joint[1] .. "_" .. joint[2]]

			if p1 and p2 and line then
				local pos1, onScreen1 = cam:WorldToViewportPoint(p1.Position)
				local pos2, onScreen2 = cam:WorldToViewportPoint(p2.Position)

				if onScreen1 and onScreen2 and pos1.Z > 0 and pos2.Z > 0 then
					line.From = Vector2.new(pos1.X, pos1.Y)
					line.To = Vector2.new(pos2.X, pos2.Y)
					line.Visible = true
				else
					line.Visible = false
				end
			end
		end
	end)

	return lines
end

local function removeSkeletonUI(character)
	if SkeletonConnections[character] then
		SkeletonConnections[character]:Disconnect()
		SkeletonConnections[character] = nil
	end
	if SkeletonUIs[character] then
		for _, line in pairs(SkeletonUIs[character]) do
			if line and line.Remove then
				line:Remove()
			end
		end
		SkeletonUIs[character] = nil
	end
end

function createBoxUI(character)
	if BoxUIs[character] then
		return BoxUIs[character]
	end

	local hrp = character:FindFirstChild("HumanoidRootPart")
	if not hrp then
		return
	end

	local boxLines = {
		TopLeft = Drawing.new("Line"),
		TopRight = Drawing.new("Line"),
		BottomLeft = Drawing.new("Line"),
		BottomRight = Drawing.new("Line"),
	}

	for _, line in pairs(boxLines) do
		line.Thickness = Settings.EspSettings.PlayerEsp.BoxEsp.Thickness
		line.Color = Settings.EspSettings.PlayerEsp.BoxEsp.Color
		line.Transparency = Settings.EspSettings.PlayerEsp.BoxEsp.Transparency
		line.Visible = false
	end

	BoxUIs[character] = boxLines

	BoxConnections[character] = RunService.RenderStepped:Connect(function()
		if not character or not character.Parent or not character:FindFirstChild("HumanoidRootPart") then
			return
		end

		local cam = workspace.CurrentCamera
		local hrp = character:FindFirstChild("HumanoidRootPart")

		if not hrp then
			for _, line in pairs(boxLines) do
				line.Visible = false
			end
			return
		end

		local parts = {}
		for _, part in pairs(character:GetDescendants()) do
			if part:IsA("BasePart") and part.Name ~= "HumanoidRootPart" then
				table.insert(parts, part)
			end
		end

		if #parts == 0 then
			for _, line in pairs(boxLines) do
				line.Visible = false
			end
			return
		end

		local minX, minY = math.huge, math.huge
		local maxX, maxY = -math.huge, -math.huge
		local allOnScreen = true

		for _, part in pairs(parts) do
			local pos, onScreen = cam:WorldToViewportPoint(part.Position)
			if onScreen and pos.Z > 0 then
				local size = part.Size
				local corners = {
					part.CFrame * CFrame.new(size.X / 2, size.Y / 2, 0),
					part.CFrame * CFrame.new(-size.X / 2, size.Y / 2, 0),
					part.CFrame * CFrame.new(size.X / 2, -size.Y / 2, 0),
					part.CFrame * CFrame.new(-size.X / 2, -size.Y / 2, 0),
				}

				for _, corner in pairs(corners) do
					local cornerPos = cam:WorldToViewportPoint(corner.Position)
					minX = math.min(minX, cornerPos.X)
					minY = math.min(minY, cornerPos.Y)
					maxX = math.max(maxX, cornerPos.X)
					maxY = math.max(maxY, cornerPos.Y)
				end
			else
				allOnScreen = false
			end
		end

		if allOnScreen and minX ~= math.huge then
			boxLines.TopLeft.From = Vector2.new(minX, minY)
			boxLines.TopLeft.To = Vector2.new(maxX, minY)

			boxLines.BottomLeft.From = Vector2.new(minX, maxY)
			boxLines.BottomLeft.To = Vector2.new(maxX, maxY)

			boxLines.TopRight.From = Vector2.new(minX, minY)
			boxLines.TopRight.To = Vector2.new(minX, maxY)

			boxLines.BottomRight.From = Vector2.new(maxX, minY)
			boxLines.BottomRight.To = Vector2.new(maxX, maxY)

			for _, line in pairs(boxLines) do
				line.Visible = true
			end
		else
			for _, line in pairs(boxLines) do
				line.Visible = false
			end
		end
	end)

	return boxLines
end

function updateBoxUI()
	for _, v in pairs(Players:GetPlayers()) do
		local character = v.Character or v.CharacterAdded:Wait()
		local lines = BoxUIs[character]
		if not lines then
			return
		end
		for _, line in pairs(lines) do
			line.Thickness = Settings.EspSettings.PlayerEsp.BoxEsp.Thickness
			line.Color = Settings.EspSettings.PlayerEsp.BoxEsp.Color
			line.Transparency = Settings.EspSettings.PlayerEsp.BoxEsp.Transparency
		end
	end
end

function removeBoxUI(character)
	if BoxConnections[character] then
		BoxConnections[character]:Disconnect()
		BoxConnections[character] = nil
	end
	if BoxUIs[character] then
		for _, line in pairs(BoxUIs[character]) do
			if line and line.Remove then
				line:Remove()
			end
		end
		BoxUIs[character] = nil
	end
end

function startTracers()
	for _, plr in pairs(Players:GetPlayers()) do
		if plr ~= player then
			local line = Drawing.new("Line")
			TracerLines[plr] = line

			local conn = RunService.PreRender:Connect(function()
				if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
					local hrp = plr.Character.HumanoidRootPart
					local pos, onScreen = camera:WorldToViewportPoint(hrp.Position)

					local tSettings = Settings.EspSettings.PlayerEsp.TracerSettings
					line.Color = tSettings.Color or Color3.new(0, 1, 0)
					line.Thickness = tSettings.Thickness or 2
					line.Transparency = 1

					local from
					if tSettings.FromBottom == true then
						from = Vector2.new(camera.ViewportSize.X / 2, camera.ViewportSize.Y)
					else
						from = Vector2.new(camera.ViewportSize.X / 2, camera.ViewportSize.Y / 2)
					end

					if onScreen then
						line.From = from
						line.To = Vector2.new(pos.X, pos.Y)
						line.Visible = tSettings.Enabled
					else
						line.Visible = false
					end
				else
					line.Visible = false
				end
			end)

			table.insert(TracerConnections, conn)
		end
	end
end

function stopTracers()
	for _, conn in pairs(TracerConnections) do
		conn:Disconnect()
	end
	TracerConnections = {}
	for _, line in pairs(TracerLines) do
		line:Remove()
	end
	TracerLines = {}
end

function UpdateTracers()
	local tracerSettings = Settings.EspSettings.PlayerEsp.TracerSettings

	for player, line in pairs(TracerLines) do
		if line then
			line.Color = tracerSettings.Color
			line.Thickness = tracerSettings.Thickness
			line.Transparency = tracerSettings.Transparancy

			if not tracerSettings.Enabled then
				line.Visible = false
			end
		end
	end
end

function stopSkeletonEsp()
	for character, _ in pairs(SkeletonConnections) do
		removeSkeletonUI(character)
	end
end

function startSkeleton()
	stopSkeletonEsp()
	for _, plr in pairs(Players:GetPlayers()) do
		if plr ~= player and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
			createSkeletonUI(plr.Character)
		end
	end
end

function UpdateSkeleton()
	local skelSettings = Settings.EspSettings.PlayerEsp.SkeletonSettings

	for character, lines in pairs(SkeletonUIs) do
		for _, line in pairs(lines) do
			if line then
				line.Color = skelSettings.Color
				line.Thickness = skelSettings.Thickness
				line.Transparency = skelSettings.Transparency
				if not Settings.EspSettings.PlayerEsp.UseSkeletonEsp then
					line.Visible = false
				end
			end
		end
	end

	if not Settings.EspSettings.PlayerEsp.UseSkeletonEsp then
		for character, lines in pairs(SkeletonUIs) do
			for _, line in pairs(lines) do
				if line then
					line.Visible = false
				end
			end
		end
	end
end

function stopBoxEsp()
	for character in pairs(BoxUIs) do
		removeBoxUI(character)
	end
end

local function startBoxEsp()
	stopBoxEsp()
	for _, plr in pairs(Players:GetPlayers()) do
		if plr ~= player and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
			createBoxUI(plr.Character)
		end
	end
end

local function CreateRunnerTimerLabel(plr)
	local character = plr.Character
	if character then
		local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
		if humanoidRootPart then
			local billboard = humanoidRootPart:FindFirstChild("BeastPowerBillboard")
			if not billboard then
				billboard = Instance.new("BillboardGui")
				billboard.Name = "BeastPowerBillboard"
				billboard.Size = UDim2.new(2, 0, 1, 0)
				billboard.StudsOffset = Vector3.new(0, 3, 0)
				billboard.AlwaysOnTop = true
				billboard.LightInfluence = 1
				billboard.Parent = humanoidRootPart

				local label = Instance.new("TextLabel")
				label.Name = "BeastPowerLabel"
				label.Size = UDim2.new(1, 0, 1, 0)
				label.BackgroundTransparency = 1
				label.Font = Enum.Font.Arcade
				label.TextSize = 20
				label.Text = ""
				label.TextStrokeTransparency = 0.5
				label.TextColor3 = Settings.GadgetSettings.ProgressSettings.RunnerTimer.TextColor
				label.TextStrokeColor3 = Color3.new(0, 0, 0)
				label.Parent = billboard
			else
				local label = billboard:FindFirstChild("BeastPowerLabel")
				if label then
					label.TextColor3 = Settings.GadgetSettings.ProgressSettings.RunnerTimer.TextColor
				end
			end
			return billboard:FindFirstChild("BeastPowerLabel")
		end
	end
	return nil
end
local function EnsureAllBillboardsExist()
	for _, plr in pairs(Players:GetPlayers()) do
		if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
			CreateRunnerTimerLabel(plr)
		end
	end
end

local function UpdateRunnerTimerColor()
	for _, plr in pairs(Players:GetPlayers()) do
		if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
			local billboard = plr.Character.HumanoidRootPart:FindFirstChild("BeastPowerBillboard")
			if billboard then
				local label = billboard:FindFirstChild("BeastPowerLabel")
				if label then
					label.TextColor3 = Settings.GadgetSettings.ProgressSettings.RunnerTimer.TextColor
				end
			end
		end
	end
end

local function UpdateRunnerTimer()
	local beast = GetBeast()
	if not beast then
		return
	end

	local beastPlayer = Players:GetPlayerFromCharacter(beast)
	if not beastPlayer then
		return
	end

	local label = CreateRunnerTimerLabel(beastPlayer)

	if label then
		local beastPowers = beast:FindFirstChild("BeastPowers")
		if beastPowers then
			local numberValue = beastPowers:FindFirstChildOfClass("NumberValue")
			if numberValue then
				local v = numberValue.Value
				local previousV = previousValues[beastPlayer.UserId] or v
				local state = runnerStates[beastPlayer.UserId] or "cooldown"

				if v < previousV and v < 1 then
					state = "active"
				elseif v > previousV or v >= 1 then
					state = "cooldown"
				end

				runnerStates[beastPlayer.UserId] = state

				if Settings.GadgetSettings.ProgressSettings.RunnerTimer.DisplaySeconds then
					if v >= 1 then
						label.Text = "Full"
					elseif state == "active" then
						local secondsLeft = v * 3
						label.Text = string.format("%.3fs", secondsLeft)
					else
						local secondsLeft = (1 - v) * 22
						label.Text = string.format("%.3fs", secondsLeft)
					end
				else
					local percentage = v * 100
					label.Text = string.format("%.1f%%", percentage)
				end

				previousValues[beastPlayer.UserId] = v
			else
				label.Text = ""
			end
		else
			label.Text = ""
		end
	end

	for _, plr in pairs(Players:GetPlayers()) do
		if plr ~= beastPlayer and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
			local billboard = plr.Character.HumanoidRootPart:FindFirstChild("BeastPowerBillboard")
			if billboard then
				local label = billboard:FindFirstChild("BeastPowerLabel")
				if label then
					label.Text = ""
				end
			end
		end
	end
end

local function StopRunnerTimer()
	if Settings.GadgetSettings.ProgressSettings.RunnerTimer.Connection then
		Settings.GadgetSettings.ProgressSettings.RunnerTimer.Connection:Disconnect()
		Settings.GadgetSettings.ProgressSettings.RunnerTimer.Connection = nil
	end
	for _, plr in pairs(Players:GetPlayers()) do
		if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
			local billboard = plr.Character.HumanoidRootPart:FindFirstChild("BeastPowerBillboard")
			if billboard then
				local label = billboard:FindFirstChild("BeastPowerLabel")
				if label then
					label.Text = ""
				end
			end
		end
	end
	runnerStates = {}
end

local function StartRunnerTimer()
	StopRunnerTimer()

	EnsureAllBillboardsExist()

	local connection = RunService.Heartbeat:Connect(function(deltaTime)
		if not Settings.GadgetSettings.ProgressSettings.RunnerTimer.Enabled then
			StopRunnerTimer()
			return
		end
		local currentTime = tick()
		if currentTime - lastUpdate >= UPDATE_INTERVAL then
			lastUpdate = currentTime
			UpdateRunnerTimer()
		end
	end)
	Settings.GadgetSettings.ProgressSettings.RunnerTimer.Connection = connection
end

local function UpdateGetupTimerColors()
	for plr, uiData in pairs(GetupUis) do
		if uiData and uiData.timerLabel then
			local tempStats = plr:FindFirstChild("TempPlayerStatsModule")
			if tempStats then
				local actionProgress = tempStats:FindFirstChild("ActionProgress")
				if actionProgress then
					local secondsLeft = (1 - actionProgress.Value) * c
					uiData.timerLabel.TextColor3 = secondsLeft
								<= Settings.GadgetSettings.ProgressSettings.GetupTimer.WhenToHit
							and Settings.GadgetSettings.ProgressSettings.GetupTimer.HitColor
						or Settings.GadgetSettings.ProgressSettings.GetupTimer.NotHitColor
				end
			end
		end
	end

	for _, plr in pairs(Players:GetPlayers()) do
		if plr.Character then
			local head = plr.Character:FindFirstChild("Head")
			if head then
				local countdown = head:FindFirstChild("RagdollCountdown")
				if countdown then
					local label = countdown:FindFirstChild("CountdownLabel")
					if label then
						local tempStats = plr:FindFirstChild("TempPlayerStatsModule")
						if tempStats then
							local actionProgress = tempStats:FindFirstChild("ActionProgress")
							if actionProgress then
								local secondsLeft = (1 - actionProgress.Value) * c
								label.TextColor3 = secondsLeft
											<= Settings.GadgetSettings.ProgressSettings.GetupTimer.WhenToHit
										and Settings.GadgetSettings.ProgressSettings.GetupTimer.HitColor
									or Settings.GadgetSettings.ProgressSettings.GetupTimer.NotHitColor
							end
						end
					end
				end
			end
		end
	end
end

local function CreateGetupTimerLabel(head)
	local billboardGui = Instance.new("BillboardGui")
	billboardGui.Name = "RagdollCountdown"
	billboardGui.AlwaysOnTop = true
	billboardGui.Size = UDim2.new(3, 0, 1, 0)
	billboardGui.StudsOffset = Vector3.new(0, 3, 0)
	billboardGui.Parent = head

	local label = Instance.new("TextLabel")
	label.Name = "CountdownLabel"
	label.Size = UDim2.new(1, 0, 1, 0)
	label.BackgroundTransparency = 1
	label.TextScaled = true
	label.TextColor3 = Settings.GadgetSettings.ProgressSettings.GetupTimer.NotHitColor
	label.TextStrokeTransparency = 0
	label.TextStrokeColor3 = Color3.new(0, 0, 0)
	label.Text = ""
	label.Parent = billboardGui

	return billboardGui, label
end

local function RemoveGetupTimerLabel(head)
	local countdown = head:FindFirstChild("RagdollCountdown")
	if countdown then
		countdown:Destroy()
	end
end

local function updateUIPositions()
	local screenHeight = 1
	local baseY = 0.94
	local yStep = 0.1

	for i, plr in pairs(HitPlayers) do
		local uiData = GetupUis[plr]
		if uiData then
			local frame = uiData.frame
			local yOffset = (i - 1) * yStep
			frame.Position = UDim2.new(1, 0, baseY - yOffset, 0)
			frame.AnchorPoint = Vector2.new(1, 1)
		end
	end
end

local function removeBottomRightUI(plr)
	if GetupUis[plr] then
		GetupUis[plr].screenGui:Destroy()
		GetupUis[plr] = nil
		updateUIPositions()
	end
end

local function updateBottomRightUI(plr, actionProgress)
	if not GetupUis[plr] then
		local screenGui = Instance.new("ScreenGui")
		screenGui.Name = "RagdollUI"
		screenGui.Parent = player:FindFirstChild("PlayerGui") or player:WaitForChild("PlayerGui")

		local frame = Instance.new("Frame")
		frame.Size = UDim2.new(0.15, 0, 0.08, 0)
		frame.BackgroundTransparency = 1
		frame.Parent = screenGui

		local nameLabel = Instance.new("TextLabel")
		nameLabel.Name = "PlayerNameLabel"
		nameLabel.Size = UDim2.new(1, 0, 0.5, 0)
		nameLabel.Position = UDim2.new(0, 0, 0, 0)
		nameLabel.BackgroundTransparency = 1
		nameLabel.TextScaled = true
		nameLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
		nameLabel.TextStrokeTransparency = 0
		nameLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
		nameLabel.Text = ""
		nameLabel.Parent = frame

		local timerLabel = Instance.new("TextLabel")
		timerLabel.Name = "TimerLabel"
		timerLabel.Size = UDim2.new(1, 0, 0.5, 0)
		timerLabel.Position = UDim2.new(0, 0, 0.5, 0)
		timerLabel.BackgroundTransparency = 1
		timerLabel.TextScaled = true
		timerLabel.TextColor3 = Settings.GadgetSettings.ProgressSettings.GetupTimer.NotHitColor
		timerLabel.TextStrokeTransparency = 0
		timerLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
		timerLabel.Text = ""
		timerLabel.Parent = frame

		GetupUis[plr] = { screenGui = screenGui, frame = frame, timerLabel = timerLabel, nameLabel = nameLabel }
		updateUIPositions()
	end

	local uiData = GetupUis[plr]
	local timerLabel = uiData.timerLabel
	local nameLabel = uiData.nameLabel

	if not Settings.GadgetSettings.ProgressSettings.GetupTimer.Enabled then
		timerLabel.Text = ""
		nameLabel.Text = ""
		return
	end

	local secondsLeft = (1 - actionProgress) * c
	local newName, _, _, tag, tagColor = getPlayerData(plr.Name)
	nameLabel.Text = newName or plr.Name
	timerLabel.Text = string.format("%.3f", secondsLeft)
	timerLabel.TextColor3 = secondsLeft <= Settings.GadgetSettings.ProgressSettings.GetupTimer.WhenToHit
			and Settings.GadgetSettings.ProgressSettings.GetupTimer.HitColor
		or Settings.GadgetSettings.ProgressSettings.GetupTimer.NotHitColor
end

local function startRagdollCountdown(plr, ragdoll, actionProgress)
	local character = plr.Character or plr.CharacterAdded:Wait()
	local head = character:FindFirstChild("Head")
	if not head then
		return
	end

	RemoveGetupTimerLabel(head)
	local _, label = CreateGetupTimerLabel(head)

	if GetupConnections[plr] then
		GetupConnections[plr]:Disconnect()
	end

	GetupConnections[plr] = RunService.PreRender:Connect(function()
		if not ragdoll.Value then
			RemoveGetupTimerLabel(head)
			removeBottomRightUI(plr)
			GetupConnections[plr]:Disconnect()
			GetupConnections[plr] = nil
			return
		end

		local secondsLeft = (1 - actionProgress.Value) * c
		if secondsLeft < 0 then
			RemoveGetupTimerLabel(head)
			removeBottomRightUI(plr)
			GetupConnections[plr]:Disconnect()
			GetupConnections[plr] = nil
		else
			if not Settings.GadgetSettings.ProgressSettings.GetupTimer.Enabled then
				label.Text = ""
			else
				label.Text = string.format("%.3f", secondsLeft)
				label.TextColor3 = secondsLeft <= Settings.GadgetSettings.ProgressSettings.GetupTimer.WhenToHit
						and Settings.GadgetSettings.ProgressSettings.GetupTimer.HitColor
					or Settings.GadgetSettings.ProgressSettings.GetupTimer.NotHitColor
			end

			updateBottomRightUI(plr, actionProgress.Value)
		end
	end)
end

local function setupRagdollMonitoring(plr)
	local tempStats = plr:FindFirstChild("TempPlayerStatsModule")
	if not tempStats then
		return
	end

	local ragdoll = tempStats:FindFirstChild("Ragdoll")
	if not ragdoll then
		return
	end

	ConnectionManager:AddPerPlayer(
		plr,
		"RagdollMonitor",
		ragdoll.Changed:Connect(function(newValue)
			if not RopeHelperSettings.Enabled or not RopeHelperSettings.AutoRopeOnHit then
				return
			end

			if newValue then
				local myChar = player.Character
				if not myChar or not myChar:FindFirstChild("BeastPowers") then
					return
				end

				local myHrp = myChar:FindFirstChild("HumanoidRootPart")
				local targetHrp = plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")

				if myHrp and targetHrp then
					local distance = (myHrp.Position - targetHrp.Position).Magnitude
					if distance <= RopeHelperSettings.MaxDistance then
						AutoRopePlayer(plr)
					end
				end
			end
		end)
	)
end
local function onRagdollChanged(plr)
	local tempStats = plr:WaitForChild("TempPlayerStatsModule")
	local ragdoll = tempStats:WaitForChild("Ragdoll")
	local actionProgress = tempStats:WaitForChild("ActionProgress")

	if ragdoll.Value then
		startRagdollCountdown(plr, ragdoll, actionProgress)
		if not table.find(HitPlayers, plr) then
			table.insert(HitPlayers, plr)
		end
		updateUIPositions()
	end

	ragdoll.Changed:Connect(function()
		if ragdoll.Value then
			startRagdollCountdown(plr, ragdoll, actionProgress)
			if not table.find(HitPlayers, plr) then
				table.insert(HitPlayers, plr)
			end
			updateUIPositions()
			if RopeHelperSettings.AutoRopeOnHit and RopeHelperSettings.Enabled then
				AutoRopePlayer(plr)
			end
		else
			local character = plr.Character
			if character then
				RemoveGetupTimerLabel(character:FindFirstChild("Head"))
			end
			removeBottomRightUI(plr)
			local index = table.find(HitPlayers, plr)
			if index then
				table.remove(HitPlayers, index)
			end
			updateUIPositions()
			if GetupConnections[plr] then
				GetupConnections[plr]:Disconnect()
				GetupConnections[plr] = nil
			end
		end
	end)
end

local function isDoorLocked(door)
	local trigger = door:FindFirstChild("DoorTrigger")
	if trigger then
		local actionSign = trigger:FindFirstChild("ActionSign")
		if actionSign then
			return actionSign.Value ~= 11
		end
	end
	return true
end

local function isExitOpen(exit)
	local exitTrigger = exit:FindFirstChild("ExitDoorTrigger")
	if exitTrigger then
		return false
	end
	return true
end

local function updateUIforPC(Pc, objectType, progress, timeRemaining)
	local gui = Pc:FindFirstChild("BillboardGui")
	if not gui then
		return
	end

	local ProgressBox = gui:FindFirstChild("ProgressBox")
	local ProgressFill = ProgressBox and ProgressBox:FindFirstChild("ProgressFill")
	local PercentageBox = gui:FindFirstChild("PercentageBox")
	local PlayerNameLabel = gui:FindFirstChild("PlayerNameLabel")

	if not ProgressBox or not ProgressFill or not PercentageBox then
		return
	end

	progress = math.clamp(progress or 0, 0, 1)

	local s
	local data
	if objectType == "computer" then
		s = Settings.GadgetSettings.ProgressSettings.PcProgress
		data = objectProgress.computers[Pc]
	elseif objectType == "exit" then
		s = Settings.GadgetSettings.ProgressSettings.ExitProgress
		data = objectProgress.exits[Pc]
	elseif objectType == "door" then
		s = Settings.GadgetSettings.ProgressSettings.DoorProgress
		data = objectProgress.doors[Pc]
	end

	if not s then
		return
	end

	gui.Enabled = s.Enabled
	if s.Enabled then
		ProgressBox.BackgroundColor3 = s.BackgroundColor
		ProgressBox.BackgroundTransparency = s.BackgroundTransparancy or 0.4
		ProgressFill.BackgroundColor3 = s.ProgressFill
		ProgressFill.BackgroundTransparency = s.ProgressTransparancy or 0.1
		PercentageBox.TextColor3 = s.TextColor

		local percentageText = string.format("%.1f%%", progress * 100)

		if s.DisplaySeconds and timeRemaining and timeRemaining > 0 then
			local secondsText = string.format("%.3fs", timeRemaining)
			PercentageBox.Text = percentageText .. " | " .. secondsText
		else
			PercentageBox.Text = percentageText
		end

		if PlayerNameLabel and data then
			if objectType ~= "computer" and s.DisplayOpener then
				if s.DisplayOpener and data.playerName and data.playerName ~= "" then
					PlayerNameLabel.Text = data.playerName
					PlayerNameLabel.TextColor3 = s.OpenerTextColor
				else
					PlayerNameLabel.Text = ""
				end
			end
		end
	end

	if ProgressFill then
		ProgressFill.Size = UDim2.new(progress, 0, 1, 0)
	end
end

local function updateprogresstracker(object, objectType, progress, timeRemaining)
	if objectType == "computer" then
		if objectProgress.computers[object] then
			objectProgress.computers[object].progress = progress
			objectProgress.computers[object].timeRemaining = timeRemaining
		end
	elseif objectType == "exit" then
		if objectProgress.exits[object] then
			objectProgress.exits[object].progress = progress
			objectProgress.exits[object].timeRemaining = timeRemaining
		end
	elseif objectType == "door" then
		if objectProgress.doors[object] then
			objectProgress.doors[object].progress = progress
			objectProgress.doors[object].timeRemaining = timeRemaining
		end
	end

	updateUIforPC(object, objectType, progress, timeRemaining)
end

local function checkDoorAndExitStates()
	for door, data in pairs(objectProgress.doors) do
		if door and door.Parent then
			local locked = isDoorLocked(door)

			if data.playerName == "" then
				local newProgress = locked and 0 or 1
				if data.progress ~= newProgress then
					data.progress = newProgress
					data.timeRemaining = nil
					updateprogresstracker(door, "door", newProgress, nil)
				end
			end
		end
	end

	for exit, data in pairs(objectProgress.exits) do
		if exit and exit.Parent then
			if data.progress >= 1 then
				data.timeRemaining = nil
				updateprogresstracker(exit, "exit", 1, nil)
				continue
			end

			local exitTrigger = exit:FindFirstChild("ExitDoorTrigger") or exit:FindFirstChild("Trigger")
			local isOpen = exitTrigger == nil

			if data.playerName == "" then
				local newProgress = isOpen and 1 or 0
				if newProgress == 1 or data.progress ~= newProgress then
					data.progress = newProgress
					data.timeRemaining = nil
					updateprogresstracker(exit, "exit", newProgress, nil)
				end
			end
		end
	end
end
local function createuiforpc(Pc, objectType)
	local existingUI = Pc:FindFirstChild("BillboardGui")
	if existingUI then
		existingUI:Destroy()
	end

	local enabled = false
	if objectType == "computer" then
		enabled = Settings.GadgetSettings.ProgressSettings.PcProgress.Enabled
	elseif objectType == "exit" then
		enabled = Settings.GadgetSettings.ProgressSettings.ExitProgress.Enabled
	elseif objectType == "door" then
		enabled = Settings.GadgetSettings.ProgressSettings.DoorProgress.Enabled
	end

	local BillboardGui = Instance.new("BillboardGui")
	local size, studsOffset

	if objectType == "computer" then
		size = UDim2.new(25, 0, 25, 0)
		studsOffset = Vector3.new(0, 13, 0)

		local ProgressBox = Instance.new("TextLabel")
		local ProgressFill = Instance.new("TextLabel")
		local PercentageBox = Instance.new("TextLabel")
		local PlayerNameLabel = Instance.new("TextLabel")

		BillboardGui.Name = "BillboardGui"
		BillboardGui.Parent = Pc
		BillboardGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
		BillboardGui.Active = true
		BillboardGui.AlwaysOnTop = true
		BillboardGui.LightInfluence = 1
		BillboardGui.Size = size
		BillboardGui.StudsOffset = studsOffset
		BillboardGui.Enabled = enabled

		ProgressBox.Name = "ProgressBox"
		ProgressBox.Parent = BillboardGui
		ProgressBox.AnchorPoint = Vector2.new(0.5, 0)
		ProgressBox.BackgroundColor3 = Color3.fromRGB(32, 32, 32)
		ProgressBox.BackgroundTransparency = 0.4
		ProgressBox.BorderSizePixel = 0
		ProgressBox.Position = UDim2.new(0.5, 0, 0.94, 0)
		ProgressBox.Size = UDim2.new(0.5, 0, 0.04, 0)
		ProgressBox.SizeConstraint = Enum.SizeConstraint.RelativeYY
		ProgressBox.Text = ""

		ProgressFill.Name = "ProgressFill"
		ProgressFill.Parent = ProgressBox
		ProgressFill.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		ProgressFill.BackgroundTransparency = 0.1
		ProgressFill.BorderSizePixel = 0
		ProgressFill.Size = UDim2.new(0, 0, 1, 0)
		ProgressFill.ZIndex = 2
		ProgressFill.Text = ""

		PercentageBox.Name = "PercentageBox"
		PercentageBox.Parent = BillboardGui
		PercentageBox.AnchorPoint = Vector2.new(0.5, 0)
		PercentageBox.BackgroundTransparency = 1
		PercentageBox.Position = UDim2.new(0.5, 0, 0.89, 0)
		PercentageBox.Size = UDim2.new(0.5, 0, 0.04, 0)
		PercentageBox.SizeConstraint = Enum.SizeConstraint.RelativeYY
		PercentageBox.Text = "0.000%"
		PercentageBox.TextColor3 = Color3.fromRGB(255, 255, 255)
		PercentageBox.TextScaled = true

		PlayerNameLabel.Name = "PlayerNameLabel"
		PlayerNameLabel.Parent = BillboardGui
		PlayerNameLabel.AnchorPoint = Vector2.new(0.5, 0)
		PlayerNameLabel.BackgroundTransparency = 1
		PlayerNameLabel.Position = UDim2.new(0.5, 0, 0.84, 0)
		PlayerNameLabel.Size = UDim2.new(0.5, 0, 0.04, 0)
		PlayerNameLabel.SizeConstraint = Enum.SizeConstraint.RelativeYY
		PlayerNameLabel.Text = ""
		PlayerNameLabel.TextColor3 = Color3.fromRGB(255, 255, 0)
		PlayerNameLabel.TextScaled = true
		PlayerNameLabel.TextStrokeTransparency = 0.5
	elseif objectType == "exit" then
		size = UDim2.new(25, 0, 25, 0)
		studsOffset = Vector3.new(0, 10, 0)

		local ProgressBox = Instance.new("TextLabel")
		local ProgressFill = Instance.new("TextLabel")
		local PercentageBox = Instance.new("TextLabel")
		local PlayerNameLabel = Instance.new("TextLabel")

		BillboardGui.Name = "BillboardGui"
		BillboardGui.Parent = Pc
		BillboardGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
		BillboardGui.Active = true
		BillboardGui.AlwaysOnTop = true
		BillboardGui.LightInfluence = 1
		BillboardGui.Size = size
		BillboardGui.StudsOffset = studsOffset
		BillboardGui.Enabled = enabled

		ProgressBox.Name = "ProgressBox"
		ProgressBox.Parent = BillboardGui
		ProgressBox.AnchorPoint = Vector2.new(0.5, 0)
		ProgressBox.BackgroundColor3 = Color3.fromRGB(32, 32, 32)
		ProgressBox.BackgroundTransparency = 0.4
		ProgressBox.BorderSizePixel = 0
		ProgressBox.Position = UDim2.new(0.5, 0, 0.94, 0)
		ProgressBox.Size = UDim2.new(0.5, 0, 0.04, 0)
		ProgressBox.SizeConstraint = Enum.SizeConstraint.RelativeYY
		ProgressBox.Text = ""

		ProgressFill.Name = "ProgressFill"
		ProgressFill.Parent = ProgressBox
		ProgressFill.BackgroundColor3 = Color3.fromRGB(85, 255, 127)
		ProgressFill.BackgroundTransparency = 0.1
		ProgressFill.BorderSizePixel = 0
		ProgressFill.Size = UDim2.new(0, 0, 1, 0)
		ProgressFill.ZIndex = 2
		ProgressFill.Text = ""

		PercentageBox.Name = "PercentageBox"
		PercentageBox.Parent = BillboardGui
		PercentageBox.AnchorPoint = Vector2.new(0.5, 0)
		PercentageBox.BackgroundTransparency = 1
		PercentageBox.Position = UDim2.new(0.5, 0, 0.89, 0)
		PercentageBox.Size = UDim2.new(0.5, 0, 0.04, 0)
		PercentageBox.SizeConstraint = Enum.SizeConstraint.RelativeYY
		PercentageBox.Text = "0.000%"
		PercentageBox.TextColor3 = Color3.fromRGB(85, 255, 127)
		PercentageBox.TextScaled = true

		PlayerNameLabel.Name = "PlayerNameLabel"
		PlayerNameLabel.Parent = BillboardGui
		PlayerNameLabel.AnchorPoint = Vector2.new(0.5, 0)
		PlayerNameLabel.BackgroundTransparency = 1
		PlayerNameLabel.Position = UDim2.new(0.5, 0, 0.84, 0)
		PlayerNameLabel.Size = UDim2.new(0.5, 0, 0.04, 0)
		PlayerNameLabel.SizeConstraint = Enum.SizeConstraint.RelativeYY
		PlayerNameLabel.Text = ""
		PlayerNameLabel.TextColor3 = Color3.fromRGB(255, 255, 0)
		PlayerNameLabel.TextScaled = true
		PlayerNameLabel.TextStrokeTransparency = 0.5
	elseif objectType == "door" then
		size = UDim2.new(10, 0, 10, 0)
		studsOffset = Vector3.new(0, 0, 0)

		local ProgressBox = Instance.new("TextLabel")
		local ProgressFill = Instance.new("TextLabel")
		local PercentageBox = Instance.new("TextLabel")
		local PlayerNameLabel = Instance.new("TextLabel")

		BillboardGui.Name = "BillboardGui"
		BillboardGui.Parent = Pc
		BillboardGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
		BillboardGui.Active = true
		BillboardGui.AlwaysOnTop = true
		BillboardGui.LightInfluence = 1
		BillboardGui.Size = size
		BillboardGui.StudsOffset = studsOffset
		BillboardGui.Enabled = enabled

		ProgressBox.Name = "ProgressBox"
		ProgressBox.Parent = BillboardGui
		ProgressBox.AnchorPoint = Vector2.new(0.5, 0)
		ProgressBox.BackgroundColor3 = Color3.fromRGB(32, 32, 32)
		ProgressBox.BackgroundTransparency = 0.4
		ProgressBox.BorderSizePixel = 0
		ProgressBox.Position = UDim2.new(0.5, 0, 0.6, 0)
		ProgressBox.Size = UDim2.new(0.7, 0, 0.08, 0)
		ProgressBox.SizeConstraint = Enum.SizeConstraint.RelativeYY
		ProgressBox.Text = ""

		ProgressFill.Name = "ProgressFill"
		ProgressFill.Parent = ProgressBox
		ProgressFill.BackgroundColor3 = Color3.fromRGB(133, 88, 0)
		ProgressFill.BackgroundTransparency = 0.1
		ProgressFill.BorderSizePixel = 0
		ProgressFill.Size = UDim2.new(0, 0, 1, 0)
		ProgressFill.ZIndex = 2
		ProgressFill.Text = ""

		PercentageBox.Name = "PercentageBox"
		PercentageBox.Parent = BillboardGui
		PercentageBox.AnchorPoint = Vector2.new(0.5, 0)
		PercentageBox.BackgroundTransparency = 1
		PercentageBox.Position = UDim2.new(0.5, 0, 0.45, 0)
		PercentageBox.Size = UDim2.new(0.7, 0, 0.1, 0)
		PercentageBox.SizeConstraint = Enum.SizeConstraint.RelativeYY
		PercentageBox.Text = "0.000%"
		PercentageBox.TextColor3 = Color3.fromRGB(133, 88, 0)
		PercentageBox.TextScaled = true

		PlayerNameLabel.Name = "PlayerNameLabel"
		PlayerNameLabel.Parent = BillboardGui
		PlayerNameLabel.AnchorPoint = Vector2.new(0.5, 0)
		PlayerNameLabel.BackgroundTransparency = 1
		PlayerNameLabel.Position = UDim2.new(0.5, 0, 0.3, 0)
		PlayerNameLabel.Size = UDim2.new(0.7, 0, 0.12, 0)
		PlayerNameLabel.SizeConstraint = Enum.SizeConstraint.RelativeYY
		PlayerNameLabel.Text = ""
		PlayerNameLabel.TextColor3 = Color3.fromRGB(255, 255, 0)
		PlayerNameLabel.TextScaled = true
		PlayerNameLabel.TextStrokeTransparency = 0.5
	end
end

local function isValidDoorOrExit(obj)
	if obj:IsA("Script") or obj:IsA("LocalScript") or obj:IsA("ModuleScript") then
		return false
	end
	if not (obj:IsA("Model") or obj:IsA("BasePart")) then
		return false
	end
	if obj:IsA("Model") then
		local hasParts = false
		for _, child in pairs(obj:GetDescendants()) do
			if child:IsA("BasePart") then
				hasParts = true
				break
			end
		end
		return hasParts
	end
	return true
end

local function cleanupAllProgressUIs()
	for computer, data in pairs(objectProgress.computers) do
		local billboard = computer:FindFirstChild("BillboardGui")
		if billboard then
			billboard:Destroy()
		end
	end

	for door, data in pairs(objectProgress.doors) do
		local billboard = door:FindFirstChild("BillboardGui")
		if billboard then
			billboard:Destroy()
		end
	end

	for exit, data in pairs(objectProgress.exits) do
		local billboard = exit:FindFirstChild("BillboardGui")
		if billboard then
			billboard:Destroy()
		end
	end
end

local function determinestuff()
	cleanupAllProgressUIs()

	computers = {}
	exits = {}
	doors = {}
	objectProgress = {
		computers = {},
		doors = {},
		exits = {},
	}

	local currentMap = getmap()
	if currentMap then
		for _, v in pairs(workspace:GetDescendants()) do
			local name = v.Name:lower()
			if not string.find(name, "trigger") then
				if string.find(name, "computertable") then
					if isValidDoorOrExit(v) then
						table.insert(computers, v)
						objectProgress.computers[v] = {
							progress = 0,
							playerName = "",
							hackerCount = 0,
							timeRemaining = nil,
						}
						createuiforpc(v, "computer")
						updateprogresstracker(v, "computer", 0, nil)
					end
				elseif string.find(name, "exitdoor") then
					if isValidDoorOrExit(v) then
						table.insert(exits, v)
						objectProgress.exits[v] = {
							progress = 0,
							playerName = "",
							lastProgress = 0,
							lastUpdateTime = tick(),
							progressVelocity = 0,
							timeRemaining = nil,
						}
						createuiforpc(v, "exit")
						updateprogresstracker(v, "exit", 0, nil)
					end
				elseif (name == "singledoor" or name == "doubledoor") and isValidDoorOrExit(v) then
					table.insert(doors, v)
					objectProgress.doors[v] = {
						progress = 0,
						playerName = "",
						lastProgress = 0,
						lastUpdateTime = tick(),
						progressVelocity = 0,
						timeRemaining = nil,
					}
					createuiforpc(v, "door")
					updateprogresstracker(v, "door", 0, nil)
				end
			end
		end
	end
end

local function calculateTimeRemaining(object, objectType, progress, deltaTime, data)
	if progress <= 0 or progress >= 1 then
		return nil
	end

	local currentTime = tick()
	local beast = GetBeast()

	if objectType == "computer" then
		local hackerCount = data.hackerCount or 1
		if hackerCount < 1 then
			hackerCount = 1
		end

		local remainingProgress = 1 - progress
		local timeRemaining = (remainingProgress * 50) / hackerCount

		return timeRemaining
	elseif objectType == "door" then
		local deltaProgress = progress - data.lastProgress
		local timeSinceLastUpdate = currentTime - data.lastUpdateTime

		if deltaProgress > 0 and timeSinceLastUpdate > 0 then
			local progressPerSecond = deltaProgress / timeSinceLastUpdate
			local remainingProgress = 1 - progress
			return remainingProgress / progressPerSecond
		end

		local isBeastOpening = false
		if beast and data.playerName ~= "" then
			isBeastOpening = (data.playerName == beast.Name)
		end

		local totalTime = isBeastOpening and 1 or 1.5
		return (1 - progress) * totalTime
	elseif objectType == "exit" then
		return (1 - progress) * 11
	end

	return nil
end

local function updateObjectUI(object, progress, playerName, objectType, deltaTime)
	local data
	if objectType == "computer" then
		data = objectProgress.computers[object]
	elseif objectType == "door" then
		data = objectProgress.doors[object]
	elseif objectType == "exit" then
		data = objectProgress.exits[object]
	end

	if not data then
		return
	end

	local timeRemaining = calculateTimeRemaining(object, objectType, progress, deltaTime, data)

	data.progress = progress
	data.playerName = playerName
	data.timeRemaining = timeRemaining
	data.lastProgress = progress
	data.lastUpdateTime = tick()

	updateprogresstracker(object, objectType, progress, timeRemaining)
end

local function maintainObjectUIs()
	for computer, data in pairs(objectProgress.computers) do
		if computer.Parent then
			local timeRemaining = calculateTimeRemaining(computer, "computer", data.progress, 0, data)
			data.timeRemaining = timeRemaining
			updateprogresstracker(computer, "computer", data.progress, timeRemaining)
		end
	end

	for door, data in pairs(objectProgress.doors) do
		if door.Parent then
			updateprogresstracker(door, "door", data.progress, data.timeRemaining)
		end
	end

	for exit, data in pairs(objectProgress.exits) do
		if exit.Parent then
			updateprogresstracker(exit, "exit", data.progress, data.timeRemaining)
		end
	end
end

progresstrackerconnection = RunService.Heartbeat:Connect(function(deltaTime)
	local activeObjects = {
		computers = {},
		doors = {},
		exits = {},
	}

	local computerHackers = {}
	for _, computer in pairs(computers) do
		computerHackers[computer] = 0
	end

	for _, localPlayer in pairs(Players:GetPlayers()) do
		local character = localPlayer.Character
		if not character or not character:FindFirstChild("HumanoidRootPart") then
			continue
		end

		local stats = localPlayer:FindFirstChild("TempPlayerStatsModule")
		if not stats then
			continue
		end

		local progressVal = stats:FindFirstChild("ActionProgress")
		local ragdollVal = stats:FindFirstChild("Ragdoll")
		local animVal = stats:FindFirstChild("CurrentAnimation")

		local progress = progressVal and progressVal.Value or 0
		if progress == 0 then
			continue
		end
		if ragdollVal and ragdollVal.Value then
			continue
		end

		local animation = animVal and animVal.Value or ""
		local playerPosition = character.HumanoidRootPart.Position

		if animation == "Typing" then
			local nearestComputer, distance = findNearestObject(playerPosition, computers)
			if nearestComputer and distance < 15 then
				computerHackers[nearestComputer] = computerHackers[nearestComputer] + 1
			end
		end
	end

	for computer, count in pairs(computerHackers) do
		if objectProgress.computers[computer] then
			objectProgress.computers[computer].hackerCount = count
		end
	end

	for _, localPlayer in pairs(Players:GetPlayers()) do
		local character = localPlayer.Character
		if not character or not character:FindFirstChild("HumanoidRootPart") then
			continue
		end

		local stats = localPlayer:FindFirstChild("TempPlayerStatsModule")
		if not stats then
			continue
		end

		local progressVal = stats:FindFirstChild("ActionProgress")
		local ragdollVal = stats:FindFirstChild("Ragdoll")
		local animVal = stats:FindFirstChild("CurrentAnimation")

		local progress = progressVal and progressVal.Value or 0
		if progress == 0 then
			continue
		end
		if ragdollVal and ragdollVal.Value then
			continue
		end

		local animation = animVal and animVal.Value or ""
		local playerPosition = character.HumanoidRootPart.Position

		local nearestComputer, computerDistance = findNearestObject(playerPosition, computers)
		local nearestDoor, doorDistance = findNearestObject(playerPosition, doors)
		local nearestExit, exitDistance = findNearestObject(playerPosition, exits)

		if animation == "Typing" and nearestComputer and computerDistance < 15 then
			updateObjectUI(nearestComputer, progress, localPlayer.Name, "computer", deltaTime)
			activeObjects.computers[nearestComputer] = true
		end

		if nearestDoor and doorDistance < 8 then
			local doorData = objectProgress.doors[nearestDoor]
			if doorData then
				if progress > 0 and (doorData.progress < 1 or doorData.progress > 0) then
					updateObjectUI(nearestDoor, progress, localPlayer.Name, "door", deltaTime)
					activeObjects.doors[nearestDoor] = true
				end
			end
		end

		if nearestExit and exitDistance < 20 then
			local exitData = objectProgress.exits[nearestExit]
			if exitData then
				if progress > 0 and exitData.progress < 1 then
					updateObjectUI(nearestExit, progress, localPlayer.Name, "exit", deltaTime)
					activeObjects.exits[nearestExit] = true
				end
			end
		end
	end

	for computer, data in pairs(objectProgress.computers) do
		if not activeObjects.computers[computer] then
			data.playerName = ""
			data.hackerCount = 0
		end
	end

	for door, data in pairs(objectProgress.doors) do
		if not activeObjects.doors[door] then
			if data.playerName ~= "" then
				data.playerName = ""
				updateprogresstracker(door, "door", data.progress, data.timeRemaining)
			end
			if isDoorLocked(door) and data.progress > 0 and data.progress < 1 then
				data.progress = 0
				data.timeRemaining = nil
			elseif not isDoorLocked(door) then
				data.progress = 1
			end
		end
	end

	for exit, data in pairs(objectProgress.exits) do
		if not activeObjects.exits[exit] then
			if data.playerName ~= "" then
				data.playerName = ""
				data.timeRemaining = nil
				updateprogresstracker(exit, "exit", data.progress, data.timeRemaining)
			end

			local exitIsOpen = isExitOpen(exit)
			if not exitIsOpen and data.progress > 0 and data.progress < 1 then
				data.progress = 0
				data.timeRemaining = nil
			elseif exitIsOpen and data.progress < 1 then
				data.progress = 1
				data.timeRemaining = nil
			end

			if data.progress >= 1 then
				updateprogresstracker(exit, "exit", 1, nil)
			end
		end
	end

	maintainObjectUIs()
	checkDoorAndExitStates()
end)

local function LerpColor(color1, color2, alpha)
	return Color3.new(
		color1.R + (color2.R - color1.R) * alpha,
		color1.G + (color2.G - color1.G) * alpha,
		color1.B + (color2.B - color1.B) * alpha
	)
end

local function GetHealthValue(plr)
	local tempStats = plr:FindFirstChild("TempPlayerStatsModule")
	if not tempStats then
		return 0
	end
	local captured = IsCaptured(plr)
	if captured and captured.Value then
		local actionProgress = tempStats:FindFirstChild("ActionProgress")
		if actionProgress then
			return (1 - actionProgress.Value) * 100
		end
	else
		local health = tempStats:FindFirstChild("Health")
		if health then
			return health.Value
		end
	end
	return 0
end

local function GetHealthInSeconds(plr)
	local tempStats = plr:FindFirstChild("TempPlayerStatsModule")
	if not tempStats then
		return 0
	end
	local captured = IsCaptured(plr)
	if captured and captured.Value then
		local actionProgress = tempStats:FindFirstChild("ActionProgress")
		if actionProgress then
			local totalFreezeTime = 50
			return (1 - actionProgress.Value) * totalFreezeTime
		end
	else
		local health = tempStats:FindFirstChild("Health")
		if health then
			return health.Value * 0.5
		end
	end
	return 0
end

local function GetHealthColor(healthPercent)
	local settings = Settings.GadgetSettings.ProgressSettings.HealthTimer
	local lowHp = settings.LowHp
	local highColor = settings.HighHpColor
	local lowColor = settings.LowHpColor
	if healthPercent >= lowHp then
		local alpha = 1 - ((healthPercent - lowHp) / (100 - lowHp))
		return LerpColor(highColor, lowColor, alpha * 0.5)
	else
		local alpha = 1 - (healthPercent / lowHp)
		return LerpColor(highColor, lowColor, 0.5 + (alpha * 0.5))
	end
end

local function GetHealthStrokeColor(healthPercent)
	local settings = Settings.GadgetSettings.ProgressSettings.HealthTimer
	local lowHp = settings.LowHp
	if healthPercent >= lowHp then
		return settings.HighHpStrokeColor
	else
		return settings.LowHpStrokeColor
	end
end

local function CreateHealthUI(plr)
	if PlayerHealthUis[plr] then
		return
	end

	local beast = GetBeast()
	if beast and beast.Name == plr.Name then
		return
	end

	local character = plr.Character
	if not character then
		return
	end

	local head = character:WaitForChild("Head")

	local billboard = Instance.new("BillboardGui")
	billboard.Name = "HealthTimerUI"
	billboard.AlwaysOnTop = true
	billboard.Size = UDim2.new(0, 100, 0, 50)
	billboard.StudsOffset = Vector3.new(0, 4, 0)
	billboard.LightInfluence = 1
	billboard.Parent = head

	local nameLabel = Instance.new("TextLabel")
	nameLabel.Name = "NameLabel"
	nameLabel.Size = UDim2.new(1, 0, 0.5, 0)
	nameLabel.BackgroundTransparency = 1
	nameLabel.Font = Enum.Font.GothamBold
	nameLabel.TextScaled = false
	nameLabel.TextSize = 18
	nameLabel.Text = plr.Name
	nameLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
	nameLabel.TextStrokeTransparency = 0
	nameLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
	nameLabel.Visible = Settings.GadgetSettings.ProgressSettings.HealthTimer.DisplayName or false
	nameLabel.Parent = billboard

	local healthLabel = Instance.new("TextLabel")
	healthLabel.Name = "HealthLabel"
	healthLabel.Size = UDim2.new(1, 0, 0.5, 0)
	healthLabel.Position = UDim2.new(0, 0, 0.5, 0)
	healthLabel.BackgroundTransparency = 1
	healthLabel.Font = Enum.Font.GothamBold
	healthLabel.TextScaled = false
	healthLabel.TextSize = 18
	healthLabel.Text = ""
	healthLabel.TextColor3 = Settings.GadgetSettings.ProgressSettings.HealthTimer.HighHpColor
	healthLabel.TextStrokeTransparency = 0
	healthLabel.TextStrokeColor3 = Settings.GadgetSettings.ProgressSettings.HealthTimer.HighHpStrokeColor
	healthLabel.Parent = billboard

	PlayerHealthUis[plr] = {
		Billboard = billboard,
		NameLabel = nameLabel,
		HealthLabel = healthLabel,
	}
end

local function UpdateHealthUI(plr)
	local ui = PlayerHealthUis[plr]
	if not ui then
		return
	end

	if not Settings.GadgetSettings.ProgressSettings.HealthTimer.Enabled then
		ui.HealthLabel.Text = ""
		return
	end

	local healthValue = GetHealthValue(plr)
	local color = GetHealthColor(healthValue)
	local strokeColor = GetHealthStrokeColor(healthValue)

	local formatted
	if Settings.GadgetSettings.ProgressSettings.HealthTimer.DisplaySeconds then
		local seconds = GetHealthInSeconds(plr)
		formatted = string.format("%.3fs", seconds)
	else
		formatted = string.format("%.3f", healthValue)
	end

	ui.HealthLabel.TextColor3 = color
	ui.HealthLabel.TextStrokeColor3 = strokeColor
	ui.HealthLabel.Text = formatted
end

local function RemoveHealthUI(plr)
	if PlayerHealthUis[plr] then
		if PlayerHealthUis[plr].Billboard then
			PlayerHealthUis[plr].Billboard:Destroy()
		end
		PlayerHealthUis[plr] = nil
	end
	if PlayerHealths[plr] then
		if PlayerHealths[plr].ActionProgressConnection then
			PlayerHealths[plr].ActionProgressConnection:Disconnect()
		end
		if PlayerHealths[plr].HealthConnection then
			PlayerHealths[plr].HealthConnection:Disconnect()
		end
		if PlayerHealths[plr].CapturedConnection then
			PlayerHealths[plr].CapturedConnection:Disconnect()
		end
		PlayerHealths[plr] = nil
	end
	CapturedPlayers[plr] = nil
end
CapturedPlayerUIs = {}

local function CreateCapturedPlayerUI(plr)
	if CapturedPlayerUIs[plr] then
		return
	end

	local screenGui = Instance.new("ScreenGui")
	screenGui.Name = "CapturedPlayerUI_" .. plr.Name
	screenGui.Parent = playergui
	screenGui.ResetOnSpawn = false

	local frame = Instance.new("Frame")
	frame.Size = UDim2.new(0.15, 0, 0.08, 0)
	frame.BackgroundTransparency = 1
	frame.Parent = screenGui

	local nameLabel = Instance.new("TextLabel")
	nameLabel.Size = UDim2.new(1, 0, 0.5, 0)
	nameLabel.Position = UDim2.new(0, 0, 0, 0)
	nameLabel.BackgroundTransparency = 1
	nameLabel.Text = plr.Name
	nameLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
	nameLabel.TextScaled = true
	nameLabel.Font = Enum.Font.GothamBold
	nameLabel.TextStrokeTransparency = 0
	nameLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
	nameLabel.Parent = frame

	local timeLabel = Instance.new("TextLabel")
	timeLabel.Size = UDim2.new(1, 0, 0.5, 0)
	timeLabel.Position = UDim2.new(0, 0, 0.5, 0)
	timeLabel.BackgroundTransparency = 1
	timeLabel.Text = "50.000s"
	timeLabel.TextScaled = true
	timeLabel.Font = Enum.Font.GothamBold
	timeLabel.TextStrokeTransparency = 0
	timeLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
	timeLabel.Parent = frame

	CapturedPlayerUIs[plr] = {
		ScreenGui = screenGui,
		Frame = frame,
		NameLabel = nameLabel,
		TimeLabel = timeLabel,
	}

	local index = 0
	for _ in pairs(CapturedPlayerUIs) do
		index = index + 1
	end

	local baseY = 0.94
	local yStep = 0.1
	local yOffset = (index - 1) * yStep
	frame.Position = UDim2.new(0, 10, baseY - yOffset, 0)
	frame.AnchorPoint = Vector2.new(0, 1)
end

local function UpdateCapturedPlayerUI(plr)
	local ui = CapturedPlayerUIs[plr]
	if not ui then
		return
	end

	local tempStats = plr:FindFirstChild("TempPlayerStatsModule")
	if not tempStats then
		return
	end

	local actionProgress = tempStats:FindFirstChild("ActionProgress")
	if not actionProgress then
		return
	end

	local totalFreezeTime = 50
	local timeRemaining = (1 - actionProgress.Value) * totalFreezeTime

	local healthPercent = (timeRemaining / totalFreezeTime) * 100
	local color = GetHealthColor(healthPercent)
	local strokeColor = GetHealthStrokeColor(healthPercent)

	ui.NameLabel.Text = getPlayerData(plr.Name) or plr.Name
	ui.TimeLabel.TextColor3 = color
	ui.TimeLabel.TextStrokeColor3 = strokeColor
	ui.TimeLabel.Text = string.format("%.3fs", timeRemaining)
end

local function RemoveCapturedPlayerUI(plr)
	if CapturedPlayerUIs[plr] then
		CapturedPlayerUIs[plr].ScreenGui:Destroy()
		CapturedPlayerUIs[plr] = nil

		local index = 0
		for i, p in pairs(CapturedPlayerUIs) do
			local baseY = 0.94
			local yStep = 0.1
			local yOffset = index * yStep
			p.Frame.Position = UDim2.new(0, 10, baseY - yOffset, 0)
			p.Frame.AnchorPoint = Vector2.new(0, 1)
			index = index + 1
		end
	end
end

local function MonitorCapturedPlayers()
	for _, plr in pairs(Players:GetPlayers()) do
		if plr ~= player and Settings.GadgetSettings.ProgressSettings.HealthTimer.Enabled then
			local captured = IsCaptured(plr)
			if captured and captured.Value then
				if not CapturedPlayerUIs[plr] then
					CreateCapturedPlayerUI(plr)
				end
				UpdateCapturedPlayerUI(plr)
			else
				RemoveCapturedPlayerUI(plr)
			end
		end
	end
end

healthtrackerconn = RunService.Heartbeat:Connect(function()
	if Settings.GadgetSettings.ProgressSettings.HealthTimer.Enabled then
		MonitorCapturedPlayers()
	else
		for plr in pairs(CapturedPlayerUIs) do
			RemoveCapturedPlayerUI(plr)
		end
	end
end)

local function CreateWalkspeedUI(character)
	if WalkspeedUIs[character] then
		return
	end

	local hrp = character:FindFirstChild("HumanoidRootPart")
	if not hrp then
		return
	end

	local billboard = Instance.new("BillboardGui")
	billboard.Name = "WalkspeedBillboard"
	billboard.Adornee = hrp
	billboard.AlwaysOnTop = true
	billboard.Size = UDim2.new(0, 100, 0, 25)
	billboard.StudsOffset = Vector3.new(0, 5, 0)
	billboard.MaxDistance = 1000
	billboard.Parent = character

	local label = Instance.new("TextLabel")
	label.Size = UDim2.new(1, 0, 1, 0)
	label.BackgroundTransparency = 1
	label.TextColor3 = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.TextColor
	label.TextTransparency = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.TextTransparency
	label.Font = Enum.Font.GothamBold
	label.TextScaled = false
	label.TextSize = 18
	label.Text = "0"
	label.Parent = billboard

	local stroke = Instance.new("UIStroke")
	stroke.Color = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.StrokeColor
	stroke.Thickness = 2
	stroke.Transparency = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.StrokeTransparency
	stroke.Parent = label

	WalkspeedUIs[character] = {
		Gui = billboard,
		Label = label,
		Stroke = stroke,
	}

	WalkspeedTracking[character] = {
		LastPosition = hrp.Position,
		LastUpdateTime = tick(),
		SpeedSamples = {},
		SampleCount = 0,
		MaxSamples = 10,
		CurrentSpeed = 0,
		IsMoving = false,
		StoppedTime = 0,
	}
end

local function RemoveWalkspeedUI(character)
	if WalkspeedUIs[character] then
		WalkspeedUIs[character].Gui:Destroy()
		WalkspeedUIs[character] = nil
	end
	if WalkspeedTracking[character] then
		WalkspeedTracking[character] = nil
	end
end

local function UpdateWalkspeedColors()
	for character, ui in pairs(WalkspeedUIs) do
		if ui and ui.Label and ui.Stroke then
			ui.Label.TextColor3 = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.TextColor
			ui.Label.TextTransparency = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.TextTransparency
			ui.Stroke.Color = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.StrokeColor
			ui.Stroke.Transparency = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.StrokeTransparency
		end
	end
end

local function UpdateBasicSpeed(character, hrp)
	local ui = WalkspeedUIs[character]
	if not ui then
		return
	end

	local humanoid = character:FindFirstChild("Humanoid")
	if not humanoid then
		ui.Label.Text = "0.0"
		return
	end

	local speed = humanoid.WalkSpeed

	if humanoid.MoveDirection.Magnitude > 0.1 then
		ui.Label.Text = string.format("%.1f", speed)
	else
		ui.Label.Text = "0.0"
	end
end

local function UpdateAdvancedSpeed(character, hrp, humanoid)
	local tracking = WalkspeedTracking[character]
	local ui = WalkspeedUIs[character]
	if not tracking or not ui then
		return
	end

	local now = tick()
	local dt = now - tracking.LastUpdateTime

	if dt < 0.05 then
		return
	end

	local currentPos = hrp.Position
	local delta = currentPos - tracking.LastPosition
	local horizontalDist = math.sqrt(delta.X * delta.X + delta.Z * delta.Z)
	local measuredSpeed = horizontalDist / dt

	local isMoving = humanoid.MoveDirection.Magnitude > 0.1
		and humanoid:GetState() ~= Enum.HumanoidStateType.Freefall
		and humanoid:GetState() ~= Enum.HumanoidStateType.Ragdoll

	if not isMoving then
		tracking.SpeedSamples = {}
		tracking.SampleCount = 0
		tracking.CurrentSpeed = 0
		ui.Label.Text = "0.0"
	else
		table.insert(tracking.SpeedSamples, measuredSpeed)
		tracking.SampleCount = tracking.SampleCount + 1

		if tracking.SampleCount > 10 then
			table.remove(tracking.SpeedSamples, 1)
			tracking.SampleCount = 10
		end

		local sum = 0
		for _, speed in ipairs(tracking.SpeedSamples) do
			sum = sum + speed
		end
		local avgSpeed = sum / tracking.SampleCount

		tracking.CurrentSpeed = avgSpeed
		ui.Label.Text = string.format("%.1f", avgSpeed)
	end

	tracking.LastPosition = currentPos
	tracking.LastUpdateTime = now
end

local function SetupHealthTracking(plr)
	if not plr.Character then
		return
	end
	local tempStats = plr:WaitForChild("TempPlayerStatsModule")
	local actionProgress = tempStats:WaitForChild("ActionProgress")
	local health = tempStats:WaitForChild("Health")
	local captured = IsCaptured(plr)

	CreateHealthUI(plr)

	PlayerHealths[plr] = {}
	PlayerHealths[plr].ActionProgressConnection = actionProgress.Changed:Connect(function()
		UpdateHealthUI(plr)
	end)
	PlayerHealths[plr].HealthConnection = health.Changed:Connect(function()
		UpdateHealthUI(plr)
	end)

	if captured then
		PlayerHealths[plr].CapturedConnection = captured.Changed:Connect(function(value)
			CapturedPlayers[plr] = value
			UpdateHealthUI(plr)
		end)
		CapturedPlayers[plr] = captured.Value
	end

	UpdateHealthUI(plr)
end

local function EnableHealthTimer()
	for _, plr in pairs(game.Players:GetPlayers()) do
		if plr ~= game.Players.LocalPlayer and plr.Character then
			SetupHealthTracking(plr)
		end
	end
end

local function DisableHealthTimer()
	for plr, ui in pairs(PlayerHealthUis) do
		if ui and ui.Label then
			ui.Label.Text = ""
		end
	end
end

walkspeedConnection = RunService.Heartbeat:Connect(function()
	if not Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.Enabled then
		for character, ui in pairs(WalkspeedUIs) do
			if ui and ui.Gui then
				ui.Gui.Enabled = false
			end
		end
		return
	end

	for _, plr in pairs(Players:GetPlayers()) do
		if plr ~= localPlayer and plr.Character then
			local character = plr.Character
			local hrp = character:FindFirstChild("HumanoidRootPart")
			local humanoid = character:FindFirstChild("Humanoid")

			if hrp and humanoid then
				if not WalkspeedUIs[character] then
					CreateWalkspeedUI(character)
				end

				local ui = WalkspeedUIs[character]
				if ui and ui.Gui then
					ui.Gui.Enabled = true
					if Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.UseAdvancedDetection then
						UpdateAdvancedSpeed(character, hrp, humanoid)
					else
						UpdateBasicSpeed(character, hrp)
					end
				end
			end
		end
	end
end)

local function UpdateHeadstartTimer(TimeRemaining)
	local ui = playergui:FindFirstChild("HeadstartTracker")
	local textlabel = ui and ui:FindFirstChild("Timer")
	local stroke = textlabel and textlabel:FindFirstChild("Stroke")
	local sets = Settings.GadgetSettings.OtherGadgets.HeadstartTracker

	if not ui then
		ui = Instance.new("ScreenGui")
		ui.Name = "HeadstartTracker"
		ui.Parent = playergui

		textlabel = Instance.new("TextLabel")
		textlabel.Parent = ui
		textlabel.Name = "Timer"
		textlabel.AnchorPoint = Vector2.new(0.5, 0.5)
		textlabel.Position = UDim2.fromScale(0.5, 0.75)
		textlabel.Size = UDim2.fromScale(0.25, 0.25)
		textlabel.BackgroundTransparency = 1
		textlabel.TextScaled = true
		textlabel.Text = ""
		textlabel.TextColor3 = sets.TextColor
		textlabel.TextTransparency = sets.TextTransparancy

		stroke = Instance.new("UIStroke")
		stroke.Name = "Stroke"
		stroke.Parent = textlabel
		stroke.Color = sets.StrokeColor
		stroke.Transparency = sets.StrokeTransparancy
	end

	if textlabel and stroke then
		textlabel.TextColor3 = sets.TextColor
		textlabel.TextTransparency = sets.TextTransparancy
		stroke.Color = sets.StrokeColor
		stroke.Transparency = sets.StrokeTransparancy

		if TimeRemaining then
			if sets.Enabled then
				textlabel.Text = string.format("%.3f", TimeRemaining)
			else
				textlabel.Text = ""
			end
		end
	end
end

local function StopHeadstartTracking()
	local sets = Settings.GadgetSettings.OtherGadgets.HeadstartTracker
	if sets.TrackerConnection then
		sets.TrackerConnection:Disconnect()
		sets.TrackerConnection = nil
	end
	local ui = playergui:FindFirstChild("HeadstartTracker")
	if ui then
		ui:Destroy()
	end
end

local function StartHeadstartTracking()
	if not Settings.GadgetSettings.OtherGadgets.HeadstartTracker.Enabled then
		return
	end

	StopHeadstartTracking()

	local sets = Settings.GadgetSettings.OtherGadgets.HeadstartTracker

	local ui = Instance.new("ScreenGui")
	ui.Name = "HeadstartTracker"
	ui.Parent = playergui

	local text = Instance.new("TextLabel")
	text.Parent = ui
	text.Name = "Timer"
	text.AnchorPoint = Vector2.new(0.5, 0.5)
	text.Position = UDim2.fromScale(0.5, 0.75)
	text.Size = UDim2.fromScale(0.25, 0.25)
	text.BackgroundTransparency = 1
	text.TextScaled = true
	text.Text = "15.000"
	text.TextColor3 = sets.TextColor
	text.TextTransparency = sets.TextTransparancy

	local stroke = Instance.new("UIStroke")
	stroke.Parent = text
	stroke.Color = sets.StrokeColor
	stroke.Transparency = sets.StrokeTransparancy

	local mytime = 15.5
	local myconnection
	myconnection = RunService.Heartbeat:Connect(function(deltaTime)
		if not sets.Enabled then
			StopHeadstartTracking()
			return
		end
		mytime = mytime - deltaTime
		if mytime <= 0 then
			StopHeadstartTracking()
			return
		end
		text.Text = string.format("%.3f", mytime)
	end)
	sets.TrackerConnection = myconnection
end

local function GetCurrentBoost()
	local ME = Players.LocalPlayer
	local MyChar = ME.Character
	if not MyChar then
		return 0, 0
	end

	local Humanoid = MyChar:FindFirstChild("Humanoid")
	if not Humanoid then
		return 0, 0
	end

	local WalkSpeed = Humanoid.WalkSpeed
	local Beast = MyChar:FindFirstChild("BeastPowers")

	if Beast then
		if WalkSpeed >= 20 and WalkSpeed <= 29 then
			local jp = SpeedSettings.AllowJumpDuringRunner and SpeedSettings.BeastJumpPower or 0
			return SpeedSettings.RunnerBoost, jp
		elseif WalkSpeed >= 15 and WalkSpeed <= 19 then
			return SpeedSettings.BeastBoost, SpeedSettings.BeastJumpPower
		elseif WalkSpeed >= 1 and WalkSpeed <= 6 then
			return SpeedSettings.FatigueBoost, SpeedSettings.BeastJumpPower
		end
	else
		if WalkSpeed >= 15 and WalkSpeed <= 18 then
			return SpeedSettings.SurvivorBoost, SpeedSettings.SurvivorJumpPower
		elseif WalkSpeed >= 6 and WalkSpeed <= 10 then
			return SpeedSettings.CrawlBoost, SpeedSettings.SurvivorJumpPower
		end
	end

	return 0, 0
end

local function ResetSpeed()
	if SpeedSettings.Connection then
		SpeedSettings.Connection:Disconnect()
		SpeedSettings.Connection = nil
	end
	if SpeedSettings.FatigueConnection then
		SpeedSettings.FatigueConnection:Disconnect()
		SpeedSettings.FatigueConnection = nil
	end
end

local function StartFatigueMonitoring()
	if SpeedSettings.FatigueConnection then
		SpeedSettings.FatigueConnection:Disconnect()
	end

	local fatigueActive = false
	local fatigueStartTime = nil
	local lastWalkspeed = nil

	SpeedSettings.FatigueConnection = RunService.Stepped:Connect(function()
		if not SpeedSettings.Enabled or not SpeedSettings.UseFatigueCheats then
			fatigueActive = false
			fatigueStartTime = nil
			return
		end

		local MyChar = localPlayer.Character
		if not MyChar then
			fatigueActive = false
			fatigueStartTime = nil
			return
		end

		local Humanoid = MyChar:FindFirstChild("Humanoid")
		local Beast = MyChar:FindFirstChild("BeastPowers")
		if not Humanoid or not Beast then
			fatigueActive = false
			fatigueStartTime = nil
			return
		end

		local currentSpeed = Humanoid.WalkSpeed

		if currentSpeed >= 3 and currentSpeed <= 4 and (lastWalkspeed == nil or lastWalkspeed > 4) then
			fatigueActive = true
			fatigueStartTime = tick()
		end

		if fatigueActive and fatigueStartTime then
			local elapsed = tick() - fatigueStartTime
			local delayDuration = SpeedSettings.FatigueDelay
			local boostDuration = SpeedSettings.FatigueDuration

			-- If timer is below 0.8 seconds, adjust the boost duration
			if boostDuration < 0.8 then
				-- For short durations, only apply reduced boost if within the time window
				if elapsed < delayDuration then
					Humanoid.WalkSpeed = SpeedSettings.BeastSpeed
				elseif elapsed < (delayDuration + boostDuration) then
					-- Scale the walkspeed based on remaining time in boost window
					local remainingTime = (delayDuration + boostDuration) - elapsed
					Humanoid.WalkSpeed = 3.4
				else
					fatigueActive = false
					fatigueStartTime = nil
				end
			else
				-- Original behavior for longer durations
				if elapsed < delayDuration then
					Humanoid.WalkSpeed = SpeedSettings.BeastSpeed
				elseif elapsed < (delayDuration + boostDuration) then
					Humanoid.WalkSpeed = 3.4
				else
					fatigueActive = false
					fatigueStartTime = nil
				end
			end
		end

		if currentSpeed > 6 then
			fatigueActive = false
			fatigueStartTime = nil
		end

		lastWalkspeed = currentSpeed
	end)
end

local function ApplySpeed()
	if not SpeedSettings.Enabled then
		return
	end
	if SpeedSettings.Connection then
		SpeedSettings.Connection:Disconnect()
	end

	SpeedSettings.Connection = RunService.Stepped:Connect(function(gameTime, deltaTime)
		if not SpeedSettings.Enabled then
			return
		end

		local ME = Players.LocalPlayer
		local MyChar = ME.Character
		if not MyChar then
			return
		end

		local Humanoid = MyChar:FindFirstChild("Humanoid")
		local HumanoidRootPart = MyChar:FindFirstChild("HumanoidRootPart")
		if not Humanoid or not HumanoidRootPart then
			return
		end

		for _, part in pairs(MyChar:GetDescendants()) do
			if part.Name == "CamBrick" then
				part:Destroy()
			end
		end

		local Beast = MyChar:FindFirstChild("BeastPowers")

		if not SpeedSettings.UseFatigueCheats then
			local currentWalkSpeed = Humanoid.WalkSpeed
			if not (currentWalkSpeed >= 3 and currentWalkSpeed <= 4) then
				if Beast then
					Humanoid.WalkSpeed = SpeedSettings.BeastSpeed
				else
					if not (currentWalkSpeed >= 6 and currentWalkSpeed <= 10) then
						Humanoid.WalkSpeed = SpeedSettings.SurvivorSpeed
					end
				end
			end
		end

		local MoveDirection = Humanoid.MoveDirection

		if MoveDirection.Magnitude > 0 then
			local boost, jumpPower = GetCurrentBoost()

			if boost > 0 then
				HumanoidRootPart.CFrame = HumanoidRootPart.CFrame + (MoveDirection * boost * deltaTime)
			end

			if jumpPower > 0 then
				Humanoid.JumpPower = jumpPower
			end
		end
	end)

	if SpeedSettings.UseFatigueCheats then
		StartFatigueMonitoring()
	end
end

local function MakeDraggable(frame, slotName)
	local dragging = false
	local dragInput
	local dragStart
	local startPos

	frame.InputBegan:Connect(function(input)
		if
			input.UserInputType == Enum.UserInputType.MouseButton1
			or input.UserInputType == Enum.UserInputType.Touch
		then
			dragging = true
			dragStart = input.Position
			startPos = frame.Position

			input.Changed:Connect(function()
				if input.UserInputState == Enum.UserInputState.End then
					dragging = false
				end
			end)
		end
	end)

	frame.InputChanged:Connect(function(input)
		if
			input.UserInputType == Enum.UserInputType.MouseMovement
			or input.UserInputType == Enum.UserInputType.Touch
		then
			dragInput = input
		end
	end)

	RunService.Heartbeat:Connect(function()
		if dragging and dragInput then
			local delta = dragInput.Position - dragStart
			local screenSize = frame.Parent.AbsoluteSize
			local deltaScaleX = delta.X / screenSize.X
			local deltaScaleY = delta.Y / screenSize.Y

			local newScaleX = startPos.X.Scale + deltaScaleX
			local newScaleY = startPos.Y.Scale + deltaScaleY

			newScaleX = math.clamp(newScaleX, 0, 1 - frame.Size.X.Scale)
			newScaleY = math.clamp(newScaleY, 0, 1 - frame.Size.Y.Scale)

			frame.Position = UDim2.new(newScaleX, 0, newScaleY, 0)

			CameraSettings.CameraSlots[slotName].Position = Vector2.new(newScaleX, newScaleY)
		end
	end)

	UserInputService.InputEnded:Connect(function(input)
		if
			(input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch)
			and dragging
		then
			dragging = false
			local scaleX = frame.Position.X.Scale
			local scaleY = frame.Position.Y.Scale

			if Options["Cam" .. slotName .. "PosX"] and Options["Cam" .. slotName .. "PosY"] then
				Options["Cam" .. slotName .. "PosX"]:SetValue(string.format("%.3f", scaleX))
				Options["Cam" .. slotName .. "PosY"]:SetValue(string.format("%.3f", scaleY))
			end
		end
	end)
end

local function MakeResizable(frame, minSize, slotName)
	minSize = minSize or Vector2.new(0.1, 0.1)

	local resizeButton = Instance.new("TextButton")
	resizeButton.Size = UDim2.new(0, 20, 0, 20)
	resizeButton.Position = UDim2.new(1, -20, 1, -20)
	resizeButton.AnchorPoint = Vector2.new(1, 1)
	resizeButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
	resizeButton.Text = "â—¢"
	resizeButton.TextColor3 = Color3.new(1, 1, 1)
	resizeButton.Parent = frame

	local resizing = false
	local resizeStart
	local startSize

	resizeButton.InputBegan:Connect(function(input)
		if
			input.UserInputType == Enum.UserInputType.MouseButton1
			or input.UserInputType == Enum.UserInputType.Touch
		then
			resizing = true
			resizeStart = input.Position
			startSize = frame.AbsoluteSize
		end
	end)

	UserInputService.InputChanged:Connect(function(input)
		if
			resizing
			and (
				input.UserInputType == Enum.UserInputType.MouseMovement
				or input.UserInputType == Enum.UserInputType.Touch
			)
		then
			local delta = input.Position - resizeStart
			local screenSize = frame.Parent.AbsoluteSize
			local deltaScaleX = delta.X / screenSize.X
			local deltaScaleY = delta.Y / screenSize.Y

			local newScaleX = math.max(minSize.X, (startSize.X / screenSize.X) + deltaScaleX)
			local newScaleY = math.max(minSize.Y, (startSize.Y / screenSize.Y) + deltaScaleY)

			newScaleX = math.clamp(newScaleX, minSize.X, 1 - frame.Position.X.Scale)
			newScaleY = math.clamp(newScaleY, minSize.Y, 1 - frame.Position.Y.Scale)

			frame.Size = UDim2.new(newScaleX, 0, newScaleY, 0)
		end
	end)

	UserInputService.InputEnded:Connect(function(input)
		if
			(input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch)
			and resizing
		then
			resizing = false
			local scaleX = frame.Size.X.Scale
			local scaleY = frame.Size.Y.Scale

			CameraSettings.CameraSlots[slotName].Size = Vector2.new(scaleX, scaleY)
			if Options["Cam" .. slotName .. "SizeX"] and Options["Cam" .. slotName .. "SizeY"] then
				Options["Cam" .. slotName .. "SizeX"]:SetValue(string.format("%.3f", scaleX))
				Options["Cam" .. slotName .. "SizeY"]:SetValue(string.format("%.3f", scaleY))
			end
		end
	end)
end

local function CreateCameraSlot(slotName, targetPlayer)
	if CameraSettings.CameraGuis[slotName] then
		if CameraSettings.CameraGuis[slotName].Connection then
			CameraSettings.CameraGuis[slotName].Connection:Disconnect()
		end
		if CameraSettings.CameraGuis[slotName].MapConnection then
			CameraSettings.CameraGuis[slotName].MapConnection:Disconnect()
		end
		if CameraSettings.CameraGuis[slotName].Gui then
			CameraSettings.CameraGuis[slotName].Gui:Destroy()
		end
	end

	local slot = CameraSettings.CameraSlots[slotName]
	slot.Player = targetPlayer

	local screenGui = Instance.new("ScreenGui")
	screenGui.Name = "CameraSlot_" .. slotName
	screenGui.Parent = playergui
	screenGui.ResetOnSpawn = false
	screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

	local frame = Instance.new("Frame")
	frame.Name = "CameraFrame"
	frame.Size = UDim2.new(slot.Size.X, 0, slot.Size.Y, 0)
	frame.Position = UDim2.new(slot.Position.X, 0, slot.Position.Y, 0)
	frame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
	frame.BorderSizePixel = 2
	frame.BorderColor3 = Color3.fromRGB(255, 255, 255)
	frame.Parent = screenGui

	local isBeast = targetPlayer.Character and targetPlayer.Character:FindFirstChild("BeastPowers") ~= nil

	local titleBar = Instance.new("TextLabel")
	titleBar.Size = UDim2.new(1, 0, 0, 25)
	titleBar.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	titleBar.BorderSizePixel = 0
	titleBar.Text = targetPlayer.Name .. " [" .. slotName .. "]"
	titleBar.TextColor3 = isBeast and Color3.new(1, 0, 0) or Color3.new(1, 1, 1)
	titleBar.Font = Enum.Font.GothamBold
	titleBar.TextSize = 14
	titleBar.Parent = frame

	local viewportFrame = Instance.new("ViewportFrame")
	viewportFrame.Name = "Viewport"
	viewportFrame.Size = UDim2.new(1, 0, 1, -25)
	viewportFrame.Position = UDim2.new(0, 0, 0, 25)
	viewportFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
	viewportFrame.BorderSizePixel = 0
	viewportFrame.Parent = frame

	local cam = Instance.new("Camera")
	cam.CameraType = Enum.CameraType.Scriptable
	cam.FieldOfView = 70
	cam.Parent = viewportFrame
	viewportFrame.CurrentCamera = cam

	local dummyCache = {}

	local function updateMap()
		for _, child in pairs(viewportFrame:GetChildren()) do
			if child:IsA("Model") or child:IsA("Folder") or child.Name == "MapClone" then
				child:Destroy()
			end
		end

		local newCam = Instance.new("Camera")
		newCam.CameraType = Enum.CameraType.Scriptable
		newCam.FieldOfView = 70
		newCam.Parent = viewportFrame
		viewportFrame.CurrentCamera = newCam
		cam = newCam

		if map.Value then
			local mapClone = map.Value:Clone()
			mapClone.Name = "MapClone"
			for _, obj in ipairs(mapClone:GetDescendants()) do
				if
					obj.Name == "SingleDoor"
					or obj.Name == "DoubleDoor"
					or obj:IsA("Sound")
					or obj:IsA("LocalScript")
					or obj:IsA("Script")
				then
					obj:Destroy()
				end
			end
			mapClone.Parent = viewportFrame
		end

		local dummyFolder = Instance.new("Folder")
		dummyFolder.Name = "DummyFolder"
		dummyFolder.Parent = viewportFrame

		dummyCache = {}
		for _, plr in ipairs(Players:GetPlayers()) do
			if plr ~= targetPlayer and plr.Character then
				plr.Character.Archivable = true
				local dummyClone = plr.Character:Clone()
				for _, part in ipairs(dummyClone:GetDescendants()) do
					if part:IsA("Sound") or part:IsA("LocalScript") or part:IsA("Script") then
						part:Destroy()
					end
				end
				dummyClone.Parent = dummyFolder
				dummyCache[plr] = dummyClone
			end
		end

		if CameraSettings.CameraGuis[slotName] then
			CameraSettings.CameraGuis[slotName].DummyCache = dummyCache
			CameraSettings.CameraGuis[slotName].Camera = cam
		end
	end

	updateMap()

	MakeDraggable(frame, slotName)
	MakeResizable(frame, Vector2.new(0.1, 0.1), slotName)

	local mapConn = map.Changed:Connect(function()
		task.wait(0.5)
		updateMap()
	end)

	local lastUpdateTime = tick()
	local conn = RunService.Heartbeat:Connect(function()
		local currentTime = tick()
		local deltaTime = currentTime - lastUpdateTime
		lastUpdateTime = currentTime

		local fps = 1 / deltaTime
		local lerpAlpha = math.min(1, (60 / math.max(fps, 1)) * 0.2)

		if not targetPlayer or not targetPlayer.Character or not targetPlayer.Character:FindFirstChild("Head") then
			return
		end

		local headCF = targetPlayer.Character.Head.CFrame
		cam.CFrame = cam.CFrame:Lerp(headCF, lerpAlpha)

		for plr, dummy in pairs(dummyCache) do
			if plr.Character and plr.Character.PrimaryPart and dummy.PrimaryPart then
				dummy:SetPrimaryPartCFrame(plr.Character.PrimaryPart.CFrame)
			end
		end

		local newIsBeast = targetPlayer.Character:FindFirstChild("BeastPowers") ~= nil
		if newIsBeast ~= isBeast then
			isBeast = newIsBeast
			titleBar.TextColor3 = isBeast and Color3.new(1, 0, 0) or Color3.new(1, 1, 1)
		end
	end)

	CameraSettings.CameraGuis[slotName] = {
		Gui = screenGui,
		Camera = cam,
		Connection = conn,
		MapConnection = mapConn,
		Player = targetPlayer,
		DummyCache = dummyCache,
		Frame = frame,
	}
end

local function StopCameraSlot(slotName)
	local camData = CameraSettings.CameraGuis[slotName]
	if camData then
		if camData.Connection then
			camData.Connection:Disconnect()
		end
		if camData.MapConnection then
			camData.MapConnection:Disconnect()
		end
		if camData.Gui then
			camData.Gui:Destroy()
		end
		CameraSettings.CameraGuis[slotName] = nil
	end
	CameraSettings.CameraSlots[slotName].Player = nil
end

local function UpdateAllCameras()
	for slotName, slot in pairs(CameraSettings.CameraSlots) do
		if slot.Enabled then
			if slotName == "Beast" then
				local beast = GetBeast()
				if beast then
					local beastPlayer = Players:GetPlayerFromCharacter(beast)
					if beastPlayer and beastPlayer ~= player then
						if slot.Player ~= beastPlayer then
							CreateCameraSlot("Beast", beastPlayer)
						end
					else
						StopCameraSlot("Beast")
					end
				else
					StopCameraSlot("Beast")
				end
			end
		else
			StopCameraSlot(slotName)
		end
	end

	if
		CameraSettings.CameraSlots.Surv1.Enabled
		or CameraSettings.CameraSlots.Surv2.Enabled
		or CameraSettings.CameraSlots.Surv3.Enabled
		or CameraSettings.CameraSlots.Surv4.Enabled
	then
		local survivors = {}
		for _, plr in pairs(Players:GetPlayers()) do
			if
				plr ~= player
				and plr.Character
				and not plr.Character:FindFirstChild("BeastPowers")
				and plr.Character:FindFirstChild("Head")
			then
				table.insert(survivors, plr)
			end
		end

		for i, slotName in ipairs({ "Surv1", "Surv2", "Surv3", "Surv4" }) do
			local slot = CameraSettings.CameraSlots[slotName]
			if slot.Enabled then
				if survivors[i] then
					if slot.Player ~= survivors[i] then
						CreateCameraSlot(slotName, survivors[i])
					end
				else
					StopCameraSlot(slotName)
				end
			end
		end
	end
end

local function StopAllCameras()
	for slotName in pairs(CameraSettings.CameraSlots) do
		StopCameraSlot(slotName)
	end
end

local function CreateCrosshair()
	for _, element in pairs(crosshairElements) do
		if element and element.Destroy then
			element:Destroy()
		end
	end
	crosshairElements = {}

	local defaultCrosshair = playergui:FindFirstChild("CrosshairGUI")
	if defaultCrosshair then
		defaultCrosshair.Enabled = false
	end

	if not CrosshairSettings.Enabled then
		if defaultCrosshair then
			defaultCrosshair.Enabled = true
		end
		return
	end
	local screenGui = Instance.new("ScreenGui")
	screenGui.Name = "CustomCrosshairGUI"
	screenGui.Parent = playergui
	screenGui.ResetOnSpawn = false
	screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
	screenGui.IgnoreGuiInset = true
	table.insert(crosshairElements, screenGui)

	local container = Instance.new("Frame")
	container.Name = "CrosshairContainer"
	container.Size = UDim2.new(0, 100, 0, 100)
	container.Position = UDim2.new(0.5, -50, 0.5, -50)
	container.BackgroundTransparency = 1
	container.Parent = screenGui

	if CrosshairSettings.Type == "Cross" then
		if CrosshairSettings.OutlineEnabled then
			local topOutline = Instance.new("Frame")
			topOutline.Name = "TopOutline"
			topOutline.Size = UDim2.new(
				0,
				CrosshairSettings.Thickness + CrosshairSettings.OutlineThickness * 2,
				0,
				CrosshairSettings.Size
			)
			topOutline.Position = UDim2.new(
				0.5,
				-((CrosshairSettings.Thickness + CrosshairSettings.OutlineThickness * 2) / 2),
				0.5,
				-(CrosshairSettings.Gap + CrosshairSettings.Size)
			)
			topOutline.BackgroundColor3 = CrosshairSettings.OutlineColor
			topOutline.BackgroundTransparency = CrosshairSettings.Transparency
			topOutline.BorderSizePixel = 0
			topOutline.Parent = container

			local bottomOutline = Instance.new("Frame")
			bottomOutline.Name = "BottomOutline"
			bottomOutline.Size = UDim2.new(
				0,
				CrosshairSettings.Thickness + CrosshairSettings.OutlineThickness * 2,
				0,
				CrosshairSettings.Size
			)
			bottomOutline.Position = UDim2.new(
				0.5,
				-((CrosshairSettings.Thickness + CrosshairSettings.OutlineThickness * 2) / 2),
				0.5,
				CrosshairSettings.Gap
			)
			bottomOutline.BackgroundColor3 = CrosshairSettings.OutlineColor
			bottomOutline.BackgroundTransparency = CrosshairSettings.Transparency
			bottomOutline.BorderSizePixel = 0
			bottomOutline.Parent = container

			local leftOutline = Instance.new("Frame")
			leftOutline.Name = "LeftOutline"
			leftOutline.Size = UDim2.new(
				0,
				CrosshairSettings.Size,
				0,
				CrosshairSettings.Thickness + CrosshairSettings.OutlineThickness * 2
			)
			leftOutline.Position = UDim2.new(
				0.5,
				-(CrosshairSettings.Gap + CrosshairSettings.Size),
				0.5,
				-((CrosshairSettings.Thickness + CrosshairSettings.OutlineThickness * 2) / 2)
			)
			leftOutline.BackgroundColor3 = CrosshairSettings.OutlineColor
			leftOutline.BackgroundTransparency = CrosshairSettings.Transparency
			leftOutline.BorderSizePixel = 0
			leftOutline.Parent = container

			local rightOutline = Instance.new("Frame")
			rightOutline.Name = "RightOutline"
			rightOutline.Size = UDim2.new(
				0,
				CrosshairSettings.Size,
				0,
				CrosshairSettings.Thickness + CrosshairSettings.OutlineThickness * 2
			)
			rightOutline.Position = UDim2.new(
				0.5,
				CrosshairSettings.Gap,
				0.5,
				-((CrosshairSettings.Thickness + CrosshairSettings.OutlineThickness * 2) / 2)
			)
			rightOutline.BackgroundColor3 = CrosshairSettings.OutlineColor
			rightOutline.BackgroundTransparency = CrosshairSettings.Transparency
			rightOutline.BorderSizePixel = 0
			rightOutline.Parent = container
		end

		local top = Instance.new("Frame")
		top.Name = "Top"
		top.Size = UDim2.new(0, CrosshairSettings.Thickness, 0, CrosshairSettings.Size)
		top.Position =
			UDim2.new(0.5, -(CrosshairSettings.Thickness / 2), 0.5, -(CrosshairSettings.Gap + CrosshairSettings.Size))
		top.BackgroundColor3 = CrosshairSettings.Color
		top.BackgroundTransparency = CrosshairSettings.Transparency
		top.BorderSizePixel = 0
		top.Parent = container

		local bottom = Instance.new("Frame")
		bottom.Name = "Bottom"
		bottom.Size = UDim2.new(0, CrosshairSettings.Thickness, 0, CrosshairSettings.Size)
		bottom.Position = UDim2.new(0.5, -(CrosshairSettings.Thickness / 2), 0.5, CrosshairSettings.Gap)
		bottom.BackgroundColor3 = CrosshairSettings.Color
		bottom.BackgroundTransparency = CrosshairSettings.Transparency
		bottom.BorderSizePixel = 0
		bottom.Parent = container

		local left = Instance.new("Frame")
		left.Name = "Left"
		left.Size = UDim2.new(0, CrosshairSettings.Size, 0, CrosshairSettings.Thickness)
		left.Position =
			UDim2.new(0.5, -(CrosshairSettings.Gap + CrosshairSettings.Size), 0.5, -(CrosshairSettings.Thickness / 2))
		left.BackgroundColor3 = CrosshairSettings.Color
		left.BackgroundTransparency = CrosshairSettings.Transparency
		left.BorderSizePixel = 0
		left.Parent = container

		local right = Instance.new("Frame")
		right.Name = "Right"
		right.Size = UDim2.new(0, CrosshairSettings.Size, 0, CrosshairSettings.Thickness)
		right.Position = UDim2.new(0.5, CrosshairSettings.Gap, 0.5, -(CrosshairSettings.Thickness / 2))
		right.BackgroundColor3 = CrosshairSettings.Color
		right.BackgroundTransparency = CrosshairSettings.Transparency
		right.BorderSizePixel = 0
		right.Parent = container

		if CrosshairSettings.CenterDot then
			local centerDot = Instance.new("Frame")
			centerDot.Name = "CenterDot"
			centerDot.Size = UDim2.new(0, CrosshairSettings.CenterDotSize, 0, CrosshairSettings.CenterDotSize)
			centerDot.Position =
				UDim2.new(0.5, -(CrosshairSettings.CenterDotSize / 2), 0.5, -(CrosshairSettings.CenterDotSize / 2))
			centerDot.BackgroundColor3 = CrosshairSettings.CenterDotColor
			centerDot.BackgroundTransparency = CrosshairSettings.Transparency
			centerDot.BorderSizePixel = 0
			centerDot.Parent = container

			local dotCorner = Instance.new("UICorner")
			dotCorner.CornerRadius = UDim.new(1, 0)
			dotCorner.Parent = centerDot
		end
	elseif CrosshairSettings.Type == "Dot" then
		if CrosshairSettings.OutlineEnabled then
			local outline = Instance.new("Frame")
			outline.Name = "DotOutline"
			outline.Size = UDim2.new(
				0,
				CrosshairSettings.Size + CrosshairSettings.OutlineThickness * 2,
				0,
				CrosshairSettings.Size + CrosshairSettings.OutlineThickness * 2
			)
			outline.Position = UDim2.new(
				0.5,
				-((CrosshairSettings.Size + CrosshairSettings.OutlineThickness * 2) / 2),
				0.5,
				-((CrosshairSettings.Size + CrosshairSettings.OutlineThickness * 2) / 2)
			)
			outline.BackgroundColor3 = CrosshairSettings.OutlineColor
			outline.BackgroundTransparency = CrosshairSettings.Transparency
			outline.BorderSizePixel = 0
			outline.Parent = container

			local outlineCorner = Instance.new("UICorner")
			outlineCorner.CornerRadius = UDim.new(1, 0)
			outlineCorner.Parent = outline
		end

		local dot = Instance.new("Frame")
		dot.Name = "Dot"
		dot.Size = UDim2.new(0, CrosshairSettings.Size, 0, CrosshairSettings.Size)
		dot.Position = UDim2.new(0.5, -(CrosshairSettings.Size / 2), 0.5, -(CrosshairSettings.Size / 2))
		dot.BackgroundColor3 = CrosshairSettings.Color
		dot.BackgroundTransparency = CrosshairSettings.Transparency
		dot.BorderSizePixel = 0
		dot.Parent = container

		local dotCorner = Instance.new("UICorner")
		dotCorner.CornerRadius = UDim.new(1, 0)
		dotCorner.Parent = dot
	end

	if CrosshairSettings.DynamicCrosshair then
		local dynamicConnection = RunService.RenderStepped:Connect(function()
			if not CrosshairSettings.Enabled or not CrosshairSettings.DynamicCrosshair then
				return
			end

			local myChar = player.Character
			if not myChar then
				return
			end

			local humanoid = myChar:FindFirstChild("Humanoid")
			if not humanoid then
				return
			end

			local moveDirection = humanoid.MoveDirection
			local isMoving = moveDirection.Magnitude > 0

			local targetSize = isMoving and CrosshairSettings.DynamicSize or CrosshairSettings.Size
			local targetGap = isMoving and (CrosshairSettings.Gap + 5) or CrosshairSettings.Gap

			for _, child in pairs(container:GetChildren()) do
				if child.Name == "Top" then
					child.Size = UDim2.new(0, CrosshairSettings.Thickness, 0, targetSize)
					child.Position = UDim2.new(0.5, -(CrosshairSettings.Thickness / 2), 0.5, -(targetGap + targetSize))
				elseif child.Name == "Bottom" then
					child.Size = UDim2.new(0, CrosshairSettings.Thickness, 0, targetSize)
					child.Position = UDim2.new(0.5, -(CrosshairSettings.Thickness / 2), 0.5, targetGap)
				elseif child.Name == "Left" then
					child.Size = UDim2.new(0, targetSize, 0, CrosshairSettings.Thickness)
					child.Position = UDim2.new(0.5, -(targetGap + targetSize), 0.5, -(CrosshairSettings.Thickness / 2))
				elseif child.Name == "Right" then
					child.Size = UDim2.new(0, targetSize, 0, CrosshairSettings.Thickness)
					child.Position = UDim2.new(0.5, targetGap, 0.5, -(CrosshairSettings.Thickness / 2))
				end
			end
		end)
		table.insert(crosshairElements, dynamicConnection)
	end
end

local function UpdateCrosshair()
	CreateCrosshair()
end

local function FlopAction(actionName, inputState, inputObject)
	if not FlopSettings.Enabled then
		return Enum.ContextActionResult.Pass
	end

	if inputState == Enum.UserInputState.Begin then
		local MyChar = player.Character
		if not MyChar then
			return Enum.ContextActionResult.Pass
		end

		local HumanoidRootPart = MyChar:FindFirstChild("HumanoidRootPart")
		local tempStats = player:FindFirstChild("TempPlayerStatsModule")

		if not HumanoidRootPart or not tempStats then
			return Enum.ContextActionResult.Pass
		end

		local ragdoll = tempStats:FindFirstChild("Ragdoll")
		if not ragdoll or not ragdoll.Value then
			return Enum.ContextActionResult.Pass
		end

		local currentTime = time()
		if currentTime - FlopSettings.LastFlopTime >= FlopSettings.Delay then
			FlopSettings.LastFlopTime = currentTime

			local direction = HumanoidRootPart.CFrame.p - workspace.CurrentCamera.CFrame.p
			local flopVector = Vector3.new(
				direction.X * FlopSettings.XMultiplier,
				direction.Y * FlopSettings.YMultiplier,
				direction.Z * FlopSettings.ZMultiplier
			)

			local RemoteEvent = ReplicatedStorage:FindFirstChild("RemoteEvent")
			if RemoteEvent then
				RemoteEvent:FireServer("Flop", flopVector)
			end
		end
	end

	return Enum.ContextActionResult.Sink
end

local function StartFlopHelper()
	local MyChar = player.Character
	if not MyChar then
		return
	end

	local Humanoid = MyChar:FindFirstChild("Humanoid")
	local tempStats = player:FindFirstChild("TempPlayerStatsModule")

	if not Humanoid or not tempStats then
		return
	end

	local ragdoll = tempStats:FindFirstChild("Ragdoll")

	if FlopSettings.FlopConnection then
		FlopSettings.FlopConnection:Disconnect()
	end

	local function updateFlopBind(isRagdolled)
		if isRagdolled and FlopSettings.Enabled then
			Humanoid:ChangeState(Enum.HumanoidStateType.Physics)
			Humanoid.JumpPower = 0
			player.CameraMinZoomDistance = 2
			task.wait()
			for _, v in pairs(Humanoid:GetPlayingAnimationTracks()) do
				v:AdjustSpeed(0)
			end
			ContextActionService:UnbindAction("Flop")
			ContextActionService:BindAction("Flop", FlopAction, true, Enum.KeyCode.Space, Enum.KeyCode.ButtonA)
			ContextActionService:SetTitle("Flop", "W")
		else
			Humanoid:ChangeState(Enum.HumanoidStateType.GettingUp)
			Humanoid.JumpPower = 36
			player.CameraMinZoomDistance = 0.5
			ContextActionService:UnbindAction("Flop")
		end
	end

	if ragdoll then
		updateFlopBind(ragdoll.Value)
		FlopSettings.FlopConnection = ragdoll.Changed:Connect(updateFlopBind)
	end
end

local function StopFlopHelper()
	if FlopSettings.FlopConnection then
		FlopSettings.FlopConnection:Disconnect()
		FlopSettings.FlopConnection = nil
	end
	ContextActionService:UnbindAction("Flop")

	local MyChar = player.Character
	if MyChar then
		local Humanoid = MyChar:FindFirstChild("Humanoid")
		if Humanoid then
			Humanoid.JumpPower = 36
		end
		player.CameraMinZoomDistance = 0.5
	end
end

local function isPartOfPlayerCharacter(part)
	for _, v in ipairs(Players:GetPlayers()) do
		if v.Character and part:IsDescendantOf(v.Character) then
			return true
		end
	end
	return false
end

local function isExcludedFromBarrier(part)
	local obj = part
	if
		obj.Name == "ComputerTable"
		or obj.Name == "ExitDoor"
		or obj.Name == "SingleDoor"
		or obj.Name == "DoubleDoor"
		or obj.Name == "VentBlock"
		or obj.Name == "InvisibleWall"
		or obj.Name == "OBSpawnPad"
		or obj.Name == "WindowBlock"
		or obj.Name == "FacilitySiren"
	then
		return true
	end
	return false
end

local function EnableWallhops()
	for _, part in ipairs(workspace:GetDescendants()) do
		if
			part:IsA("Part")
			and part.Shape == Enum.PartType.Block
			and part.Transparency ~= 1
			and part.CanCollide
			and not isPartOfPlayerCharacter(part)
			and not part:FindFirstChildOfClass("SelectionBox")
		then
			local selectionBox = Instance.new("SelectionBox")
			selectionBox.Color3 = Color3.fromRGB(255, 255, 255)
			selectionBox.LineThickness = 0.025
			selectionBox.Adornee = part
			selectionBox.Parent = part
			table.insert(WallhopSettings.SelectionBoxes, selectionBox)
		end
	end
end

local function DisableWallhops()
	for _, selectionBox in ipairs(WallhopSettings.SelectionBoxes) do
		if selectionBox and selectionBox.Parent then
			selectionBox:Destroy()
		end
	end
	WallhopSettings.SelectionBoxes = {}
end

local function EnableBarrierVisibility()
	for _, part in ipairs(workspace:GetDescendants()) do
		if
			part:IsA("BasePart")
			and part.Transparency == 1
			and not isPartOfPlayerCharacter(part)
			and not isExcludedFromBarrier(part)
		then
			BarrierSettings.OriginalTransparencies[part] = part.Transparency
			part.Transparency = 0.5
			part.Color = Color3.fromRGB(255, 0, 0)
		end
	end
end

local function DisableBarrierVisibility()
	for part, originalTransparency in pairs(BarrierSettings.OriginalTransparencies) do
		if part and part.Parent then
			part.Transparency = originalTransparency
		end
	end
	BarrierSettings.OriginalTransparencies = {}
end

local function EnableNoFog()
	if not FogSettings.LightingFolder then
		FogSettings.LightingFolder = Instance.new("Folder")
		FogSettings.LightingFolder.Name = "StoredLightingElements"
		FogSettings.LightingFolder.Parent = ReplicatedStorage
	end

	for _, element in ipairs(game.Lighting:GetChildren()) do
		if
			element:IsA("Atmosphere")
			or element:IsA("BloomEffect")
			or element:IsA("BlurEffect")
			or element:IsA("ColorCorrectionEffect")
			or element:IsA("DepthOfFieldEffect")
			or element:IsA("SunRaysEffect")
		then
			element.Parent = FogSettings.LightingFolder
		end
	end

	game.Lighting.FogEnd = 100000
	game.Lighting.TimeOfDay = "21:00:00"
end

local function DisableNoFog()
	if FogSettings.LightingFolder then
		for _, element in ipairs(FogSettings.LightingFolder:GetChildren()) do
			element.Parent = game.Lighting
		end
	end

	game.Lighting.TimeOfDay = "14:00:00"
end

local function DisableBushes()
	for i = #BushSettings.Cached, 1, -1 do
		local v = BushSettings.Cached[i]
		if v and v.Parent then
			v.Transparency = 0
		end
		table.remove(BushSettings.Cached, i)
	end
end

local function EnableBushes()
	for _, v in ipairs(game.Workspace:GetDescendants()) do
		if v:IsA("BasePart") then
			if
				getIsTreeBush(v.Size)
				and v.Transparency == 0
				and v.CanCollide == false
				and v.Material == Enum.Material.Grass
			then
				v.Transparency = 1
				table.insert(BushSettings.Cached, v)
			end
		end
	end
end

local function DisableShadows()
	ShadowSettings.OriginalState = Lighting.GlobalShadows
	Lighting.GlobalShadows = false
end

local function MonitorRopedPlayers()
	local ropedPlayer = GetRopedPlayer()

	for plr, wasRoped in pairs(TrollSettings.RopedPlayers) do
		if ropedPlayer ~= plr then
			TrollSettings.RopedPlayers[plr] = false
		end
	end

	if ropedPlayer then
		TrollSettings.RopedPlayers[ropedPlayer] = true
	end
end

local function MonitorRopedPlayersHelper()
	local ropedPlayer = GetRopedPlayer()

	for plr, _ in pairs(RopeHelperSettings.RopedPlayers) do
		if ropedPlayer ~= plr then
			RopeHelperSettings.RopedPlayers[plr] = nil
		end
	end

	if ropedPlayer then
		RopeHelperSettings.RopedPlayers[ropedPlayer] = true
	end
end

local function EnableShadows()
	Lighting.GlobalShadows = ShadowSettings.OriginalState
end

local function TeleportToPlayer(TargetPlayer)
	local TargetChar = TargetPlayer.Character
	if not TargetChar then
		return
	end
	local HRP = TargetChar:FindFirstChild("HumanoidRootPart")
	if not HRP then
		return
	end
	local MyChar = player.Character
	if not MyChar then
		return
	end
	local newCFrame = HRP:GetPivot()
	newCFrame = newCFrame + Vector3.new(2, 0, 0)
	MyChar:PivotTo(newCFrame)
end

local function Interact(State)
	local re = ReplicatedStorage:WaitForChild("RemoteEvent")
	re:FireServer("Input", "Trigger", State)
end

local function DoAction(State)
	local re = ReplicatedStorage:WaitForChild("RemoteEvent")
	re:FireServer("Input", "Action", State)
end

local function GoToPod()
	local currmap = getmap()
	if not currmap then
		return
	end
	local MyChar = player.Character
	if not MyChar then
		return
	end
	for _, v in ipairs(currmap:GetDescendants()) do
		if v.Name == "FreezePod" then
			local trigger = v:FindFirstChild("PodTrigger")
			if trigger and trigger:FindFirstChild("CapturedTorso").Value == false then
				MyChar:PivotTo(trigger:GetPivot())
				task.wait(0.3)
				Interact(true)
				return
			end
		end
	end
end

local function GoToPc()
	local currmap = getmap()
	if not currmap then
		return
	end
	local MyChar = player.Character
	if not MyChar then
		return
	end
	local bestPC = nil

	for _, pc in ipairs(currmap:GetDescendants()) do
		if pc.Name == "ComputerTable" then
			local pcData = objectProgress.computers[pc]
			if AutoFarmSettings.GotoComputersWithMostProg and pcData then
				if not bestPC or pcData.progress > objectProgress.computers[bestPC].progress then
					bestPC = pc
				end
			elseif not AutoFarmSettings.GotoComputersWithMostProg then
				bestPC = pc
				break
			end
		end
	end

	if not bestPC then
		return
	end

	for _, trigger in ipairs(bestPC:GetChildren()) do
		if string.find(string.lower(trigger.Name), "computertrigger") and trigger:FindFirstChild("ActionSign") then
			if trigger.ActionSign.Value ~= 20 then
				continue
			end

			local beast = GetBeast()
			if beast and beast:FindFirstChild("HumanoidRootPart") then
				local dist = getDistance(MyChar:FindFirstChild("HumanoidRootPart"), beast.HumanoidRootPart)
				if dist < 15 then
					continue
				end
			end

			MyChar:PivotTo(trigger:GetPivot())
			task.wait(5)
			DoAction(true)
			return
		end
	end

	for _, pc in ipairs(currmap:GetDescendants()) do
		if pc.Name == "ComputerTable" and pc ~= bestPC then
			GoToPc()
		end
	end
end

local function RestartInteraction()
	local char = player.Character
	if not char then
		return
	end
	local humanoid = char:FindFirstChild("Humanoid")
	if humanoid then
		humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
	end
	DoAction(true)
end

local function StartAutoFarm()
	if AutoFarmSettings.DistanceConnection then
		task.cancel(AutoFarmSettings.DistanceConnection)
		AutoFarmSettings.DistanceConnection = nil
	end

	if not AutoFarmSettings.Enabled then
		return
	end

	AutoFarmSettings.DistanceConnection = task.spawn(function()
		while AutoFarmSettings.Enabled do
			task.wait(0.5)

			local beast = GetBeast()
			if not beast then
				continue
			end

			if beast == player.Character then
				for _, v in ipairs(Players:GetPlayers()) do
					if v == player then
						continue
					end
					if not AutoFarmSettings.Enabled then
						break
					end

					local isHit = false
					repeat
						if not AutoFarmSettings.Enabled or not canPerformAction() then
							break
						end
						if canTeleport() then
							TeleportToPlayer(v)
						end
						HitPlayer(v)
						task.wait(0.3)
						isHit = IsHit(v)
					until isHit or not AutoFarmSettings.Enabled

					if not AutoFarmSettings.Enabled then
						break
					end

					repeat
						if not AutoFarmSettings.Enabled or not canPerformAction() then
							break
						end
						local currentlyRoped = GetRopedPlayer()
						if not currentlyRoped or currentlyRoped ~= v then
							AutoRopePlayer(v)
						end
						task.wait(0.3)
					until GetRopedPlayer() == v or not AutoFarmSettings.Enabled

					if not AutoFarmSettings.Enabled then
						break
					end

					local isCaptured = false
					repeat
						if not AutoFarmSettings.Enabled or not canPerformAction() then
							break
						end
						if canTeleport() then
							GoToPod()
						end
						task.wait(0.3)
						isCaptured = IsCaptured(v)
					until isCaptured or not AutoFarmSettings.Enabled
				end
			elseif AutoFarmSettings.FarmAsSurvivor then
				while AutoFarmSettings.Enabled and GetBeast() ~= player.Character do
					task.wait(0.5)

					local gameStatus = ReplicatedStorage:FindFirstChild("GameStatus")
					if gameStatus and gameStatus.Value == "FIND AN EXIT" then
						if not canPerformAction() then
							continue
						end

						local tempStats = player:FindFirstChild("TempPlayerStatsModule")
						if tempStats then
							local escaped = tempStats:FindFirstChild("Escaped")
							if not escaped or not escaped.Value then
								local currmap = getmap()
								if currmap then
									for _, exit in ipairs(currmap:GetDescendants()) do
										if exit.Name == "ExitDoor" then
											local trigger = exit:FindFirstChild("ExitDoorTrigger")
												or exit:FindFirstChild("Trigger")
											if trigger and canTeleport() then
												local MyChar = player.Character
												if MyChar then
													MyChar:PivotTo(trigger:GetPivot())
													task.wait(0.3)
													Interact(true)
													DoAction(true)
													task.wait(0.5)

													local actionSign = trigger:FindFirstChild("ActionSign")
													if actionSign and actionSign.Value == 11 then
														for i = 1, 20 do
															if not AutoFarmSettings.Enabled then
																break
															end
															local offset = Vector3.new(
																math.random(-10, 10),
																0,
																math.random(-10, 10)
															)
															MyChar:PivotTo(trigger:GetPivot() + offset)
															task.wait(0.1)
															if escaped and escaped.Value then
																break
															end
														end
													end
												end
												break
											end
										end
									end
								end
							end
						end
					else
						if not canPerformAction() then
							continue
						end

						local beastChar = beast
						local beastHrp = beastChar and beastChar:FindFirstChild("HumanoidRootPart")
						local myChar = player.Character
						local myHrp = myChar and myChar:FindFirstChild("HumanoidRootPart")

						if myHrp and beastHrp then
							local distance = (myHrp.Position - beastHrp.Position).Magnitude
							if distance < 30 and canTeleport() then
								local awayPos = myHrp.Position + (myHrp.Position - beastHrp.Position).Unit * 50
								myChar:PivotTo(CFrame.new(awayPos))
								task.wait(0.5)
								continue
							end
						end

						local bestPC = nil
						local highestProgress = -1

						for pc, pcData in pairs(objectProgress.computers) do
							if pc.Parent and pcData.progress < 1 then
								if AutoFarmSettings.GotoComputersWithMostProg then
									if pcData.progress > highestProgress then
										highestProgress = pcData.progress
										bestPC = pc
									end
								else
									bestPC = pc
									break
								end
							end
						end

						if bestPC and canTeleport() then
							for _, trigger in ipairs(bestPC:GetChildren()) do
								if
									string.find(string.lower(trigger.Name), "computertrigger")
									and trigger:FindFirstChild("ActionSign")
								then
									if trigger.ActionSign.Value ~= 20 then
										continue
									end

									if beastHrp then
										local dist = getDistance(myHrp, beastHrp)
										if dist < 30 then
											local awayPos = myHrp.Position
												+ (myHrp.Position - beastHrp.Position).Unit * 50
											myChar:PivotTo(CFrame.new(awayPos))
											task.wait(0.5)
											break
										end
									end

									myChar:PivotTo(trigger:GetPivot())
									task.wait(0.3)
									DoAction(true)

									local startTime = tick()
									while tick() - startTime < 5 and AutoFarmSettings.Enabled do
										DoAction(true)
										task.wait(0.1)
										if beastHrp then
											local dist = getDistance(myHrp, beastHrp)
											if dist < 30 then
												break
											end
										end
									end
									break
								end
							end
						end
					end
				end
			end
		end
	end)
end

local function DisableAutoFarm()
	AutoFarmSettings.Enabled = false
	if AutoFarmSettings.DistanceConnection then
		task.cancel(AutoFarmSettings.DistanceConnection)
		AutoFarmSettings.DistanceConnection = nil
	end
end

local function GiveFatigue()
	local beast = GetBeast()
	if not beast then
		return
	end

	local beastpowers = beast:FindFirstChild("BeastPowers")
	if not beastpowers then
		return
	end

	local Remote = beastpowers:FindFirstChild("PowersEvent")
	if Remote then
		Remote:FireServer("Jumped")
	end
end

local function UseBeastAbility()
	local beast = GetBeast()
	if not beast then
		return
	end

	local beastpowers = beast:FindFirstChild("BeastPowers")
	if not beastpowers then
		return
	end

	local Remote = beastpowers:FindFirstChild("PowersEvent")
	if Remote then
		Remote:FireServer("Input")
	end
end

local function UnropePlayer()
	local beast = GetBeast()
	if not beast then
		return
	end

	local Hammer = beast:FindFirstChild("Hammer")
	if not Hammer then
		return
	end

	local HammerEvent = Hammer:FindFirstChild("HammerEvent")
	HammerEvent:FireServer("HammerClick", true)
end

local function StartAutoFatigue()
	if TrollSettings.AutoFatigue.Connection then
		TrollSettings.AutoFatigue.Connection:Disconnect()
	end

	TrollSettings.AutoFatigue.Connection = task.spawn(function()
		while TrollSettings.AutoFatigue.Enabled do
			GiveFatigue()
			task.wait(TrollSettings.AutoFatigue.Interval)
		end
	end)
end

local function StartAutoAbility()
	if TrollSettings.AutoAbility.Connection then
		TrollSettings.AutoAbility.Connection:Disconnect()
	end

	TrollSettings.AutoAbility.Connection = task.spawn(function()
		while TrollSettings.AutoAbility.Enabled do
			UseBeastAbility()
			task.wait(TrollSettings.AutoAbility.Interval)
		end
	end)
end

local function StartAutoUnrope()
	if TrollSettings.AutoUnrope.Connection then
		TrollSettings.AutoUnrope.Connection:Disconnect()
	end

	TrollSettings.AutoUnrope.Connection = RunService.Heartbeat:Connect(function()
		if not TrollSettings.AutoUnrope.Enabled then
			return
		end

		UnropePlayer()
	end)
end

AutoSaveConn = task.spawn(function()
	while task.wait(0.2) do
		if AutoFarmSettings.Enabled and AutoFarmSettings.AutoSave then
			local MyChar = player.Character
			if MyChar and IsCaptured(player) then
				GoToPod()
			end
		end
	end
end)

local function trackPlayer(plr)
	local function applyEsp()
		local char = plr.Character
		if not char or not char:FindFirstChild("HumanoidRootPart") then
			return
		end

		if not Settings.EspSettings.PlayerEsp.Enabled then
			return
		end

		if Settings.EspSettings.PlayerEsp.UseSkeletonEsp then
			createSkeletonUI(char)
		elseif Settings.EspSettings.PlayerEsp.UseBoxEsp then
			createBoxUI(char)
		else
			AddPlayerEsp(char)
		end

		if Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.Enabled then
			CreateWalkspeedUI(char)
		end
	end

	local conn = plr.CharacterAdded:Connect(function(char)
		char:WaitForChild("HumanoidRootPart")
		task.wait(0.1)
		applyEsp()

		if Settings.GadgetSettings.ProgressSettings.HealthTimer.Enabled then
			SetupHealthTracking(plr)
		end

		if plr == player and FlopSettings.Enabled then
			task.wait(0.5)
			StartFlopHelper()
		end
	end)

	if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
		task.wait(0.1)
		applyEsp()

		if Settings.GadgetSettings.ProgressSettings.HealthTimer.Enabled then
			SetupHealthTracking(plr)
		end

		if plr == player and FlopSettings.Enabled then
			StartFlopHelper()
		end
	end

	PlayerConnections.EspConnections[plr] = conn
end

local function untrackPlayer(plr)
	if plr.Character then
		removeSkeletonUI(plr.Character)
		removeBoxUI(plr.Character)
		RemovePlayerEsp(plr.Character)
		RemoveWalkspeedUI(plr.Character)
	end
	local conn = PlayerConnections.EspConnections[plr]
	if conn then
		conn:Disconnect()
		PlayerConnections.EspConnections[plr] = nil
	end
end

local function CleanupMapEsp()
	StopPcEsp()
	StopTubeEsp()
	StopExitEsp()
end

local function RopeNearestRagdolled(mousePosition)
	local nearestPlayer = nil
	local shortestDistance = math.huge

	for _, plr in pairs(Players:GetPlayers()) do
		if plr ~= player and plr.Character then
			local hrp = plr.Character:FindFirstChild("HumanoidRootPart")
			local tempStats = plr:FindFirstChild("TempPlayerStatsModule")

			if hrp and tempStats then
				local ragdoll = tempStats:FindFirstChild("Ragdoll")
				if ragdoll and ragdoll.Value then
					local screenPos, onScreen = camera:WorldToViewportPoint(hrp.Position)
					if onScreen then
						local distance = (Vector2.new(screenPos.X, screenPos.Y) - mousePosition).Magnitude
						if distance < shortestDistance and distance < 200 then
							shortestDistance = distance
							nearestPlayer = plr
						end
					end
				end
			end
		end
	end

	if nearestPlayer then
		local myChar = player.Character
		local myHrp = myChar and myChar:FindFirstChild("HumanoidRootPart")
		local targetHrp = nearestPlayer.Character and nearestPlayer.Character:FindFirstChild("HumanoidRootPart")

		if myHrp and targetHrp then
			local distance = (myHrp.Position - targetHrp.Position).Magnitude
			if distance <= RopeHelperSettings.MaxDistance then
				AutoRopePlayer(nearestPlayer)
			end
		end
	end
end
ConnectionManager:AddGlobal(
	"RopeHelperClick",
	UserInputService.InputBegan:Connect(function(input, gameProcessed)
		if gameProcessed then
			return
		end
		if
			input.UserInputType == Enum.UserInputType.MouseButton1
			and RopeHelperSettings.ClickToRope
			and RopeHelperSettings.Enabled
		then
			local mousePos = UserInputService:GetMouseLocation()
			RopeNearestRagdolled(mousePos)
		end
	end)
)
local function StartSpectating(targetPlayer)
	if SpectateSettings.ViewDied then
		SpectateSettings.ViewDied:Disconnect()
	end
	if SpectateSettings.ViewChanged then
		SpectateSettings.ViewChanged:Disconnect()
	end

	if not targetPlayer or not targetPlayer.Character then
		return
	end

	SpectateSettings.TargetPlayer = targetPlayer

	local function updateCamera()
		if targetPlayer.Character and targetPlayer.Character:FindFirstChild("HumanoidRootPart") then
			workspace.CurrentCamera.CameraSubject = targetPlayer.Character:FindFirstChild("Humanoid")
			workspace.CurrentCamera.CFrame = targetPlayer.Character.HumanoidRootPart.CFrame
		end
	end

	updateCamera()

	SpectateSettings.ViewDied = targetPlayer.CharacterAdded:Connect(function(character)
		repeat
			task.wait()
		until character:FindFirstChild("HumanoidRootPart") and character:FindFirstChild("Humanoid")
		updateCamera()
	end)

	SpectateSettings.ViewChanged = workspace.CurrentCamera:GetPropertyChangedSignal("CameraSubject"):Connect(function()
		if SpectateSettings.Enabled and SpectateSettings.TargetPlayer then
			task.wait()
			updateCamera()
		end
	end)
end

local function StopSpectating()
	SpectateSettings.Enabled = false
	SpectateSettings.TargetPlayer = nil

	if SpectateSettings.ViewDied then
		SpectateSettings.ViewDied:Disconnect()
		SpectateSettings.ViewDied = nil
	end
	if SpectateSettings.ViewChanged then
		SpectateSettings.ViewChanged:Disconnect()
		SpectateSettings.ViewChanged = nil
	end

	workspace.CurrentCamera.CameraSubject = player.Character
end

conn2 = Players.PlayerRemoving:Connect(function(p)
	NameHiderSettings.CustomPlayers[p.Name] = nil
	for obj in pairs(NameHiderSettings.TextObjectCache) do
		replaceInObject(obj)
	end
end)

local function formatChatMessage(msg, plr)
	if not NameHiderSettings.Enabled then
		return msg
	end
	local newName, _, _, tag, tagColor = getPlayerData(plr.Name)
	if not newName then
		return msg
	end
	local m = msg
	if tag and tagColor then
		local col = tagColor:gsub("#", "")
		m = string.format("<font color='#%s'>[%s]</font> %s", col, tag, m)
	end
	return m
end

gameactivechanged = game.ReplicatedStorage.IsGameActive.Changed:Connect(function()
	UpdatePlayerEsp()
	if game.ReplicatedStorage.IsGameActive.Value == true then
		task.wait(1)
		StopRunnerTimer()
		StartRunnerTimer()

		if Settings.EspSettings.PcEsp.Enabled then
			StartPcEsp()
		end
		if Settings.EspSettings.TubeEsp.Enabled then
			StartTubeEsp()
		end
		if Settings.EspSettings.ExitEsp.Enabled then
			StartExitEsp()
		end
		if Settings.EspSettings.DoorEsp.Enabled then
			DoorEsp()
		end
	end
	if Settings.GadgetSettings.ProgressSettings.HealthTimer.Enabled then
		DisableHealthTimer()
		EnableHealthTimer()
	end
	UpdateAllCameras()
end)

mapchanged = game.ReplicatedStorage.CurrentMap.Changed:Connect(function()
	cleanupAllProgressUIs()

	task.wait(2)

	StopRunnerTimer()
	StartRunnerTimer()

	if Settings.EspSettings.PcEsp.Enabled then
		StartPcEsp()
	end
	if Settings.EspSettings.TubeEsp.Enabled then
		StartTubeEsp()
	end
	if Settings.EspSettings.ExitEsp.Enabled then
		StartExitEsp()
	end
	if Settings.EspSettings.DoorEsp.Enabled then
		DoorEsp()
	end

	if Settings.GadgetSettings.ProgressSettings.HealthTimer.Enabled then
		DisableHealthTimer()
		EnableHealthTimer()
	end

	if BarrierSettings.Enabled then
		DisableBarrierVisibility()
		EnableBarrierVisibility()
	end

	if WallhopSettings.Enabled then
		DisableWallhops()
		EnableWallhops()
	end

	if BushSettings.Enabled then
		DisableBushes()
		EnableBushes()
	end

	UpdateAllCameras()
end)
if game.ReplicatedStorage.IsGameActive.Value == true then
	determinestuff()

	if Settings.EspSettings.PcEsp.Enabled then
		StartPcEsp()
	end
	if Settings.EspSettings.TubeEsp.Enabled then
		StartTubeEsp()
	end
	if Settings.EspSettings.ExitEsp.Enabled then
		StartExitEsp()
	end
	if Settings.EspSettings.DoorEsp.Enabled then
		DoorEsp()
	end
end

if getmap() then
	task.wait(2)
	determinestuff()
end

PlayerConnections.GameStartingConnection = game:GetService("ReplicatedStorage").GameStatus
	:GetPropertyChangedSignal("Value")
	:Connect(function()
		if game:GetService("ReplicatedStorage").GameStatus.Value == "GAME STARTING" then
			task.wait(2)
			CleanupMapEsp()
			if Settings.EspSettings.PcEsp.Enabled then
				StartPcEsp()
			end
			if Settings.EspSettings.TubeEsp.Enabled then
				StartTubeEsp()
			end
			if Settings.EspSettings.ExitEsp.Enabled then
				StartExitEsp()
			end
			if Settings.EspSettings.DoorEsp.Enabled then
				DoorEsp()
			end
			determinestuff()
			UpdateAllCameras()
		end

		if game:GetService("ReplicatedStorage").GameStatus.Value == "15 SEC HEAD START" then
			task.wait(0.5)
			if Settings.EspSettings.PcEsp.Enabled then
				StartPcEsp()
			end
			if Settings.EspSettings.TubeEsp.Enabled then
				StartTubeEsp()
			end
			if Settings.EspSettings.ExitEsp.Enabled then
				StartExitEsp()
			end
			if Settings.EspSettings.DoorEsp.Enabled then
				DoorEsp()
			end
			StartHeadstartTracking()
			UpdateAllCameras()
		end
	end)

PcEspToggle = Groupboxes.Visual.LeftGroupBox:AddToggle("PcEsp", {
	Text = "Computer ESP",
	Default = false,
	Tooltip = "Highlight computers with color based on status",
	Callback = function(Value)
		Settings.EspSettings.PcEsp.Enabled = Value
		if Value then
			StartPcEsp()
		else
			StopPcEsp()
		end
	end,
})

TubeEspToggle = Groupboxes.Visual.LeftGroupBox:AddToggle("TubeEsp", {
	Text = "Tube ESP",
	Default = false,
	Tooltip = "Highlights tubes",
	Callback = function(Value)
		Settings.EspSettings.TubeEsp.Enabled = Value
		if Value then
			StartTubeEsp()
		else
			StopTubeEsp()
		end
	end,
})

DoorEspToggle = Groupboxes.Visual.LeftGroupBox:AddToggle("DoorEsp", {
	Text = "Door Esp",
	Default = false,
	Tooltip = "Adds highlights on doors",
	Callback = function(Value)
		Settings.EspSettings.DoorEsp.Enabled = Value
		if Value then
			DoorEsp()
		else
			StopDoorEsp()
		end
	end,
})

SpectateTab = Tabs.Crosshair:AddRightGroupbox("Spectate")

SpectateTab:AddToggle("EnableSpectate", {
	Text = "Enable Spectate",
	Default = false,
	Callback = function(Value)
		SpectateSettings.Enabled = Value
		if Value and SpectateSettings.TargetPlayer then
			StartSpectating(SpectateSettings.TargetPlayer)
		else
			StopSpectating()
		end
	end,
})

spectatePlayerNames = {}
for _, plr in pairs(Players:GetPlayers()) do
	table.insert(spectatePlayerNames, plr.Name)
end

SpectateTab:AddDropdown("SpectateTarget", {
	Values = spectatePlayerNames,
	Default = "",
	Text = "Select Player",
	Callback = function(Value)
		if Value ~= "" then
			local targetPlayer = Players:FindFirstChild(Value)
			SpectateSettings.TargetPlayer = targetPlayer
			if SpectateSettings.Enabled and targetPlayer then
				StartSpectating(targetPlayer)
			end
		end
	end,
})

conn3 = Players.PlayerAdded:Connect(function(newPlayer)
	if newPlayer ~= player and Options.SpectateTarget then
		local values = Options.SpectateTarget.Values
		table.insert(values, newPlayer.Name)
		Options.SpectateTarget:SetValues(values)
	end
end)

conn4 = Players.PlayerRemoving:Connect(function(removingPlayer)
	if removingPlayer ~= player and Options.SpectateTarget then
		local values = Options.SpectateTarget.Values
		local index = table.find(values, removingPlayer.Name)
		if index then
			table.remove(values, index)
			Options.SpectateTarget:SetValues(values)
		end

		if SpectateSettings.TargetPlayer == removingPlayer then
			StopSpectating()
		end
	end
end)

NameHiderTab = Tabs["Crosshair"]:AddRightTabbox("Name Hider")
MyNameTab = NameHiderTab:AddTab("My Settings")
MyNameTab:AddDivider()
OthersTab = NameHiderTab:AddTab("Other Players")

MyNameTab:AddToggle("EnableNameHider", {
	Text = "Enable Name Hider",
	Default = false,
	Tooltip = "Hide/change your name and other players",
	Callback = function(Value)
		if Value then
			StartNameHider()
		else
			StopNameHider()
		end
	end,
})

MyNameTab:AddInput("MyCustomName", {
	Default = player.Name,
	Text = "Your Display Name",
	Tooltip = "Name shown to you",
	Callback = function(Value)
		NameHiderSettings.MyName = Value == "" and player.Name or Value
	end,
})
MyNameTab:AddInput("MyCustomLevel", {
	Default = "",
	Numeric = true,
	Text = "Your Display Level",
	Tooltip = "Level shown to you",
	Callback = function(Value)
		NameHiderSettings.MyLevel = tonumber(Value)
	end,
})

MyNameTab:AddDropdown("MyRankTag", {
	Values = RankList,
	Default = "None",
	Text = "Your Rank Tag",
	Callback = function(Value)
		if Value == "None" then
			NameHiderSettings.MyTag = nil
			NameHiderSettings.MyTagColor = nil
			NameHiderSettings.MyIcon = nil
		else
			NameHiderSettings.MyTag = Value
			NameHiderSettings.MyTagColor = RankData[Value].Color
			NameHiderSettings.MyIcon = RankData[Value].Icon
		end
	end,
})
MyNameTab:AddInput("MyCustomIcon", {
	Default = "",
	Text = "Custom Icon ID",
	Tooltip = "rbxassetid://... for custom icon",
	Callback = function(Value)
		if Value ~= "" and string.find(Value, "rbxassetid://") then
			NameHiderSettings.MyIcon = Value
		end
	end,
})

MyNameTab:AddDivider()
MyNameTab:AddLabel("Avatar Changer")

MyNameTab:AddInput("MyAvatarTarget", {
	Default = "",
	Text = "Username or UserID",
	Tooltip = "Player to copy avatar from",
})

MyNameTab:AddButton("Apply Avatar to Myself", function()
	local target = Options.MyAvatarTarget.Value
	if target and target ~= "" then
		applyavatar(player.Name, target)
	else
		Library:Notify("Please enter a username or UserID", 3)
	end
end)

MyNameTab:AddButton("Reset My Avatar", function()
	if player.Character then
		player.Character:BreakJoints()
	end
end)

selectedPlayer = nil

OthersTab:AddDropdown("SelectPlayer", {
	Values = (function()
		local names = {}
		for _, plr in ipairs(Players:GetPlayers()) do
			if plr ~= player then
				table.insert(names, plr.Name)
			end
		end
		return names
	end)(),
	Default = "",
	Text = "Select Player",
	Callback = function(Value)
		selectedPlayer = Value
	end,
})

OthersTab:AddInput("OtherCustomName", {
	Default = "",
	Text = "Their Display Name",
	Callback = function(Value)
		if not selectedPlayer or selectedPlayer == "" then
			return
		end
		if not NameHiderSettings.CustomPlayers[selectedPlayer] then
			NameHiderSettings.CustomPlayers[selectedPlayer] = {}
		end
		NameHiderSettings.CustomPlayers[selectedPlayer].Name = Value == "" and selectedPlayer or Value
	end,
})
OthersTab:AddInput("OtherCustomLevel", {
	Default = "",
	Numeric = true,
	Text = "Their Display Level",
	Callback = function(Value)
		if not selectedPlayer or selectedPlayer == "" then
			return
		end
		if not NameHiderSettings.CustomPlayers[selectedPlayer] then
			NameHiderSettings.CustomPlayers[selectedPlayer] = {}
		end
		NameHiderSettings.CustomPlayers[selectedPlayer].Level = tonumber(Value)
	end,
})

OthersTab:AddDropdown("OtherRankTag", {
	Values = RankList,
	Default = "None",
	Text = "Their Rank Tag",
	Callback = function(Value)
		if not selectedPlayer or selectedPlayer == "" then
			return
		end

		if not NameHiderSettings.CustomPlayers[selectedPlayer] then
			NameHiderSettings.CustomPlayers[selectedPlayer] = {}
		end

		if Value == "None" then
			NameHiderSettings.CustomPlayers[selectedPlayer].Tag = nil
			NameHiderSettings.CustomPlayers[selectedPlayer].TagColor = nil
			NameHiderSettings.CustomPlayers[selectedPlayer].Icon = nil
		else
			NameHiderSettings.CustomPlayers[selectedPlayer].Tag = Value
			NameHiderSettings.CustomPlayers[selectedPlayer].TagColor = RankData[Value].Color
			NameHiderSettings.CustomPlayers[selectedPlayer].Icon = RankData[Value].Icon
		end
	end,
})

OthersTab:AddDivider()
OthersTab:AddLabel("Avatar Changer")

OthersTab:AddInput("OtherAvatarTarget", {
	Default = "",
	Text = "Avatar Username/UserID",
	Tooltip = "Player to copy avatar from",
})

OthersTab:AddButton("Apply Avatar to Selected", function()
	if not selectedPlayer or selectedPlayer == "" then
		Library:Notify("Please select a player first", 3)
		return
	end

	local avatarTarget = Options.OtherAvatarTarget.Value
	if avatarTarget and avatarTarget ~= "" then
		applyavatar(selectedPlayer, avatarTarget)
	else
		Library:Notify("Please enter a username or UserID", 3)
	end
end)

OthersTab:AddButton("Reset Selected Player Avatar", function()
	if not selectedPlayer or selectedPlayer == "" then
		Library:Notify("Please select a player first", 3)
		return
	end

	local targetPlayer = Players:FindFirstChild(selectedPlayer)
	if targetPlayer and targetPlayer.Character then
		targetPlayer.Character:BreakJoints()
	end
end)

OthersTab:AddButton("Clear Player Settings", function()
	if selectedPlayer and selectedPlayer ~= "" then
		NameHiderSettings.CustomPlayers[selectedPlayer] = nil
		Library:Notify("Cleared settings for " .. selectedPlayer, 3)
	end
end)

conn5 = Players.PlayerAdded:Connect(function(newPlayer)
	if Options.SelectPlayer then
		local values = Options.SelectPlayer.Values
		table.insert(values, newPlayer.Name)
		Options.SelectPlayer:SetValues(values)
	end
end)

conn6 = Players.PlayerRemoving:Connect(function(removingPlayer)
	if Options.SelectPlayer then
		local values = Options.SelectPlayer.Values
		local index = table.find(values, removingPlayer.Name)
		if index then
			table.remove(values, index)
			Options.SelectPlayer:SetValues(values)
		end
	end
	NameHiderSettings.CustomPlayers[removingPlayer.Name] = nil
end)

BeastChanceSnitch = Tabs["Crosshair"]:AddRightGroupbox("Beast Chances")
BeastChanceLabels = {}

local function UpdateBeastLabel(plr)
	local savedStats = plr:FindFirstChild("SavedPlayerStatsModule")
	if not savedStats then
		return
	end

	local beastChance = savedStats:FindFirstChild("BeastChance")
	if not beastChance then
		return
	end

	if not BeastChanceLabels[plr] then
		local label = BeastChanceSnitch:AddLabel(string.format("%s: %.1f%%", plr.Name, beastChance.Value))
		BeastChanceLabels[plr] = {
			Label = label,
			BeastChance = beastChance,
		}
	else
		BeastChanceLabels[plr].Label:SetText(string.format("%s: %.1f%%", plr.Name, beastChance.Value))
	end
end

local function RemoveBeastLabel(plr)
	if BeastChanceLabels[plr] then
		BeastChanceSnitch:RemoveLabel(BeastChanceLabels[plr].Label)
		BeastChanceLabels[plr] = nil
	end
end

BeastChanceTracker = RunService.Heartbeat:Connect(function()
	for _, plr in ipairs(Players:GetPlayers()) do
		UpdateBeastLabel(plr)
	end

	if Settings.EspSettings.PlayerEsp.UseRainbowEsp then
		UpdatePlayerEsp()
	end
end)

conn14 = Players.PlayerAdded:Connect(function(plr)
	plr.CharacterAdded:Connect(function()
		task.wait(0.5)
		UpdateBeastLabel(plr)
		Add3DBoxEsp(char)
	end)
end)

conn15 = Players.PlayerRemoving:Connect(RemoveBeastLabel)
PlayerEspToggle = Groupboxes.Visual.RightGroupBox:AddToggle("PlayerEsp", {
	Text = "Player ESP",
	Default = false,
	Tooltip = "Toggle player ESP",
	Callback = function(Value)
		Settings.EspSettings.PlayerEsp.Enabled = Value
		if Settings.EspSettings.PlayerEsp.UseSkeletonEsp or Settings.EspSettings.PlayerEsp.UseBoxEsp then
			for _, v in Players:GetPlayers() do
				if v.Character then
					RemovePlayerEsp(v.Character)
				end
			end
			return
		end
		if Value then
			for _, v in Players:GetPlayers() do
				if v ~= player and v.Character then
					AddPlayerEsp(v.Character)
				end
			end
		else
			for _, v in Players:GetPlayers() do
				if v.Character then
					RemovePlayerEsp(v.Character)
				end
			end
		end
	end,
})

UseCloneEspToggle = Groupboxes.Visual.RightGroupBox:AddToggle("UseCloneEsp", {
	Text = "Clone ESP Mode",
	Default = false,
	Tooltip = "Use this to hide hitbox extender",
	Callback = function(Value)
		Settings.EspSettings.PlayerEsp.UseCloneEsp = Value
		if Settings.EspSettings.PlayerEsp.UseSkeletonEsp or Settings.EspSettings.PlayerEsp.UseBoxEsp then
			return
		end
		if Settings.EspSettings.PlayerEsp.Enabled then
			ReloadPlayerEsp()
		end
	end,
})

SkeletonEspToggle = Groupboxes.Visual.RightGroupBox:AddToggle("SkeletonEsp", {
	Text = "Skeleton ESP",
	Default = false,
	Tooltip = "Eric esp",
	Callback = function(Value)
		Settings.EspSettings.PlayerEsp.UseSkeletonEsp = Value
		if Value then
			stopBoxEsp()
			ReloadPlayerEsp()
			startSkeleton()
		else
			stopSkeletonEsp()
			ReloadPlayerEsp()
		end
	end,
})

BoxEspToggle = Groupboxes.Visual.RightGroupBox:AddToggle("BoxEsp", {
	Text = "Box ESP",
	Default = false,
	Tooltip = "2D Box ESP",
	Callback = function(Value)
		Settings.EspSettings.PlayerEsp.UseBoxEsp = Value
		if Value then
			stopSkeletonEsp()
			ReloadPlayerEsp()
			startBoxEsp()
		else
			stopBoxEsp()
			ReloadPlayerEsp()
		end
	end,
})

ThreeDBoxToggle = Groupboxes.Visual.RightGroupBox:AddToggle("ThreeDBoxEsp", {
	Text = "3D Box ESP",
	Default = false,
	Tooltip = "3D box around players",
	Callback = function(Value)
		Settings.EspSettings.PlayerEsp.d3esp.Enabled = Value
		if Value then
			stopSkeletonEsp()
			stopBoxEsp()
			ReloadPlayerEsp()
			for _, plr in pairs(Players:GetPlayers()) do
				if plr ~= player and plr.Character then
					Add3DBoxEsp(plr.Character)
				end
			end
		else
			for _, plr in pairs(Players:GetPlayers()) do
				if plr.Character then
					Remove3DBoxEsp(plr.Character)
				end
			end
			ReloadPlayerEsp()
		end
	end,
})

TracersToggle = Groupboxes.Visual.RightGroupBox:AddToggle("Tracers", {
	Text = "Tracers",
	Default = false,
	Tooltip = "draw lines to players",
	Callback = function(Value)
		Settings.EspSettings.PlayerEsp.TracerSettings.Enabled = Value
		if Value then
			startTracers()
		else
			stopTracers()
		end
	end,
})

SurvivorFillPicker =
	Groupboxes.EspCustomization.PlayerEsp:AddLabel("Survivor Fil"):AddColorPicker("SurvivorFillPicker", {
		Default = Settings.EspSettings.PlayerEsp.SurvivorFillColor,
		Title = "Adjust Survivor Fill",
		Transparency = Settings.EspSettings.PlayerEsp.SurvivorFillTransparancy,
		Callback = function(value)
			Settings.EspSettings.PlayerEsp.SurvivorFillColor = value
			Settings.EspSettings.PlayerEsp.SurvivorFillTransparancy = Options.SurvivorFillPicker.Transparency
			UpdatePlayerEsp()
		end,
	})

SurvivorOutlinePicker =
	Groupboxes.EspCustomization.PlayerEsp:AddLabel("Survivor Outline"):AddColorPicker("SurvivorOutlinePicker", {
		Default = Settings.EspSettings.PlayerEsp.SurvivorOutlineColor,
		Title = "Adjust Survivor Outline",
		Transparency = Settings.EspSettings.PlayerEsp.SurvivorOutlineTransparancy,
		Callback = function(value)
			Settings.EspSettings.PlayerEsp.SurvivorOutlineColor = value
			Settings.EspSettings.PlayerEsp.SurvivorOutlineTransparancy = Options.SurvivorOutlinePicker.Transparency
			UpdatePlayerEsp()
		end,
	})

BeastFillPicker = Groupboxes.EspCustomization.PlayerEsp:AddLabel("Beast Fill"):AddColorPicker("BeastFillPicker", {
	Default = Settings.EspSettings.PlayerEsp.BeastFillColor,
	Title = "Adjust Beast Fill",
	Transparency = Settings.EspSettings.PlayerEsp.BeastFillTransparancy,
	Callback = function(value)
		Settings.EspSettings.PlayerEsp.BeastFillColor = value
		Settings.EspSettings.PlayerEsp.BeastFillTransparancy = Options.BeastFillPicker.Transparency
		UpdatePlayerEsp()
	end,
})

ThreeDSurvivorPicker =
	Groupboxes.EspCustomization.BoxEsp:AddLabel("3D Survivor Color"):AddColorPicker("ThreeDSurvivorPicker", {
		Default = Settings.EspSettings.PlayerEsp.d3esp.SurvivorFillColor,
		Title = "3D Box Survivor Color",
		Transparency = 0,
		Callback = function(value)
			Settings.EspSettings.PlayerEsp.d3esp.SurvivorFillColor = value
			UpdateAll3DBoxEsp()
		end,
	})

ThreeDBeastPicker = Groupboxes.EspCustomization.BoxEsp:AddLabel("3D Beast Color"):AddColorPicker("ThreeDBeastPicker", {
	Default = Settings.EspSettings.PlayerEsp.d3esp.BeastFillColor,
	Title = "3D Box Beast Color",
	Transparency = 0,
	Callback = function(value)
		Settings.EspSettings.PlayerEsp.d3esp.BeastFillColor = value
		UpdateAll3DBoxEsp()
	end,
})

BeastOutlinePicker =
	Groupboxes.EspCustomization.PlayerEsp:AddLabel("Beast Outline"):AddColorPicker("BeastOutlinePicker", {
		Default = Settings.EspSettings.PlayerEsp.BeastOutlineColor,
		Title = "Adjust Beast Outline",
		Transparency = Settings.EspSettings.PlayerEsp.BeastOutlineTransparancy,
		Callback = function(value)
			Settings.EspSettings.PlayerEsp.BeastOutlineColor = value
			Settings.EspSettings.PlayerEsp.BeastOutlineTransparancy = Options.BeastOutlinePicker.Transparency
			UpdatePlayerEsp()
		end,
	})

PickTracerColor = Groupboxes.EspCustomization.Tracers:AddLabel("Color Picker"):AddColorPicker("PickTracer", {
	Default = Settings.EspSettings.PlayerEsp.TracerSettings.Color,
	Title = "Adjust tracer color",
	Transparency = Settings.EspSettings.PlayerEsp.TracerSettings.Transparancy,
	Callback = function(value)
		Settings.EspSettings.PlayerEsp.TracerSettings.Color = value
		Settings.EspSettings.PlayerEsp.TracerSettings.Transparancy = Options.PickTracer.Transparancy
		UpdateTracers()
	end,
})

TracerThicknessSlider = Groupboxes.EspCustomization.Tracers:AddSlider("Thickness Slider", {
	Default = Settings.EspSettings.PlayerEsp.TracerSettings.Thickness,
	Min = 0.5,
	Max = 15,
	Rounding = 1,
	Text = "Adjust the tracer thickness",
	Tooltip = "Adjusts your tracers thickness",
	Callback = function(value)
		Settings.EspSettings.PlayerEsp.TracerSettings.Thickness = value
		UpdateTracers()
	end,
})

TracerFromBottomToggle = Groupboxes.EspCustomization.Tracers:AddToggle("From Bottom", {
	Text = "Tracer start from bottom",
	Tooltip = "Adjust if the tracer comes from the bottom or the top",
	Default = Settings.EspSettings.PlayerEsp.TracerSettings.FromBottom,
	Callback = function(value)
		Settings.EspSettings.PlayerEsp.TracerSettings.FromBottom = value
	end,
})

SkeletonColorPicker =
	Groupboxes.EspCustomization.Skeleton:AddLabel("SkeletonColor"):AddColorPicker("SkeletonColorPicker", {
		Default = Settings.EspSettings.PlayerEsp.SkeletonSettings.Color,
		Title = "Pick your skeleton esp color",
		Transparency = Settings.EspSettings.PlayerEsp.SkeletonSettings.Transparency,
		Callback = function(val)
			Settings.EspSettings.PlayerEsp.SkeletonSettings.Color = val
			Settings.EspSettings.PlayerEsp.SkeletonSettings.Transparency = Options.SkeletonColorPicker.Transparency
			UpdateSkeleton()
		end,
	})

SkeletonThicknessSlider = Groupboxes.EspCustomization.Skeleton:AddSlider("Skeleton Thickness", {
	Default = Settings.EspSettings.PlayerEsp.SkeletonSettings.Thickness,
	Min = 0.5,
	Max = 15,
	Rounding = 1,
	Text = "Adjust skeleton thickness",
	Tooltip = "Changes the thickness of skeleton lines",
	Callback = function(value)
		Settings.EspSettings.PlayerEsp.SkeletonSettings.Thickness = value
		UpdateSkeleton()
	end,
})

PcOutlinePicker = Groupboxes.EspCustomization.PcAndTube:AddLabel("Pc Outline"):AddColorPicker("PcOutlinePicker", {
	Default = Settings.EspSettings.PcEsp.OutlineColor,
	Title = "Adjust pc outline",
	Transparency = Settings.EspSettings.PcEsp.OutlineTransparency,
	Callback = function(value)
		Settings.EspSettings.PcEsp.OutlineColor = value
		Settings.EspSettings.PcEsp.OutlineTransparency = Options.PcOutlinePicker.Transparency
		UpdatePcEspColors()
	end,
})

PcFillTransparancy = Groupboxes.EspCustomization.PcAndTube:AddInput("InputPicker", {
	Text = "Pc fill transparancy",
	Default = Settings.EspSettings.PcEsp.FillTransparency,
	Tooltip = "Adjusts the fill transparancy on computers",
	Numeric = true,
	ClearTextOnFocus = false,
	Finished = false,
	Callback = function(value)
		Settings.EspSettings.PcEsp.FillTransparency = value
		UpdatePcEspColors()
	end,
})

TubeFillPicker = Groupboxes.EspCustomization.PcAndTube:AddLabel("Tube Fill"):AddColorPicker("TubeFillPicker", {
	Default = Settings.EspSettings.TubeEsp.FillColor,
	Title = "Adjust tube fill",
	Transparency = Settings.EspSettings.TubeEsp.FillTransparency,
	Callback = function(value)
		Settings.EspSettings.TubeEsp.FillColor = value
		Settings.EspSettings.TubeEsp.FillTransparency = Options.TubeFillPicker.Transparency
		UpdateTubeEspColors()
	end,
})

TubeOutlinePicker = Groupboxes.EspCustomization.PcAndTube:AddLabel("Tube Outline"):AddColorPicker("TubeOutlinePicker", {
	Default = Settings.EspSettings.TubeEsp.OutlineColor,
	Title = "Adjust tube outline",
	Transparency = Settings.EspSettings.TubeEsp.OutlineTransparency,
	Callback = function(value)
		Settings.EspSettings.TubeEsp.OutlineColor = value
		Settings.EspSettings.TubeEsp.OutlineTransparency = Options.TubeOutlinePicker.Transparency
		UpdateTubeEspColors()
	end,
})

OpenDoorFillPicker =
	Groupboxes.EspCustomization.DoorEsp:AddLabel("Open Door Fill"):AddColorPicker("OpenDoorFillPicker", {
		Default = Settings.EspSettings.DoorEsp.OpenColor,
		Title = "Adjust open door fill",
		Transparency = Settings.EspSettings.DoorEsp.OpenFillTransparency,
		Callback = function(value)
			Settings.EspSettings.DoorEsp.OpenColor = value
			Settings.EspSettings.DoorEsp.OpenFillTransparency = Options.OpenDoorFillPicker.Transparency
			UpdateDoorEspColors()
		end,
	})

OpenDoorOutlinePicker =
	Groupboxes.EspCustomization.DoorEsp:AddLabel("Open Door Outline"):AddColorPicker("OpenDoorOutlinePicker", {
		Default = Settings.EspSettings.DoorEsp.OpenOutlineColor,
		Title = "Adjust open door outline",
		Transparency = Settings.EspSettings.DoorEsp.OutlineTransparency,
		Callback = function(value)
			Settings.EspSettings.DoorEsp.OpenOutlineColor = value
			Settings.EspSettings.DoorEsp.OutlineTransparency = Options.OpenDoorOutlinePicker.Transparency
			UpdateDoorEspColors()
		end,
	})

ClosedDoorFillPicker =
	Groupboxes.EspCustomization.DoorEsp:AddLabel("Closed Door Fill"):AddColorPicker("ClosedDoorFillPicker", {
		Default = Settings.EspSettings.DoorEsp.ClosedColor,
		Title = "Adjust closed door fill",
		Transparency = Settings.EspSettings.DoorEsp.ClosedFillTransparency,
		Callback = function(value)
			Settings.EspSettings.DoorEsp.ClosedColor = value
			Settings.EspSettings.DoorEsp.ClosedFillTransparency = Options.ClosedDoorFillPicker.Transparency
			UpdateDoorEspColors()
		end,
	})

ClosedDoorOutlinePicker =
	Groupboxes.EspCustomization.DoorEsp:AddLabel("Closed Door Outline"):AddColorPicker("ClosedDoorOutlinePicker", {
		Default = Settings.EspSettings.DoorEsp.ClosedOutlineColor,
		Title = "Adjust closed door outline",
		Transparency = Settings.EspSettings.DoorEsp.OutlineTransparency,
		Callback = function(value)
			Settings.EspSettings.DoorEsp.ClosedOutlineColor = value
			Settings.EspSettings.DoorEsp.OutlineTransparency = Options.ClosedDoorOutlinePicker.Transparency
			UpdateDoorEspColors()
		end,
	})

BoxEspPicker = Groupboxes.EspCustomization.BoxEsp:AddLabel("Box esp color"):AddColorPicker("BoxEspPicker", {
	Default = Settings.EspSettings.PlayerEsp.BoxEsp.Color,
	Title = "Box esp color picker",
	Transparency = Settings.EspSettings.PlayerEsp.BoxEsp.Transparency,
	Callback = function(value)
		Settings.EspSettings.PlayerEsp.BoxEsp.Color = value
		Settings.EspSettings.PlayerEsp.BoxEsp.Transparency = Options.BoxEspPicker.Transparency
		updateBoxUI()
	end,
})

BoxThicknessSlider = Groupboxes.EspCustomization.BoxEsp:AddSlider("Box Thickness Slider", {
	Default = Settings.EspSettings.PlayerEsp.TracerSettings.Thickness,
	Min = 0.5,
	Max = 15,
	Rounding = 1,
	Text = "Adjust the box esp thickness",
	Tooltip = "Adjusts your box esp thickness",
	Callback = function(value)
		Settings.EspSettings.PlayerEsp.BoxEsp.Thickness = value
		updateBoxUI()
	end,
})

PcProgressToggle = Groupboxes.Gadgets.Left:AddToggle("PcProgress", {
	Text = "PC Progress",
	Default = false,
	Tooltip = "Shows how close a pc is to finishing",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.PcProgress.Enabled = Value
	end,
})

ExitProgressToggle = Groupboxes.Gadgets.Left:AddToggle("ExitProgress", {
	Text = "Exit Progress",
	Default = false,
	Tooltip = "Shows how close an exit is to opening",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.ExitProgress.Enabled = Value
	end,
})

DoorProgressToggle = Groupboxes.Gadgets.Left:AddToggle("DoorProgress", {
	Text = "Door Progress",
	Default = false,
	Tooltip = "Shows how close a door is to opening",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.DoorProgress.Enabled = Value
	end,
})

GetupTimerToggle = Groupboxes.Gadgets.Right:AddToggle("GetupTimer", {
	Text = "Getup Timer",
	Default = false,
	Tooltip = "Shows how long till a survivor wakes up",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.GetupTimer.Enabled = Value
	end,
})

RunnerTimerToggle = Groupboxes.Gadgets.Right:AddToggle("RunnerTimer", {
	Text = "Runner Timer",
	Default = false,
	Tooltip = "Shows how close beast is to getting runner back",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.RunnerTimer.Enabled = Value
		if Value then
			StartRunnerTimer()
		else
			StopRunnerTimer()
		end
	end,
})

BlackRemoverToggle = Groupboxes.Gadgets.OtherGadgets:AddToggle("Black Remover", {
	Text = "Black screen remover",
	Default = Settings.GadgetSettings.OtherGadgets.HideBlack,
	Tooltip = "Removes black screen at the beginning of the round",
	Callback = function(Value)
		Settings.GadgetSettings.OtherGadgets.HideBlack = not Value
		local ui = playergui:FindFirstChild("BlackOutScreenGui")
		ui.Enabled = not Value
	end,
})

HealthTimerToggle = Groupboxes.Gadgets.OtherGadgets:AddToggle("Health Timer", {
	Text = "Health Timer",
	Default = Settings.GadgetSettings.ProgressSettings.HealthTimer.Enabled,
	Tooltip = "Shows player health above their head",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.HealthTimer.Enabled = Value
		if Value then
			EnableHealthTimer()
		else
			DisableHealthTimer()
		end
	end,
})

HealthDisplayNameToggle = Groupboxes.GadgetCustomization.HealthTimer:AddToggle("HealthDisplayName", {
	Text = "Display Name Above Head",
	Default = Settings.GadgetSettings.ProgressSettings.HealthTimer.DisplayName,
	Tooltip = "Show player name above their health",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.HealthTimer.DisplayName = Value
		for plr, ui in pairs(PlayerHealthUis) do
			if ui and ui.NameLabel then
				ui.NameLabel.Visible = Value
			end
		end
	end,
})

WalkspeedDetectorToggle = Groupboxes.Gadgets.OtherGadgets:AddToggle("Walkspeed Detector", {
	Text = "Walkspeed Detector",
	Default = false,
	Tooltip = "Detects if anyone is using walkspeed",
	Callback = function(Value)
		Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.Enabled = Value
		if Value then
			for _, plr in pairs(Players:GetPlayers()) do
				if plr ~= player and plr.Character then
					CreateWalkspeedUI(plr.Character)
				end
			end
		else
			for character, ui in pairs(WalkspeedUIs) do
				RemoveWalkspeedUI(character)
			end
		end
	end,
})

HeadstartTracker = Groupboxes.Gadgets.OtherGadgets:AddToggle("Headstart Tracker", {
	Default = Settings.GadgetSettings.OtherGadgets.HeadstartTracker.Enabled,
	Text = "Headstart tracker",
	Tooltip = "Displays when the headstart will be over",
	Callback = function(val)
		Settings.GadgetSettings.OtherGadgets.HeadstartTracker.Enabled = val
	end,
})

WalkspeedTextPicker = WalkspeedCustomization:AddLabel("Text Color"):AddColorPicker("WalkspeedTextPicker", {
	Default = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.TextColor,
	Title = "Walkspeed Text Color",
	Transparency = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.TextTransparency,
	Callback = function(value)
		Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.TextColor = value
		Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.TextTransparency =
			Options.WalkspeedTextPicker.Transparency
		UpdateWalkspeedColors()
	end,
})

WalkspeedStrokePicker = WalkspeedCustomization:AddLabel("Stroke Color"):AddColorPicker("WalkspeedStrokePicker", {
	Default = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.StrokeColor,
	Title = "Walkspeed Stroke Color",
	Transparency = Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.StrokeTransparency,
	Callback = function(value)
		Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.StrokeColor = value
		Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.StrokeTransparency =
			Options.WalkspeedStrokePicker.Transparency
		UpdateWalkspeedColors()
	end,
})

AdvancedDetectionToggle = WalkspeedCustomization:AddToggle("Advanced Detection", {
	Text = "Advanced Detection",
	Default = false,
	Tooltip = "Use to counter hideable walkspeed, less useful against normal walkspeed",
	Callback = function(Value)
		Settings.GadgetSettings.OtherGadgets.WalkspeedDetector.UseAdvancedDetection = Value
		if Value then
			for character, ui in pairs(WalkspeedUIs) do
				local hrp = character:FindFirstChild("HumanoidRootPart")
				if hrp then
					WalkspeedTracking[character] = {
						LastPosition = hrp.Position,
						LastUpdateTime = tick(),
						CurrentSpeed = 0,
						IsMoving = false,
					}
				end
			end
		else
			WalkspeedTracking = {}
		end
	end,
})

PcTextColorPicker =
	Groupboxes.GadgetCustomization.PcProgress:AddLabel("Text Color"):AddColorPicker("PcTextColorPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.PcProgress.TextColor,
		Title = "PC Progress Text Color",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.PcProgress.TextColor = value
			maintainObjectUIs()
		end,
	})

PcProgressFillPicker =
	Groupboxes.GadgetCustomization.PcProgress:AddLabel("Progress Fill"):AddColorPicker("PcProgressFillPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.PcProgress.ProgressFill,
		Title = "PC Progress Fill Color",
		Transparency = Settings.GadgetSettings.ProgressSettings.PcProgress.ProgressTransparancy,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.PcProgress.ProgressFill = value
			Settings.GadgetSettings.ProgressSettings.PcProgress.ProgressTransparancy =
				Options.PcProgressFillPicker.Transparency
			maintainObjectUIs()
		end,
	})

PcBackgroundPicker =
	Groupboxes.GadgetCustomization.PcProgress:AddLabel("Background"):AddColorPicker("PcBackgroundPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.PcProgress.BackgroundColor,
		Title = "PC Progress Background",
		Transparency = Settings.GadgetSettings.ProgressSettings.PcProgress.BackgroundTransparancy,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.PcProgress.BackgroundColor = value
			Settings.GadgetSettings.ProgressSettings.PcProgress.BackgroundTransparancy =
				Options.PcBackgroundPicker.Transparency
			maintainObjectUIs()
		end,
	})

PcDisplaySecondsToggle = Groupboxes.GadgetCustomization.PcProgress:AddToggle("PcDisplaySeconds", {
	Text = "Display Seconds",
	Default = Settings.GadgetSettings.ProgressSettings.PcProgress.DisplaySeconds,
	Tooltip = "Show time remaining in seconds",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.PcProgress.DisplaySeconds = Value
		maintainObjectUIs()
	end,
})

ExitTextColorPicker =
	Groupboxes.GadgetCustomization.ExitProgress:AddLabel("Text Color"):AddColorPicker("ExitTextColorPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.ExitProgress.TextColor,
		Title = "Exit Progress Text Color",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.ExitProgress.TextColor = value
			maintainObjectUIs()
		end,
	})

ExitProgressFillPicker =
	Groupboxes.GadgetCustomization.ExitProgress:AddLabel("Progress Fill"):AddColorPicker("ExitProgressFillPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.ExitProgress.ProgressFill,
		Title = "Exit Progress Fill Color",
		Transparency = Settings.GadgetSettings.ProgressSettings.ExitProgress.ProgressTransparancy,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.ExitProgress.ProgressFill = value
			Settings.GadgetSettings.ProgressSettings.ExitProgress.ProgressTransparancy =
				Options.ExitProgressFillPicker.Transparency
			maintainObjectUIs()
		end,
	})

ExitBackgroundPicker =
	Groupboxes.GadgetCustomization.ExitProgress:AddLabel("Background"):AddColorPicker("ExitBackgroundPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.ExitProgress.BackgroundColor,
		Title = "Exit Progress Background",
		Transparency = Settings.GadgetSettings.ProgressSettings.ExitProgress.BackgroundTransparancy,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.ExitProgress.BackgroundColor = value
			Settings.GadgetSettings.ProgressSettings.ExitProgress.BackgroundTransparancy =
				Options.ExitBackgroundPicker.Transparency
			maintainObjectUIs()
		end,
	})

ExitOpenerTextPicker =
	Groupboxes.GadgetCustomization.ExitProgress:AddLabel("Opener Text"):AddColorPicker("ExitOpenerTextPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.ExitProgress.OpenerTextColor,
		Title = "Exit Opener Name Color",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.ExitProgress.OpenerTextColor = value
			maintainObjectUIs()
		end,
	})

ExitDisplaySecondsToggle = Groupboxes.GadgetCustomization.ExitProgress:AddToggle("ExitDisplaySeconds", {
	Text = "Display Seconds",
	Default = Settings.GadgetSettings.ProgressSettings.ExitProgress.DisplaySeconds,
	Tooltip = "Show time remaining in seconds",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.ExitProgress.DisplaySeconds = Value
		maintainObjectUIs()
	end,
})

ExitDisplayOpenerToggle = Groupboxes.GadgetCustomization.ExitProgress:AddToggle("ExitDisplayOpener", {
	Text = "Display Opener Name",
	Default = Settings.GadgetSettings.ProgressSettings.ExitProgress.DisplayOpener,
	Tooltip = "Show who is opening the exit",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.ExitProgress.DisplayOpener = Value
		maintainObjectUIs()
	end,
})

DoorTextColorPicker =
	Groupboxes.GadgetCustomization.DoorProgress:AddLabel("Text Color"):AddColorPicker("DoorTextColorPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.DoorProgress.TextColor,
		Title = "Door Progress Text Color",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.DoorProgress.TextColor = value
			maintainObjectUIs()
		end,
	})

DoorProgressFillPicker =
	Groupboxes.GadgetCustomization.DoorProgress:AddLabel("Progress Fill"):AddColorPicker("DoorProgressFillPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.DoorProgress.ProgressFill,
		Title = "Door Progress Fill Color",
		Transparency = Settings.GadgetSettings.ProgressSettings.DoorProgress.ProgressTransparancy,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.DoorProgress.ProgressFill = value
			Settings.GadgetSettings.ProgressSettings.DoorProgress.ProgressTransparancy =
				Options.DoorProgressFillPicker.Transparency
			maintainObjectUIs()
		end,
	})

DoorBackgroundPicker =
	Groupboxes.GadgetCustomization.DoorProgress:AddLabel("Background"):AddColorPicker("DoorBackgroundPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.DoorProgress.BackgroundColor,
		Title = "Door Progress Background",
		Transparency = Settings.GadgetSettings.ProgressSettings.DoorProgress.BackgroundTransparancy,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.DoorProgress.BackgroundColor = value
			Settings.GadgetSettings.ProgressSettings.DoorProgress.BackgroundTransparancy =
				Options.DoorBackgroundPicker.Transparency
			maintainObjectUIs()
		end,
	})

DoorOpenerTextPicker =
	Groupboxes.GadgetCustomization.DoorProgress:AddLabel("Opener Text"):AddColorPicker("DoorOpenerTextPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.DoorProgress.OpenerTextColor,
		Title = "Door Opener Name Color",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.DoorProgress.OpenerTextColor = value
			maintainObjectUIs()
		end,
	})

DoorDisplaySecondsToggle = Groupboxes.GadgetCustomization.DoorProgress:AddToggle("DoorDisplaySeconds", {
	Text = "Display Seconds",
	Default = Settings.GadgetSettings.ProgressSettings.DoorProgress.DisplaySeconds,
	Tooltip = "Show time remaining in seconds",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.DoorProgress.DisplaySeconds = Value
		maintainObjectUIs()
	end,
})

DoorDisplayOpenerToggle = Groupboxes.GadgetCustomization.DoorProgress:AddToggle("DoorDisplayOpener", {
	Text = "Display Opener Name",
	Default = Settings.GadgetSettings.ProgressSettings.DoorProgress.DisplayOpener,
	Tooltip = "Show who is opening the door",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.DoorProgress.DisplayOpener = Value
		maintainObjectUIs()
	end,
})

GetupNotHitColorPicker =
	Groupboxes.GadgetCustomization.GetupTimer:AddLabel("Not Hit Color"):AddColorPicker("GetupNotHitColorPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.GetupTimer.NotHitColor,
		Title = "Color When Not Time to Hit",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.GetupTimer.NotHitColor = value
			UpdateGetupTimerColors()
		end,
	})

GetupHitColorPicker =
	Groupboxes.GadgetCustomization.GetupTimer:AddLabel("Hit Color"):AddColorPicker("GetupHitColorPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.GetupTimer.HitColor,
		Title = "Color When Time to Hit",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.GetupTimer.HitColor = value
			UpdateGetupTimerColors()
		end,
	})

GetupWhenToHitSlider = Groupboxes.GadgetCustomization.GetupTimer:AddSlider("GetupWhenToHit", {
	Default = Settings.GadgetSettings.ProgressSettings.GetupTimer.WhenToHit,
	Min = 0,
	Max = 5,
	Rounding = 2,
	Text = "When to Hit (seconds)",
	Tooltip = "Changes color when timer reaches this value",
	Callback = function(value)
		Settings.GadgetSettings.ProgressSettings.GetupTimer.WhenToHit = value
		UpdateGetupTimerColors()
	end,
})

RunnerTextColorPicker =
	Groupboxes.GadgetCustomization.RunnerTimer:AddLabel("Text Color"):AddColorPicker("RunnerTextColorPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.RunnerTimer.TextColor,
		Title = "Runner Timer Text Color",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.RunnerTimer.TextColor = value
			UpdateRunnerTimerColor()
		end,
	})

RunnerDisplaySecondsToggle = Groupboxes.GadgetCustomization.RunnerTimer:AddToggle("RunnerDisplaySeconds", {
	Text = "Display Seconds",
	Default = Settings.GadgetSettings.ProgressSettings.RunnerTimer.DisplaySeconds,
	Tooltip = "Show runner time in seconds instead of percentage",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.RunnerTimer.DisplaySeconds = Value
	end,
})

HealthHighColorPicker =
	Groupboxes.GadgetCustomization.HealthTimer:AddLabel("High HP Color"):AddColorPicker("HealthHighColorPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.HealthTimer.HighHpColor,
		Title = "High Health Color",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.HealthTimer.HighHpColor = value
			for _, plr in pairs(Players:GetPlayers()) do
				UpdateHealthUI(plr)
			end
		end,
	})

HealthLowColorPicker =
	Groupboxes.GadgetCustomization.HealthTimer:AddLabel("Low HP Color"):AddColorPicker("HealthLowColorPicker", {
		Default = Settings.GadgetSettings.ProgressSettings.HealthTimer.LowHpColor,
		Title = "Low Health Color",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.HealthTimer.LowHpColor = value
			for _, plr in pairs(Players:GetPlayers()) do
				UpdateHealthUI(plr)
			end
		end,
	})

HealthHighStrokePicker =
	Groupboxes.GadgetCustomization.HealthTimer:AddLabel("High HP Stroke"):AddColorPicker("HealthHighStrokePicker", {
		Default = Settings.GadgetSettings.ProgressSettings.HealthTimer.HighHpStrokeColor,
		Title = "High Health Stroke Color",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.HealthTimer.HighHpStrokeColor = value
			for _, plr in pairs(Players:GetPlayers()) do
				UpdateHealthUI(plr)
			end
		end,
	})

HealthLowStrokePicker =
	Groupboxes.GadgetCustomization.HealthTimer:AddLabel("Low HP Stroke"):AddColorPicker("HealthLowStrokePicker", {
		Default = Settings.GadgetSettings.ProgressSettings.HealthTimer.LowHpStrokeColor,
		Title = "Low Health Stroke Color",
		Transparency = 0,
		Callback = function(value)
			Settings.GadgetSettings.ProgressSettings.HealthTimer.LowHpStrokeColor = value
			for _, plr in pairs(Players:GetPlayers()) do
				UpdateHealthUI(plr)
			end
		end,
	})

HealthLowHpThresholdSlider = Groupboxes.GadgetCustomization.HealthTimer:AddSlider("HealthLowHpThreshold", {
	Default = Settings.GadgetSettings.ProgressSettings.HealthTimer.LowHp,
	Min = 0,
	Max = 100,
	Rounding = 1,
	Text = "Low HP Threshold",
	Tooltip = "Health percentage considered 'low'",
	Callback = function(value)
		Settings.GadgetSettings.ProgressSettings.HealthTimer.LowHp = value
		for _, plr in pairs(Players:GetPlayers()) do
			UpdateHealthUI(plr)
		end
	end,
})

HealthDisplaySecondsToggle = Groupboxes.GadgetCustomization.HealthTimer:AddToggle("HealthDisplaySeconds", {
	Text = "Display Seconds",
	Default = Settings.GadgetSettings.ProgressSettings.HealthTimer.DisplaySeconds,
	Tooltip = "Show health as time remaining instead of percentage",
	Callback = function(Value)
		Settings.GadgetSettings.ProgressSettings.HealthTimer.DisplaySeconds = Value
		for _, plr in pairs(Players:GetPlayers()) do
			UpdateHealthUI(plr)
		end
	end,
})
HeadstartColorChanged =
	Groupboxes.GadgetCustomization.HeadstartTracker:AddLabel("Text color changer"):AddColorPicker("TextColorChanged", {
		Default = Settings.GadgetSettings.OtherGadgets.HeadstartTracker.TextColor,
		Title = "Text color changer",
		Transparency = Settings.GadgetSettings.OtherGadgets.HeadstartTracker.TextTransparancy,
		Callback = function(val)
			Settings.GadgetSettings.OtherGadgets.HeadstartTracker.TextColor = val
			Settings.GadgetSettings.OtherGadgets.HeadstartTracker.TextTransparancy =
				Options.TextColorChanged.Transparency
			UpdateHeadstartTimer()
		end,
	})

ExitEspToggle = Groupboxes.Visual.LeftGroupBox:AddToggle("ExitEsp", {
	Text = "Exit ESP",
	Default = false,
	Tooltip = "Highlights exits",
	Callback = function(Value)
		Settings.EspSettings.ExitEsp.Enabled = Value
		if Value then
			StartExitEsp()
		else
			StopExitEsp()
		end
	end,
})

Groupboxes.Visual.LeftGroupBox:AddDivider()
Groupboxes.Visual.LeftGroupBox:AddLabel("Random")

NoFogToggle = Groupboxes.Visual.LeftGroupBox:AddToggle("NoFog", {
	Text = "No Fog",
	Default = false,
	Tooltip = "Remove fog and atmosphere effects",
	Callback = function(Value)
		FogSettings.Enabled = Value
		if Value then
			EnableNoFog()
		else
			DisableNoFog()
		end
	end,
})

ogfogend = Lighting.FogEnd
ogfogcolor = Lighting.FogColor
fogremoverenabled = false

function cleanupblackfog()
	local cache = workspace:FindFirstChild("Cache")

	local blackfogsky = Lighting:FindFirstChild("blackfogsky")
	local blackfognocolor = Lighting:FindFirstChild("blackfognocolor")
	local blackfogbloom = Lighting:FindFirstChild("blackfogbloom")

	if blackfogsky then
		blackfogsky:Destroy()
	end
	if blackfognocolor then
		blackfognocolor:Destroy()
	end
	if blackfogbloom then
		blackfogbloom:Destroy()
	end
	local ogsky = cache:FindFirstChildOfClass("Sky")
	if ogsky then
		ogsky.Parent = Lighting
	end
	Lighting.FogColor = ogfogcolor
	FogColor.FogEnd = ogfogend
end

function setupblackfog()
	if not fogremoverenabled then
		return
	end
	local blackSky = Instance.new("Sky")
	blackSky.SkyboxBk = "rbxassetid://0"
	blackSky.SkyboxDn = "rbxassetid://0"
	blackSky.SkyboxFt = "rbxassetid://0"
	blackSky.SkyboxLf = "rbxassetid://0"
	blackSky.SkyboxRt = "rbxassetid://0"
	blackSky.SkyboxUp = "rbxassetid://0"
	blackSky.Name = "blackfogsky"

	local cache = workspace:FindFirstChild("Cache")
	if not cache then
		cache = Instance.new("Folder")
		cache.Parent = workspace
		cache.Name = "Cache"
	end

	if Lighting:FindFirstChildOfClass("Sky") then
		Lighting:FindFirstChildOfClass("Sky").Parent = cache
	end

	blackSky.Parent = Lighting

	Lighting.FogEnd = 0
	Lighting.FogColor = Color3.new(0, 0, 0)

	local colorCorrection = Instance.new("ColorCorrectionEffect")
	colorCorrection.Brightness = 0.2
	colorCorrection.Contrast = 0.3
	colorCorrection.Saturation = 0.2
	colorCorrection.Parent = Lighting
	colorCorrection.Name = "blackfognocolor"

	local bloom = Instance.new("BloomEffect")
	bloom.Intensity = 1.5
	bloom.Threshold = 2
	bloom.Size = 24
	bloom.Parent = Lighting
	bloom.Name = "blackfogbloom"
end

Groupboxes.Visual.LeftGroupBox:AddToggle("BlackFog", {
	Text = "Black fog",
	Default = false,
	Tooltip = "Simulates removing the fog on pc",
	callback = function(Value)
		fogremoverenabled = Value
		if Value then
			setupblackfog()
		else
			cleanupblackfog()
		end
	end,
})

WallhopsToggle = Groupboxes.Visual.LeftGroupBox:AddToggle("Wallhops", {
	Text = "Show Wallhops",
	Default = false,
	Tooltip = "Highlight wallhoppable surfaces",
	Callback = function(Value)
		WallhopSettings.Enabled = Value
		if Value then
			EnableWallhops()
		else
			DisableWallhops()
		end
	end,
})

BarrierToggle = Groupboxes.Visual.LeftGroupBox:AddToggle("BarrierVisibility", {
	Text = "Barrier Visibility",
	Default = false,
	Tooltip = "Make invisible barriers slightly visible",
	Callback = function(Value)
		BarrierSettings.Enabled = Value
		if Value then
			EnableBarrierVisibility()
		else
			DisableBarrierVisibility()
		end
	end,
})

HeadstartStrokeColorChanged = Groupboxes.GadgetCustomization.HeadstartTracker
	:AddLabel("Stroke color changer")
	:AddColorPicker("HeadstartStrokeColorChanged", {
		Default = Settings.GadgetSettings.OtherGadgets.HeadstartTracker.StrokeColor,
		Title = "Stroke color changer",
		Transparency = Settings.GadgetSettings.OtherGadgets.HeadstartTracker.StrokeTransparancy,
		Callback = function(val)
			Settings.GadgetSettings.OtherGadgets.HeadstartTracker.StrokeColor = val
			Settings.GadgetSettings.OtherGadgets.HeadstartTracker.StrokeTransparancy =
				Options.HeadstartStrokeColorChanged.Transparency
			UpdateHeadstartTimer()
		end,
	})
for _, plr in pairs(Players:GetPlayers()) do
	if plr ~= player then
		trackPlayer(plr)

		if plr.Character then
			CreateRunnerTimerLabel(plr)
		end

		plr.CharacterAdded:Connect(function(character)
			CreateRunnerTimerLabel(plr)
		end)
	end

	onRagdollChanged(plr)
end

for _, plr in pairs(Players:GetPlayers()) do
	if plr ~= player then
		trackPlayer(plr)

		if plr.Character then
			CreateRunnerTimerLabel(plr)
		end

		plr.CharacterAdded:Connect(function(character)
			CreateRunnerTimerLabel(plr)
		end)

		setupRagdollMonitoring(plr)
	end

	onRagdollChanged(plr)
end

conn7 = Players.PlayerAdded:Connect(function(newPlayer)
	if newPlayer ~= player then
		trackPlayer(newPlayer)

		newPlayer.CharacterAdded:Connect(function(character)
			character:WaitForChild("HumanoidRootPart")
			task.wait(0.5)
			CreateRunnerTimerLabel(newPlayer)
			SetupHealthTracking(newPlayer)
			setupRagdollMonitoring(newPlayer)
			UpdateAllCameras()
		end)

		onRagdollChanged(newPlayer)
		setupRagdollMonitoring(newPlayer)
	end
	if Settings.EspSettings.PcEsp.Enabled then
		StopPcEsp()
		StartPcEsp()
	end
	if Settings.EspSettings.TubeEsp.Enabled then
		StopTubeEsp()
		StartTubeEsp()
	end
end)

conn8 = Players.PlayerRemoving:Connect(function(removingPlayer)
	if removingPlayer ~= player then
		untrackPlayer(removingPlayer)

		if previousValues[removingPlayer.UserId] then
			previousValues[removingPlayer.UserId] = nil
		end

		removeBottomRightUI(removingPlayer)

		local index = table.find(HitPlayers, removingPlayer)
		if index then
			table.remove(HitPlayers, index)
		end

		updateUIPositions()

		if GetupConnections[removingPlayer] then
			GetupConnections[removingPlayer]:Disconnect()
			GetupConnections[removingPlayer] = nil
		end

		RemoveCapturedPlayerUI(removingPlayer)
		UpdateAllCameras()
	end
end)

CameraConfigManager = {
	ConfigFolder = "FTFX/CameraConfigs",
}

function CameraConfigManager:EnsureFolder()
	if not isfolder(self.ConfigFolder) then
		makefolder(self.ConfigFolder)
	end
end

function CameraConfigManager:SaveConfig(configName)
	self:EnsureFolder()

	local config = {}
	for slotName, slot in pairs(CameraSettings.CameraSlots) do
		config[slotName] = {
			Enabled = slot.Enabled,
			Position = { X = slot.Position.X, Y = slot.Position.Y },
			Size = { X = slot.Size.X, Y = slot.Size.Y },
		}
	end

	local filePath = self.ConfigFolder .. "/" .. configName .. ".json"
	local success, err = pcall(function()
		writefile(filePath, HttpService:JSONEncode(config))
	end)

	if success then
		Library:Notify("Camera config saved: " .. configName, 3)
	else
		Library:Notify("Failed to save camera config: " .. tostring(err), 5)
	end
end

function CameraConfigManager:OverwriteConfig(configName)
	self:EnsureFolder()

	local filePath = self.ConfigFolder .. "/" .. configName .. ".json"

	if not isfile(filePath) then
		Library:Notify("Camera config not found: " .. configName, 3)
		return false
	end

	local config = {}
	for slotName, slot in pairs(CameraSettings.CameraSlots) do
		config[slotName] = {
			Enabled = slot.Enabled,
			Position = { X = slot.Position.X, Y = slot.Position.Y },
			Size = { X = slot.Size.X, Y = slot.Size.Y },
		}
	end
	local success, err = pcall(function()
		writefile(filePath, HttpService:JSONEncode(config))
	end)

	if success then
		Library:Notify("Camera config saved: " .. configName, 3)
	else
		Library:Notify("Failed to save camera config: " .. tostring(err), 5)
	end
	return true
end

function CameraConfigManager:LoadConfig(configName)
	local filePath = self.ConfigFolder .. "/" .. configName .. ".json"

	if not isfile(filePath) then
		Library:Notify("Camera config not found: " .. configName, 3)
		return false
	end

	local success, result = pcall(function()
		local data = readfile(filePath)
		return HttpService:JSONDecode(data)
	end)

	if not success then
		Library:Notify("Failed to load camera config: " .. tostring(result), 5)
		return false
	end

	for slotName, slotData in pairs(result) do
		if CameraSettings.CameraSlots[slotName] then
			CameraSettings.CameraSlots[slotName].Enabled = slotData.Enabled
			CameraSettings.CameraSlots[slotName].Position = Vector2.new(slotData.Position.X, slotData.Position.Y)
			CameraSettings.CameraSlots[slotName].Size = Vector2.new(slotData.Size.X, slotData.Size.Y)
		end
	end

	UpdateAllCameras()
	Library:Notify("Camera config loaded: " .. configName, 3)
	return true
end

function CameraConfigManager:DeleteConfig(configName)
	local filePath = self.ConfigFolder .. "/" .. configName .. ".json"

	if not isfile(filePath) then
		Library:Notify("Camera config not found: " .. configName, 3)
		return false
	end

	local success, err = pcall(function()
		delfile(filePath)
	end)

	if success then
		Library:Notify("Camera config deleted: " .. configName, 3)
		return true
	else
		Library:Notify("Failed to delete camera config: " .. tostring(err), 5)
		return false
	end
end

function CameraConfigManager:ListConfigs()
	self:EnsureFolder()

	if not isfolder(self.ConfigFolder) then
		return {}
	end

	local configs = {}
	local success, files = pcall(function()
		return listfiles(self.ConfigFolder)
	end)

	if not success then
		return {}
	end

	for _, filePath in ipairs(files) do
		local fileName = filePath:match("([^/\\]+)%.json$")
		if fileName then
			table.insert(configs, fileName)
		end
	end

	return configs
end

function CameraConfigManager:BuildConfigSection(tab)
	local ConfigGroup = tab:AddRightGroupbox("Camera Configs")

	ConfigGroup:AddInput("CameraConfigName", {
		Default = "Default",
		Text = "Config Name",
		Tooltip = "Name for your camera configuration",
	})

	ConfigGroup:AddButton("Save Camera Config", function()
		local configName = Options.CameraConfigName.Value
		if configName and configName ~= "" then
			self:SaveConfig(configName)
		else
			Library:Notify("Please enter a config name", 3)
		end
	end)

	ConfigGroup:AddDivider()

	local configList = self:ListConfigs()

	ConfigGroup:AddDropdown("CameraConfigList", {
		Values = configList,
		Default = "",
		Text = "Select Config",
		Tooltip = "Choose a camera config to load",
	})

	ConfigGroup:AddButton("Load Camera Config", function()
		local configName = Options.CameraConfigList.Value
		if configName and configName ~= "" then
			self:LoadConfig(configName)
		else
			Library:Notify("Please select a config", 3)
		end
	end)

	ConfigGroup:AddButton("Delete Camera Config", function()
		local configName = Options.CameraConfigList.Value
		if configName and configName ~= "" then
			self:DeleteConfig(configName)
			local newList = self:ListConfigs()
			Options.CameraConfigList:SetValues(newList)
		else
			Library:Notify("Please select a config", 3)
		end
	end)

	ConfigGroup:AddButton("Refresh Config List", function()
		local newList = self:ListConfigs()
		Options.CameraConfigList:SetValues(newList)
		Library:Notify("Config list refreshed", 2)
	end)

	ConfigGroup:AddButton("Overwrite Config", function()
		local currentconfigname = Options.CameraConfigList.Value
		if currentconfigname and currentconfigname ~= "" then
			CameraConfigManager:OverwriteConfig(currentconfigname)
		else
			Library:Notify("Please select a config", 3)
		end
	end)
end

	local LeftSpeedTab = DangerSettingsTabBox:AddTab("Speed Settings")

	local SpeedToggle = LeftSpeedTab:AddToggle("SpeedEnabled", {
		Text = "Enable Speed",
		Default = false,
		Tooltip = "Enable custom walkspeed/jumppower",
		Callback = function(Value)
			SpeedSettings.Enabled = Value
			if Value then
				ApplySpeed()
			else
				ResetSpeed()
			end
		end,
	})

	LeftSpeedTab:AddInput("SurvivorBoost", {
		Default = tostring(SpeedSettings.SurvivorBoost),
		Numeric = true,
		Finished = true,
		Text = "Survivor Boost",
		Tooltip = "Extra studs per frame for survivor walking",
		Callback = function(Value)
			SpeedSettings.SurvivorBoost = tonumber(Value) or 1
		end,
	})

	LeftSpeedTab:AddInput("BeastBoost", {
		Default = tostring(SpeedSettings.BeastBoost),
		Numeric = true,
		Finished = true,
		Text = "Beast Boost",
		Tooltip = "Extra studs per frame for beast walking",
		Callback = function(Value)
			SpeedSettings.BeastBoost = tonumber(Value) or 1
		end,
	})

	LeftSpeedTab:AddInput("RunnerBoost", {
		Default = tostring(SpeedSettings.RunnerBoost),
		Numeric = true,
		Finished = true,
		Text = "Runner Boost",
		Tooltip = "Extra studs per frame for runner state",
		Callback = function(Value)
			SpeedSettings.RunnerBoost = tonumber(Value) or 2
		end,
	})

	LeftSpeedTab:AddInput("FatigueBoost", {
		Default = tostring(SpeedSettings.FatigueBoost),
		Numeric = true,
		Finished = true,
		Text = "Fatigue Boost",
		Tooltip = "Extra studs per frame for fatigue",
		Callback = function(Value)
			SpeedSettings.FatigueBoost = tonumber(Value) or 1
		end,
	})

	LeftSpeedTab:AddInput("CrawlBoost", {
		Default = tostring(SpeedSettings.CrawlBoost),
		Numeric = true,
		Finished = true,
		Text = "Crawl Boost",
		Tooltip = "Extra studs per frame for crawling",
		Callback = function(Value)
			SpeedSettings.CrawlBoost = tonumber(Value) or 2
		end,
	})

	LeftSpeedTab:AddDivider()
	LeftSpeedTab:AddLabel("Jump Power Settings")

	LeftSpeedTab:AddInput("SurvivorJump", {
		Default = tostring(SpeedSettings.SurvivorJumpPower),
		Numeric = true,
		Finished = true,
		Text = "Survivor Jump Power",
		Tooltip = "Survivor jump power (0 = don't change)",
		Callback = function(Value)
			SpeedSettings.SurvivorJumpPower = tonumber(Value) or 36
		end,
	})

	LeftSpeedTab:AddInput("BeastJump", {
		Default = tostring(SpeedSettings.BeastJumpPower),
		Numeric = true,
		Finished = true,
		Text = "Beast Jump Power",
		Tooltip = "Beast jump power (0 = don't change unless runner)",
		Callback = function(Value)
			SpeedSettings.BeastJumpPower = tonumber(Value) or 36
		end,
	})

	local RightFatigueTab = Tabs["Danger Settings"]:AddRightTabbox("Fatigue Settings")
	local FatigueTab = RightFatigueTab:AddTab("Fatigue")

	FatigueTab:AddToggle("UseFatigueCheats", {
		Text = "Enable Fatigue Cheats",
		Default = false,
		Tooltip = "Enable anti-fatigue modifications",
		Callback = function(Value)
			SpeedSettings.UseFatigueCheats = Value
			if Value and SpeedSettings.Enabled then
				StartFatigueMonitoring()
			elseif SpeedSettings.FatigueConnection then
				SpeedSettings.FatigueConnection:Disconnect()
				SpeedSettings.FatigueConnection = nil
			end
		end,
	})

	FatigueTab:AddInput("FatigueDelay", {
		Default = tostring(SpeedSettings.FatigueDelay or 0),
		Numeric = true,
		Finished = true,
		Text = "Fatigue Delay (seconds)",
		Tooltip = "Time to wait after fatigue starts before boosting",
		Callback = function(Value)
			SpeedSettings.FatigueDelay = tonumber(Value) or 0
		end,
	})

	FatigueTab:AddInput("FatigueDuration", {
		Default = tostring(SpeedSettings.FatigueDuration or 0.8),
		Numeric = true,
		Finished = true,
		Text = "Fatigue Duration (seconds)",
		Tooltip = "How long to boost speed during fatigue",
		Callback = function(Value)
			SpeedSettings.FatigueDuration = tonumber(Value) or 0.8
		end,
	})

	local FlopHelperTab = Tabs["Danger Settings"]:AddLeftTabbox("Flop Helper")
	local FlopTab = FlopHelperTab:AddTab("Flop Settings")

	FlopTab:AddToggle("EnableFlopHelper", {
		Text = "Enable Flop Helper",
		Default = false,
		Tooltip = "Override default flop controls",
		Callback = function(Value)
			FlopSettings.Enabled = Value
			if Value then
				StartFlopHelper()
			else
				StopFlopHelper()
			end
		end,
	})

	FlopTab:AddSlider("FlopDelay", {
		Default = 1.5,
		Min = 0.1,
		Max = 5,
		Rounding = 2,
		Text = "Flop Delay",
		Tooltip = "Cooldown between flops in seconds",
		Callback = function(Value)
			FlopSettings.Delay = Value
		end,
	})

	FlopTab:AddSlider("FlopX", {
		Default = 1,
		Min = -5,
		Max = 5,
		Rounding = 1,
		Text = "X Direction",
		Tooltip = "Horizontal force multiplier",
		Callback = function(Value)
			FlopSettings.XMultiplier = Value
		end,
	})

	FlopTab:AddSlider("FlopY", {
		Default = 0,
		Min = -5,
		Max = 5,
		Rounding = 1,
		Text = "Y Direction",
		Tooltip = "Vertical force multiplier",
		Callback = function(Value)
			FlopSettings.YMultiplier = Value
		end,
	})

	FlopTab:AddSlider("FlopZ", {
		Default = 1,
		Min = -5,
		Max = 5,
		Rounding = 1,
		Text = "Z Direction",
		Tooltip = "Depth force multiplier",
		Callback = function(Value)
			FlopSettings.ZMultiplier = Value
		end,
	})

CrosshairTab = Tabs.Crosshair:AddLeftGroupbox("Crosshair Settings")

CrosshairTab:AddToggle("CrosshairEnabled", {
	Text = "Enable Crosshair",
	Default = false,
	Tooltip = "Show custom crosshair",
	Callback = function(Value)
		CrosshairSettings.Enabled = Value
		CreateCrosshair()
	end,
})

CrosshairTab:AddDropdown("CrosshairType", {
	Values = { "Cross", "Dot" },
	Default = "Cross",
	Text = "Crosshair Type",
	Callback = function(Value)
		CrosshairSettings.Type = Value
		UpdateCrosshair()
	end,
})

CrosshairTab:AddLabel("Crosshair Color"):AddColorPicker("CrosshairColor", {
	Default = CrosshairSettings.Color,
	Title = "Crosshair Color",
	Transparency = CrosshairSettings.Transparency,
	Callback = function(Value)
		CrosshairSettings.Color = Value
		CrosshairSettings.Transparency = Options.CrosshairColor.Transparency
		UpdateCrosshair()
	end,
})

CrosshairTab:AddSlider("CrosshairThickness", {
	Default = CrosshairSettings.Thickness,
	Min = 1,
	Max = 10,
	Rounding = 1,
	Text = "Thickness",
	Callback = function(Value)
		CrosshairSettings.Thickness = Value
		UpdateCrosshair()
	end,
})

CrosshairTab:AddSlider("CrosshairSize", {
	Default = CrosshairSettings.Size,
	Min = 5,
	Max = 50,
	Rounding = 1,
	Text = "Size",
	Callback = function(Value)
		CrosshairSettings.Size = Value
		UpdateCrosshair()
	end,
})

CrosshairTab:AddSlider("CrosshairGap", {
	Default = CrosshairSettings.Gap,
	Min = 0,
	Max = 30,
	Rounding = 1,
	Text = "Gap",
	Callback = function(Value)
		CrosshairSettings.Gap = Value
		UpdateCrosshair()
	end,
})

CrosshairTab:AddToggle("CrosshairOutline", {
	Text = "Enable Outline",
	Default = true,
	Callback = function(Value)
		CrosshairSettings.OutlineEnabled = Value
		UpdateCrosshair()
	end,
})

CrosshairTab:AddLabel("Outline Color"):AddColorPicker("CrosshairOutlineColor", {
	Default = CrosshairSettings.OutlineColor,
	Title = "Outline Color",
	Callback = function(Value)
		CrosshairSettings.OutlineColor = Value
		UpdateCrosshair()
	end,
})

CameraTab = Tabs["Camera Views"]:AddLeftGroupbox("Camera Slots")

CameraTab:AddToggle("BeastCamToggle", {
	Text = "Beast Camera",
	Default = false,
	Tooltip = "Show beast camera in dedicated slot",
	Callback = function(Value)
		CameraSettings.CameraSlots.Beast.Enabled = Value
		UpdateAllCameras()
	end,
})

CameraTab:AddToggle("Surv1CamToggle", {
	Text = "Survivor 1 Camera",
	Default = false,
	Tooltip = "Show first survivor camera",
	Callback = function(Value)
		CameraSettings.CameraSlots.Surv1.Enabled = Value
		UpdateAllCameras()
	end,
})

CameraTab:AddToggle("Surv2CamToggle", {
	Text = "Survivor 2 Camera",
	Default = false,
	Tooltip = "Show second survivor camera",
	Callback = function(Value)
		CameraSettings.CameraSlots.Surv2.Enabled = Value
		UpdateAllCameras()
	end,
})

CameraTab:AddToggle("Surv3CamToggle", {
	Text = "Survivor 3 Camera",
	Default = false,
	Tooltip = "Show third survivor camera",
	Callback = function(Value)
		CameraSettings.CameraSlots.Surv3.Enabled = Value
		UpdateAllCameras()
	end,
})

CameraTab:AddToggle("Surv4CamToggle", {
	Text = "Survivor 4 Camera",
	Default = false,
	Tooltip = "Show fourth survivor camera",
	Callback = function(Value)
		CameraSettings.CameraSlots.Surv4.Enabled = Value
		UpdateAllCameras()
	end,
})

CameraTab:AddDivider()

CameraTab:AddButton("Stop All Cameras", function()
	StopAllCameras()
	for slotName in pairs(CameraSettings.CameraSlots) do
		CameraSettings.CameraSlots[slotName].Enabled = false
	end
end)

ExitFillPicker = Groupboxes.EspCustomization.PcAndTube:AddLabel("Exit Fill"):AddColorPicker("ExitFillPicker", {
	Default = Settings.EspSettings.ExitEsp.FillColor,
	Title = "Adjust exit fill",
	Transparency = Settings.EspSettings.ExitEsp.FillTransparency,
	Callback = function(value)
		Settings.EspSettings.ExitEsp.FillColor = value
		Settings.EspSettings.ExitEsp.FillTransparency = Options.ExitFillPicker.Transparency
		UpdateExitEspColors()
	end,
})

ExitOutlinePicker = Groupboxes.EspCustomization.PcAndTube:AddLabel("Exit Outline"):AddColorPicker("ExitOutlinePicker", {
	Default = Settings.EspSettings.ExitEsp.OutlineColor,
	Title = "Adjust exit outline",
	Transparency = Settings.EspSettings.ExitEsp.OutlineTransparency,
	Callback = function(value)
		Settings.EspSettings.ExitEsp.OutlineColor = value
		Settings.EspSettings.ExitEsp.OutlineTransparency = Options.ExitOutlinePicker.Transparency
		UpdateExitEspColors()
	end,
})

BushToggle = Groupboxes.Visual.LeftGroupBox:AddToggle("BushVisibility", {
	Text = "Remove Bushes",
	Default = false,
	Tooltip = "Make bushes transparent",
	Callback = function(Value)
		BushSettings.Enabled = Value
		if Value then
			EnableBushes()
		else
			DisableBushes()
		end
	end,
})

ShadowToggle = Groupboxes.Visual.LeftGroupBox:AddToggle("ShadowVisibility", {
	Text = "Remove Shadows",
	Default = false,
	Tooltip = "Disable global shadows",
	Callback = function(Value)
		ShadowSettings.Enabled = Value
		if Value then
			DisableShadows()
		else
			EnableShadows()
		end
	end,
})

CameraCustomization = Tabs["Camera Views"]:AddRightGroupbox("Camera Customization")

conn9 = Players.PlayerRemoving:Connect(function(removingPlayer)
	if removingPlayer ~= player then
		untrackPlayer(removingPlayer)

		if previousValues[removingPlayer.UserId] then
			previousValues[removingPlayer.UserId] = nil
		end

		removeBottomRightUI(removingPlayer)

		local index = table.find(HitPlayers, removingPlayer)
		if index then
			table.remove(HitPlayers, index)
		end

		updateUIPositions()

		if GetupConnections[removingPlayer] then
			GetupConnections[removingPlayer]:Disconnect()
			GetupConnections[removingPlayer] = nil
		end

		StopCameraView(removingPlayer)
	end
end)

AutoFarmTab = Tabs["Auto Farm"]
autofarmleft = AutoFarmTab:AddLeftGroupbox("AUTO FARM SETTINGS")

autofarmleft:AddToggle("Toggle Auto Farm", {
	Text = "Enable AutoFarm",
	Default = AutoFarmSettings.Enabled,
	Tooltip = "Toggles auto farm",
	Callback = function(state)
		AutoFarmSettings.Enabled = state
		if state then
			StartAutoFarm()
		else
			DisableAutoFarm()
		end
	end,
})

autofarmleft:AddToggle("Farm As Survivor", {
	Text = "Farm as Survivor",
	Tooltip = "Will farm as survivor as well",
	Default = AutoFarmSettings.FarmAsSurvivor,
	Callback = function(state)
		AutoFarmSettings.FarmAsSurvivor = state
	end,
})

autofarmleft:AddToggle("TargetBestPc", {
	Text = "Goto PCs with Most Progress",
	Default = AutoFarmSettings.GotoComputersWithMostProg,
	Tooltip = "Goto pc with most progress",
	Callback = function(state)
		AutoFarmSettings.GotoComputersWithMostProg = state
	end,
})

autofarmleft:AddToggle("AutoSave", {
	Text = "Auto saves survivor",
	Default = AutoFarmSettings.AutoSave,
	Tooltip = "Automatically goes to tubes and saves survivors",
	Callback = function(state)
		AutoFarmSettings.AutoSave = state
	end,
})

TrollTab = Tabs.Trolling:AddLeftGroupbox("Troll Features")

TrollTab:AddButton("Give Fatigue", function()
	GiveFatigue()
end)

TrollTab:AddToggle("AutoFatigue", {
	Text = "Auto Give Fatigue",
	Default = false,
	Tooltip = "Automatically gives fatigue on interval",
	Callback = function(Value)
		TrollSettings.AutoFatigue.Enabled = Value
		if Value then
			StartAutoFatigue()
		else
			if TrollSettings.AutoFatigue.Connection then
				task.cancel(TrollSettings.AutoFatigue.Connection)
			end
		end
	end,
})

TrollTab:AddSlider("FatigueInterval", {
	Default = 1,
	Min = 0.01,
	Max = 10,
	Rounding = 2,
	Text = "Fatigue Interval",
	Tooltip = "Interval in seconds",
	Callback = function(Value)
		TrollSettings.AutoFatigue.Interval = Value
	end,
})

TrollTab:AddDivider()

TrollTab:AddButton("Use Beast Ability", function()
	UseBeastAbility()
end)

TrollTab:AddToggle("AutoAbility", {
	Text = "Auto Use Ability",
	Default = false,
	Tooltip = "Automatically uses beast ability on interval",
	Callback = function(Value)
		TrollSettings.AutoAbility.Enabled = Value
		if Value then
			StartAutoAbility()
		else
			if TrollSettings.AutoAbility.Connection then
				task.cancel(TrollSettings.AutoAbility.Connection)
			end
		end
	end,
})

TrollTab:AddSlider("AbilityInterval", {
	Default = 1,
	Min = 0.01,
	Max = 10,
	Rounding = 2,
	Text = "Ability Interval",
	Tooltip = "Interval in seconds",
	Callback = function(Value)
		TrollSettings.AutoAbility.Interval = Value
	end,
})
TrollTab:AddDivider()

playerNames = {}
for _, plr in pairs(Players:GetPlayers()) do
	if plr ~= player then
		table.insert(playerNames, plr.Name)
	end
end

TrollTab:AddButton("Unrope Player", function()
	UnropePlayer()
end)

TrollTab:AddToggle("AutoUnrope", {
	Text = "Auto Unrope Players",
	Default = false,
	Tooltip = "Automatically unropes any ragdolled player",
	Callback = function(Value)
		TrollSettings.AutoUnrope.Enabled = Value
		if Value then
			StartAutoUnrope()
		else
			if TrollSettings.AutoUnrope.Connection then
				TrollSettings.AutoUnrope.Connection:Disconnect()
			end
			TrollSettings.RopedPlayers = {}
		end
	end,
})
RopeHelperTab = Tabs["Danger Settings"]:AddRightTabbox("Rope Helper")
RopeTab = RopeHelperTab:AddTab("Rope Settings")

RopeTab:AddToggle("EnableRopeHelper", {
	Text = "Enable Rope Helper",
	Default = false,
	Tooltip = "Enable automatic roping",
	Callback = function(Value)
		RopeHelperSettings.Enabled = Value
	end,
})

RopeTab:AddToggle("RandomizePart", {
	Text = "Randomize Roped Part",
	Default = false,
	Tooltip = "Randomly select which body part to rope",
	Callback = function(Value)
		RopeHelperSettings.RandomizePart = Value
	end,
})

RopeTab:AddDropdown("RopePartSelection", {
	Values = { "Head", "Torso", "Left Arm", "Right Arm", "Left Leg", "Right Leg" },
	Default = "Torso",
	Text = "Select Part to Rope",
	Tooltip = "Choose which body part to rope (ignored if randomize is on)",
	Callback = function(Value)
		RopeHelperSettings.SelectedPart = Value
	end,
})

RopeTab:AddToggle("AutoRopeOnHit", {
	Text = "Auto Rope on Hit",
	Default = false,
	Tooltip = "Automatically rope players when they get hit",
	Callback = function(Value)
		RopeHelperSettings.AutoRopeOnHit = Value
	end,
})

RopeTab:AddToggle("ClickToRope", {
	Text = "Click to Rope Nearest",
	Default = false,
	Tooltip = "Click to rope nearest ragdolled player to your cursor",
	Callback = function(Value)
		RopeHelperSettings.ClickToRope = Value
	end,
})

RopeTab:AddSlider("RopeMaxDistance", {
	Default = 30,
	Min = 10,
	Max = 100,
	Rounding = 1,
	Text = "Max Rope Distance",
	Tooltip = "Maximum distance to rope players",
	Callback = function(Value)
		RopeHelperSettings.MaxDistance = Value
	end,
})

KillAuraTab = Tabs["Danger Settings"]:AddRightTabbox("Kill Aura")
KATab = KillAuraTab:AddTab("Kill Aura")

KATab:AddToggle("EnableKillAura", {
	Text = "Enable Kill Aura",
	Default = false,
	Tooltip = "Automatically hit all nearby players",
	Callback = function(Value)
		KillAuraSettings.Enabled = Value
		if Value then
			StartKillAura()
		else
			if KillAuraSettings.Connection then
				KillAuraSettings.Connection:Disconnect()
			end
		end
	end,
})

KATab:AddSlider("KillAuraDistance", {
	Default = 30,
	Min = 1,
	Max = 100,
	Rounding = 1,
	Text = "Max Hit Distance",
	Tooltip = "Maximum distance to hit players",
	Callback = function(Value)
		KillAuraSettings.MaxDistance = Value
	end,
})

ThreeDSurvivorFillPicker =
	Groupboxes.EspCustomization.PlayerEsp:AddLabel("3D Survivor Fill"):AddColorPicker("ThreeDSurvivorFillPicker", {
		Default = Settings.EspSettings.PlayerEsp.d3esp.SurvivorFillColor,
		Title = "3D Survivor Box Color",
		Transparency = 0,
		Callback = function(value)
			Settings.EspSettings.PlayerEsp.d3esp.SurvivorFillColor = value
			UpdateAll3DBoxEsp()
		end,
	})

ThreeDEspBeastFillPicker =
	Groupboxes.EspCustomization.PlayerEsp:AddLabel("3D Beast Fill"):AddColorPicker("ThreeDEspBeastFillPicker", {
		Default = Settings.EspSettings.PlayerEsp.d3esp.BeastFillColor,
		Title = "3D Beast Box Color",
		Transparency = 0,
		Callback = function(value)
			Settings.EspSettings.PlayerEsp.d3esp.BeastFillColor = value
			UpdateAll3DBoxEsp()
		end,
	})

RainbowEspToggle = Groupboxes.Visual.RightGroupBox:AddToggle("RainbowEsp", {
	Text = "Rainbow ESP",
	Default = false,
	Tooltip = "Cycle through rainbow colors",
	Callback = function(Value)
		RainbowEspState.Enabled = Value
		if Value then
			StartRainbowEsp()
		else
			StopRainbowEsp()
		end
	end,
})

RainbowSpeedSlider = Groupboxes.EspCustomization.PlayerEsp:AddSlider("RainbowSpeed", {
	Default = 0.5,
	Min = 0.1,
	Max = 5,
	Rounding = 1,
	Text = "Rainbow Speed",
	Tooltip = "How fast the rainbow cycles",
	Callback = function(value)
		RainbowEspState.Speed = value
	end,
})

local function ApplyFontToObject(obj)
	if not FontSettings.Enabled then
		return
	end
	if HasFontObject(obj) then
		obj.Font = FontSettings.SelectedFont
	end
end

local function ApplyFontToContainer(container)
	for _, obj in ipairs(container:GetDescendants()) do
		ApplyFontToObject(obj)
	end
end

local function StartFontChanger()
	if not FontSettings.Enabled then
		return
	end

	ApplyFontToContainer(workspace)
	ApplyFontToContainer(playergui)

	table.insert(FontSettings.Connections, workspace.DescendantAdded:Connect(ApplyFontToObject))
	table.insert(FontSettings.Connections, CoreGui.DescendantAdded:Connect(ApplyFontToObject))
	table.insert(FontSettings.Connections, playergui.DescendantAdded:Connect(ApplyFontToObject))
end

local function StopFontChanger()
	for _, conn in ipairs(FontSettings.Connections) do
		conn:Disconnect()
	end
	FontSettings.Connections = {}
end

local function ApplyTextureToObject(obj)
	if not TextureSettings.Enabled then
		return
	end
	if obj:IsA("BasePart") and not obj:IsA("Terrain") then
		if not TextureSettings.OriginalMaterials[obj] then
			TextureSettings.OriginalMaterials[obj] = {
				Material = obj.Material,
				Color = obj.Color,
			}
		end
		obj.Material = TextureSettings.SelectedTexture

		if TextureSettings.UsePerPartColors and TextureSettings.PerPartColors[obj] then
			obj.Color = TextureSettings.PerPartColors[obj]
		elseif not TextureSettings.UsePerPartColors then
			obj.Color = TextureSettings.DefaultColor
		end
	end
end

local function ApplyTextureToContainer(container)
	for _, obj in ipairs(container:GetDescendants()) do
		ApplyTextureToObject(obj)
	end
end

local function StartTextureChanger()
	if not TextureSettings.Enabled then
		return
	end

	ApplyTextureToContainer(workspace)

	table.insert(TextureSettings.Connections, workspace.DescendantAdded:Connect(ApplyTextureToObject))
end

local function StopTextureChanger()
	for _, conn in ipairs(TextureSettings.Connections) do
		conn:Disconnect()
	end
	TextureSettings.Connections = {}

	for obj, originalData in pairs(TextureSettings.OriginalMaterials) do
		if obj and obj.Parent then
			obj.Material = originalData.Material
			obj.Color = originalData.Color
		end
	end
	TextureSettings.OriginalMaterials = {}
	TextureSettings.PerPartColors = {}
end

GeneralCustomizationLeft = Tabs["General Customization"]:AddLeftGroupbox("Fonts")

GeneralCustomizationLeft:AddToggle("EnableFontChanger", {
	Text = "Enable Font Changer",
	Default = false,
	Tooltip = "Changes all text fonts in the game",
	Callback = function(Value)
		FontSettings.Enabled = Value
		if Value then
			StartFontChanger()
		else
			StopFontChanger()
		end
	end,
})

GeneralCustomizationLeft:AddDropdown("FontSelection", {
	Values = {
		"SourceSans",
		"SourceSansBold",
		"SourceSansLight",
		"SourceSansItalic",
		"SourceSansSemibold",
		"Gotham",
		"GothamBold",
		"GothamBlack",
		"GothamMedium",
		"Arial",
		"ArialBold",
		"Arcade",
		"AmaticSC",
		"Bangers",
		"Creepster",
		"DenkOne",
		"Fondamento",
		"FredokaOne",
		"Gaegu",
		"Grenze",
		"GrenzeGotisch",
		"Highway",
		"IndieFlower",
		"JosefinSans",
		"Jura",
		"Kalam",
		"Merriweather",
		"Michroma",
		"Nunito",
		"Oswald",
		"PatrickHand",
		"PermanentMarker",
		"Roboto",
		"RobotoCondensed",
		"RobotoMono",
		"SciFi",
		"SpecialElite",
		"TitilliumWeb",
		"Ubuntu",
	},
	Default = "SourceSans",
	Text = "Select Font",
	Tooltip = "Choose font to apply",
	Callback = function(Value)
		FontSettings.SelectedFont = Enum.Font[Value]
		if FontSettings.Enabled then
			ApplyFontToContainer(workspace)
			ApplyFontToContainer(CoreGui)
			ApplyFontToContainer(playergui)
		end
	end,
})

GeneralCustomizationRight = Tabs["General Customization"]:AddRightGroupbox("Textures")

GeneralCustomizationRight:AddToggle("EnableTextureChanger", {
	Text = "Enable Texture Changer",
	Default = false,
	Tooltip = "Changes all part materials in workspace",
	Callback = function(Value)
		TextureSettings.Enabled = Value
		if Value then
			StartTextureChanger()
		else
			StopTextureChanger()
		end
	end,
})

GeneralCustomizationRight:AddDropdown("TextureSelection", {
	Values = {
		"Plastic",
		"SmoothPlastic",
		"Wood",
		"WoodPlanks",
		"Marble",
		"Slate",
		"Concrete",
		"Granite",
		"Brick",
		"Pebble",
		"Cobblestone",
		"CorrodedMetal",
		"DiamondPlate",
		"Foil",
		"Metal",
		"Grass",
		"LeafyGrass",
		"Sand",
		"Fabric",
		"Ice",
		"Glacier",
		"Snow",
		"Sandstone",
		"Basalt",
		"Ground",
		"CrackedLava",
		"Asphalt",
		"Limestone",
		"Pavement",
		"Rock",
		"Salt",
		"Cardboard",
		"Carpet",
		"Glass",
		"ForceField",
		"Neon",
		"Ceramic",
		"Clay",
		"Rubber",
	},
	Default = "Plastic",
	Text = "Select Texture",
	Tooltip = "Choose material to apply to all parts",
	Callback = function(Value)
		TextureSettings.SelectedTexture = Enum.Material[Value]
		if TextureSettings.Enabled then
			ApplyTextureToContainer(workspace)
		end
	end,
})

GeneralCustomizationLeft:AddDivider()
GeneralCustomizationLeft:AddLabel("Grey Avatar")

GeneralCustomizationLeft:AddToggle("EnableGreyAvatar", {
	Text = "Enable Grey Avatar",
	Default = false,
	Tooltip = "Makes all player avatars grey except yours",
	Callback = function(Value)
		GreyAvatarSettings.Enabled = Value
		if Value then
			StartGreyAvatar()
		else
			StopGreyAvatar()
		end
	end,
})

GeneralCustomizationRight:AddDivider()
GeneralCustomizationRight:AddLabel("Black Fog Gamma")

GeneralCustomizationRight:AddToggle("EnableBlackFogGamma", {
	Text = "Enable Gamma Adjustment",
	Default = false,
	Tooltip = "Adjust brightness for black fog",
	Callback = function(Value)
		BlackFogGammaSettings.Enabled = Value
		if Value then
			StartBlackFogGamma()
		else
			StopBlackFogGamma()
		end
	end,
})

GeneralCustomizationRight:AddSlider("GammaValue", {
	Default = 1,
	Min = 0.1,
	Max = 3,
	Rounding = 2,
	Text = "Gamma Value",
	Tooltip = "Adjust screen brightness",
	Callback = function(Value)
		BlackFogGammaSettings.GammaValue = Value
		UpdateBlackFogGamma()
	end,
})

SoundBoosterTab = Tabs["General Customization"]:AddLeftTabbox("Sound Booster")
SoundTab = SoundBoosterTab:AddTab("Sound Settings")

SoundTab:AddSlider("HeartbeatVolume", {
	Default = 1,
	Min = 1,
	Max = 10,
	Rounding = 1,
	Text = "Heartbeat Volume",
	Tooltip = "Boost beast heartbeat sounds",
	Callback = function(Value)
		SoundBoosterSettings.HeartbeatVolume = Value
		UpdateSoundBoosterVolumes()
	end,
})

SoundTab:AddSlider("StepsVolume", {
	Default = 1,
	Min = 1,
	Max = 10,
	Rounding = 1,
	Text = "Steps Volume",
	Tooltip = "Boost footstep sounds",
	Callback = function(Value)
		SoundBoosterSettings.StepsVolume = Value
		UpdateSoundBoosterVolumes()
	end,
})

SoundTab:AddSlider("JumpsVolume", {
	Default = 1,
	Min = 1,
	Max = 10,
	Rounding = 1,
	Text = "Jumps Volume",
	Tooltip = "Boost jump sounds",
	Callback = function(Value)
		SoundBoosterSettings.JumpsVolume = Value
		UpdateSoundBoosterVolumes()
	end,
})

ShaderTab = Tabs["General Customization"]:AddRightTabbox("Shaders")
ShaderSettings1 = ShaderTab:AddTab("Shader Presets")

ShaderSettings1:AddToggle("EnableShaders", {
	Text = "Enable Shaders",
	Default = false,
	Tooltip = "Apply lighting shaders",
	Callback = function(Value)
		ShaderSettings.Enabled = Value
		ApplyShaderLighting()
	end,
})

ShaderSettings1:AddDropdown("ShaderPreset", {
	Values = { "Default", "Morning", "Midday", "Afternoon", "Evening", "Night", "Midnight" },
	Default = "Default",
	Text = "Shader Preset",
	Callback = function(Value)
		local presets = LoadShaderPresets()
		if Value == "Default" then
			shaderlight = {
				["yfbghj"] = backupLighting.Ambient,
				["tgvbyd"] = backupLighting.ClockTime,
				["ghuybhuyhj"] = backupLighting.GeographicLatitude,
				["khnbfth"] = backupLighting.Brightness,
				["hgyghkg"] = backupLighting.ColorShift_Bottom,
				["yfbhjku"] = backupLighting.ColorShift_Top,
				["ygyyfgvhbjytrt"] = backupLighting.EnvironmentDiffuseScale,
				["sdfcddc"] = backupLighting.EnvironmentSpecularScale,
				["hgnujuu7thgr"] = backupLighting.GlobalShadows,
				["hyhnngtf"] = backupLighting.OutdoorAmbient,
				["hdfr7thgr"] = backupLighting.ExposureCompensation,
				["fhnchvhfjsd"] = 0,
				["ugtbbjhygt"] = 0,
				["tfbghuugbnjhg"] = 0,
				["fvrtccvghghj"] = Color3.fromRGB(255, 255, 255),
				["jnfdhbnfcvh"] = 0.4,
				["fvtyghj"] = 24,
				["ygbhnj"] = 0.95,
				["njnfg"] = 0,
				["jdfkd"] = 0.1,
				["fvgsdfg"] = 50,
				["sdkvkflv"] = 10,
				["hbjhd"] = 0.75,
				["gyhgtg"] = 0,
				["ygbhggv"] = 0,
				["jghbjhgyfd"] = Color3.fromRGB(255, 255, 255),
				["shdbsnjfc"] = 0,
				["skdjfkdm"] = 0,
				["sjdjncdjf"] = Color3.fromRGB(199, 199, 199),
				["efjdjfk"] = Color3.fromRGB(106, 112, 125),
				["sejfd"] = 0,
				["jddfjsd"] = 0,
			}
		else
			shaderlight = presets[Value:lower()]
		end
		ApplyShaderLighting()
	end,
})

ShaderSettings1:AddDivider()

ShaderSettings1:AddToggle("ColorCorrection", {
	Text = "Color Correction",
	Default = true,
	Callback = function(Value)
		shaderWL["cor"] = Value
	end,
})

ShaderSettings1:AddToggle("Bloom", {
	Text = "Bloom Effect",
	Default = true,
	Callback = function(Value)
		shaderWL["bl"] = Value
	end,
})

ShaderSettings1:AddToggle("DepthOfField", {
	Text = "Depth Of Field",
	Default = false,
	Callback = function(Value)
		shaderWL["dof"] = Value
	end,
})

ShaderSettings1:AddToggle("BlurEffect", {
	Text = "Blur Effect",
	Default = false,
	Callback = function(Value)
		shaderWL["blr"] = Value
	end,
})

ShaderSettings1:AddToggle("SunRays", {
	Text = "Sun Rays",
	Default = false,
	Callback = function(Value)
		shaderWL["sray"] = Value
	end,
})

ResolutionTab = Tabs["General Customization"]:AddRightTabbox("Resolution")
ResSettings = ResolutionTab:AddTab("Resolution Settings")

ResSettings:AddToggle("EnableResolution", {
	Text = "Enable Resolution Scale",
	Default = false,
	Tooltip = "Change game resolution",
	Callback = function(Value)
		ResolutionSettings.Enabled = Value
		if Value then
			StartResolutionScale()
		else
			StopResolutionScale()
		end
	end,
})

ResSettings:AddSlider("ResolutionScale", {
	Default = 1,
	Min = 0.25,
	Max = 2,
	Rounding = 2,
	Text = "Resolution Scale",
	Callback = function(Value)
		ResolutionSettings.ResolutionScale = Value
	end,
})

conn10 = Players.PlayerAdded:Connect(function(newPlayer)
	if newPlayer ~= player and Options.KillAuraTarget then
		local values = Options.KillAuraTarget.Values
		table.insert(values, newPlayer.Name)
		Options.KillAuraTarget:SetValues(values)
	end
end)

conn11 = Players.PlayerRemoving:Connect(function(removingPlayer)
	if removingPlayer ~= player and Options.KillAuraTarget then
		local values = Options.KillAuraTarget.Values
		local index = table.find(values, removingPlayer.Name)
		if index then
			table.remove(values, index)
			Options.KillAuraTarget:SetValues(values)
		end

		if KillAuraSettings.TargetPlayer == removingPlayer then
			KillAuraSettings.TargetPlayer = nil
		end
	end
end)

conn12 = Players.PlayerAdded:Connect(function(newPlayer)
	if newPlayer ~= player then
		local currentValues = Options.UnropeTarget.Values
		table.insert(currentValues, newPlayer.Name)
		Options.UnropeTarget:SetValues(currentValues)
	end
end)

conn13 = Players.PlayerRemoving:Connect(function(removingPlayer)
	if removingPlayer ~= player then
		local currentValues = Options.UnropeTarget.Values
		local index = table.find(currentValues, removingPlayer.Name)
		if index then
			table.remove(currentValues, index)
			Options.UnropeTarget:SetValues(currentValues)
		end

		if TrollSettings.AutoUnrope.TargetPlayer == removingPlayer then
			TrollSettings.AutoUnrope.TargetPlayer = nil
		end

		TrollSettings.RopedPlayers[removingPlayer] = nil
	end
end)

conn17 = player.CharacterAdded:Connect(function(character)
	character:WaitForChild("HumanoidRootPart")
	task.wait(0.5)
	if FlopSettings.Enabled then
		StartFlopHelper()
	end
end)

local function FullCleanup()
	if AutoFarmSettings then
		AutoFarmSettings.Enabled = false
		AutoFarmSettings.FarmAsSurvivor = false
		AutoFarmSettings.GotoComputersWithMostProg = false
		AutoFarmSettings.AutoSave = false
	end

	if AutoFarmSettings and AutoFarmSettings.DistanceConnection then
		task.cancel(AutoFarmSettings.DistanceConnection)
	end

	if Settings and Settings.EspSettings and Settings.EspSettings.PlayerEsp.Enabled then
		Settings.EspSettings.PlayerEsp.Enabled = false
	end

	for _, plr in pairs(Players:GetPlayers()) do
		if plr.Character then
			RemovePlayerEsp(plr.Character)
			removeSkeletonUI(plr.Character)
			removeBoxUI(plr.Character)
			RemoveWalkspeedUI(plr.Character)
			RemoveHealthUI(plr)
			RemoveBeastChanceLabel(plr)
		end
	end

	if PlayerConnections and PlayerConnections.EspConnections then
		for plr, conn in pairs(PlayerConnections.EspConnections) do
			if conn then
				conn:Disconnect()
			end
		end
		PlayerConnections.EspConnections = {}
	end

	if FogSettings then
		if FogSettings.Enabled then
			DisableNoFog()
		end
		if FogSettings.LightingFolder then
			FogSettings.LightingFolder:Destroy()
		end
		FogSettings = nil
	end

	if WallhopSettings then
		if WallhopSettings.Enabled then
			DisableWallhops()
		end
		WallhopSettings = nil
	end

	if BarrierSettings then
		if BarrierSettings.Enabled then
			DisableBarrierVisibility()
		end
		BarrierSettings = nil
	end

	if BushSettings then
		if BushSettings.Enabled then
			DisableBushes()
		end
		BushSettings = nil
	end

	if ShadowSettings then
		if ShadowSettings.Enabled then
			EnableShadows()
		end
		ShadowSettings = nil
	end

	StopPcEsp()
	StopTubeEsp()
	StopExitEsp()
	StopDoorEsp()
	stopTracers()
	stopSkeletonEsp()
	stopBoxEsp()
	cleanupAllProgressUIs()
	StopHeadstartTracking()
	StopRunnerTimer()

	for _, element in pairs(crosshairElements) do
		if element and element.Destroy then
			element:Destroy()
		end
	end
	if RainbowEspState then
		StopRainbowEsp()
		RainbowEspState = nil
	end

	for character in pairs(ThreeDESPObjects or {}) do
		Remove3DBoxEsp(character)
	end
	ThreeDESPObjects = nil
	crosshairElements = {}

	StopAllCameras()

	for _, plr in pairs(Players:GetPlayers()) do
		if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
			local billboard = plr.Character.HumanoidRootPart:FindFirstChild("BeastPowerBillboard")
			if billboard then
				billboard:Destroy()
			end
		end
	end

	if TrollSettings then
		if TrollSettings.AutoFatigue.Connection then
			task.cancel(TrollSettings.AutoFatigue.Connection)
		end
		if TrollSettings.AutoAbility.Connection then
			task.cancel(TrollSettings.AutoAbility.Connection)
		end
		if TrollSettings.AutoUnrope.Connection then
			TrollSettings.AutoUnrope.Connection:Disconnect()
		end
		TrollSettings = nil
	end

	if RopeHelperSettings then
		RopeHelperSettings = nil
	end

	if AutoSaveConn then
		task.cancel(AutoSaveConn)
	end

	if GetupConnections then
		for plr, conn in pairs(GetupConnections) do
			if conn then
				conn:Disconnect()
			end
			if plr.Character then
				local head = plr.Character:FindFirstChild("Head")
				if head then
					RemoveGetupTimerLabel(head)
				end
			end
			removeBottomRightUI(plr)
		end
		GetupConnections = {}
	end
	GetupUis = {}
	HitPlayers = {}

	if PlayerConnections and PlayerConnections.GameStartingConnection then
		PlayerConnections.GameStartingConnection:Disconnect()
		PlayerConnections.GameStartingConnection = nil
	end

	local doorsManager = workspace:FindFirstChild("DoorsManager")
	if doorsManager then
		doorsManager:Destroy()
	end

	if progresstrackerconnection then
		progresstrackerconnection:Disconnect()
		progresstrackerconnection = nil
	end
	computers = nil
	exits = nil
	doors = nil
	objectProgress = nil

	if PlayerHealthUis then
		for _, ui in pairs(PlayerHealthUis) do
			if ui and ui.Billboard then
				ui.Billboard:Destroy()
			end
		end
	end
	PlayerHealthUis = nil
	CapturedPlayers = nil

	for plr in pairs(CapturedPlayerUIs or {}) do
		RemoveCapturedPlayerUI(plr)
	end
	CapturedPlayerUIs = nil

	if healthtrackerconn then
		healthtrackerconn:Disconnect()
		healthtrackerconn = nil
	end

	if mapchanged then
		mapchanged:Disconnect()
		mapchanged = nil
	end
	if gameactivechanged then
		gameactivechanged:Disconnect()
		gameactivechanged = nil
	end

	runnerStates = nil

	if Settings and Settings.GadgetSettings and Settings.GadgetSettings.ProgressSettings.RunnerTimer.Connection then
		Settings.GadgetSettings.ProgressSettings.RunnerTimer.Connection:Disconnect()
	end

	if WalkspeedUIs then
		for character, ui in pairs(WalkspeedUIs) do
			RemoveWalkspeedUI(character)
		end
	end
	WalkspeedUIs = nil
	WalkspeedTracking = nil
	if walkspeedConnection then
		walkspeedConnection:Disconnect()
		walkspeedConnection = nil
	end

	for _, plrs in pairs(Players:GetPlayers()) do
		RemoveHealthUI(plrs)
	end

	ResetSpeed()
	if SpeedSettings then
		if SpeedSettings.Connection then
			SpeedSettings.Connection:Disconnect()
		end
		if SpeedSettings.FatigueConnection then
			SpeedSettings.FatigueConnection:Disconnect()
		end
	end

	if KillAuraSettings and KillAuraSettings.Connection then
		KillAuraSettings.Connection:Disconnect()
	end

	StopSpectating()

	if BeastChanceTracker then
		BeastChanceTracker:Disconnect()
		BeastChanceTracker = nil
	end

	for _, plr in pairs(Players:GetPlayers()) do
		RemoveBeastChanceLabel(plr)
	end

	if FlopSettings then
		StopFlopHelper()
		FlopSettings = nil
	end

	SkeletonUIs = nil
	SkeletonConnections = nil
	TracerLines = nil
	TracerConnections = nil
	BoxLines = nil
	BoxConnections = nil
	BoxUIs = nil
	previousValues = nil
	PlayerConnections = nil
	Settings = nil
	GetupUis = nil
	HitPlayers = nil
	GetupConnections = nil
	crosshairElements = {}
	SpeedSettings = nil
	CameraSettings = nil
	KillAuraSettings = nil
	SpectateSettings = nil

	AutoFarmSettings = {
		Enabled = false,
		FarmAsSurvivor = false,
		GotoComputersWithMostProg = false,
		AutoSave = false,
		DistanceConnection = nil,
	}

	if NameHiderSettings then
		StopNameHider()
		NameHiderSettings = nil
	end

	conn2:Disconnect()
	conn3:Disconnect()
	conn4:Disconnect()
	conn5:Disconnect()
	conn6:Disconnect()
	conn7:Disconnect()
	conn8:Disconnect()
	conn9:Disconnect()
	conn10:Disconnect()
	conn11:Disconnect()
	conn12:Disconnect()
	conn13:Disconnect()
	conn14:Disconnect()
	conn15:Disconnect()
	conn17:Disconnect()
	conn19:Disconnect()

	BeastChanceTracker:Disconnect()
	ConnectionManager:DisconnectAll()

	cleanupblackfog()

	if GreyAvatarSettings and GreyAvatarSettings.Enabled then
		StopGreyAvatar()
	end
	GreyAvatarSettings = nil

	if BlackFogGammaSettings and BlackFogGammaSettings.Enabled then
		StopBlackFogGamma()
	end
	if BlackFogGammaSettings and BlackFogGammaSettings.ColorCorrection then
		BlackFogGammaSettings.ColorCorrection:Destroy()
	end
	BlackFogGammaSettings = nil

	if SoundBoosterSettings and SoundBoosterSettings.Enabled then
		StopSoundBooster()
	end
	SoundBoosterSettings = nil
	if ShaderSettings and ShaderSettings.Enabled then
		ShaderSettings.Enabled = false
		ApplyShaderLighting()
	end
	if shaderConnection then
		shaderConnection:Disconnect()
		shaderConnection = nil
	end
	ShaderSettings = nil
	shaderlight = nil
	shaderWL = nil

	if ResolutionSettings and ResolutionSettings.Enabled then
		StopResolutionScale()
	end
	ResolutionSettings = nil
end

task.spawn(function()
	local MenuGroup = Tabs["UI Settings"]:AddLeftGroupbox("Menu", "wrench")
	MenuGroup:AddToggle("KeybindMenuOpen", {
		Default = Library.KeybindFrame.Visible,
		Text = "Open Keybind Menu",
		Callback = function(value)
			Library.KeybindFrame.Visible = value
		end,
	})
	MenuGroup:AddToggle("ShowCustomCursor", {
		Text = "Custom Cursor",
		Default = true,
		Callback = function(Value)
			Library.ShowCustomCursor = Value
		end,
	})
	MenuGroup:AddDropdown("NotificationSide", {
		Values = { "Left", "Right" },
		Default = "Right",
		Text = "Notification Side",
		Callback = function(Value)
			Library:SetNotifySide(Value)
		end,
	})
	MenuGroup:AddDropdown("DPIDropdown", {
		Values = { "50%", "75%", "100%", "125%", "150%", "175%", "200%" },
		Default = "100%",
		Text = "DPI Scale",
		Callback = function(Value)
			Value = Value:gsub("%%", "")
			local DPI = tonumber(Value)
			Library:SetDPIScale(DPI)
		end,
	})
	MenuGroup:AddDivider()
	MenuGroup:AddLabel("Menu bind")
		:AddKeyPicker("MenuKeybind", { Default = "RightShift", NoUI = true, Text = "Menu keybind" })

	MenuGroup:AddButton("Unload", function()
		Library:Unload()
		FullCleanup()
	end)

	MenuGroup:AddToggle("Execute Infinite yield", {
		Text = "Execute Infinite yield",
		Tooltip = "Executes Infinite yield, automatically executes it per config",
		Default = false,
		Callback = function(value)
			if value then
				loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))()
			end
		end,
	})

	MenuGroup:AddDivider()
	MenuGroup:AddLabel("Discord")
	MenuGroup:AddButton("Copy Invite", function()
		setclipboard("https://discord.gg/P2rH4K7ySQ")
		Library:Notify("Successfully copied the link to your clipboard", 5)
	end)

	Library.ToggleKeybind = Options.MenuKeybind

	ThemeManager:SetLibrary(Library)
	SaveManager:SetLibrary(Library)
	SaveManager:IgnoreThemeSettings()
	SaveManager:SetIgnoreIndexes({ "MenuKeybind" })
	ThemeManager:SetFolder("FTFX")
	SaveManager:SetFolder("FTFX/FTF")
	SaveManager:BuildConfigSection(Tabs["UI Settings"])
	ThemeManager:ApplyToTab(Tabs["UI Settings"])
	SaveManager:LoadAutoloadConfig()
	CameraConfigManager:BuildConfigSection(Tabs["Camera Views"])
end)
