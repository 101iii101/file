local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()
local selectedTheme = "Default"
local Window = Rayfield:CreateWindow({
   Name = "99 Nights In The Forest - Script By Iliankytb",
   Icon = 0, -- Icon in Topbar. Can use Lucide Icons (string) or Roblox Image (number). 0 to use no icon (default).
   LoadingTitle = "99 Nights In The Forest",
   LoadingSubtitle = "Script By Iliankytb",
   Theme = selectedTheme, -- Check https://docs.sirius.menu/rayfield/configuration/themes

   DisableRayfieldPrompts = false,
   DisableBuildWarnings = false, -- Prevents Rayfield from warning when the script has a version mismatch with the interface

   ConfigurationSaving = {
      Enabled = true,
      FolderName = "SaverNITF", -- Create a custom folder for your hub/game
      FileName = "K"
   },

   Discord = {
      Enabled = false, -- Prompt the user to join your Discord server if their executor supports it
      Invite = "noinvitelink", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ ABCD would be ABCD
      RememberJoins = true -- Set this to false to make them join the discord every time they load it up
   },

   KeySystem = false, -- Set this to true to use our key system
   KeySettings = {
      Title = "Untitled",
      Subtitle = "Key System",
      Note = "No method of obtaining the key is provided", -- Use this to tell the user how to get a key
      FileName = "Key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
      SaveKey = true, -- The user's key will be saved, but if you change the key, they will be unable to use your script
      GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
      Key = {"Hello"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
   }
})
local InfoTab = Window:CreateTab("Info")
local PlayerTab = Window:CreateTab("Player")
local EspTab = Window:CreateTab("Esp")
local GameTab = Window:CreateTab("Game")
local BringItemTab = Window:CreateTab("Bring Item")
local DiscordTab = Window:CreateTab("Discord")
local SettingsTab = Window:CreateTab("Settings")
local ActiveEspItems,ActiveDistanceEsp,ActiveEspEnemy,ActiveEspChildren,ActiveEspPeltTrader,ActivateFly,AlrActivatedFlyPC,ActiveNoCooldownPrompt,ActiveNoFog,
ActiveAuoChopTree,ActiveKillAura,ActivateInfiniteJump,ActiveNoclip = false,false,false,false,false,false,false,false,false,false,false,false,false
local ParagraphInfoServer = InfoTab:CreateParagraph({Title = "Info", Content = "Loading"})
local DistanceForKillAura = 25
local DistanceForAutoChopTree = 25
Rayfield:Notify({
   Title = "Cheat Version",
   Content = "V.0.19",
   Duration = 2.5,
   Image = "rewind",
})
local function DragItem(Item)
game:GetService("ReplicatedStorage").RemoteEvents.RequestStartDraggingItem:FireServer(Item)
wait(0.0000001)
game:GetService("ReplicatedStorage").RemoteEvents.StopDraggingItem:FireServer(Item)
end
local function getServerInfo()
	local Players = game:GetService("Players")
	local playerCount = #Players:GetPlayers()
local maxPlayers = game:GetService("Players").MaxPlayers
local isStudio = game:GetService("RunService"):IsStudio()

	return {
		PlaceId = game.PlaceId,
		JobId = game.JobId,
		IsStudio = isStudio,
		CurrentPlayers = playerCount,
MaxPlayers =maxPlayers
	}
end
local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")

local IYMouse = Players.LocalPlayer:GetMouse()
local FLYING = false
local QEfly = true
local iyflyspeed = 1
local vehicleflyspeed = 1

local function sFLY(vfly)
	repeat wait() until Players.LocalPlayer and Players.LocalPlayer.Character and Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart") and Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
	repeat wait() until IYMouse
	if flyKeyDown or flyKeyUp then flyKeyDown:Disconnect() flyKeyUp:Disconnect() end

	local T = Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart")
	local CONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
	local lCONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
	local SPEED = 0

	local function FLY()
		FLYING = true
		local BG = Instance.new('BodyGyro')
		local BV = Instance.new('BodyVelocity')
		BG.P = 9e4
		BG.Parent = T
		BV.Parent = T
		BG.MaxTorque = Vector3.new(9e9, 9e9, 9e9)
		BG.CFrame = T.CFrame
		BV.Velocity = Vector3.new(0, 0, 0)
		BV.MaxForce = Vector3.new(9e9, 9e9, 9e9)
		task.spawn(function()
			repeat wait()
				if not vfly and Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid') then
					Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid').PlatformStand = true
				end
				if CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 or CONTROL.Q + CONTROL.E ~= 0 then
					SPEED = 50
				elseif not (CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 or CONTROL.Q + CONTROL.E ~= 0) and SPEED ~= 0 then
					SPEED = 0
				end
				if (CONTROL.L + CONTROL.R) ~= 0 or (CONTROL.F + CONTROL.B) ~= 0 or (CONTROL.Q + CONTROL.E) ~= 0 then
					BV.Velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (CONTROL.F + CONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(CONTROL.L + CONTROL.R, (CONTROL.F + CONTROL.B + CONTROL.Q + CONTROL.E) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
					lCONTROL = {F = CONTROL.F, B = CONTROL.B, L = CONTROL.L, R = CONTROL.R}
				elseif (CONTROL.L + CONTROL.R) == 0 and (CONTROL.F + CONTROL.B) == 0 and (CONTROL.Q + CONTROL.E) == 0 and SPEED ~= 0 then
					BV.Velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (lCONTROL.F + lCONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(lCONTROL.L + lCONTROL.R, (lCONTROL.F + lCONTROL.B + CONTROL.Q + CONTROL.E) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
				else
					BV.Velocity = Vector3.new(0, 0, 0)
				end
				BG.CFrame = workspace.CurrentCamera.CoordinateFrame
			until not FLYING
			CONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
			lCONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
			SPEED = 0
			BG:Destroy()
			BV:Destroy()
			if Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid') then
				Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid').PlatformStand = false
			end
		end)
	end
	flyKeyDown = IYMouse.KeyDown:Connect(function(KEY)
		if KEY:lower() == 'w' then
			CONTROL.F = (vfly and vehicleflyspeed or iyflyspeed)
		elseif KEY:lower() == 's' then
			CONTROL.B = - (vfly and vehicleflyspeed or iyflyspeed)
		elseif KEY:lower() == 'a' then
			CONTROL.L = - (vfly and vehicleflyspeed or iyflyspeed)
		elseif KEY:lower() == 'd' then 
			CONTROL.R = (vfly and vehicleflyspeed or iyflyspeed)
		elseif QEfly and KEY:lower() == 'e' then
			CONTROL.Q = (vfly and vehicleflyspeed or iyflyspeed)*2
		elseif QEfly and KEY:lower() == 'q' then
			CONTROL.E = -(vfly and vehicleflyspeed or iyflyspeed)*2
		end
		pcall(function() workspace.CurrentCamera.CameraType = Enum.CameraType.Track end)
	end)
	flyKeyUp = IYMouse.KeyUp:Connect(function(KEY)
		if KEY:lower() == 'w' then
			CONTROL.F = 0
		elseif KEY:lower() == 's' then
			CONTROL.B = 0
		elseif KEY:lower() == 'a' then
			CONTROL.L = 0
		elseif KEY:lower() == 'd' then
			CONTROL.R = 0
		elseif KEY:lower() == 'e' then
			CONTROL.Q = 0
		elseif KEY:lower() == 'q' then
			CONTROL.E = 0
		end
	end)
	FLY()
end

local function NOFLY()
	FLYING = false
	if flyKeyDown or flyKeyUp then flyKeyDown:Disconnect() flyKeyUp:Disconnect() end
	if Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid') then
		Players.LocalPlayer.Character:FindFirstChildOfClass('Humanoid').PlatformStand = false
	end
	pcall(function() workspace.CurrentCamera.CameraType = Enum.CameraType.Custom end)
end

local velocityHandlerName = "BodyVelocity"
local gyroHandlerName = "BodyGyro"
local mfly1
local mfly2

local function UnMobileFly()
	pcall(function()
		FLYING = false
		local root = Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart")
		root:FindFirstChild(velocityHandlerName):Destroy()
		root:FindFirstChild(gyroHandlerName):Destroy()
		Players.LocalPlayer.Character:FindFirstChildWhichIsA("Humanoid").PlatformStand = false
		mfly1:Disconnect()
		mfly2:Disconnect()
	end)
end

local function MobileFly()
	UnMobileFly()
	FLYING = true

	local root = Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart")
	local camera = workspace.CurrentCamera
	local v3none = Vector3.new()
	local v3zero = Vector3.new(0, 0, 0)
	local v3inf = Vector3.new(9e9, 9e9, 9e9)

	local controlModule = require(Players.LocalPlayer.PlayerScripts:WaitForChild("PlayerModule"):WaitForChild("ControlModule"))
	local bv = Instance.new("BodyVelocity")
	bv.Name = velocityHandlerName
	bv.Parent = root
	bv.MaxForce = v3zero
	bv.Velocity = v3zero

	local bg = Instance.new("BodyGyro")
	bg.Name = gyroHandlerName
	bg.Parent = root
	bg.MaxTorque = v3inf
	bg.P = 1000
	bg.D = 50

	mfly1 = Players.LocalPlayer.CharacterAdded:Connect(function()
		local bv = Instance.new("BodyVelocity")
		bv.Name = velocityHandlerName
		bv.Parent = root
		bv.MaxForce = v3zero
		bv.Velocity = v3zero

		local bg = Instance.new("BodyGyro")
		bg.Name = gyroHandlerName
		bg.Parent = root
		bg.MaxTorque = v3inf
		bg.P = 1000
		bg.D = 50
	end)

	mfly2 = RunService.RenderStepped:Connect(function()
		root = Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart")
		camera = workspace.CurrentCamera
		if Players.LocalPlayer.Character:FindFirstChildWhichIsA("Humanoid") and root and root:FindFirstChild(velocityHandlerName) and root:FindFirstChild(gyroHandlerName) then
			local humanoid = Players.LocalPlayer.Character:FindFirstChildWhichIsA("Humanoid")
			local VelocityHandler = root:FindFirstChild(velocityHandlerName)
			local GyroHandler = root:FindFirstChild(gyroHandlerName)

			VelocityHandler.MaxForce = v3inf
			GyroHandler.MaxTorque = v3inf
			humanoid.PlatformStand = true
			GyroHandler.CFrame = camera.CoordinateFrame
			VelocityHandler.Velocity = v3none

			local direction = controlModule:GetMoveVector()
			if direction.X > 0 then
				VelocityHandler.Velocity = VelocityHandler.Velocity + camera.CFrame.RightVector * (direction.X * ((iyflyspeed) * 50))
			end
			if direction.X < 0 then
				VelocityHandler.Velocity = VelocityHandler.Velocity + camera.CFrame.RightVector * (direction.X * ((iyflyspeed) * 50))
			end
			if direction.Z > 0 then
				VelocityHandler.Velocity = VelocityHandler.Velocity - camera.CFrame.LookVector * (direction.Z * ((iyflyspeed) * 50))
			end
			if direction.Z < 0 then
				VelocityHandler.Velocity = VelocityHandler.Velocity - camera.CFrame.LookVector * (direction.Z * ((iyflyspeed) * 50))
			end
		end
	end)
end

local function CreateEsp(Char, Color, Text,Parent,number)
	if not Char then return end
	if Char:FindFirstChild("ESP") and Char:FindFirstChildOfClass("Highlight") then return end
	local highlight = Char:FindFirstChildOfClass("Highlight") or Instance.new("Highlight")
	highlight.Name = "ESP_Highlight"
highlight.Adornee = Char
highlight.FillColor = Color
highlight.FillTransparency = 1
highlight.OutlineColor = Color
highlight.OutlineTransparency = 0
highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
highlight.Enabled = true
	highlight.Parent = Char

	
	local billboard = Char:FindFirstChild("ESP") or Instance.new("BillboardGui")
	billboard.Name = "ESP"
	billboard.Size = UDim2.new(0, 50, 0, 25)
	billboard.AlwaysOnTop = true
	billboard.StudsOffset = Vector3.new(0, number, 0)
	billboard.Adornee = Parent
	billboard.Enabled = true
	billboard.Parent = Parent

	
	local label = billboard:FindFirstChildOfClass("TextLabel") or Instance.new("TextLabel")
	label.Size = UDim2.new(1, 0, 1, 0)
	label.BackgroundTransparency = 1
	label.Text = Text
	label.TextColor3 = Color
	label.TextScaled = true
	label.Parent = billboard

	task.spawn(function()
		local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")

local LocalPlayer = Players.LocalPlayer
local Camera = Workspace.CurrentCamera

while highlight and billboard and Parent and Parent.Parent do
	local cameraPosition = Camera and Camera.CFrame.Position
	if cameraPosition and Parent and Parent:IsA("BasePart") then
	local distance = (cameraPosition - Parent.Position).Magnitude
				task.spawn(function()
if ActiveDistanceEsp then
label.Text = Text.." ("..math.floor(distance + 0.5).." m)"
else
label.Text = Text
end
end)

	end

	wait(0.1)
end

	end)
end

local function KeepEsp(Char,Parent)
	if Char and Char:FindFirstChildOfClass("Highlight") and Parent:FindFirstChildOfClass("BillboardGui") then
		Char:FindFirstChildOfClass("Highlight"):Destroy()
		Parent:FindFirstChildOfClass("BillboardGui"):Destroy()
	end
end

local function copyToClipboard(text)
    if setclipboard then
        setclipboard(text)
    else
        warn("setclipboard is not supported in this environment.")
    end
end
local DiscordLink = DiscordTab:CreateButton({
   Name = "Discord Link",
   Callback = function()
copyToClipboard("https://discord.gg/E2TqYRsRP4")
end,
})
local PlayerNoclipToggle = PlayerTab:CreateToggle({
   Name = "Noclip",
   CurrentValue = false,
   Flag = "ButtonNoclip", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
  ActiveNoclip = Value 
task.spawn(function()
while ActiveNoclip do 
task.spawn(function()
if Game.Players.LocalPlayer.Character then
for _, Parts in pairs(Game.Players.LocalPlayer.Character:GetDescendants()) do
if Parts:isA("BasePart") and Parts.CanCollide then
Parts.CanCollide = false
end
end
end
end)
task.wait(0.1)
end 
if Game.Players.LocalPlayer.Character then
for _, Parts in pairs(Game.Players.LocalPlayer.Character:GetDescendants()) do
if Parts:isA("BasePart") and not Parts.CanCollide then
Parts.CanCollide = true
end
end
end
end)
end,
})
local PlayerInfiniteJumpToggle = PlayerTab:CreateToggle({
   Name = "Infinite Jump",
   CurrentValue = false,
   Flag = "ButtonInfiniteJump", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
  ActivateInfiniteJump = Value 
while ActivateInfiniteJump do
local plr = game:GetService('Players').LocalPlayer
	local m = plr:GetMouse()
	m.KeyDown:connect(function(k)
		if ActivateInfiniteJump then
			if k:byte() == 32 then
			humanoid = game:GetService'Players'.LocalPlayer.Character:FindFirstChildOfClass('Humanoid')
			humanoid:ChangeState('Jumping')
			wait()
			humanoid:ChangeState('Seated')
			end
		end
	end)
wait(0.1)
end
end,
})
local EspItemsToggle = EspTab:CreateToggle({
   Name = "Items Esp",
   CurrentValue = false,
   Flag = "EspItems",
   Callback = function(Value)
  ActiveEspItems = Value 
task.spawn(function()
while ActiveEspItems do 
task.spawn(function()
 for _,Obj in pairs(Game.Workspace.Items:GetChildren()) do 
if Obj:isA("Model") and Obj.PrimaryPart and not Obj:FindFirstChildOfClass("Highlight") and not Obj.PrimaryPart:FindFirstChildOfClass("BillboardGui") then
CreateEsp(Obj,Color3.fromRGB(255,255,0),Obj.Name,Obj.PrimaryPart) 
end 
end
end)
task.wait(0.1)
end task.spawn(function()
 for _,Obj in pairs(Game.Workspace.Items:GetChildren()) do 
if Obj:isA("Model") and Obj.PrimaryPart and  Obj:FindFirstChildOfClass("Highlight") and Obj.PrimaryPart:FindFirstChildOfClass("BillboardGui") then
KeepEsp(Obj,Obj.PrimaryPart)
end 
end
end)
end)
end,
})
local EspEnemyToggle = EspTab:CreateToggle({
   Name = "Enemy Esp",
   CurrentValue = false,
   Flag = "EspEnemy",
   Callback = function(Value)
  ActiveEspEnemy = Value 
task.spawn(function()
while ActiveEspEnemy do 
task.spawn(function()
 for _,Obj in pairs(Game.Workspace.Characters:GetChildren()) do 
if Obj:isA("Model") and Obj.PrimaryPart and (Obj.Name ~= "Lost Child" or Obj.Name ~= "Lost Child2" or Obj.Name ~= "Lost Child3" or Obj.Name ~= "Lost Child4" or Obj.Name ~= "Pelt Trader") and not Obj:FindFirstChildOfClass("Highlight") and not Obj.PrimaryPart:FindFirstChildOfClass("BillboardGui") then
CreateEsp(Obj,Color3.fromRGB(255,0,0),Obj.Name,Obj.PrimaryPart) 
end 
end
end)
task.wait(0.1)
end task.spawn(function()
 for _,Obj in pairs(Game.Workspace.Characters:GetChildren()) do 
if Obj:isA("Model") and Obj.PrimaryPart and (Obj.Name ~= "Lost Child" or Obj.Name ~= "Lost Child2" or Obj.Name ~= "Lost Child3" or Obj.Name ~= "Lost Child4" or Obj.Name ~= "Pelt Trader") and Obj:FindFirstChildOfClass("Highlight") and Obj.PrimaryPart:FindFirstChildOfClass("BillboardGui") then
KeepEsp(Obj,Obj.PrimaryPart)
end 
end
end)
end)
end,
})
local EspChildrensToggle = EspTab:CreateToggle({
   Name = "Childrens Esp",
   CurrentValue = false,
   Flag = "EspChildrens",
   Callback = function(Value)
  ActiveEspChildren = Value 
task.spawn(function()
while ActiveEspChildren do 
task.spawn(function()
 for _,Obj in pairs(Game.Workspace.Characters:GetChildren()) do 
if Obj:isA("Model") and Obj.PrimaryPart and (Obj.Name == "Lost Child" or Obj.Name == "Lost Child2" or Obj.Name == "Lost Child3" or Obj.Name == "Lost Child4") and not Obj:FindFirstChildOfClass("Highlight") and not Obj.PrimaryPart:FindFirstChildOfClass("BillboardGui") then
CreateEsp(Obj,Color3.fromRGB(0,255,0),Obj.Name,Obj.PrimaryPart) 
end 
end
end)
task.wait(0.1)
end task.spawn(function()
 for _,Obj in pairs(Game.Workspace.Characters:GetChildren()) do 
if Obj:isA("Model") and Obj.PrimaryPart and (Obj.Name == "Lost Child" or Obj.Name == "Lost Child2" or Obj.Name == "Lost Child3" or Obj.Name == "Lost Child4") and Obj:FindFirstChildOfClass("Highlight") and Obj.PrimaryPart:FindFirstChildOfClass("BillboardGui") then
KeepEsp(Obj,Obj.PrimaryPart)
end 
end
end)
end)
end,
})
local EspPeltTraderToggle = EspTab:CreateToggle({
   Name = "Pelt Trader Esp",
   CurrentValue = false,
   Flag = "EspPeltTrader",
   Callback = function(Value)
  ActiveEspPeltTrader = Value 
task.spawn(function()
while ActiveEspPeltTrader do 
task.spawn(function()
 for _,Obj in pairs(Game.Workspace.Characters:GetChildren()) do 
if Obj:isA("Model") and Obj.PrimaryPart and Obj.Name == "Pelt Trader" and not Obj:FindFirstChildOfClass("Highlight") and not Obj.PrimaryPart:FindFirstChildOfClass("BillboardGui") then
CreateEsp(Obj,Color3.fromRGB(0,255,255),Obj.Name,Obj.PrimaryPart) 
end 
end
end)
task.wait(0.1)
end task.spawn(function()
 for _,Obj in pairs(Game.Workspace.Characters:GetChildren()) do 
if Obj:isA("Model") and Obj.PrimaryPart and Obj.Name == "Pelt Trader" and Obj:FindFirstChildOfClass("Highlight") and Obj.PrimaryPart:FindFirstChildOfClass("BillboardGui") then
KeepEsp(Obj,Obj.PrimaryPart)
end 
end
end)
end)
end,
})
local ButtonBringAllItems = BringItemTab:CreateButton({
   Name = "Bring All Items",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
task.spawn(function()
DragItem(Obj)
end)
end  
end
end)
end,
})
local ButtonBringAllLogs = BringItemTab:CreateButton({
   Name = "Bring All Logs",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Log" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end  
end
end)
end,
})
local ButtonBringAllCoal = BringItemTab:CreateButton({
   Name = "Bring All Coal",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Coal" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end 
wait(0.1)
end
end)
end,
})
local ButtonBringAllFuelCanister = BringItemTab:CreateButton({
   Name = "Bring All Fuel Canister",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Fuel Canister" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end 
end
end)
end,
})
local ButtonBringAllCarrot = BringItemTab:CreateButton({
   Name = "Bring All Carrot",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Carrot" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end 
end
end)
end,
})
local ButtonBringAllFuel = BringItemTab:CreateButton({
   Name = "Bring All Fuel",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if (Obj.Name == "Log" or Obj.Name == "Fuel Canister" or Obj.Name == "Coal" or Obj.Name == "Oil Barrel") and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end   
end
end)
end,
})
local ButtonBringAllScraps = BringItemTab:CreateButton({
   Name = "Bring All Scraps",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if (Obj.Name == "Tyre" or Obj.Name == "Sheet Metal" or Obj.Name == "Broken Fan" or Obj.Name == "Bolt" or Obj.Name == "Old Radio" or Obj.Name == "UFO Junk" or Obj.Name == "UFO Scrap" or Obj.Name == "Broken Microwave") and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end 
end
end)
end,
})
local ButtonBringAllAmmo = BringItemTab:CreateButton({
   Name = "Bring All Ammo",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if (Obj.Name == "Rifle Ammo" or Obj.Name == "Revolver Ammo") and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end 
end
end)
end,
})
local ButtonBringAllGuns = BringItemTab:CreateButton({
   Name = "Bring All Guns",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if (Obj.Name == "Rifle" or Obj.Name == "Revolver") and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end  
end
end)
end,
})
local ButtonBringAllChildren = BringItemTab:CreateButton({
   Name = "Bring All Children",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Characters:GetChildren()) do
if (Obj.Name == "Lost Child" or Obj.Name == "Lost Child2" or Obj.Name == "Lost Child3" or Obj.Name == "Lost Child4" ) and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end  
end
end)
end,
})
local ButtonBringAllFoods = BringItemTab:CreateButton({
   Name = "Bring All Foods",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if (Obj.Name == "Cake" or Obj.Name == "Carrot" or Obj.Name == "Morsel" or Obj.Name == "Meat? Sandwich") and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end  
end
end)
end,
})
local ButtonBringAllBody = BringItemTab:CreateButton({
   Name = "Bring All Body",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if (Obj.Name == "Leather Body" or Obj.Name == "Iron Body") and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end    
end
end)
end,
})
local ButtonBringAllBandage = BringItemTab:CreateButton({
   Name = "Bring All Bandage",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Bandage" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end
wait(0.1)
end
end)
end,
})
local ButtonBringAllMedkit = BringItemTab:CreateButton({
   Name = "Bring All Medkit",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "MedKit" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end
end
end)
end,
})
local ButtonBringAllCoins = BringItemTab:CreateButton({
   Name = "Bring All Coins",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Coin Stack" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end
end
end)
end,
})
local ButtonBringAllOldRadio = BringItemTab:CreateButton({
   Name = "Bring All Old Radio",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Old Radio" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end 
end
end)
end,
})
local ButtonBringAllTyre = BringItemTab:CreateButton({
   Name = "Bring All Tyre",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Tyre" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end 
end
end)
end,
})
local ButtonBringAllBrokenFan = BringItemTab:CreateButton({
   Name = "Bring All Broken Fan",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Broken Fan" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end
end
end)
end,
})
local ButtonBringAllBrokenMicrowave = BringItemTab:CreateButton({
   Name = "Bring All Broken Microwave",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Broken Microwave" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end 
end
end)
end,
})
local ButtonBringAllBolt = BringItemTab:CreateButton({
   Name = "Bring All Bolt",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Bolt" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end
end
end)
end,
})
local ButtonBringAllBrokenMicrowave = BringItemTab:CreateButton({
   Name = "Bring All Broken Microwave",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Broken Microwave" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end
end
end)
end,
})
local ButtonBringAllSheetMetal = BringItemTab:CreateButton({
   Name = "Bring All Sheet Metal",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Sheet Metal" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end
end
end)
end,
})
local ButtonBringAllSeedBox = BringItemTab:CreateButton({
   Name = "Bring All SeedBox",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Seed Box" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end   
end
end)
end,
})
local ButtonBringAllChair = BringItemTab:CreateButton({
   Name = "Bring All Chair",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == "Chair" and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end 
end
end)
end,
})
local TextBoxText = ""
local isInTheMap = "no"
local HowManyItemCanShowUp = 0
local Label = BringItemTab:CreateLabel("Item Is In The Map: No (x"..HowManyItemCanShowUp..")", "rewind")
local TextboxBringNameItem = BringItemTab:CreateInput({
   Name = "TextBox",
   CurrentValue = "",
   PlaceholderText = "Put a name only 1 for bring it on you(use the esp for the name)",
   RemoveTextAfterFocusLost = false,
   Flag = "Textbox1",
   Callback = function(Text)
  TextBoxText = Text
isInTheMap = "no"
HowManyItemCanShowUp = 0
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == TextBoxText and Obj:isA("Model") and Obj.PrimaryPart then 
HowManyItemCanShowUp = HowManyItemCanShowUp +1
isInTheMap ="yes"
end 
end
Label:Set("Item Is In The Map: "..isInTheMap.." (x"..HowManyItemCanShowUp..")","rewind")
   end,
})
local ButtonBringAllThingsNamedInTextBox = BringItemTab:CreateButton({
   Name = "Bring All the item with the name you choosed",
   Callback = function(Value)
task.spawn(function()
for _, Obj in pairs(game.workspace.Items:GetChildren()) do
if Obj.Name == TextBoxText and Obj:isA("Model") and Obj.PrimaryPart then 
Obj.PrimaryPart.CFrame = game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame
DragItem(Obj)
end 
end
end)
end,
})

local ValueSpeed = 16
local OldSpeed = Game.Players.LocalPlayer.Character.Humanoid.WalkSpeed
local PlayerSpeedSlider = PlayerTab:CreateSlider({
   Name = "Player Speed",
   Range = {0, 500},
   Increment = 1,
   Suffix = "Speeds",
   CurrentValue = 16,
   Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
CurrentValue = Value
ValueSpeed = Value
end,  ValueSpeed = CurrentValue,
})
local PlayerActiveModifyingSpeedToggle = PlayerTab:CreateToggle({
   Name = "Active Modifying Player Speed",
   CurrentValue = false,
   Flag = "ButtonSpeed", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
  ActiveSpeedBoost = Value task.spawn(function()
while ActiveSpeedBoost do
Game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = ValueSpeed
task.wait(0.1)
end
Game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = OldSpeed
end)
end,
})
local PlayerFlySpeedSlider = PlayerTab:CreateSlider({
   Name = "Fly Speed(Recommended to put 1 or below 5!)",
   Range = {0, 10},
   Increment = 0.1,
   Suffix = "Fly Speed",
   CurrentValue = 1,
   Flag = "Slider2", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
CurrentValue = Value
iyflyspeed = Value
end,  iyflyspeed = CurrentValue,
})

local PlayerFlyToggle = PlayerTab:CreateToggle({
   Name = "Fly",
   CurrentValue = false,
   Flag = "ButtonFly", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
  ActivateFly = Value 
task.spawn(function()
if not FLYING and ActivateFly then
			if UserInputService.TouchEnabled then
				MobileFly()
			else
task.spawn(function()
if not AlrActivatedFlyPC then 
AlrActivatedFlyPC = true
Rayfield:Notify({
   Title = "Fly",
   Content = "When you enable to fly you can press F to fly/unfly (it won't disable the button!)",
   Duration = 5,
   Image = "rewind",
})
end
end)
				NOFLY()
				wait()
				sFLY()
			end
		elseif FLYING and not ActivateFly then
			if UserInputService.TouchEnabled then
				UnMobileFly()
			else
				NOFLY()
			end
		end
end)
end,
})
UserInputService.InputBegan:Connect(function(input, processed)
	if processed then return end
	if input.KeyCode == Enum.KeyCode.F then
		if not FLYING and ActivateFly then
			if UserInputService.TouchEnabled then
				MobileFly()
			else
				NOFLY()
				wait()
				sFLY()
			end
		elseif FLYING and ActivateFly then
			if UserInputService.TouchEnabled then
				UnMobileFly()
			else
				NOFLY()
			end
		end
	end
end)
local NoCooldownpromptToggle = PlayerTab:CreateToggle({
   Name = "Instant Prompt",
   CurrentValue = false,
   Flag = "NoCooldownPrompt1", 
   Callback = function(Value)
ActiveNoCooldownPrompt = Value 
task.spawn(function()
if ActiveNoCooldownPrompt then
for _,Assets in pairs(Game.Workspace:GetDescendants()) do  
if Assets:isA("ProximityPrompt") and Assets.HoldDuration ~= 0 then 
Assets:SetAttribute("HoldDurationOld",Assets.HoldDuration)
Assets.HoldDuration = 0
end 
end  
else 
for _,Assets in pairs(Game.Workspace:GetDescendants()) do  
if Assets:isA("ProximityPrompt") and Assets:GetAttribute("HoldDurationOld") and Assets:GetAttribute("HoldDurationOld") ~= 0 then 
Assets.HoldDuration = Assets:GetAttribute("HoldDurationOld")
end 
end  
end
end)
end,
})
local NoFogToggle = PlayerTab:CreateToggle({
   Name = "No Fog",
   CurrentValue = false,
   Flag = "NoFog1", 
   Callback = function(Value)
ActiveNoFog = Value 
task.spawn(function()
while ActiveNoFog do
for _, part in pairs(Workspace.Map.Boundaries:GetChildren()) do 
	if part:isA("Part") then
		part:Destroy()
	end
end  
wait(0.1)
end
end)
end,
})
local ParagraphNote = GameTab:CreateParagraph({Title = "Note", Content = "For Auto Chop Tree and kill aura work equip any of axe and it will work!"})
local PlayerKillAuraDistanceSlider = GameTab:CreateSlider({
   Name = "Distance For Kill Aura",
   Range = {25, 10000},
   Increment = 0.1,
   Suffix = "Distance",
   CurrentValue = 25,
   Flag = "KillAuraD2", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
CurrentValue = Value
DistanceForKillAura = Value
end,  DistanceForKillAura = CurrentValue,
})
local KillAuraToggle = GameTab:CreateToggle({
   Name = "Kill Aura",
   CurrentValue = false,
   Flag = "KillAura1", 
   Callback = function(Value)
ActiveKillAura = Value 
task.spawn(function()
while ActiveKillAura do 
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local hrp = character:WaitForChild("HumanoidRootPart")
local weapon = (player.Inventory:FindFirstChild("Old Axe") or player.Inventory:FindFirstChild("Good Axe") or player.Inventory:FindFirstChild("Strong Axe") or player.Inventory:FindFirstChild("Chainsaw"))
task.spawn(function()
for _, bunny in pairs(workspace.Characters:GetChildren()) do
	if bunny:IsA("Model") and bunny.PrimaryPart then
		local distance = (bunny.PrimaryPart.Position - hrp.Position).Magnitude
		if distance <= DistanceForKillAura then
			local result = game:GetService("ReplicatedStorage").RemoteEvents.ToolDamageObject:InvokeServer(bunny, weapon, 999, hrp.CFrame)
		end
	end
end
end)
wait(0.1)
end
end)
end,
})
local PlayerDistanceAutoChopTreeSlider = GameTab:CreateSlider({
   Name = "Distance For Auto Chop Tree(Recommended to put below 250 if you have strong axe or chainsaw)",
   Range = {0, 1000},
   Increment = 0.1,
   Suffix = "Distance",
   CurrentValue = 25,
   Flag = "AutoChopTreeDistance2", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
CurrentValue = Value
DistanceForAutoChopTree = Value
end,  DistanceForAutoChopTree = CurrentValue,
})
local AutoChopTreeToggle = GameTab:CreateToggle({
   Name = "Auto Chop Tree",
   CurrentValue = false,
   Flag = "AutoChopTree1", 
   Callback = function(Value)
ActiveAutoChopTree = Value 
task.spawn(function()
while ActiveAutoChopTree do 
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local hrp = character:WaitForChild("HumanoidRootPart")
local weapon = (player.Inventory:FindFirstChild("Old Axe") or player.Inventory:FindFirstChild("Good Axe") or player.Inventory:FindFirstChild("Strong Axe") or player.Inventory:FindFirstChild("Chainsaw"))
task.spawn(function()
for _, bunny in pairs(workspace.Map.Foliage:GetChildren()) do
	if bunny:IsA("Model") and (bunny.Name == "Small Tree" or bunny.Name == "TreeBig1" or bunny.Name == "TreeBig2")  and bunny.PrimaryPart then
		local distance = (bunny.PrimaryPart.Position - hrp.Position).Magnitude
		if distance <= DistanceForAutoChopTree then
			local result = game:GetService("ReplicatedStorage").RemoteEvents.ToolDamageObject:InvokeServer(bunny, weapon, 999, hrp.CFrame)
		end
	end
end 
end)
task.spawn(function()
for _, bunny in pairs(workspace.Map.Landmarks:GetChildren()) do
	if bunny:IsA("Model") and (bunny.Name == "Small Tree" or bunny.Name == "TreeBig1" or bunny.Name == "TreeBig2")  and bunny.PrimaryPart then
		local distance = (bunny.PrimaryPart.Position - hrp.Position).Magnitude
		if distance <= DistanceForAutoChopTree then
			local result = game:GetService("ReplicatedStorage").RemoteEvents.ToolDamageObject:InvokeServer(bunny, weapon, 999, hrp.CFrame)
			end
	end
end
end)
wait(0.1)
end
end)
end,
})
local ButtonTeleportToCampfire = PlayerTab:CreateButton({
   Name = "Teleport to campfire",
   Callback = function(Value)
task.spawn(function()
 game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame = Workspace.Map.Campground.MainFire.PrimaryPart.CFrame
end)
end,
})
local ButtonUnloadCheat = SettingsTab:CreateButton({
   Name = "Unload Cheat",
   Callback = function()
  Rayfield:Destroy()
end,
})
local ActiveEspDistanceToggle = SettingsTab:CreateToggle({
   Name = "Active Distance for esp",
   CurrentValue = false,
   Flag = "EspDistance",
   Callback = function(Value)
  ActiveDistanceEsp = Value 
end,
})
local Themes = {
   ["Default"] = "Default",
   ["Amber Glow"] = "AmberGlow",
   ["Amethyst"] = "Amethyst",
   ["Bloom"] = "Bloom",
   ["Dark Blue"] = "DarkBlue",
   ["Green"] = "Green",
   ["Light"] = "Light",
   ["Ocean"] = "Ocean",
   ["Serenity"] = "Serenity"
}

local Dropdown = SettingsTab:CreateDropdown({
   Name = "Change Theme",
   Options = {"Default", "Amber Glow", "Amethyst", "Bloom", "Dark Blue", "Green", "Light", "Ocean", "Serenity"},
   CurrentOption = selectedTheme,  -- pour afficher ce qui est réellement chargé
   Flag = "ThemeSelection",
   Callback = function(Selected)
      local ident = Themes[Selected[1]]
      Window.ModifyTheme(ident)  -- <— Applique le thème en direct
   end, 
})
Rayfield:LoadConfiguration()
task.spawn(function()
while true do
	task.wait(1) 
task.spawn(function()
	local updatedInfo = getServerInfo()
	local updatedContent = string.format(
		"📌 PlaceId: %s\n🔑 JobId: %s\n🧪 IsStudio: %s\n👥 Players: %d/%d",
		updatedInfo.PlaceId,
		updatedInfo.JobId,
		
		tostring(updatedInfo.IsStudio),
		updatedInfo.CurrentPlayers,
updatedInfo.MaxPlayers
	)

	ParagraphInfoServer:Set({
		Title = "Info",
		Content = updatedContent
	})
end)
end

end)