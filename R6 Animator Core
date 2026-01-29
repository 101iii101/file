--//====================================================\\--
--||                Animator6D Pro V4 (R6)             ||--
--||  Author: gObl00x + GPT-5                         ||--
--||  Features: universal rig, local cache, safe play  ||--
--|| Ya sorry, I dont want to die cuz writing this shit on a shitty phone for 90 years, thanks GPT
--\\====================================================//--

if getgenv().Animator6DLoadedPro then return end
getgenv().Animator6DLoadedPro = true

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local hum = character:WaitForChild("Humanoid")

-- ========== LOCAL CACHE / 403 EVASION ==========
local LocalAssetCache = {}
local fullModel = nil
pcall(function()
	fullModel = game:GetObjects("rbxassetid://107495486817639")[1]
	if fullModel then
		fullModel.Parent = workspace
	end
end)

local function LoadLocalAsset(id)
	id = tostring(id):gsub("^rbxassetid://", "")
	if LocalAssetCache[id] then
		return LocalAssetCache[id]
	end

	local found = fullModel and fullModel:FindFirstChild(id, true)
	if found then
		LocalAssetCache[id] = found
		warn("[Animator6D] ✅ Loaded from local cache:", id)
		return found
	end

	local ok, obj = pcall(function()
		return game:GetObjects("rbxassetid://" .. id)[1]
	end)
	if ok and obj then
		LocalAssetCache[id] = obj
		warn("[Animator6D] ✅ Loaded via GetObjects👍👍:", id)
		return obj
	end

	warn("[Animator6D] ts is bad, failed to load animation:", id)
	return nil
end
-- ===============================================

local R6Map = {
	["Head"] = "Neck",
	["Torso"] = "RootJoint",
	["Right Arm"] = "Right Shoulder",
	["Left Arm"] = "Left Shoulder",
	["Right Leg"] = "Right Hip",
	["Left Leg"] = "Left Hip"
}

-- ========== KEYFRAME PARSER  ==========
local function ConvertToTable(kfs)
	if not (kfs and typeof(kfs) == "Instance" and kfs:IsA("KeyframeSequence")) then
		if typeof(kfs) == "Instance" then
			for _, obj in ipairs(kfs:GetDescendants()) do
				if obj:IsA("KeyframeSequence") then
					kfs = obj
					break
				end
			end
		end
	end

	assert(kfs and typeof(kfs) == "Instance" and kfs:IsA("KeyframeSequence"), "Expected KeyframeSequence")

	local seq = {}
	for _, frame in ipairs(kfs:GetKeyframes()) do
		local entry = { Time = frame.Time, Data = {} }
		for _, pose in ipairs(frame:GetDescendants()) do
			if pose:IsA("Pose") and pose.Weight > 0 then
				entry.Data[pose.Name] = { CFrame = pose.CFrame }
			end
		end
		table.insert(seq, entry)
	end
	table.sort(seq, function(a, b) return a.Time < b.Time end)
	return seq, kfs.Loop
end

-- ========== MOTOR MAP ==========
local function BuildMotorMap(rig)
	local map, lower = {}, {}
	for _, m in ipairs(rig:GetDescendants()) do
		if m:IsA("Motor6D") then
			map[m.Name] = m
			lower[string.lower(m.Name)] = m
		end
	end
	return map, lower
end

local function FindMotor(poseName, map, lower)
	local match = R6Map[poseName] or poseName
	return map[match] or lower[string.lower(match)]
end

-- ========== ANIM PLAYER ==========
local AnimPlayer = {}
AnimPlayer.__index = AnimPlayer

function AnimPlayer.new(rig, kfs)
	local self = setmetatable({}, AnimPlayer)
	self.rig = rig
	self.seq, self.looped = ConvertToTable(kfs)
	self.map, self.lower = BuildMotorMap(rig)
	self.time, self.playing = 0, false
	self.length = self.seq[#self.seq].Time
	self.speed = 1
	self.savedC0 = {}
	for _, m in pairs(self.map) do
		self.savedC0[m] = m.C0
	end
	return self
end

function AnimPlayer:Play(speed, loop)
	if self.playing then return end
	self.playing, self.speed = true, speed or 1
	self.looped = (loop == nil) and true or loop

	self.conn = RunService.Heartbeat:Connect(function(dt)
		if not self.playing then return end
		self.time += dt * self.speed

		if self.time > self.length then
			if self.looped then
				self.time -= self.length
			else
				self:Stop(true)
				return
			end
		end

		local prev = self.seq[1]
		for i = 1, #self.seq do
			if self.seq[i].Time <= self.time then
				prev = self.seq[i]
			else
				break
			end
		end

		for joint, data in pairs(prev.Data) do
			local motor = FindMotor(joint, self.map, self.lower)
			if motor then
				pcall(function()
					motor.C0 = self.savedC0[motor] * data.CFrame
				end)
			end
		end
	end)
end

function AnimPlayer:Stop(restore)
	self.playing = false
	if self.conn then self.conn:Disconnect() self.conn = nil end
	if restore then
		for motor, origC0 in pairs(self.savedC0) do
			pcall(function() motor.C0 = origC0 end)
		end
	else
		for _, m in pairs(self.map) do
			pcall(function() m.Transform = CFrame.new() end)
		end
	end
end

-- ========== DISABLE DEFAULT ANIMS ==========
local function disableDefaultAnimations(char)
	if not hum then return end
	for _, track in ipairs(hum:GetPlayingAnimationTracks()) do
		track:Stop(0)
	end
	local animScript = char:FindFirstChild("Animate")
	if animScript then animScript.Disabled = true end
	local animator = hum:FindFirstChildOfClass("Animator")
	if animator then animator:Destroy() end
end

-- ========== GLOBAL INTERFACE ==========
getgenv().Animator6D = function(idOrInstance, speed, looped)
	local kfs
	if typeof(idOrInstance) == "Instance" then
		kfs = idOrInstance:IsA("KeyframeSequence") and idOrInstance or idOrInstance:FindFirstChildOfClass("KeyframeSequence")
	else
		local asset = LoadLocalAsset(idOrInstance)
		if asset then
			kfs = asset:FindFirstChildOfClass("KeyframeSequence") or asset
		end
	end

	if not kfs then
		warn("[Animator6D] yo sorry could not load animation:", idOrInstance)
		return
	end

	disableDefaultAnimations(character)

	if getgenv().currentAnimator6D then
		pcall(function()
			getgenv().currentAnimator6D:Stop(true)
		end)
	end

	local anim = AnimPlayer.new(character, kfs)
	getgenv().currentAnimator6D = anim
	anim:Play(speed or 1, looped)
end

getgenv().Animator6DStop = function()
	if getgenv().currentAnimator6D then
		pcall(function() getgenv().currentAnimator6D:Stop(true) end)
		getgenv().currentAnimator6D = nil
	end
end

-- ========== NOTIFY ==========
warn("[Animator6D Pro V4] ya.. Allah hotbar")
pcall(function()
	game:GetService("StarterGui"):SetCore("SendNotification", {
		Title = "Animator6D Pro V4",
		Text = "Loaded with Local Cache Support!",
		Duration = 5
	})
end)

--
--[[
(pls, If ur down here, read these instructions)
Instructions:
--
If u want to play the anim outside ts loadstring, then:
getgenv().Animator6D(1234567890, 1, true) -- idOrInstance, Speed, Looped? --
--
If u will be using an instance and not an ID, then:
local animInstance = game:GetObjects("rbxassetid://ID")[1]..Here the KeyframeSequence Path -- replace ID with the ID --
getgenv().Animator6D(animInstance, 1, true) -- or false if u want the anim to have a loop
--
If u want to stop the anim outside ts loadstring, then:
getgenv().Animator6DStop()
--]]
