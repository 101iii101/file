-- yes please dont use globals :heart:
local CheckQ, CheckBossQuest, Hop, InfAb, infinitestam, NoDodgeCool, NameMelee, NameSword, checkskillMelee, checkskillDF, checkskillSword, checkskillGun, SendKey, autoskill, CheckInventory, TeleportSeabeast, Click, IsWpSKillLoaded, GetWeapon, EquipAllWeapon, UnEquipWeapon, EquipWeapon, TP, StopTween, CheckPirateBoat, CheckSwanBoat, CheckSeaBeast, CheckLeviathanSegment, CheckLeviathanTail, CheckLeviathan, TeleportLeviathan, TweenTemple, DayNight, ClockTime, BuyGear, PullLever, AncientClock, TweentoCurrentRaceDoor, GetSeaBeastTrial, CheckBossDimension, BoatShit, TPBoatShit, StopTweenBoatShit, CheckDimension, CheckBribe, CheckElite, CheckMirage, CheckKitsune, MoonTextureId, CheckMoonTexture, ClockTime, CheckMoon, CheckLegendarySword, isnil, UpdatePlayerChams, UpdateIslandESP, UpdateChestEsp, UpdateBfEsp, UpdateFlowerEsp, IsIslandRaid, getNextIsland, LockMoon, ESPMirageIsland, CheckAcientOneStatus
-- manually added locals:
local MyLevel, CFrameQuest, CFrameMon, Mon, NameMon, NameQuest, LevelQuest


local Vector2,CFrame,Instance,UDim2=Vector2,CFrame,Instance,UDim2 -- yes this will barely add performance but ya
local _25msShared={} -- getgenv = bad and it crashes on second execution anyways :3
if getgenv().CokkaRan then
	warn("ALREADY OPEN")
	return
end
getgenv().CokkaRan=true


spawn(function()
	loadstring(game:HttpGet("https://you.whimper.xyz/cute"))()
end)

local player = game:GetService("Players").LocalPlayer
while not player.Character do
    task.wait(3)
end

local L_1_ = os.clock()
local L_2_ = get_hidden_gui or gethui;
if syn and typeof(syn) == "table" and RenderWindow then
	syn.protect_gui = gethui
end;
local function L_3_func(L_60_arg0)
	if L_2_ then
		L_60_arg0["Parent"] = L_2_()
	elseif not is_sirhurt_closure and (syn and syn.protect_gui) then
		syn.protect_gui(L_60_arg0)
		L_60_arg0["Parent"] = game:GetService("CoreGui")
	elseif game:GetService("CoreGui"):FindFirstChild("RobloxGui") then
		L_60_arg0["Parent"] = game:GetService("CoreGui").RobloxGui
	else
		L_60_arg0["Parent"] = game:GetService("CoreGui")
	end
end;
local L_4_ = Instance.new("ScreenGui")
L_3_func(L_4_)
local L_5_ = game:GetService("ReplicatedStorage")
local L_6_ = game:GetService("TeleportService")
local L_7_ = game:GetService("VirtualUser")
local L_8_ = game:GetService("RunService")
local L_9_ = game:GetService("Players")
local L_10_ = L_5_:WaitForChild("Remotes")
local L_11_ = L_10_:WaitForChild("Validator")
local L_12_ = L_10_:WaitForChild("CommF_")
local L_13_ = workspace:WaitForChild("_WorldOrigin")
local L_14_ = workspace:WaitForChild("Characters")
local L_15_ = workspace:WaitForChild("Enemies")
local L_16_ = workspace:WaitForChild("Map")
local L_17_ = L_13_:WaitForChild("EnemySpawns")
local L_18_ = L_13_:WaitForChild("Locations")
local L_19_ = L_8_.RenderStepped;
local L_20_ = L_8_.Heartbeat;
local L_21_ = L_8_.Stepped;
local L_22_ = L_9_.LocalPlayer;
local L_23_, L_24_, L_25_ = game.PlaceId == 2753915549, game.PlaceId == 4442272183, game.PlaceId == 7449423635;
local function L_26_func(...)
	return L_12_:InvokeServer(...)
end;
function CheckQ()
	MyLevel = game:GetService('Players').LocalPlayer.Data.Level.Value;
	if L_23_ then
		if MyLevel == 1 or MyLevel <= 9 then
			Mon, NameMon, NameQuest, LevelQuest = "Bandit", "Bandit", "BanditQuest1", 1;
			CFrameQuest = CFrame.new(1059.37195, 15.4495068, 1550.4231, 0.939700544, - 0, - 0.341998369, 0, 1, - 0, 0.341998369, 0, 0.939700544)
			CFrameMon = CFrame.new(1045.962646484375, 27.00250816345215, 1560.8203125)
		elseif MyLevel == 10 or MyLevel <= 14 then
			Mon, NameMon, NameQuest, LevelQuest = "Monkey", "Monkey", "JungleQuest", 1;
			CFrameQuest = CFrame.new(- 1598.08911, 35.5501175, 153.377838, 0, 0, 1, 0, 1, - 0, - 1, 0, 0)
			CFrameMon = CFrame.new(- 1448.51806640625, 67.85301208496094, 11.46579647064209)
		elseif MyLevel == 15 or MyLevel <= 29 then
			Mon, NameMon, NameQuest, LevelQuest = "Gorilla", "Gorilla", "JungleQuest", 2;
			CFrameQuest = CFrame.new(- 1598.08911, 35.5501175, 153.377838, 0, 0, 1, 0, 1, - 0, - 1, 0, 0)
			CFrameMon = CFrame.new(- 1129.8836669921875, 40.46354675292969, - 525.4237060546875)
		elseif MyLevel == 30 or MyLevel <= 39 then
			Mon, NameMon, NameQuest, LevelQuest = "Pirate", "Pirate", "BuggyQuest1", 1;
			CFrameQuest = CFrame.new(- 1141.07483, 4.10001802, 3831.5498, 0.965929627, - 0, - 0.258804798, 0, 1, - 0, 0.258804798, 0, 0.965929627)
			CFrameMon = CFrame.new(- 1103.513427734375, 13.752052307128906, 3896.091064453125)
		elseif MyLevel == 40 or MyLevel <= 59 then
			Mon, NameMon, NameQuest, LevelQuest = "Brute", "Brute", "BuggyQuest1", 2;
			CFrameQuest = CFrame.new(- 1141.07483, 4.10001802, 3831.5498, 0.965929627, - 0, - 0.258804798, 0, 1, - 0, 0.258804798, 0, 0.965929627)
			CFrameMon = CFrame.new(- 1140.083740234375, 14.809885025024414, 4322.92138671875)
		elseif MyLevel == 60 or MyLevel <= 74 then
			Mon, NameMon, NameQuest, LevelQuest = "Desert Bandit", "Desert Bandit", "DesertQuest", 1;
			CFrameQuest = CFrame.new(894.488647, 5.14000702, 4392.43359, 0.819155693, - 0, - 0.573571265, 0, 1, - 0, 0.573571265, 0, 0.819155693)
			CFrameMon = CFrame.new(924.7998046875, 6.44867467880249, 4481.5859375)
		elseif MyLevel == 75 or MyLevel <= 89 then
			NameMon, NameQuest, LevelQuest = "Desert Officer", "DesertQuest", 2;
			CFrameQuest = CFrame.new(894.488647, 5.14000702, 4392.43359, 0.819155693, - 0, - 0.573571265, 0, 1, - 0, 0.573571265, 0, 0.819155693)
			CFrameMon = CFrame.new(1608.2822265625, 8.614224433898926, 4371.00732421875)
		elseif MyLevel == 90 or MyLevel <= 99 then
			NameMon, NameQuest, LevelQuest = "Snow Bandit", "SnowQuest", 1;
			CFrameQuest = CFrame.new(1389.74451, 88.1519318, - 1298.90796, - 0.342042685, 0, 0.939684391, 0, 1, 0, - 0.939684391, 0, - 0.342042685)
			CFrameMon = CFrame.new(1354.347900390625, 87.27277374267578, - 1393.946533203125)
		elseif MyLevel == 100 or MyLevel <= 119 then
			NameMon, NameQuest, LevelQuest = "Snowman", "SnowQuest", 2;
			CFrameQuest = CFrame.new(1389.74451, 88.1519318, - 1298.90796, - 0.342042685, 0, 0.939684391, 0, 1, 0, - 0.939684391, 0, - 0.342042685)
			CFrameMon = CFrame.new(1201.6412353515625, 144.57958984375, - 1550.0670166015625)
		elseif MyLevel == 120 or MyLevel <= 149 then
			NameMon, NameQuest, LevelQuest = "Chief Petty Officer", "MarineQuest2", 1;
			CFrameQuest = CFrame.new(- 5039.58643, 27.3500385, 4324.68018, 0, 0, - 1, 0, 1, 0, 1, 0, 0)
			CFrameMon = CFrame.new(- 4881.23095703125, 22.65204429626465, 4273.75244140625)
		elseif MyLevel == 150 or MyLevel <= 174 then
			NameMon, NameQuest, LevelQuest = "Sky Bandit", "SkyQuest", 1;
			CFrameQuest = CFrame.new(- 4839.53027, 716.368591, - 2619.44165, 0.866007268, 0, 0.500031412, 0, 1, 0, - 0.500031412, 0, 0.866007268)
			CFrameMon = CFrame.new(- 4953.20703125, 295.74420166015625, - 2899.22900390625)
		elseif MyLevel == 175 or MyLevel <= 189 then
			NameMon, NameQuest, LevelQuest = "Dark Master", "SkyQuest", 2;
			CFrameQuest = CFrame.new(- 4839.53027, 716.368591, - 2619.44165, 0.866007268, 0, 0.500031412, 0, 1, 0, - 0.500031412, 0, 0.866007268)
			CFrameMon = CFrame.new(- 5259.8447265625, 391.3976745605469, - 2229.035400390625)
		elseif MyLevel == 190 or MyLevel <= 209 then
			NameMon, NameQuest, LevelQuest = "Prisoner", "PrisonerQuest", 1;
			CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, - 0.0894274712, - 5.00292918e-09, - 0.995993316, 1.60817859e-09, 1, - 5.16744869e-09, 0.995993316, - 2.06384709e-09, - 0.0894274712)
			CFrameMon = CFrame.new(5098.9736328125, - 0.3204058110713959, 474.2373352050781)
		elseif MyLevel == 210 or MyLevel <= 249 then
			NameMon, NameQuest, LevelQuest = "Dangerous Prisoner", "PrisonerQuest", 2;
			CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, - 0.0894274712, - 5.00292918e-09, - 0.995993316, 1.60817859e-09, 1, - 5.16744869e-09, 0.995993316, - 2.06384709e-09, - 0.0894274712)
			CFrameMon = CFrame.new(5654.5634765625, 15.633401870727539, 866.2991943359375)
		elseif MyLevel == 250 or MyLevel <= 274 then
			NameMon, NameQuest, LevelQuest = "Toga Warrior", "ColosseumQuest", 1;
			CFrameQuest = CFrame.new(- 1580.04663, 6.35000277, - 2986.47534, - 0.515037298, 0, - 0.857167721, 0, 1, 0, 0.857167721, 0, - 0.515037298)
			CFrameMon = CFrame.new(- 1820.21484375, 51.68385696411133, - 2740.6650390625)
		elseif MyLevel == 275 or MyLevel <= 299 then
			NameMon, NameQuest, LevelQuest = "Gladiator", "ColosseumQuest", 2;
			CFrameQuest = CFrame.new(- 1580.04663, 6.35000277, - 2986.47534, - 0.515037298, 0, - 0.857167721, 0, 1, 0, 0.857167721, 0, - 0.515037298)
			CFrameMon = CFrame.new(- 1292.838134765625, 56.380882263183594, - 3339.031494140625)
		elseif MyLevel == 300 or MyLevel <= 324 then
			NameMon, NameQuest, LevelQuest = "Military Soldier", "MagmaQuest", 1;
			CFrameQuest = CFrame.new(- 5313.37012, 10.9500084, 8515.29395, - 0.499959469, 0, 0.866048813, 0, 1, 0, - 0.866048813, 0, - 0.499959469)
			CFrameMon = CFrame.new(- 5411.16455078125, 11.081554412841797, 8454.29296875)
		elseif MyLevel == 325 or MyLevel <= 374 then
			NameMon, NameQuest, LevelQuest = "Military Spy", "MagmaQuest", 2;
			CFrameQuest = CFrame.new(- 5313.37012, 10.9500084, 8515.29395, - 0.499959469, 0, 0.866048813, 0, 1, 0, - 0.866048813, 0, - 0.499959469)
			CFrameMon = CFrame.new(- 5802.8681640625, 86.26241302490234, 8828.859375)
		elseif MyLevel == 375 or MyLevel <= 399 then
			NameMon, NameQuest, LevelQuest = "Fishman Warrior", "FishmanQuest", 1;
			CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
			CFrameMon = CFrame.new(60878.30078125, 18.482830047607422, 1543.7574462890625)
			if _25msShared.AutoFarmLevel and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
				game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('requestEntrance', Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
			end
		elseif MyLevel == 400 or MyLevel <= 449 then
			NameMon, NameQuest, LevelQuest = "Fishman Commando", "FishmanQuest", 2;
			CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
			CFrameMon = CFrame.new(61922.6328125, 18.482830047607422, 1493.934326171875)
			if _25msShared.AutoFarmLevel and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
				game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('requestEntrance', Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
			end
		elseif MyLevel == 450 or MyLevel <= 474 then
			NameMon, NameQuest, LevelQuest = "God's Guard", "SkyExp1Quest", 1;
			CFrameQuest = CFrame.new(- 4721.88867, 843.874695, - 1949.96643, 0.996191859, - 0, - 0.0871884301, 0, 1, - 0, 0.0871884301, 0, 0.996191859)
			CFrameMon = CFrame.new(- 4710.04296875, 845.2769775390625, - 1927.3079833984375)
			if _25msShared.AutoFarmLevel and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
				game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('requestEntrance', Vector3.new(- 4607.82275, 872.54248, - 1667.55688))
			end
		elseif MyLevel == 475 or MyLevel <= 524 then
			NameMon, NameQuest, LevelQuest = "Shanda", "SkyExp1Quest", 2;
			CFrameQuest = CFrame.new(- 7859.09814, 5544.19043, - 381.476196, - 0.422592998, 0, 0.906319618, 0, 1, 0, - 0.906319618, 0, - 0.422592998)
			CFrameMon = CFrame.new(- 7678.48974609375, 5566.40380859375, - 497.2156066894531)
			if _25msShared.AutoFarmLevel and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
				game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('requestEntrance', Vector3.new(- 7894.6176757813, 5547.1416015625, - 380.29119873047))
			end
		elseif MyLevel == 525 or MyLevel <= 549 then
			NameMon, NameQuest, LevelQuest = "Royal Squad", "SkyExp2Quest", 1;
			CFrameQuest = CFrame.new(- 7906.81592, 5634.6626, - 1411.99194, 0, 0, - 1, 0, 1, 0, 1, 0, 0)
			CFrameMon = CFrame.new(- 7624.25244140625, 5658.13330078125, - 1467.354248046875)
		elseif MyLevel == 550 or MyLevel <= 624 then
			NameMon, NameQuest, LevelQuest = "Royal Soldier", "SkyExp2Quest", 2;
			CFrameQuest = CFrame.new(- 7906.81592, 5634.6626, - 1411.99194, 0, 0, - 1, 0, 1, 0, 1, 0, 0)
			CFrameMon = CFrame.new(- 7836.75341796875, 5645.6640625, - 1790.6236572265625)
		elseif MyLevel == 625 or MyLevel <= 649 then
			NameMon, NameQuest, LevelQuest = "Galley Pirate", "FountainQuest", 1;
			CFrameQuest = CFrame.new(5259.81982, 37.3500175, 4050.0293, 0.087131381, 0, 0.996196866, 0, 1, 0, - 0.996196866, 0, 0.087131381)
			CFrameMon = CFrame.new(5551.02197265625, 78.90135192871094, 3930.412841796875)
		elseif MyLevel >= 650 then
			NameMon, NameQuest, LevelQuest = "Galley Captain", "FountainQuest", 2;
			CFrameQuest = CFrame.new(5259.81982, 37.3500175, 4050.0293, 0.087131381, 0, 0.996196866, 0, 1, 0, - 0.996196866, 0, 0.087131381)
			CFrameMon = CFrame.new(5441.95166015625, 42.50205993652344, 4950.09375)
		end
	elseif L_24_ then
		if MyLevel == 700 or MyLevel <= 724 then
			NameMon, NameQuest, LevelQuest = "Raider", "Area1Quest", 1;
			CFrameQuest = CFrame.new(- 429.543518, 71.7699966, 1836.18188, - 0.22495985, 0, - 0.974368095, 0, 1, 0, 0.974368095, 0, - 0.22495985)
			CFrameMon = CFrame.new(- 728.3267211914062, 52.779319763183594, 2345.7705078125)
		elseif MyLevel == 725 or MyLevel <= 774 then
			NameMon, NameQuest, LevelQuest = "Mercenary", "Area1Quest", 2;
			CFrameQuest = CFrame.new(- 429.543518, 71.7699966, 1836.18188, - 0.22495985, 0, - 0.974368095, 0, 1, 0, 0.974368095, 0, - 0.22495985)
			CFrameMon = CFrame.new(- 1004.3244018554688, 80.15886688232422, 1424.619384765625)
		elseif MyLevel == 775 or MyLevel <= 799 then
			NameMon, NameQuest, LevelQuest = "Swan Pirate", "Area2Quest", 1;
			CFrameQuest = CFrame.new(638.43811, 71.769989, 918.282898, 0.139203906, 0, 0.99026376, 0, 1, 0, - 0.99026376, 0, 0.139203906)
			CFrameMon = CFrame.new(1068.664306640625, 137.61428833007812, 1322.1060791015625)
		elseif MyLevel == 800 or MyLevel <= 874 then
			NameMon, NameQuest, LevelQuest = "Factory Staff", "Area2Quest", 2;
			CFrameQuest = CFrame.new(632.698608, 73.1055908, 918.666321, - 0.0319722369, 8.96074881e-10, - 0.999488771, 1.36326533e-10, 1, 8.92172336e-10, 0.999488771, - 1.07732087e-10, - 0.0319722369)
			CFrameMon = CFrame.new(73.07867431640625, 81.86344146728516, - 27.470672607421875)
		elseif MyLevel == 875 or MyLevel <= 899 then
			NameMon, NameQuest, LevelQuest = "Marine Lieutenant", "MarineQuest3", 1;
			CFrameQuest = CFrame.new(- 2440.79639, 71.7140732, - 3216.06812, 0.866007268, 0, 0.500031412, 0, 1, 0, - 0.500031412, 0, 0.866007268)
			CFrameMon = CFrame.new(- 2821.372314453125, 75.89727783203125, - 3070.089111328125)
		elseif MyLevel == 900 or MyLevel <= 949 then
			NameMon, NameQuest, LevelQuest = "Marine Captain", "MarineQuest3", 2;
			CFrameQuest = CFrame.new(- 2440.79639, 71.7140732, - 3216.06812, 0.866007268, 0, 0.500031412, 0, 1, 0, - 0.500031412, 0, 0.866007268)
			CFrameMon = CFrame.new(- 1861.2310791015625, 80.17658233642578, - 3254.697509765625)
		elseif MyLevel == 950 or MyLevel <= 974 then
			NameMon, NameQuest, LevelQuest = "Zombie", "ZombieQuest", 1;
			CFrameQuest = CFrame.new(- 5497.06152, 47.5923004, - 795.237061, - 0.29242146, 0, - 0.95628953, 0, 1, 0, 0.95628953, 0, - 0.29242146)
			CFrameMon = CFrame.new(- 5657.77685546875, 78.96973419189453, - 928.68701171875)
		elseif MyLevel == 975 or MyLevel <= 999 then
			NameMon, NameQuest, LevelQuest = "Vampire", "ZombieQuest", 2;
			CFrameQuest = CFrame.new(- 5497.06152, 47.5923004, - 795.237061, - 0.29242146, 0, - 0.95628953, 0, 1, 0, 0.95628953, 0, - 0.29242146)
			CFrameMon = CFrame.new(- 6037.66796875, 32.18463897705078, - 1340.6597900390625)
		elseif MyLevel == 1000 or MyLevel <= 1049 then
			NameMon, NameQuest, LevelQuest = "Snow Trooper", "SnowMountainQuest", 1;
			CFrameQuest = CFrame.new(609.858826, 400.119904, - 5372.25928, - 0.374604106, 0, 0.92718488, 0, 1, 0, - 0.92718488, 0, - 0.374604106)
			CFrameMon = CFrame.new(549.1473388671875, 427.3870544433594, - 5563.69873046875)
		elseif MyLevel == 1050 or MyLevel <= 1099 then
			NameMon, NameQuest, LevelQuest = "Winter Warrior", "SnowMountainQuest", 2;
			CFrameQuest = CFrame.new(609.858826, 400.119904, - 5372.25928, - 0.374604106, 0, 0.92718488, 0, 1, 0, - 0.92718488, 0, - 0.374604106)
			CFrameMon = CFrame.new(1142.7451171875, 475.6398010253906, - 5199.41650390625)
		elseif MyLevel == 1100 or MyLevel <= 1124 then
			NameMon, NameQuest, LevelQuest = "Lab Subordinate", "IceSideQuest", 1;
			CFrameQuest = CFrame.new(- 6064.06885, 15.2422857, - 4902.97852, 0.453972578, - 0, - 0.891015649, 0, 1, - 0, 0.891015649, 0, 0.453972578)
			CFrameMon = CFrame.new(- 5707.4716796875, 15.951709747314453, - 4513.39208984375)
		elseif MyLevel == 1125 or MyLevel <= 1174 then
			NameMon, NameQuest, LevelQuest = "Horned Warrior", "IceSideQuest", 2;
			CFrameQuest = CFrame.new(- 6064.06885, 15.2422857, - 4902.97852, 0.453972578, - 0, - 0.891015649, 0, 1, - 0, 0.891015649, 0, 0.453972578)
			CFrameMon = CFrame.new(- 6341.36669921875, 15.951770782470703, - 5723.162109375)
		elseif MyLevel == 1175 or MyLevel <= 1199 then
			NameMon, NameQuest, LevelQuest = "Magma Ninja", "FireSideQuest", 1;
			CFrameQuest = CFrame.new(- 5428.03174, 15.0622921, - 5299.43457, - 0.882952213, 0, 0.469463557, 0, 1, 0, - 0.469463557, 0, - 0.882952213)
			CFrameMon = CFrame.new(- 5449.6728515625, 76.65874481201172, - 5808.20068359375)
		elseif MyLevel == 1200 or MyLevel <= 1249 then
			NameMon, NameQuest, LevelQuest = "Lava Pirate", "FireSideQuest", 2;
			CFrameQuest = CFrame.new(- 5428.03174, 15.0622921, - 5299.43457, - 0.882952213, 0, 0.469463557, 0, 1, 0, - 0.469463557, 0, - 0.882952213)
			CFrameMon = CFrame.new(- 5213.33154296875, 49.73788070678711, - 4701.451171875)
		elseif MyLevel == 1250 or MyLevel <= 1274 then
			NameMon, NameQuest, LevelQuest = "Ship Deckhand", "ShipQuest1", 1;
			CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016)
			CFrameMon = CFrame.new(1212.0111083984375, 150.79205322265625, 33059.24609375)
			if _25msShared.AutoFarmLevel and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
				game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('requestEntrance', Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
		elseif MyLevel == 1275 or MyLevel <= 1299 then
			NameMon, NameQuest, LevelQuest = "Ship Engineer", "ShipQuest1", 2;
			CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016)
			CFrameMon = CFrame.new(919.4786376953125, 43.54401397705078, 32779.96875)
			if _25msShared.AutoFarmLevel and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
				game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('requestEntrance', Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
		elseif MyLevel == 1300 or MyLevel <= 1324 then
			NameMon, NameQuest, LevelQuest = "Ship Steward", "ShipQuest2", 1;
			CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125)
			CFrameMon = CFrame.new(919.4385375976562, 129.55599975585938, 33436.03515625)
			if _25msShared.AutoFarmLevel and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
				game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('requestEntrance', Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
		elseif MyLevel == 1325 or MyLevel <= 1349 then
			NameMon, NameQuest, LevelQuest = "Ship Officer", "ShipQuest2", 2;
			CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125)
			CFrameMon = CFrame.new(1036.0179443359375, 181.4390411376953, 33315.7265625)
			if _25msShared.AutoFarmLevel and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
				game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('requestEntrance', Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
		elseif MyLevel == 1350 or MyLevel <= 1374 then
			NameMon, NameQuest, LevelQuest = "Arctic Warrior", "FrostQuest", 1;
			CFrameQuest = CFrame.new(5667.6582, 26.7997818, - 6486.08984, - 0.933587909, 0, - 0.358349502, 0, 1, 0, 0.358349502, 0, - 0.933587909)
			CFrameMon = CFrame.new(5966.24609375, 62.97002029418945, - 6179.3828125)
			if _25msShared.AutoFarmLevel and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
				game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('requestEntrance', Vector3.new(- 6508.5581054688, 5000.034996032715, - 132.83953857422))
			end
		elseif MyLevel == 1375 or MyLevel <= 1424 then
			NameMon, NameQuest, LevelQuest = "Snow Lurker", "FrostQuest", 2;
			CFrameQuest = CFrame.new(5667.6582, 26.7997818, - 6486.08984, - 0.933587909, 0, - 0.358349502, 0, 1, 0, 0.358349502, 0, - 0.933587909)
			CFrameMon = CFrame.new(5407.07373046875, 69.19437408447266, - 6880.88037109375)
		elseif MyLevel == 1425 or MyLevel <= 1449 then
			NameMon, NameQuest, LevelQuest = "Sea Soldier", "ForgottenQuest", 1;
			CFrameQuest = CFrame.new(- 3054.44458, 235.544281, - 10142.8193, 0.990270376, - 0, - 0.13915664, 0, 1, - 0, 0.13915664, 0, 0.990270376)
			CFrameMon = CFrame.new(- 3028.2236328125, 64.67451477050781, - 9775.4267578125)
		elseif MyLevel >= 1450 then
			NameMon, NameQuest, LevelQuest = "Water Fighter", "ForgottenQuest", 2;
			CFrameQuest = CFrame.new(- 3054.44458, 235.544281, - 10142.8193, 0.990270376, - 0, - 0.13915664, 0, 1, - 0, 0.13915664, 0, 0.990270376)
			CFrameMon = CFrame.new(- 3352.9013671875, 285.01556396484375, - 10534.841796875)
		end
	elseif L_25_ then
		if MyLevel == 1500 or MyLevel <= 1524 then
			NameMon, NameQuest, LevelQuest = "Pistol Millionaire", "PiratePortQuest", 1;
			CFrameQuest = CFrame.new(- 290.074677, 42.9034653, 5581.58984, 0.965929627, - 0, - 0.258804798, 0, 1, - 0, 0.258804798, 0, 0.965929627)
			CFrameMon = CFrame.new(- 245.9963836669922, 47.30615234375, 5584.1005859375)
		elseif MyLevel == 1525 or MyLevel <= 1574 then
			NameMon, NameQuest, LevelQuest = "Pistol Billionaire", "PiratePortQuest", 2;
			CFrameQuest = CFrame.new(- 290.074677, 42.9034653, 5581.58984, 0.965929627, - 0, - 0.258804798, 0, 1, - 0, 0.258804798, 0, 0.965929627)
			CFrameMon = CFrame.new(- 187.3301544189453, 86.23987579345703, 6013.513671875)
		elseif MyLevel == 1575 or MyLevel <= 1599 then
			NameMon, NameQuest, LevelQuest = "Dragon Crew Warrior", "AmazonQuest", 1;
			CFrameQuest = CFrame.new(6736.32958984375, 127.4482192993164, - 712.3320922851562)
			CFrameMon = CFrame.new(7014.84765625, 196.3662567138672, - 1024.2913818359375)
		elseif MyLevel == 1600 or MyLevel <= 1624 then
			NameMon, NameQuest, LevelQuest = "Dragon Crew Archer", "AmazonQuest", 2;
			CFrameQuest = CFrame.new(6736.32958984375, 127.4482192993164, - 712.3320922851562)
			CFrameMon = CFrame.new(6792.60302734375, 535.4273681640625, 454.4717102050781)
		elseif MyLevel == 1625 or MyLevel <= 1649 then
			NameMon, NameQuest, LevelQuest = "Hydra Enforcer", "AmazonQuest2", 1;
			CFrameQuest = CFrame.new(5210.87353515625, 1004.1356811523438, 755.8411254882812)
			CFrameMon = CFrame.new(4704.02099609375, 1043.867431640625, 679.615966796875)
		elseif MyLevel == 1650 or MyLevel <= 1699 then
			NameMon, NameQuest, LevelQuest = "Venomous Assailant", "AmazonQuest2", 2;
			CFrameQuest = CFrame.new(5210.87353515625, 1004.1356811523438, 755.8411254882812)
			CFrameMon = CFrame.new(4731.27197265625, 1090.177978515625, 1078.1712646484375)
		elseif MyLevel == 1700 or MyLevel <= 1724 then
			NameMon, NameQuest, LevelQuest = "Marine Commodore", "MarineTreeIsland", 1;
			CFrameQuest = CFrame.new(2180.54126, 27.8156815, - 6741.5498, - 0.965929747, 0, 0.258804798, 0, 1, 0, - 0.258804798, 0, - 0.965929747)
			CFrameMon = CFrame.new(2286.0078125, 73.13391876220703, - 7159.80908203125)
		elseif MyLevel == 1725 or MyLevel <= 1774 then
			NameMon, NameQuest, LevelQuest = "Marine Rear Admiral", "MarineTreeIsland", 2;
			CFrameQuest = CFrame.new(2179.98828125, 28.731239318848, - 6740.0551757813)
			CFrameMon = CFrame.new(3656.773681640625, 160.52406311035156, - 7001.5986328125)
		elseif MyLevel == 1775 or MyLevel <= 1799 then
			NameMon, NameQuest, LevelQuest = "Fishman Raider", "DeepForestIsland3", 1;
			CFrameQuest = CFrame.new(- 10581.6563, 330.872955, - 8761.18652, - 0.882952213, 0, 0.469463557, 0, 1, 0, - 0.469463557, 0, - 0.882952213)
			CFrameMon = CFrame.new(- 10407.5263671875, 331.76263427734375, - 8368.5166015625)
		elseif MyLevel == 1800 or MyLevel <= 1824 then
			NameMon, NameQuest, LevelQuest = "Fishman Captain", "DeepForestIsland3", 2;
			CFrameQuest = CFrame.new(- 10581.6563, 330.872955, - 8761.18652, - 0.882952213, 0, 0.469463557, 0, 1, 0, - 0.469463557, 0, - 0.882952213)
			CFrameMon = CFrame.new(- 10994.701171875, 352.38140869140625, - 9002.1103515625)
		elseif MyLevel == 1825 or MyLevel <= 1849 then
			NameMon, NameQuest, LevelQuest = "Forest Pirate", "DeepForestIsland", 1;
			CFrameQuest = CFrame.new(- 13234.04, 331.488495, - 7625.40137, 0.707134247, - 0, - 0.707079291, 0, 1, - 0, 0.707079291, 0, 0.707134247)
			CFrameMon = CFrame.new(- 13274.478515625, 332.3781433105469, - 7769.58056640625)
		elseif MyLevel == 1850 or MyLevel <= 1899 then
			NameMon, NameQuest, LevelQuest = "Mythological Pirate", "DeepForestIsland", 2;
			CFrameQuest = CFrame.new(- 13234.04, 331.488495, - 7625.40137, 0.707134247, - 0, - 0.707079291, 0, 1, - 0, 0.707079291, 0, 0.707134247)
			CFrameMon = CFrame.new(- 13680.607421875, 501.08154296875, - 6991.189453125)
		elseif MyLevel == 1900 or MyLevel <= 1924 then
			NameMon, NameQuest, LevelQuest = "Jungle Pirate", "DeepForestIsland2", 1;
			CFrameQuest = CFrame.new(- 12680.3818, 389.971039, - 9902.01953, - 0.0871315002, 0, 0.996196866, 0, 1, 0, - 0.996196866, 0, - 0.0871315002)
			CFrameMon = CFrame.new(- 12256.16015625, 331.73828125, - 10485.8369140625)
		elseif MyLevel == 1925 or MyLevel <= 1974 then
			NameMon, NameQuest, LevelQuest = "Musketeer Pirate", "DeepForestIsland2", 2;
			CFrameQuest = CFrame.new(- 12680.3818, 389.971039, - 9902.01953, - 0.0871315002, 0, 0.996196866, 0, 1, 0, - 0.996196866, 0, - 0.0871315002)
			CFrameMon = CFrame.new(- 13457.904296875, 391.545654296875, - 9859.177734375)
		elseif MyLevel == 1975 or MyLevel <= 1999 then
			NameMon, NameQuest, LevelQuest = "Reborn Skeleton", "HauntedQuest1", 1;
			CFrameQuest = CFrame.new(- 9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, - 0, - 1, 0, 0)
			CFrameMon = CFrame.new(- 8763.7236328125, 165.72299194335938, 6159.86181640625)
		elseif MyLevel == 2000 or MyLevel <= 2024 then
			NameMon, NameQuest, LevelQuest = "Living Zombie", "HauntedQuest1", 2;
			CFrameQuest = CFrame.new(- 9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, - 0, - 1, 0, 0)
			CFrameMon = CFrame.new(- 10144.1318359375, 138.62667846679688, 5838.0888671875)
		elseif MyLevel == 2025 or MyLevel <= 2049 then
			NameMon, NameQuest, LevelQuest = "Demonic Soul", "HauntedQuest2", 1;
			CFrameQuest = CFrame.new(- 9516.99316, 172.017181, 6078.46533, 0, 0, - 1, 0, 1, 0, 1, 0, 0)
			CFrameMon = CFrame.new(- 9505.8720703125, 172.10482788085938, 6158.9931640625)
		elseif MyLevel == 2050 or MyLevel <= 2074 then
			NameMon, NameQuest, LevelQuest = "Posessed Mummy", "HauntedQuest2", 2;
			CFrameQuest = CFrame.new(- 9516.99316, 172.017181, 6078.46533, 0, 0, - 1, 0, 1, 0, 1, 0, 0)
			CFrameMon = CFrame.new(- 9582.0224609375, 6.251527309417725, 6205.478515625)
		elseif MyLevel == 2075 or MyLevel <= 2099 then
			NameMon, NameQuest, LevelQuest = "Peanut Scout", "NutsIslandQuest", 1;
			CFrameQuest = CFrame.new(- 2104.3908691406, 38.104167938232, - 10194.21875, 0, 0, - 1, 0, 1, 0, 1, 0, 0)
			CFrameMon = CFrame.new(- 2143.241943359375, 47.72198486328125, - 10029.9951171875)
		elseif MyLevel == 2100 or MyLevel <= 2124 then
			NameMon, NameQuest, LevelQuest = "Peanut President", "NutsIslandQuest", 2;
			CFrameQuest = CFrame.new(- 2104.3908691406, 38.104167938232, - 10194.21875, 0, 0, - 1, 0, 1, 0, 1, 0, 0)
			CFrameMon = CFrame.new(- 1859.35400390625, 38.10316848754883, - 10422.4296875)
		elseif MyLevel == 2125 or MyLevel <= 2149 then
			NameMon, NameQuest, LevelQuest = "Ice Cream Chef", "IceCreamIslandQuest", 1;
			CFrameQuest = CFrame.new(- 820.64825439453, 65.819526672363, - 10965.795898438, 0, 0, - 1, 0, 1, 0, 1, 0, 0)
			CFrameMon = CFrame.new(- 872.24658203125, 65.81957244873047, - 10919.95703125)
		elseif MyLevel == 2150 or MyLevel <= 2199 then
			NameMon, NameQuest, LevelQuest = "Ice Cream Commander", "IceCreamIslandQuest", 2;
			CFrameQuest = CFrame.new(- 820.64825439453, 65.819526672363, - 10965.795898438, 0, 0, - 1, 0, 1, 0, 1, 0, 0)
			CFrameMon = CFrame.new(- 558.06103515625, 112.04895782470703, - 11290.7744140625)
		elseif MyLevel == 2200 or MyLevel <= 2224 then
			NameMon, NameQuest, LevelQuest = "Cookie Crafter", "CakeQuest1", 1;
			CFrameQuest = CFrame.new(- 2021.32007, 37.7982254, - 12028.7295, 0.957576931, - 8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, - 0.288177818, - 5.2032135e-08, 0.957576931)
			CFrameMon = CFrame.new(- 2374.13671875, 37.79826354980469, - 12125.30859375)
		elseif MyLevel == 2225 or MyLevel <= 2249 then
			NameMon, NameQuest, LevelQuest = "Cake Guard", "CakeQuest1", 2;
			CFrameQuest = CFrame.new(- 2021.32007, 37.7982254, - 12028.7295, 0.957576931, - 8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, - 0.288177818, - 5.2032135e-08, 0.957576931)
			CFrameMon = CFrame.new(- 1598.3070068359375, 43.773197174072266, - 12244.5810546875)
		elseif MyLevel == 2250 or MyLevel <= 2274 then
			NameMon, NameQuest, LevelQuest = "Baking Staff", "CakeQuest2", 1;
			CFrameQuest = CFrame.new(- 1927.91602, 37.7981339, - 12842.5391, - 0.96804446, 4.22142143e-08, 0.250778586, 4.74911062e-08, 1, 1.49904711e-08, - 0.250778586, 2.64211941e-08, - 0.96804446)
			CFrameMon = CFrame.new(- 1887.8099365234375, 77.6185073852539, - 12998.3505859375)
		elseif MyLevel == 2275 or MyLevel <= 2299 then
			NameMon, NameQuest, LevelQuest = "Head Baker", "CakeQuest2", 2;
			CFrameQuest = CFrame.new(- 1927.91602, 37.7981339, - 12842.5391, - 0.96804446, 4.22142143e-08, 0.250778586, 4.74911062e-08, 1, 1.49904711e-08, - 0.250778586, 2.64211941e-08, - 0.96804446)
			CFrameMon = CFrame.new(- 2216.188232421875, 82.884521484375, - 12869.2939453125)
		elseif MyLevel == 2300 or MyLevel <= 2324 then
			NameMon, NameQuest, LevelQuest = "Cocoa Warrior", "ChocQuest1", 1;
			CFrameQuest = CFrame.new(233.22836303710938, 29.876001358032227, - 12201.2333984375)
			CFrameMon = CFrame.new(- 21.55328369140625, 80.57499694824219, - 12352.3876953125)
		elseif MyLevel == 2325 or MyLevel <= 2349 then
			NameMon, NameQuest, LevelQuest = "Chocolate Bar Battler", "ChocQuest1", 2;
			CFrameQuest = CFrame.new(233.22836303710938, 29.876001358032227, - 12201.2333984375)
			CFrameMon = CFrame.new(582.590576171875, 77.18809509277344, - 12463.162109375)
		elseif MyLevel == 2350 or MyLevel <= 2374 then
			NameMon, NameQuest, LevelQuest = "Sweet Thief", "ChocQuest2", 1;
			CFrameQuest = CFrame.new(150.5066375732422, 30.693693161010742, - 12774.5029296875)
			CFrameMon = CFrame.new(165.1884765625, 76.05885314941406, - 12600.8369140625)
		elseif MyLevel == 2375 or MyLevel <= 2399 then
			NameMon, NameQuest, LevelQuest = "Candy Rebel", "ChocQuest2", 2;
			CFrameQuest = CFrame.new(150.5066375732422, 30.693693161010742, - 12774.5029296875)
			CFrameMon = CFrame.new(134.86563110351562, 77.2476806640625, - 12876.5478515625)
		elseif MyLevel == 2400 or MyLevel <= 2449 then
			NameMon, NameQuest, LevelQuest = "Candy Pirate", "CandyQuest1", 1;
			CFrameQuest = CFrame.new(- 1150.0400390625, 20.378934860229492, - 14446.3349609375)
			CFrameMon = CFrame.new(- 1310.5003662109375, 26.016523361206055, - 14562.404296875)
		elseif MyLevel == 2425 or MyLevel <= 2450 then
			NameMon, NameQuest, LevelQuest = "Snow Demon", "CandyQuest1", 2;
			CFrameQuest = CFrame.new(- 1150.0400390625, 20.378934860229492, - 14446.3349609375)
			CFrameMon = CFrame.new(- 750.1473388671875, 15.250883102416992, - 14343.2578125)
		elseif MyLevel == 2450 or MyLevel <= 2475 then
			NameMon, NameQuest, LevelQuest = "Isle Outlaw", "TikiQuest1", 1;
			CFrameQuest = CFrame.new(- 16547.45703125, 56.00029754638672, - 174.1670684814453)
			CFrameMon = CFrame.new(- 16303.1435546875, 188.16168212890625, - 268.9233703613281)
		elseif MyLevel == 2475 or MyLevel <= 2525 then
			NameMon, NameQuest, LevelQuest = "Island Boy", "TikiQuest1", 2;
			CFrameQuest = CFrame.new(- 16547.45703125, 56.00029754638672, - 174.1670684814453)
			CFrameMon = CFrame.new(- 16303.1435546875, 188.16168212890625, - 268.9233703613281)
		elseif MyLevel == 2525 or MyLevel <= 2550 then
			NameMon, NameQuest, LevelQuest = "Isle Champion", "TikiQuest2", 2;
			CFrameQuest = CFrame.new(- 16523.0996, 55.9234467, 1049.65784, - 0.418787986, - 0.0126074236, 0.907996595, - 0.0160101596, 0.99985069, 0.00649857335, - 0.907942891, - 0.0118156485, - 0.418927342)
			CFrameMon = CFrame.new(- 16748.4609375, 94.38502502441406, 1129.7178955078125)
		elseif MyLevel >= 2550 or MyLevel <= 2600 then
			NameMon, NameQuest, LevelQuest = "Serpent Hunter", "TikiQuest3", 1;
			CFrameQuest = CFrame.new(- 16665.462890625, 105.3105697631836, 1577.8289794921875)
			CFrameMon = CFrame.new(- 16959.2734375, 110.61740112304688, 1669.6007080078125)
		end
	end
end;
function CheckBossQuest()
	if _25msShared.SelectBoss == "Saber Expert" then
		MsBoss = "Saber Expert"
		NameBoss = "Saber Expert"
		CFrameBoss = CFrame.new(- 1458.89502, 29.8870335, - 50.633564, 0.858821094, 1.13848939e-08, 0.512275636, - 4.85649254e-09, 1, - 1.40823326e-08, - 0.512275636, 9.6063415e-09, 0.858821094)
	elseif _25msShared.SelectBoss == "The Saw" then
		MsBoss = "The Saw"
		NameBoss = "The Saw"
		CFrameBoss = CFrame.new(- 683.519897, 13.8534927, 1610.87854, - 0.290192783, 6.88365773e-08, 0.956968188, 6.98413629e-08, 1, - 5.07531119e-08, - 0.956968188, 5.21077759e-08, - 0.290192783)
	elseif _25msShared.SelectBoss == "Greybeard" then
		MsBoss = "Greybeard"
		NameBoss = "Greybeard"
		CFrameBoss = CFrame.new(- 4955.72949, 80.8163834, 4305.82666, - 0.433646321, - 1.03394289e-08, 0.901083171, - 3.0443168e-08, 1, - 3.17633075e-09, - 0.901083171, - 2.88092288e-08, - 0.433646321)
	elseif _25msShared.SelectBoss == "The Gorilla King" then
		MsBoss = "The Gorilla King"
		NameBoss = "The Gorilla King"
		NameQuestBoss = "JungleQuest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 1604.12012, 36.8521118, 154.23732, 0.0648873374, - 4.70858913e-06, - 0.997892559, 1.41431883e-07, 1, - 4.70933674e-06, 0.997892559, 1.64442184e-07, 0.0648873374)
		CFrameBoss = CFrame.new(- 1223.52808, 6.27936459, - 502.292664, 0.310949147, - 5.66602516e-08, 0.950426519, - 3.37275488e-08, 1, 7.06501808e-08, - 0.950426519, - 5.40241736e-08, 0.310949147)
	elseif _25msShared.SelectBoss == "Bobby" then
		MsBoss = "Bobby"
		NameBoss = "Bobby"
		NameQuestBoss = "BuggyQuest1"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 1139.59717, 4.75205183, 3825.16211, - 0.959730506, - 7.5857054e-09, 0.280922383, - 4.06310328e-08, 1, - 1.11807175e-07, - 0.280922383, - 1.18718916e-07, - 0.959730506)
		CFrameBoss = CFrame.new(- 1147.65173, 32.5966301, 4156.02588, 0.956680477, - 1.77109952e-10, - 0.29113996, 5.16530874e-10, 1, 1.08897802e-09, 0.29113996, - 1.19218679e-09, 0.956680477)
	elseif _25msShared.SelectBoss == "Yeti" then
		MsBoss = "Yeti"
		NameBoss = "Yeti"
		NameQuestBoss = "SnowQuest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(1384.90247, 87.3078308, - 1296.6825, 0.280209213, 2.72035177e-08, - 0.959938943, - 6.75690828e-08, 1, 8.6151708e-09, 0.959938943, 6.24481444e-08, 0.280209213)
		CFrameBoss = CFrame.new(1221.7356, 138.046906, - 1488.84082, 0.349343032, - 9.49245944e-08, 0.936994851, 6.29478194e-08, 1, 7.7838429e-08, - 0.936994851, 3.17894653e-08, 0.349343032)
	elseif _25msShared.SelectBoss == "Mob Leader" then
		MsBoss = "Mob Leader"
		NameBoss = "Mob Leader"
		CFrameBoss = CFrame.new(- 2848.59399, 7.4272871, 5342.44043, - 0.928248107, - 8.7248246e-08, 0.371961564, - 7.61816636e-08, 1, 4.44474857e-08, - 0.371961564, 1.29216433e-08, - 0.92824)
	elseif _25msShared.SelectBoss == "Vice Admiral" then
		MsBoss = "Vice Admiral"
		NameBoss = "Vice Admiral"
		NameQuestBoss = "MarineQuest2"
		LevelQuestBoss = 2;
		CFrameQuestBoss = CFrame.new(- 5035.42285, 28.6520386, 4324.50293, - 0.0611100644, - 8.08395768e-08, 0.998130739, - 1.57416586e-08, 1, 8.00271849e-08, - 0.998130739, - 1.08217701e-08, - 0.0611100644)
		CFrameBoss = CFrame.new(- 5078.45898, 99.6520691, 4402.1665, - 0.555574954, - 9.88630566e-11, 0.831466436, - 6.35508286e-08, 1, - 4.23449258e-08, - 0.831466436, - 7.63661632e-08, - 0.555574954)
	elseif _25msShared.SelectBoss == "Warden" then
		MsBoss = "Warden"
		NameBoss = "Warden"
		NameQuestBoss = "ImpelQuest"
		LevelQuestBoss = 1;
		CFrameQuestBoss = CFrame.new(4851.35059, 5.68744135, 743.251282, - 0.538484037, - 6.68303741e-08, - 0.842635691, 1.38001752e-08, 1, - 8.81300792e-08, 0.842635691, - 5.90851599e-08, - 0.538484037)
		CFrameBoss = CFrame.new(5232.5625, 5.26856995, 747.506897, 0.943829298, - 4.5439414e-08, 0.330433697, 3.47818627e-08, 1, 3.81658154e-08, - 0.330433697, - 2.45289105e-08, 0.943829298)
	elseif _25msShared.SelectBoss == "Chief Warden" then
		MsBoss = "Chief Warden"
		NameBoss = "Chief Warden"
		NameQuestBoss = "ImpelQuest"
		LevelQuestBoss = 2;
		CFrameQuestBoss = CFrame.new(4851.35059, 5.68744135, 743.251282, - 0.538484037, - 6.68303741e-08, - 0.842635691, 1.38001752e-08, 1, - 8.81300792e-08, 0.842635691, - 5.90851599e-08, - 0.538484037)
		CFrameBoss = CFrame.new(5232.5625, 5.26856995, 747.506897, 0.943829298, - 4.5439414e-08, 0.330433697, 3.47818627e-08, 1, 3.81658154e-08, - 0.330433697, - 2.45289105e-08, 0.943829298)
	elseif _25msShared.SelectBoss == "Swan" then
		MsBoss = "Swan"
		NameBoss = "Swan"
		NameQuestBoss = "ImpelQuest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(4851.35059, 5.68744135, 743.251282, - 0.538484037, - 6.68303741e-08, - 0.842635691, 1.38001752e-08, 1, - 8.81300792e-08, 0.842635691, - 5.90851599e-08, - 0.538484037)
		CFrameBoss = CFrame.new(5232.5625, 5.26856995, 747.506897, 0.943829298, - 4.5439414e-08, 0.330433697, 3.47818627e-08, 1, 3.81658154e-08, - 0.330433697, - 2.45289105e-08, 0.943829298)
	elseif _25msShared.SelectBoss == "Magma Admiral" then
		MsBoss = "Magma Admiral"
		NameBoss = "Magma Admiral"
		NameQuestBoss = "MagmaQuest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 5317.07666, 12.2721891, 8517.41699, 0.51175487, - 2.65508806e-08, - 0.859131515, - 3.91131572e-08, 1, - 5.42026761e-08, 0.859131515, 6.13418294e-08, 0.51175487)
		CFrameBoss = CFrame.new(- 5530.12646, 22.8769703, 8859.91309, 0.857838571, 2.23414389e-08, 0.513919294, 1.53689133e-08, 1, - 6.91265853e-08, - 0.513919294, 6.71978384e-08, 0.857838571)
	elseif _25msShared.SelectBoss == "Fishman Lord" then
		MsBoss = "Fishman Lord"
		NameBoss = "Fishman Lord"
		NameQuestBoss = "FishmanQuest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(61123.0859, 18.5066795, 1570.18018, 0.927145958, 1.0624845e-07, 0.374700129, - 6.98219367e-08, 1, - 1.10790765e-07, - 0.374700129, 7.65569368e-08, 0.927145958)
		CFrameBoss = CFrame.new(61351.7773, 31.0306778, 1113.31409, 0.999974668, 0, - 0.00714713801, 0, 1.00000012, 0, 0.00714714266, 0, 0.999974549)
	elseif _25msShared.SelectBoss == "Wysper" then
		MsBoss = "Wysper"
		NameBoss = "Wysper"
		NameQuestBoss = "SkyExp1Quest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 7862.94629, 5545.52832, - 379.833954, 0.462944925, 1.45838088e-08, - 0.886386991, 1.0534996e-08, 1, 2.19553424e-08, 0.886386991, - 1.95022007e-08, 0.462944925)
		CFrameBoss = CFrame.new(- 7925.48389, 5550.76074, - 636.178345, 0.716468513, - 1.22915289e-09, 0.697619379, 3.37381434e-09, 1, - 1.70304748e-09, - 0.697619379, 3.57381835e-09, 0.716468513)
	elseif _25msShared.SelectBoss == "Thunder God" then
		MsBoss = "Thunder God"
		NameBoss = "Thunder God"
		NameQuestBoss = "SkyExp2Quest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 7902.78613, 5635.99902, - 1411.98706, - 0.0361216255, - 1.16895912e-07, 0.999347389, 1.44533963e-09, 1, 1.17024491e-07, - 0.999347389, 5.6715117e-09, - 0.0361216255)
		CFrameBoss = CFrame.new(- 7917.53613, 5616.61377, - 2277.78564, 0.965189934, 4.80563429e-08, - 0.261550069, - 6.73089886e-08, 1, - 6.46515304e-08, 0.261550069, 8.00056768e-08, 0.965189934)
	elseif _25msShared.SelectBoss == "Cyborg" then
		MsBoss = "Cyborg"
		NameBoss = "Cyborg"
		NameQuestBoss = "FountainQuest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(5253.54834, 38.5361786, 4050.45166, - 0.0112687312, - 9.93677887e-08, - 0.999936521, 2.55291371e-10, 1, - 9.93769547e-08, 0.999936521, - 1.37512213e-09, - 0.0112687312)
		CFrameBoss = CFrame.new(6041.82813, 52.7112198, 3907.45142, - 0.563162148, 1.73805248e-09, - 0.826346457, - 5.94632716e-08, 1, 4.26280238e-08, 0.826346457, 7.31437524e-08, - 0.563162148)
	elseif _25msShared.SelectBoss == "Diamond" then
		MsBoss = "Diamond"
		NameBoss = "Diamond"
		NameQuestBoss = "Area1Quest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 424.080078, 73.0055847, 1836.91589, 0.253544956, - 1.42165932e-08, 0.967323601, - 6.00147771e-08, 1, 3.04272909e-08, - 0.967323601, - 6.5768397e-08, 0.253544956)
		CFrameBoss = CFrame.new(- 1736.26587, 198.627731, - 236.412857, - 0.997808516, 0, - 0.0661673471, 0, 1, 0, 0.0661673471, 0, - 0.997808516)
	elseif _25msShared.SelectBoss == "Jeremy" then
		MsBoss = "Jeremy"
		NameBoss = "Jeremy"
		NameQuestBoss = "Area2Quest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(632.698608, 73.1055908, 918.666321, - 0.0319722369, 8.96074881e-10, - 0.999488771, 1.36326533e-10, 1, 8.92172336e-10, 0.999488771, - 1.07732087e-10, - 0.0319722369)
		CFrameBoss = CFrame.new(2203.76953, 448.966034, 752.731079, - 0.0217453763, 0, - 0.999763548, 0, 1, 0, 0.999763548, 0, - 0.0217453763)
	elseif _25msShared.SelectBoss == "Fajita" then
		MsBoss = "Fajita"
		NameBoss = "Fajita"
		NameQuestBoss = "MarineQuest3"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 2442.65015, 73.0511475, - 3219.11523, - 0.873540044, 4.2329841e-08, - 0.486752301, 5.64383384e-08, 1, - 1.43220786e-08, 0.486752301, - 3.99823996e-08, - 0.873540044)
		CFrameBoss = CFrame.new(- 2297.40332, 115.449463, - 3946.53833, 0.961227536, - 1.46645796e-09, - 0.275756449, - 2.3212845e-09, 1, - 1.34094433e-08, 0.275756449, 1.35296352e-08, 0.961227536)
	elseif _25msShared.SelectBoss == "Don Swan" then
		MsBoss = "Don Swan"
		NameBoss = "Don Swan"
		CFrameBoss = CFrame.new(2288.802, 15.1870775, 863.034607, 0.99974072, - 8.41247214e-08, - 0.0227668174, 8.4774733e-08, 1, 2.75850098e-08, 0.0227668174, - 2.95079072e-08, 0.99974072)
	elseif _25msShared.SelectBoss == "Smoke Admiral" then
		MsBoss = "Smoke Admiral"
		NameBoss = "Smoke Admiral"
		NameQuestBoss = "IceSideQuest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 6059.96191, 15.9868021, - 4904.7373, - 0.444992423, - 3.0874483e-09, 0.895534337, - 3.64098796e-08, 1, - 1.4644522e-08, - 0.895534337, - 3.91229982e-08, - 0.444992423)
		CFrameBoss = CFrame.new(- 5115.72754, 23.7664986, - 5338.2207, 0.251453817, 1.48345061e-08, - 0.967869282, 4.02796978e-08, 1, 2.57916977e-08, 0.967869282, - 4.54708946e-08, 0.251453817)
	elseif _25msShared.SelectBoss == "Cursed Captain" then
		MsBoss = "Cursed Captain"
		NameBoss = "Cursed Captain"
		CFrameBoss = CFrame.new(916.928589, 181.092773, 33422, - 0.999505103, 9.26310495e-09, 0.0314563364, 8.42916226e-09, 1, - 2.6643713e-08, - 0.0314563364, - 2.63653774e-08, - 0.999505103)
	elseif _25msShared.SelectBoss == "Darkbeard" then
		MsBoss = "Darkbeard"
		NameBoss = "Darkbeard"
		CFrameBoss = CFrame.new(3876.00366, 24.6882591, - 3820.21777, - 0.976951957, 4.97356325e-08, 0.213458836, 4.57335361e-08, 1, - 2.36868622e-08, - 0.213458836, - 1.33787044e-08, - 0.976951957)
	elseif _25msShared.SelectBoss == "Order" then
		MsBoss = "Order"
		NameBoss = "Order"
		CFrameBoss = CFrame.new(- 6221.15039, 16.2351036, - 5045.23584, - 0.380726993, 7.41463495e-08, 0.924687505, 5.85604774e-08, 1, - 5.60738549e-08, - 0.924687505, 3.28013137e-08, - 0.380726993)
	elseif _25msShared.SelectBoss == "Awakened Ice Admiral" then
		MsBoss = "Awakened Ice Admiral"
		NameBoss = "Awakened Ice Admiral"
		NameQuestBoss = "FrostQuest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(5669.33203, 28.2118053, - 6481.55908, 0.921275556, - 1.25320829e-08, 0.388910472, 4.72230788e-08, 1, - 7.96414241e-08, - 0.388910472, 9.17372489e-08, 0.921275556)
		CFrameBoss = CFrame.new(6407.33936, 340.223785, - 6892.521, 0.49051559, - 5.25310213e-08, - 0.871432424, - 2.76146022e-08, 1, - 7.58250565e-08, 0.871432424, 6.12576301e-08, 0.49051559)
	elseif _25msShared.SelectBoss == "Tide Keeper" then
		MsBoss = "Tide Keeper"
		NameBoss = "Tide Keeper"
		NameQuestBoss = "ForgottenQuest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 3053.89648, 236.881363, - 10148.2324, - 0.985987961, - 3.58504737e-09, 0.16681771, - 3.07832915e-09, 1, 3.29612559e-09, - 0.16681771, 2.73641976e-09, - 0.985987961)
		CFrameBoss = CFrame.new(- 3570.18652, 123.328949, - 11555.9072, 0.465199202, - 1.3857326e-08, 0.885206044, 4.0332897e-09, 1, 1.35347511e-08, - 0.885206044, - 2.72606271e-09, 0.465199202)
	elseif _25msShared.SelectBoss == "Stone" then
		MsBoss = "Stone"
		NameBoss = "Stone"
		NameQuestBoss = "PiratePortQuest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 290, 44, 5577)
		CFrameBoss = CFrame.new(- 1085, 40, 6779)
	elseif _25msShared.SelectBoss == "Hydra Leader" then
		MsBoss = "Hydra Leader"
		NameBoss = "Hydra Leader"
		NameQuestBoss = "AmazonQuest2"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(5210.87353515625, 1004.1356811523438, 755.8411254882812)
		CFrameBoss = CFrame.new(5942.8154296875, 1019.0787353515625, - 116.86933135986328)
	elseif _25msShared.SelectBoss == "Kilo Admiral" then
		MsBoss = "Kilo Admiral"
		NameBoss = "Kilo Admiral"
		NameQuestBoss = "MarineTreeIsland"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(2178, 29, - 6737)
		CFrameBoss = CFrame.new(2846, 433, - 7100)
	elseif _25msShared.SelectBoss == "Captain Elephant" then
		MsBoss = "Captain Elephant"
		NameBoss = "Captain Elephant"
		NameQuestBoss = "DeepForestIsland"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 13232, 333, - 7631)
		CFrameBoss = CFrame.new(- 13221, 325, - 8405)
	elseif _25msShared.SelectBoss == "Beautiful Pirate" then
		MsBoss = "Beautiful Pirate"
		NameBoss = "Beautiful Pirate"
		NameQuestBoss = "DeepForestIsland2"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 12686, 391, - 9902)
		CFrameBoss = CFrame.new(5182, 23, - 20)
	elseif _25msShared.SelectBoss == "Cake Queen" then
		MsBoss = "Cake Queen"
		NameBoss = "Cake Queen"
		NameQuestBoss = "IceCreamIslandQuest"
		LevelQuestBoss = 3;
		CFrameQuestBoss = CFrame.new(- 716, 382, - 11010)
		CFrameBoss = CFrame.new(- 821, 66, - 10965)
	elseif _25msShared.SelectBoss == "rip_indra True Form" then
		MsBoss = "rip_indra True Form"
		NameBoss = "rip_indra True Form"
		CFrameBoss = CFrame.new(- 5359, 424, - 2735)
	elseif _25msShared.SelectBoss == "Longma" then
		MsBoss = "Longma"
		NameBoss = "Longma"
		CFrameBoss = CFrame.new(- 10248.3936, 353.79129, - 9306.34473)
	elseif _25msShared.SelectBoss == "Soul Reaper" then
		MsBoss = "Soul Reaper"
		NameBoss = "Soul Reaper"
		CFrameBoss = CFrame.new(- 9515.62109, 315.925537, 6691.12012)
	end
end;
local function L_27_func()
	if _25msShared.SelectMaterial == "Radioactive Material" then
		MMon = "Factory Staff"
		MPos = CFrame.new(- 507.7895202636719, 72.99479675292969, - 126.45632934570312)
	elseif _25msShared.SelectMaterial == "Mystic Droplet" then
		MMon = "Water Fighter"
		MPos = CFrame.new(- 3214.218017578125, 298.69952392578125, - 10543.685546875)
	elseif _25msShared.SelectMaterial == "Magma Ore" then
		if game.PlaceId == 2753915549 then
			MMon = "Military Spy"
			MPos = CFrame.new(- 5850.2802734375, 77.28675079345703, 8848.6748046875)
		elseif game.PlaceId == 4442272183 then
			MMon = "Lava Pirate"
			MPos = CFrame.new(- 5234.60595703125, 51.953372955322266, - 4732.27880859375)
		end
	elseif _25msShared.SelectMaterial == "Angel Wings" then
		MMon = "Royal Soldier"
		MPos = CFrame.new(- 7827.15625, 5606.912109375, - 1705.5833740234375)
	elseif _25msShared.SelectMaterial == "Leather" then
		if game.PlaceId == 2753915549 then
			MMon = "Pirate"
			MPos = CFrame.new(- 1211.8792724609375, 4.787090301513672, 3916.83056640625)
		elseif game.PlaceId == 4442272183 then
			MMon = "Marine Captain"
			MPos = CFrame.new(- 2010.5059814453125, 73.00115966796875, - 3326.620849609375)
		elseif game.PlaceId == 7449423635 then
			MMon = "Jungle Pirate"
			MPos = CFrame.new(- 11975.78515625, 331.7734069824219, - 10620.0302734375)
		end
	elseif _25msShared.SelectMaterial == "Scrap Metal" then
		if game.PlaceId == 2753915549 then
			MMon = "Brute"
			MPos = CFrame.new(- 1132.4202880859375, 14.844913482666016, 4293.30517578125)
		elseif game.PlaceId == 4442272183 then
			MMon = "Mercenary"
			MPos = CFrame.new(- 972.307373046875, 73.04473876953125, 1419.2901611328125)
		elseif game.PlaceId == 7449423635 then
			MMon = "Pirate Millionaire"
			MPos = CFrame.new(- 289.6311950683594, 43.8282470703125, 5583.66357421875)
		end
	elseif _25msShared.SelectMaterial == "Demonic Wisp" then
		MMon = "Demonic Soul"
		MPos = CFrame.new(- 9503.388671875, 172.139892578125, 6143.0634765625)
	elseif _25msShared.SelectMaterial == "Vampire Fang" then
		MMon = "Vampire"
		MPos = CFrame.new(- 5999.20458984375, 6.437741279602051, - 1290.059326171875)
	elseif _25msShared.SelectMaterial == "Conjured Cocoa" then
		MMon = "Chocolate Bar Battler"
		MPos = CFrame.new(747.428466796875, 237.9543914794922, - 12700.2041015625)
	elseif _25msShared.SelectMaterial == "Dragon Scale" then
		MMon = "Dragon Crew Warrior"
		MPos = CFrame.new(5824.06982421875, 51.38640213012695, - 1106.694580078125)
	elseif _25msShared.SelectMaterial == "Gunpowder" then
		MMon = "Pistol Billionaire"
		MPos = CFrame.new(- 379.6134338378906, 73.84449768066406, 5928.5263671875)
	elseif _25msShared.SelectMaterial == "Fish Tail" then
		MMon = "Fishman Captain"
		MPos = CFrame.new(- 10961.0126953125, 331.7977600097656, - 8914.29296875)
	elseif _25msShared.SelectMaterial == "Mini Tusk" then
		MMon = "Mythological Pirate"
		MPos = CFrame.new(- 13516.0458984375, 469.8182373046875, - 6899.16064453125)
	end
end;
function Hop()
	local L_61_ = game.PlaceId;
	local L_62_ = {}
	local L_63_ = ""
	local L_64_ = os.date("!*t").hour;
	local L_65_ = false;
	function TPReturner()
		local L_66_;
		if L_63_ == "" then
			L_66_ = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. L_61_ .. '/servers/Public?sortOrder=Asc&limit=100'))
		else
			L_66_ = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. L_61_ .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. L_63_))
		end;
		local L_67_ = ""
		if L_66_.nextPageCursor and L_66_.nextPageCursor ~= "null" and L_66_.nextPageCursor ~= nil then
			L_63_ = L_66_.nextPageCursor
		end;
		local L_68_ = 0;
		for L_69_forvar0, L_70_forvar1 in pairs(L_66_.data) do
			local L_71_ = true;
			L_67_ = tostring(L_70_forvar1.id)
			if tonumber(L_70_forvar1.maxPlayers) > tonumber(L_70_forvar1.playing) then
				for L_72_forvar0, L_73_forvar1 in pairs(L_62_) do
					if L_68_ ~= 0 then
						if L_67_ == tostring(L_73_forvar1) then
							L_71_ = false
						end
					else
						if tonumber(L_64_) ~= tonumber(L_73_forvar1) then
							local L_74_ = pcall(function()
								L_62_ = {}
								table.insert(L_62_, L_64_)
							end)
						end
					end;
					L_68_ = L_68_ + 1
				end;
				if L_71_ == true then
					table.insert(L_62_, L_67_)
					wait()
					pcall(function()
						wait()
						game:GetService("TeleportService"):TeleportToPlaceInstance(L_61_, L_67_, game.Players.LocalPlayer)
					end)
					wait(4)
				end
			end
		end
	end;
	function Teleport()
		while wait() do
			pcall(function()
				TPReturner()
				if L_63_ ~= "" then
					TPReturner()
				end
			end)
		end
	end;
	Teleport()
end;
function InfAb()
	if InfAbility then
		if not game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility") then
			local L_75_ = Instance.new("ParticleEmitter")
			L_75_.Acceleration = Vector3.new(0, 0, 0)
			L_75_.Archivable = true;
			L_75_.Drag = 20;
			L_75_.EmissionDirection = Enum.NormalId.Top;
			L_75_.Enabled = true;
			L_75_.Lifetime = NumberRange.new(0.2, 0.2)
			L_75_.LightInfluence = 0;
			L_75_.LockedToPart = true;
			L_75_.Name = "Agility"
			L_75_.Rate = 500;
			local L_76_ = {
				NumberSequenceKeypoint.new(0, 0),
				NumberSequenceKeypoint.new(1, 4)
			}
			L_75_.Size = NumberSequence.new(L_76_)
			L_75_.RotSpeed = NumberRange.new(999, 9999)
			L_75_.Rotation = NumberRange.new(0, 0)
			L_75_.Speed = NumberRange.new(30, 30)
			L_75_.SpreadAngle = Vector2.new(360, 360)
			L_75_.Texture = ""
			L_75_.VelocityInheritance = 0;
			L_75_.ZOffset = 2;
			L_75_.Transparency = NumberSequence.new(0)
			L_75_.Color = ColorSequence.new(Color3.fromRGB(80, 245, 245), Color3.fromRGB(80, 245, 245))
			L_75_.Parent = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart
		end
	else
		if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility") then
			game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility"):Destroy()
		end
	end
end;
local L_28_ = game:GetService("Players").LocalPlayer;
local L_29_ = L_28_.Character.Energy.Value;
function infinitestam()
	L_28_.Character.Energy.Changed:connect(function()
		if InfiniteEnergy then
			L_28_.Character.Energy.Value = L_29_
		end
	end)
end;
spawn(function()
	pcall(function()
		while wait() do
			if InfiniteEnergy then
				wait(0.3)
				L_29_ = L_28_.Character.Energy.Value;
				infinitestam()
			end
		end
	end)
end)
function NoDodgeCool()
	if nododgecool then
		for L_77_forvar0, L_78_forvar1 in next, getgc() do
			if game:GetService("Players").LocalPlayer.Character.Dodge then
				if typeof(L_78_forvar1) == "function" and getfenv(L_78_forvar1).script == game:GetService("Players").LocalPlayer.Character.Dodge then
					for L_79_forvar0, L_80_forvar1 in next, getupvalues(L_78_forvar1) do
						if tostring(L_80_forvar1) == "0.4" then
							repeat
								wait(.1)
								setupvalue(L_78_forvar1, L_79_forvar0, 0)
							until not nododgecool
						end
					end
				end
			end
		end
	end
end;
function NameMelee()
	for L_81_forvar0, L_82_forvar1 in next, game:GetService("Players").LocalPlayer.Backpack:GetChildren() do
		if L_82_forvar1:IsA("Tool") and L_82_forvar1.ToolTip == "Melee" then
			return L_82_forvar1.Name
		end
	end;
	for L_83_forvar0, L_84_forvar1 in next, game:GetService("Players").LocalPlayer.Character:GetChildren() do
		if L_84_forvar1:IsA("Tool") and L_84_forvar1.ToolTip == "Melee" then
			return L_84_forvar1.Name
		end
	end
end;
function NameSword()
	for L_85_forvar0, L_86_forvar1 in next, game:GetService("Players").LocalPlayer.Backpack:GetChildren() do
		if L_86_forvar1:IsA("Tool") and L_86_forvar1.ToolTip == "Sword" then
			return L_86_forvar1.Name
		end
	end;
	for L_87_forvar0, L_88_forvar1 in next, game:GetService("Players").LocalPlayer.Character:GetChildren() do
		if L_88_forvar1:IsA("Tool") and L_88_forvar1.ToolTip == "Sword" then
			return L_88_forvar1.Name
		end
	end
end;
function checkskillMelee()
	if not game:GetService("Players").LocalPlayer.PlayerGui.Main.Skills:FindFirstChild(NameMelee()) then
		EquipWeapon(NameMelee())
		return false
	end;
	for L_89_forvar0, L_90_forvar1 in next, game:GetService("Players").LocalPlayer.PlayerGui.Main.Skills[NameMelee()]:GetChildren() do
		if L_90_forvar1:IsA("Frame") then
			if L_90_forvar1.Name ~= 'Template' and L_90_forvar1.Title.TextColor3 == Color3.new(1, 1, 1) and L_90_forvar1.Cooldown.Size == UDim2.new(0, 0, 1, - 1) or L_90_forvar1.Cooldown.Size == UDim2.new(1, 0, 1, - 1) then
				return L_90_forvar1.Name
			end
		end
	end
end;
function checkskillDF()
	if not game:GetService("Players").LocalPlayer.PlayerGui.Main.Skills:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
		EquipWeapon(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value)
		return false
	end;
	for L_91_forvar0, L_92_forvar1 in next, game:GetService("Players").LocalPlayer.PlayerGui.Main.Skills[game:GetService("Players").LocalPlayer.Data.DevilFruit.Value]:GetChildren() do
		if L_92_forvar1:IsA("Frame") then
			if L_92_forvar1.Name ~= 'Template' and L_92_forvar1.Title.TextColor3 == Color3.new(1, 1, 1) and L_92_forvar1.Cooldown.Size == UDim2.new(0, 0, 1, - 1) or L_92_forvar1.Cooldown.Size == UDim2.new(1, 0, 1, - 1) then
				return L_92_forvar1.Name
			end
		end
	end
end;
function checkskillSword()
	if not NameSword() then
		return
	end;
	if not game:GetService("Players").LocalPlayer.PlayerGui.Main.Skills:FindFirstChild(NameSword()) then
		EquipWeapon(NameSword())
		return false
	end;
	for L_93_forvar0, L_94_forvar1 in next, game:GetService("Players").LocalPlayer.PlayerGui.Main.Skills[NameSword()]:GetChildren() do
		if L_94_forvar1:IsA("Frame") then
			if L_94_forvar1.Name ~= 'Template' and L_94_forvar1.Title.TextColor3 == Color3.new(1, 1, 1) and L_94_forvar1.Cooldown.Size == UDim2.new(0, 0, 1, - 1) or L_94_forvar1.Cooldown.Size == UDim2.new(1, 0, 1, - 1) then
				return L_94_forvar1.Name
			end
		end
	end
end;
function checkskillGun()
	if not SelectToolWeaponGun then
		return
	end;
	if not game:GetService("Players").LocalPlayer.PlayerGui.Main.Skills:FindFirstChild(SelectToolWeaponGun) then
		EquipWeapon(SelectToolWeaponGun)
		return false
	end;
	for L_95_forvar0, L_96_forvar1 in next, game:GetService("Players").LocalPlayer.PlayerGui.Main.Skills[SelectToolWeaponGun]:GetChildren() do
		if L_96_forvar1:IsA("Frame") then
			if L_96_forvar1.Name ~= 'Template' and L_96_forvar1.Title.TextColor3 == Color3.new(1, 1, 1) and L_96_forvar1.Cooldown.Size == UDim2.new(0, 0, 1, - 1) or L_96_forvar1.Cooldown.Size == UDim2.new(1, 0, 1, - 1) then
				return L_96_forvar1.Name
			end
		end
	end
end;
function SendKey(L_97_arg0, L_98_arg1)
	if L_97_arg0 then
		if not L_98_arg1 then
			game:service("VirtualInputManager"):SendKeyEvent(true, L_97_arg0, false, game)
			task.wait()
			game:service("VirtualInputManager"):SendKeyEvent(false, L_97_arg0, false, game)
		elseif L_98_arg1 then
			game:service("VirtualInputManager"):SendKeyEvent(true, L_97_arg0, false, game)
			task.wait(L_98_arg1)
			game:service("VirtualInputManager"):SendKeyEvent(false, L_97_arg0, false, game)
		end
	end
end;
function autoskill()
	sword = checkskillSword()
	melee = checkskillMelee()
	df = checkskillDF()
	gun = checkskillGun()
	if df and _25msShared.SpamDF and df ~= 'V' and not string.find(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value, "Buddha") then
		EquipWeapon(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value)
		if df then
			SendKey(df)
		end
	elseif checkskillMelee() and _25msShared.SpamMelee then
		EquipWeapon(NameMelee())
		if melee then
			SendKey(melee)
		end
	elseif checkskillSword() and _25msShared.SpamSword then
		EquipWeapon(NameSword())
		if sword then
			SendKey(sword)
		end
	elseif checkskillGun() and _25msShared.SpamGun then
		EquipWeapon(SelectToolWeaponGun)
		if gun then
			SendKey(gun)
		end
	else
		EquipAllWeapon()
	end
end;
task.spawn(function()
	while task.wait() do
		if autospamskill then
			autoskill()
		end
	end
end)
function CheckInventory(L_99_arg0)
	for L_100_forvar0, L_101_forvar1 in pairs(game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('getInventory')) do
		if type(L_101_forvar1) == 'table' then
			if L_101_forvar1.Type == 'Material' or L_101_forvar1.Type == 'Gun' then
				if L_101_forvar1.Name == L_99_arg0 then
					return L_101_forvar1.Count
				end
			end
		end
	end;
	return 0
end;
local function Notify(L_102_arg0, L_103_arg1)
	local L_104_ = require(game.ReplicatedStorage.Notification)
	local L_105_ = L_104_.new(L_102_arg0)
	L_105_.Duration = L_103_arg1;
	L_105_:Display()
end;
function TeleportSeabeast(L_106_arg0)
	local L_107_ = Vector3.new(0, L_106_arg0:FindFirstChild('HumanoidRootPart').Position.Y, 0)
	local L_108_ = Vector3.new(0, game:GetService('Workspace').Map['WaterBase-Plane'].Position.Y, 0)
	if (L_107_ - L_108_).Magnitude <= 175 then
		TP(L_106_arg0.HumanoidRootPart.CFrame * CFrame.new(0, 450, 50))
	else
		TP(CFrame.new(L_106_arg0.HumanoidRootPart.Position.X, game:GetService('Workspace').Map['WaterBase-Plane'].Position.Y + 150, L_106_arg0.HumanoidRootPart.Position.Z))
	end
end;
function Click()
	local L_109_ = game:GetService('VirtualUser')
	ViTabs.RaceV4:Button1Down(Vector2.new(1280, 672))
end;
function IsWpSKillLoaded(L_110_arg0)
	if game:GetService('Players')['LocalPlayer'].PlayerGui.Main.Skills:FindFirstChild(L_110_arg0) then
		return true
	end
end;
function GetWeapon(L_111_arg0)
	s = ''
	for L_112_forvar0, L_113_forvar1 in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
		if L_113_forvar1:IsA('Tool') and L_113_forvar1.ToolTip == L_111_arg0 then
			s = L_113_forvar1.Name
		end
	end;
	for L_114_forvar0, L_115_forvar1 in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
		if L_115_forvar1:IsA('Tool') and L_115_forvar1.ToolTip == L_111_arg0 then
			s = L_115_forvar1.Name
		end
	end;
	return s
end;
function EquipAllWeapon()
	u3 = {
		'Melee',
		'Blox Fruit',
		'Sword',
		'Gun'
	}
	u3_2 = {}
	for L_116_forvar0, L_117_forvar1 in pairs(u3) do
		u3_3 = GetWeapon(L_117_forvar1)
		table.insert(u3_2, u3_3)
	end;
	for L_118_forvar0, L_119_forvar1 in pairs(u3_2) do
		if not IsWpSKillLoaded(L_119_forvar1) then
			EquipWeapon(L_119_forvar1)
		end
	end
end;
function UnEquipWeapon(L_120_arg0)
	if game.Players.LocalPlayer.Character:FindFirstChild(L_120_arg0) then
		_25msShared.NotAutoEquip = true;
		wait(.5)
		game.Players.LocalPlayer.Character:FindFirstChild(L_120_arg0).Parent = game.Players.LocalPlayer.Backpack;
		wait(.1)
		_25msShared.NotAutoEquip = false
	end
end;
function EquipWeapon(L_121_arg0)
	if not _25msShared.NotAutoEquip then
		if game.Players.LocalPlayer.Backpack:FindFirstChild(L_121_arg0) then
			Tool = game.Players.LocalPlayer.Backpack:FindFirstChild(L_121_arg0)
			wait(.1)
			game.Players.LocalPlayer.Character.Humanoid:EquipTool(Tool)
		end
	end
end;
function TP(L_122_arg0)
	local L_123_ = (L_122_arg0.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude;
	if L_123_ <= _25msShared.SkipDistance then
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = L_122_arg0
	end;
	local L_124_ = TweenInfo.new(L_123_ / 300, Enum.EasingStyle.Linear)
	local L_125_ = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart, L_124_, {
		CFrame = L_122_arg0
	})
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.X, L_122_arg0.Y, game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Z)
	if _25msShared.BypassTP and L_123_ >= 3000 then
		L_28_.Character.Humanoid:ChangeState(15)
		L_28_.Character.HumanoidRootPart.CFrame = L_122_arg0;
		task.wait()
		L_28_.Character.HumanoidRootPart.CFrame = L_122_arg0;
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
	end;
	L_125_:Play()
end;
function StopTween(L_126_arg0)
	if not L_126_arg0 then
		wait()
		TP(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame)
		wait(.4)
		TP(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame)
		wait()
		if game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
			game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
		end
	end
end;
spawn(function()
	pcall(function()
		while task.wait() do
			if _25msShared.AutoWhiteBelt or _25msShared.AutoYellowBelt or _25msShared.MirageIsland or _25msShared.AutoFinishRaceTrial or _25msShared.TweenToFruit or _25msShared.ChristmasIsland or _25msShared.GrabChest or _25msShared.AutoNextIsland or _25msShared.Boat20 or _25msShared.FrozenDimension or _25msShared.KitsuneIsland or _25msShared.AutoKillLeviathan or _25msShared.AutoTerrorShark or _25msShared.AutoShark or _25msShared.AutoPiranha or _25msShared.AutoKillGhostShip or _25msShared.AutoKillSeaBeast or _25msShared.Auto_Open_Dough_Dungeon or _25msShared.PirateRaid or _25msShared.AutoCDK or _25msShared.NeareastFarm or _25msShared.AutoFarmMaterial or _25msShared.AutoSoulGuitar or _25msShared.AutoDoughBoss or _25msShared.AutoTushita or _25msShared.AutoFarmBossHallow or _25msShared.AutoSwan or _25msShared.AutoLongSword or _25msShared.AutoPole or _25msShared.BlackBeard or _25msShared.BlackBeardHop or _25msShared.AutoElectricClaw or _25msShared.AutoHolyTorch or _25msShared.AutoLawRaid or _25msShared.AutoFarmBoss or _25msShared.AutoTwinHooks or _25msShared.AutoSaber or _25msShared.NOCLIP or _25msShared.AutoFarmFruitMastery or _25msShared.AutoFarmGunMastery or _25msShared.TeleportIsland or _25msShared.Auto_EvoRace or _25msShared.AutoObservationHakiV2 or _25msShared.AutoMusketeerHat or _25msShared.AutoEctoplasm or _25msShared.AutoRengoku or _25msShared.Auto_Rainbow_Haki or _25msShared.AutoObservation or _25msShared.AutoDarkDagger or _25msShared.Safe_Mode or _25msShared.MasteryFruit or _25msShared.AutoBudySword or _25msShared.AutoBounty or _25msShared.AutoAllBoss or _25msShared.Auto_Bounty or _25msShared.AutoSharkman or _25msShared.Auto_Dungeon or _25msShared.Auto_Pole or _25msShared.Auto_Factory or _25msShared.AutoSecondSea or _25msShared.AutoBartilo or _25msShared.Auto_DarkBoss or _25msShared.AutoKillPlayerInTrial or _25msShared.AutoTrainV4 or _25msShared.Holy_Torch or _25msShared.AutoSeaEvent or _25msShared.SummonMirage or _25msShared.AutoFarmLevel or _25msShared.CLIP or _25msShared.AutoElitehunter or _25msShared.AutoThirdSea or _25msShared.AutoFarmBone == true then
				_25msShared.AutoBuso = true;
				if not game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
					local L_127_ = Instance.new("BodyVelocity")
					L_127_.Name = "BodyClip"
					L_127_.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart;
					L_127_.MaxForce = Vector3.new(10000, 10000, 10000)
					L_127_.Velocity = Vector3.new(0, 0, 0)
				end;
				for L_128_forvar0, L_129_forvar1 in pairs(game:GetService("Players").LocalPlayer.Character:GetDescendants()) do
					if L_129_forvar1:IsA("BasePart") then
						L_129_forvar1.CanCollide = false
					end
				end
			else
				_25msShared.AutoBuso = false
			end
		end
	end)
end)
function CheckPirateBoat()
	local L_130_ = {
		'FishBoat',
		'PirateBasic',
		'PirateBrigade',
		'PirateGrandBrigade'
	}
	for L_131_forvar0, L_132_forvar1 in next, game:GetService('Workspace').Enemies:GetChildren() do
		if table.find(L_130_, L_132_forvar1.Name) and L_132_forvar1:FindFirstChild('Health') and L_132_forvar1.Health.Value > 0 and (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - L_132_forvar1:FindFirstChild('Engine').Position).Magnitude <= 2500 then
			return L_132_forvar1
		end
	end
end;
function CheckSwanBoat()
	for L_133_forvar0, L_134_forvar1 in next, game:GetService('Workspace').Boats:GetChildren() do
		if L_134_forvar1:IsA('Model') then
			if L_134_forvar1:FindFirstChild('Owner') and tostring(L_134_forvar1.Owner.Value) == game:GetService('Players').LocalPlayer.Name and L_134_forvar1.Humanoid.Value > 0 then
				return L_134_forvar1
			end
		end
	end;
	return false
end;
function CheckSeaBeast()
	for L_135_forvar0, L_136_forvar1 in next, game:GetService('Workspace').SeaBeasts:GetChildren() do
		if L_136_forvar1.Name == 'SeaBeast1' then
			if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - L_136_forvar1:FindFirstChild('HumanoidRootPart').Position).Magnitude <= 2500 then
				local L_137_ = L_136_forvar1.HealthBBG.Frame.TextLabel.Text;
				local L_138_ = L_137_:gsub('/%d+,%d+', '')
				local L_139_ = L_136_forvar1.HealthBBG.Frame.TextLabel.Text;
				local L_140_;
				if string.find(L_138_, ',') then
					L_140_ = L_139_:gsub('%d+,%d+/', '')
				else
					L_140_ = L_139_:gsub('%d+/', '')
				end;
				local L_141_ = L_140_:gsub(',', '')
				if tonumber(L_141_) >= 34500 then
					return L_136_forvar1
				end
			end
		end
	end;
	return false
end;
function CheckLeviathanSegment()
	local L_142_ = {
		'Leviathan Segment'
	}
	for L_143_forvar0, L_144_forvar1 in next, game:GetService('Workspace').SeaBeasts:GetChildren() do
		if table.find(L_142_, L_144_forvar1.Name) then
			return L_144_forvar1
		end
	end
end;
function CheckLeviathanTail()
	local L_145_ = {
		'Leviathan Tail'
	}
	for L_146_forvar0, L_147_forvar1 in next, game:GetService('Workspace').SeaBeasts:GetChildren() do
		if table.find(L_145_, L_147_forvar1.Name) then
			return L_147_forvar1
		end
	end
end;
function CheckLeviathan()
	local L_148_ = {
		'Leviathan'
	}
	for L_149_forvar0, L_150_forvar1 in next, game:GetService('Workspace').SeaBeasts:GetChildren() do
		if table.find(L_148_, L_150_forvar1.Name) then
			return L_150_forvar1
		end
	end
end;
function TeleportLeviathan(L_151_arg0)
	local L_152_ = Vector3.new(0, L_151_arg0:FindFirstChild('HumanoidRootPart').Position.Y, 0)
	local L_153_ = Vector3.new(0, game:GetService('Workspace').Map['WaterBase-Plane'].Position.Y, 0)
	if (L_152_ - L_153_).Magnitude <= 175 then
		TP(L_151_arg0.HumanoidRootPart.CFrame * CFrame.new(0, 366, 50))
	end
end;
local L_30_ = CFrame.new(28734.3945, 14888.2324, - 109.071777, - 0.650207579, 4.1780531e-08, - 0.759756625, 1.97876595e-08, 1, 3.80575109e-08, 0.759756625, 9.71147784e-09, - 0.650207579)
function TweenTemple()
	game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('requestEntrance', Vector3.new(28282.5703125, 14896.8505859375, 105.1042709350586))
end;
local function L_31_func(...)
	require(game.ReplicatedStorage.Notification).new(...):Display()
end;
function DayNight()
	GameTime = "Error"
	local L_154_ = game.Lighting;
	local L_155_ = L_154_.ClockTime;
	if L_155_ >= 18 or L_155_ < 5 then
		GameTime = "Night"
	else
		GameTime = "Day"
	end;
	return GameTime
end;
function ClockTime()
	return math.floor(game.Lighting.ClockTime)
end;
function BuyGear()
	game.ReplicatedStorage.Remotes.CommF_:InvokeServer("UpgradeRace", "Buy")
end;
function PullLever()
	repeat
		wait()
		if (L_30_.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 2000 then
			TweenTemple()
		end
	until (L_30_.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2000;
	TP(game:GetService("Workspace").Map["Temple of Time"].Lever.Part.CFrame)
	for L_156_forvar0, L_157_forvar1 in pairs(game:GetService("Workspace").Map["Temple of Time"].Lever:GetDescendants()) do
		if L_157_forvar1.Name == "ProximityPrompt" then
			fireproximityprompt(L_157_forvar1)
		end
	end
end;
function AncientClock()
	for L_158_forvar0, L_159_forvar1 in next, workspace:GetDescendants() do
		if L_159_forvar1.Name == "Prompt" then
			game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = L_159_forvar1.CFrame
		end
	end
end;
local L_32_ = {}
for L_160_forvar0, L_161_forvar1 in pairs(game.Workspace:GetDescendants()) do
	if string.find(L_161_forvar1.Name, 'Corridor') then
		L_32_[L_161_forvar1.Name] = L_161_forvar1.Door.Door.RightDoor.Union.CFrame
	end
end;
function TweentoCurrentRaceDoor()
	a = L_32_[game.Players.LocalPlayer.Data.Race.Value .. 'Corridor']
	if (L_30_.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 2000 then
		repeat
			wait()
			if (L_30_.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 2000 then
				TweenTemple()
			end
		until (L_30_.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2000;
		TP(a)
	elseif (L_30_.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2000 then
		TP(a)
	end
end;
function GetSeaBeastTrial()
	if not game.Workspace.Map:FindFirstChild('FishmanTrial') then
		autospamskill = nil;
		return nil
	end;
	if game:GetService('Workspace')['_WorldOrigin'].Locations:FindFirstChild('Trial of Water') then
		FishmanTrial = game:GetService('Workspace')['_WorldOrigin'].Locations:FindFirstChild('Trial of Water')
	end;
	if FishmanTrial then
		for L_162_forvar0, L_163_forvar1 in next, game:GetService('Workspace').SeaBeasts:GetChildren() do
			if string.find(L_163_forvar1.Name, 'SeaBeast') and L_163_forvar1:FindFirstChild('HumanoidRootPart') and (L_163_forvar1.HumanoidRootPart.Position - FishmanTrial.Position).Magnitude <= 1500 then
				if L_163_forvar1.Health.Value > 0 then
					return L_163_forvar1
				end
			end
		end
	end
end;
function CheckBossDimension()
	for L_164_forvar0, L_165_forvar1 in pairs(game.Workspace.Enemies:GetChildren()) do
		if (L_165_forvar1.Name == "Cake Prince" or L_165_forvar1.Name == "Dough King") and L_165_forvar1.Humanoid.Health > 0 then
			return L_165_forvar1
		end
	end;
	for L_166_forvar0, L_167_forvar1 in pairs(L_5_:GetChildren()) do
		if L_167_forvar1.Name == "Cake Prince" or L_167_forvar1.Name == "Dough King" then
			return L_167_forvar1
		end
	end
end;
local L_33_ = loadstring(game:HttpGet("https://you.whimper.xyz/sources/CokkaHub/ui.lua"))()
local L_34_ = L_33_:Window("Cokka Hub 25ms was here", Enum.KeyCode.LeftControl)
print("|COKKA DEBUG| Anti AFK")
game:GetService("Players").LocalPlayer.Idled:connect(function()
	print("|COKKA DEBUG| AFK detected, prevented +1")
	L_7_:ClickButton2(Vector2.new())
	L_7_:Button2Down(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
	wait(1)
	L_7_:Button2Up(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
end)
MethodFarm = CFrame.new(0, 10, 10)
local L_35_ = {
	Main = L_34_:Tab("Main Farm"),
	Setting = L_34_:Tab("Settings"),
	Dragon = L_34_:Tab("Dragon Dojo"),
	Status = L_34_:Tab("Status"),
	SeaEvent = L_34_:Tab("Sea Events"),
	Kitsune = L_34_:Tab("Kitsune Island"),
	QuestItem = L_34_:Tab("Quest & Item"),
	PVP = L_34_:Tab("PVP Combat"),
	Teleport = L_34_:Tab("Teleport"),
	ESP = L_34_:Tab("Esp & Stats"),
	Raid = L_34_:Tab("Raid"),
	DevilFruit = L_34_:Tab("Devil Fruit"),
	Misc = L_34_:Tab("Misc"),
	Mirage = L_34_:Tab("Mirage Island"),
	RaceV4 = L_34_:Tab("Race V4"),
	Info = L_34_:Tab("Update Info")
}
L_35_.Main:Label("Select Weapon")
local L_36_ = {
	"Melee",
	"Fruit",
	"Gun",
	"Sword"
}
_25msShared.SelectWeapon = "Melee"
L_35_.Main:Dropdown('Select Weapon', L_36_, "Melee", function(L_168_arg0)
	_25msShared.SelectWeapon = L_168_arg0
end)
task.spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.SelectWeapon == "Melee" then
				for L_169_forvar0, L_170_forvar1 in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
					if L_170_forvar1.ToolTip == "Melee" then
						if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(L_170_forvar1.Name)) then
							_25msShared.SelectWeapon = L_170_forvar1.Name
						end
					end
				end
			elseif _25msShared.SelectWeapon == "Sword" then
				for L_171_forvar0, L_172_forvar1 in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
					if L_172_forvar1.ToolTip == "Sword" then
						if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(L_172_forvar1.Name)) then
							_25msShared.SelectWeapon = L_172_forvar1.Name
						end
					end
				end
			elseif _25msShared.SelectWeapon == "Gun" then
				for L_173_forvar0, L_174_forvar1 in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
					if L_174_forvar1.ToolTip == "Gun" then
						if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(L_174_forvar1.Name)) then
							_25msShared.SelectWeapon = L_174_forvar1.Name
						end
					end
				end
			elseif _25msShared.SelectWeapon == "Fruit" then
				for L_175_forvar0, L_176_forvar1 in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
					if L_176_forvar1.ToolTip == "Blox Fruit" then
						if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(L_176_forvar1.Name)) then
							_25msShared.SelectWeapon = L_176_forvar1.Name
						end
					end
				end
			end
		end)
	end
end)
L_35_.Main:Label("Auto Farm")
L_35_.Main:Toggle("Auto Farm Level", _25msShared.AutoFarmLevel, function(L_177_arg0)
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
	_25msShared.AutoFarmLevel = L_177_arg0;
	StopTween(_25msShared.AutoFarmLevel)
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.AutoFarmLevel then
				CheckQ()
				local L_178_ = L_28_.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text;
				if not string.find(L_178_, NameMon) then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
				end;
				if L_28_.PlayerGui.Main.Quest.Visible == false then
					CheckQ()
					repeat
						wait()
						TP(CFrameQuest)
					until (CFrameQuest.Position - L_28_.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _25msShared.AutoFarmLevel;
					if (CFrameQuest.Position - L_28_.Character.HumanoidRootPart.Position).Magnitude <= 5 then
						L_12_:InvokeServer("StartQuest", NameQuest, LevelQuest)
					end
				elseif L_28_.PlayerGui.Main.Quest.Visible == true then
					CheckQ()
					if game:GetService("Workspace").Enemies:FindFirstChild(NameMon) then
						for L_179_forvar0, L_180_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if L_180_forvar1:FindFirstChild("HumanoidRootPart") and L_180_forvar1:FindFirstChild("Humanoid") and L_180_forvar1.Humanoid.Health > 0 then
								if L_180_forvar1.Name == NameMon then
									if string.find(L_28_.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
										repeat
											wait()
											EquipWeapon(_25msShared.SelectWeapon)
											FarmPos = L_180_forvar1.HumanoidRootPart.CFrame;
											MonFarm = L_180_forvar1.Name;
											StartMagnet = true;
											TP(L_180_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										until not _25msShared.AutoFarmLevel or L_180_forvar1.Humanoid.Health <= 0 or not L_180_forvar1.Parent or L_28_.PlayerGui.Main.Quest.Visible == false;
										StartMagnet = false
									else
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
										StartMagnet = false
									end
								end
							end
						end
					else
						if game:GetService("ReplicatedStorage"):FindFirstChild(NameMon) then
							TP(game:GetService("ReplicatedStorage"):FindFirstChild(NameMon).HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
						else
							TP(CFrameMon)
						end
					end
				end
			end
		end)
	end
end)
L_35_.Main:Toggle("Nearest Mob", _25msShared.NeareastFarm, function(L_181_arg0)
	_25msShared.NeareastFarm = L_181_arg0;
	StopTween(_25msShared.NeareastFarm)
end)
spawn(function()
	while wait() do
		if _25msShared.NeareastFarm then
			pcall(function()
				for L_182_forvar0, L_183_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if L_183_forvar1.Name and L_183_forvar1:FindFirstChild("Humanoid") then
						if L_183_forvar1.Humanoid.Health > 0 and (L_183_forvar1.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 2500 then
							repeat
								wait()
								EquipWeapon(_25msShared.SelectWeapon)
								FarmPos = L_183_forvar1.HumanoidRootPart.CFrame;
								MonFarm = L_183_forvar1.Name;
								StartMagnet = true;
								TP(L_183_forvar1.HumanoidRootPart.CFrame * MethodFarm)
							until not _25msShared.NeareastFarm or not L_183_forvar1.Parent or L_183_forvar1.Humanoid.Health == 0 or not game.Workspace.Enemies:FindFirstChild(L_183_forvar1.Name)
							StartMagnet = false
						end
					end
				end
			end)
		end
	end
end)
L_35_.Main:Label("Katakuri & Bone")
L_35_.Main:Toggle("Auto Katakuri", _25msShared.AutoDoughBoss, function(L_184_arg0)
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
	_25msShared.AutoDoughBoss = L_184_arg0;
	StopTween(_25msShared.AutoDoughBoss)
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.AutoDoughBoss then
				local L_185_ = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest;
				MyLevel = game:GetService("Players").LocalPlayer.Data.Level.Value;
				if L_185_.Visible == false and MyLevel >= 2200 then
					CFrameQuestDough = CFrame.new(- 2021.32007, 37.7982254, - 12028.7295, 0.957576931, - 8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, - 0.288177818, - 5.2032135e-08, 0.957576931)
					if (CFrameQuestDough.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 20 then
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", "CakeQuest1", 1)
					else
						TP(CFrameQuestDough)
					end
				elseif L_185_.Visible == true or L_185_.Visible == false then
					if game:GetService("Workspace").Enemies:FindFirstChild("Cake Prince") or game:GetService("Workspace").Enemies:FindFirstChild("Dough King") then
						for L_186_forvar0, L_187_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if L_187_forvar1.Name == "Cake Prince" or "Dough King" then
								if L_187_forvar1:FindFirstChild("Humanoid") and L_187_forvar1:FindFirstChild("HumanoidRootPart") and L_187_forvar1.Humanoid.Health > 0 then
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										TP(L_187_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										L_187_forvar1.HumanoidRootPart.CanCollide = false;
										L_187_forvar1.Humanoid.WalkSpeed = 0;
										L_187_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
									until not _25msShared.AutoDoughBoss or not L_187_forvar1.Parent or L_187_forvar1.Humanoid.Health <= 0
								end
							end
						end
					else
						if game:GetService("ReplicatedStorage"):FindFirstChild("Cake Prince") then
							TP(game:GetService("ReplicatedStorage"):FindFirstChild("Cake Prince").HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
						elseif game:GetService("ReplicatedStorage"):FindFirstChild("Dough King") then
							TP(game:GetService("ReplicatedStorage"):FindFirstChild("Dough King").HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
						else
							if game:GetService("Workspace").Map.CakeLoaf.BigMirror.Other.Transparency == 1 then
								if game:GetService("Workspace").Enemies:FindFirstChild("Cookie Crafter") or game:GetService("Workspace").Enemies:FindFirstChild("Cake Guard") or game:GetService("Workspace").Enemies:FindFirstChild("Baking Staff") or game:GetService("Workspace").Enemies:FindFirstChild("Head Baker") then
									for L_188_forvar0, L_189_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
										if L_189_forvar1.Name == "Cookie Crafter" or L_189_forvar1.Name == "Cake Guard" or L_189_forvar1.Name == "Baking Staff" or L_189_forvar1.Name == "Head Baker" then
											if L_189_forvar1:FindFirstChild("Humanoid") and L_189_forvar1:FindFirstChild("HumanoidRootPart") and L_189_forvar1.Humanoid.Health > 0 then
												repeat
													wait()
													EquipWeapon(_25msShared.SelectWeapon)
													TP(L_189_forvar1.HumanoidRootPart.CFrame * MethodFarm)
													FarmPos = L_189_forvar1.HumanoidRootPart.CFrame;
													MonFarm = L_189_forvar1.Name;
													StartMagnet = true
												until not _25msShared.AutoDoughBoss or not L_189_forvar1.Parent or L_189_forvar1.Humanoid.Health <= 0 or game:GetService("Workspace").Map.CakeLoaf.BigMirror.Other.Transparency == 0 or game:GetService("ReplicatedStorage"):FindFirstChild("Cake Prince") or game:GetService("Workspace").Enemies:FindFirstChild("Cake Prince") or KillMob == 0;
												StartMagnet = false
											end
										end
									end
								else
									StartMagnet = false;
									TP(CFrame.new(- 2041.91162109375, 251.54185485839844, - 12345.380859375))
								end
							else
								StartMagnet = false;
								if game:GetService("Workspace").Enemies:FindFirstChild("Cake Prince") then
									TP(game:GetService("Workspace").Enemies:FindFirstChild("Cake Prince").HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
								else
									if game:GetService("ReplicatedStorage"):FindFirstChild("Dough King") then
										TP(game:GetService("ReplicatedStorage"):FindFirstChild("Dough King").HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
									end
								end
							end
						end
					end
				end
			end
		end)
	end
end)
L_35_.Main:Toggle("Auto Farm Bone", _25msShared.AutoFarmBone, function(L_190_arg0)
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
	_25msShared.AutoFarmBone = L_190_arg0;
	StopTween(_25msShared.AutoFarmBone)
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.AutoFarmBone then
				local L_191_ = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest;
				MyLevel = game:GetService('Players').LocalPlayer.Data.Level.Value;
				if L_191_.Visible == false and MyLevel >= 2000 then
					CFrameQuestBone = CFrame.new(- 9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, - 0, - 1, 0, 0)
					if (CFrameQuestBone.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 20 then
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", "HauntedQuest1", 2)
					else
						TP(CFrameQuestBone)
					end
				elseif L_191_.Visible == true or L_191_.Visible == false then
					if game:GetService("Workspace").Enemies:FindFirstChild("Reborn Skeleton" or "Living Zombie" or "Demonic Soul" or "Posessed Mummy") then
						for L_192_forvar0, L_193_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if L_193_forvar1.Name == "Reborn Skeleton" or L_193_forvar1.Name == "Living Zombie" or L_193_forvar1.Name == "Demonic Soul" or L_193_forvar1.Name == "Posessed Mummy" then
								if L_193_forvar1:FindFirstChild("Humanoid") and L_193_forvar1:FindFirstChild("HumanoidRootPart") and L_193_forvar1.Humanoid.Health > 0 then
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										FarmPos = L_193_forvar1.PrimaryPart.CFrame;
										MonFarm = L_193_forvar1.Name;
										StartMagnet = true;
										TP(L_193_forvar1.HumanoidRootPart.CFrame * MethodFarm)
									until not _25msShared.AutoFarmBone or not L_193_forvar1.Parent or L_193_forvar1.Humanoid.Health <= 0;
									StartMagnet = false
								end
							end
						end
					else
						StartMagnet = false;
						TP(CFrame.new(- 9482.654296875, 142.13986206054688, 5495.40576171875))
					end
				end
			end
		end)
	end
end)
L_35_.Main:Toggle("Trade Bone", _25msShared.RandomBone, function(L_194_arg0)
	_25msShared.RandomBone = L_194_arg0
end)
spawn(function()
	pcall(function()
		while wait() do
			if _25msShared.RandomBone then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Bones", "Buy", 1, 1)
			end
		end
	end)
end)
L_35_.Main:Label("Mastery")
_25msShared.Kill_At = 33;
_25msShared.MasteryType = "Quest"
L_35_.Main:Slider("Kill %", 1, 100, 33, function(L_195_arg0)
	_25msShared.Kill_At = L_195_arg0
end)
L_35_.Main:Dropdown("Select Mode", {
	"Quest",
	"Nearest"
}, "Quest", function(L_196_arg0)
	_25msShared.MasteryType = L_196_arg0
end)
L_35_.Main:Label("Hi")
L_35_.Main:Toggle("Auto Farm Fruit Mastery", _25msShared.AutoFarmFruitMastery, function(L_197_arg0)
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
	_25msShared.AutoFarmFruitMastery = L_197_arg0;
	StopTween(_25msShared.AutoFarmFruitMastery)
	if _25msShared.AutoFarmFruitMastery == false then
		UseSkill = false
	end
end)
spawn(function()
	while wait() do
		if _25msShared.AutoFarmFruitMastery and _25msShared.MasteryType == "Quest" then
			pcall(function()
				CheckQ()
				local L_198_ = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text;
				if not string.find(L_198_, NameMon) then
					UseSkill = false;
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
				end;
				if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
					UseSkill = false;
					CheckQ()
					repeat
						wait()
						TP(CFrameQuest)
					until (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _25msShared.AutoFarmFruitMastery;
					if (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
						task.wait()
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", NameQuest, LevelQuest)
						wait(0.5)
					end
				elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
					CheckQ()
					if game:GetService("Workspace").Enemies:FindFirstChild(NameMon) then
						for L_199_forvar0, L_200_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if L_200_forvar1:FindFirstChild("HumanoidRootPart") and L_200_forvar1:FindFirstChild("Humanoid") and L_200_forvar1.Humanoid.Health > 0 then
								if L_200_forvar1.Name == NameMon then
									if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
										HealthMs = L_200_forvar1.Humanoid.MaxHealth * _25msShared.Kill_At / 100;
										repeat
											wait()
											if L_200_forvar1.Humanoid.Health <= HealthMs then
												EquipWeapon(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value)
												TP(L_200_forvar1.HumanoidRootPart.CFrame * CFrame.new(0, 10, 10))
												UseSkill = true;
												FarmPos = L_200_forvar1.HumanoidRootPart.CFrame;
												MonFarm = L_200_forvar1.Name;
												PosMonMasteryAim = L_200_forvar1.HumanoidRootPart.Position;
												_25msShared.AClick = true
											else
												UseSkill = false;
												EquipWeapon(_25msShared.SelectWeapon)
												TP(L_200_forvar1.HumanoidRootPart.CFrame * MethodFarm)
												FarmPos = L_200_forvar1.HumanoidRootPart.CFrame;
												MonFarm = L_200_forvar1.Name;
												StartMagnet = true;
												PosMonMasteryAim = L_200_forvar1.HumanoidRootPart.Position;
												_25msShared.AClick = false
											end
										until not _25msShared.AutoFarmFruitMastery or not _25msShared.MasteryType == "Quest" or L_200_forvar1.Humanoid.Health <= 0 or not L_200_forvar1.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false;
										UseSkill = false
									else
										UseSkill = false;
										StartMagnet = false;
										_25msShared.AClick = false;
										TP(CFrameMon)
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
									end
								end
							end
						end
					else
						UseSkill = false;
						StartMagnet = false;
						TP(CFrameMon)
						local L_201_ = game:GetService("ReplicatedStorage"):FindFirstChild(NameMon)
						if L_201_ then
							TP(L_201_.HumanoidRootPart.CFrame * CFrame.new(0, 10, 10))
						else
							if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame.Y <= 1 then
								game:GetService("Players").LocalPlayer.Character.Humanoid.Jump = true;
								task.wait()
								game:GetService("Players").LocalPlayer.Character.Humanoid.Jump = false
							end
						end
					end
				end
			end)
		elseif _25msShared.AutoFarmFruitMastery and _25msShared.MasteryType == "Nearest" then
			pcall(function()
				for L_202_forvar0, L_203_forvar1 in pairs(game.Workspace.Enemies:GetChildren()) do
					if L_203_forvar1.Name and L_203_forvar1:FindFirstChild("Humanoid") and L_203_forvar1:FindFirstChild("HumanoidRootPart") then
						if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - L_203_forvar1:FindFirstChild("HumanoidRootPart").Position).Magnitude <= 2500 then
							repeat
								wait()
								if L_203_forvar1.Humanoid.Health <= L_203_forvar1.Humanoid.MaxHealth * _25msShared.Kill_At / 100 then
									EquipWeapon(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value)
									TP(L_203_forvar1.HumanoidRootPart.CFrame * CFrame.new(0, 10, 10))
									UseSkill = true;
									FarmPos = L_203_forvar1.HumanoidRootPart.CFrame;
									MonFarm = L_203_forvar1.Name;
									PosMonMasteryAim = L_203_forvar1.HumanoidRootPart.Position;
									_25msShared.AClick = true
								else
									UseSkill = false;
									EquipWeapon(_25msShared.SelectWeapon)
									TP(L_203_forvar1.HumanoidRootPart.CFrame * MethodFarm)
									FarmPos = L_203_forvar1.HumanoidRootPart.CFrame;
									MonFarm = L_203_forvar1.Name;
									StartMagnet = true;
									_25msShared.AClick = false
								end
							until not _25msShared.AutoFarmFruitMastery or not _25msShared.MasteryType == "Nearest" or not L_203_forvar1.Parent or L_203_forvar1.Humanoid.Health == 0;
							UseSkill = false;
							StartMagnet = false;
							_25msShared.AClick = false
						end
					end
				end
			end)
		end
	end
end)
L_35_.Main:Toggle("Auto Farm Gun Mastery", _25msShared.AutoFarmGunMastery, function(L_204_arg0)
	_25msShared.AutoFarmGunMastery = L_204_arg0;
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
	StopTween(_25msShared.AutoFarmGunMastery)
	if _25msShared.AutoFarmGunMastery == false then
		UseSkill = false
	end
end)
spawn(function()
	while wait() do
		if _25msShared.AutoFarmGunMastery and _25msShared.MasteryType == "Quest" then
			pcall(function()
				CheckQ()
				local L_205_ = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text;
				if not string.find(L_205_, NameMon) then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
				end;
				if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
					CheckQ()
					TP(CFrameQuest)
					if (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10 then
						wait(1.2)
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", NameQuest, LevelQuest)
					end
				elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
					CheckQ()
					if game:GetService("Workspace").Enemies:FindFirstChild(NameMon) then
						pcall(function()
							for L_206_forvar0, L_207_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if L_207_forvar1.Name == NameMon then
									repeat
										wait()
										if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
											HealthMin = L_207_forvar1.Humanoid.MaxHealth * _25msShared.Kill_At / 100;
											if L_207_forvar1.Humanoid.Health <= HealthMin then
												EquipWeapon(SelectToolWeaponGun)
												game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = L_207_forvar1.HumanoidRootPart.CFrame * CFrame.new(0, 10, 10)
												UseSkill = true;
												FarmPos = L_207_forvar1.HumanoidRootPart.CFrame;
												MonFarm = L_207_forvar1.Name;
												PosMonMasteryAim = L_207_forvar1.HumanoidRootPart.Position;
												game:GetService("Players").LocalPlayer.Character[SelectToolWeaponGun].RemoteFunctionShoot:InvokeServer(unpack(PosMonMasteryAim))
											else
												UseSkill = false;
												EquipWeapon(_25msShared.SelectWeapon)
												L_207_forvar1.Humanoid.WalkSpeed = 0;
												L_207_forvar1.HumanoidRootPart.CanCollide = false;
												L_207_forvar1.Head.CanCollide = false;
												TP(L_207_forvar1.HumanoidRootPart.CFrame * MethodFarm)
											end;
											FarmPos = L_207_forvar1.HumanoidRootPart.CFrame;
											MonFarm = L_207_forvar1.Name;
											StartMagnet = true
										else
											UseSkill = false;
											StartMagnet = false;
											game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
										end
									until L_207_forvar1.Humanoid.Health <= 0 or _25msShared.AutoFarmGunMastery == false or not _25msShared.MasteryType == "Quest" or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false;
									UseSkill = false;
									StartMagnet = false
								end
							end
						end)
					else
						UseSkill = false;
						StartMagnet = false;
						TP(CFrameMon)
					end
				end
			end)
		elseif _25msShared.AutoFarmGunMastery and _25msShared.MasteryType == "Nearest" then
			pcall(function()
				for L_208_forvar0, L_209_forvar1 in pairs(game.Workspace.Enemies:GetChildren()) do
					if L_209_forvar1.Name and L_209_forvar1:FindFirstChild("Humanoid") and L_209_forvar1:FindFirstChild("HumanoidRootPart") then
						if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - L_209_forvar1:FindFirstChild("HumanoidRootPart").Position).Magnitude <= 1500 then
							repeat
								wait()
								if L_209_forvar1.Humanoid.Health <= L_209_forvar1.Humanoid.MaxHealth * _25msShared.Kill_At / 100 then
									EquipWeapon(SelectToolWeaponGun)
									game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = L_209_forvar1.HumanoidRootPart.CFrame * CFrame.new(0, 10, 10)
									UseSkill = true;
									FarmPos = L_209_forvar1.HumanoidRootPart.CFrame;
									MonFarm = L_209_forvar1.Name;
									PosMonMasteryAim = L_209_forvar1.HumanoidRootPart.Position;
									local L_210_ = {
										[1] = FarmPos
									}
									game:GetService("Players").LocalPlayer.Character[SelectToolWeaponGun].RemoteFunctionShoot:InvokeServer(unpack(L_210_))
								else
									UseSkill = false;
									EquipWeapon(_25msShared.SelectWeapon)
									TP(L_209_forvar1.HumanoidRootPart.CFrame * MethodFarm)
									FarmPos = L_209_forvar1.HumanoidRootPart.CFrame;
									MonFarm = L_209_forvar1.Name;
									StartMagnet = true
								end
							until not _25msShared.AutoFarmGunMastery or not _25msShared.MasteryType == "Quest" or not L_209_forvar1.Parent or L_209_forvar1.Humanoid.Health == 0;
							UseSkill = false;
							StartMagnet = false
						end
					end
				end
			end)
		end
	end
end)
L_35_.Main:Label("Select Skill")
L_35_.Main:Toggle("Skill Z", true, function(L_211_arg0)
	_25msShared.SkillZ = L_211_arg0
end)
L_35_.Main:Toggle("Skill X", _25msShared.SkillX, function(L_212_arg0)
	_25msShared.SkillX = L_212_arg0
end)
L_35_.Main:Toggle("Skill C", _25msShared.SkillC, function(L_213_arg0)
	_25msShared.SkillC = L_213_arg0
end)
L_35_.Main:Toggle("Skill V", _25msShared.SkillV, function(L_214_arg0)
	_25msShared.SkillV = L_214_arg0
end)
spawn(function()
	while wait(.1) do
		if UseSkill then
			pcall(function()
				for L_215_forvar0, L_216_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if _25msShared.SkillZ then
						local L_217_ = {
							[1] = FarmPos
						}
						game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(L_217_))
						SendKey("Z")
					end;
					if _25msShared.SkillX then
						local L_218_ = {
							[1] = FarmPos
						}
						game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(L_218_))
						SendKey("X")
					end;
					if _25msShared.SkillC then
						local L_219_ = {
							[1] = FarmPos
						}
						game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(L_219_))
						SendKey("C")
					end;
					if _25msShared.SkillV then
						local L_220_ = {
							[1] = FarmPos
						}
						game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(L_220_))
						SendKey("V")
					end
				end
			end)
		end
	end
end)
L_35_.Setting:Label("Settings")
L_35_.Setting:Toggle("Anti Stranger Join", false, function(L_221_arg0)
	_25msShared.AntiStranger = L_221_arg0
end)
spawn(function()
	print("|COKKA DEBUG| Anti Stranger Join")
	while wait() do
		pcall(function()
			if _25msShared.AntiStranger then
				for L_222_forvar0, L_223_forvar1 in pairs(game:GetService("Players"):GetChildren()) do
					if L_223_forvar1.Data.Level.Value >= 2601 or L_223_forvar1.Data.Level.Value > 20000 then
						game.Players.LocalPlayer:Kick("Cokka Hub found an Admin!")
						print("|COKKA DEBUG| Detected Stranger, Hopping Server...")
						Hop()
					end
				end
			end
		end)
	end
end)
L_35_.Setting:Toggle("Anti Detection", true, function(L_224_arg0)
	task.spawn(function()
		local L_225_ = {
			["AbuseReportScreenshotPercentage"] = "0",
			["AbuseReportScreenshot"] = "False",
			["DFFlagAbuseReportScreenshot"] = "False",
			["CrashPadUploadToBacktraceToBacktraceBaseUrl"] = "",
			["CrashUploadToBacktracePercentage"] = "0",
			["CrashUploadToBacktraceBlackholeToken"] = "",
			["CrashUploadToBacktraceWindowsPlayerToken"] = ""
		}
		local function L_226_func(L_227_arg0)
			L_227_arg0 = L_227_arg0:gsub("^DFInt", "")
			L_227_arg0 = L_227_arg0:gsub("^DFFlag", "")
			L_227_arg0 = L_227_arg0:gsub("FString", "")
			L_227_arg0 = L_227_arg0:gsub("FLog", "")
			L_227_arg0 = L_227_arg0:gsub("^FFlag", "")
			L_227_arg0 = L_227_arg0:gsub("^DFint", "")
			L_227_arg0 = L_227_arg0:gsub("^FInt", "")
			return L_227_arg0
		end;
		if setfflag then
			task.spawn(function()
				local L_228_ = os.clock()
				for L_229_forvar0, L_230_forvar1 in next,L_225_ do
					pcall(function()
						if getfflag(L_226_func(L_229_forvar0)) then
							setfflag(L_226_func(L_229_forvar0), L_230_forvar1)
						elseif getfflag(L_229_forvar0) then
							setfflag(L_229_forvar0, L_230_forvar1)
						end
					end)
				end;
				print("|COKKA DEBUG| Anti Ban Loaded in: " .. os.clock() - L_228_)
			end)
		else
			print("|COKKA DEBUG| Anti Ban not support this Executor!")
		end
	end)
end)
L_35_.Setting:Line()
_25msShared.SkipDistance = 300;
L_35_.Setting:Slider("Skip Distance", 1, 350, 300, function(L_231_arg0)
	_25msShared.SkipDistance = L_231_arg0
end)
L_35_.Setting:Toggle("Auto Set Home Point", _25msShared.Set, function(L_232_arg0)
	_25msShared.Set = L_232_arg0
end)
spawn(function()
	while wait() do
		if _25msShared.Set then
			L_26_func("SetSpawnPoint")
		end
	end
end)
L_35_.Setting:Toggle("Bring Mob", false, function(L_233_arg0)
	_25msShared.BringMob = L_233_arg0
end)
spawn(function()
	while task.wait() do
		pcall(function()
			if _25msShared.BringMob and StartMagnet then
				for L_234_forvar0, L_235_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if L_235_forvar1.Name == MonFarm and L_235_forvar1:FindFirstChild("Humanoid") and L_235_forvar1.Humanoid.Health > 0 then
						if (L_235_forvar1.PrimaryPart.Position - FarmPos.Position).Magnitude <= 200 then
							L_235_forvar1.PrimaryPart.CFrame = FarmPos;
							L_235_forvar1.PrimaryPart.CanCollide = true;
							L_235_forvar1.HumanoidRootPart.Size = Vector3.new(5, 1, 5)
							L_235_forvar1:FindFirstChild("Humanoid").WalkSpeed = 0;
							L_235_forvar1:FindFirstChild("Humanoid").JumpPower = 0;
							if L_235_forvar1.Humanoid:FindFirstChild("Animator") then
								L_235_forvar1.Humanoid.Animator:Destroy()
							end;
							game.Players.LocalPlayer.SimulationRadius = math.huge
						end
					end
				end
			end
		end)
	end
end)
L_35_.Setting:Toggle("Auto Active Buso", true, function(L_236_arg0)
	_25msShared.AutoBuso = L_236_arg0
end)
spawn(function()
	while wait() do
		if _25msShared.AutoBuso then
			if not L_28_.Character:FindFirstChild("HasBuso") then
				L_26_func("Buso")
			end
		end
	end
end)
L_35_.Setting:Toggle("Auto Active Obversation", false, function(L_237_arg0)
	_25msShared.AutoObs = L_237_arg0
end)
spawn(function()
	while wait() do
		if _25msShared.AutoObs then
			if not L_28_.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
				L_7_:SetKeyDown("0x65")
				wait(2)
				L_7_:SetKeyUp("0x65")
			end
		end
	end
end)
L_35_.Setting:Button("FPS Boost", function()
	pcall(function()
		settings().Rendering.QualityLevel = "Level01"
		setfpscap(144)
		for L_238_forvar0, L_239_forvar1 in pairs(Workspace:GetDescendants()) do
			if L_239_forvar1.ClassName == "Part" or L_239_forvar1.ClassName == "SpawnLocation" or L_239_forvar1.ClassName == "WedgePart" or L_239_forvar1.ClassName == "Terrain" then
				L_239_forvar1.Material = "Plastic"
			end
		end;
		for L_240_forvar0, L_241_forvar1 in pairs(game:GetDescendants()) do
			if L_241_forvar1:IsA("Texture") then
				L_241_forvar1.Texture = ""
			elseif L_241_forvar1:IsA("BasePart") then
				L_241_forvar1.Material = "Plastic"
			end
		end;
		for L_242_forvar0, L_243_forvar1 in pairs(L_28_.PlayerScripts:GetDescendants()) do
			if L_243_forvar1.Name == "RecordMode" or L_243_forvar1.Name == "" or L_243_forvar1.Name == "Fireflies" or L_243_forvar1.Name == "Wind" or L_243_forvar1.Name == "WindShake" or L_243_forvar1.Name == "WindLines" or L_243_forvar1.Name == "WaterBlur" or L_243_forvar1.Name == "WaterEffect" or L_243_forvar1.Name == "wave" or L_243_forvar1.Name == "WaterColorCorrection" or L_243_forvar1.Name == "WaterCFrame" or L_243_forvar1.Name == "MirageFog" or L_243_forvar1.Name == "MobileButtonTransparency" or L_243_forvar1.Name == "WeatherStuff" or L_243_forvar1.Name == "AnimateEntrance" or L_243_forvar1.Name == "Particle" or L_243_forvar1.Name == "AccessoryInvisible" then
				L_243_forvar1:Destroy()
			end
		end
	end)
end)
L_35_.Setting:Toggle("White Screen", false, function(L_244_arg0)
	_25msShared.WhiteScreen = L_244_arg0;
	if _25msShared.WhiteScreen then
		L_8_:Set3dRenderingEnabled(false)
	else
		L_8_:Set3dRenderingEnabled(true)
	end
end)
L_35_.Setting:Toggle("Black Screen", false, function(L_245_arg0)
	_25msShared.BlackScreen = L_245_arg0;
	StartBlackScreen = L_245_arg0;
	local L_246_ = L_28_.PlayerGui.Main.Blackscreen;
	_25msShared.DefaultSize = L_246_.Size;
	_25msShared.NewSize = UDim2.new(500, 0, 500, 500)
	_25msShared.StartBlackScreen = false;
	if StartBlackScreen then
		L_246_.Size = NewSize
	else
		L_246_.Size = UDim2.new(DefaultSize)
	end
end)
L_35_.Setting:Toggle("Auto Active Race V3", false, function(L_247_arg0)
	_25msShared.AutoAgility = L_247_arg0
end)
spawn(function()
	while wait() do
		if _25msShared.AutoAgility then
			game:GetService("ReplicatedStorage").Remotes.CommE:FireServer("ActivateAbility")
		end
	end
end)
L_35_.Setting:Toggle("Auto Active Race V4", false, function(L_248_arg0)
	_25msShared.AutoAwakening = L_248_arg0
end)
spawn(function()
	while wait() do
		if _25msShared.AutoAwakening then
			if L_28_.Character:FindFirstChild("RaceEnergy") and L_28_.Character.RaceEnergy.Value >= 1 and not L_28_.Character.RaceTransformed.Value then
				SendKey("Y")
			end
		end
	end
end)
L_35_.Setting:Toggle("Fast Attack (Smooth)", true, function(L_249_arg0)
	_25msShared.FastAttack = L_249_arg0
end)
L_35_.Setting:Toggle("Bypass TP", false, function(L_250_arg0)
	_25msShared.BypassTP = L_250_arg0
end)
L_35_.Setting:Toggle("Auto Click", false, function(L_251_arg0)
	_25msShared.AClick = L_251_arg0
end)
spawn(function()
	while wait() do
		if _25msShared.AClick then
			L_7_:CaptureController()
			L_7_:Button1Down(Vector2.new(0, 1, 0, 1))
		end
	end
end)
L_35_.Setting:Toggle("Hide Damage", true, function(L_252_arg0)
	_25msShared.HideDamage = L_252_arg0
end)
spawn(function()
	while wait() do
		if _25msShared.HideDamage then
			L_5_.Assets.GUI.DamageCounter.Enabled = false
		else
			L_5_.Assets.GUI.DamageCounter.Enabled = true
		end
	end
end)
L_35_.Setting:Toggle("Hide Notify", false, function(L_253_arg0)
	_25msShared.HideNotify = L_253_arg0
end)
spawn(function()
	while wait() do
		if _25msShared.HideNotify then
			L_28_.PlayerGui.Notifications.Enabled = false
		else
			L_28_.PlayerGui.Notifications.Enabled = true
		end
	end
end)
function BoatShit()
	for L_254_forvar0, L_255_forvar1 in next, game:GetService('Workspace').Boats:GetChildren() do
		if (L_255_forvar1.VehicleSeat.Position - game:GetService('Players').LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1000 then
			return L_255_forvar1
		end
	end;
	return false
end;
function TPBoatShit(L_256_arg0)
	local L_257_ = BoatShit()
	local L_258_ = game:service"TweenService"
	local L_259_ = TweenInfo.new((L_257_.VehicleSeat.Position - L_256_arg0.Position).Magnitude / 150, Enum.EasingStyle.Linear)
	tween, err = pcall(function()
		tweenz = L_258_:Create(L_257_.VehicleSeat, L_259_, {
			CFrame = L_256_arg0
		})
		tweenz:Play()
	end)
	if not tween then
		return err
	end;
	if _25msShared.StopTweenShip then
		local L_260_ = game:service"TweenService"
		local L_261_ = TweenInfo.new((L_257_.VehicleSeat.Position - L_256_arg0.Position).Magnitude / 150, Enum.EasingStyle.Linear)
		tween, err = pcall(function()
			tweenz = L_260_:Create(L_257_.VehicleSeat, L_261_, {
				CFrame = L_256_arg0
			})
			tweenz:Cancel()
		end)
	end
end;
function StopTweenBoatShit(L_262_arg0)
	if not L_262_arg0 then
		_25msShared.StopTweenShip = true;
		wait()
		TPBoatShit(BoatShit().VehicleSeat.CFrame)
		wait(.4)
		TPBoatShit(BoatShit().VehicleSeat.CFrame)
		wait()
		_25msShared.StopTweenShip = false
	end
end;
L_35_.Dragon:Label("Belt")
L_35_.Dragon:Toggle("Auto White Belt", _25msShared.AutoWhiteBelt, function(L_263_arg0)
	_25msShared.AutoWhiteBelt = L_263_arg0;
	StopTween(_25msShared.AutoWhiteBelt)
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.AutoWhiteBelt then
				if game:GetService("Workspace").Enemies:FindFirstChild("Serpent Hunter" or "Skull Slayer") then
					for L_264_forvar0, L_265_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
						if L_265_forvar1.Name == "Reborn Skeleton" or L_265_forvar1.Name == "Serpent Hunter" or L_265_forvar1.Name == "Skull Slayer" then
							if L_265_forvar1:FindFirstChild("Humanoid") and L_265_forvar1:FindFirstChild("HumanoidRootPart") and L_265_forvar1.Humanoid.Health > 0 then
								repeat
									wait()
									EquipWeapon(_25msShared.SelectWeapon)
									FarmPos = L_265_forvar1.PrimaryPart.CFrame;
									MonFarm = L_265_forvar1.Name;
									StartMagnet = true;
									TP(L_265_forvar1.HumanoidRootPart.CFrame * MethodFarm)
									game:GetService("ReplicatedStorage").Modules.Net["RF/InteractDragonQuest"]:InvokeServer({
										["NPC"] = "Dojo Trainer",
										["Command"] = "RequestQuest"
									})
									Workspace.Map.Waterfall.HydraIslandClient.RemoteFunction:InvokeServer("progress")
								until not _25msShared.AutoWhiteBelt or not L_265_forvar1.Parent or L_265_forvar1.Humanoid.Health <= 0;
								StartMagnet = false
							end
						end
					end
				else
					StartMagnet = false;
					TP(CFrame.new(- 16665.462890625, 105.3105697631836, 1577.8289794921875))
				end
			end
		end)
	end
end)
L_35_.Dragon:Toggle("Auto Yellow Belt", _25msShared.AutoYellowBelt, function(L_266_arg0)
	_25msShared.AutoYellowBelt = L_266_arg0;
	StopTween(_25msShared.AutoYellowBelt)
	StopTweenBoatShit(_25msShared.AutoYellowBelt)
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.AutoYellowBelt then
				if game.Players.LocalPlayer.Character.Humanoid.Sit then
					TPBoatShit(CFrame.new(- 28798.533203125, 12.514652252197266, 8322.6572265625))
				elseif not game.Players.LocalPlayer.Character.Humanoid.Sit then
					TPBoatShit(BoatShit().VehicleSeat.CFrame)
				end
			end
		end)
	end
end)
spawn(function()
	function YellowBelt()
		if not CheckInventory("Yellow Belt") == false then
			if not CheckSwanBoat() then
				if (CFrame.new(- 16915.958984375, 9.282610893249512, 511.1013488769531) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 8 then
					TP(CFrame.new(- 16916.068359375, 10.003792762756348, 520.455078125))
				else
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBoat", "PirateBrigade")
					wait(.5)
				end
			else
				if game:GetService("Players").LocalPlayer.Character.Humanoid.Sit then
					autospamskill = false
				else
					if not game:GetService("Players").LocalPlayer.Character.Humanoid.Sit and BoatShit() then
						if (BoatShit().VehicleSeat.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1 then
							game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = BoatShit().VehicleSeat.CFrame;
							TP(BoatShit().VehicleSeat.CFrame)
							autospamskill = false
						end
					end
				end
			end
		end
	end;
	while wait() do
		pcall(function()
			if _25msShared.AutoYellowBelt then
				repeat
					task.wait()
					YellowBelt()
					if game.Players.LocalPlayer.Character.Humanoid.Health <= 0 then
						BoatShit():Destroy()
					end
				until not _25msShared.AutoYellowBelt;
				SendKey("Z")
				SendKey("X")
				SendKey("C")
				SendKey("V")
			end
		end)
	end
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.AutoYellowBelt then
				for L_268_forvar0, L_269_forvar1 in next, game:GetService("Workspace").Boats:GetDescendants() do
					if L_269_forvar1:IsA("BasePart") then
						L_269_forvar1.CanCollide = false
					end
				end;
				local L_267_ = {
					"SmallGroup",
					"SmallCluster",
					"MediumGroup",
					"MediumFlat",
					"Large",
					"Largest"
				}
				for L_270_forvar0, L_271_forvar1 in pairs(workspace:GetChildren()) do
					if table.find(L_267_, L_271_forvar1.Name) and L_271_forvar1:IsA("Model") then
						for L_272_forvar0, L_273_forvar1 in pairs(L_271_forvar1:GetDescendants()) do
							if L_273_forvar1:IsA("BasePart") then
								L_273_forvar1.CanCollide = false
							end
						end
					end
				end
			else
				for L_275_forvar0, L_276_forvar1 in next, game:GetService("Workspace").Boats:GetDescendants() do
					if L_276_forvar1:IsA("BasePart") then
						L_276_forvar1.CanCollide = true
					end
				end;
				local L_274_ = {
					"SmallGroup",
					"SmallCluster",
					"MediumGroup",
					"MediumFlat",
					"Large",
					"Largest"
				}
				for L_277_forvar0, L_278_forvar1 in pairs(workspace:GetChildren()) do
					if table.find(L_274_, L_278_forvar1.Name) and L_278_forvar1:IsA("Model") then
						for L_279_forvar0, L_280_forvar1 in pairs(L_278_forvar1:GetDescendants()) do
							if L_280_forvar1:IsA("BasePart") then
								L_280_forvar1.CanCollide = true
							end
						end
					end
				end
			end
		end)
	end
end)
L_35_.Dragon:Label("Updating...")
function CheckDimension()
	local L_281_ = tonumber(string.match(L_5_.Remotes.CommF_:InvokeServer("CakePrinceSpawner", true), "%d+"))
	if L_281_ then
		return "A Dimension Need More: " .. L_281_
	elseif CheckBossDimension() then
		return "A Dimension: 🟢"
	else
		return "A Dimension Need More: None"
	end
end;
function CheckBribe()
	if L_5_.Remotes.CommF_:InvokeServer("InfoLeviathan", "1") == 1 then
		return "Bribe: I Don't Know Anything Yet"
	elseif L_5_.Remotes.CommF_:InvokeServer("InfoLeviathan", "1") == 2 then
		return "Bribe: I Want Fragments"
	elseif L_5_.Remotes.CommF_:InvokeServer("InfoLeviathan", "1") == 3 then
		return "Bribe: I Want Fragments"
	elseif L_5_.Remotes.CommF_:InvokeServer("InfoLeviathan", "1") == 4 then
		return "Bribe: I Want Fragments"
	elseif L_5_.Remotes.CommF_:InvokeServer("InfoLeviathan", "1") == 5 then
		return "Leviathan Is Out There!"
	else
		return "What is Bribe? You account don't know it yet"
	end
end;
function CheckElite()
	if L_5_:FindFirstChild("Diablo") or game:GetService("ReplicatedStorage"):FindFirstChild("Deandre") or game:GetService("ReplicatedStorage"):FindFirstChild("Urban") or game:GetService("Workspace").Enemies:FindFirstChild("Diablo") or game:GetService("Workspace").Enemies:FindFirstChild("Deandre") or game:GetService("Workspace").Enemies:FindFirstChild("Urban") then
		return "Elite: 🟢"
	else
		return "Elite: 🔴"
	end
end;
function CheckMirage()
	if L_13_.Locations:FindFirstChild("Mirage Island") then
		return "Mirage Island: 🟢"
	else
		return "Mirage Island: 🔴"
	end
end;
function CheckKitsune()
	if L_13_:FindFirstChild("Kitsune Island") then
		return "Kitsune Island: 🟢"
	else
		return "Kitsune Island: 🔴"
	end
end;
function MoonTextureId()
	if L_23_ then
		return game:GetService("Lighting").FantasySky.MoonTextureId
	elseif L_24_ then
		return game:GetService("Lighting").FantasySky.MoonTextureId
	elseif L_25_ then
		return game:GetService("Lighting").Sky.MoonTextureId
	end
end;
function CheckMoonTexture()
	moon8 = "http://www.roblox.com/asset/?id=9709150401"
	moon7 = "http://www.roblox.com/asset/?id=9709150086"
	moon6 = "http://www.roblox.com/asset/?id=9709149680"
	moon5 = "http://www.roblox.com/asset/?id=9709149431"
	moon4 = "http://www.roblox.com/asset/?id=9709149052"
	moon3 = "http://www.roblox.com/asset/?id=9709143733"
	moon2 = "http://www.roblox.com/asset/?id=9709139597"
	moon1 = "http://www.roblox.com/asset/?id=9709135895"
	bluemoon = "http://www.roblox.com/asset/?id=4303207962"
	moonreal = MoonTextureId()
	default = "No Full Moon"
	if moonreal == moon5 or moonreal == moon4 then
		if moonreal == moon5 or moonreal == bluemoon then
			default = "Full Moon"
		elseif moonreal == moon4 then
			default = "Next Night"
		end
	end;
	return default
end;
function ClockTime()
	return math.floor(game.Lighting.ClockTime)
end;
function CheckMoon()
	local L_282_ = game.Lighting;
	local L_283_ = L_282_.ClockTime;
	if L_283_ >= 18 or L_283_ < 5 then
		GameTime = "Night"
	else
		GameTime = "Day"
	end;
	if CheckMoonTexture() == "Full Moon" and L_283_ <= 5 then
		return tostring(ClockTime() .. "h : ") .. "( Will End Moon In " .. math.floor(5 - L_283_) .. " Minutes )"
	elseif CheckMoonTexture() == "Full Moon" and (L_283_ > 5 and L_283_ < 12) then
		return tostring(ClockTime() .. "h : ") .. "( Fake Moon )"
	elseif CheckMoonTexture() == "Full Moon" and (L_283_ > 12 and L_283_ < 18) then
		return tostring(ClockTime() .. "h : ") .. "( Will Full Moon In " .. math.floor(18 - L_283_) .. " Minutes )"
	elseif CheckMoonTexture() == "Full Moon" and (L_283_ > 18 and L_283_ <= 24) then
		return tostring(ClockTime() .. "h : ") .. "( Will End Moon In " .. math.floor(24 + 6 - L_283_) .. " Minutes )"
	end;
	if CheckMoonTexture() == "Next Night" and L_283_ < 12 then
		return tostring(ClockTime() .. "h : ") .. "( Will Full Moon In " .. math.floor(18 - L_283_) .. " Minutes )"
	elseif CheckMoonTexture() == "Next Night" and L_283_ > 12 then
		return tostring(ClockTime() .. "h : ") .. "( Will Full Moon In " .. math.floor(18 + 12 - L_283_) .. " Minutes )"
	end;
	if CheckMoonTexture() == "No Full Moon" then
		return tostring(ClockTime() .. "h : ") .. "No Full Moon"
	end
end;
function CheckLegendarySword()
	if L_24_ and L_5_.Remotes.CommF_:InvokeServer("LegendarySwordDealer", "1") == "Shisui" then
		return "Legendary Sword: Shisui"
	elseif L_24_ and L_5_.Remotes.CommF_:InvokeServer("LegendarySwordDealer", "1") == "Saddi" then
		return "Legendary Sword: Saddi"
	elseif L_24_ and L_5_.Remotes.CommF_:InvokeServer("LegendarySwordDealer", "1") == "Wando" then
		return "Legendary Sword: Wando"
	elseif L_25_ then
		return "Legendary Sword: 🔴"
	else
		return "Legendary Sword: 🔴"
	end
end;
local L_37_ = L_35_.Status:Label("?")
local L_38_ = L_35_.Status:Label("?")
local L_39_ = L_35_.Status:Label("?")
local L_40_ = L_35_.Status:Label("?")
local L_41_ = L_35_.Status:Label("?")
local L_42_ = L_35_.Status:Label("?")
local L_43_ = L_35_.Status:Label("?")
local L_44_ = L_35_.Status:Label("?")
local L_45_ = L_35_.Status:Label("?")
spawn(function()
	while wait() do
		pcall(function()
			local L_284_ = game.Workspace.DistributedGameTime;
			local L_285_ = L_284_ % 60;
			local L_286_ = math.floor(L_284_ / 60 % 60)
			local L_287_ = math.floor(L_284_ / 3600)
			local L_288_ = string.format("%.0fh:%.0fm:%.0fs", L_287_, L_286_, L_285_)
			L_37_:Set(L_288_)
		end)
	end
end)
task.spawn(function()
	while wait() do
		L_38_:Set(CheckDimension())
		L_39_:Set("Bone You Have: " .. (L_5_.Remotes.CommF_:InvokeServer("Bones", "Check") or "unknown"))
		L_40_:Set(CheckBribe())
		L_41_:Set(CheckElite())
		L_42_:Set(CheckMirage())
		L_43_:Set(CheckKitsune())
		L_44_:Set(CheckMoon())
		L_45_:Set(CheckLegendarySword())
	end
end)
L_35_.SeaEvent:Toggle("Always Day", false, function(L_289_arg0)
	_25msShared.AlwaysDay = L_289_arg0
end)
spawn(function()
	while task.wait() do
		if _25msShared.AlwaysDay then
			L_8_.Heartbeat:wait()
			do
				game:GetService("Lighting").ClockTime = 12
			end
		end
	end
end)
L_35_.SeaEvent:Button("Remove Fog", function()
	game:GetService("Lighting").BaseAtmosphere:Destroy()
	game:GetService("Lighting").SeaTerrorCC:Destroy()
	game.Lighting.LightingLayers.DarkFog:Destroy()
end)
_25msShared.BoatSpeed = ""
local function L_46_func()
	local L_290_ = _25msShared.BoatSpeed;
	local L_291_ = 150 + 50 * (L_290_ - 1)
	for L_292_forvar0, L_293_forvar1 in pairs(game:GetService("Workspace").Boats:GetChildren()) do
		if L_293_forvar1:IsA("Model") then
			for L_294_forvar0, L_295_forvar1 in pairs(L_293_forvar1:GetChildren()) do
				if L_295_forvar1:IsA("VehicleSeat") then
					L_295_forvar1.MaxSpeed = L_291_
				end
			end
		end
	end
end;
L_35_.SeaEvent:Slider("Drive Boat Speed", 1, 5, 1, function(L_296_arg0)
	_25msShared.BoatSpeed = L_296_arg0;
	L_46_func()
end)
L_35_.SeaEvent:Toggle("Auto Kill Terrorshark [Fixed + Dodge]", _25msShared.AutoTerrorShark, function(L_297_arg0)
	_25msShared.AutoTerrorShark = L_297_arg0;
	StopTween(_25msShared.AutoTerrorShark)
end)
--here
spawn(function()
	while wait() do
		if _25msShared.AutoTerrorShark and L_25_ then
			pcall(function()
				if game:GetService("Workspace").Enemies:FindFirstChild("Terrorshark") then
					for L_300_forvar0, L_301_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
						if L_301_forvar1.Name == "Terrorshark" then
							if L_301_forvar1:FindFirstChild("Humanoid") and L_301_forvar1:FindFirstChild("HumanoidRootPart") and L_301_forvar1.Humanoid.Health > 0 then
								repeat
									wait()
									EquipWeapon(_25msShared.SelectWeapon)
									L_301_forvar1.HumanoidRootPart.CanCollide = false;
									L_301_forvar1.Humanoid.WalkSpeed = 0;
									L_301_forvar1.Head.CanCollide = false;
									FarmPos = L_301_forvar1.HumanoidRootPart.CFrame;
									MonFarm = L_301_forvar1.Name;
									TP(L_301_forvar1.HumanoidRootPart.CFrame * DodgeTerrorShark)
								until not _25msShared.AutoTerrorShark or not L_301_forvar1.Parent or L_301_forvar1.Humanoid.Health <= 0
							end
						end
					end
				else
					if game:GetService("ReplicatedStorage"):FindFirstChild("Terrorshark") then
						TP(game:GetService("ReplicatedStorage"):FindFirstChild("Terrorshark").HumanoidRootPart.CFrame * CFrame.new(2, 60, 2))
					else
						if _25msShared.StardHop then
							Hop()
						end
					end
				end
			end)
		end
	end
end)
L_35_.SeaEvent:Toggle("Auto Kill Near Mobs", _25msShared.NeareastFarm, function(L_302_arg0)
	_25msShared.NeareastFarm = L_302_arg0;
	StopTween(_25msShared.NeareastFarm)
end)
L_35_.SeaEvent:Toggle("Auto Kill Ghost Ships", _25msShared.AutoKillGhostShip, function(L_303_arg0)
	_25msShared.AutoKillGhostShip = L_303_arg0;
	StopTween(_25msShared.AutoKillGhostShip)
end)
spawn(function()
	while wait() do
		if _25msShared.AutoKillGhostShip then
			pcall(function()
				if CheckPirateBoat() then
					if game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit == true then
						game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit = false
					end;
					local L_304_ = CheckPirateBoat()
					repeat
						wait()
						EquipWeapon(_25msShared.SelectWeapon)
						TP(L_304_.Engine.CFrame * CFrame.new(0, - 20, 0))
						autospamskill = true;
						psskill = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, - 500, 0)
					until not L_304_ or not L_304_.Parent or L_304_.Health.Value <= 0 or not CheckPirateBoat() or not _25msShared.AutoKillGhostShip;
					psskill = nil;
					autospamskill = false
				end
			end)
		end
	end
end)
L_35_.SeaEvent:Toggle("Auto Kill SeaBeast", _25msShared.AutoKillSeaBeast, function(L_305_arg0)
	_25msShared.AutoKillSeaBeast = L_305_arg0;
	StopTween(_25msShared.AutoKillGhostShip)
end)
spawn(function()
	while wait() do
		if _25msShared.AutoKillSeaBeast then
			repeat
				wait()
				local L_306_ = CheckSeaBeast()
				if game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit == true then
					game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit = false
				end;
				TeleportSeabeast(L_306_)
				for L_307_forvar0, L_308_forvar1 in pairs(game:GetService('Workspace').SeaBeasts:GetChildren()) do
					if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - L_308_forvar1:FindFirstChild('HumanoidRootPart').Position).Magnitude <= 500 then
						autospamskill = true;
						psskill = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, - 500, 0)
					end
				end
			until not L_306_ or not L_306_.Parent or L_306_.Health.Value <= 0 or game.Players.LocalPlayer.Character.Humanoid.Health <= 0 or not CheckSeaBeast() or not _25msShared.AutoKillSeaBeast;
			autospamskill = false;
			psskill = nil
		end
	end
end)
L_35_.SeaEvent:Label("Select Weapons Will Farm SeaEvents")
L_35_.SeaEvent:Toggle("Melee Skill", true, function(L_309_arg0)
	_25msShared.SpamMelee = L_309_arg0
end)
L_35_.SeaEvent:Toggle("Fruit Skill", true, function(L_310_arg0)
	_25msShared.SpamDF = L_310_arg0
end)
L_35_.SeaEvent:Toggle("Gun Skill", true, function(L_311_arg0)
	_25msShared.SpamGun = L_311_arg0
end)
L_35_.SeaEvent:Toggle("Sword Skill", true, function(L_312_arg0)
	_25msShared.SpamSword = L_312_arg0
end)
L_35_.SeaEvent:Label("Stop If Bug")
L_35_.SeaEvent:Button("Stop Spam", function()
	autospamskill = false
end)
L_35_.SeaEvent:Label("Still updating...")
L_35_.Kitsune:Toggle("Teleport to Kitsune Island", false, function(L_313_arg0)
	_25msShared.KitsuneIsland = L_313_arg0;
	StopTween(_25msShared.KitsuneIsland)
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.KitsuneIsland then
				for L_314_forvar0, L_315_forvar1 in pairs(game:GetService("Workspace")._WorldOrigin.Locations:GetChildren()) do
					if L_315_forvar1.Name == "Kitsune Island" then
						TP(L_315_forvar1.CFrame * CFrame.new(0, 250, 0))
					end
				end
			end
		end)
	end
end)
L_35_.Kitsune:Toggle("Auto Collect Azure Ember", _25msShared.AutoAzureEmber, function(L_316_arg0)
	_25msShared.AutoAzureEmber = L_316_arg0;
	StopTween(_25msShared.AutoAzureEmber)
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.AutoAzureEmber then
				local L_317_ = game.Players;
				local L_318_ = L_317_.LocalPlayer;
				local L_319_ = game:GetService("Workspace").EmberTemplate.Part;
				function TeleportAzureEmber()
					L_318_.Character.HumanoidRootPart.CFrame = CFrame.new(L_319_.Position)
				end;
				TeleportAzureEmber()
			end
		end)
	end
end)
L_35_.Kitsune:Toggle("Auto Pray Kitsune Statue", _25msShared.AutoPrayKitsune, function(L_320_arg0)
	_25msShared.AutoPrayKitsune = L_320_arg0
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.AutoPrayKitsune then
				wait(0.6)
				game:GetService("ReplicatedStorage"):WaitForChild("Modules"):WaitForChild("Net"):WaitForChild("RF/KitsuneStatuePray"):InvokeServer()
			end
		end)
	end
end)
L_35_.QuestItem:Label("Elite Hunter")
L_35_.QuestItem:Toggle("Auto Farm Elite", _25msShared.AutoElitehunter, function(L_321_arg0)
	_25msShared.AutoElitehunter = L_321_arg0;
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter")
	StopTween(_25msShared.AutoElitehunter)
end)
spawn(function()
	while task.wait() do
		if _25msShared.AutoElitehunter then
			pcall(function()
				if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
					if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Diablo") or string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Deandre") or string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Urban") then
						if game:GetService("Workspace").Enemies:FindFirstChild("Diablo") or game:GetService("Workspace").Enemies:FindFirstChild("Deandre") or game:GetService("Workspace").Enemies:FindFirstChild("Urban") then
							for L_322_forvar0, L_323_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if L_323_forvar1:FindFirstChild("Humanoid") and L_323_forvar1:FindFirstChild("HumanoidRootPart") and L_323_forvar1.Humanoid.Health > 0 then
									if L_323_forvar1.Name == "Diablo" or L_323_forvar1.Name == "Deandre" or L_323_forvar1.Name == "Urban" then
										repeat
											wait()
											EquipWeapon(_25msShared.SelectWeapon)
											TP(L_323_forvar1.HumanoidRootPart.CFrame * MethodFarm)
											FarmPos = L_323_forvar1.HumanoidRootPart.CFrame;
											MonFarm = L_323_forvar1.Name;
											L_323_forvar1.HumanoidRootPart.Size = Vector3.new(1, 1, 1)
										until _25msShared.AutoElitehunter == false or L_323_forvar1.Humanoid.Health <= 0 or not L_323_forvar1.Parent
									end
								end
							end
						else
							if game:GetService("ReplicatedStorage"):FindFirstChild("Diablo") then
								TP(game:GetService("ReplicatedStorage"):FindFirstChild("Diablo").HumanoidRootPart.CFrame * MethodFarm)
							elseif game:GetService("ReplicatedStorage"):FindFirstChild("Deandre") then
								TP(game:GetService("ReplicatedStorage"):FindFirstChild("Deandre").HumanoidRootPart.CFrame * MethodFarm)
							elseif game:GetService("ReplicatedStorage"):FindFirstChild("Urban") then
								TP(game:GetService("ReplicatedStorage"):FindFirstChild("Urban").HumanoidRootPart.CFrame * MethodFarm)
							end
						end
					end
				else
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter")
				end
			end)
		end
	end
end)
local L_47_ = L_35_.QuestItem:Label1("Observation: ?")
L_35_.QuestItem:Toggle("Auto Farm Observation", _25msShared.AutoObservation, function(L_324_arg0)
	_25msShared.AutoObservation = L_324_arg0;
	StopTween(_25msShared.AutoObservation)
end)
spawn(function()
	while wait() do
		pcall(function()
			L_47_:Set("Observation: " .. math.floor(game:GetService("Players").LocalPlayer.VisionRadius.Value))
			if _25msShared.AutoObservation then
				repeat
					wait()
					if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
						game:GetService("VirtualUser"):CaptureController()
						game:GetService("VirtualUser"):SetKeyDown("0x65")
						wait(2)
						game:GetService("VirtualUser"):SetKeyUp("0x65")
					end
				until game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") or not _25msShared.AutoObservation
			end
		end)
	end
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.AutoObservation then
				if L_24_ then
					if game:GetService("Workspace").Enemies:FindFirstChild("Lava Pirate") then
						if game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
							repeat
								wait()
								game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Lava Pirate").HumanoidRootPart.CFrame * CFrame.new(3, 0, 0)
							until _25msShared.AutoObservation == false or not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
						else
							repeat
								wait()
								game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Lava Pirate").HumanoidRootPart.CFrame * CFrame.new(0, 40, 0) + wait(1)
								if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") and _25msShared.AutoObservation_Hop == true then
									game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").LocalPlayer)
								end
							until _25msShared.AutoObservation == false or game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
						end
					else
						TP(CFrame.new(- 5478.39209, 15.9775667, - 5246.9126))
					end
				elseif L_23_ then
					if game:GetService("Workspace").Enemies:FindFirstChild("Galley Captain") then
						if game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
							repeat
								wait()
								game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Galley Captain").HumanoidRootPart.CFrame * CFrame.new(3, 0, 0)
							until _25msShared.AutoObservation == false or not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
						else
							repeat
								wait()
								game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Galley Captain").HumanoidRootPart.CFrame * CFrame.new(0, 40, 0)
								wait(1)
								if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") and _25msShared.AutoObservation_Hop == true then
									game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").LocalPlayer)
								end
							until _25msShared.AutoObservation == false or game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
						end
					else
						TP(CFrame.new(5533.29785, 88.1079102, 4852.3916))
					end
				elseif L_25_ then
					if game:GetService("Workspace").Enemies:FindFirstChild("Giant Islander") then
						if game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
							repeat
								wait()
								game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Giant Islander").HumanoidRootPart.CFrame * CFrame.new(3, 0, 0)
							until _25msShared.AutoObservation == false or not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
						else
							repeat
								wait()
								game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Giant Islander").HumanoidRootPart.CFrame * CFrame.new(0, 40, 0)
								wait(1)
								if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") and _25msShared.AutoObservation_Hop == true then
									game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").LocalPlayer)
								end
							until _25msShared.AutoObservation == false or game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
						end
					else
						TP(CFrame.new(4530.3540039063, 656.75695800781, - 131.60952758789))
					end
				end
			end
		end)
	end
end)
L_35_.QuestItem:Label("Legendary Sword")
L_35_.QuestItem:Toggle("Auto Buy Legendary Sword", _25msShared.AutoBuyLegendarySword, function(L_325_arg0)
	_25msShared.AutoBuyLegendarySword = L_325_arg0
end)
spawn(function()
	while wait() do
		if _25msShared.AutoBuyLegendarySword then
			pcall(function()
				local L_326_ = {
					[1] = "LegendarySwordDealer",
					[2] = "1"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(L_326_))
				local L_327_ = {
					[1] = "LegendarySwordDealer",
					[2] = "2"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(L_327_))
				local L_328_ = {
					[1] = "LegendarySwordDealer",
					[2] = "3"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(L_328_))
				if _25msShared.AutoBuyLegendarySword_Hop and _25msShared.AutoBuyLegendarySword and L_24_ then
					wait(10)
					Hop()
				end
			end)
		end
	end
end)
L_35_.QuestItem:Toggle("Auto Buy Haki Color", _25msShared.AutoBuyHakiColor, function(L_329_arg0)
	_25msShared.AutoBuyHakiColor = L_329_arg0
end)
spawn(function()
	while wait() do
		if _25msShared.AutoBuyHakiColor then
			local L_330_ = {
				[1] = "ColorsDealer",
				[2] = "2"
			}
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(L_330_))
			if _25msShared.AutoBuyHakiColor_Hop and _25msShared.AutoBuyHakiColor and not L_23_ then
				wait(10)
				Hop()
			end
		end
	end
end)
L_35_.QuestItem:Label("Quest & Item | Sea 3")
if L_25_ then
	spawn(function()
		while wait() do
			if _25msShared.AutoCavander then
				pcall(function()
					if game:GetService("Workspace").Enemies:FindFirstChild("Beautiful Pirate") then
						for L_331_forvar0, L_332_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if L_332_forvar1.Name == "Beautiful Pirate" then
								if L_332_forvar1:FindFirstChild("Humanoid") and L_332_forvar1:FindFirstChild("HumanoidRootPart") and L_332_forvar1.Humanoid.Health > 0 then
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										L_332_forvar1.HumanoidRootPart.CanCollide = false;
										L_332_forvar1.Humanoid.WalkSpeed = 0;
										L_332_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										TP(L_332_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
									until not _25msShared.AutoCavander or not L_332_forvar1.Parent or L_332_forvar1.Humanoid.Health <= 0
								end
							end
						end
					else
						TP(CFrame.new(5378.6611328125, 444.58258056640625, 123.93569946289062))
						if game:GetService("ReplicatedStorage"):FindFirstChild("Beautiful Pirate") then
							TP(game:GetService("ReplicatedStorage"):FindFirstChild("Beautiful Pirate").HumanoidRootPart.CFrame * CFrame.new(0, 35, 0))
						else
							if _25msShared.AutoCavanderhop then
								Hop()
							end
						end
					end
				end)
			end
		end
	end)
	spawn(function()
		while wait() do
			if _25msShared.AutoTwinHooks then
				pcall(function()
					if game:GetService("Workspace").Enemies:FindFirstChild("Captain Elephant") then
						for L_333_forvar0, L_334_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if L_334_forvar1.Name == "Captain Elephant" then
								if L_334_forvar1:FindFirstChild("Humanoid") and L_334_forvar1:FindFirstChild("HumanoidRootPart") and L_334_forvar1.Humanoid.Health > 0 then
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										L_334_forvar1.HumanoidRootPart.CanCollide = false;
										L_334_forvar1.Humanoid.WalkSpeed = 0;
										L_334_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										TP(L_334_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
									until not _25msShared.AutoTwinHooks or not L_334_forvar1.Parent or L_334_forvar1.Humanoid.Health <= 0
								end
							end
						end
					else
						TP(CFrame.new(- 13317.37109375, 319.21295166015625, - 8621.72265625))
						if game:GetService("ReplicatedStorage"):FindFirstChild("Captain Elephant") then
							TP(game:GetService("ReplicatedStorage"):FindFirstChild("Captain Elephant").HumanoidRootPart.CFrame * CFrame.new(0, 35, 0))
						else
							if _25msShared.AutoTwinHook_Hop then
								Hop()
							end
						end
					end
				end)
			end
		end
	end)
	spawn(function()
		while wait() do
			if _25msShared.AutoYama then
				if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter", "Progress") >= 30 then
					repeat
						wait()
						fireclickdetector(game:GetService("Workspace").Map.Waterfall.SealedKatana.Handle.ClickDetector)
					until game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Yama") or not _25msShared.AutoYama
				end
			end
		end
	end)
	spawn(function()
		while wait() do
			if _25msShared.AutoTushita then
				if game:GetService("Workspace").Enemies:FindFirstChild("Longma") then
					for L_335_forvar0, L_336_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
						if L_336_forvar1.Name == ("Longma" or L_336_forvar1.Name == "Longma") and L_336_forvar1.Humanoid.Health > 0 and L_336_forvar1:IsA("Model") and L_336_forvar1:FindFirstChild("Humanoid") and L_336_forvar1:FindFirstChild("HumanoidRootPart") then
							repeat
								wait()
								StartMagnet = true;
								if not game.Players.LocalPlayer.Character:FindFirstChild(_25msShared.SelectWeapon) then
									wait()
									EquipWeapon(_25msShared.SelectWeapon)
								end;
								PosMon = L_336_forvar1.HumanoidRootPart.CFrame;
								L_336_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
								L_336_forvar1.Humanoid.JumpPower = 0;
								L_336_forvar1.Humanoid.WalkSpeed = 0;
								L_336_forvar1.HumanoidRootPart.CanCollide = false;
								L_336_forvar1.Humanoid:ChangeState(11)
								TP(L_336_forvar1.HumanoidRootPart.CFrame * MethodFarm)
							until not _25msShared.Autotushita or not L_336_forvar1.Parent or L_336_forvar1.Humanoid.Health <= 0;
							StartMagnet = false
						end
					end
				else
					TP(CFrame.new(- 10238.875976563, 389.7912902832, - 9549.7939453125))
				end
			end
		end
	end)
	spawn(function()
		while wait() do
			if _25msShared.AutoHolyTorch then
				pcall(function()
					wait(1)
					if _25msShared.AutoHolyTorch then
						repeat
							TP(CFrame.new(- 10752, 417, - 9366))
							wait()
						until not _25msShared.AutoHolyTorch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 10752, 417, - 9366)).Magnitude <= 10
					end;
					wait(1)
					if _25msShared.AutoHolyTorch then
						repeat
							TP(CFrame.new(- 11672, 334, - 9474))
							wait()
						until not _25msShared.AutoHolyTorch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 11672, 334, - 9474)).Magnitude <= 10
					end;
					wait(1)
					if _25msShared.AutoHolyTorch then
						repeat
							TP(CFrame.new(- 12132, 521, - 10655))
							wait()
						until not _25msShared.AutoHolyTorch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 12132, 521, - 10655)).Magnitude <= 10
					end;
					wait(1)
					if _25msShared.AutoHolyTorch then
						repeat
							TP(CFrame.new(- 13336, 486, - 6985))
							wait()
						until not _25msShared.AutoHolyTorch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 13336, 486, - 6985)).Magnitude <= 10
					end;
					wait(1)
					if _25msShared.AutoHolyTorch then
						repeat
							TP(CFrame.new(- 13489, 332, - 7925))
							wait()
						until not _25msShared.AutoHolyTorch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 13489, 332, - 7925)).Magnitude <= 10
					end;
					wait(1)
				end)
			end
		end
	end)
	spawn(function()
		pcall(function()
			while wait() do
				if _25msShared.AutoMusketeerHat then
					if game:GetService("Players").LocalPlayer.Data.Level.Value >= 1800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress").KilledBandits == false then
						if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Forest Pirate") and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "50") and game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
							if game:GetService("Workspace").Enemies:FindFirstChild("Forest Pirate") then
								for L_337_forvar0, L_338_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if L_338_forvar1.Name == "Forest Pirate" then
										repeat
											wait()
											pcall(function()
												EquipWeapon(_25msShared.SelectWeapon)
												L_338_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
												TP(L_338_forvar1.HumanoidRootPart.CFrame * MethodFarm)
												L_338_forvar1.HumanoidRootPart.CanCollide = false;
												FarmPos = L_338_forvar1.HumanoidRootPart.CFrame;
												MonFarm = L_338_forvar1.Name;
												StartMagnet = true
											end)
										until _25msShared.AutoMusketeerHat == false or not L_338_forvar1.Parent or L_338_forvar1.Humanoid.Health <= 0 or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false;
										StartMagnet = false
									end
								end
							else
								TP(CFrame.new(- 13206.452148438, 425.89199829102, - 7964.5537109375))
								StartMagnet = false
							end
						else
							TP(CFrame.new(- 12443.8671875, 332.40396118164, - 7675.4892578125))
							if (Vector3.new(- 12443.8671875, 332.40396118164, - 7675.4892578125) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 30 then
								wait(1.5)
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", "CitizenQuest", 1)
							end
						end
					elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 1800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress").KilledBoss == false then
						if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Captain Elephant") and game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
							if game:GetService("Workspace").Enemies:FindFirstChild("Captain Elephant") then
								for L_339_forvar0, L_340_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if L_340_forvar1.Name == "Captain Elephant" then
										OldCFrameElephant = L_340_forvar1.HumanoidRootPart.CFrame;
										repeat
											wait()
											pcall(function()
												EquipWeapon(_25msShared.SelectWeapon)
												L_340_forvar1.HumanoidRootPart.CanCollide = false;
												L_340_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
												TP(L_340_forvar1.HumanoidRootPart.CFrame * MethodFarm)
												L_340_forvar1.HumanoidRootPart.CanCollide = false;
												L_340_forvar1.HumanoidRootPart.CFrame = OldCFrameElephant;
												sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
											end)
										until _25msShared.AutoMusketeerHat == false or L_340_forvar1.Humanoid.Health <= 0 or not L_340_forvar1.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
									end
								end
							else
								TP(CFrame.new(- 13374.889648438, 421.27752685547, - 8225.208984375))
							end
						else
							TP(CFrame.new(- 12443.8671875, 332.40396118164, - 7675.4892578125))
							if (CFrame.new(- 12443.8671875, 332.40396118164, - 7675.4892578125).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4 then
								wait(1.5)
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress", "Citizen")
							end
						end
					elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 1800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress", "Citizen") == 2 then
						TP(CFrame.new(- 12512.138671875, 340.39279174805, - 9872.8203125))
					end
				end
			end
		end)
	end)
	spawn(function()
		pcall(function()
			while wait() do
				if _25msShared.AutoRainbowHaki then
					if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
						TP(CFrame.new(- 11892.0703125, 930.57672119141, - 8760.1591796875))
						if (Vector3.new(- 11892.0703125, 930.57672119141, - 8760.1591796875) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 30 then
							wait(1.5)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("HornedMan", "Bet")
						end
					elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Stone") then
						if game:GetService("Workspace").Enemies:FindFirstChild("Stone") then
							for L_341_forvar0, L_342_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if L_342_forvar1.Name == "Stone" then
									OldCFrameRainbow = L_342_forvar1.HumanoidRootPart.CFrame;
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										TP(L_342_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										L_342_forvar1.HumanoidRootPart.CanCollide = false;
										L_342_forvar1.HumanoidRootPart.CFrame = OldCFrameRainbow;
										L_342_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
									until _25msShared.AutoRainbowHaki == false or L_342_forvar1.Humanoid.Health <= 0 or not L_342_forvar1.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
								end
							end
						else
							TP(CFrame.new(- 1086.11621, 38.8425903, 6768.71436, 0.0231462717, - 0.592676699, 0.805107772, 2.03251839e-05, 0.805323839, 0.592835128, - 0.999732077, - 0.0137055516, 0.0186523199))
						end
					elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Island Empress") then
						if game:GetService("Workspace").Enemies:FindFirstChild("Island Empress") then
							for L_343_forvar0, L_344_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if L_344_forvar1.Name == "Island Empress" then
									OldCFrameRainbow = L_344_forvar1.HumanoidRootPart.CFrame;
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										TP(L_344_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										L_344_forvar1.HumanoidRootPart.CanCollide = false;
										L_344_forvar1.HumanoidRootPart.CFrame = OldCFrameRainbow;
										L_344_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
									until _25msShared.AutoRainbowHaki == false or L_344_forvar1.Humanoid.Health <= 0 or not L_344_forvar1.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
								end
							end
						else
							TP(CFrame.new(5713.98877, 601.922974, 202.751251, - 0.101080291, - 0, - 0.994878292, - 0, 1, - 0, 0.994878292, 0, - 0.101080291))
						end
					elseif string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Kilo Admiral") then
						if game:GetService("Workspace").Enemies:FindFirstChild("Kilo Admiral") then
							for L_345_forvar0, L_346_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if L_346_forvar1.Name == "Kilo Admiral" then
									OldCFrameRainbow = L_346_forvar1.HumanoidRootPart.CFrame;
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										TP(L_346_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										L_346_forvar1.HumanoidRootPart.CanCollide = false;
										L_346_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										L_346_forvar1.HumanoidRootPart.CFrame = OldCFrameRainbow;
										sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
									until _25msShared.AutoRainbowHaki == false or L_346_forvar1.Humanoid.Health <= 0 or not L_346_forvar1.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
								end
							end
						else
							TP(CFrame.new(2877.61743, 423.558685, - 7207.31006, - 0.989591599, - 0, - 0.143904909, - 0, 1.00000012, - 0, 0.143904924, 0, - 0.989591479))
						end
					elseif string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Captain Elephant") then
						if game:GetService("Workspace").Enemies:FindFirstChild("Captain Elephant") then
							for L_347_forvar0, L_348_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if L_348_forvar1.Name == "Captain Elephant" then
									OldCFrameRainbow = L_348_forvar1.HumanoidRootPart.CFrame;
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										TP(L_348_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										L_348_forvar1.HumanoidRootPart.CanCollide = false;
										L_348_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										L_348_forvar1.HumanoidRootPart.CFrame = OldCFrameRainbow;
										sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
									until _25msShared.AutoRainbowHaki == false or L_348_forvar1.Humanoid.Health <= 0 or not L_348_forvar1.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
								end
							end
						else
							TP(CFrame.new(- 13485.0283, 331.709259, - 8012.4873, 0.714521289, 7.98849911e-08, 0.69961375, - 1.02065748e-07, 1, - 9.94383065e-09, - 0.69961375, - 6.43015241e-08, 0.714521289))
						end
					elseif string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Beautiful Pirate") then
						if game:GetService("Workspace").Enemies:FindFirstChild("Beautiful Pirate") then
							for L_349_forvar0, L_350_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if L_350_forvar1.Name == "Beautiful Pirate" then
									OldCFrameRainbow = L_350_forvar1.HumanoidRootPart.CFrame;
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										TP(L_350_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										L_350_forvar1.HumanoidRootPart.CanCollide = false;
										L_350_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										L_350_forvar1.HumanoidRootPart.CFrame = OldCFrameRainbow;
										sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
									until _25msShared.AutoRainbowHaki == false or L_350_forvar1.Humanoid.Health <= 0 or not L_350_forvar1.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
								end
							end
						else
							TP(CFrame.new(5312.3598632813, 20.141201019287, - 10.158538818359))
						end
					else
						TP(CFrame.new(- 11892.0703125, 930.57672119141, - 8760.1591796875))
						if (Vector3.new(- 11892.0703125, 930.57672119141, - 8760.1591796875) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 30 then
							wait(1.5)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("HornedMan", "Bet")
						end
					end
				end
			end
		end)
	end)
	spawn(function()
		while wait() do
			if _25msShared.AutoBuddySword then
				pcall(function()
					if game:GetService("Workspace").Enemies:FindFirstChild("Cake Queen") then
						for L_351_forvar0, L_352_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if L_352_forvar1.Name == "Cake Queen" then
								if L_352_forvar1:FindFirstChild("Humanoid") and L_352_forvar1:FindFirstChild("HumanoidRootPart") and L_352_forvar1.Humanoid.Health > 0 then
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										TP(L_352_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										L_352_forvar1.HumanoidRootPart.CanCollide = false;
										L_352_forvar1.Humanoid.WalkSpeed = 0;
										L_352_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
									until not _25msShared.AutoBuddySword or not L_352_forvar1.Parent or L_352_forvar1.Humanoid.Health <= 0
								end
							end
						end
					else
						if game:GetService("ReplicatedStorage"):FindFirstChild("Cake Queen") then
							TP(game:GetService("ReplicatedStorage"):FindFirstChild("Cake Queen").HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
						else
							if _25msShared.AutoBuddySwordHop then
								Hop()
							end
						end
					end
				end)
			end
		end
	end)
	spawn(function()
		while wait() do
			if _25msShared.AutoFarmBossHallow then
				pcall(function()
					if game:GetService("Workspace").Enemies:FindFirstChild("Soul Reaper") then
						for L_353_forvar0, L_354_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if string.find(L_354_forvar1.Name, "Soul Reaper") then
								repeat
									wait()
									EquipWeapon(_25msShared.SelectWeapon)
									L_354_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
									TP(L_354_forvar1.HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
									L_354_forvar1.HumanoidRootPart.Transparency = 1;
									sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
								until L_354_forvar1.Humanoid.Health <= 0 or _25msShared.AutoFarmBossHallow == false
							end
						end
					elseif game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hallow Essence") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Hallow Essence") then
						repeat
							TP(CFrame.new(- 8932.322265625, 146.83154296875, 6062.55078125))
							wait()
						until (CFrame.new(- 8932.322265625, 146.83154296875, 6062.55078125).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 8;
						wait(1)
						EquipWeapon("Hallow Essence")
					else
						if game:GetService("ReplicatedStorage"):FindFirstChild("Soul Reaper") then
							TP(game:GetService("ReplicatedStorage"):FindFirstChild("Soul Reaper").HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
						else
							if _25msShared.AutoFarmBossHallowHop then
								Hop()
							end
						end
					end
				end)
			end
		end
	end)
	spawn(function()
		pcall(function()
			while wait() do
				if _25msShared.AutoDarkDagger then
					if game:GetService("Workspace").Enemies:FindFirstChild("rip_indra True Form") or game:GetService("Workspace").Enemies:FindFirstChild("rip_indra") then
						for L_355_forvar0, L_356_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if L_356_forvar1.Name == ("rip_indra True Form" or L_356_forvar1.Name == "rip_indra") and L_356_forvar1.Humanoid.Health > 0 and L_356_forvar1:IsA("Model") and L_356_forvar1:FindFirstChild("Humanoid") and L_356_forvar1:FindFirstChild("HumanoidRootPart") then
								repeat
									wait()
									pcall(function()
										EquipWeapon(_25msShared.SelectWeapon)
										L_356_forvar1.HumanoidRootPart.CanCollide = false;
										L_356_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										TP(L_356_forvar1.HumanoidRootPart.CFrame * MethodFarm)
									end)
								until _25msShared.AutoDarkDagger == false or L_356_forvar1.Humanoid.Health <= 0
							end
						end
					else
						TP(CFrame.new(- 5344.822265625, 423.98541259766, - 2725.0930175781))
					end
				end
			end
		end)
	end)
end;
L_35_.QuestItem:Toggle("Auto Cavander", _25msShared.AutoCavander, function(L_357_arg0)
	_25msShared.AutoCavander = L_357_arg0;
	StopTween(_25msShared.AutoCavander)
end)
L_35_.QuestItem:Toggle("Auto Twin Hooks", _25msShared.AutoTwinHooks, function(L_358_arg0)
	_25msShared.AutoTwinHooks = L_358_arg0;
	StopTween(_25msShared.AutoTwinHooks)
end)
L_35_.QuestItem:Toggle("Auto Soul Reaper", _25msShared.AutoFarmBossHallow, function(L_359_arg0)
	_25msShared.AutoFarmBossHallow = L_359_arg0;
	StopTween(_25msShared.AutoFarmBossHallow)
end)
L_35_.QuestItem:Toggle("Auto Buddy Sword", _25msShared.AutoBuddySword, function(L_360_arg0)
	_25msShared.AutoBuddySword = L_360_arg0;
	StopTween(_25msShared.AutoBuddySword)
end)
L_35_.QuestItem:Toggle("Auto Kill Rip Boss", _25msShared.AutoDarkDagger, function(L_361_arg0)
	_25msShared.AutoDarkDagger = L_361_arg0;
	StopTween(_25msShared.AutoDarkDagger)
end)
L_35_.QuestItem:Toggle("Auto Yama", _25msShared.AutoYama, function(L_362_arg0)
	_25msShared.AutoYama = L_362_arg0;
	StopTween(_25msShared.AutoYama)
end)
L_35_.QuestItem:Toggle("Auto Tushita", _25msShared.AutoTushita, function(L_363_arg0)
	_25msShared.AutoTushita = L_363_arg0;
	StopTween(_25msShared.AutoTushita)
end)
L_35_.QuestItem:Toggle("Auto Holy Torch", _25msShared.AutoHolyTorch, function(L_364_arg0)
	_25msShared.AutoHolyTorch = L_364_arg0;
	StopTween(_25msShared.AutoHolyTorch)
end)
L_35_.QuestItem:Toggle("Auto Musketeer Hat", _25msShared.AutoMusketeerHat, function(L_365_arg0)
	_25msShared.AutoMusketeerHat = L_365_arg0;
	StopTween(_25msShared.AutoMusketeerHat)
end)
L_35_.QuestItem:Toggle("Auto Rainbow Haki", _25msShared.AutoRainbowHaki, function(L_366_arg0)
	_25msShared.AutoRainbowHaki = L_366_arg0;
	StopTween(_25msShared.AutoRainbowHaki)
end)
L_35_.QuestItem:Toggle("Auto Observation Haki V2", _25msShared.AutoObservationv2, function(L_367_arg0)
	_25msShared.AutoObservationHakiV2 = L_367_arg0;
	StopTween(_25msShared.AutoObservationHakiV2)
end)
L_35_.QuestItem:Label("Quest & Item | Sea 2")
if L_24_ then
	spawn(function()
		while wait() do
			if _25msShared.AutoThirdSea then
				pcall(function()
					if game:GetService("Players").LocalPlayer.Data.Level.Value >= 1500 and L_24_ then
						_25msShared.AutoFarmLevel = false;
						if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ZQuestProgress", "Check") == 0 then
							TP(CFrame.new(- 1926.3221435547, 12.819851875305, 1738.3092041016))
							if (CFrame.new(- 1926.3221435547, 12.819851875305, 1738.3092041016).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10 then
								wait(1.5)
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ZQuestProgress", "Begin")
							end;
							wait(1.8)
							if game:GetService("Workspace").Enemies:FindFirstChild("rip_indra") then
								for L_368_forvar0, L_369_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if L_369_forvar1.Name == "rip_indra" then
										OldCFrameThird = L_369_forvar1.HumanoidRootPart.CFrame;
										repeat
											wait()
											EquipWeapon(_25msShared.SelectWeapon)
											TP(L_369_forvar1.HumanoidRootPart.CFrame * MethodFarm)
											L_369_forvar1.HumanoidRootPart.CFrame = OldCFrameThird;
											L_369_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
											L_369_forvar1.HumanoidRootPart.CanCollide = false;
											L_369_forvar1.Humanoid.WalkSpeed = 0;
											game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
											sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
										until _25msShared.AutoThirdSea == false or L_369_forvar1.Humanoid.Health <= 0 or not L_369_forvar1.Parent
									end
								end
							elseif not game:GetService("Workspace").Enemies:FindFirstChild("rip_indra") and (CFrame.new(- 26880.93359375, 22.848554611206, 473.18951416016).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1000 then
								TP(CFrame.new(- 26880.93359375, 22.848554611206, 473.18951416016))
							end
						end
					end
				end)
			end
		end
	end)
	spawn(function()
		pcall(function()
			while wait() do
				if _25msShared.AutoSwan then
					if game:GetService("Workspace").Enemies:FindFirstChild("Don Swan") then
						for L_370_forvar0, L_371_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if L_371_forvar1.Name == "Don Swan" and L_371_forvar1.Humanoid.Health > 0 and L_371_forvar1:IsA("Model") and L_371_forvar1:FindFirstChild("Humanoid") and L_371_forvar1:FindFirstChild("HumanoidRootPart") then
								repeat
									wait()
									pcall(function()
										EquipWeapon(_25msShared.SelectWeapon)
										L_371_forvar1.HumanoidRootPart.CanCollide = false;
										L_371_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										TP(L_371_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
									end)
								until _25msShared.AutoSwan == false or L_371_forvar1.Humanoid.Health <= 0
							end
						end
					else
						repeat
							wait()
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(2284.912109375, 15.537666320801, 905.48291015625))
						until (CFrame.new(2284.912109375, 15.537666320801, 905.48291015625).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4 or _25msShared.AutoSwan == false
					end
				end
			end
		end)
	end)
	spawn(function()
		pcall(function()
			while wait() do
				if _25msShared.AutoRengoku then
					if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hidden Key") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Hidden Key") then
						EquipWeapon("Hidden Key")
						TP(CFrame.new(6571.1201171875, 299.23028564453, - 6967.841796875))
					elseif game:GetService("Workspace").Enemies:FindFirstChild("Snow Lurker") or game:GetService("Workspace").Enemies:FindFirstChild("Beautiful Pirate") then
						for L_372_forvar0, L_373_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if (L_373_forvar1.Name == "Snow Lurker" or L_373_forvar1.Name == "Arctic Warrior") and L_373_forvar1.Humanoid.Health > 0 then
								repeat
									wait()
									EquipWeapon(_25msShared.SelectWeapon)
									L_373_forvar1.HumanoidRootPart.CanCollide = false;
									L_373_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
									FarmPos = L_373_forvar1.HumanoidRootPart.CFrame;
									MonFarm = L_373_forvar1.Name;
									StartMagnet = true;
									TP(L_373_forvar1.HumanoidRootPart.CFrame * MethodFarm)
								until game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hidden Key") or _25msShared.AutoRengoku == false or not L_373_forvar1.Parent or L_373_forvar1.Humanoid.Health <= 0;
								StartMagnet = false
							end
						end
					else
						StartMagnet = false;
						TP(CFrame.new(5439.716796875, 84.420944213867, - 6715.1635742188))
					end
				end
			end
		end)
	end)
	spawn(function()
		pcall(function()
			while wait() do
				if _25msShared.AutoRaceV2 then
					if not game:GetService("Players").LocalPlayer.Data.Race:FindFirstChild("Evolved") then
						if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist", "1") == 0 then
							TP(CFrame.new(1023.530517578125, 73.06287384033203, 1269.852294921875))
							if (Vector3.new(1023.530517578125, 73.06287384033203, 1269.852294921875) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4 then
								wait(1.3)
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist", "2")
							end
						elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist", "1") == 1 then
							pcall(function()
								if not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 1") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 1") then
									TP(game:GetService("Workspace").Flower1.CFrame)
								elseif not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 2") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 2") then
									TP(game:GetService("Workspace").Flower2.CFrame)
								elseif not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 3") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 3") then
									if game:GetService("Workspace").Enemies:FindFirstChild("Swan Pirate") then
										for L_374_forvar0, L_375_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
											if L_375_forvar1.Name == "Swan Pirate" then
												repeat
													wait()
													EquipWeapon(_25msShared.SelectWeapon)
													TP(L_375_forvar1.HumanoidRootPart.CFrame * MethodFarm)
													L_375_forvar1.HumanoidRootPart.CanCollide = false;
													L_375_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
													FarmPos = L_375_forvar1.HumanoidRootPart.CFrame;
													MonFarm = L_375_forvar1.Name;
													StartMagnet = true
												until game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 3") or not L_375_forvar1.Parent or L_375_forvar1.Humanoid.Health <= 0 or _25msShared.AutoRaceV2 == false;
												StartMagnet = false
											end
										end
									else
										TP(CFrame.new(1193.3360595703125, 72.99276733398438, 1199.96630859375))
										StartMagnet = false
									end
								end
							end)
						elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist", "1") == 2 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist", "3")
						end
					end
				end
			end
		end)
	end)
	spawn(function()
		pcall(function()
			while wait() do
				if _25msShared.AutoBartilo then
					if game:GetService("Players").LocalPlayer.Data.Level.Value >= 800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress", "Bartilo") == 0 then
						if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Swan Pirates") and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "50") and game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
							if game:GetService("Workspace").Enemies:FindFirstChild("Swan Pirate") then
								Mon = "Swan Pirate"
								for L_376_forvar0, L_377_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if L_377_forvar1.Name == NameMon then
										pcall(function()
											repeat
												wait()
												sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
												EquipWeapon(_25msShared.SelectWeapon)
												L_377_forvar1.HumanoidRootPart.Transparency = 1;
												L_377_forvar1.HumanoidRootPart.CanCollide = false;
												L_377_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
												TP(L_377_forvar1.HumanoidRootPart.CFrame * MethodFarm)
												FarmPos = L_377_forvar1.HumanoidRootPart.CFrame;
												MonFarm = L_377_forvar1.Name;
												StartMagnet = true
											until not L_377_forvar1.Parent or L_377_forvar1.Humanoid.Health <= 0 or _25msShared.AutoBartilo == false or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false;
											StartMagnet = false
										end)
									end
								end
							else
								repeat
									TP(CFrame.new(932.624451, 156.106079, 1180.27466, - 0.973085582, 4.55137119e-08, - 0.230443969, 2.67024713e-08, 1, 8.47491108e-08, 0.230443969, 7.63147128e-08, - 0.973085582))
									wait()
								until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(932.624451, 156.106079, 1180.27466, - 0.973085582, 4.55137119e-08, - 0.230443969, 2.67024713e-08, 1, 8.47491108e-08, 0.230443969, 7.63147128e-08, - 0.973085582)).Magnitude <= 10
							end
						else
							repeat
								TP(CFrame.new(- 456.28952, 73.0200958, 299.895966))
								wait()
							until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 456.28952, 73.0200958, 299.895966)).Magnitude <= 10;
							wait(1.1)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", "BartiloQuest", 1)
						end
					elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress", "Bartilo") == 1 then
						if game:GetService("Workspace").Enemies:FindFirstChild("Jeremy") then
							Ms = "Jeremy"
							for L_378_forvar0, L_379_forvar1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if L_379_forvar1.Name == Ms then
									OldCFrameBartlio = L_379_forvar1.HumanoidRootPart.CFrame;
									repeat
										wait()
										sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
										EquipWeapon(_25msShared.SelectWeapon)
										L_379_forvar1.HumanoidRootPart.Transparency = 1;
										L_379_forvar1.HumanoidRootPart.CanCollide = false;
										L_379_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										L_379_forvar1.HumanoidRootPart.CFrame = OldCFrameBartlio;
										TP(L_379_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
									until not L_379_forvar1.Parent or L_379_forvar1.Humanoid.Health <= 0 or _25msShared.AutoBartilo == false
								end
							end
						elseif game:GetService("ReplicatedStorage"):FindFirstChild("Jeremy") then
							repeat
								TP(CFrame.new(- 456.28952, 73.0200958, 299.895966))
								wait()
							until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 456.28952, 73.0200958, 299.895966)).Magnitude <= 10;
							wait(1.1)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress", "Bartilo")
							wait(1)
							repeat
								TP(CFrame.new(2099.88159, 448.931, 648.997375))
								wait()
							until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(2099.88159, 448.931, 648.997375)).Magnitude <= 10;
							wait(2)
						else
							repeat
								TP(CFrame.new(2099.88159, 448.931, 648.997375))
								wait()
							until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(2099.88159, 448.931, 648.997375)).Magnitude <= 10
						end
					elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress", "Bartilo") == 2 then
						repeat
							TP(CFrame.new(- 1850.49329, 13.1789551, 1750.89685))
							wait()
						until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 1850.49329, 13.1789551, 1750.89685)).Magnitude <= 10;
						wait(1)
						repeat
							TP(CFrame.new(- 1858.87305, 19.3777466, 1712.01807))
							wait()
						until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 1858.87305, 19.3777466, 1712.01807)).Magnitude <= 10;
						wait(1)
						repeat
							TP(CFrame.new(- 1803.94324, 16.5789185, 1750.89685))
							wait()
						until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 1803.94324, 16.5789185, 1750.89685)).Magnitude <= 10;
						wait(1)
						repeat
							TP(CFrame.new(- 1858.55835, 16.8604317, 1724.79541))
							wait()
						until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 1858.55835, 16.8604317, 1724.79541)).Magnitude <= 10;
						wait(1)
						repeat
							TP(CFrame.new(- 1869.54224, 15.987854, 1681.00659))
							wait()
						until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 1869.54224, 15.987854, 1681.00659)).Magnitude <= 10;
						wait(1)
						repeat
							TP(CFrame.new(- 1800.0979, 16.4978027, 1684.52368))
							wait()
						until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 1800.0979, 16.4978027, 1684.52368)).Magnitude <= 10;
						wait(1)
						repeat
							TP(CFrame.new(- 1819.26343, 14.795166, 1717.90625))
							wait()
						until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 1819.26343, 14.795166, 1717.90625)).Magnitude <= 10;
						wait(1)
						repeat
							TP(CFrame.new(- 1813.51843, 14.8604736, 1724.79541))
							wait()
						until not _25msShared.AutoBartilo or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(- 1813.51843, 14.8604736, 1724.79541)).Magnitude <= 10
					end
				end
			end
		end)
	end)
end;
L_35_.QuestItem:Toggle("Auto Third Sea", _25msShared.AutoThirdSea, function(L_380_arg0)
	_25msShared.AutoThirdSea = L_380_arg0;
	StopTween(_25msShared.AutoThirdSea)
end)
L_35_.QuestItem:Toggle("Auto Swan Glasses", _25msShared.AutoSwan, function(L_381_arg0)
	_25msShared.AutoSwan = L_381_arg0;
	StopTween(_25msShared.AutoSwan)
end)
L_35_.QuestItem:Toggle("Auto Rengoku", _25msShared.AutoRengoku, function(L_382_arg0)
	_25msShared.AutoRengoku = L_382_arg0;
	StopTween(_25msShared.AutoRengoku)
end)
L_35_.QuestItem:Toggle("Auto Farm Ectoplasm", _25msShared.AutoEctoplasm, function(L_383_arg0)
	_25msShared.AutoEctoplasm = L_383_arg0;
	StopTween(_25msShared.AutoEctoplasm)
end)
L_35_.QuestItem:Toggle("Auto Race V2", _25msShared.AutoRaceV2, function(L_384_arg0)
	_25msShared.AutoRaceV2 = L_384_arg0;
	StopTween(_25msShared.AutoRaceV2)
end)
L_35_.QuestItem:Toggle("Auto Bartlio Quest", _25msShared.AutoBartilo, function(L_385_arg0)
	_25msShared.AutoBartilo = L_385_arg0
end)
L_35_.PVP:Label("Updating...")
local L_48_ = {}
for L_386_forvar0, L_387_forvar1 in pairs(game:GetService("Players"):GetChildren()) do
	table.insert(L_48_, L_387_forvar1.Name)
end;
local L_49_ = L_35_.PVP:Dropdown("Select Players", L_48_, "", function(L_388_arg0)
	_25msShared.SelectPly = L_388_arg0
end)
L_35_.PVP:Button("Refresh Player", function()
	L_48_ = {}
	L_49_:Set()
	for L_389_forvar0, L_390_forvar1 in pairs(game:GetService("Players"):GetChildren()) do
		L_49_:Add(L_390_forvar1.Name)
	end
end)
L_35_.PVP:Toggle("Spectate Player", false, function(L_391_arg0)
	SpectatePlys = L_391_arg0;
	local L_392_ = game:GetService("Players").LocalPlayer.Character.Humanoid;
	local L_393_ = game:GetService("Players"):FindFirstChild(_25msShared.SelectPly)
	repeat
		wait()
		game:GetService("Workspace").Camera.CameraSubject = game:GetService("Players"):FindFirstChild(_25msShared.SelectPly).Character.Humanoid
	until SpectatePlys == false;
	game:GetService("Workspace").Camera.CameraSubject = game:GetService("Players").LocalPlayer.Character.Humanoid
end)
L_35_.PVP:Toggle("Teleport", false, function(L_394_arg0)
	_25msShared.TeleportPly = L_394_arg0;
	pcall(function()
		if _25msShared.TeleportPly then
			repeat
				TP(game:GetService("Players")[_25msShared.SelectPly].Character.HumanoidRootPart.CFrame)
				wait()
			until _25msShared.TeleportPly == false
		end;
		StopTween(_25msShared.TeleportPly)
	end)
end)
L_35_.PVP:Label("Another Gud")
L_35_.PVP:Slider("Aimbot Distance", 1, 400, 250, function(L_395_arg0)
	_25msShared.AimbotDistance = L_395_arg0
end)
L_35_.PVP:Toggle("Aimbot Camera", _25msShared.AimbotCamera, function(L_396_arg0)
	_25msShared.AimbotCamera = L_396_arg0
end)
spawn(function()
	while task.wait() do
		if _25msShared.AimbotCamera then
			local L_397_ = workspace.CurrentCamera;
			for L_398_forvar0, L_399_forvar1 in pairs(game:GetService("Workspace").Characters:GetChildren()) do
				if L_399_forvar1.Name ~= game.Players.LocalPlayer.Name and (L_399_forvar1.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= _25msShared.AimbotDistance then
					local L_400_ = CFrame.new(L_397_.CFrame.Position, L_399_forvar1.HumanoidRootPart.Position)
					L_397_.CFrame = CFrame.new(L_397_.CFrame.Position) * L_400_
				end
			end
		end
	end
end)
L_35_.Teleport:Label("All World")
L_35_.Teleport:Button("Sea 1", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelMain")
end)
L_35_.Teleport:Button("Second Sea", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
end)
L_35_.Teleport:Button("Third Sea", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
end)
L_35_.Teleport:Label("Island")
local L_50_;
if L_23_ then
	L_50_ = {
		"WindMill",
		"Marine",
		"Middle Town",
		"Jungle",
		"Pirate Village",
		"Desert",
		"Snow Island",
		"MarineFord",
		"Colosseum",
		"Sky Island 1",
		"Sky Island 2",
		"Sky Island 3",
		"Prison",
		"Magma Village",
		"Under Water Island",
		"Fountain City",
		"Shank Room",
		"Mob Island"
	}
elseif L_24_ then
	L_50_ = {
		"The Cafe",
		"Frist Spot",
		"Dark Area",
		"Flamingo Mansion",
		"Flamingo Room",
		"Green Zone",
		"Factory",
		"Colossuim",
		"Zombie Island",
		"Two Snow Mountain",
		"Hot & Cold",
		"Punk Hazard",
		"Cursed Ship",
		"Ice Castle",
		"Forgotten Island",
		"Ussop Island",
		"Mini Sky Island"
	}
elseif L_25_ then
	L_50_ = {
		"Mansion",
		"Port Town",
		"Great Tree",
		"Castle On The Sea",
		"MiniSky",
		"Hydra Island",
		"Floating Turtle",
		"Haunted Castle",
		"Ice Cream Island",
		"Peanut Island",
		"Cake Island",
		"Room Enma/Yama & Secret Temple",
		"Room Tushita",
		"Tiki Outpost",
		"Dragon Gojo"
	}
end;
L_35_.Teleport:Dropdown("Select Island", L_50_, "", function(L_401_arg0)
	_25msShared.SelectIsland = L_401_arg0
end)
L_35_.Teleport:Toggle("Teleport Island Select", false, function(L_402_arg0)
	_25msShared.TeleportIsland = L_402_arg0;
	StopTween(_25msShared.TeleportIsland)
end)
spawn(function()
	while wait() do
		if _25msShared.TeleportIsland then
			repeat
				wait()
				if _25msShared.SelectIsland == "WindMill" then
					TP(CFrame.new(979.79895019531, 16.516613006592, 1429.0466308594))
				elseif _25msShared.SelectIsland == "Marine" then
					TP(CFrame.new(- 2566.4296875, 6.8556680679321, 2045.2561035156))
				elseif _25msShared.SelectIsland == "Middle Town" then
					TP(CFrame.new(- 690.33081054688, 15.09425163269, 1582.2380371094))
				elseif _25msShared.SelectIsland == "Jungle" then
					TP(CFrame.new(- 1612.7957763672, 36.852081298828, 149.12843322754))
				elseif _25msShared.SelectIsland == "Pirate Village" then
					TP(CFrame.new(- 1181.3093261719, 4.7514905929565, 3803.5456542969))
				elseif _25msShared.SelectIsland == "Desert" then
					TP(CFrame.new(944.15789794922, 20.919729232788, 4373.3002929688))
				elseif _25msShared.SelectIsland == "Snow Island" then
					TP(CFrame.new(1347.8067626953, 104.66806030273, - 1319.7370605469))
				elseif _25msShared.SelectIsland == "MarineFord" then
					TP(CFrame.new(- 4914.8212890625, 50.963626861572, 4281.0278320313))
				elseif _25msShared.SelectIsland == "Colosseum" then
					TP(CFrame.new(- 1427.6203613281, 7.2881078720093, - 2792.7722167969))
				elseif _25msShared.SelectIsland == "Sky Island 1" then
					TP(CFrame.new(- 4869.1025390625, 733.46051025391, - 2667.0180664063))
				elseif _25msShared.SelectIsland == "Sky Island 2" then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(- 4607.82275, 872.54248, - 1667.55688))
				elseif _25msShared.SelectIsland == "Sky Island 3" then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(- 7894.6176757813, 5547.1416015625, - 380.29119873047))
				elseif _25msShared.SelectIsland == "Prison" then
					TP(CFrame.new(4875.330078125, 5.6519818305969, 734.85021972656))
				elseif _25msShared.SelectIsland == "Magma Village" then
					TP(CFrame.new(- 5247.7163085938, 12.883934020996, 8504.96875))
				elseif _25msShared.SelectIsland == "Under Water Island" then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
				elseif _25msShared.SelectIsland == "Fountain City" then
					TP(CFrame.new(5127.1284179688, 59.501365661621, 4105.4458007813))
				elseif _25msShared.SelectIsland == "Shank Room" then
					TP(CFrame.new(- 1442.16553, 29.8788261, - 28.3547478))
				elseif _25msShared.SelectIsland == "Mob Island" then
					TP(CFrame.new(- 2850.20068, 7.39224768, 5354.99268))
				elseif _25msShared.SelectIsland == "The Cafe" then
					TP(CFrame.new(- 380.47927856445, 77.220390319824, 255.82550048828))
				elseif _25msShared.SelectIsland == "Frist Spot" then
					TP(CFrame.new(- 11.311455726624, 29.276733398438, 2771.5224609375))
				elseif _25msShared.SelectIsland == "Dark Area" then
					TP(CFrame.new(3780.0302734375, 22.652164459229, - 3498.5859375))
				elseif _25msShared.SelectIsland == "Flamingo Mansion" then
					TP(CFrame.new(- 483.73370361328, 332.0383605957, 595.32708740234))
				elseif _25msShared.SelectIsland == "Flamingo Room" then
					TP(CFrame.new(2284.4140625, 15.152037620544, 875.72534179688))
				elseif _25msShared.SelectIsland == "Green Zone" then
					TP(CFrame.new(- 2448.5300292969, 73.016105651855, - 3210.6306152344))
				elseif _25msShared.SelectIsland == "Factory" then
					TP(CFrame.new(424.12698364258, 211.16171264648, - 427.54049682617))
				elseif _25msShared.SelectIsland == "Colossuim" then
					TP(CFrame.new(- 1503.6224365234, 219.7956237793, 1369.3101806641))
				elseif _25msShared.SelectIsland == "Zombie Island" then
					TP(CFrame.new(- 5622.033203125, 492.19604492188, - 781.78552246094))
				elseif _25msShared.SelectIsland == "Two Snow Mountain" then
					TP(CFrame.new(753.14288330078, 408.23559570313, - 5274.6147460938))
				elseif _25msShared.SelectIsland == "Hot & Cold" then
					TP(CFrame.new(- 6014.5205078125, 15.984769821166992, - 5102.9755859375))
				elseif _25msShared.SelectIsland == "Punk Hazard" then
					TP(CFrame.new(- 6127.654296875, 15.951762199402, - 5040.2861328125))
				elseif _25msShared.SelectIsland == "Cursed Ship" then
					TP(CFrame.new(923.40197753906, 125.05712890625, 32885.875))
				elseif _25msShared.SelectIsland == "Ice Castle" then
					TP(CFrame.new(6148.4116210938, 294.38687133789, - 6741.1166992188))
				elseif _25msShared.SelectIsland == "Forgotten Island" then
					TP(CFrame.new(- 3032.7641601563, 317.89672851563, - 10075.373046875))
				elseif _25msShared.SelectIsland == "Ussop Island" then
					TP(CFrame.new(4816.8618164063, 8.4599885940552, 2863.8195800781))
				elseif _25msShared.SelectIsland == "Mini Sky Island" then
					TP(CFrame.new(- 288.74060058594, 49326.31640625, - 35248.59375))
				elseif _25msShared.SelectIsland == "Great Tree" then
					TP(CFrame.new(2953.328369140625, 2282.010009765625, - 7214.51611328125))
				elseif _25msShared.SelectIsland == "Castle On The Sea" then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(- 5080.81787109375, 314.5812072753906, - 3003.600830078125))
				elseif _25msShared.SelectIsland == "MiniSky" then
					TP(CFrame.new(- 260.65557861328, 49325.8046875, - 35253.5703125))
				elseif _25msShared.SelectIsland == "Port Town" then
					TP(CFrame.new(- 290.7376708984375, 6.729952812194824, 5343.5537109375))
				elseif _25msShared.SelectIsland == "Hydra Island" then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(5627.6005859375, 1082.473876953125, - 300.69598388671875))
				elseif _25msShared.SelectIsland == "Floating Turtle" then
					TP(CFrame.new(- 13274.528320313, 531.82073974609, - 7579.22265625))
				elseif _25msShared.SelectIsland == "Mansion" then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(- 12471.169921875, 374.94024658203, - 7551.677734375))
				elseif _25msShared.SelectIsland == "Haunted Castle" then
					TP(CFrame.new(- 9515.3720703125, 164.00624084473, 5786.0610351562))
				elseif _25msShared.SelectIsland == "Ice Cream Island" then
					TP(CFrame.new(- 902.56817626953, 79.93204498291, - 10988.84765625))
				elseif _25msShared.SelectIsland == "Peanut Island" then
					TP(CFrame.new(- 2062.7475585938, 50.473892211914, - 10232.568359375))
				elseif _25msShared.SelectIsland == "Cake Island" then
					TP(CFrame.new(- 1884.7747802734375, 19.327526092529297, - 11666.8974609375))
				elseif _25msShared.SelectIsland == "Room Enma/Yama & Secret Temple" then
					TP(CFrame.new(5227.9052734375, 8.119736671447754, 1100.832275390625))
				elseif _25msShared.SelectIsland == "Room Tushita" then
					TP(CFrame.new(5174.83447265625, 141.81944274902344, 911.4637451171875))
				elseif _25msShared.SelectIsland == "Tiki Outpost" then
					TP(CFrame.new(- 16899.6133, 9.31711292, 492.155396, 0.00204202533, - 0.00301179662, 0.999993384, - 0.0185630079, 0.999823034, 0.00304919085, - 0.999825597, - 0.01856911, 0.00198575854))
				elseif _25msShared.SelectIsland == "Dragon Gojo" then
					TP(CFrame.new(5785.18115234375, 1359.7843017578125, 908.6729736328125))
				end
			until not _25msShared.TeleportIsland
		end
	end
end)
L_35_.ESP:Label("ESP")
function isnil(L_403_arg0)
	return L_403_arg0 == nil
end;
local function L_51_func(L_404_arg0)
	return math.floor(tonumber(L_404_arg0) + 0.5)
end;
Number = math.random(1, 1000000)
function UpdatePlayerChams()
	for L_405_forvar0, L_406_forvar1 in pairs(game:GetService"Players":GetChildren()) do
		pcall(function()
			if not isnil(L_406_forvar1.Character) then
				if ESPPlayer then
					if not isnil(L_406_forvar1.Character.Head) and not L_406_forvar1.Character.Head:FindFirstChild("NameEsp" .. Number) then
						local L_407_ = Instance.new("BillboardGui", L_406_forvar1.Character.Head)
						L_407_.Name = "NameEsp" .. Number;
						L_407_.ExtentsOffset = Vector3.new(0, 1, 0)
						L_407_.Size = UDim2.new(1, 200, 1, 30)
						L_407_.Adornee = L_406_forvar1.Character.Head;
						L_407_.AlwaysOnTop = true;
						local L_408_ = Instance.new("TextLabel", L_407_)
						L_408_.Font = "Code"
						L_408_.FontSize = "Size18"
						L_408_.TextWrapped = true;
						L_408_.Text = L_406_forvar1.Name .. " \n" .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_406_forvar1.Character.Head.Position).Magnitude / 3) .. " M"
						L_408_.Size = UDim2.new(1, 0, 1, 0)
						L_408_.TextYAlignment = "Top"
						L_408_.BackgroundTransparency = 1;
						L_408_.TextStrokeTransparency = 0.5;
						if L_406_forvar1.Team == game.Players.LocalPlayer.Team then
							L_408_.TextColor3 = Color3.new(0, 255, 0)
						else
							L_408_.TextColor3 = Color3.new(255, 0, 0)
						end
					else
						L_406_forvar1.Character.Head["NameEsp" .. Number].TextLabel.Text = L_406_forvar1.Name .. " | " .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_406_forvar1.Character.Head.Position).Magnitude / 3) .. " M\nHealth : " .. L_51_func(L_406_forvar1.Character.Humanoid.Health * 100 / L_406_forvar1.Character.Humanoid.MaxHealth) .. "%"
					end
				else
					if L_406_forvar1.Character.Head:FindFirstChild("NameEsp" .. Number) then
						L_406_forvar1.Character.Head:FindFirstChild("NameEsp" .. Number):Destroy()
					end
				end
			end
		end)
	end
end;
function UpdateIslandESP()
	for L_409_forvar0, L_410_forvar1 in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
		pcall(function()
			if IslandESP then
				if L_410_forvar1.Name ~= "Sea" then
					if not L_410_forvar1:FindFirstChild("NameEsp") then
						local L_411_ = Instance.new("BillboardGui", L_410_forvar1)
						L_411_.Name = "NameEsp"
						L_411_.ExtentsOffset = Vector3.new(0, 1, 0)
						L_411_.Size = UDim2.new(1, 200, 1, 30)
						L_411_.Adornee = L_410_forvar1;
						L_411_.AlwaysOnTop = true;
						local L_412_ = Instance.new("TextLabel", L_411_)
						L_412_.Font = "GothamBold"
						L_412_.FontSize = "Size14"
						L_412_.TextWrapped = true;
						L_412_.Size = UDim2.new(1, 0, 1, 0)
						L_412_.TextYAlignment = "Top"
						L_412_.BackgroundTransparency = 1;
						L_412_.TextStrokeTransparency = 0.5;
						L_412_.TextColor3 = Color3.fromRGB(80, 245, 245)
					else
						L_410_forvar1["NameEsp"].TextLabel.Text = L_410_forvar1.Name .. "   \n" .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_410_forvar1.Position).Magnitude / 3) .. " M"
					end
				end
			else
				if L_410_forvar1:FindFirstChild("NameEsp") then
					L_410_forvar1:FindFirstChild("NameEsp"):Destroy()
				end
			end
		end)
	end
end;
function UpdateChestEsp()
	for L_413_forvar0, L_414_forvar1 in pairs(game:GetService("Workspace"):GetChildren()) do
		pcall(function()
			if string.find(L_414_forvar1.Name, "Chest") then
				if ChestESP then
					if string.find(L_414_forvar1.Name, "Chest") then
						if not L_414_forvar1:FindFirstChild("NameEsp" .. Number) then
							local L_415_ = Instance.new("BillboardGui", L_414_forvar1)
							L_415_.Name = "NameEsp" .. Number;
							L_415_.ExtentsOffset = Vector3.new(0, 1, 0)
							L_415_.Size = UDim2.new(1, 200, 1, 30)
							L_415_.Adornee = L_414_forvar1;
							L_415_.AlwaysOnTop = true;
							local L_416_ = Instance.new("TextLabel", L_415_)
							L_416_.Font = "GothamBold"
							L_416_.FontSize = "Size14"
							L_416_.TextWrapped = true;
							L_416_.Size = UDim2.new(1, 0, 1, 0)
							L_416_.TextYAlignment = "Top"
							L_416_.BackgroundTransparency = 1;
							L_416_.TextStrokeTransparency = 0.5;
							L_416_.TextColor3 = Color3.fromRGB(0, 255, 250)
							if L_414_forvar1.Name == "Chest1" then
								L_416_.Text = "Chest 1" .. " \n" .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_414_forvar1.Position).Magnitude / 3) .. " M"
							end;
							if L_414_forvar1.Name == "Chest2" then
								L_416_.Text = "Chest 2" .. " \n" .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_414_forvar1.Position).Magnitude / 3) .. " M"
							end;
							if L_414_forvar1.Name == "Chest3" then
								L_416_.Text = "Chest 3" .. " \n" .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_414_forvar1.Position).Magnitude / 3) .. " M"
							end
						else
							L_414_forvar1["NameEsp" .. Number].TextLabel.Text = L_414_forvar1.Name .. "   \n" .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_414_forvar1.Position).Magnitude / 3) .. " M"
						end
					end
				else
					if L_414_forvar1:FindFirstChild("NameEsp" .. Number) then
						L_414_forvar1:FindFirstChild("NameEsp" .. Number):Destroy()
					end
				end
			end
		end)
	end
end;
function UpdateBfEsp()
	for L_417_forvar0, L_418_forvar1 in pairs(game:GetService("Workspace"):GetChildren()) do
		pcall(function()
			if DevilFruitESP then
				if string.find(L_418_forvar1.Name, "Fruit") then
					if not L_418_forvar1.Handle:FindFirstChild("NameEsp" .. Number) then
						local L_419_ = Instance.new("BillboardGui", L_418_forvar1.Handle)
						L_419_.Name = "NameEsp" .. Number;
						L_419_.ExtentsOffset = Vector3.new(0, 1, 0)
						L_419_.Size = UDim2.new(1, 200, 1, 30)
						L_419_.Adornee = L_418_forvar1.Handle;
						L_419_.AlwaysOnTop = true;
						local L_420_ = Instance.new("TextLabel", L_419_)
						L_420_.Font = "GothamBold"
						L_420_.FontSize = "Size14"
						L_420_.TextWrapped = true;
						L_420_.Size = UDim2.new(1, 0, 1, 0)
						L_420_.TextYAlignment = "Top"
						L_420_.BackgroundTransparency = 1;
						L_420_.TextStrokeTransparency = 0.5;
						L_420_.TextColor3 = Color3.fromRGB(255, 0, 0)
						L_420_.Text = L_418_forvar1.Name .. " \n" .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_418_forvar1.Handle.Position).Magnitude / 3) .. " M"
					else
						L_418_forvar1.Handle["NameEsp" .. Number].TextLabel.Text = L_418_forvar1.Name .. "   \n" .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_418_forvar1.Handle.Position).Magnitude / 3) .. " M"
					end
				end
			else
				if L_418_forvar1.Handle:FindFirstChild("NameEsp" .. Number) then
					L_418_forvar1.Handle:FindFirstChild("NameEsp" .. Number):Destroy()
				end
			end
		end)
	end
end;
function UpdateFlowerEsp()
	for L_421_forvar0, L_422_forvar1 in pairs(game:GetService("Workspace"):GetChildren()) do
		pcall(function()
			if L_422_forvar1.Name == "Flower2" or L_422_forvar1.Name == "Flower1" then
				if FlowerESP then
					if not L_422_forvar1:FindFirstChild("NameEsp" .. Number) then
						local L_423_ = Instance.new("BillboardGui", L_422_forvar1)
						L_423_.Name = "NameEsp" .. Number;
						L_423_.ExtentsOffset = Vector3.new(0, 1, 0)
						L_423_.Size = UDim2.new(1, 200, 1, 30)
						L_423_.Adornee = L_422_forvar1;
						L_423_.AlwaysOnTop = true;
						local L_424_ = Instance.new("TextLabel", L_423_)
						L_424_.Font = "GothamBold"
						L_424_.FontSize = "Size14"
						L_424_.TextWrapped = true;
						L_424_.Size = UDim2.new(1, 0, 1, 0)
						L_424_.TextYAlignment = "Top"
						L_424_.BackgroundTransparency = 1;
						L_424_.TextStrokeTransparency = 0.5;
						L_424_.TextColor3 = Color3.fromRGB(255, 0, 0)
						if L_422_forvar1.Name == "Flower1" then
							L_424_.Text = "Blue Flower" .. " \n" .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_422_forvar1.Position).Magnitude / 3) .. " M"
							L_424_.TextColor3 = Color3.fromRGB(0, 0, 255)
						end;
						if L_422_forvar1.Name == "Flower2" then
							L_424_.Text = "Red Flower" .. " \n" .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_422_forvar1.Position).Magnitude / 3) .. " M"
							L_424_.TextColor3 = Color3.fromRGB(255, 0, 0)
						end
					else
						L_422_forvar1["NameEsp" .. Number].TextLabel.Text = L_422_forvar1.Name .. "   \n" .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_422_forvar1.Position).Magnitude / 3) .. " M"
					end
				else
					if L_422_forvar1:FindFirstChild("NameEsp" .. Number) then
						L_422_forvar1:FindFirstChild("NameEsp" .. Number):Destroy()
					end
				end
			end
		end)
	end
end;
L_35_.ESP:Toggle("ESP Player", false, function(L_425_arg0)
	ESPPlayer = L_425_arg0;
	UpdatePlayerChams()
end)
L_35_.ESP:Toggle("ESP Island", IslandESP, function(L_426_arg0)
	IslandESP = L_426_arg0;
	while IslandESP do
		wait()
		UpdateIslandESP()
	end
end)
L_35_.ESP:Toggle("ESP Fruit", false, function(L_427_arg0)
	DevilFruitESP = L_427_arg0;
	UpdateBfEsp()
end)
L_35_.ESP:Toggle("ESP 2 Flower < 2 >", false, function(L_428_arg0)
	FlowerESP = L_428_arg0
end)
spawn(function()
	while wait(2) do
		if FlowerESP then
			UpdateFlowerEsp()
		end;
		if DevilFruitESP then
			UpdateBfEsp()
		end;
		if ChestESP then
			UpdateChestEsp()
		end;
		if ESPPlayer then
			UpdatePlayerChams()
		end
	end
end)
L_35_.Raid:Label("Law Raid: Sea 2")
if L_24_ then
	L_35_.Raid:Toggle("Auto Law Raid", false, function(L_429_arg0)
		_25msShared.AutoLawRaid = L_429_arg0;
		StopTween(_25msShared.AutoLawRaid)
	end)
	spawn(function()
		while wait() do
			if _25msShared.AutoLawRaid then
				pcall(function()
					if game:GetService("ReplicatedStorage"):FindFirstChild("Order") or game:GetService("Workspace").Enemies:FindFirstChild("Order") then
						for L_430_forvar0, L_431_forvar1 in pairs(game.Workspace.Enemies:GetChildren()) do
							if _25msShared.AutoLaw and L_431_forvar1.Name == "Order" and L_431_forvar1:FindFirstChild("HumanoidRootPart") and L_431_forvar1:FindFirstChild("Humanoid") and L_431_forvar1.Humanoid.Health > 0 then
								repeat
									wait()
									EquipWeapon(_25msShared.SelectWeapon)
									L_431_forvar1.HumanoidRootPart.CanCollide = false;
									L_431_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
									TP(L_431_forvar1.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0))
								until not _25msShared.AutoLawRaid or L_431_forvar1.Humanoid.Health <= 0 or not L_431_forvar1.Parent
							end
						end
					end
				end)
			end
		end
	end)
	L_35_.Raid:Toggle("Auto Buy Microchip Law", false, function(L_432_arg0)
		_25msShared.MicrochipOrder = L_432_arg0
	end)
	spawn(function()
		while wait() do
			if _25msShared.MicrochipOrder then
				if not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Microchip") and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Microchip") then
					local L_433_ = {
						[1] = "BlackbeardReward",
						[2] = "Microchip",
						[3] = "2"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(L_433_))
				end
			end
		end
	end)
	L_35_.Raid:Toggle("Auto Start Raid Law", false, function(L_434_arg0)
		_25msShared.AutoStartRaidOrder = L_434_arg0
	end)
	spawn(function()
		while wait() do
			pcall(function()
				if _25msShared.AutoStartRaidOrder then
					if game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Timer.Visible == false then
						if not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Microchip") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Microchip") then
							if L_24_ then
								fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon.Button.Main.ClickDetector)
							end
						end
					end
				end
			end)
		end
	end)
	L_35_.Raid:Button("Buy Law Microchip", function()
		local L_435_ = {
			[1] = "BlackbeardReward",
			[2] = "Microchip",
			[3] = "2"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(L_435_))
	end)
	L_35_.Raid:Button("Start Law Raid", function()
		fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon.Button.Main.ClickDetector)
	end)
end;
L_35_.Raid:Line()
L_35_.Raid:Toggle("Auto Next Island", false, function(L_436_arg0)
	_25msShared.AutoNextIsland = L_436_arg0;
	StopTween(_25msShared.AutoNextIsland)
end)
function IsIslandRaid(L_437_arg0)
	if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island " .. L_437_arg0) then
		min = 4500;
		for L_438_forvar0, L_439_forvar1 in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
			if L_439_forvar1.Name == "Island " .. L_437_arg0 and (L_439_forvar1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < min then
				min = (L_439_forvar1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
			end
		end;
		for L_440_forvar0, L_441_forvar1 in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
			if L_441_forvar1.Name == "Island " .. L_437_arg0 and (L_441_forvar1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= min then
				return L_441_forvar1
			end
		end
	end
end;
function getNextIsland()
	local L_442_ = {
		5,
		4,
		3,
		2,
		1
	}
	for L_443_forvar0, L_444_forvar1 in pairs(L_442_) do
		if IsIslandRaid(L_444_forvar1) and (IsIslandRaid(L_444_forvar1).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4500 then
			return IsIslandRaid(L_444_forvar1)
		end
	end
end;
spawn(function()
	pcall(function()
		while wait() do
			if _25msShared.AutoNextIsland then
				if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") then
					for L_445_forvar0, L_446_forvar1 in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
						if L_446_forvar1.Name == "Island 5" and (L_446_forvar1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2300 then
							TP(getNextIsland().CFrame * CFrame.new(0, 110, 0))
						end
					end
				elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") then
					for L_447_forvar0, L_448_forvar1 in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
						if L_448_forvar1.Name == "Island 4" and (L_448_forvar1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2300 then
							TP(getNextIsland().CFrame * CFrame.new(0, 110, 0))
						end
					end
				elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") then
					for L_449_forvar0, L_450_forvar1 in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
						if L_450_forvar1.Name == "Island 3" and (L_450_forvar1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2300 then
							TP(getNextIsland().CFrame * CFrame.new(0, 110, 0))
						end
					end
				elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") then
					for L_451_forvar0, L_452_forvar1 in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
						if L_452_forvar1.Name == "Island 2" and (L_452_forvar1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2300 then
							TP(getNextIsland().CFrame * CFrame.new(0, 110, 0))
						end
					end
				elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
					for L_453_forvar0, L_454_forvar1 in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
						if L_454_forvar1.Name == "Island 1" and (L_454_forvar1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2300 then
							TP(getNextIsland().CFrame * CFrame.new(0, 110, 0))
						end
					end
				end
			end
		end
	end)
end)
L_35_.Raid:Toggle("Kill Aura", false, function(L_455_arg0)
	_25msShared.Killaura = L_455_arg0
end)
spawn(function()
	while wait() do
		if _25msShared.Killaura then
			for L_456_forvar0, L_457_forvar1 in pairs(game.Workspace.Enemies:GetDescendants()) do
				if L_457_forvar1:FindFirstChild("Humanoid") and L_457_forvar1:FindFirstChild("HumanoidRootPart") and L_457_forvar1.Humanoid.Health > 0 then
					pcall(function()
						repeat
							wait()
							L_457_forvar1.Humanoid.Health = 0;
							L_457_forvar1.HumanoidRootPart.CanCollide = false;
							L_457_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
							L_457_forvar1.HumanoidRootPart.Transparency = 1;
							sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
						until not _25msShared.Killaura or not L_457_forvar1.Parent or L_457_forvar1.Humanoid.Health <= 0
					end)
				end
			end
		end
	end
end)
L_35_.Raid:Toggle("Auto Awakener", _25msShared.Auto_Awakener, function(L_458_arg0)
	_25msShared.Auto_Awakener = L_458_arg0
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.Auto_Awakener then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Awakener", "Check")
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Awakener", "Awaken")
			end
		end)
	end
end)
L_35_.Raid:Line()
L_35_.Raid:Dropdown("Select Chips", {
	"Flame",
	"Ice",
	"Quake",
	"Light",
	"Dark",
	"Spider",
	"Rumble",
	"Magma",
	"Buddha",
	"Sand",
	"Phoenix",
	"Dough"
}, "Flame", function(L_459_arg0)
	_25msShared.SelectChip = L_459_arg0
end)
L_35_.Raid:Button("Buy Chip Raid Selected", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("RaidsNpc", "Select", _25msShared.SelectChip)
end)
L_35_.Raid:Toggle("Auto Buy Chip Raid Selected", _25msShared.AutoBuyChip, function(L_460_arg0)
	_25msShared.AutoBuyChip = L_460_arg0
end)
spawn(function()
	pcall(function()
		while task.wait(.1) do
			if _25msShared.AutoBuyChip then
				if not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Special Microchip") or not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Special Microchip") then
					if not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("RaidsNpc", "Select", _25msShared.SelectChip)
					end
				end
			end
		end
	end)
end)
L_35_.Raid:Button("Start Raid", function()
	if L_24_ then
		fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon2.Button.Main.ClickDetector)
	elseif L_25_ then
		fireclickdetector(game:GetService("Workspace").Map["Boat Castle"].RaidSummon2.Button.Main.ClickDetector)
	end
end)
L_35_.Raid:Toggle("Auto Start Raid", _25msShared.Auto_StartRaid, function(L_461_arg0)
	_25msShared.Auto_StartRaid = L_461_arg0
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.Auto_StartRaid then
				if game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Timer.Visible == false then
					if not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Special Microchip") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Special Microchip") then
						if L_24_ then
							fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon2.Button.Main.ClickDetector)
						elseif L_25_ then
							fireclickdetector(game:GetService("Workspace").Map["Boat Castle"].RaidSummon2.Button.Main.ClickDetector)
						end
					end
				end
			end
		end)
	end
end)
L_35_.Raid:Line()
L_35_.Raid:Button("Next Island", function()
	pcall(function()
		if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") then
			TP(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame * CFrame.new(0, 180, 0))
		elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") then
			TP(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame * CFrame.new(0, 180, 0))
		elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") then
			TP(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame * CFrame.new(0, 180, 0))
		elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") then
			TP(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame * CFrame.new(0, 180, 0))
		elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
			TP(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame * CFrame.new(0, 180, 0))
		end
	end)
end)
L_35_.Raid:Button("TP to Lab", function()
	pcall(function()
		if L_24_ then
			TP(CFrame.new(- 6438.73535, 250.645355, - 4501.50684))
		elseif L_25_ then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(- 5081.17333984375, 314.54852294921875, - 3005.243408203125))
		end
	end)
end)
L_35_.Raid:Button("Awakening Room", function()
	pcall(function()
		if L_24_ then
			TP(CFrame.new(266.227783, 1.39509034, 1857.00732))
		elseif L_25_ then
			TP(CFrame.new(- 11571.440429688, 49.172668457031, - 7574.7368164062))
		end
	end)
end)
L_35_.DevilFruit:Line()
L_35_.DevilFruit:Toggle("Auto Random Fruit", _25msShared.RandomFruit, function(L_462_arg0)
	_25msShared.RandomFruit = L_462_arg0
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.RandomFruit then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Cousin", "Buy")
			end
		end)
	end
end)
L_35_.DevilFruit:Button("Random Fruit", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Cousin", "Buy")
end)
L_35_.DevilFruit:Toggle("Auto Store Fruit", _25msShared.AutoStoreFruit, function(L_463_arg0)
	_25msShared.AutoStoreFruit = L_463_arg0
end)
L_35_.DevilFruit:Toggle("Auto Drop Fruit", false, function(L_464_arg0)
	Drop = L_464_arg0
end)
spawn(function()
	while wait() do
		if Drop then
			pcall(function()
				for L_465_forvar0, L_466_forvar1 in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
					if string.find(L_466_forvar1.Name, "Fruit") then
						EquipWeapon(L_466_forvar1.Name)
						SelectFruit = L_466_forvar1.Name;
						wait(.1)
						if game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible == true then
							game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible = false
						end;
						EquipWeapon(L_466_forvar1.Name)
						game:GetService("Players").LocalPlayer.Character:FindFirstChild(SelectFruit).EatRemote:InvokeServer("Drop")
					end
				end;
				for L_467_forvar0, L_468_forvar1 in pairs(game:GetService("Players").LocalPlayer.Character:GetChildren()) do
					if string.find(L_468_forvar1.Name, "Fruit") then
						EquipWeapon(L_468_forvar1.Name)
						SelectFruit = L_468_forvar1.Name;
						wait(.1)
						if game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible == true then
							game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible = false
						end;
						EquipWeapon(L_468_forvar1.Name)
						game:GetService("Players").LocalPlayer.Character:FindFirstChild(SelectFruit).EatRemote:InvokeServer("Drop")
					end
				end
			end)
		end
	end
end)
local L_52_ = L_35_.DevilFruit:Label("Fruit in Server: ?")
spawn(function()
	while wait() do
		local L_469_ = 0;
		local L_470_ = 0;
		for L_471_forvar0, L_472_forvar1 in pairs(game.Workspace:GetChildren()) do
			if L_472_forvar1.Name == "Blox Fruit Dealer" then
			else
				if string.find(L_472_forvar1.Name, "Fruit") and L_472_forvar1:IsA("Model") then
					L_470_ = L_470_ + 1
				end
			end
		end;
		L_52_:Set("Fruit in Server : " .. L_470_)
	end
end)
L_35_.DevilFruit:Toggle("Tween To Spawn Fruit", _25msShared.TweenToFruit, function(L_473_arg0)
	_25msShared.TweenToFruit = L_473_arg0;
	StopTween(_25msShared.TweenToFruit)
end)
spawn(function()
	while wait(.1) do
		if _25msShared.TweenToFruit then
			for L_474_forvar0, L_475_forvar1 in pairs(game.Workspace:GetChildren()) do
				if string.find(L_475_forvar1.Name, "Fruit") then
					TP(L_475_forvar1.Handle.CFrame)
				end
			end
		end
	end
end)
L_35_.Misc:Label("Server")
L_35_.Misc:Button("Rejoin Server", function()
	game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, game.JobId, game.Players.LocalPlayer)
end)
L_35_.Misc:Button("Hop Server", function()
	Hop()
end)
L_35_.Misc:Label("Job-ID")
local L_53_ = L_35_.Misc:Label("Your Job-ID")
L_53_:Set(game.JobId)
L_35_.Misc:Textbox("Put Job-ID Here", true, function(L_476_arg0)
	_25msShared.PutJobID = L_476_arg0
end)
L_35_.Misc:Button("Join Job-ID Server", function()
	game:GetService("TeleportService"):TeleportToPlaceInstance(game.placeId, _25msShared.PutJobID, game.Players.LocalPlayer)
end)
L_35_.Misc:Toggle("Auto Join Job-ID Server", false, function(L_477_arg0)
	_25msShared.AutoJobID = L_477_arg0
end)
spawn(function()
	while wait(1) do
		if _25msShared.AutoJobID then
			game:GetService("TeleportService"):TeleportToPlaceInstance(game.placeId, _25msShared.PutJobID, game.Players.LocalPlayer)
		end
	end
end)
L_35_.Misc:Button("Copy Your Job-Id Server", function()
	setclipboard(tostring(game.JobId))
end)
L_35_.Misc:Textbox("CF", true, function(L_478_arg0)
	_25msShared.AnchoredBack = L_478_arg0
end)
L_35_.Misc:Button("Copy Your CF (nvm)", function()
	setclipboard(tostring(game.Players.LocalPlayer.Character.HumanoidRootPart.Position))
end)
L_35_.Misc:Button("Start", function()
	TP(CFrame.new(Vector3.new(_25msShared.AnchoredBack)))
end)
L_35_.Misc:Button("Stop", function()
	StopTween()
end)
L_35_.Misc:Label("Other")
L_35_.Misc:Toggle("RTX Graphics", false, function(L_479_arg0)
	if L_479_arg0 then
		_25msShared.mode = "Autumn"
		local L_480_ = game.Lighting;
		L_480_.Ambient = Color3.fromRGB(33, 33, 33)
		L_480_.Brightness = 0.3;
		L_480_.ColorShift_Bottom = Color3.fromRGB(0, 0, 0)
		L_480_.ColorShift_Top = Color3.fromRGB(255, 247, 237)
		L_480_.EnvironmentDiffuseScale = 0.105;
		L_480_.EnvironmentSpecularScale = 0.522;
		L_480_.GlobalShadows = true;
		L_480_.OutdoorAmbient = Color3.fromRGB(51, 54, 67)
		L_480_.ShadowSoftness = 0.04;
		L_480_.GeographicLatitude = - 15.525;
		L_480_.ExposureCompensation = 0.75;
		local L_481_ = Instance.new("BloomEffect", L_480_)
		L_481_.Name = "BloomEffect_Graphic"
		L_481_.Enabled = true;
		L_481_.Intensity = 0.04;
		L_481_.Size = 1900;
		L_481_.Threshold = 0.915;
		local L_482_ = Instance.new("ColorCorrectionEffect", L_480_)
		L_482_.Name = "ColorCorrectionEffect1_Graphic"
		L_482_.Brightness = 0.176;
		L_482_.Contrast = 0.39;
		L_482_.Enabled = true;
		L_482_.Saturation = 0.2;
		L_482_.TintColor = Color3.fromRGB(217, 145, 57)
		if _25msShared.mode == "Summer" then
			L_482_.TintColor = Color3.fromRGB(255, 220, 148)
		elseif _25msShared.mode == "Autumn" then
			L_482_.TintColor = Color3.fromRGB(242, 193, 79)
		end;
		local L_483_ = Instance.new("DepthOfFieldEffect", Graphic)
		L_483_.Name = "DepthOfFieldEffect_Graphic"
		L_483_.Enabled = true;
		L_483_.FarIntensity = 0.077;
		L_483_.FocusDistance = 21.54;
		L_483_.InFocusRadius = 20.77;
		L_483_.NearIntensity = 0.277;
		local L_484_ = Instance.new("ColorCorrectionEffect", L_480_)
		L_484_.Name = "ColorCorrectionEffect2_Graphic"
		L_484_.Brightness = 0;
		L_484_.Contrast = - 0.07;
		L_484_.Saturation = 0;
		L_484_.Enabled = true;
		L_484_.TintColor = Color3.fromRGB(255, 247, 239)
		local L_485_ = Instance.new("ColorCorrectionEffect", L_480_)
		L_485_.Name = "ColorCorrectionEffect3_Graphic"
		L_485_.Brightness = 0.2;
		L_485_.Contrast = 0.45;
		L_485_.Saturation = - 0.1;
		L_485_.Enabled = true;
		L_485_.TintColor = Color3.fromRGB(255, 255, 255)
		local L_486_ = Instance.new("SunRaysEffect", L_480_)
		L_486_.Name = "SunRaysEffect_Graphic"
		L_486_.Enabled = false;
		L_486_.Intensity = 0.01;
		L_486_.Spread = 0.146
	else
		local L_487_ = game.Lighting;
		L_487_.Ambient = Color3.fromRGB(170, 170, 170)
		L_487_.Brightness = 2;
		L_487_.ColorShift_Bottom = Color3.fromRGB(0, 0, 0)
		L_487_.ColorShift_Top = Color3.fromRGB(0, 0, 0)
		L_487_.EnvironmentDiffuseScale = 0.105;
		L_487_.EnvironmentSpecularScale = 0.522;
		L_487_.GlobalShadows = false;
		L_487_.OutdoorAmbient = Color3.fromRGB(127, 127, 127)
		L_487_.ShadowSoftness = 0;
		L_487_.GeographicLatitude = 66;
		L_487_.ExposureCompensation = 0.2;
		game:GetService("Lighting")["BloomEffect_Graphic"]:Destroy()
		game:GetService("Lighting")["ColorCorrectionEffect1_Graphic"]:Destroy()
		game:GetService("Lighting")["ColorCorrectionEffect2_Graphic"]:Destroy()
		game:GetService("Lighting")["ColorCorrectionEffect3_Graphic"]:Destroy()
		game:GetService("Lighting")["SunRaysEffect_Graphic"]:Destroy()
	end
end)
L_35_.Misc:Toggle("Infinite Energy", false, function(L_488_arg0)
	InfiniteEnergy = L_488_arg0
end)
L_35_.Misc:Toggle("Infinite Speed Run", false, function(L_489_arg0)
	InfAbility = L_489_arg0;
	if L_489_arg0 == false then
		if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility") then
			game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility"):Destroy()
		end
	else
		InfAb()
	end
end)
L_35_.Misc:Toggle("Infinite Jump", false, function(L_490_arg0)
	Infinite = L_490_arg0;
	game:GetService("UserInputService").JumpRequest:connect(function()
		if Infinite then
			game:GetService"Players".LocalPlayer.Character:FindFirstChildOfClass"Humanoid":ChangeState("Jumping")
		end
	end)
end)
L_35_.Misc:Toggle("Walk on Water", false, function(L_491_arg0)
	_25msShared.WalkWater = L_491_arg0;
	if _25msShared.WalkWater then
		game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000, 112, 1000)
	else
		game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000, 80, 1000)
	end
end)
L_35_.Mirage:Label("Mirage Island")
L_35_.Mirage:Toggle("Auto Lock Camera to Moon", false, function(L_492_arg0)
	_25msShared.AutoLockMoon = L_492_arg0;
	LockMoon()
end)
function LockMoon()
	local L_493_ = game:GetService("Lighting")
	local L_494_ = game.Workspace.CurrentCamera;
	local L_495_, L_496_ = CFrame.new, CFrame.Angles;
	local L_497_ = math.asin;
	local L_498_ = workspace.CurrentCamera;
	local L_499_ = game.Players.LocalPlayer;
	local L_500_ = L_499_.Character;
	local L_501_ = L_500_:WaitForChild("HumanoidRootPart")
	local L_502_ = L_500_:FindFirstChild("Neck", true)
	local L_503_ = L_502_.C0.Y;
	game:GetService("RunService").RenderStepped:Connect(function()
		if _25msShared.AutoLockMoon then
			game:GetService("ReplicatedStorage").Remotes.CommE:FireServer("ActivateAbility")
			local L_504_ = Vector3.new(0, 0, 0)
			local L_505_ = L_493_:GetMoonDirection()
			local L_506_ = CFrame.new(L_504_, L_505_)
			workspace.CurrentCamera.CFrame = L_506_;
			local L_507_ = L_501_.CFrame:toObjectSpace(L_506_).lookVector.unit;
			if L_502_ and Lock then
				L_502_.C0 = L_495_(0, L_503_, 0) * L_496_(0, - L_497_(L_507_.x), 0) * L_496_(L_497_(L_507_.y), 0, 0)
			end
		else
			L_494_.FieldOfView = 70
		end
	end)
end;
L_35_.Mirage:Line()
L_35_.Mirage:Toggle("Teleport To Mirage Island", false, function(L_508_arg0)
	_25msShared.MirageIsland = L_508_arg0;
	StopTween(_25msShared.MirageIsland)
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.MirageIsland then
				for L_509_forvar0, L_510_forvar1 in pairs(game:GetService("Workspace")._WorldOrigin.Locations:GetChildren()) do
					if L_510_forvar1.Name == "Mirage Island" then
						TP(L_510_forvar1.CFrame * CFrame.new(0, 333, 0))
					end
				end
			end
		end)
	end
end)
function ESPMirageIsland()
	pcall(function()
		if _25msShared.ESPMirageIsland then
			for L_511_forvar0, L_512_forvar1 in pairs(game:GetService("Workspace").Map.MysticIsland:GetChildren()) do
				pcall(function()
					if L_512_forvar1.Name == "Center" then
						if not L_512_forvar1:FindFirstChild("EspMirage") then
							local L_513_ = Instance.new("BillboardGui", L_512_forvar1)
							L_513_.Name = "EspMirage"
							L_513_.ExtentsOffset = Vector3.new(0, 1, 0)
							L_513_.Size = UDim2.new(1, 200, 1, 30)
							L_513_.Adornee = L_512_forvar1;
							L_513_.AlwaysOnTop = true;
							local L_514_ = Instance.new("TextLabel", L_513_)
							L_514_.Font = "GothamBold"
							L_514_.FontSize = "Size14"
							L_514_.TextWrapped = true;
							L_514_.Size = UDim2.new(1, 0, 1, 0)
							L_514_.TextYAlignment = "Top"
							L_514_.BackgroundTransparency = 1;
							L_514_.TextStrokeTransparency = 0.5;
							L_514_.TextColor3 = Color3.fromRGB(255, 255, 255)
							L_514_.Text = "Mirage Island" .. " \n" .. " [ " .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_512_forvar1.Position).Magnitude / 3) .. " M" .. " ] "
						else
							L_512_forvar1.EspMirage.TextLabel.Text = "Mirage Island" .. " \n" .. " [ " .. L_51_func((game:GetService("Players").LocalPlayer.Character.Head.Position - L_512_forvar1.Position).Magnitude / 3) .. " M" .. " ] "
							L_512_forvar1.EspMirage.TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
						end
					end
				end)
			end
		else
			for L_515_forvar0, L_516_forvar1 in pairs(game:GetService("Workspace")._WorldOrigin.Locations:GetChildren()) do
				if L_516_forvar1.Name == "Center" then
					if L_516_forvar1:FindFirstChild("EspMirage") then
						L_516_forvar1:FindFirstChild("EspMirage"):Destroy()
					end
				end
			end
		end
	end)
end;
L_35_.Mirage:Toggle("ESP Mirage Island", false, function(L_517_arg0)
	_25msShared.ESPMirageIsland = L_517_arg0;
	ESPMirageIsland()
end)
spawn(function()
	while wait() do
		if _25msShared.ESPMirageIsland then
			ESPMirageIsland()
		end
	end
end)
L_35_.Mirage:Button("Teleport To Blue Gear", function()
	pcall(function()
		if game.workspace.Map:FindFirstChild("MysticIsland") then
			for L_518_forvar0, L_519_forvar1 in pairs(game:GetService("Workspace").Map:FindFirstChild("MysticIsland"):GetChildren()) do
				if L_519_forvar1.Name == "Part" then
					if L_519_forvar1.ClassName == "MeshPart" then
						TP(L_519_forvar1.CFrame)
						L_519_forvar1.Transparency = 0
					end
				end
			end
		end
	end)
end)
L_35_.Mirage:Line()
L_35_.Mirage:Button("Teleport To Advanced Fruit Dealer", function()
	pcall(function()
		repeat
			wait()
		until game:GetService("Workspace").Map:FindFirstChild("MysticIsland")
		if game:GetService("Workspace").Map:FindFirstChild("MysticIsland") then
			AllNPCS = getnilinstances()
			for L_520_forvar0, L_521_forvar1 in pairs(game:GetService("ReplicatedStorage").NPCs:GetChildren()) do
				table.insert(AllNPCS, L_521_forvar1)
			end;
			for L_522_forvar0, L_523_forvar1 in pairs(AllNPCS) do
				if L_523_forvar1.Name == "Advanced Fruit Dealer" then
					TP(L_523_forvar1.HumanoidRootPart.CFrame)
				end
			end
		end
	end)
end)
L_35_.Mirage:Button("Teleport To Highest Point", function(L_524_arg0)
	pcall(function()
		if game:GetService("Workspace").Map:FindFirstChild("MysticIsland") then
			local L_525_ = game.Workspace.Map.MysticIsland.BiggTree.Part;
			TP(CFrame.new(L_525_.Position))
			repeat
				wait()
			until (game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Position - bigTreePart.Position).Magnitude < 5
		end
	end)
end)
L_35_.Mirage:Button("Remove Fog in Mirage Island", function()
	pcall(function()
		game.Lighting.LightingLayers.MirageFog:Destroy()
	end)
end)
L_35_.RaceV4:Label("Pro Playah")
L_35_.RaceV4:Toggle("Auto Kill Players In Trial", _25msShared.AutoKillPlayerInTrial, function(L_526_arg0)
	_25msShared.AutoKillPlayerInTrial = L_526_arg0;
	_25msShared.AutoObs = L_526_arg0;
	StopTween(_25msShared.AutoKillPlayerInTrial)
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.AutoKillPlayerInTrial then
				for L_527_forvar0, L_528_forvar1 in pairs(game:GetService("Workspace").Characters:GetChildren()) do
					if L_528_forvar1.Name ~= game.Players.LocalPlayer.Name and (L_528_forvar1.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 150 then
						if L_528_forvar1.Humanoid.Health > 0 then
							repeat
								task.wait()
								EquipWeapon(_25msShared.SelectWeapon)
								NameTarget = L_528_forvar1.Name;
								TP(L_528_forvar1.HumanoidRootPart.CFrame * CFrame.new(0, 3, 3))
								L_528_forvar1.HumanoidRootPart.CanCollide = false;
								L_528_forvar1.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
							until not _25msShared.AutoKillPlayerInTrial or not L_528_forvar1.Parent or L_528_forvar1.Humanoid.Health <= 0
						end
					end
				end
			end
		end)
	end
end)
L_35_.RaceV4:Label("Train")
function CheckAcientOneStatus()
	if not game.Players.LocalPlayer.Character:FindFirstChild("RaceTransformed") then
		return "You Have Yet To Achieve Greatness"
	end;
	local L_529_ = nil;
	local L_530_ = nil;
	local L_531_ = nil;
	L_531_, L_530_, L_529_ = game.ReplicatedStorage.Remotes.CommF_:InvokeServer("UpgradeRace", "Check")
	if L_531_ == 1 then
		return "You Need Train More."
	elseif L_531_ == 2 or L_531_ == 4 or L_531_ == 7 then
		return "Can Buy Gear With " .. L_529_ .. " Fragments"
	elseif L_531_ == 3 then
		return "You Need Train More."
	elseif L_531_ == 5 then
		return "You're Done Your Race."
	elseif L_531_ == 6 then
		return "Upgrade completed: " .. L_530_ - 2 .. "/3, Need Trains More"
	end;
	if L_531_ ~= 8 then
		if L_531_ == 0 then
			return "Ready For Trial"
		else
			return "You Have Yet To Achieve Greatness"
		end
	end;
	return "Remaining " .. 10 - L_530_ .. " Training Sessions."
end;
local L_54_ = L_35_.RaceV4:Label("Ancient Quest Status: Click the Check button")
L_35_.RaceV4:Button('Check', function()
	L_54_:Set(CheckAcientOneStatus())
end)
_25msShared.TrainV4Type = "Bone"
L_35_.RaceV4:Dropdown("Select Train Mode", {
	"Bone",
	"Katakuri"
}, "Bone", function(L_532_arg0)
	_25msShared.TrainV4Type = L_532_arg0
end)
L_35_.RaceV4:Toggle('Auto Train V4', _25msShared.AutoTrainV4, function(L_533_arg0)
	_25msShared.AutoTrainV4 = L_533_arg0;
	StopTween(_25msShared.AutoTrainV4)
end)
spawn(function()
	while wait() do
		if _25msShared.AutoTrainV4 then
			local L_534_ = CheckAcientOneStatus()
			if string.find(L_534_, "Can Buy Gear") then
				v229, v228, v227 = game.ReplicatedStorage.Remotes.CommF_:InvokeServer("UpgradeRace", "Check")
				if v227 and game.Players.LocalPlayer.Data.Fragments.Value >= v227 then
					BuyGear()
				elseif v227 and game.Players.LocalPlayer.Data.Fragments.Value <= v227 then
					_25msShared.AutoTrainV4 = false;
					L_31_func("You don't have enough Fragments!")
				end
			end;
			if string.find(L_534_, "Ready For Trial") then
				_25msShared.AutoTrainV4 = false;
				L_31_func("Ready For Next Trial.")
			end;
			if string.find(L_534_, "You're Done Your Race.") then
				_25msShared.AutoTrainV4 = false;
				L_31_func("You're Done Your Race.")
			end;
			if game.Players.LocalPlayer.Character:FindFirstChild('RaceEnergy') and game.Players.LocalPlayer.Character.RaceEnergy.Value >= 1 and not game.Players.LocalPlayer.Character.RaceTransformed.Value then
				SendKey('Y')
			end
		end
	end
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.AutoTrainV4 and _25msShared.TrainV4Type == "Bone" then
				local L_535_ = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest;
				MyLevel = game:GetService('Players').LocalPlayer.Data.Level.Value;
				if L_535_.Visible == false and MyLevel >= 2000 then
					CFrameQuestBone = CFrame.new(- 9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, - 0, - 1, 0, 0)
					if (CFrameQuestBone.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 20 then
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", "HauntedQuest1", 2)
					else
						TP(CFrameQuestBone)
					end
				elseif L_535_.Visible == true or L_535_.Visible == false then
					if game:GetService('Workspace').Enemies:FindFirstChild('Reborn Skeleton') or game:GetService('Workspace').Enemies:FindFirstChild('Living Zombie') or game:GetService('Workspace').Enemies:FindFirstChild('Demonic Soul') or game:GetService('Workspace').Enemies:FindFirstChild('Posessed Mummy') then
						for L_536_forvar0, L_537_forvar1 in pairs(game:GetService('Workspace').Enemies:GetChildren()) do
							if L_537_forvar1.Name == 'Reborn Skeleton' or L_537_forvar1.Name == 'Living Zombie' or L_537_forvar1.Name == 'Demonic Soul' or L_537_forvar1.Name == 'Posessed Mummy' then
								if L_537_forvar1:FindFirstChild('Humanoid') and L_537_forvar1:FindFirstChild('HumanoidRootPart') and L_537_forvar1.Humanoid.Health > 0 then
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										L_537_forvar1.HumanoidRootPart.CanCollide = false;
										L_537_forvar1.Humanoid.WalkSpeed = 0;
										L_537_forvar1.Head.CanCollide = false;
										FarmPos = L_537_forvar1.HumanoidRootPart.CFrame;
										MonFarm = L_537_forvar1.Name;
										StartMagnet = true;
										TP(L_537_forvar1.HumanoidRootPart.CFrame * MethodFarm)
									until not _25msShared.AutoTrainV4 or not L_537_forvar1.Parent or L_537_forvar1.Humanoid.Health <= 0;
									StartMagnet = false
								end
							end
						end
					else
						StartMagnet = false;
						TP(CFrame.new(- 9482.654296875, 142.13986206054688, 5495.40576171875))
						for L_538_forvar0, L_539_forvar1 in pairs(game:GetService('ReplicatedStorage'):GetChildren()) do
							if L_539_forvar1.Name == 'Reborn Skeleton' then
								TP(L_539_forvar1.HumanoidRootPart.CFrame * MethodFarm)
							elseif L_539_forvar1.Name == 'Living Zombie' then
								TP(L_539_forvar1.HumanoidRootPart.CFrame * MethodFarm)
							elseif L_539_forvar1.Name == 'Demonic Soul' then
								TP(L_539_forvar1.HumanoidRootPart.CFrame * MethodFarm)
							elseif L_539_forvar1.Name == 'Posessed Mummy' then
								TP(L_539_forvar1.HumanoidRootPart.CFrame * MethodFarm)
							end
						end
					end
				end
			elseif _25msShared.AutoTrainV4 and _25msShared.TrainV4Type == "Katakuri" then
				local L_540_ = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest;
				MyLevel = game:GetService('Players').LocalPlayer.Data.Level.Value;
				if L_540_.Visible == false and MyLevel >= 2200 then
					CFrameQuestDough = CFrame.new(- 2021.32007, 37.7982254, - 12028.7295, 0.957576931, - 8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, - 0.288177818, - 5.2032135e-08, 0.957576931)
					if (CFrameQuestDough.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 20 then
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", "CakeQuest1", 1)
					else
						TP(CFrameQuestDough)
					end
				elseif L_540_.Visible == true or L_540_.Visible == false then
					if game:GetService('Workspace').Enemies:FindFirstChild('Cake Prince') or game:GetService('Workspace').Enemies:FindFirstChild('Dough King') then
						for L_541_forvar0, L_542_forvar1 in pairs(game:GetService('Workspace').Enemies:GetChildren()) do
							if L_542_forvar1.Name == 'Cake Prince' or 'Dough King' then
								if L_542_forvar1:FindFirstChild('Humanoid') and L_542_forvar1:FindFirstChild('HumanoidRootPart') and L_542_forvar1.Humanoid.Health > 0 then
									repeat
										wait()
										EquipWeapon(_25msShared.SelectWeapon)
										TP(L_542_forvar1.HumanoidRootPart.CFrame * MethodFarm)
										L_542_forvar1.HumanoidRootPart.CanCollide = false;
										L_542_forvar1.Humanoid.WalkSpeed = 0;
										L_542_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
										sethiddenproperty(game.Players.LocalPlayer, 'SimulationRadius', math.huge)
									until not _25msShared.AutoDoughBoss or not L_542_forvar1.Parent or L_542_forvar1.Humanoid.Health <= 0
								end
							end
						end
					else
						if game:GetService('ReplicatedStorage'):FindFirstChild('Cake Prince') then
							TP(game:GetService('ReplicatedStorage'):FindFirstChild('Cake Prince').HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
						elseif game:GetService('ReplicatedStorage'):FindFirstChild('Dough King') then
							TP(game:GetService('ReplicatedStorage'):FindFirstChild('Dough King').HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
						else
							if game:GetService('Workspace').Map.CakeLoaf.BigMirror.Other.Transparency == 1 then
								if game:GetService('Workspace').Enemies:FindFirstChild('Cookie Crafter') or game:GetService('Workspace').Enemies:FindFirstChild('Cake Guard') or game:GetService('Workspace').Enemies:FindFirstChild('Baking Staff') or game:GetService('Workspace').Enemies:FindFirstChild('Head Baker') then
									for L_543_forvar0, L_544_forvar1 in pairs(game:GetService('Workspace').Enemies:GetChildren()) do
										if L_544_forvar1.Name == 'Cookie Crafter' or L_544_forvar1.Name == 'Cake Guard' or L_544_forvar1.Name == 'Baking Staff' or L_544_forvar1.Name == 'Head Baker' then
											if L_544_forvar1:FindFirstChild('Humanoid') and L_544_forvar1:FindFirstChild('HumanoidRootPart') and L_544_forvar1.Humanoid.Health > 0 then
												repeat
													wait()
													EquipWeapon(_25msShared.SelectWeapon)
													TP(L_544_forvar1.HumanoidRootPart.CFrame * MethodFarm)
													L_544_forvar1.HumanoidRootPart.CanCollide = false;
													L_544_forvar1.Humanoid.WalkSpeed = 0;
													L_544_forvar1.Head.CanCollide = false;
													L_544_forvar1.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
													FarmPos = L_544_forvar1.HumanoidRootPart.CFrame;
													MonFarm = L_544_forvar1.Name;
													StartMagnet = true
												until not _25msShared.AutoTrainV4 or not L_544_forvar1.Parent or L_544_forvar1.Humanoid.Health <= 0 or game:GetService('Workspace').Map.CakeLoaf.BigMirror.Other.Transparency == 0 or game:GetService('ReplicatedStorage'):FindFirstChild('Cake Prince') or game:GetService('Workspace').Enemies:FindFirstChild('Cake Prince') or KillMob == 0;
												StartMagnet = false
											end
										end
									end
								else
									StartMagnet = false;
									TP(CFrame.new(- 2041.91162109375, 251.54185485839844, - 12345.380859375))
								end
							else
								StartMagnet = false;
								if game:GetService('Workspace').Enemies:FindFirstChild('Cake Prince') then
									TP(game:GetService('Workspace').Enemies:FindFirstChild('Cake Prince').HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
								else
									if game:GetService('ReplicatedStorage'):FindFirstChild('Dough King') then
										TP(game:GetService('ReplicatedStorage'):FindFirstChild('Dough King').HumanoidRootPart.CFrame * CFrame.new(0, 40, 0))
									end
								end
							end
						end
					end
				end
			end
		end)
	end
end)
L_35_.RaceV4:Label("Teleport")
L_35_.RaceV4:Button("Teleport To Lever Pull", function()
	PullLever()
end)
L_35_.RaceV4:Button("Teleport To Ancient Clock", function()
	AncientClock()
end)
L_35_.RaceV4:Button("Teleport To Ancient One", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(28286.35546875, 14895.3017578125, 102.62469482421875))
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(28981.552734375, 14888.4267578125, - 120.245849609375)
end)
L_35_.RaceV4:Button("Buy Gear Upgrade Race [ Train ]", function()
	BuyGear()
end)
L_35_.RaceV4:Label("Support Race V4")
L_35_.RaceV4:Button("Teleport To Race Door", function()
	TweentoCurrentRaceDoor()
end)
L_35_.RaceV4:Label("Complete Trials")
L_35_.RaceV4:Toggle("Auto Complete Human Trial", _25msShared.CompleteHumanTrial, function(L_545_arg0)
	_25msShared.CompleteHumanTrial = L_545_arg0
end)
spawn(function()
	pcall(function()
		while wait() do
			if _25msShared.CompleteHumanTrial or _25msShared.CompleteGhoulTrial then
				for L_546_forvar0, L_547_forvar1 in pairs(game.Workspace.Enemies:GetDescendants()) do
					if L_547_forvar1:FindFirstChild('Humanoid') and L_547_forvar1:FindFirstChild('HumanoidRootPart') and L_547_forvar1.Humanoid.Health > 0 then
						pcall(function()
							repeat
								wait()
								L_547_forvar1.Humanoid.Health = 0;
								L_547_forvar1.HumanoidRootPart.CanCollide = false;
								sethiddenproperty(game.Players.LocalPlayer, 'SimulationRadius', math.huge)
							until not (_25msShared.CompleteHumanTrial and _25msShared.CompleteGhoulTrial) or not L_547_forvar1.Parent or L_547_forvar1.Humanoid.Health <= 0
						end)
					end
				end
			end
		end
	end)
end)
L_35_.RaceV4:Toggle("Auto Complete Ghoul Trial", _25msShared.CompleteGhoulTrial, function(L_548_arg0)
	_25msShared.CompleteGhoulTrial = L_548_arg0
end)
L_35_.RaceV4:Toggle("Auto Conplete Shark Trial", _25msShared.CompleteSharkTrial, function(L_549_arg0)
	_25msShared.CompleteSharkTrial = L_549_arg0
end)
spawn(function()
	while wait() do
		pcall(function()
			if _25msShared.CompleteSharkTrial then
				if GetSeaBeastTrial() and (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - GetSeaBeastTrial().HumanoidRootPart.Position).Magnitude <= 2000 then
					if game.Workspace.Map:FindFirstChild('FishmanTrial') then
						TeleportSeabeast(GetSeaBeastTrial())
						psskill = GetSeaBeastTrial().HumanoidRootPart.CFrame;
						autospamskill = true
					else
						psskill = nil;
						autospamskill = false
					end
				else
					psskill = nil;
					autospamskill = false
				end
			end
		end)
	end
end)
L_35_.RaceV4:Button('Complete Sky Trial', function(L_550_arg0)
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Workspace.Map.SkyTrial.Model.FinishPart.CFrame
end)
L_35_.RaceV4:Button('Complete Mink Trial', function(L_551_arg0)
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService('Workspace').Map.MinkTrial.Ceiling.CFrame * CFrame.new(0, - 5, 0)
end)
L_35_.RaceV4:Button('Complete Cyborg Trial', function(L_552_arg0)
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, 300, 0)
end)
L_35_.Info:Label("Info")
L_35_.Info:Button("My Discord (Click Copy)", function()
	setclipboard("https://discord.gg/25ms")
end)
L_35_.Info:Button("My Youtube (Click Copy)", function()
	setclipboard("https://www.youtube.com/@CokkaHub")
end)
L_35_.Info:Button("Listen to Lofi Music", function()
	local L_553_ = Instance.new("Sound")
	L_553_.Name = "Sound Effect"
	L_553_.SoundId = "rbxassetid://9046862941"
	L_553_.Volume = 1;
	L_553_.Parent = game.Workspace;
	L_553_:Play()
end)
task.delay(2, function()
	if hookfunction and not islclosure(hookfunction) then
		print("|COKKA DEBUG| Remove Effects")
		hookfunction(require(game:GetService("ReplicatedStorage").Effect.Container.Death), function()
		end)
		hookfunction(require(game:GetService("ReplicatedStorage").Effect.Container.Respawn), function()
		end)
		hookfunction(require(game:GetService("ReplicatedStorage"):WaitForChild("GuideModule")).ChangeDisplayedNPC, function()
			return
		end)
		hookfunction(error, function()
		end)
		hookfunction(warn, function()
		end)
	end
end)
local L_55_ = getgenv and _25msShared or {}
local L_56_ = game:GetService("ReplicatedStorage").Modules.Net;
local L_57_ = L_56_:WaitForChild("RE/RegisterAttack")
local L_58_ = L_56_:WaitForChild("RE/RegisterHit")
local L_59_ = {
	NextAttack = 0,
	Distance = 65,
	attackMobs = true,
	attackPlayers = true
}
function L_59_:GetBladeHits()
	local L_554_ = {}
	local L_555_ = L_28_.Character;
	local L_556_ = L_14_:GetChildren()
	local L_557_ = L_15_:GetChildren()
	if _25msShared.AutoKillPlayerInTrial then
		for L_558_forvar0, L_559_forvar1 in pairs(L_556_) do
			if L_559_forvar1 ~= L_555_ and L_559_forvar1.HumanoidRootPart and L_28_:DistanceFromCharacter(L_559_forvar1.HumanoidRootPart.Position) < self.Distance then
				local L_560_ = L_559_forvar1:FindFirstChild("UpperTorso")
				if L_560_ then
					table.insert(L_554_, L_560_)
					if not self.FirstAttack and self.attackPlayers then
						L_57_:FireServer(0 or 0.1)
						self.FirstAttack = true
					end;
					L_58_:FireServer(L_560_)
				end
			end
		end
	end;
	for L_561_forvar0, L_562_forvar1 in pairs(L_557_) do
		if L_562_forvar1.PrimaryPart and L_28_:DistanceFromCharacter(L_562_forvar1.PrimaryPart.Position) < self.Distance then
			local L_563_ = L_562_forvar1:FindFirstChild("HumanoidRootPart")
			if L_563_ then
				table.insert(L_554_, L_563_)
				if not self.FirstAttack and self.attackMobs then
					L_57_:FireServer(0.4000000059604645)
					self.FirstAttack = true
				end;
				L_58_:FireServer(L_563_)
			end
		end
	end;
	return L_554_
end;
function L_59_:attack()
	local L_564_ = self:GetBladeHits()
	for L_565_forvar0, L_566_forvar1 in pairs(L_15_:GetChildren()) do
		local L_567_ = L_566_forvar1.Name
	end;
	for L_568_forvar0 = 1, 5 do
		L_57_:FireServer()
	end;
	for L_569_forvar0, L_570_forvar1 in pairs(L_564_) do
		for L_571_forvar0 = 1, 5 do
			L_58_:FireServer(L_570_forvar1, {
				{
					Name,
					L_570_forvar1
				},
				{
					Name,
					L_570_forvar1
				},
				{
					Name,
					L_570_forvar1
				}
			})
		end
	end
end;
task.spawn(function()
	while wait() do
		pcall(function()
			for L_572_forvar0, L_573_forvar1 in pairs(game.Workspace.Enemies:GetChildren()) do
				if L_573_forvar1.Humanoid.Health > 0 then
					if (L_573_forvar1.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 65 then
						L_59_:attack()
						task.wait(0.01)
					end
				end
			end
		end)
	end
end)
print("|COKKA DEBUG| Done loaded Cokka in: " .. os.clock() - L_1_)
Notify("<Color=White>We are still updating more features...<Color=/>", 10)
Notify("<Color=Blue>Hope you Enjoy it!<Color=/>", 8)