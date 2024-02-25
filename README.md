
  
repeat wait() until game.Players.LocalPlayer

if not game:IsLoaded() then
	local GameLoadGui = Instance.new("Message",workspace);
	GameLoadGui.Text = 'Wait Game Loading';
	game.Loaded:Wait();
	GameLoadGui:Destroy();
	task.wait(10);
end;

repeat wait() until game:IsLoaded()
repeat wait() until game:GetService("Players")
repeat wait() until game:GetService("Players").LocalPlayer
repeat wait() until game:GetService("Players").LocalPlayer.PlayerGui
repeat wait() until game:GetService("ReplicatedStorage").Effect.Container


local module = {
	Library = loadstring(game:HttpGet('https://raw.githubusercontent.com/Marukulaes/Manake-Hub/main/Library'))(),
}

_G.Settings = {

	-- [ General Tab ] --
	Auto_Farm_Level = false,
	Auto_Farm_Fast = true,
	Auto_Farm_Mob_Aura = false,
	Auto_Factory_Farm = false,
	
	-- [ World Tab ] --
	Auto_New_World = false,
	Auto_Third_World = false,

	-- [ Chest Tab ] --
	Auto_Farm_Chest = false,

	-- [ Misc World1 ] -- 
	Auto_Saber = false,
	Auto_Saber_Hop = false,
	Auto_Pole_V1 = false,
	Auto_Pole_V1_Hop = false,
	Auto_Buy_Ablility = false,

	-- [ Misc World2 ] -- 
	Auto_Bartilo_Quest = false,
	Auto_Evo_Race_V2 = false,
	Auto_Farm_Ectoplasm = false,
	Auto_True_Triple_Katana = false,
	Auto_Buy_Legendary_Sword = false,
	Auto_Buy_Enchanment_Haki = false,

	-- [ items World2 ] -- 
	Auto_Rengoku = false,
	Auto_Dragon_Trident = false,
	Auto_Dark_Coat = false,
	
	Auto_Swan_Glasses = false,
	Auto_Swan_Glasses_Hop = false,

	-- [ Setting ] --  
	Brimob = true,
	Bypass = false,
	Rejoin = true,
	FastAttack = true,
	SkillZ = true,
	SkillX = true,
	SkillC = true,
	SkillV = true,

	-- [ Funs World3 ] -- 
	Auto_Elite_Hunter = false,
	Auto_Elite_Hunter_Hop = false,

	Auto_Spawn_Cake_Prince = false,
	Auto_Cake_Prince = false,

	Auto_Farm_Bone = false,
	Auto_Trade_Bone = false,

	-- [ items World3 ] -- 
	Auto_Rainbow_Haki = false,
	Auto_Rainbow_Haki_Hop = false,


	Auto_Buddy_Sword = false,
	Auto_Buddy_Sword_Hop = false,

	Auto_Farm_Boss_Hallow = false,
	Auto_Farm_Boss_Hallow_Hop = false,

	Auto_Canvander = false,
	Auto_Canvander_Hop = false,

	Auto_Twin_Hook = false,
	Auto_Twin_Hook_Hop = false,

	Auto_Serpent_Bow = false,
	Auto_Serpent_Bow_Hop = false,

	Auto_Yama = false,
	Auto_Tushita = false,

	Auto_Dark_Dagger = false,
	Auto_Dark_Dagger_Hop = false,

	Auto_Holy_Torch = false,
	Auto_Musketeer_Hat = false,
--[[
	Auto_Farm_Boss = false,
	Select_Boss = "",
	Auto_Quest_Boss = true,
	Auto_Farm_All_Boss = false,
]]--
    -- [ Fighting Style ] --

	Auto_Superhuman = false,
	Auto_Fully_Superhuman = false,
	Auto_Death_Step = false,
	Auto_Fully_Death_Step = false,
	Auto_SharkMan_Karate = false,
	Auto_Fully_SharkMan_Karate = false,
	Auto_Electric_Claw = false,
	Auto_Dragon_Talon = false,
	Auto_God_Human = false,

	-- [ Players ] -- 

	Select_Player = "",
	Spectate_Player = false,
	Teleport_to_Player = false,
	Auto_Kill_Player = false,
	EnabledPvP = false,

	-- [ Stats ] --

	Auto_Stats = false,
	Point = 1,

	-- [ Island ] -- 

	Select_Island = "",
	Start_Tween_Island = false,

	-- [ Dungeon ] --

	Select_Dungeon = false,
	Auto_Buy_Chips_Dungeon = false,
	Auto_Start_Dungeon = false,
	Auto_Next_Island = false,
	Kill_Aura = false,
	Auto_Awake = false,

	-- [ Law ] --

	Auto_Buy_Law_Chip = false,
	Auto_Start_Law_Dungeon = false,
	Auto_Kill_Law = false,

	Select_Devil_Fruit = "",
	Auto_Buy_Devil_Fruit = false,
	Auto_Random_Fruit = false,
	Auto_Bring_Fruit = false,
	Auto_Store_Fruit = false,
--[[
	LockMoon = false,
	Auto_Mirage_Island = false,
	AutoMasterySkill = false,
	HealthMs = 85,

    ESP_Mirage_Island = false,
	Auto_Awakening_One_Quest = false,
	ESP_Chest = false,
	Auto_Sea_King = false,
	Select_Mode = "Chest",
	Remove_UI_DamageCounter = false,
	Notifications_Remove = false,
	Auto_CFrame = false,
	Auto_Gear = false,
	AutoCDK = false,
	Auto_Soul_Guitar = false,
	Select_Material = {},
	MaterialFarm = false,]]--
}

function LoadSettings()
	if readfile and writefile and isfile and isfolder then
		if not isfolder("Maruko Hub Free Script") then
			makefolder("Maruko Hub Free Script")
		end
		if not isfolder("Maruko Hub Free Script/Blox Fruits/") then
			makefolder("Maruko Hub Free Script/Blox Fruits/")
		end
		if not isfile("Maruko Hub Free Script/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json") then
			writefile("Maruko Hub Free Script/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json", game:GetService("HttpService"):JSONEncode(_G.Settings))
		else
			local Decode = game:GetService("HttpService"):JSONDecode(readfile("Maruko Hub Free Script/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json"))
			for i,v in pairs(Decode) do
				_G.Settings[i] = v
			end
		end
	else
		return warn("Status : Undetected Executor")
	end
end

function SaveSettings()
	if readfile and writefile and isfile and isfolder then
		if not isfile("Maruko Hub Free Script/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json") then
			LoadSettings()
		else
			local Decode = game:GetService("HttpService"):JSONDecode(readfile("Maruko Hub Free Script/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json"))
			local Array = {}
			for i,v in pairs(_G.Settings) do
				Array[i] = v
			end
			writefile("Maruko Hub Free Script/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json", game:GetService("HttpService"):JSONEncode(Array))
		end
	else
		return warn("Status : Undetected Executor")
	end
end

LoadSettings()

if _G.Settings.Select_Boss == nil then
	_G.Settings.Select_Boss = "nil"
end

--Script 

if game.PlaceId == 2753915549 then
	World1 = true 
elseif game.PlaceId == 4442272183 then
	World2 = true
elseif game.PlaceId == 7449423635 then
	World3 = true
end

local function QuestCheck()
	local Lvl = game:GetService("Players").LocalPlayer.Data.Level.Value
	if Lvl >= 1 and Lvl <= 9 then
		if tostring(game.Players.LocalPlayer.Team) == "Marines" then
			MobName = "Trainee"
			QuestName = "MarineQuest"
			QuestLevel = 1
			Mon = "Trainee"
			NPCPosition = CFrame.new(-2709.67944, 24.5206585, 2104.24585, -0.744724929, -3.97967455e-08, -0.667371571, 4.32403588e-08, 1, -1.07884304e-07, 0.667371571, -1.09201515e-07, -0.744724929)
		elseif tostring(game.Players.LocalPlayer.Team) == "Pirates" then
			MobName = "Bandit"
			Mon = "Bandit"
			QuestName = "BanditQuest1"
			QuestLevel = 1
			NPCPosition = CFrame.new(1059.99731, 16.9222069, 1549.28162, -0.95466274, 7.29721794e-09, 0.297689587, 1.05190106e-08, 1, 9.22064114e-09, -0.297689587, 1.19340022e-08, -0.95466274)
		end
		return {
			[1] = QuestLevel,
			[2] = NPCPosition,
			[3] = MobName,
			[4] = QuestName,
			[5] = LevelRequire,
			[6] = Mon,
			[7] = MobCFrame
		}
	end

	if Lvl >= 210 and Lvl <= 249 then
		MobName = "Dangerous Prisoner"
		QuestName = "PrisonerQuest"
		QuestLevel = 2
		Mon = "Dangerous Prisoner"
		NPCPosition = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
		local matchingCFrames = {}
		local result2 = string.gsub(result, "[%[%]]", "")
		local result3 = string.gsub(result2, "%d+", "")
		local result4 = string.gsub(result3, "%s+", "")

		for i,v in pairs(game.workspace.EnemySpawns:GetChildren()) do
			if v.Name == result4 then
				table.insert(matchingCFrames, v.CFrame)
			end
			MobCFrame = matchingCFrames
		end
		return {
			[1] = QuestLevel,
			[2] = NPCPosition,
			[3] = MobName,
			[4] = QuestName,
			[5] = LevelRequire,
			[6] = Mon,
			[7] = MobCFrame
		}
	end

	--game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
	local GuideModule = require(game:GetService("ReplicatedStorage").GuideModule)
	local Quests = require(game:GetService("ReplicatedStorage").Quests)
	for i,v in pairs(GuideModule["Data"]["NPCList"]) do
		for i1,v1 in pairs(v["Levels"]) do
			if Lvl >= v1 then
				if not LevelRequire then
					LevelRequire = 0
				end
				if v1 > LevelRequire then
					NPCPosition = i["CFrame"]
					QuestLevel = i1
					LevelRequire = v1
				end
				if #v["Levels"] == 3 and QuestLevel == 3 then
					NPCPosition = i["CFrame"]
					QuestLevel = 2
					LevelRequire = v["Levels"][2]
				end
			end
		end
	end
	if Lvl >= 375 and Lvl <= 399 then -- Fishman Warrior
		if _G.Auto_Farm_Level and (NPCPosition.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 3000 then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
		end
	end

	if Lvl >= 400 and Lvl <= 449 then -- Fishman Commando
		if _G.Auto_Farm_Level and (NPCPosition.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 3000 then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
		end
	end
	for i,v in pairs(Quests) do
		for i1,v1 in pairs(v) do
			if v1["LevelReq"] == LevelRequire and i ~= "CitizenQuest" then
				QuestName = i
				for i2,v2 in pairs(v1["Task"]) do
					MobName = i2
					Mon = string.split(i2," [Lv. ".. v1["LevelReq"] .. "]")[1]
				end
			end
		end
	end
	if QuestName == "MarineQuest2" then
		QuestName = "MarineQuest2"
		QuestLevel = 1
		MobName = "Chief Petty Officer"
		Mon = "Chief Petty Officer"
		LevelRequire = 120
	elseif QuestName == "ImpelQuest" then
		QuestName = "PrisonerQuest"
		QuestLevel = 2
		MobName = "Dangerous Prisoner"
		Mon = "Dangerous Prisoner"
		LevelRequire = 210
		NPCPosition = CFrame.new(5310.60547, 0.350014925, 474.946594, 0.0175017118, 0, 0.999846935, 0, 1, 0, -0.999846935, 0, 0.0175017118)
	elseif QuestName == "SkyExp1Quest" then
		if QuestLevel == 1 then
			NPCPosition = CFrame.new(-4721.88867, 843.874695, -1949.96643, 0.996191859, -0, -0.0871884301, 0, 1, -0, 0.0871884301, 0, 0.996191859)
		elseif QuestLevel == 2 then
			NPCPosition = CFrame.new(-7859.09814, 5544.19043, -381.476196, -0.422592998, 0, 0.906319618, 0, 1, 0, -0.906319618, 0, -0.422592998)
		end
	elseif QuestName == "Area2Quest" and QuestLevel == 2 then
		QuestName = "Area2Quest"
		QuestLevel = 1
		MobName = "Swan Pirate"
		Mon = "Swan Pirate"
		LevelRequire = 775
	end
	MobName = MobName:sub(1,#MobName)
	if not MobName:find("Lv") then
		for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
			MonLV = string.match(v.Name, "%d+")
			if v.Name:find(MobName) and #v.Name > #MobName and tonumber(MonLV) <= Lvl + 50 then
				MobName = v.Name
			end
		end
	end
	if not MobName:find("Lv") then
		for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
			MonLV = string.match(v.Name, "%d+")
			if v.Name:find(MobName) and #v.Name > #MobName and tonumber(MonLV) <= Lvl + 50 then
				MobName = v.Name
				Mon = a
			end
		end
	end

	local matchingCFrames = {}
	local result2 = string.gsub(result, "[%[%]]", "")
	local result3 = string.gsub(result2, "%d+", "")
	local result4 = string.gsub(result3, "%s+", "")

	for i,v in pairs(game.workspace.EnemySpawns:GetChildren()) do
		if v.Name == result4 then
			table.insert(matchingCFrames, v.CFrame)
		else
			table.insert(matchingCFrames, nil)
		end
		MobCFrame = matchingCFrames
	end

	return {
		[1] = QuestLevel,
		[2] = NPCPosition,
		[3] = MobName,
		[4] = QuestName,
		[5] = LevelRequire,
		[6] = Mon,
		[7] = MobCFrame,
		[8] = MonQ,
		[9] = MobCFrameNuber
	}
end

-----------------------------------------------------------------------------------

function AutoHaki()
	if not game:GetService("Players").LocalPlayer.Character:FindFirstChild("HasBuso") then
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
	end
end

function EquipWeapon(ToolSe)
	if not _G.NotAutoEquip then
		if game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe) then
			Tool = game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe)
			wait(.1)
			game.Players.LocalPlayer.Character.Humanoid:EquipTool(Tool)
		end
	end
end

function Com(com,...)
	local Remote = game:GetService('ReplicatedStorage').Remotes:FindFirstChild("Comm"..com)
	if Remote:IsA("RemoteEvent") then
		Remote:FireServer(...)
	elseif Remote:IsA("RemoteFunction") then
		Remote:InvokeServer(...)
	end
end

-- [Tween Functions]

getgenv().ToTarget = function(Pos)
	Distance = (Pos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
	if game.Players.LocalPlayer.Character.Humanoid.Sit == true then game.Players.LocalPlayer.Character.Humanoid.Sit = false end
	pcall(function() tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart,TweenInfo.new(Distance/350, Enum.EasingStyle.Linear),{CFrame = Pos}) end)
	tween:Play()
	if Distance <= 250 then
		tween:Cancel()
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Pos
	end
	if _G.StopTween == true then
		tween:Cancel()
		_G.Clip = false
	end
end

function StopTween(target)
	if not target then
		getgenv().ToTarget(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)
		_G.StopTween = true
		_G.UseSkill = false
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
		if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
			game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
		end
		wait(0.2)
		_G.StopTween = false
		_G.Clip = false
	end
	if game.Players.LocalPlayer.Character:FindFirstChild('Highlight') then
		game.Players.LocalPlayer.Character:FindFirstChild('Highlight'):Destroy()
	end
end

---------------------------------------------------------------

spawn(function()
	pcall(function()
		game:GetService("RunService").Stepped:Connect(function()
			if _G.Auto_Farm_Level or _G.Auto_Yama or _G.Auto_Sea_King or _G.Auto_Dack_Coat or _G.Auto_Buddy_Sword or _G.MaterialFarm or _G.Auto_Rip_Indar or _G.Auto_Farm_Mastery_Gun or _G.Auto_Farm_All_Sword or _G.Auto_Awakening_One_Quest or _G.Auto_Lever_UnLock or _G.Auto_Complete_Trial or _G.Auto_Farm_Mastery_Fruit or Auto_Mirage_Island or Auto_Gear or _G.Auto_Farm_All_Boss or _G.Auto_New_World or _G.Auto_Third_World or _G.Auto_Farm_Chest or _G.Auto_Farm_Boss or _G.Auto_Castle_Raid or _G.Auto_Elite_Hunter or _G.Auto_Cake_Prince or _G.AutoCakePrinceV2 or _G.AutoCakePrinceV2 or _G.Auto_Farm_All_Boss or _G.Auto_Saber or _G.Auto_Pole or _G.Auto_Farm_Scrap_and_Leather or _G.Auto_Farm_Angel_Wing or _G.Auto_Factory_Farm or _G.Auto_Farm_Ectoplasm or _G.Auto_Bartilo_Quest or _G.Auto_Rengoku or _G.Auto_Farm_Radioactive or _G.Auto_Farm_Vampire_Fang or _G.Auto_Farm_Mystic_Droplet or _G.Auto_Farm_GunPowder or _G.Auto_Farm_Dragon_Scales or _G.Auto_Evo_Race_V2 or _G.Auto_Swan_Glasses or _G.Auto_Dragon_Trident or _G.Auto_Soul_Reaper or _G.Auto_Farm_Fish_Tail or _G.Auto_Farm_Mini_Tusk or _G.Auto_Farm_Magma_Ore or _G.Auto_Farm_Bone or _G.AutoCDK or _G.Auto_Soul_Guitar or _G.Auto_Farm_Conjured_Cocoa or _G.Auto_Open_Dough_Dungeon or _G.Auto_Rainbow_Haki or _G.Auto_Musketeer_Hat or _G.Auto_Holy_Torch or _G.Auto_Canvander or _G.Auto_Twin_Hook or _G.Auto_Serpent_Bow or _G.Auto_Fully_Death_Step or _G.Auto_Fully_SharkMan_Karate or _G.Teleport_to_Player or _G.Auto_Kill_Player_Melee or _G.Auto_Kill_Player_Gun or _G.Start_Tween_Island or _G.Auto_Next_Island or _G.Auto_Kill_Law then
				if not game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
					local Noclip = Instance.new("BodyVelocity")
					Noclip.Name = "BodyClip"
					Noclip.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart
					Noclip.MaxForce = Vector3.new(100000,100000,100000)
					Noclip.Velocity = Vector3.new(0,0,0)
				end
			else	
				if game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
					game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
				end
			end
		end)
	end)
end)

spawn(function()
	pcall(function()
		game:GetService("RunService").Stepped:Connect(function()
			if _G.Auto_Farm_Level or _G.Auto_Yama or _G.Auto_Sea_King or _G.Auto_Dack_Coat or _G.Auto_Buddy_Sword or _G.MaterialFarm or _G.Auto_Rip_Indar or _G.Auto_Farm_Mastery_Gun or _G.Auto_Farm_All_Sword or _G.Auto_Awakening_One_Quest or _G.Auto_Farm_Mastery_Fruit or _G.Auto_Lever_UnLock or _G.Auto_Complete_Trial or Auto_Mirage_Island or Auto_Gear or _G.Auto_Farm_All_Boss or _G.Auto_New_World or _G.Auto_Third_World or _G.Auto_Farm_Chest or _G.Auto_Farm_Boss or _G.Auto_Castle_Raid or _G.Auto_Elite_Hunter or _G.Auto_Cake_Prince or _G.AutoCakePrinceV2 or _G.AutoCakePrinceV2 or _G.Auto_Farm_All_Boss or _G.Auto_Saber or _G.Auto_Pole or _G.Auto_Farm_Scrap_and_Leather or _G.Auto_Farm_Angel_Wing or _G.Auto_Factory_Farm or _G.Auto_Farm_Ectoplasm or _G.Auto_Bartilo_Quest or _G.Auto_Rengoku or _G.Auto_Farm_Radioactive or _G.Auto_Farm_Vampire_Fang or _G.Auto_Farm_Mystic_Droplet or _G.Auto_Farm_GunPowder or _G.Auto_Farm_Dragon_Scales or _G.Auto_Evo_Race_V2 or _G.Auto_Swan_Glasses or _G.Auto_Dragon_Trident or _G.Auto_Soul_Reaper or _G.Auto_Farm_Fish_Tail or _G.Auto_Farm_Mini_Tusk or _G.Auto_Farm_Magma_Ore or _G.Auto_Farm_Bone or _G.AutoCDK or _G.Auto_Soul_Guitar or _G.Auto_Farm_Conjured_Cocoa or _G.Auto_Open_Dough_Dungeon or _G.Auto_Rainbow_Haki or _G.Auto_Musketeer_Hat or _G.Auto_Holy_Torch or _G.Auto_Canvander or _G.Auto_Twin_Hook or _G.Auto_Serpent_Bow or _G.Auto_Fully_Death_Step or _G.Auto_Fully_SharkMan_Karate or _G.Teleport_to_Player or _G.Auto_Kill_Player_Melee or _G.Auto_Kill_Player_Gun or _G.Start_Tween_Island or _G.Auto_Next_Island or _G.Auto_Kill_Law then
				for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
					if v:IsA("BasePart") then
						v.CanCollide = false    
					end
				end
			end
		end)
	end)
end)

local function Bypass(Position)
	local CFramePos = Position
	_G.StopTween =  true
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(111111,111111,111111)
	wait()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Position
	wait()
	game.Players.LocalPlayer.Character.Head:Destroy()
	wait()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Position
	wait()
	local args = {
		[1] = "SetSpawnPoint"
	}

	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	wait()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Position

	wait()
	local args = {
		[1] = "SetSpawnPoint"
	}

	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	wait(0.1)
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Position
	wait()
	local args = {
		[1] = "SetSpawnPoint"
	}

	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	wait()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(111111,111111,111111)
	wait()
	game.Players.LocalPlayer.Character.Head:Destroy()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(99999999,99999999,99999999)
	wait()
	local args = {
		[1] = "SetLastSpawnPoint",
		[2] = tostring(game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value)
	}

	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	wait()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Position
	wait()
	local args = {
		[1] = "SetSpawnPoint"
	}

	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	wait()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(99999999,99999999,99999999)
	wait()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(99999999,99999999,99999999)
	wait()
	local args = {
		[1] = "SetLastSpawnPoint",
		[2] = tostring(game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value)
	}

	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	wait()
	local args = {
		[1] = "SetLastSpawnPoint",
		[2] = tostring(game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value)
	}

	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	wait(0.5)
	local args = {
		[1] = "SetLastSpawnPoint",
		[2] = tostring(game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value)
	}

	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	wait()
	wait()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Position
	wait()
	game.Players.LocalPlayer.Character.Head:Destroy()
	wait()
	game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Position
	wait()
	_G.StopTween = false
	return
end

function TPPlayer(Point)
	TweeSpeed = 300
	local LocalPlayer = game.Players.LocalPlayer 
	TweenPlay = (Point.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
	pcall(function() 
		tot = game:GetService("TweenService"):Create(LocalPlayer.Character.HumanoidRootPart,TweenInfo.new(TweenPlay/TweeSpeed, Enum.EasingStyle.Linear),{CFrame = Point})
	end);tot:Play()
	if TweenPlay >= 1200 then
		game.Players.LocalPlayer.Character.Head:Destroy()
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Point * CFrame.new(0,50,0)
		wait(.2)
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Point
		wait(.1)
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Point * CFrame.new(0,50,0)
		game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = true
		wait(.1)
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Point
		wait(0.5)
		game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = false
		_G.Clip = false
	elseif TweenPlay <= 300 then
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Point
	end
	if _G.StopTween == true then tot:Cancel();_G.Clip = false end
	if _G.StopTween then
		tot:Cancel()
		BringMobFarm = false
		UseSkillGun = false
		_G.UseSkill = false
	elseif game.Players.LocalPlayer.Character.Humanoid.Health > 0 then
		tot:Play()
	end
end	

function Check_Sword(Sword_Name)
	for i, v in pairs(game:GetService("ReplicatedStorage").Remotes['CommF_']:InvokeServer("getInventory")) do
		if (v.Type == "Sword") then
			if v.Name == Sword_Name then
				return true
			end
		end
	end
end

-- CDK ["Alucard Fragment"]

spawn(function()
	while task.wait() do
		pcall(function()
			if _G.Auto_Farm_Level or _G.Auto_Farm_Mob_Aura or _G.Auto_Farm_Candy or _G.Auto_New_World or _G.Auto_Saber or _G.Auto_Pole or _G.Auto_Third_World or _G.Auto_Rengoku or _G.Auto_Dragon_Trident 
				or _G.Auto_Dark_Coat or _G.Auto_Swan_Glasses or _G.Auto_Bartilo_Quest or _G.Auto_Ectoplasm or _G.Auto_Evo_Race_V2 or _G.Auto_True_Triple_Katana or _G.Auto_Buy_Legendary_Sword 
				or _G.Auto_Buy_Enchanment_Haki or _G.Auto_Elite_Hunter or _G.Auto_Farm_Bone or _G.Auto_Cake_Prince or _G.Auto_Buddy_Sword or _G.Auto_Farm_Boss_Hallow or _G.Auto_Twin_Hook 
				or _G.Auto_Cavander or _G.Auto_Yama or _G.Auto_Tushita or _G.Auto_Cursed_Dual_Katana or _G.Auto_Serpent_Bow or _G.Auto_Dark_Dagger or _G.Auto_Rainbow_Haki 
				or _G.Auto_Musketeer_Hat or _G.Auto_Ken_Haki_V2 or _G.Auto_Farm_All_Boss or _G.Auto_Farm_Boss or _G.Auto_Farm_Gun_Mastery or _G.Auto_Farm_BF_Mastery or _G.AutoSuperhuman 
				or _G.AutoDeathStep or _G.Auto_SharkMan_Karate or _G.Auto_Fully_SharkMan_Karate or _G.Auto_Fully_DeathStep or _G.Auto_Electric_Claw or _G.Auto_Dragon_Talon or _G.Auto_Kill_Law 
				or _G.Auto_Next_Island or _G.Teleport_to_Player then
				if not game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
					local Noclip = Instance.new("BodyVelocity")
					Noclip.Name = "BodyClip"
					Noclip.Parent = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart
					Noclip.MaxForce = Vector3.new(100000,100000,100000)
					Noclip.Velocity = Vector3.new(0,0,0)
				end
			else
				game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
			end
		end)
	end
end)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------
local Window = module.Library:CreateWindow({ Title =  ' Manake Hub - Moblie Script [ General Script ]', Center = true,  AutoShow = true, })
local Tabs = { Main = Window:AddTab('[ General ]'),  items = Window:AddTab('[ items / Quest ]'), Island = Window:AddTab('[ Island ]'), Shop = Window:AddTab('[ Shop ]'), }
module.Library:SetWatermark('Manake Hub - Moblie Script | '..os.date('%A, %B %d %Y'))
local Farm = Tabs.Main:AddLeftGroupbox('General Tab')

Farm:AddToggle('AutoFarmLevel', {
	Text = 'Auto Farm Level',
	Default = _G.Settings.Auto_Farm_Level,
	Tooltip = 'Auto Farm Level',
})

Toggles.AutoFarmLevel:OnChanged(function(value)
	_G.Auto_Farm_Level = value
	_G.Settings.Auto_Farm_Level = value
	StopTween(_G.Auto_Farm_Level)
	SaveSettings()
end)

Farm:AddToggle('AutoFarmFast', {
	Text = 'Auto Farm Fast',
	Default = _G.Settings.Auto_Farm_Fast,
	Tooltip = 'Auto Farm Fast',
})

Toggles.AutoFarmFast:OnChanged(function(value)
	if World1 then
		_G.AutoFarmFast = value
	else
		_G.AutoFarmFast = false
	end
	_G.Settings.Auto_Farm_Fast = value
	StopTween(_G.AutoFarmFast)
	SaveSettings()
end)

spawn(function()
	while wait() do 
		if _G.Settings.Auto_Farm_Fast and _G.AutoFarmFast_Num == 1 then
			_G.AutoFarmFast = false
		end
	end
end)

local SetCFarme = 1
spawn(function()
	while wait() do
		local MyLevel = game.Players.LocalPlayer.Data.Level.Value
		local QuestC = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest
		pcall(function()
			if _G.Auto_Farm_Level then
				if _G.AutoFarmFast and (MyLevel >= 15 and MyLevel <= 300) then
					if MyLevel >= 15 and MyLevel <= 300 then
						Auto_Farm_Level_Fast()
						return
					end
				else
					if QuestC.Visible == true then
						if game:GetService("Workspace").Enemies:FindFirstChild(QuestCheck()[3]) then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if string.find(v.Name,QuestCheck()[3]) then
									if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
										repeat task.wait()
											if _G.Auto_CFrame then
												SetCFarme = 1
											end
											if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, QuestCheck()[6]) then
												game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
											else
												PosMon = v.HumanoidRootPart.CFrame
												v.HumanoidRootPart.Size = Vector3.new(60,60,60)
												v.HumanoidRootPart.CanCollide = false
												v.Humanoid.WalkSpeed = 0
												v.Head.CanCollide = false
												BringMobFarm = true
												EquipWeapon(_G.Select_Weapon)
												v.HumanoidRootPart.Transparency = 1
												getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
											end
										until not _G.Auto_Farm_Level or not v.Parent or v.Humanoid.Health <= 0 or QuestC.Visible == false or not v:FindFirstChild("HumanoidRootPart")
									end
								end
							end
						else
							if _G.Auto_CFrame and not _G.AutoFarmFast then
								getgenv().ToTarget(QuestCheck()[7][SetCFarme] * MethodFarm)
								if (QuestCheck()[7][SetCFarme].Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
									if SetCFarme == nil or SetCFarme == '' then
										SetCFarme = 1
									elseif SetCFarme >= #QuestCheck()[7] then
										SetCFarme = 1
									end
									SetCFarme =  SetCFarme + 1
									wait(0.5)
								end
							end
						end
					else
						getgenv().ToTarget(QuestCheck()[2])
						if (QuestCheck()[2].Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1 then
							BringMobFarm = false
							wait(0.2)
							game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("StartQuest", QuestCheck()[4], QuestCheck()[1]) wait(0.5)
							getgenv().ToTarget(QuestCheck()[7][1] * MethodFarm)
						end
					end
				end
			end
		end)
	end
end)

_G.ChackPlayer = 0
_G.ChackPlayer2 = _G.ChackPlayer
function Auto_Farm_Level_Fast()
	local PlayersAll = game.Players:GetPlayers()
	local PlayerLevel = game.Players.LocalPlayer.Data.Level.Value
	local quest = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text
	local Player = string.split(quest," ")[2]
	getgenv().SelectPly = string.split(quest," ")[2]
	pcall(function()
		local MyLevel = game.Players.LocalPlayer.Data.Level.Value
		local QuestC = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest
		CFrameMon = CFrame.new(-4837.64258, 850.10199, -1840.58374, -0.430530697, -4.42848638e-08, -0.90257591, -3.08042516e-08, 1, -3.43712756e-08, 0.90257591, 1.30052875e-08, -0.430530697)
		if MyLevel >= 15 and MyLevel <= 69 then
			BringMobFarm = false
			for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
				if string(v.Name,"God's Guard") then
					if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
						repeat task.wait()
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
							v.HumanoidRootPart.CanCollide = false
							v.Humanoid.WalkSpeed = 0
							v.Head.CanCollide = false
							BringMobFarm = true
							EquipWeapon(_G.Select_Weapon)
							if MyLevel >= 70 and MyLevel <= 310 then
								if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
									game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("PlayerHunter")
								end
							end
							PosMon = v.HumanoidRootPart.CFrame
							v.HumanoidRootPart.Size = Vector3.new(60,60,60)
							v.HumanoidRootPart.Transparency = 1
							getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
						until not v.Parent or not _G.Auto_Farm_Level or v.Humanoid.Health < 0
					end
				else
					BringMobFarm = false
					if _G.Auto_Farm_Level and (CFrameMon.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 500 then
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
					end
					getgenv().ToTarget(CFrameMon)
				end
			end
		elseif MyLevel >= 70 and MyLevel <= 310 then
			if QuestC.Visible == false then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("PlayerHunter")
			elseif QuestC.Visible == true then
				if string.find(quest,"Defeat") then
					if game.Players[getgenv().SelectPly].Data.Level.Value >= 20 and game.Players[getgenv().SelectPly].Data.Level.Value <= MyLevel * 2 then
						repeat task.wait()
							if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
							end

							if game:GetService("Players").LocalPlayer.PlayerGui.Main.PvpDisabled.Visible == true then
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EnablePvp")
							end

							EquipWeapon(_G.Select_Weapon)
							TPPlayer(game:GetService("Players")[getgenv().SelectPly].Character.HumanoidRootPart.CFrame * CFrame.new(0,0,5))

							game:GetService("Players")[getgenv().SelectPly].Character.HumanoidRootPart.Size = Vector3.new(120,120,120)

							game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
							game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)

							game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
							game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
							Cilck()

							if game:GetService("Players")[getgenv().SelectPly].Character.Humanoid.Health <= 0 then
								_G.AutoFarmFast_Num = 1
								_G.AutoFarmFast = false
							end

						until game.Players[getgenv().SelectPly].Character.Humanoid.Health <= 0 or not Auto_Farm_Level_Fast() or _G.AutoFarmFast_Num == 1
						_G.AutoFarmFast_Num = 1
						_G.AutoFarmFast = false
						if not game.Players:FindFirstChild(Player) then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("PlayerHunter")
						end
					else
						for i,v in pairs(PlayersAll) do
							if v.Data.Level.Value >= 20 and v.Data.Level.Value <= PlayerLevel * 2 then
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("PlayerHunter")
								print(v)
							else
								_G.ChackPlayer = _G.ChackPlayer + 1
								if _G.ChackPlayer >= 12 then
									_G.AutoFarmFast = false
								else
									print("Chack Player ".._G.ChackPlayer)
								end
							end
						end
					end
				end
			end
		end
	end)
end

Farm:AddToggle('MobAura', {
	Text = 'Auto Farm Mob Aura',
	Default = _G.Settings.Auto_Farm_Mob_Aura,
	Tooltip = 'Farm Mob Aura',
})

Toggles.MobAura:OnChanged(function(value)
	_G.Auto_Farm_Mob_Aura = value
	_G.Settings.Auto_Farm_Mob_Aura = value
	SaveSettings()
	StopTween(_G.Auto_Farm_Mob_Aura)
end)

task.spawn(function()
	while wait() do
		pcall(function()
			if _G.Auto_Farm_Mob_Aura then
				for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
					if _G.Auto_Farm_Mob_Aura and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 and (v.HumanoidRootPart.Position-game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 1000 then
						repeat wait()
							EquipWeapon(_G.Select_Weapon)
							AutoHaki()
							PosMonAura = v.HumanoidRootPart.CFrame
							v.HumanoidRootPart.Size = Vector3.new(60,60,60)
							v.Humanoid.JumpPower = 0
							v.Humanoid.WalkSpeed = 0
							v.HumanoidRootPart.CanCollide = false
							v.Humanoid:ChangeState(11)
							getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
						until not _G.Auto_Farm_Mob_Aura or not v.Parent or v.Humanoid.Health <= 0
					end
				end
			end
		end)
	end
end)

local Chest = Tabs.Main:AddLeftGroupbox('Chest')

Chest:AddToggle('Auto_Farm_Chest', {
	Text = 'Auto Farm Chest',
	Default = _G.Settings.Auto_Farm_Chest,
	Tooltip = 'Auto Farm Chest',
})

Toggles.Auto_Farm_Chest:OnChanged(function(value)
	_G.Auto_Farm_Chest = value 
	StopTween(_G.Auto_Farm_Chest)
	if _G.Bypass_TP == false and _G.HH then
		wait(0.5)
		_G.Bypass_TP = true
	else
		_G.Bypass_TP = false
	end
	_G.Settings.Auto_Farm_Chest = value
	SaveSettings()  
end)

_G.AddPoint = 500
spawn(function()
	while wait() do 
		if _G.Auto_Farm_Chest then
			for i,v in pairs(game:GetService("Workspace"):GetDescendants()) do 
				if v.Name:find("Chest") and v:IsA("Part") then
					if (v.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 500 + _G.AddPoint then
						repeat wait()
							getgenv().ToTarget(v.CFrame)
							if (v.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1 then
								UnEquipWeapon(_G.Select_Weapon)
							else
								EquipWeapon(_G.Select_Weapon)
							end
						until _G.Auto_Farm_Chest == false or not v.Parent
						break
					else
						_G.AddPoint = _G.AddPoint + 500
					end
				else
					if v.Name:find("Chest") and v:IsA("Part") then
						if (v.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude >= 500 + _G.AddPoint then
							_G.AddPoint = _G.AddPoint + 500
						end
					end
				end
			end
		end
	end
end)

local Mastery = Tabs.Main:AddLeftGroupbox('Mastery Sections')

Mastery:AddToggle('Auto_Farm_BF_Mastery', {
	Text = "Auto Farm BF Mastery",
	Tooltip = "Auto_Farm_BF_Mastery",
	Default = _G.Settings.Auto_Farm_Mastery_Fruit,
})

Toggles.Auto_Farm_BF_Mastery:OnChanged(function(value)
	_G.Auto_Farm_Mastery_Fruit = value    
	_G.Settings.Auto_Farm_Mastery_Fruit = value
	SaveSettings()
	StopTween(_G.Auto_Farm_BF_Mastery)
end)

function EquipBloxFruit()
	for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
		if v.ToolTip == "Blox Fruit" then
			if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
				EquipWeapon(v.Name)
			end
		end
	end
end
local gg = getrawmetatable(game)
local old = gg.__namecall
setreadonly(gg,false)
gg.__namecall = newcclosure(function(...)
	local method = getnamecallmethod()
	local args = {...}
	if tostring(method) == "FireServer" then
		if tostring(args[1]) == "RemoteEvent" then
			if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
				if _G.Auto_Farm_Mastery_Fruit then
					args[2] = FrunitPosition
					return old(unpack(args))
				end
			end
		end
	end
	return old(...)
end)
spawn(function()
	while wait() do
		local MyLevel = game.Players.LocalPlayer.Data.Level.Value
		local QuestC = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest
		pcall(function()
			if _G.Auto_Farm_Mastery_Fruit then
				if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, QuestCheck()[6]) then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
				end
				if QuestC.Visible == true then
					if game:GetService("Workspace").Enemies:FindFirstChild(QuestCheck()[3]) then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if string.find(v.Name,QuestCheck()[3]) then
								if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
									repeat task.wait()
										if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, QuestCheck()[6]) then
											game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
										else
											if v.Humanoid.Health <= v.Humanoid.MaxHealth * _G.Settings.HealthMs/100 then 
												_G.UseSkill = true
												EquipBloxFruit()
												getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
												PosMon = v.HumanoidRootPart.CFrame
												FrunitPosition = v.HumanoidRootPart.CFrame.Position
												v.HumanoidRootPart.Size = Vector3.new(60,60,60)
												v.HumanoidRootPart.CanCollide = false
												v.Humanoid.WalkSpeed = 0
												v.Head.CanCollide = false
												BringMobFarm = true
												v.HumanoidRootPart.TranAsparency = 1
											else
												_G.UseSkill = false
												PosMon = v.HumanoidRootPart.CFrame
												v.HumanoidRootPart.Size = Vector3.new(60,60,60)
												v.HumanoidRootPart.CanCollide = false
												v.Head.CanCollide = false
												BringMobFarm = true
												EquipWeapon(_G.Select_Weapon)
												v.HumanoidRootPart.Transparency = 1
												getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
												AutoHaki()
												Cilck()
											end
										end
									until not _G.Auto_Farm_Mastery_Fruit or not v.Parent or v.Humanoid.Health <= 0 or QuestC.Visible == false or not v:FindFirstChild("HumanoidRootPart")
								end
							end
						end
					else
						_G.UseSkill = false
						UnEquipWeapon(_G.Select_Weapon)
						if _G.Auto_CFrame then
							getgenv().ToTarget(QuestCheck()[7][SetCFarme] * MethodFarm)
							if (QuestCheck()[7][SetCFarme].Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
								if SetCFarme == nil or SetCFarme == '' then
									SetCFarme = 1
									print(SetCFarme)
								elseif SetCFarme >= #QuestCheck()[7] then
									SetCFarme = 1
									print(SetCFarme)
								end
								SetCFarme =  SetCFarme + 1

								print(SetCFarme)
								wait(0.5)
							end
						end
					end
				else
					getgenv().ToTarget(QuestCheck()[2])
					if (QuestCheck()[2].Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1 then
						BringMobFarm = false
						wait(0.2)
						game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("StartQuest", QuestCheck()[4], QuestCheck()[1]) wait(0.5) 
						getgenv().ToTarget(QuestCheck()[7][1] * MethodFarm)
					end
				end
			end
		end)
	end
end)

Mastery:AddToggle('Auto_Farm_Gun_Mastery', {
	Text = "Auto Farm Gun Mastery",
	Tooltip = "Auto_Farm_Gun_Mastery",
	Default = _G.Settings.Auto_Farm_Mastery_Gun,
})

Toggles.Auto_Farm_Gun_Mastery:OnChanged(function(value)
	_G.Auto_Farm_Mastery_Gun = value
	_G.Settings.Auto_Farm_Mastery_Gun = value
	StopTween(_G.Auto_Farm_Mastery_Gun)
	SaveSettings()
end)

spawn(function()
	local gt = getrawmetatable(game)
	local old = gt.__namecall
	setreadonly(gt,false)
	gt.__namecall = newcclosure(function(...)
		local args = {...}
		if getnamecallmethod() == "InvokeServer" then 
			if _G.SelectWeaponGun then
				if _G.SelectWeaponGun == "Soul Guitar" then
					if tostring(args[2]) == "TAP" then
						if  _G.Auto_Farm_Mastery_Gun and _G.UseSkill then
							args[3] = PositionSkillMasteryGun
						end
					end
				end
			end
		end
		return old(unpack(args))
	end)
	setreadonly(gt,true)
end)
spawn(function()
	while wait() do
		for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
			if v:IsA("Tool") then
				if v.ToolTip == "Gun" then
					_G.SelectWeaponGun = v.Name
				end
			end
		end
		for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do  
			if v:IsA("Tool") then
				if v.ToolTip == "Gun" then
					_G.SelectWeaponGun = v.Name
				end
			end
		end
	end
end)
spawn(function()
	while wait() do
		local MyLevel = game.Players.LocalPlayer.Data.Level.Value
		local QuestC = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest
		pcall(function()
			if _G.Auto_Farm_Mastery_Gun then
				if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, QuestCheck()[6]) then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
				end
				if QuestC.Visible == true then
					if game:GetService("Workspace").Enemies:FindFirstChild(QuestCheck()[3]) then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if string.find(v.Name,QuestCheck()[3]) then
								if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
									PosMon = v.HumanoidRootPart.CFrame
									MonHumanoidRootPart = v.HumanoidRootPart
									PositionSkillMasteryGun = v.HumanoidRootPart.CFrame.Position
									repeat task.wait()
										v.HumanoidRootPart.CFrame = PosMon
										if v.Humanoid.Health <= v.Humanoid.MaxHealth * _G.Settings.HealthMs/100 then 
											_G.UseSkill = true
											getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
											v.HumanoidRootPart.Size = Vector3.new(120,120,120)
											v.HumanoidRootPart.CanCollide = false
											v.Head.CanCollide = false
											BringMobFarm = true
											v.HumanoidRootPart.Transparency = 1
											EquipWeapon(_G.SelectWeaponGun)
										else
											_G.UseSkill = false
											v.HumanoidRootPart.Size = Vector3.new(120,120,120)
											v.HumanoidRootPart.CanCollide = false
											v.Head.CanCollide = false
											BringMobFarm = true
											EquipWeapon(_G.Select_Weapon)
											v.HumanoidRootPart.Transparency = 1
											getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
											AutoHaki()
											Cilck()
										end
									until not _G.Auto_Farm_Mastery_Gun or not v.Parent or v.Humanoid.Health <= 0 or QuestC.Visible == false or not v:FindFirstChild("HumanoidRootPart")
								end
							end
						end
					else
						_G.UseSkill = false
						UnEquipWeapon(_G.Select_Weapon)
						if _G.Auto_CFrame then
							getgenv().ToTarget(QuestCheck()[7][SetCFarme] * MethodFarm)
							if (QuestCheck()[7][SetCFarme].Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
								if SetCFarme == nil or SetCFarme == '' then
									SetCFarme = 1
									print(SetCFarme)
								elseif SetCFarme >= #QuestCheck()[7] then
									SetCFarme = 1
									print(SetCFarme)
								end
								SetCFarme =  SetCFarme + 1

								print(SetCFarme)
								wait(0.5)
							end
						end
					end
				else
					getgenv().ToTarget(QuestCheck()[2])
					if (QuestCheck()[2].Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1 then
						BringMobFarm = false
						wait(0.2)
						game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("StartQuest", QuestCheck()[4], QuestCheck()[1]) wait(0.5)
						getgenv().ToTarget(QuestCheck()[7][1] * MethodFarm)
					end
				end
			end
		end)
	end
end)
spawn(function()
	while wait() do
		if _G.Auto_Farm_Mastery_Gun and _G.UseSkill == true then
			game:GetService("VirtualUser"):CaptureController()
			game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 672))
			local args = {
				[1] = PositionSkillMasteryGun,
				[2] = MonHumanoidRootPart
			}
			game:GetService("Players").LocalPlayer.Character[_G.SelectWeaponGun].RemoteFunctionShoot:InvokeServer(unpack(args))
		end
	end
end)
local gg = getrawmetatable(game)
local old = gg.__namecall
setreadonly(gg,false)
gg.__namecall = newcclosure(function(...)
	local method = getnamecallmethod()
	local args = {...}
	if tostring(method) == "FireServer" then
		if tostring(args[1]) == "RemoteEvent" then
			if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
				if _G.Auto_Farm_Mastery_Gun then
					args[2] = PositionSkillMasteryGun
					return old(unpack(args))
				end
			end
		end
	end
	return old(...)
end)


Mastery:AddDropdown('Select_Kill', {
	Values = { "10", "25", "50", "100" },
	Default = _G.Settings.HealthMs,
	Multi = false,
	Text = 'Select Health Mob',
	Tooltip = 'Select Health Mob',
})
Options.Select_Kill:OnChanged(function(value)
	_G.Settings.HealthMs = value
	SaveSettings()
end)

if World1 then

	local World = Tabs.Main:AddLeftGroupbox('New World')

	World:AddToggle('AutoNewWorld', {
		Text = 'Auto New World',
		Default = _G.Settings.Auto_New_World,
		Tooltip = 'Auto New World',
	})

	Toggles.AutoNewWorld:OnChanged(function(value)
		_G.Auto_New_World = value
		_G.Settings.Auto_New_World = value
		SaveSettings()
		StopTween(_G.Auto_New_World)
	end)

	spawn(function()
		while wait() do
			if _G.Auto_New_World then
				pcall(function()
					if game.Players.LocalPlayer.Data.Level.Value >= 700 and World1 then
						_G.Auto_Farm_Level = false
						if game.Workspace.Map.Ice.Door.CanCollide == true and game.Workspace.Map.Ice.Door.Transparency == 0 then
							repeat wait() getgenv().ToTarget(CFrame.new(4851.8720703125, 5.6514348983765, 718.47094726563)) until (CFrame.new(4851.8720703125, 5.6514348983765, 718.47094726563).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_New_World
							wait(1)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("DressrosaQuestProgress","Detective")
							EquipWeapon("Key")
							local pos2 = CFrame.new(1347.7124, 37.3751602, -1325.6488)
							repeat wait() getgenv().ToTarget(pos2) until (pos2.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_New_World
							wait(3)
						elseif game.Workspace.Map.Ice.Door.CanCollide == false and game.Workspace.Map.Ice.Door.Transparency == 1 then
							if game:GetService("Workspace").Enemies:FindFirstChild("Ice Admiral") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if string.find(v.Name,"Ice Admiral") and v.Humanoid.Health > 0 then
										repeat wait()
											AutoHaki()
											EquipWeapon(_G.Select_Weapon)
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(60,60,60)
											v.HumanoidRootPart.Transparency = 1
											getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
											game:GetService("VirtualUser"):CaptureController()
											game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 870),workspace.CurrentCamera.CFrame)
										until v.Humanoid.Health <= 0 or not v.Parent or not _G.Auto_New_World
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
									end
								end
							else
								getgenv().ToTarget(CFrame.new(1347.7124, 37.3751602, -1325.6488))
							end
						else
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
						end
					end
				end)
			end
		end
	end)
	

	local FuncrionWorld1 = Tabs.Main:AddLeftGroupbox('Misc')

	FuncrionWorld1:AddToggle('Auto_Saber', {
		Text = 'Auto Saber',
		Default = _G.Settings.Auto_Saber,
		Tooltip = 'Auto Saber',
	})

	Toggles.Auto_Saber:OnChanged(function(value)
		_G.Auto_Saber = value
		_G.Settings.Auto_Saber = value
		SaveSettings()
		StopTween(_G.Auto_Saber)
	end)

	FuncrionWorld1:AddToggle('Auto_Saber_Hop', {
		Text = 'Auto Saber Hop',
		Default = _G.Settings.Auto_Saber_Hop,
		Tooltip = 'Auto Saber',
	})

	Toggles.Auto_Saber_Hop:OnChanged(function(value)
		_G.Auto_Saber_Hop = value
		_G.Settings.Auto_Saber_Hop = value
		SaveSettings()
	end)

	spawn(function()
		while task.wait() do
			pcall(function()
				if _G.Auto_Saber and game.Players.LocalPlayer.Data.Level.Value >= 200 and Check_Sword("Saber") == nil and World1 then
					_G.Auto_Farm_Level = false
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
					if game:GetService("Workspace").Map.Jungle.Final.Part.Transparency == 0 then
						if game:GetService("Workspace").Map.Jungle.QuestPlates.Door.Transparency == 0 then
							if (CFrame.new(-1480.06018, 47.9773636, 4.53454018, -0.386713833, 1.11673025e-07, 0.922199786, 7.96717785e-08, 1, -8.76847395e-08, -0.922199786, 3.95643944e-08, -0.386713833).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 100 then
								getgenv().ToTarget(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame)
								task.wait(1)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Map.Jungle.QuestPlates.Plate1.Button.CFrame
								task.wait(1)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Map.Jungle.QuestPlates.Plate2.Button.CFrame
								task.wait(1)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Map.Jungle.QuestPlates.Plate3.Button.CFrame
								task.wait(1)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Map.Jungle.QuestPlates.Plate4.Button.CFrame
								task.wait(1)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Map.Jungle.QuestPlates.Plate5.Button.CFrame
								task.wait(1) 
							end
							local CFrameSaber = CFrame.new(-1480.06018, 47.9773636, 4.53454018, -0.386713833, 1.11673025e-07, 0.922199786, 7.96717785e-08, 1, -8.76847395e-08, -0.922199786, 3.95643944e-08, -0.386713833)
							if _G.Auto_Farm_Level and _G.Auto_Saber and (CFrameSaber.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1200 then
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
								getgenv().ToTarget(CFrameSaber)
							end
							getgenv().ToTarget(CFrameSaber)
						else
							if game:GetService("Workspace").Map.Desert.Burn.Part.Transparency == 0 then
								if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Torch") then
									EquipWeapon("Torch")
									getgenv().ToTarget(CFrame.new(1113.7229, 5.04679585, 4350.33691, -0.541527212, 5.27007726e-09, 0.840683222, 8.74004868e-08, 1, 5.00303372e-08, -0.840683222, 1.00568911e-07, -0.541527212))
									UnEquipWeapon("Torch")
									EquipWeapon("Torch")
									task.wait(0.5)
								else
									getgenv().ToTarget(CFrame.new(-1610.56824, 12.1773882, 162.830322, -0.907543361, -2.88120088e-08, -0.419958383, -4.66550922e-08, 1, 3.22163096e-08, 0.419958383, 4.88308949e-08, -0.907543361))                 
								end
							else
								if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan") ~= 0 then
									game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","GetCup")
									task.wait(0.5)
									EquipWeapon("Cup")
									task.wait(0.5)
									game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","FillCup",game:GetService("Players").LocalPlayer.Character.Cup)
									task.wait(0)
									game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan") 
								else
									if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == nil then
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon")
									elseif  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 0 then
										if game:GetService("Workspace").Enemies:FindFirstChild("Mob Leader") or game:GetService("ReplicatedStorage"):FindFirstChild("Mob Leader") then
											for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
												if string.find(v.Name,"Mob Leader") then
													if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
														repeat task.wait()
															EquipWeapon(_G.Select_Weapon)
															v.HumanoidRootPart.CanCollide = false
															v.Humanoid.WalkSpeed = 0
															v.Head.CanCollide = false
															v.HumanoidRootPart.Size = Vector3.new(100,100,100)
															v.HumanoidRootPart.Transparency = 1
															EquipWeapon(_G.Select_Weapon)
															getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
														until v.Humanoid.Health <= 0 or _G.AutoSaber == false
													end
												end
											end
											for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
												if v.Name == "Mob Leader" then
													if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
														getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
													end
												else
													if _G.Auto_Saber_Hop then
														wait(2.5)
														Hop()
													end
												end
											end		
										end
									elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 1 then
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon")
										task.wait(0.5)
										EquipWeapon("Relic")
										task.wait(0.5)
										getgenv().ToTarget(CFrame.new(-1406.37512, 29.9773273, 4.45027685, 0.877344251, -3.82776442e-08, 0.479861468, 4.93218133e-09, 1, 7.07504668e-08, -0.479861468, -5.9705755e-08, 0.877344251))
									end
								end
							end
						end
					else
						if game:GetService("Workspace").Enemies:FindFirstChild("Saber Expert") or game:GetService("ReplicatedStorage"):FindFirstChild("Saber Expert") then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if string.find(v.Name,"Saber Expert") then
									repeat task.wait()
										EquipWeapon(_G.Select_Weapon)
										v.HumanoidRootPart.Size = Vector3.new(60,60,60)
										v.HumanoidRootPart.Transparency = 1
										getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
										Cilck()
									until v.Humanoid.Health <= 0 or _G.AutoSaber == false
									_G.Auto_Saber = false
									if _G.Settings.Auto_Farm_Level then
										_G.Auto_Farm_Level = true
									end
									if v.Humanoid.Health <= 0 then
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","PlaceRelic")
									end
								end
							end
						else 
							if _G.Auto_Saber_Hop then
								wait(2.5)
								Hop()
							end
						end
					end
				end
			end)
		end
	end)

	FuncrionWorld1:AddToggle('Auto_Pole', {
		Text = 'Auto Pole',
		Default = _G.Settings.Auto_Pole,
		Tooltip = 'Auto Pole',
	})

	Toggles.Auto_Pole:OnChanged(function(value)
		_G.Auto_Pole = value
		_G.Settings.Auto_Pole = value
		SaveSettings()
		StopTween(_G.Auto_Pole)
	end)

	FuncrionWorld1:AddToggle('Auto_Pole_Hop', {
		Text = 'Auto Pole Hop',
		Default = _G.Settings.Auto_Pole_V1_Hop,
		Tooltip = 'Auto Pole Hop',
	})

	Toggles.Auto_Pole_Hop:OnChanged(function(value)
		_G.Auto_Pole_Hop = value
		_G.Settings.Auto_Pole_V1_Hop = value
		SaveSettings()
	end)

	spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Pole and game.ReplicatedStorage:FindFirstChild("Thunder God") or game.Workspace.Enemies:FindFirstChild("Thunder God") then
					if game.Workspace.Enemies:FindFirstChild("Thunder God") then
						for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
							if _G.Auto_Pole and string.find(v.Name,"Thunder God") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
								repeat wait()  
									AutoHaki()
									EquipWeapon(_G.Select_Weapon)
									getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
									game:GetService'VirtualUser':CaptureController()
									game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
								until not _G.Auto_Pole or v.Humanoid.Health <= 0 or not v.Parent
							end
						end
					else
						if _G.Auto_Pole_Hop then
							wait(2.5)
							Hop()
						end
						getgenv().ToTarget(CFrame.new(-7900.66406, 5606.90918, -2267.46436))
					end
				else
					if _G.Auto_Pole_Hop then
						wait(2.5)
						Hop()
					end
				end
			end)
		end
	end)

	FuncrionWorld1:AddToggle('Auto_Buy_Ablility', {
		Text = 'Auto Buy Ablility',
		Default = _G.Settings.Auto_Buy_Ablility,
		Tooltip = 'Auto Buy Ablility',
	})

	Toggles.Auto_Buy_Ablility:OnChanged(function(value)
		_G.Auto_Buy_Ablility = value
		_G.Settings.Auto_Buy_Ablility = value
		SaveSettings()
	end)


	task.spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Buy_Ablility then
					local Beli = game:GetService("Players").LocalPlayer.Data.Beli.Value
					local BusoCheck = false
					local SoruCheck = false
					local GeppoCheck = false
					local KenCheck = false
					if Beli >= 885000 then
						repeat wait() 
							local args = {
								[1] = "BuyHaki",
								[2] = "Buso"
							}

							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
							BusoCheck = true
							local args = {
								[1] = "BuyHaki",
								[2] = "Geppo"
							}
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
							GeppoCheck = true
							local args = {
								[1] = "BuyHaki",
								[2] = "Soru"
							}
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
							SoruCheck = true
							local args = {
								[1] = "KenTalk",
								[2] = "Start"
							}

							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

							local args = {
								[1] = "KenTalk",
								[2] = "Buy"
							}

							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
							KenCheck = true
						until not BusoCheck and not GeppoCheck and not SoruCheck and not KenCheck or not _G.Auto_Buy_Ablility
					end
				end
			end)
		end
	end)
elseif World2 then

	local World = Tabs.Main:AddLeftGroupbox('World Tab')

	World:AddToggle('AutoThirdWorld', {
		Text = 'Auto Third World',
		Default = _G.Settings.Auto_Third_World,
		Tooltip = 'Auto Third World',
	})

	Toggles.AutoThirdWorld:OnChanged(function(value)
		_G.Auto_Third_World = value
		_G.Settings.Auto_Third_World = value
		SaveSettings()  
		StopTween(_G.Auto_Third_World)
	end)

	spawn(function()
		while wait() do
			if _G.Auto_Third_World and World2 then
				pcall(function()
					local QuestC = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest
					local MyLevel = game.Players.LocalPlayer.Data.Level.Value
					if game:GetService("Players").LocalPlayer.Data.Level.Value >= 1500 then
						if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 3 then
							if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetUnlockables").FlamingoAccess ~= nil then							
								if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ZQuestProgress","Check") == 0 then
									game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ZQuestProgress","Begin")
									if game:GetService("Workspace").Enemies:FindFirstChild("rip_indra") then
										for i, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
											if string.find(v.Name,"rip_indra") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
												repeat wait()
													v.HumanoidRootPart.Size = Vector3.new(60,60,60)
													v.HumanoidRootPart.CanCollide = false
													v.Head.CanCollide = false
													EquipWeapon(_G.Select_Weapon)
													v.HumanoidRootPart.Transparency = 1
													getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
													AutoHaki()
													if (v.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
														game:GetService("VirtualUser"):CaptureController()
														game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
													end
												until not _G.Auto_Third_World or not v.Parent or v.Humanoid.Health <= 0 
												repeat wait() game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou") until LOL == "LOLOL"
											end
										end
									else
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ZQuestProgress","Check")
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ZQuestProgress","Begin")
									end
								else
									game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
									if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ZQuestProgress","Check") ~= 0 then
										if game:GetService("Workspace").Enemies:FindFirstChild("Don Swan") or game.ReplicatedStorage:FindFirstChild("Don Swan") then
											for i, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
												if string.find(v.Name,"Don Swan") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
													repeat wait()
														v.HumanoidRootPart.Size = Vector3.new(60,60,60)
														v.HumanoidRootPart.CanCollide = false
														v.Head.CanCollide = false
														EquipWeapon(_G.Select_Weapon)
														v.HumanoidRootPart.Transparency = 1
														getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
														AutoHaki()
														if (v.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
															game:GetService("VirtualUser"):CaptureController()
															game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
														end
													until not _G.Auto_Third_World or not v.Parent or v.Humanoid.Health <= 0 
												else
													getgenv().ToTarget(2207.38672, 15.1333914, 883.866394, 0.931175113, 3.09244754e-08, -0.364572287, 1.20643637e-08, 1, 1.15638279e-07, 0.364572287, -1.12077821e-07, 0.931175113)
												end
											end
										else
											getgenv().ToTarget(2207.38672, 15.1333914, 883.866394, 0.931175113, 3.09244754e-08, -0.364572287, 1.20643637e-08, 1, 1.15638279e-07, 0.364572287, -1.12077821e-07, 0.931175113)
										end
									end
								end
							else
								for i,v in next,game.ReplicatedStorage:WaitForChild("Remotes").CommF_:InvokeServer("GetFruits") do
									if v.Price >= 1000000 then  
										table.insert(FruitPrice,v.Name)
									end
								end
								for i,v in pairs(game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("getInventoryFruits")) do
									for _,x in pairs(v) do
										if _ == "Name" then 
											table.insert(FruitStore,x)
										end
									end
								end
								function CheckFruit()
									local player = game.Players.LocalPlayer
									for _, tool in pairs(player.Backpack:GetDescendants()) do
										if tool:FindFirstChild("Fruit") then
											return tool
										end
									end
								end
								function AddToNpc()
									if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(CheckFruit())) then
										wait(1.5)
										EquipWeapon(tostring(CheckFruit()))
										wait(0.5)
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TalkTrevor","1")
										wait(0.5)
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TalkTrevor","2")
										wait(0.5)
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TalkTrevor","1")
										wait(0.5)
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TalkTrevor","3")
									end
								end
								for _,y in pairs(FruitPrice) do
									for _,z in pairs(FruitStore) do
										if y == z and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetUnlockables").FlamingoAccess == nil then
											local args = {
												[1] = "LoadFruit",
												[2] = tostring(y)
											}
	
											game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
											AddToNpc()
										end
									end 
								end
							end
						else
							if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 0 then
								_G.Auto_Farm_Level = false
								if QuestC.Visible == true then
									if game:GetService("Workspace").Enemies:FindFirstChild("Swan Pirate") then
										for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
											if string.find(v.Name,"Swan Pirate") then
												if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") then
													repeat task.wait()
														if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Swan Pirate") then
															game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
														else
															PosMon = v.HumanoidRootPart.CFrame
															v.HumanoidRootPart.Size = Vector3.new(60,60,60)
															v.HumanoidRootPart.CanCollide = false
															v.Humanoid.WalkSpeed = 0
															v.Head.CanCollide = false
															BringMobFarm = true
															EquipWeapon(_G.Select_Weapon)
															v.HumanoidRootPart.Transparency = 1
															getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
															Cilck()
														end
													until not _G.Auto_Third_World or not v.Parent or v.Humanoid.Health <= 0 or QuestC.Visible == false or not v:FindFirstChild("HumanoidRootPart")
												end
											end
										end
									else
										BringMobFarm = false
										for i,v in pairs(workspace._WorldOrigin.EnemySpawns:GetChildren()) do
											if v.Name == "Swan Pirate" then local CFrameEnemySpawns = v.CFrame  wait(0.5)
												getgenv().ToTarget(CFrameEnemySpawns * MethodFarm)
											end
										end
									end
								else
									repeat wait() getgenv().ToTarget(CFrame.new(-461.533203, 72.3478546, 300.311096, 0.050853312, -0, -0.998706102, 0, 1, -0, 0.998706102, 0, 0.050853312)) until (CFrame.new(-461.533203, 72.3478546, 300.311096, 0.050853312, -0, -0.998706102, 0, 1, -0, 0.998706102, 0, 0.050853312).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 20 or not _G.Auto_Bartilo_Quest
									if (CFrame.new(-461.533203, 72.3478546, 300.311096, 0.050853312, -0, -0.998706102, 0, 1, -0, 0.998706102, 0, 0.050853312).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1 then
										BringMobFarm = false
										game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("StartQuest", "BartiloQuest", 1)
									end
								end
							elseif  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 1 then
								_G.Auto_Farm_Level = false
								if game:GetService("Workspace").Enemies:FindFirstChild("Jeremy") then
									for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
										if string.find(v.Name,"Jeremy") then
											if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") then
												repeat task.wait()
													PosMon = v.HumanoidRootPart.CFrame
													v.HumanoidRootPart.Size = Vector3.new(60,60,60)
													v.HumanoidRootPart.CanCollide = false
													v.Humanoid.WalkSpeed = 0
													v.Head.CanCollide = false
													BringMobFarm = true
													EquipWeapon(_G.Select_Weapon)
													v.HumanoidRootPart.Transparency = 1
													getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
													Cilck()
												until not _G.Auto_Third_World or not v.Parent or v.Humanoid.Health <= 0 or QuestC.Visible == false or not v:FindFirstChild("HumanoidRootPart")
											end
										end
									end
								else
									getgenv().ToTarget(CFrame.new(2158.97412, 449.056244, 705.411682, -0.754199564, -4.17389057e-09, -0.656645238, -4.47752875e-08, 1, 4.50709301e-08, 0.656645238, 6.3393955e-08, -0.754199564))
								end
							elseif  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 2 then
								repeat wait() getgenv().ToTarget(CFrame.new(-1830.83972, 10.5578213, 1680.60229, 0.979988456, -2.02152783e-08, -0.199054286, 2.20792113e-08, 1, 7.1442483e-09, 0.199054286, -1.13962431e-08, 0.979988456)) until (CFrame.new(-1830.83972, 10.5578213, 1680.60229, 0.979988456, -2.02152783e-08, -0.199054286, 2.20792113e-08, 1, 7.1442483e-09, 0.199054286, -1.13962431e-08, 0.979988456).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1 or _G.Auto_Third_World == false
								wait(0.7)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate1.CFrame
								wait(0.7)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate2.CFrame
								wait(0.7)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate3.CFrame
								wait(0.7)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate4.CFrame
								wait(0.7)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate5.CFrame
								wait(0.7)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate6.CFrame
								wait(0.7)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate7.CFrame
								wait(0.7)
								game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate8.CFrame
							end
						end
					end
				end)
			end
		end
	end)

	local Misc2 = Tabs.Main:AddLeftGroupbox('Misc')

	Misc2:AddToggle('Auto_Bartilo_Quest', {
		Text = 'Auto Bartilo Quest',
		Default = _G.Settings.Auto_Bartilo_Quest,
		Tooltip = 'Auto Bartilo Quest',
	})

	Toggles.Auto_Bartilo_Quest:OnChanged(function(value)
		_G.Auto_Bartilo_Quest = value
		_G.Settings.Auto_Bartilo_Quest = value
		SaveSettings()
		StopTween(_G.Auto_Bartilo_Quest)
	end)

	spawn(function()
		while wait() do
			local MyLevel = game.Players.LocalPlayer.Data.Level.Value
			local QuestC = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest
			pcall(function()
				if _G.Auto_Bartilo_Quest and MyLevel >= 850 then
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 0 then
						_G.Auto_Farm_Level = false
						if QuestC.Visible == true then
							if game:GetService("Workspace").Enemies:FindFirstChild("Swan Pirate") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if string.find(v.Name,"Swan Pirate") then
										if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") then
											repeat task.wait()
												if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Swan Pirate") then
													game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
												else
													PosMon = v.HumanoidRootPart.CFrame
													v.HumanoidRootPart.Size = Vector3.new(60,60,60)
													v.HumanoidRootPart.CanCollide = false
													v.Humanoid.WalkSpeed = 0
													v.Head.CanCollide = false
													BringMobFarm = true
													EquipWeapon(_G.Select_Weapon)
													v.HumanoidRootPart.Transparency = 1
													getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
													Cilck()
												end
											until not _G.Auto_Bartilo_Quest or not v.Parent or v.Humanoid.Health <= 0 or QuestC.Visible == false or not v:FindFirstChild("HumanoidRootPart")
										end
									end
								end
							else
								BringMobFarm = false
								for i,v in pairs(workspace._WorldOrigin.EnemySpawns:GetChildren()) do
									if v.Name == "Swan Pirate" then local CFrameEnemySpawns = v.CFrame  wait(0.5)
										getgenv().ToTarget(CFrameEnemySpawns * MethodFarm)
									end
								end
							end
						else
							repeat wait() getgenv().ToTarget(CFrame.new(-461.533203, 72.3478546, 300.311096, 0.050853312, -0, -0.998706102, 0, 1, -0, 0.998706102, 0, 0.050853312)) until (CFrame.new(-461.533203, 72.3478546, 300.311096, 0.050853312, -0, -0.998706102, 0, 1, -0, 0.998706102, 0, 0.050853312).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 20 or not _G.Auto_Bartilo_Quest
							if (CFrame.new(-461.533203, 72.3478546, 300.311096, 0.050853312, -0, -0.998706102, 0, 1, -0, 0.998706102, 0, 0.050853312).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1 then
								BringMobFarm = false
								game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("StartQuest", "BartiloQuest", 1)
							end
						end
					elseif  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 1 then
						_G.Auto_Farm_Level = false
						if game:GetService("Workspace").Enemies:FindFirstChild("Jeremy") then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if string.find(v.Name,"Jeremy") then
									if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") then
										repeat task.wait()
											PosMon = v.HumanoidRootPart.CFrame
											v.HumanoidRootPart.Size = Vector3.new(60,60,60)
											v.HumanoidRootPart.CanCollide = false
											v.Humanoid.WalkSpeed = 0
											v.Head.CanCollide = false
											BringMobFarm = true
											EquipWeapon(_G.Select_Weapon)
											v.HumanoidRootPart.Transparency = 1
											getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
											Cilck()
										until not _G.Auto_Bartilo_Quest or not v.Parent or v.Humanoid.Health <= 0 or QuestC.Visible == false or not v:FindFirstChild("HumanoidRootPart")
									end
								end
							end
						else
							getgenv().ToTarget(CFrame.new(2158.97412, 449.056244, 705.411682, -0.754199564, -4.17389057e-09, -0.656645238, -4.47752875e-08, 1, 4.50709301e-08, 0.656645238, 6.3393955e-08, -0.754199564))
						end
					elseif  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 2 then
						repeat wait() getgenv().ToTarget(CFrame.new(-1830.83972, 10.5578213, 1680.60229, 0.979988456, -2.02152783e-08, -0.199054286, 2.20792113e-08, 1, 7.1442483e-09, 0.199054286, -1.13962431e-08, 0.979988456)) until (CFrame.new(-1830.83972, 10.5578213, 1680.60229, 0.979988456, -2.02152783e-08, -0.199054286, 2.20792113e-08, 1, 7.1442483e-09, 0.199054286, -1.13962431e-08, 0.979988456).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1 or _G.Auto_Bartilo_Quest == false
						wait(0.7)
						game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate1.CFrame
						wait(0.7)
						game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate2.CFrame
						wait(0.7)
						game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate3.CFrame
						wait(0.7)
						game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate4.CFrame
						wait(0.7)
						game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate5.CFrame
						wait(0.7)
						game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate6.CFrame
						wait(0.7)
						game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate7.CFrame
						wait(0.7)
						game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = workspace.Map.Dressrosa.BartiloPlates.Plate8.CFrame
						wait(2.5)
					end
				end
			end)
		end
	end)


	Misc2:AddToggle('Auto_Evo_Race_V2', {
		Text = 'Auto Evo Race V2',
		Default = _G.Settings.Auto_Evo_Race_V2,
		Tooltip = 'Auto Evo Race V2',
	})

	Toggles.Auto_Evo_Race_V2:OnChanged(function(value)
		_G.Auto_Evo_Race_V2 = value
		_G.Settings.Auto_Evo_Race_V2 = value
		SaveSettings()
		StopTween(_G.Auto_Evo_Race_V2)
	end)


	spawn(function()
		pcall(function()
			while wait() do
				if  _G.Auto_Evo_Race_V2 then
					if not game:GetService("Players").LocalPlayer.Data.Race:FindFirstChild("Evolved") then
						if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","1") == 0 then
							getgenv().ToTarget(CFrame.new(-2779.83521, 72.9661407, -3574.02002, -0.730484903, 6.39014104e-08, -0.68292886, 3.59963224e-08, 1, 5.50667032e-08, 0.68292886, 1.56424669e-08, -0.730484903))
							if (Vector3.new(-2779.83521, 72.9661407, -3574.02002) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4 then
								wait(1.3)
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","2")
							end
						elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","1") == 1 then
							pcall(function()
								if not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 1") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 1") then
									getgenv().ToTarget(game:GetService("Workspace").Flower1.CFrame)
								elseif not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 2") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 2") then
									getgenv().ToTarget(game:GetService("Workspace").Flower2.CFrame)
								elseif not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 3") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 3") then
									if game:GetService("Workspace").Enemies:FindFirstChild("Swan Pirate") then
										for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
											if string.find(v.Name,"Swan Pirate") then
												repeat wait()
													AutoHaki()
													EquipWeapon(_G.Select_Weapon)
													getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
													v.HumanoidRootPart.CanCollide = false
													v.HumanoidRootPart.Size = Vector3.new(50,50,50)
													PosMonEvo = v.HumanoidRootPart.CFrame
													StartEvoMagnet = true
												until game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 3") or not v.Parent or v.Humanoid.Health <= 0 or _G.Auto_Evo_Race_V2 == false
												StartEvoMagnet = false
											end
										end
									else
										StartEvoMagnet = false
										getgenv().ToTarget(CFrame.new(980.0985107421875, 121.331298828125, 1287.2093505859375))
									end
								end
							end)
						elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","1") == 2 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","3")
						end
					end
				end
			end
		end)
	end)

	
	Misc2:AddToggle('Auto_Ectoplasm', {
		Text = 'Auto Ectoplasm',
		Default = _G.Settings.Auto_Farm_Ectoplasm,
		Tooltip = 'Auto Ectoplasm',
	})

	Toggles.Auto_Ectoplasm:OnChanged(function(value)
		_G.Auto_Ectoplasm = value
		_G.Settings.Auto_Farm_Ectoplasm = value
		SaveSettings()
		StopTween(_G.Auto_Ectoplasm)
	end)

	task.spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Ectoplasm then
					if game:GetService("Workspace").Enemies:FindFirstChild("Ship Deckhand") or game:GetService("Workspace").Enemies:FindFirstChild("Ship Engineer") or game:GetService("Workspace").Enemies:FindFirstChild("Ship Steward") or game:GetService("Workspace").Enemies:FindFirstChild("Ship Officer") or game:GetService("Workspace").Enemies:FindFirstChild("Arctic Warrior") then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if string.find(v.Name,"Ship Deckhand") or string.find(v.Name,"Ship Engineer") or string.find(v.Name,"Ship Steward") or string.find(v.Name,"Ship Officer") or string.find(v.Name,"Arctic Warrior") then
								if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
									repeat wait()
										MagnetEctoplasm = true
										AutoHaki()
										EquipWeapon(_G.Select_Weapon)
										PosMon = v.HumanoidRootPart.CFrame
										v.HumanoidRootPart.Size = Vector3.new(60,60,60)
										v.Humanoid.JumpPower = 0
										v.Humanoid.WalkSpeed = 0
										v.HumanoidRootPart.CanCollide = false
										v.Humanoid:ChangeState(11)
										getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until not _G.Auto_Ectoplasm or not v.Parent or v.Humanoid.Health <= 0
								end
							else
								MagnetEctoplasm = false
								getgenv().ToTarget(CFrame.new(904.4072265625, 181.05767822266, 33341.38671875))
							end
						end
					else
						MagnetEctoplasm = false
						local Distance = (Vector3.new(904.4072265625, 181.05767822266, 33341.38671875) - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
						if Distance > 20000 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
						end
						getgenv().ToTarget(CFrame.new(904.4072265625, 181.05767822266, 33341.38671875))
					end
				end
			end)
		end
	end)

	Misc2:AddToggle('Auto_True_Triple_Katana', {
		Text = 'Auto True Triple Katana',
		Default = _G.Settings.Auto_True_Triple_Katana,
		Tooltip = 'Auto True Triple Katana',
	})

	Toggles.Auto_True_Triple_Katana:OnChanged(function(value)
		_G.Auto_True_Triple_Katana = value
		_G.Settings.Auto_True_Triple_Katana = value
		StopTween(_G.Auto_True_Triple_Katana)
		SaveSettings()
	end)


	task.spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_True_Triple_Katana then
					local string_1 = "MysteriousMan";
					local string_2 = "2";
					local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
					Target:InvokeServer(string_1, string_2);  
				end
			end)
		end
	end)

	Misc2:AddToggle('Auto_Buy_Legendary_Sword', {
		Text = 'Auto Buy Legendary Sword',
		Default = _G.Settings.Auto_Buy_Legendary_Sword,
		Tooltip = 'Auto Buy Legendary Sword',
	})

	Toggles.Auto_Buy_Legendary_Sword:OnChanged(function(value)
		_G.Auto_Buy_Legendary_Sword = value
		_G.Settings.Auto_Buy_Legendary_Sword = value
		StopTween(_G.Auto_Buy_Legendary_Sword)
		SaveSettings()
	end)

	task.spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Buy_Legendary_Sword then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("LegendarySwordDealer","1")
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("LegendarySwordDealer","2")
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("LegendarySwordDealer","3")
				end
			end)
		end
	end)

	Misc2:AddToggle('Auto_Buy_Enchanment_Haki', {
		Text = 'Auto Buy Enchanment Haki',
		Default = _G.Settings.Auto_Buy_Enchanment_Haki,
		Tooltip = 'Auto Buy Enchanment Haki',
	})

	Toggles.Auto_Buy_Enchanment_Haki:OnChanged(function(value)
		_G.Auto_Buy_Enchanment_Haki = value
		_G.Settings.Auto_Buy_Enchanment_Haki = value
		StopTween(_G.Auto_Buy_Enchanment_Haki)
		SaveSettings()
	end)

	task.spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Buy_Enchanment_Haki then
					local args = {
						[1] = "ColorsDealer",
						[2] = "2"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
			end)
		end
	end)


	local items2 = Tabs.Main:AddLeftGroupbox('items / Quest')

	items2:AddToggle('Auto_Rengoku', {
		Text = 'Auto Rengoku',
		Default = _G.Settings.Auto_Rengoku,
		Tooltip = 'Auto Rengoku',
	})

	Toggles.Auto_Rengoku:OnChanged(function(value)
		_G.Auto_Rengoku = value
		_G.Settings.Auto_Rengoku = value
		SaveSettings()
		StopTween(_G.Auto_Rengoku)
	end)

	spawn(function()
		while wait() do
			if _G.Auto_Rengoku then
				pcall(function()
					if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hidden Key") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Hidden Key") then
						EquipWeapon("Hidden Key")
						getgenv().ToTarget(CFrame.new(6571.1201171875, 299.23028564453, -6967.841796875))
					elseif game:GetService("Workspace").Enemies:FindFirstChild("Snow Lurker") or game:GetService("Workspace").Enemies:FindFirstChild("Arctic Warrior") then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if string.find(v.Name,"Snow Lurker") or string.find(v.Name,"Arctic Warrior") and v.Humanoid.Health > 0 then
								repeat wait()
									AutoHaki()
									EquipWeapon(_G.Select_Weapon)
									v.HumanoidRootPart.CanCollide = false
									v.HumanoidRootPart.Size = Vector3.new(50,50,50)
									RengokuMon = v.HumanoidRootPart.CFrame
									getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
									Cilck()
									StartRengokuMagnet = true
								until game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hidden Key") or _G.Auto_Rengoku == false or not v.Parent or v.Humanoid.Health <= 0
								StartRengokuMagnet = false
							end
						end
					else
						StartRengokuMagnet = false
						getgenv().ToTarget(CFrame.new(5439.716796875, 84.420944213867, -6715.1635742188))
					end
				end)
			end
		end
	end)

	items2:AddToggle('Auto_Dragon_Trident', {
		Text = 'Auto Dragon Trident',
		Default = _G.Settings.Auto_Dragon_Trident,
		Tooltip = 'Auto Dragon Trident',
	})

	Toggles.Auto_Dragon_Trident:OnChanged(function(value)
		_G.Auto_Dragon_Trident = value
		_G.Settings.Auto_Dragon_Trident = value
		SaveSettings()
		StopTween(_G.Auto_Dragon_Trident)
	end)

	spawn(function()
		while wait() do
			if _G.Auto_Dragon_Trident then
				pcall(function()
					if _G.Auto_Dragon_Trident and game.ReplicatedStorage:FindFirstChild("Tide Keeper") or game.Workspace.Enemies:FindFirstChild("Tide Keeper") then
						if game.Workspace.Enemies:FindFirstChild("Tide Keeper") then
							for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
								if string.find(v.Name,"Tide Keeper") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
									repeat wait()
										EquipWeapon(_G.Select_Weapon)
										AutoHaki()
										getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
										Cilck()
									until _G.Auto_Dragon_Trident or v.Humanoid.Health <= 0 or not v.Parent
								end
							end
						else
							getgenv().ToTarget(CFrame.new(-3914.830322265625, 123.29389190673828, -11516.8642578125))
						end
					end
				end)
			end
		end
	end)

	items2:AddToggle('Auto_Dark_Coat', {
		Text = 'Auto Dark Coat',
		Default = _G.Settings.Auto_Dark_Coat,
		Tooltip = 'Auto Dark Coat',
	})

	Toggles.Auto_Dark_Coat:OnChanged(function(value)
		_G.Auto_Dark_Coat = value
		_G.Settings.Auto_Dark_Coat = value
		SaveSettings()
		StopTween(_G.Auto_Dark_Coat)
	end)

	task.spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Dark_Coat then
					if game:GetService("Workspace").Enemies:FindFirstChild("Darkbeard") then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if string.find(v.Name,"Darkbeard")  and v.Humanoid.Health > 0 and v:IsA("Model") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") then
								repeat wait()
									StartMagnet = true
									AutoHaki()
									EquipWeapon(_G.Select_Weapon)
									PosMon = v.HumanoidRootPart.CFrame
									v.HumanoidRootPart.Size = Vector3.new(60,60,60)
									v.Humanoid.JumpPower = 0
									v.Humanoid.WalkSpeed = 0
									v.HumanoidRootPart.CanCollide = false
									v.Humanoid:ChangeState(11)
									getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
									Cilck()
								until _G.Auto_Dark_Coat == false or v.Humanoid.Health <= 0
								StartMagnet = false
							end
						end
					else
						getgenv().ToTarget(CFrame.new(3677.08203125, 62.751937866211, -3144.8332519531))
					end
				end
			end)
		end
	end)

	local Swan_Glasses = Tabs.Main:AddLeftGroupbox('Swan Glasses')

	Swan_Glasses:AddToggle('Auto_Swan_Glasses', {
		Text = 'Auto Swan Glasses',
		Default = _G.Settings.Auto_Swan_Glasses,
		Tooltip = 'Auto Swan Glasses',
	})

	Toggles.Auto_Swan_Glasses:OnChanged(function(value)
		_G.Auto_Swan_Glasses = value
		_G.Settings.Auto_Swan_Glasses = value
		SaveSettings()
		StopTween(_G.Auto_Swan_Glasses)
	end)

	Swan_Glasses:AddToggle('Auto_Swan_Glasses_Hop', {
		Text = 'Auto Swan Glasses Hop',
		Default = _G.Settings.Auto_Swan_Glasses_Hop,
		Tooltip = 'Auto Swan Glasses Hop',
	})

	Toggles.Auto_Swan_Glasses_Hop:OnChanged(function(value)
		_G.Auto_Swan_Glasses_Hop = value
		_G.Settings.Auto_Swan_Glasses_Hop = value
		SaveSettings()
		StopTween(_G.Auto_Swan_Glasses_Hop)
	end)

	
	spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Swan_Glasses and game.ReplicatedStorage:FindFirstChild("Don Swan") or game.Workspace.Enemies:FindFirstChild("Don Swan") then
					if game.Workspace.Enemies:FindFirstChild("Don Swan") then
						for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
							if string.find(v.Name,"Don Swan") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
								repeat wait()  
									EquipWeapon(_G.Select_Weapon)
									AutoHaki()
									getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
									Cilck()
								until not _G.Auto_Swan_Glasses or v.Humanoid.Health <= 0 or not v.Parent
							end
						end
					else
						getgenv().ToTarget(CFrame.new(2289.47900390625, 15.152046203613281, 739.512939453125))
					end
				else
					if _G.Auto_Swan_Glasses_Hop then
						Hop()
					end
				end
			end)
		end
	end)

else 

	local Elite = Tabs.items:AddRightGroupbox('Elite Boss')


	local Elite_Hunter_Status = Elite:AddLabel('EliteHunter : Not Spawned')
	spawn(function()
		while wait() do
			pcall(function()
				if game:GetService("ReplicatedStorage"):FindFirstChild("Diablo") or game:GetService("ReplicatedStorage"):FindFirstChild("Deandre") or game:GetService("ReplicatedStorage"):FindFirstChild("Urban") or game:GetService("Workspace").Enemies:FindFirstChild("Diablo") or game:GetService("Workspace").Enemies:FindFirstChild("Deandre") or game:GetService("Workspace").Enemies:FindFirstChild("Urban") then
					Elite_Hunter_Status:SetText("EliteHunter : Is Spawn")	
				else
					Elite_Hunter_Status:SetText("EliteHunter : Not Spawned")	
				end
			end)
		end
	end)

	Elite:AddToggle('Auto_Elite_Hunter', {
		Text = 'Auto Elite Hunter',
		Default = _G.Settings.Auto_Elite_Hunter,
		Tooltip = 'Auto Elite Hunter',
	})

	Toggles.Auto_Elite_Hunter:OnChanged(function(value)
		_G.Auto_Elite_Hunter = value
		_G.Settings.Auto_Elite_Hunter = value
		SaveSettings()   
		StopTween(_G.Auto_Elite_Hunter)
	end)

	Elite:AddToggle('Auto_Elite_Hunter_Hop', {
		Text = 'Auto Elite Hunter Hop',
		Default = _G.Settings.Auto_Elite_Hunter_Hop,
		Tooltip = 'Auto Elite Hunter Hop',
	})

	Toggles.Auto_Elite_Hunter_Hop:OnChanged(function(value)
		_G.Auto_Elite_Hunter_Hop = value 
		_G.Settings.Auto_Elite_Hunter_Hop = value
		SaveSettings()  
	end)

	local Elite_All_Mon = {
		["Mon Quest"] = {"Diablo","Deandre","Urban"},
		["Mon"] = {"Diablo","Deandre","Urban"},
		["Item"] = "God's Chalice",
	}
	spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Elite_Hunter then
					local QuestUI = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest
					for _,_l1 in next,Elite_All_Mon["Mon Quest"] do
						for _,l in next,Elite_All_Mon["Mon"] do
							if QuestUI.Visible == true then
								if game:GetService("Workspace").Enemies:FindFirstChild(_l1) or game:GetService("ReplicatedStorage"):FindFirstChild(_l1) then
									for _,_1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
										if string.find(_1.Name,_l1) then
											if _1:FindFirstChild("Humanoid") and _1:FindFirstChild("HumanoidRootPart") and _1.Humanoid.Health > 0 then
												repeat wait()
													EquipWeapon(_G.Select_Weapon)
													_1.HumanoidRootPart.Size = Vector3.new(60, 60, 60)  
													getgenv().ToTarget(_1.HumanoidRootPart.CFrame * MethodFarm)
													if (_1.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
														game:GetService("VirtualUser"):CaptureController()
														game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
													end
												until _1.Humanoid.Health <= 0 or not _1.Parent or not game:GetService("Workspace").Enemies:FindFirstChild(l) or not game:GetService("ReplicatedStorage"):FindFirstChild(l) or not _G.Auto_Elite_Hunter
											end
										else
											if _G.Bypass_TP then
												if (game:GetService("ReplicatedStorage"):FindFirstChild(_l1).HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 2000 then
													repeat wait()
														Bypass(game:GetService("ReplicatedStorage"):FindFirstChild(_l1).HumanoidRootPart.CFrame * MethodFarm)
													until not _G.Auto_Elite_Hunter
												end
											end
											if game:GetService("ReplicatedStorage"):FindFirstChild(_l1) then
												getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild(_l1).HumanoidRootPart.CFrame * MethodFarm)
											end
										end
									end
								end
							else
								if game.Players.LocalPlayer.Backpack:FindFirstChild(Elite_All_Mon["Item"]) or game.Players.LocalPlayer.Character:FindFirstChild(Elite_All_Mon["Item"]) then
									game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
									_G.Auto_Elite_Hunter = false
									return
								else
									if _G.Auto_Elite_Hunter_Hop and game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("EliteHunter") == "I don't have anything for you right now. Come back later." and not ( game:GetService("Workspace").Enemies:FindFirstChild(_l1) or game:GetService("ReplicatedStorage"):FindFirstChild(_l1) ) then
										print("Hop")
										_G.Rejoin = false
										wait(0.5)
										Hop()
									else
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter")
									end
								end
							end
						end
					end
				end
			end)
		end
	end)

	local Cake = Tabs.items:AddRightGroupbox('Cake Prince')

	local MobKilled = Cake:AddLabel('No Spawning')

	spawn(function()
		while wait() do
			pcall(function()
				if string.len(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")) == 88 then
					MobKilled:SetText("Kill Mods : "..string.sub(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner"),39,41))
				elseif string.len(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")) == 87 then
					MobKilled:SetText("Kill Mods : "..string.sub(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner"),39,40))
				elseif string.len(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")) == 86 then
					MobKilled:SetText("Kill Mods : "..string.sub(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner"),39,39))
				else
					MobKilled:SetText("Katakuri Is Spawning")
				end
			end)
		end
	end)

	Cake:AddToggle('Cake_Prince', {
		Text = 'Auto Cake Prince',
		Default = _G.Settings.Auto_Cake_Prince,
		Tooltip = 'Auto Cake Prince',
	})

	Toggles.Cake_Prince:OnChanged(function(value)
		_G.Auto_Cake_Prince = value
		if _G.Bypass_TP == false and _G.HH then
			wait(0.5)
			_G.Bypass_TP = true
		else
			_G.Bypass_TP = false
		end
		_G.Settings.Auto_Cake_Prince = value
		SaveSettings()
		StopTween(_G.Auto_Cake_Prince)
	end)

	Cake:AddToggle('Cake_Prince_King', {
		Text = 'Auto Cake Prince King',
		Default = _G.Settings.Auto_Cake_Prince,
		Tooltip = 'Auto Cake Prince King',
	})

	Toggles.Cake_Prince_King:OnChanged(function(value)
		_G.AutoCakePrinceV2 = value
		if _G.Bypass_TP == false and _G.HH then
			wait(0.5)
			_G.Bypass_TP = true
		else
			_G.Bypass_TP = false
		end
		_G.Settings.AutoCakePrinceV2 = value
		SaveSettings()
		StopTween(_G.AutoCakePrinceV2)
	end)

	spawn(function()
		while wait() do
			if _G.AutoCakePrinceV2 then
				pcall(function()
					if game.Players.LocalPlayer.Backpack:FindFirstChild("God's Chalice") or game.Players.LocalPlayer.Character:FindFirstChild("God's Chalice") then
						if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SweetChaliceNpc"),"Where") then
							warn("Not Have Enough Material")
						else
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SweetChaliceNpc")
						end
					elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Sweet Chalice") or game.Players.LocalPlayer.Character:FindFirstChild("Sweet Chalice") then
						if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner"),"Do you want to open the portal now?") then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")
						else
							local MojoMs = {"Baking Staff","Head Baker","Cake Guard","Cookie Crafter"}
							if game.Workspace.Enemies:FindFirstChild("Baking Staff") or game.Workspace.Enemies:FindFirstChild("Head Baker") or game.Workspace.Enemies:FindFirstChild("Cake Guard") or game.Workspace.Enemies:FindFirstChild("Cookie Crafter") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do 
									if string.find(v.Name,"Baking Staff") or string.find(v.Name,"Head Baker") or string.find(v.Name,"Cake Guard") or string.find(v.Name,"Cookie Crafter") and v.Humanoid.Health > 0 then
										repeat wait()
											PosMon = v.HumanoidRootPart.CFrame
											EquipWeapon(_G.Select_Weapon)
											v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)  
											BringMobFarm = true
											getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
											if (v.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
												game:GetService("VirtualUser"):CaptureController()
												game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
											end
										until _G.AutoCakePrinceV2 == false or game:GetService("ReplicatedStorage"):FindFirstChild("Cake Prince") or not v.Parent or v.Humanoid.Health <= 0
									end
								end
							else
								BringMobFarm = false
								getgenv().ToTarget(CFrame.new(-1916.44983, 178.615494, -12701.5049, -0.842750371, -2.00153871e-09, -0.538304567, -3.13815285e-08, 1, 4.54115714e-08, 0.538304567, 5.516344e-08, -0.842750371))
							end
						end						
					elseif game.ReplicatedStorage:FindFirstChild("Dough King") or game:GetService("Workspace").Enemies:FindFirstChild("Dough King") then
						if game:GetService("Workspace").Enemies:FindFirstChild("Dough King") then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do 
								if string.find(v.Name,"Dough King") then
									repeat wait()
										PosMon = v.HumanoidRootPart.CFrame
										EquipWeapon(_G.Select_Weapon)
										v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)  
										BringMobFarm = true
										getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
										if (v.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
											game:GetService("VirtualUser"):CaptureController()
											game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
										end
									until _G.AutoCakePrinceV2 == false or not v.Parent or v.Humanoid.Health <= 0
								end    
							end    
						else
							getgenv().ToTarget(CFrame.new(-2009.2802734375, 4532.97216796875, -14937.3076171875)) 
						end
					elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Red Key") or game.Players.LocalPlayer.Character:FindFirstChild("Red Key") then
						local args = {
							[1] = "CakeScientist",
							[2] = "Check"
						}

						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					else
						if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
							if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,"Diablo") or string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,"Deandre") or string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,"Urban") then
								if game:GetService("Workspace").Enemies:FindFirstChild("Diablo") or game:GetService("Workspace").Enemies:FindFirstChild("Deandre") or game:GetService("Workspace").Enemies:FindFirstChild("Urban") then
									for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
										if string.find(v.Name,"Diablo") or string.find(v.Name,"Deandre") or string.find(v.Name,"Urban") then
											if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
												repeat wait()
													EquipWeapon(_G.Select_Weapon)
													v.HumanoidRootPart.CanCollide = false
													v.Humanoid.WalkSpeed = 0
													v.HumanoidRootPart.Size = Vector3.new(50,50,50)
													if AttackRandomType == 1 then
														getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
													elseif AttackRandomType == 2 then
														getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
													elseif AttackRandomType == 3 then
														getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
													else
														getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
													end
													Cilck()
													sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
												until _G.AutoCakePrinceV2 == false or v.Humanoid.Health <= 0 or not v.Parent or game.Players.LocalPlayer.Backpack:FindFirstChild("God's Chalice") or game.Players.LocalPlayer.Character:FindFirstChild("God's Chalice")
											end
										end
									end
								else
									if game:GetService("ReplicatedStorage"):FindFirstChild("Diablo") then
										getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild("Diablo").HumanoidRootPart.CFrame * MethodFarm)
									elseif game:GetService("ReplicatedStorage"):FindFirstChild("Deandre") then
										getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild("Deandre").HumanoidRootPart.CFrame * MethodFarm)
									elseif game:GetService("ReplicatedStorage"):FindFirstChild("Urban") then
										getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild("Urban").HumanoidRootPart.CFrame * MethodFarm)
									end
								end                    
							end
						else
							wait(0.5)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter")
						end
					end
				end)
			end
		end
	end)

	spawn(function()
		while wait() do
			if _G.Auto_Cake_Prince then
				pcall(function()
					if game.ReplicatedStorage:FindFirstChild("Cake Prince") or game:GetService("Workspace").Enemies:FindFirstChild("Cake Prince") or  game.ReplicatedStorage:FindFirstChild("Dough King") or game:GetService("Workspace").Enemies:FindFirstChild("Dough King") then   
						if _G.Settings.Bypass_TP then
							_G.Bypass_TP = false
						end
						if not game:GetService("Workspace").Enemies:FindFirstChild("Cake Prince") then
							for _,x in pairs(game.ReplicatedStorage:GetChildren()) do 
								if x.Name == "Cake Prince" or x.Name == "Dough King" then
									if (x.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1000 then
										wait(1.5)
										getgenv().ToTarget(CFrame.new(-2145.89722, 70.0088272, -12399.6016, 0.99999702, 1.58276379e-08, 0.00245277886, -1.57982978e-08, 1, -1.19813057e-08, -0.00245277886, 1.19425199e-08, 0.99999702))
										return
									end
								end
							end
						end

						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if string.find(v.Name,"Cake Prince") then
								if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
									repeat task.wait()
										if (v.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1000 then
											getgenv().ToTarget(CFrame.new(-2145.89722, 70.0088272, -12399.6016, 0.99999702, 1.58276379e-08, 0.00245277886, -1.57982978e-08, 1, -1.19813057e-08, -0.00245277886, 1.19425199e-08, 0.99999702))
											return
										end
										EquipWeapon(_G.Select_Weapon)
										v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)  
										BringMobFarm = true
										getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
										if (v.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
											game:GetService("VirtualUser"):CaptureController()
											game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
										end
										sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
									until not _G.Auto_Cake_Prince or not v.Parent or v.Humanoid.Health <= 0
								end
							else
								for _,x in pairs(game.ReplicatedStorage:GetChildren()) do 
									if x.Name == "Cake Prince" or x.Name == "Dough King" then
										if (x.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1000 then
											getgenv().ToTarget(CFrame.new(-2145.89722, 70.0088272, -12399.6016, 0.99999702, 1.58276379e-08, 0.00245277886, -1.57982978e-08, 1, -1.19813057e-08, -0.00245277886, 1.19425199e-08, 0.99999702))
											return
										end
									end
								end
							end
						end
					else 
						if game:GetService("Workspace").Enemies:FindFirstChild("Cake Prince ") or game.ReplicatedStorage:FindFirstChild("Cake Prince") then
							for _,x in pairs(game.ReplicatedStorage:GetChildren()) do 
								if x.Name == "Cake Prince" or x.Name == "Dough King" then
									if (x.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 1000 then
										getgenv().ToTarget(CFrame.new(-2145.89722, 70.0088272, -12399.6016, 0.99999702, 1.58276379e-08, 0.00245277886, -1.57982978e-08, 1, -1.19813057e-08, -0.00245277886, 1.19425199e-08, 0.99999702))
										return
									end
								end
							end
						else
							if game.Workspace.Enemies:FindFirstChild("Baking Staff") or game.Workspace.Enemies:FindFirstChild("Head Baker") or game.Workspace.Enemies:FindFirstChild("Cake Guard") or game.Workspace.Enemies:FindFirstChild("Cookie Crafter")  then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do  
									if string.find(v.Name,"Baking Staff") or string.find(v.Name,"Head Baker") or string.find(v.Name,"Cake Guard") or string.find(v.Name,"Cookie Crafter") and v.Humanoid.Health > 0 then
										repeat wait()
											PosMon = v.HumanoidRootPart.CFrame
											EquipWeapon(_G.Select_Weapon)
											v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)  
											BringMobFarm = true
											getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
											if (v.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
												game:GetService("VirtualUser"):CaptureController()
												game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
											end
										until _G.Auto_Cake_Prince == false or game:GetService("ReplicatedStorage"):FindFirstChild("Cake Prince") or not v.Parent or v.Humanoid.Health <= 0
									end
								end
							else
								BringMobFarm = false
								UnEquipWeapon(_G.Select_Weapon)
								getgenv().ToTarget(GetCake_CFrame_Mon() * MethodFarm)
								wait(0.5)
							end
						end
					end
				end)
			end
		end
	end)

	Cake:AddToggle('Auto_Spawn_Cake_Prince', {
		Text = 'Auto Spawn Cake Prince',
		Default = _G.Settings.Auto_Spawn_Cake_Prince,
		Tooltip = 'Auto Spawn Cake Prince',
	})

	Toggles.Auto_Spawn_Cake_Prince:OnChanged(function(value)
		_G.Auto_Spawn_Cake_Prince = value
		_G.Settings.Auto_Spawn_Cake_Prince = value
		SaveSettings()
	end)
	
	spawn(function()
		while wait() do
			if _G.Auto_Spawn_Cake_Prince then
				local args = {
					[1] = "CakePrinceSpawner",
					[2] = true
				}

				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))                    
				local args = {
					[1] = "CakePrinceSpawner"
				}

				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end
		end
	end)
	

	local Bone = Tabs.items:AddRightGroupbox('Bone')
	
	local BoneCheck = Bone:AddLabel('Bone : nii')
	
	spawn(function()
		pcall(function()
			while wait() do
				BoneCheck:SetText("Bone : "..(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Bones","Check")))
			end
		end)
	end)
	
	Bone:AddToggle('Auto_Farm_Bone', {
		Text = 'Auto Farm Bone',
		Default = _G.Settings.Auto_Farm_Bone,
		Tooltip = 'Auto Farm Bone',
	})

	Toggles.Auto_Farm_Bone:OnChanged(function(value)
		_G.Auto_Farm_Bone = value
		_G.Settings.Auto_Farm_Bone = value
		SaveSettings()   
		StopTween(_G.Auto_Farm_Bone)
	end)

	Bone:AddToggle('Auto_Random_Bone', {
		Text = 'Auto Random Bone',
		Default = _G.Settings.Auto_Trade_Bone,
		Tooltip = 'Auto Random Bone',
	})

	Toggles.Auto_Random_Bone:OnChanged(function(value)
		_G.Auto_Random_Bone = value
		_G.Settings.Auto_Trade_Bone = value
		SaveSettings()
	end)

	spawn(function()
		while wait(.1) do
			if _G.Auto_Random_Bone then
				local args = {
					[1] = "Bones",
					[2] = "Buy",
					[3] = 1,
					[4] = 1
				}

				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end
		end
	end)


	local Number2 = 1
	local BoneTabel = {
		["Mon"] = {"Reborn Skeleton","Demonic Soul","Living Zombie","Posessed Mummy"},
		["Boss"] = {"Soul Reaper"},
		["Item"] = "Hallow Essence",
	}

	local SetCFarmeBone = 1
	function GetBone_CFrame_Mon()
		local matchingCFrames = {}
		for _, v in ipairs(game.workspace.EnemySpawns:GetChildren()) do
			if v.Name == BoneTabel["Mon"] then
				table.insert(matchingCFrames, v.CFrame)
			end
		end
		return matchingCFrames
	end

	spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Farm_Bone then
					for _, _Boss in ipairs(BoneTabel["Boss"]) do
						local _Item = BoneTabel["Item"]
						if game:GetService("Workspace").Enemies:FindFirstChild(_Boss) or game:GetService("ReplicatedStorage"):FindFirstChild(_Boss) then
							for _, _v1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if string.find(_v1.Name,_Boss) then
									if _v1:FindFirstChild("Humanoid") and _v1:FindFirstChild("HumanoidRootPart") and _v1.Humanoid.Health > 0 then
										repeat wait()
											EquipWeapon(_G.Select_Weapon)
											_v1.HumanoidRootPart.Size = Vector3.new(60, 60, 60)  
											BringMobFarm = true
											getgenv().ToTarget(_v1.HumanoidRootPart.CFrame * MethodFarm)
											if (_v1.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
												game:GetService("VirtualUser"):CaptureController()
												game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
											end
										until not _G.Auto_Farm_Bone or v.Humanoid.Health <= 0 or not v.Parent or v.Humanoid.Health <= 0
										BringMobFarm = false
									end
								end
							end
						else
							if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(_Item) or game:GetService("Players").LocalPlayer.Character:FindFirstChild(_Item) then
								EquipWeapon(_Item)
								getgenv().ToTarget(workspace.Map["Haunted Castle"].Summoner.Detection.CFrame)
							else
								for _, _Mon in next, BoneTabel["Mon"] do
									if game:GetService("Workspace").Enemies:FindFirstChild("Reborn Skeleton") or game:GetService("Workspace").Enemies:FindFirstChild("Living Zombie") or game:GetService("Workspace").Enemies:FindFirstChild("Demonic Soul") or game:GetService("Workspace").Enemies:FindFirstChild("Posessed Mummy") then
										print(_Mon)
										for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
											if string.find(v.Name,_Mon) then
												if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
													repeat wait()
														PosMon = v.HumanoidRootPart.CFrame
														EquipWeapon(_G.Select_Weapon)
														v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)  
														BringMobFarm = true
														getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
														if (v.HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
															game:GetService("VirtualUser"):CaptureController()
															game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
														end
													until not _G.Auto_Farm_Bone or v.Humanoid.Health <= 0 or not v.Parent or v.Humanoid.Health <= 0
												else
													if _G.Auto_CFrame then
														getgenv().ToTarget(GetBone_CFrame_Mon()[SetCFarmeBone] * MethodFarm)
														if (GetBone_CFrame_Mon()[SetCFarmeBone].Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
															if SetCFarmeBone == nil or SetCFarmeBone == '' then
																SetCFarmeBone = 1
															elseif SetCFarmeBone >= #GetBone_CFrame_Mon() then
																SetCFarmeBone = 1
															end
															SetCFarmeBone =  SetCFarmeBone + 1

															print(SetCFarmeBone)
															wait(0.5)
														end
													else
														if AttackRandomType_MonCFrame == 1 then
															getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
														elseif AttackRandomType_MonCFrame == 2 then
															getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
														elseif AttackRandomType_MonCFrame == 3 then
															getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
														elseif AttackRandomType_MonCFrame == 4 then
															getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
														elseif AttackRandomType_MonCFrame == 5 then
															getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
														else
															getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
														end
													end
												end
											end
										end
									else
										if _G.Auto_CFrame then
											getgenv().ToTarget(GetBone_CFrame_Mon()[SetCFarmeBone] * MethodFarm)
											if (GetBone_CFrame_Mon()[SetCFarmeBone].Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
												if SetCFarmeBone == nil or SetCFarmeBone == '' then
													SetCFarmeBone = 1
												elseif SetCFarmeBone >= #GetBone_CFrame_Mon() then
													SetCFarmeBone = 1
												end
												SetCFarmeBone =  SetCFarmeBone + 1

												print(SetCFarmeBone)
												wait(0.5)
											end
										else
											if AttackRandomType_MonCFrame == 1 then
												getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
											elseif AttackRandomType_MonCFrame == 2 then
												getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
											elseif AttackRandomType_MonCFrame == 3 then
												getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
											elseif AttackRandomType_MonCFrame == 4 then
												getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
											elseif AttackRandomType_MonCFrame == 5 then
												getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
											else
												getgenv().ToTarget(GetBone_CFrame_Mon()[1] * MethodFarm)
											end
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


	local Buddy_Sword = Tabs.items:AddLeftGroupbox('Buddy Sword')

	Buddy_Sword:AddToggle('Auto_Buddy_Sword', {
		Text = 'Auto Buddy Sword',
		Default = _G.Settings.Auto_Buddy_Sword,
		Tooltip = 'Auto Buddy Sword',
	})

	Toggles.Auto_Buddy_Sword:OnChanged(function(value)
		_G.Auto_Buddy_Sword = value
		_G.Settings.Auto_Buddy_Sword = value
		SaveSettings()
		StopTween(_G.Auto_Buddy_Sword)
	end)
	
	spawn(function()
		while wait() do
			if _G.Auto_Buddy_Sword then
				pcall(function()
					if _G.Auto_Buddy_Sword and game.ReplicatedStorage:FindFirstChild("Cake Queen") then
						if game.Workspace.Enemies:FindFirstChild("Cake Queen") then
							for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
								if string.find(v.Name,"Cake Queen") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
									repeat wait()
										AutoHaki()
										EquipWeapon(_G.Select_Weapon)
										getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Twin_Hook or v.Humanoid.Health <= 0 or not v.Parent
								end
							end
						else
							getgenv().ToTarget(CFrame.new(5525.7045898438, 262.90060424805, -6755.1186523438))
						end
					else
						if _G.Auto_Buddy_Sword_Hop then
							Hop()
						end
					end
				end)
			end
		end
	end)

	Buddy_Sword:AddToggle('Auto_Buddy_Sword_Hop', {
		Text = 'Auto Buddy Sword Hop',
		Default = _G.Settings.Auto_Buddy_Sword_Hop,
		Tooltip = 'Auto Buddy Sword Hop',
	})

	Toggles.Auto_Buddy_Sword_Hop:OnChanged(function(value)
		_G.Auto_Buddy_Sword_Hop = value
		_G.Settings.Auto_Buddy_Sword_Hop = value
		SaveSettings()
	end)
	
	local Boss_Hallow = Tabs.items:AddLeftGroupbox('Hallow Sword')

	Boss_Hallow:AddToggle('Auto_Farm_Boss_Hallow', {
		Text = 'Auto Farm Boss Hallow',
		Default = _G.Settings.Auto_Farm_Boss_Hallow,
		Tooltip = 'Auto Farm Boss Hallow',
	})

	Toggles.Auto_Farm_Boss_Hallow:OnChanged(function(value)
		_G.Auto_Farm_Boss_Hallow = value
		_G.Settings.Auto_Farm_Boss_Hallow = value
		SaveSettings()
		StopTween(_G.Auto_Farm_Boss_Hallow)
	end)

	Boss_Hallow:AddToggle('Auto_Farm_Boss_Hallow_Hop', {
		Text = 'Auto Farm Boss Hallow Hop',
		Default = _G.Settings.Auto_Farm_Boss_Hallow_Hop,
		Tooltip = 'Auto Farm Boss Hallow Hop',
	})

	Toggles.Auto_Farm_Boss_Hallow_Hop:OnChanged(function(value)
		_G.Auto_Farm_Boss_Hallow_Hop = value
		_G.Settings.Auto_Farm_Boss_Hallow_Hop = value
		SaveSettings()
	end)


	spawn(function()
		while wait() do
			if _G.Auto_Farm_Boss_Hallow then
				pcall(function()
					if _G.Auto_Farm_Boss_Hallow and game.ReplicatedStorage:FindFirstChild("Soul Reaper") then
						if game.Workspace.Enemies:FindFirstChild("Soul Reaper") then
							for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
								if string.find(v.Name,"Soul Reaper") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
									repeat wait()
										AutoHaki()
										EquipWeapon(_G.Select_Weapon)
										getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Twin_Hook or v.Humanoid.Health <= 0 or not v.Parent
								end
							end
						else
							getgenv().ToTarget(CFrame.new(-9524.7890625, 315.80429077148, 6655.7192382813))
						end
					else
						if _G.Auto_Farm_Boss_Hallow_Hop then
							Hop()
						end
					end
				end)
			end
		end
	end)

	local Twin_Hook = Tabs.items:AddLeftGroupbox('Twin Hook')

	Twin_Hook:AddToggle('Auto_Twin_Hook', {
		Text = 'Auto Twin Hook',
		Default = _G.Settings.Auto_Twin_Hook,
		Tooltip = 'Auto Twin Hook',
	})

	Toggles.Auto_Twin_Hook:OnChanged(function(value)
		_G.Auto_Twin_Hook = value
		_G.Settings.Auto_Twin_Hook = value
		SaveSettings()
		StopTween(_G.Auto_Twin_Hook)
	end)

	Twin_Hook:AddToggle('Auto_Twin_Hook_Hop', {
		Text = 'Auto Twin Hook Hop',
		Default = _G.Settings.Auto_Twin_Hook_Hop,
		Tooltip = 'Auto Twin Hook Hop',
	})

	Toggles.Auto_Twin_Hook:OnChanged(function(value)
		_G.Auto_Twin_Hook_Hop = value
		_G.Settings.Auto_Twin_Hook_Hop = value
		SaveSettings()
	end)

	spawn(function()
		while wait() do
			if _G.Auto_Twin_Hook then
				pcall(function()
					if _G.Auto_Twin_Hook and game.ReplicatedStorage:FindFirstChild("Captain Elephant") or game.Workspace.Enemies:FindFirstChild("Captain Elephant") then
						if game.Workspace.Enemies:FindFirstChild("Captain Elephant") then
							for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
								if string.find(v.Name,"Captain Elephant") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
									repeat wait()
										AutoHaki()
										EquipWeapon(_G.Select_Weapon)
										getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Twin_Hook or v.Humanoid.Health <= 0 or not v.Parent
								end
							end
						else
							getgenv().ToTarget(CFrame.new(-13348.0654296875, 405.8904113769531, -8570.62890625))
						end
					else
						if _G.Auto_Twin_Hook_Hop then
							Hop()
						end
					end
				end)
			end
		end
	end)
	
	local Cavander = Tabs.items:AddLeftGroupbox('Cavander')

	Cavander:AddToggle('Auto_Cavander', {
		Text = 'Auto Cavander',
		Default = _G.Settings.Auto_Canvander,
		Tooltip = 'Auto Cavander',
	})

	Toggles.Auto_Cavander:OnChanged(function(value)
		_G.Auto_Canvander = value
		_G.Settings.Auto_Canvander = value
		SaveSettings()
		StopTween(_G.Auto_Canvander)
	end)
	

	Cavander:AddToggle('Auto_Cavander_Hop', {
		Text = 'Auto Cavander Hop',
		Default = _G.Settings.Auto_Canvander_Hop,
		Tooltip = 'Auto Cavander Hop',
	})

	Toggles.Auto_Cavander_Hop:OnChanged(function(value)
		_G.Auto_Canvander_Hop = value
		_G.Settings.Auto_Canvander_Hop = value
		SaveSettings()
	end)

	task.spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Cavander then
					if game:GetService("Workspace").Enemies:FindFirstChild("Beautiful Pirate") then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if string.find(v.Name,"Beautiful Pirate") and v.Humanoid.Health > 0 and v:IsA("Model") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") then
								repeat wait()
									StartMagnet = true
									AutoHaki()
									EquipWeapon(_G.Select_Weapon)
									PosMon = v.HumanoidRootPart.CFrame
									getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
								until not _G.Auto_Cavander or v.Humanoid.Health <= 0
							end
						end
					else
						getgenv().ToTarget(CFrame.new(5283.609375, 22.56223487854, -110.78285217285))
					end
				else
					if _G.Auto_Cavander_Hop then
						wait(10)
						Hop()	
					end
				end
			end)
		end
	end)


	local SwordYT = Tabs.items:AddLeftGroupbox('Yama & Tushita')

	SwordYT:AddToggle('Auto_Yama', {
		Text = 'Auto Yama',
		Default = _G.Settings.Auto_Yama,
		Tooltip = 'Auto Yama',
	})

	Toggles.Auto_Yama:OnChanged(function(value)
		_G.Auto_Yama = value
		_G.Settings.Auto_Yama = value

		if value == false then
			_G.Auto_Farm_Level = false
		end

		SaveSettings()
		StopTween(_G.Auto_Yama)
	end)

	
	SwordYT:AddToggle('Auto_Tushita', {
		Text = 'Auto Tushita',
		Default = _G.Settings.Auto_Tushita,
		Tooltip = 'Auto Tushita',
	})

	Toggles.Auto_Tushita:OnChanged(function(value)
		_G.Auto_Tushita = value
		_G.Settings.Auto_Tushita = value

		if value == false then
			_G.Auto_Farm_Level = false
		end

		SaveSettings()
		StopTween(_G.Auto_Tushita)
	end)

	local Yama_All_Mon = {
		["Mon Quest"] = {"Diablo","Deandre","Urban"},
		["Mon"] = {"Diablo","Deandre","Urban"},
		["Item"] = "God's Chalice",
	}

	spawn(function()
		while wait() do
			if _G.Auto_Yama then
				pcall(function()
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter","Progress") >= 30 then
						fireclickdetector(game:GetService("Workspace").Map.Waterfall.SealedKatana.Handle.ClickDetector)
					else
						local QuestUI = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest
						for _,_l1 in ipairs(Yama_All_Mon["Mon Quest"]) do
							for _,l in ipairs(Yama_All_Mon["Mon"]) do
								if QuestUI.Visible == true then
									if game:GetService("Workspace").Enemies:FindFirstChild(_l1) or game:GetService("ReplicatedStorage"):FindFirstChild(_l1) then
										for _,_v1 in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
											if string.find(_v1.Name,_l1) then
												if _v1:FindFirstChild("Humanoid") and _v1:FindFirstChild("HumanoidRootPart") and _v1.Humanoid.Health > 0 then
													repeat wait()
														_v1.HumanoidRootPart.Size = Vector3.new(60,60,60)
														_v1.HumanoidRootPart.CanCollide = false
														_v1.Head.CanCollide = false
														BringMobFarm = true
														EquipWeapon(_G.Select_Weapon)
														_v1.HumanoidRootPart.Transparency = 1
														getgenv().ToTarget(_v1.HumanoidRootPart.CFrame * MethodFarm)
													until not _G.Auto_Yama or _v1.Humanoid.Health <= 0 or not _v1.Parent
												end
											else
												if (game:GetService("ReplicatedStorage"):FindFirstChild(_l1).HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 2000 then
													BTP(game:GetService("ReplicatedStorage"):FindFirstChild(_l1).HumanoidRootPart.CFrame)
													return
												end
												getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild(_l1).HumanoidRootPart.CFrame * MethodFarm)
												return
											end
										end
									end
								else
									if game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("EliteHunter") == "I don't have anything for you right now. Come back later." and not ( game:GetService("Workspace").Enemies:FindFirstChild(_l1) or game:GetService("ReplicatedStorage"):FindFirstChild(_l1) ) then
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter")
										if (game:GetService("ReplicatedStorage"):FindFirstChild(_l1).HumanoidRootPart.CFrame.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 2000 then
											BTP(game:GetService("ReplicatedStorage"):FindFirstChild(_l1).HumanoidRootPart.CFrame)
											return
										end
										getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild(_l1).HumanoidRootPart.CFrame * MethodFarm)
										return
									end
								end
							end
						end
					end
				end)
			end
		end
	end)

	spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Tushita then
					if game:GetService("Workspace").Map.Turtle.TushitaGate:GetChildren()[2].Transparency == 1 or game:GetService("Workspace").Map.Turtle.TushitaGate:GetChildren()[1].Transparency == 1 then
						if #game:GetService("Workspace").Enemies:GetChildren() > 0 then
							if game:GetService("Workspace").Enemies:FindFirstChild("Longma") or game:GetService("ReplicatedStorage"):FindFirstChild("Longma") then
								for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if string.find(v.Name,"Longma") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
										repeat wait()
											v.HumanoidRootPart.Size = Vector3.new(60,60,60)
											v.HumanoidRootPart.CanCollide = false
											v.Head.CanCollide = false
											BringMobFarm = true
											AutoHaki()
											EquipWeapon(_G.Select_Weapon)
											v.HumanoidRootPart.Transparency = 1
											getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
										until not _G.Auto_Tushita or not v.Humanoid.Health <= 0 or not v.Parent
									else
										getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild("Longma").HumanoidRootPart.CFrame * MethodFarm)
									end
								end
							end
						end
					else
						if game:GetService("Workspace").Enemies:FindFirstChild("rip_indra True Form") or game:GetService("ReplicatedStorage"):FindFirstChild("rip_indra True Form") then
							if game:GetService("Players").LocalPlayer.Data.LastSpawnPoint.Value == tostring(GetIsLand(CFrame.new(-13274.528320313, 531.82073974609, -7579.22265625))) then
								wait(1)
								repeat getgenv().ToTarget(CFrame.new(-10752, 417, -9366)) wait() until not _G.Auto_Holy_Torch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-10752, 417, -9366)).Magnitude <= 1
								wait(1)
								repeat getgenv().ToTarget(CFrame.new(-11672, 334, -9474)) wait() until not _G.Auto_Holy_Torch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-11672, 334, -9474)).Magnitude <= 1
								wait(1)
								repeat getgenv().ToTarget(CFrame.new(-12132, 521, -10655)) wait() until not _G.Auto_Holy_Torch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-12132, 521, -10655)).Magnitude <= 1
								wait(1)
								repeat getgenv().ToTarget(CFrame.new(-13336, 486, -6985)) wait() until not _G.Auto_Holy_Torch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-13336, 486, -6985)).Magnitude <= 1
								wait(1)
								repeat getgenv().ToTarget(CFrame.new(-13489, 332, -7925)) wait() until not _G.Auto_Holy_Torch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-13489, 332, -7925)).Magnitude <= 1
							else
								if (CFrame.new(5148.03613, 162.352493, 910.548218, 0, 0, -1, 0, 1, 0, 1, 0, 0).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 2000 then
									BTP(CFrame.new(5148.03613, 162.352493, 910.548218, 0, 0, -1, 0, 1, 0, 1, 0, 0))
									return
								end
								getgenv().ToTarget(CFrame.new(5148.03613, 162.352493, 910.548218, 0, 0, -1, 0, 1, 0, 1, 0, 0))
								wait(2.5)
								return
							end
						end
					end
				else
					_G.Auto_Tushita = false
				end
			end)
		end
	end)

	local Serpent_Bow = Tabs.items:AddLeftGroupbox('Serpent Bow')

	Serpent_Bow:AddToggle('Auto_Serpent_Bow', {
		Text = 'Auto Serpent Bow',
		Default = _G.Settings.Auto_Serpent_Bow,
		Tooltip = 'Auto Serpent Bow',
	})

	Toggles.Auto_Serpent_Bow:OnChanged(function(value)
		_G.Auto_Serpent_Bow = value
		_G.Settings.Auto_Serpent_Bow = value
		SaveSettings()
		StopTween(_G.Auto_Serpent_Bow)
	end)
	
	Serpent_Bow:AddToggle('Auto_Serpent_Bow_Hop', {
		Text = 'Auto Serpent Bow Hop',
		Default = _G.Settings.Auto_Serpent_Bow_Hop,
		Tooltip = 'Auto Serpent Bow Hop',
	})

	Toggles.Auto_Serpent_Bow_Hop:OnChanged(function(value)
		_G.Auto_Serpent_Bow_Hop = value
		_G.Settings.Auto_Serpent_Bow_Hop = value
		SaveSettings()
		StopTween(_G.Auto_Serpent_Bow_Hop)
	end)
	

	spawn(function()
		while wait() do
			if _G.Auto_Serpent_Bow then
				pcall(function()
					if _G.Auto_Serpent_Bow and game.ReplicatedStorage:FindFirstChild("Island Empress") then
						if game.Workspace.Enemies:FindFirstChild("Island Empress") then
							for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
								if string.find(v.Name,"Island Empress") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
									repeat wait()
										AutoHaki()
										EquipWeapon(_G.Select_Weapon)
										getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Serpent_Bow or v.Humanoid.Health <= 0 or not v.Parent
								end
							end
						else
							getgenv().ToTarget(CFrame.new(5764.1826171875, 700.425537109375, 141.11996459960938))
						end
					else
						if _G.Auto_Serpent_Bow_Hop then
							Hop()
						end
					end
				end)
			end
		end
	end)

	local Dark_Dagger = Tabs.items:AddLeftGroupbox('Dark Dagger')

	Dark_Dagger:AddToggle('Auto_Dark_Dagger', {
		Text = 'Auto Dark Dagger',
		Default = _G.Settings.Auto_Dark_Dagger,
		Tooltip = 'Auto Dark Dagger',
	})

	Toggles.Auto_Dark_Dagger:OnChanged(function(value)
		_G.Auto_Dark_Dagger = value
		_G.Settings.Auto_Dark_Dagger = value
		SaveSettings()
		StopTween(_G.Auto_Dark_Dagger)
	end)
	

	Dark_Dagger:AddToggle('Auto_Dark_Dagger_Hop', {
		Text = 'Auto Dark Dagger Hop',
		Default = _G.Settings.Auto_Dark_Dagger_Hop,
		Tooltip = 'Auto Dark Dagger Hop',
	})

	Toggles.Auto_Dark_Dagger:OnChanged(function(value)
		_G.Auto_Dark_Dagger_Hop = value
		_G.Settings.Auto_Dark_Dagger_Hop = value
		SaveSettings()
	end)

	spawn(function()
		while wait() do
			if _G.Auto_Dark_Dagger then
				pcall(function()
					if _G.Auto_Dark_Dagger and game.ReplicatedStorage:FindFirstChild("rip_indra True Form") then
						if game.Workspace.Enemies:FindFirstChild("rip_indra True Form") then
							for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
								if string.find(v.Name,"rip_indra True Form") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and v:IsA("Model") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") then
									repeat wait()
										AutoHaki()
										EquipWeapon(_G.Select_Weapon)
										getgenv().ToTarget(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Dark_Dagger or v.Humanoid.Health <= 0 or not v.Parent
								end
							end
						else
							getgenv().ToTarget(CFrame.new(-5344.822265625, 423.98541259766, -2725.0930175781))
						end
					else
						if _G.Auto_Dark_Dagger_Hop then
							Hop()
						end
					end
				end)
			end
		end
	end)

end

local SettingFarm = Tabs.Main:AddRightGroupbox('Setting')

SettingFarm:AddDropdown('Slc', {
	Values = { "Melee", "Sword", "Gun", "Fruit" },
	Default = 1,
	Multi = false,
	Text = 'Select Weapon',
	Tooltip = 'Use Weapon Select farm',
})

Options.Slc:OnChanged(function(va)
	_G.Select_Weapon = va
end)

Options.Slc:SetValue("Melee")

task.spawn(function()
	while wait() do
		pcall(function()
			if _G.Select_Weapon == "Melee" then
				for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
					if v.ToolTip == "Melee" then
						if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
							_G.Select_Weapon = v.Name
						end
					end
				end
			elseif _G.Select_Weapon == "Sword" then
				for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
					if v.ToolTip == "Sword" then
						if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
							_G.Select_Weapon = v.Name
						end
					end
				end
			elseif _G.Select_Weapon == "Gun" then
				for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
					if v.ToolTip == "Gun" then
						if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
							_G.Select_Weapon = v.Name
						end
					end
				end
			elseif _G.Select_Weapon == "Fruit" then
				for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
					if v.ToolTip == "Blox Fruit" then
						if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
							_G.Select_Weapon = v.Name
						end
					end
				end
			end
		end)
	end
end)


if game:GetService("ReplicatedStorage").Effect.Container:FindFirstChild("Death") then
	game:GetService("ReplicatedStorage").Effect.Container.Death:Destroy()
end
if game:GetService("ReplicatedStorage").Effect.Container:FindFirstChild("Respawn") then
	game:GetService("ReplicatedStorage").Effect.Container.Respawn:Destroy()
end

SettingFarm:AddToggle('Notifications_Remove', {
	Text = 'Notifications Remove',
	Default = _G.Settings.Notifications_Remove,
	Tooltip = 'Notifications Remove',
})

Toggles.Notifications_Remove:OnChanged(function(value)
	_G.Settings.Notifications_Remove = value
	if value == true then
		game:GetService("Players").LocalPlayer.PlayerGui.Notifications.Enabled = false
	else
		game:GetService("Players").LocalPlayer.PlayerGui.Notifications.Enabled = true
	end
	SaveSettings()
end)

SettingFarm:AddToggle('Auto_Haki_Ken', {
	Text = 'Auto Haki Ken',
	Default = _G.Settings.Auto_Haki_Ken,
	Tooltip = 'Auto Haki Ken',
})

Toggles.Auto_Haki_Ken:OnChanged(function(value)
	_G.Auto_Haki_Ken = value
end)


spawn(function()
	while wait() do
		if _G.Auto_Haki_Ken then
			local args = {
				[1] = "Ken",
				[2] = true
			}

			game:GetService("ReplicatedStorage").Remotes.CommE:FireServer(unpack(args))
		end
	end
end)

SettingFarm:AddToggle('Fast', {
	Text = 'Fast Attack',
	Default = _G.Settings.FastAttack,
	Tooltip = 'Fast Attack',
})

Toggles.Fast:OnChanged(function(value)
	_G.FastAttack = value
	_G.Settings.FastAttack = value
	SaveSettings()
end)

SettingFarm:AddToggle('Bringmob', {
	Text = 'Bring mob',
	Default = _G.Settings.Bring_Mob,
	Tooltip = 'Bring mob',
})

Toggles.Bringmob:OnChanged(function(value)
	_G.Bring_Mob = value
	_G.Settings.Bring_Mob = value
	SaveSettings()
end)

SettingFarm:AddToggle('Bypass_TP', {
	Text = 'Bypass TP',
	Default = _G.Settings.Bypass,
	Tooltip = 'Bypass TP',
})

Toggles.Bypass_TP:OnChanged(function(value)
	_G.Bypass_TP = value
	_G.Settings.Bypass = value
	SaveSettings()
end)

SettingFarm:AddToggle('Rejoin', {
	Text = 'Auto Rejoin',
	Default = _G.Settings.Rejoin,
	Tooltip = 'Rejoin Server',
})

Toggles.Rejoin:OnChanged(function(value)
	_G.AutoRejoin = value
	_G.Settings.Rejoin = value
	SaveSettings()
end)


canHits = {}
_G.FastAttack = true

_Module_ = function()
	local Success,Error = pcall(function()
		local PC = require(game.Players.LocalPlayer.PlayerScripts.CombatFramework.Particle)
		local RL = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib)
		local DMG = require(game.Players.LocalPlayer.PlayerScripts.CombatFramework.Particle.Damage)
		local RigC = getupvalue(require(game.Players.LocalPlayer.PlayerScripts.CombatFramework.RigController), 2)
		local Combat = getupvalue(require(game.Players.LocalPlayer.PlayerScripts.CombatFramework), 2)
		local CameraShaker = require(game.ReplicatedStorage.Util.CameraShaker)
		local RigEvent = game:GetService("ReplicatedStorage").RigControllerEvent
		return {
			[1] = PC,
			[2] = RL,
			[3] = DMG,
			[4] = RigC,
			[5] = Combat,
			[6] = CameraShaker,
			[7] = RigEvent
		}
	end
	if not Success then
		warn("Module Error Send this message to mexuaita\n",Error)
	end
end

_getHits_ = function(table,self)
	local Hits = {}
	local nearbymon = false
	local Success,Error = pcall(function()
		if nearbymon then
			local Enemies = game.workspace.Enemies:GetChildren()
			local Characters = game.workspace.Characters:GetChildren()
			for i = 1, #Enemies do
				local v = Enemies[i]
				local Human = v:FindFirstChildOfClass("Humanoid")
				if Human and Human.RootPart and Human.Health > 0 and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
					canHits[#canHits + 1] = Human.RootPart
				end
			end
			for i = 1, #Characters do
				local v = Characters[i]
				if v ~= game.Players.LocalPlayer.Character then
					local Human = v:FindFirstChildOfClass("Humanoid")
					if Human and Human.RootPart and Human.Health > 0 and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
						canHits[#canHits + 1] = Human.RootPart
					end
				end
			end
		end
	end)
	if not Success then
		warn("Position Error Send this message to mexuaita\n",Error)
	end
	return Hits
end

task.spawn(function()
	local Success,Error = pcall(function()
		local Data = _Module_()[5]
		local Blank = function() end
		local Animation = Instance.new("Animation")
		local RecentlyFired = 0
		local AttackCD = 0
		local Controller
		local lastFireValid = 0
		local MaxLag = 350
		local fucker = 0.07
		local TryLag = 0

		local resetCD = function()
			local WeaponName = Controller.currentWeaponModel.Name
			local Cooldown = {
				combat = 0.07
			}
			AttackCD = tick() + (fucker and Cooldown[WeaponName:lower()] or fucker or 0.285) + ((TryLag / MaxLag) * 0.3)
			_Module_()[7]:FireServer("weaponChange", WeaponName)
			TryLag = TryLag + 0.8
			task.delay((fucker or 0.285) + (TryLag + 0.5 / MaxLag) * 0.3, function()
				TryLag = TryLag - 0.8
			end)
		end

		if not shared.orl then
			shared.orl = _Module_()[2].wrapAttackAnimationAsync
		end

		if not shared.cpc then
			shared.cpc = _Module_()[1].play
		end

		if not shared.dnew then
			shared.dnew = _Module_()[3].new
		end

		if not shared.attack then
			shared.attack = _Module_()[4].attack
		end

		_Module_()[2].wrapAttackAnimationAsync = function(a, b, c, d, func)
			if not _G.FastAttack then
				_Module_()[1].play = shared.cpc
				return shared.orl(a, b, c, 50, func)
			end

			local Radius = _G.FastAttack or 50

			if canHits and #canHits > 0 then
				_Module_()[1].play = function() end
				a:Play(0.00075, 0.01, 0.01)
				func(canHits)
				wait(a.length * 0.5)
				a:Stop()
			end
		end

		while game:GetService("RunService").Stepped:Wait() do
			if #canHits > 0 then
				Controller = Data.activeController

				if Controller and Controller.equipped and Controller.currentWeaponModel then
					if _G.FastAttack then
						if _G.FastAttack and tick() > AttackCD then
							resetCD()
						end

						if tick() - lastFireValid > 0.5 or not _G.FastAttack then
							Controller.timeToNextAttack = 0
							Controller.hitboxMagnitude = 65
							pcall(task.spawn, Controller.attack, Controller)
							lastFireValid = tick()
							_Module_()[6]:Stop()
						end

						local AID3 = Controller.anims.basic[3]
						local AID2 = Controller.anims.basic[2]
						local ID = AID3 or AID2
						Animation.AnimationId = ID
						local Playing = Controller.humanoid:LoadAnimation(Animation)
						Playing:Play(0.00075, 0.01, 0.01)
						_Module_()[7]:FireServer("hit", canHits, AID3 and 3 or 2, "")
						delay(0.5, function()
							Playing:Stop()
						end)
					end
				end
			end
		end
	end)
	if not Success then
		warn("Fast Attack Error Send this message to mexuaita\n",Error)
	end
end)


spawn(function()
	while task.wait() do
		pcall(function()
			if _G.Bring_Mob then
				for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
					if _G.Auto_Farm_Level and BringMobFarm and v.Name == QuestCheck()[3] and (v.HumanoidRootPart.Position - PosMon.Position).Magnitude <= 225 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then	
						v.HumanoidRootPart.CFrame = PosMon
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
					elseif _G.Auto_Farm_Mob_Aura and PosMonAura and (v.HumanoidRootPart.Position - PosMonAura.Position).magnitude <= 225 then
						v.HumanoidRootPart.CFrame = PosMonAura
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					elseif _G.Auto_Farm_Candy and posCandy and (v.HumanoidRootPart.Position - posCandy.Position).magnitude <= 225 then
						v.HumanoidRootPart.CFrame = posCandy
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					elseif _G.Auto_Farm_Bone and PosMonBone and (v.Name == "Reborn Skeleton" or v.Name == "Living Zombie" or v.Name == "Demonic Soul" or v.Name == "Posessed Mummy") and (v.HumanoidRootPart.Position - PosMonBone.Position).magnitude <= 225 then
						v.HumanoidRootPart.CFrame = PosMonBone
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					elseif _G.Auto_Cake_Prince and StartCakeMagnet and (v.Name == "Cookie Crafter" or v.Name == "Cake Guard" or v.Name == "Baking Staff" or v.Name == "Head Baker") and (v.HumanoidRootPart.Position - POSCAKE.Position).magnitude <= 225 then
						v.HumanoidRootPart.CFrame = POSCAKE
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					elseif _G.Auto_Musketeer_Hat and (v.HumanoidRootPart.Position - PosMon.Position).magnitude <= 225 then
						v.HumanoidRootPart.CFrame = PosMon
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					elseif _G.Auto_Farm_Mob_Aura and (v.HumanoidRootPart.Position - PosMonAura.Position).magnitude <= 225 then
						v.HumanoidRootPart.CFrame = PosMonAura
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					elseif _G.Auto_Rengoku and StartMagnet and (v.Name == "Snow Lurker" or v.Name == "Arctic Warrior") and (v.HumanoidRootPart.Position - PosMon.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
						v.Humanoid:ChangeState(14)
						v.HumanoidRootPart.CanCollide = false
						v.Head.CanCollide = false
						v.HumanoidRootPart.CFrame = PosMon
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
					elseif _G.Auto_EvoRace and StartEvoMagnet and v.Name == "Zombie" and (v.HumanoidRootPart.Position - PosMonEvo.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
						v.Humanoid:ChangeState(14)
						v.HumanoidRootPart.CanCollide = false
						v.Head.CanCollide = false
						v.HumanoidRootPart.CFrame = PosMonEvo
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
					elseif _G.Auto_Bartilo and StartMagnet and v.Name == "Swan Pirate" and (v.HumanoidRootPart.Position - PosMonBarto.Position).Magnitude <= 250 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
						v.Humanoid:ChangeState(14)
						v.HumanoidRootPart.CanCollide = false
						v.Head.CanCollide = false
						v.HumanoidRootPart.CFrame = PosMon
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
					elseif _G.Auto_Farm_Gun_Mastery and StartMasteryGunMagnet and v.Name == "Monkey" and (v.HumanoidRootPart.Position - PosMonMasteryGun.Position).Magnitude <= 225 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						v.Humanoid:ChangeState(14)
						v.HumanoidRootPart.CanCollide = false
						v.Head.CanCollide = false
						v.HumanoidRootPart.CFrame = PosMonMasteryGun
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
					elseif v.Name == "Factory Staff" and (v.HumanoidRootPart.Position - PosMonMasteryGun.Position).Magnitude <= 225 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						v.Humanoid:ChangeState(14)
						v.HumanoidRootPart.CanCollide = false
						v.Head.CanCollide = false
						v.HumanoidRootPart.CFrame = PosMonMasteryGun
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
					elseif v.Name == QuestCheck()[3] and (v.HumanoidRootPart.Position - PosMonMasteryGun.Position).Magnitude <= 225 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						v.Humanoid:ChangeState(14)
						v.HumanoidRootPart.CanCollide = false
						v.Head.CanCollide = false
						v.HumanoidRootPart.CFrame = PosMonMasteryGun
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
					elseif _G.Auto_Farm_BF_Mastery and StartMasteryFruitMagnet and v.Name == "Monkey" and (v.HumanoidRootPart.Position - PosMonMasteryFruit.Position).Magnitude <= 225 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						v.Humanoid:ChangeState(14)
						v.HumanoidRootPart.CanCollide = false
						v.Head.CanCollide = false
						v.HumanoidRootPart.CFrame = PosMonMasteryFruit
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
					elseif v.Name == "Factory Staff " and (v.HumanoidRootPart.Position - PosMonMasteryFruit.Position).Magnitude <= 225 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						v.Humanoid:ChangeState(14)
						v.HumanoidRootPart.CanCollide = false
						v.Head.CanCollide = false
						v.HumanoidRootPart.CFrame = PosMonMasteryFruit
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
					elseif v.Name == QuestCheck()[3] and (v.HumanoidRootPart.Position - PosMonMasteryFruit.Position).Magnitude <= 225 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						v.Humanoid:ChangeState(14)
						v.HumanoidRootPart.CanCollide = false
						v.Head.CanCollide = false
						v.HumanoidRootPart.CFrame = PosMonMasteryFruit
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
					end
				end
			end
		end)
	end
end)

spawn(function()
	while wait() do
		if _G.AutoRejoin then
			_G.AutoRejoin = game:GetService("CoreGui").RobloxPromptGui.promptOverlay.ChildAdded:Connect(function(child)
				if child.Name == 'ErrorPrompt' and child:FindFirstChild('MessageArea') and child.MessageArea:FindFirstChild("ErrorFrame") then
					game:GetService("TeleportService"):Teleport(game.PlaceId)
				end
			end)
		end
	end
end)

local x2Code = {
	"3BVISITS",
	"UPD16",
	"FUDD10",
	"BIGNEWS",
	"THEGREATACE",
	"SUB2GAMERROBOT_EXP1",
	"StrawHatMaine",
	"Sub2OfficialNoobie",
	"SUB2NOOBMASTER123",
	"Sub2Daigrock",
	"Axiore",
	"TantaiGaming",
	"STRAWHATMAINE",
	"Enyu_is_Pro",
	"Sub2Fer999",
	"Bluxxy",
	"JCWK",
	"Magicbus",
	"Starcodeheo",
	"SUB2UNCLEKIZARU"
}

SettingFarm:AddButton('Redeem All Codes', function()
	for i,v in pairs(x2Code) do
		UseCode(v)
	end
end)


local SkillFarm = Tabs.Main:AddRightGroupbox('Use Skill')

SkillFarm:AddToggle('SkillZ', {
	Text = 'Skill Z',
	Default = true,
	Tooltip = 'Skill Z',
})

Toggles.SkillZ:OnChanged(function(value)
	_G.Skill_Z = value
	_G.Settings.Skill_Z = value
	SaveSettings()
end)

SkillFarm:AddToggle('SkillX', {
	Text = 'Skill X',
	Default = true,
	Tooltip = 'Skill X',
})

Toggles.SkillX:OnChanged(function(value)
	_G.Skill_X = value
	_G.Settings.Skill_X = value
	SaveSettings()
end)

SkillFarm:AddToggle('SkillC', {
	Text = 'Skill C',
	Default = true,
	Tooltip = 'Skill C',
})

Toggles.SkillC:OnChanged(function(value)
	_G.Skill_C = value
	_G.Settings.Skill_C = value
	SaveSettings()
end)

SkillFarm:AddToggle('SkillV', {
	Text = 'Skill V',
	Default = true,
	Tooltip = 'Skill V',
})

Toggles.SkillV:OnChanged(function(value)
	_G.Skill_V = value
	_G.Settings.SkillV = value
	SaveSettings()
end)

local StatsSection = Tabs.Main:AddRightGroupbox('Stats')

SettingFarm:AddDropdown('Stats', {
	Values = {"Melee","Defense","Sword","Gun","Demon Fruit"},
	Default = 1,
	Multi = true,
	Text = 'Select Stats',
	Tooltip = 'Select Stats',
})

Options.Stats:OnChanged(function(value)
	_G.Settings.Select_Stats = value
	SaveSettings()
end)

Options.Slc:SetValue("Melee")


StatsSection:AddToggle('Auto_Stats', {
	Text = 'Auto Stats',
	Default = false,
	Tooltip = 'Auto Stats',
})

Toggles.AutoStatsMelee:OnChanged(function(value)
	_G.Auto_Stats = value
	_G.Settings.Auto_Stats = value
	SaveSettings()
end)

StatsSection:AddDropdown('Select_Point', {
	Values = { "10", "50", "100", "200" },
	Default = _G.Settings.Point,
	Multi = false,
	Text = 'Select Point',
	Tooltip = 'Select Point',
})

Options.Select_Point:OnChanged(function(value)
	_G.Point = value
	_G.Settings.Point = value
	SaveSettings()
end)


spawn(function()
	while wait() do
		pcall(function()
			if _G.Auto_Stats then
				for _,g in next, _G.Settings.Select_Stats do
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint",tostring(g),_G.Point)
				end
			end
		end)
	end
end)

