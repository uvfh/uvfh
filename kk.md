repeat wait() until game.Players
repeat wait() until game.Players.LocalPlayer
repeat wait() until game.ReplicatedStorage
repeat wait() until game.ReplicatedStorage:FindFirstChild("Remotes");
repeat wait() until game.Players.LocalPlayer:FindFirstChild("PlayerGui");
repeat wait() until game.Players.LocalPlayer.PlayerGui:FindFirstChild("Main");
repeat wait() until game:GetService("Players")
repeat wait() until game:GetService("Players").LocalPlayer.Character:FindFirstChild("Energy")

wait(1)

if not game:IsLoaded() then repeat game.Loaded:Wait() until game:IsLoaded() end

if game:GetService("Players").LocalPlayer.PlayerGui.Main:FindFirstChild("ChooseTeam") then
	repeat wait()
		if game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild("Main").ChooseTeam.Visible == true then
			if _G.Team == "Pirate" then
				for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton.Activated)) do                                                                                                
					v.Function()
				end
			elseif _G.Team == "Marine" then
				for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Marines.Frame.ViewportFrame.TextButton.Activated)) do                                                                                                
					v.Function()
				end
			else
				for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton.Activated)) do                                                                                                
					v.Function()
				end
			end
		end
	until game.Players.LocalPlayer.Team ~= nil and game:IsLoaded()
end

_G.Settings = {
    Auto_Farm_Level = false;
    Select_Mode_Farm = "Normal Mode";
    Select_Bring_Mob_Mode = "Bring Mob [Normal]";
	Normal_Fast_Attack = true;
    Extra_Fast_Attack = true;
	Select_Level_to_Redeem_All_Code = 1;
	Auto_Redeem_All_Code = false;
    Select_Weapon = nil;
	Auto_Superhuman = false;
	Auto_Fully_Superhuman = false;
	Auto_Death_Step = false;
	Auto_Fully_Death_Step = false;
	Auto_SharkMan_Karate = false;
	Auto_Fully_SharkMan_Karate = false;
	Auto_Electric_Claw = false;
	Auto_Dragon_Talon = false;
	Auto_God_Human = false;
	Auto_Stats_Kaitun = false;
	Auto_Stats_Melee = false;
	Auto_Stats_Defense = false;
	Auto_Stats_Sword = false;
	Auto_Stats_Gun = false;
	Auto_Stats_Devil_Fruit = false;
	Point = 1;
	Select_Devil_Fruit = nil;
	Auto_Buy_Devil_Fruit = false;
	Auto_Random_Fruit = false;
	Auto_Bring_Fruit = false;
	Auto_Store_Fruit = false;
}

local foldername = "ไก่ตัน"
local filename = "BloxFruit "..game.Players.LocalPlayer.Name.." Config.json"
 
function saveSettings()
    local HttpService = game:GetService("HttpService")
    local json = HttpService:JSONEncode(_G.Settings)
    if (writefile) then
        if isfolder(foldername) then
			if isfile(foldername.."\\"..filename) then
				writefile(foldername.."\\"..filename, json)
			else
				writefile(foldername.."\\"..filename, json)
			end
        else
            makefolder(foldername)
			writefile(foldername.."\\"..filename, json)
        end
    end
end

function loadSettings()
    local HttpService = game:GetService("HttpService")
    if isfile(foldername.."\\"..filename) then
        _G.Settings = HttpService:JSONDecode(readfile(foldername.."\\"..filename))
    end
end
 
loadSettings()

if _G.Settings.Select_Weapon == nil then
    for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
        if v.ToolTip == "Melee" then
            if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                _G.Settings.Select_Weapon = tostring(v.Name)
            end
        end
    end
end

for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
	if v.ToolTip == "Melee" then
		if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
			_G.Select_Weapon_Kill_Player_Melee = tostring(v.Name)
		end
	end
end

if _G.Settings.Select_Weapon_Law_Raid == nil then
    for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
        if v.ToolTip == "Melee" then
            if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                _G.Settings.Select_Weapon_Law_Raid = tostring(v.Name)
            end
        end
    end
end

if _G.Settings.Select_Boss == nil then
	_G.Settings.Select_Boss = "nil"
end

if game.PlaceId == 2753915549 then
	World1 = true
elseif game.PlaceId == 4442272183 then
	World2 = true
elseif game.PlaceId == 7449423635 then
	World3 = true
end
 
function CheckQuest() 
	local MyLevel = game.Players.LocalPlayer.Data.Level.Value
    if World1 then
		if MyLevel == 1 or MyLevel <= 9 or _G.Select_Mob_Farm == "Bandit [Lv. 5]" then -- Bandit
			Ms = "Bandit [Lv. 5]"
			NameQuest = "BanditQuest1"
			LevelQuest = 1
			NameMon = "Bandit"
			CFrameQuest = CFrame.new(1061.66699, 16.5166187, 1544.52905, -0.942978859, -3.33851502e-09, 0.332852632, 7.04340497e-09, 1, 2.99841325e-08, -0.332852632, 3.06188177e-08, -0.942978859)
			CFrameMon = CFrame.new(1199.31287, 52.2717781, 1536.91516, -0.929782331, 6.60215846e-08, -0.368109822, 3.9077392e-08, 1, 8.06501603e-08, 0.368109822, 6.06023249e-08, -0.929782331)
			SPAWNPOINT = "Default"
        elseif MyLevel == 10 or MyLevel <= 14 or _G.Select_Mob_Farm == "Monkey [Lv. 14]" then -- Monkey
			Ms = "Monkey [Lv. 14]"
			NameQuest = "JungleQuest"
			LevelQuest = 1
			NameMon = "Monkey"
			CFrameQuest = CFrame.new(-1604.12012, 36.8521118, 154.23732, 0.0648873374, -4.70858913e-06, -0.997892559, 1.41431883e-07, 1, -4.70933674e-06, 0.997892559, 1.64442184e-07, 0.0648873374)
			CFrameMon = CFrame.new(-1502.74609, 98.5633316, 90.6417007, 0.836947978, 0, 0.547282517, -0, 1, -0, -0.547282517, 0, 0.836947978)
			SPAWNPOINT = "Jungle"
		elseif MyLevel == 15 or MyLevel <= 29 or _G.Select_Mob_Farm == "Gorilla [Lv. 20]" then -- Gorilla
			Ms = "Gorilla [Lv. 20]"
			NameQuest = "JungleQuest"
			LevelQuest = 2
			NameMon = "Gorilla"
			CFrameQuest = CFrame.new(-1604.12012, 36.8521118, 154.23732, 0.0648873374, -4.70858913e-06, -0.997892559, 1.41431883e-07, 1, -4.70933674e-06, 0.997892559, 1.64442184e-07, 0.0648873374)
			CFrameMon = CFrame.new(-1223.52808, 6.27936459, -502.292664, 0.310949147, -5.66602516e-08, 0.950426519, -3.37275488e-08, 1, 7.06501808e-08, -0.950426519, -5.40241736e-08, 0.310949147)
			SPAWNPOINT = "Jungle"
		elseif MyLevel == 30 or MyLevel <= 39 or _G.Select_Mob_Farm == "Pirate [Lv. 35]" then -- Pirate
			Ms = "Pirate [Lv. 35]"
			NameQuest = "BuggyQuest1"
			LevelQuest = 1
			NameMon = "Pirate"
			CFrameQuest = CFrame.new(-1139.59717, 4.75205183, 3825.16211, -0.959730506, -7.5857054e-09, 0.280922383, -4.06310328e-08, 1, -1.11807175e-07, -0.280922383, -1.18718916e-07, -0.959730506)
			CFrameMon = CFrame.new(-1219.32324, 4.75205183, 3915.63452, -0.966492832, -6.91238853e-08, 0.25669381, -5.21195496e-08, 1, 7.3047012e-08, -0.25669381, 5.72206496e-08, -0.966492832)
			SPAWNPOINT = "Pirate"
		elseif MyLevel == 40 or MyLevel <= 59 or _G.Select_Mob_Farm == "Brute [Lv. 45]" then -- Brute
			Ms = "Brute [Lv. 45]"
			NameQuest = "BuggyQuest1"
			LevelQuest = 2
			NameMon = "Brute"
			CFrameQuest = CFrame.new(-1139.59717, 4.75205183, 3825.16211, -0.959730506, -7.5857054e-09, 0.280922383, -4.06310328e-08, 1, -1.11807175e-07, -0.280922383, -1.18718916e-07, -0.959730506)
			CFrameMon = CFrame.new(-1146.49646, 96.0936813, 4312.1333, -0.978175163, -1.53222057e-08, 0.207781896, -3.33316912e-08, 1, -8.31738873e-08, -0.207781896, -8.82843523e-08, -0.978175163)
			SPAWNPOINT = "Pirate"
		elseif MyLevel == 60 or MyLevel <= 74 or _G.Select_Mob_Farm == "Desert Bandit [Lv. 60]" then -- Desert Bandit
			Ms = "Desert Bandit [Lv. 60]"
			NameQuest = "DesertQuest"
			LevelQuest = 1
			NameMon = "Desert Bandit"
			CFrameQuest = CFrame.new(897.031128, 6.43846416, 4388.97168, -0.804044724, 3.68233266e-08, 0.594568789, 6.97835176e-08, 1, 3.24365246e-08, -0.594568789, 6.75715199e-08, -0.804044724)
			CFrameMon = CFrame.new(932.788818, 6.4503746, 4488.24609, -0.998625934, 3.08948351e-08, 0.0524050146, 2.79967303e-08, 1, -5.60361286e-08, -0.0524050146, -5.44919629e-08, -0.998625934)
			SPAWNPOINT = "Desert"
		elseif MyLevel == 75 or MyLevel <= 89 or _G.Select_Mob_Farm == "Desert Officer [Lv. 70]" then -- Desert Officre
			Ms = "Desert Officer [Lv. 70]"
			NameQuest = "DesertQuest"
			LevelQuest = 2
			NameMon = "Desert Officer"
			CFrameQuest = CFrame.new(897.031128, 6.43846416, 4388.97168, -0.804044724, 3.68233266e-08, 0.594568789, 6.97835176e-08, 1, 3.24365246e-08, -0.594568789, 6.75715199e-08, -0.804044724)
			CFrameMon = CFrame.new(1580.03198, 4.61375761, 4366.86426, 0.135744005, -6.44280718e-08, -0.990743816, 4.35738308e-08, 1, -5.90598574e-08, 0.990743816, -3.51534837e-08, 0.135744005)
			SPAWNPOINT = "Desert"
		elseif MyLevel == 90 or MyLevel <= 99 or _G.Select_Mob_Farm == "Snow Bandit [Lv. 90]" then -- Snow Bandits
			Ms = "Snow Bandit [Lv. 90]"
			NameQuest = "SnowQuest"
			LevelQuest = 1
			NameMon = "Snow Bandits"
			CFrameQuest = CFrame.new(1384.14001, 87.272789, -1297.06482, 0.348555952, -2.53947841e-09, -0.937287986, 1.49860568e-08, 1, 2.86358204e-09, 0.937287986, -1.50443711e-08, 0.348555952)
			CFrameMon = CFrame.new(1370.24316, 102.403511, -1411.52905, 0.980274439, -1.12995728e-08, 0.197641045, -9.57343449e-09, 1, 1.04655214e-07, -0.197641045, -1.04482936e-07, 0.980274439)
			SPAWNPOINT = "Ice"
		elseif MyLevel == 100 or MyLevel <= 119 or _G.Select_Mob_Farm == "Snowman [Lv. 100]"  then -- Snowman
			Ms = "Snowman [Lv. 100]"
			NameQuest = "SnowQuest"
			LevelQuest = 2
			NameMon = "Snowman"
			CFrameQuest = CFrame.new(1384.14001, 87.272789, -1297.06482, 0.348555952, -2.53947841e-09, -0.937287986, 1.49860568e-08, 1, 2.86358204e-09, 0.937287986, -1.50443711e-08, 0.348555952)
			CFrameMon = CFrame.new(1370.24316, 102.403511, -1411.52905, 0.980274439, -1.12995728e-08, 0.197641045, -9.57343449e-09, 1, 1.04655214e-07, -0.197641045, -1.04482936e-07, 0.980274439)
			SPAWNPOINT = "Ice"
		elseif MyLevel == 120 or MyLevel <= 149 or _G.Select_Mob_Farm == "Chief Petty Officer [Lv. 120]" then -- Chief Petty Officer
			Ms = "Chief Petty Officer [Lv. 120]"
			NameQuest = "MarineQuest2"
			LevelQuest = 1
			NameMon = "Chief Petty Officer"
			CFrameQuest = CFrame.new(-5035.0835, 28.6520386, 4325.29443, 0.0243340395, -7.08064647e-08, 0.999703884, -6.36926814e-08, 1, 7.23777944e-08, -0.999703884, -6.54350671e-08, 0.0243340395)
			CFrameMon = CFrame.new(-4882.8623, 22.6520386, 4255.53516, 0.273695946, -5.40380647e-08, -0.96181643, 4.37720793e-08, 1, -4.37274998e-08, 0.96181643, -3.01326679e-08, 0.273695946)
			SPAWNPOINT = "MarineBase"
		elseif MyLevel == 150 or MyLevel <= 174 or _G.Select_Mob_Farm == "Sky Bandit [Lv. 150]" then -- Sky Bandit
			Ms = "Sky Bandit [Lv. 150]"
			NameQuest = "SkyQuest"
			LevelQuest = 1
			NameMon = "Sky Bandit"
			CFrameQuest = CFrame.new(-4841.83447, 717.669617, -2623.96436, -0.875942111, 5.59710216e-08, -0.482416272, 3.04023082e-08, 1, 6.08195947e-08, 0.482416272, 3.86078725e-08, -0.875942111)
			CFrameMon = CFrame.new(-4970.74219, 294.544342, -2890.11353, -0.994874597, -8.61311236e-08, -0.101116329, -9.10836206e-08, 1, 4.43614923e-08, 0.101116329, 5.33441664e-08, -0.994874597)
			SPAWNPOINT = "Sky"
		elseif MyLevel == 175 or MyLevel <= 189 or _G.Select_Mob_Farm == "Dark Master [Lv. 175]" then -- Dark Master
			Ms = "Dark Master [Lv. 175]"
			NameQuest = "SkyQuest"
			LevelQuest = 2
			NameMon = "Dark Master"
			CFrameQuest = CFrame.new(-4841.83447, 717.669617, -2623.96436, -0.875942111, 5.59710216e-08, -0.482416272, 3.04023082e-08, 1, 6.08195947e-08, 0.482416272, 3.86078725e-08, -0.875942111)
			CFrameMon = CFrame.new(-5220.58594, 430.693298, -2278.17456, -0.925375521, 1.12086873e-08, 0.379051805, -1.05115507e-08, 1, -5.52320891e-08, -0.379051805, -5.50948407e-08, -0.925375521)
			SPAWNPOINT = "Sky"
		elseif MyLevel == 190 or MyLevel <= 209 or _G.Select_Mob_Farm == "Prisoner [Lv. 190]" then
			Ms = "Prisoner [Lv. 190]"
			NameQuest = "PrisonerQuest"
			LevelQuest = 1
			NameMon = "Prisoner"
			CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
			CFrameMon = CFrame.new(5433.39307, 88.678093, 514.986877, 0.879988372, 0, -0.474995494, 0, 1, 0, 0.474995494, 0, 0.879988372)
			SPAWNPOINT = "Prison"
		elseif MyLevel == 210 or MyLevel <= 249 or _G.Select_Mob_Farm == "Dangerous Prisoner [Lv. 210]" then
			Ms = "Dangerous Prisoner [Lv. 210]"
			NameQuest = "PrisonerQuest"
			LevelQuest = 2
			NameMon = "Dangerous Prisoner"
			CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
			CFrameMon = CFrame.new(5433.39307, 88.678093, 514.986877, 0.879988372, 0, -0.474995494, 0, 1, 0, 0.474995494, 0, 0.879988372)
			SPAWNPOINT = "Prison"
		elseif MyLevel == 250 or MyLevel <= 274 or _G.Select_Mob_Farm == "Toga Warrior [Lv. 225]" then -- Toga Warrior
			Ms = "Toga Warrior [Lv. 250]"
			NameQuest = "ColosseumQuest"
			LevelQuest = 1
			NameMon = "Toga Warrior"
			CFrameQuest = CFrame.new(-1576.11743, 7.38933945, -2983.30762, 0.576966345, 1.22114863e-09, 0.816767931, -3.58496594e-10, 1, -1.24185606e-09, -0.816767931, 4.2370063e-10, 0.576966345)
			CFrameMon = CFrame.new(-1779.97583, 44.6077499, -2736.35474, 0.984437346, 4.10396339e-08, 0.175734788, -3.62286876e-08, 1, -3.05844168e-08, -0.175734788, 2.3741821e-08, 0.984437346)
			SPAWNPOINT = "Colosseum"
		elseif MyLevel == 275 or MyLevel <= 299 or _G.Select_Mob_Farm == "Gladiator [Lv. 275]" then -- Gladiato
			Ms = "Gladiator [Lv. 275]"
			NameQuest = "ColosseumQuest"
			LevelQuest = 2
			NameMon = "Gladiato"
			CFrameQuest = CFrame.new(-1576.11743, 7.38933945, -2983.30762, 0.576966345, 1.22114863e-09, 0.816767931, -3.58496594e-10, 1, -1.24185606e-09, -0.816767931, 4.2370063e-10, 0.576966345)
			CFrameMon = CFrame.new(-1274.75903, 58.1895943, -3188.16309, 0.464524001, 6.21005611e-08, 0.885560572, -4.80449414e-09, 1, -6.76054768e-08, -0.885560572, 2.71497012e-08, 0.464524001)
			SPAWNPOINT = "Colosseum"
		elseif MyLevel == 300 or MyLevel <= 324 or _G.Select_Mob_Farm == "Military Soldier [Lv. 300]" then -- Military Soldier
			Ms = "Military Soldier [Lv. 300]"
			NameQuest = "MagmaQuest"
			LevelQuest = 1
			NameMon = "Military Soldier"
			CFrameQuest = CFrame.new(-5316.55859, 12.2370615, 8517.2998, 0.588437557, -1.37880001e-08, -0.808542669, -2.10116209e-08, 1, -3.23446478e-08, 0.808542669, 3.60215964e-08, 0.588437557)
			CFrameMon = CFrame.new(-5363.01123, 41.5056877, 8548.47266, -0.578253984, -3.29503091e-10, 0.815856814, 9.11209668e-08, 1, 6.498761e-08, -0.815856814, 1.11920997e-07, -0.578253984)
			SPAWNPOINT = "Magma"
		elseif MyLevel == 325 or MyLevel <= 374 or _G.Select_Mob_Farm == "Military Spy [Lv. 330]" then -- Military Spy
			Ms = "Military Spy [Lv. 325]"
			NameQuest = "MagmaQuest"
			LevelQuest = 2
			NameMon = "Military Spy"
			CFrameQuest = CFrame.new(-5316.55859, 12.2370615, 8517.2998, 0.588437557, -1.37880001e-08, -0.808542669, -2.10116209e-08, 1, -3.23446478e-08, 0.808542669, 3.60215964e-08, 0.588437557)
			CFrameMon = CFrame.new(-5787.99023, 120.864456, 8762.25293, -0.188358366, -1.84706277e-08, 0.982100308, -1.23782129e-07, 1, -4.93306951e-09, -0.982100308, -1.22495649e-07, -0.188358366)
			SPAWNPOINT = "Magma"
		elseif MyLevel == 375 or MyLevel <= 399 or _G.Select_Mob_Farm == "Fishman Warrior [Lv. 375]" then -- Fishman Warrior
			Ms = "Fishman Warrior [Lv. 375]"
			NameQuest = "FishmanQuest"
			LevelQuest = 1
			NameMon = "Fishman Warrior"
			CFrameQuest = CFrame.new(61122.5625, 18.4716396, 1568.16504, 0.893533468, 3.95251609e-09, 0.448996574, -2.34327455e-08, 1, 3.78297464e-08, -0.448996574, -4.43233645e-08, 0.893533468)
			CFrameMon = CFrame.new(60946.6094, 48.6735229, 1525.91687, -0.0817126185, 8.90751153e-08, 0.996655822, 2.00889794e-08, 1, -8.77269599e-08, -0.996655822, 1.28533992e-08, -0.0817126185)
			SPAWNPOINT = "Fountain"
        elseif MyLevel == 400 or MyLevel <= 449 or _G.Select_Mob_Farm == "Fishman Commando [Lv. 400]" then -- Fishman Commando
			Ms = "Fishman Commando [Lv. 400]"
			NameQuest = "FishmanQuest"
			LevelQuest = 2
			NameMon = "Fishman Commando"
			CFrameQuest = CFrame.new(61122.5625, 18.4716396, 1568.16504, 0.893533468, 3.95251609e-09, 0.448996574, -2.34327455e-08, 1, 3.78297464e-08, -0.448996574, -4.43233645e-08, 0.893533468)
			CFrameMon = CFrame.new(61885.5039, 18.4828243, 1504.17896, 0.577502489, 0, -0.816389024, -0, 1.00000012, -0, 0.816389024, 0, 0.577502489)
			SPAWNPOINT = "Fountain"
        elseif MyLevel == 450 or MyLevel <= 474 or _G.Select_Mob_Farm == "God's Guard [Lv. 450]" then -- God's Guards
			Ms = "God's Guard [Lv. 450]"
			NameQuest = "SkyExp1Quest"
			LevelQuest = 1
			NameMon = "God's Guards"
			CFrameQuest = CFrame.new(-4721.71436, 845.277161, -1954.20105, -0.999277651, -5.56969759e-09, 0.0380011722, -4.14751478e-09, 1, 3.75035256e-08, -0.0380011722, 3.73188307e-08, -0.999277651)
			CFrameMon = CFrame.new(-4716.95703, 853.089722, -1933.92542, -0.93441087, -6.77488776e-09, -0.356197298, 1.12145182e-08, 1, -4.84390199e-08, 0.356197298, -4.92565206e-08, -0.93441087)
			SPAWNPOINT = "Sky"
        elseif MyLevel == 475 or MyLevel <= 524 or _G.Select_Mob_Farm == "Shanda [Lv. 475]" then -- Shandas
            sky = false
			Ms = "Shanda [Lv. 475]"
			NameQuest = "SkyExp1Quest"
			LevelQuest = 2
			NameMon = "Shandas"
			CFrameQuest = CFrame.new(-7863.63672, 5545.49316, -379.826324, 0.362120807, -1.98046344e-08, -0.93213129, 4.05822291e-08, 1, -5.48095125e-09, 0.93213129, -3.58431969e-08, 0.362120807)
			CFrameMon = CFrame.new(-7685.12354, 5601.05127, -443.171509, 0.150056243, 1.79768236e-08, -0.988677442, 6.67798661e-09, 1, 1.91962481e-08, 0.988677442, -9.48289181e-09, 0.150056243)
			SPAWNPOINT = "Sky"
        elseif MyLevel == 525 or MyLevel <= 549 or _G.Select_Mob_Farm == "Royal Squad [Lv. 525]" then -- Royal Squad
            sky = true
			Ms = "Royal Squad [Lv. 525]"
			NameQuest = "SkyExp2Quest"
			LevelQuest = 1
			NameMon = "Royal Squad"
			CFrameQuest = CFrame.new(-7902.66895, 5635.96387, -1411.71802, 0.0504222959, 2.5710392e-08, 0.998727977, 1.12541557e-07, 1, -3.14249675e-08, -0.998727977, 1.13982921e-07, 0.0504222959)
			CFrameMon = CFrame.new(-7685.02051, 5606.87842, -1442.729, 0.561947823, 7.69527464e-09, -0.827172697, -4.24974544e-09, 1, 6.41599973e-09, 0.827172697, -9.01838604e-11, 0.561947823)
			SPAWNPOINT = "Sky2"
		elseif MyLevel == 550 or MyLevel <= 624 or _G.Select_Mob_Farm == "Royal Soldier [Lv. 550]" then -- Royal Soldier
            Dis = 240
            sky = true
			Ms = "Royal Soldier [Lv. 550]"
			NameQuest = "SkyExp2Quest"
			LevelQuest = 2
			NameMon = "Royal Soldier"
			CFrameQuest = CFrame.new(-7902.66895, 5635.96387, -1411.71802, 0.0504222959, 2.5710392e-08, 0.998727977, 1.12541557e-07, 1, -3.14249675e-08, -0.998727977, 1.13982921e-07, 0.0504222959)
			CFrameMon = CFrame.new(-7864.44775, 5661.94092, -1708.22351, 0.998389959, 2.28686137e-09, -0.0567218624, 1.99431383e-09, 1, 7.54200258e-08, 0.0567218624, -7.54117195e-08, 0.998389959)
			SPAWNPOINT = "Sky2"
		elseif MyLevel == 625 or MyLevel <= 649 or _G.Select_Mob_Farm == "Galley Pirate [Lv. 625]" then -- Galley Pirate
            Dis = 240
            sky = false
			Ms = "Galley Pirate [Lv. 625]"
			NameQuest = "FountainQuest"
			LevelQuest = 1
			NameMon = "Galley Pirate"
			CFrameQuest = CFrame.new(5254.60156, 38.5011406, 4049.69678, -0.0504891425, -3.62066501e-08, -0.998724639, -9.87921389e-09, 1, -3.57534553e-08, 0.998724639, 8.06145284e-09, -0.0504891425)
			CFrameMon = CFrame.new(5595.06982, 41.5013695, 3961.47095, -0.992138803, -2.11610267e-08, -0.125142589, -1.34249509e-08, 1, -6.26613996e-08, 0.125142589, -6.04887518e-08, -0.992138803)
			SPAWNPOINT = "Fountain"
		elseif MyLevel >= 650 or _G.Select_Mob_Farm == "Galley Captain [Lv. 650]" then -- Galley Captain
            Dis = 240
			Ms = "Galley Captain [Lv. 650]"
			NameQuest = "FountainQuest"
			LevelQuest = 2
			NameMon = "Galley Captain"
			CFrameQuest = CFrame.new(5254.60156, 38.5011406, 4049.69678, -0.0504891425, -3.62066501e-08, -0.998724639, -9.87921389e-09, 1, -3.57534553e-08, 0.998724639, 8.06145284e-09, -0.0504891425)
			CFrameMon = CFrame.new(5658.5752, 38.5361786, 4928.93506, -0.996873081, 2.12391046e-06, -0.0790185928, 2.16989656e-06, 1, -4.96097414e-07, 0.0790185928, -6.66008248e-07, -0.996873081)
			SPAWNPOINT = "Fountain"
		end
    elseif World2 then
		if MyLevel == 700 or MyLevel <= 724 or _G.Select_Mob_Farm == "Raider [Lv. 700]" then -- Raider [Lv. 700]
			Ms = "Raider [Lv. 700]"
			NameQuest = "Area1Quest"
			LevelQuest = 1
			NameMon = "Raider"
			CFrameQuest = CFrame.new(-424.080078, 73.0055847, 1836.91589, 0.253544956, -1.42165932e-08, 0.967323601, -6.00147771e-08, 1, 3.04272909e-08, -0.967323601, -6.5768397e-08, 0.253544956)
			CFrameMon = CFrame.new(-737.026123, 39.1748352, 2392.57959, 0.272128761, 0, -0.962260842, -0, 1, -0, 0.962260842, 0, 0.272128761)
			SPAWNPOINT = "DressTown"
		elseif MyLevel == 725 or MyLevel <= 774 or _G.Select_Mob_Farm == "Mercenary [Lv. 725]" then -- Mercenary [Lv. 725]
			Ms = "Mercenary [Lv. 725]"
			NameQuest = "Area1Quest"
			LevelQuest = 2
			NameMon = "Mercenary"
			CFrameQuest = CFrame.new(-424.080078, 73.0055847, 1836.91589, 0.253544956, -1.42165932e-08, 0.967323601, -6.00147771e-08, 1, 3.04272909e-08, -0.967323601, -6.5768397e-08, 0.253544956)
			CFrameMon = CFrame.new(-973.731995, 95.8733215, 1836.46936, 0.999135971, 2.02326991e-08, -0.0415605344, -1.90767793e-08, 1, 2.82094952e-08, 0.0415605344, -2.73922804e-08, 0.999135971)
			SPAWNPOINT = "DressTown"
		elseif MyLevel == 775 or MyLevel <= 799 or _G.Select_Mob_Farm == "Swan Pirate [Lv. 775]" then -- Swan Pirate [Lv. 775]
			Ms = "Swan Pirate [Lv. 775]"
			NameQuest = "Area2Quest"
			LevelQuest = 1
			NameMon = "Swan Pirate"
			CFrameQuest = CFrame.new(632.698608, 73.1055908, 918.666321, -0.0319722369, 8.96074881e-10, -0.999488771, 1.36326533e-10, 1, 8.92172336e-10, 0.999488771, -1.07732087e-10, -0.0319722369)
			CFrameMon = CFrame.new(970.369446, 142.653198, 1217.3667, 0.162079468, -4.85452638e-08, -0.986777723, 1.03357589e-08, 1, -4.74980872e-08, 0.986777723, -2.50063148e-09, 0.162079468)
			SPAWNPOINT = "DressTown"
		elseif MyLevel == 800 or MyLevel <= 874 or _G.Select_Mob_Farm == "Factory Staff [Lv. 800]" then -- Factory Staff [Lv. 800]
			Ms = "Factory Staff [Lv. 800]"
			NameQuest = "Area2Quest"
			LevelQuest = 2
			NameMon = "Factory Staff"
			CFrameQuest = CFrame.new(632.698608, 73.1055908, 918.666321, -0.0319722369, 8.96074881e-10, -0.999488771, 1.36326533e-10, 1, 8.92172336e-10, 0.999488771, -1.07732087e-10, -0.0319722369)
			CFrameMon = CFrame.new(296.786499, 72.9948196, -57.1298141, -0.876037002, -5.32364979e-08, 0.482243896, -3.87658332e-08, 1, 3.99718729e-08, -0.482243896, 1.63222538e-08, -0.876037002)
			SPAWNPOINT = "DressTown"
		elseif MyLevel == 875 or MyLevel <= 899 or _G.Select_Mob_Farm == "Marine Lieutenant [Lv. 875]" then -- Marine Lieutenant [Lv. 875]
			Ms = "Marine Lieutenant [Lv. 875]"
			NameQuest = "MarineQuest3"
			LevelQuest = 1
			NameMon = "Marine Lieutenant"
			CFrameQuest = CFrame.new(-2442.65015, 73.0511475, -3219.11523, -0.873540044, 4.2329841e-08, -0.486752301, 5.64383384e-08, 1, -1.43220786e-08, 0.486752301, -3.99823996e-08, -0.873540044)
			CFrameMon = CFrame.new(-2913.26367, 73.0011826, -2971.64282, 0.910507619, 0, 0.413492233, 0, 1.00000012, 0, -0.413492233, 0, 0.910507619)
			SPAWNPOINT = "Greenb"
		elseif MyLevel == 900 or MyLevel <= 949 or _G.Select_Mob_Farm == "Marine Captain [Lv. 900]" then -- Marine Captain [Lv. 900]
			Ms = "Marine Captain [Lv. 900]"
			NameQuest = "MarineQuest3"
			LevelQuest = 2
			NameMon = "Marine Captain"
			CFrameQuest = CFrame.new(-2442.65015, 73.0511475, -3219.11523, -0.873540044, 4.2329841e-08, -0.486752301, 5.64383384e-08, 1, -1.43220786e-08, 0.486752301, -3.99823996e-08, -0.873540044)
			CFrameMon = CFrame.new(-1868.67688, 73.0011826, -3321.66333, -0.971402287, 1.06502087e-08, 0.237439692, 3.68856199e-08, 1, 1.06050372e-07, -0.237439692, 1.11775684e-07, -0.971402287)
			SPAWNPOINT = "Greenb"
		elseif MyLevel == 950 or MyLevel <= 974 or _G.Select_Mob_Farm == "Zombie [Lv. 950]" then -- Zombie [Lv. 950]
			Ms = "Zombie [Lv. 950]"
			NameQuest = "ZombieQuest"
			LevelQuest = 1
			NameMon = "Zombie"
			CFrameQuest = CFrame.new(-5492.79395, 48.5151672, -793.710571, 0.321800292, -6.24695815e-08, 0.946807742, 4.05616092e-08, 1, 5.21931227e-08, -0.946807742, 2.16082796e-08, 0.321800292)
			CFrameMon = CFrame.new(-5634.83838, 126.067039, -697.665039, -0.992770672, 6.77618939e-09, 0.120025545, 1.65461245e-08, 1, 8.04023372e-08, -0.120025545, 8.18070234e-08, -0.992770672)
			SPAWNPOINT = "Graveyard"
		elseif MyLevel == 975 or MyLevel <= 999 or _G.Select_Mob_Farm == "Vampire [Lv. 975]" then -- Vampire [Lv. 975]
			Ms = "Vampire [Lv. 975]"
			NameQuest = "ZombieQuest"
			LevelQuest = 2
			NameMon = "Vampire"
			CFrameQuest = CFrame.new(-5492.79395, 48.5151672, -793.710571, 0.321800292, -6.24695815e-08, 0.946807742, 4.05616092e-08, 1, 5.21931227e-08, -0.946807742, 2.16082796e-08, 0.321800292)
			CFrameMon = CFrame.new(-6030.32031, 6.4377408, -1313.5564, -0.856965423, 3.9138893e-08, -0.515373945, -1.12178942e-08, 1, 9.45958547e-08, 0.515373945, 8.68467822e-08, -0.856965423)
			SPAWNPOINT = "Graveyard"
		elseif MyLevel == 1000 or MyLevel <= 1049 or _G.Select_Mob_Farm == "Snow Trooper [Lv. 1000]" then -- Snow Trooper [Lv. 1000] **
			Ms = "Snow Trooper [Lv. 1000]"
			NameQuest = "SnowMountainQuest"
			LevelQuest = 1
			NameMon = "Snow Trooper"
			CFrameQuest = CFrame.new(604.964966, 401.457062, -5371.69287, 0.353063971, 1.89520435e-08, -0.935599446, -5.81846002e-08, 1, -1.70033754e-09, 0.935599446, 5.50377841e-08, 0.353063971)
			CFrameMon = CFrame.new(535.893433, 401.457062, -5329.6958, -0.999524176, 0, 0.0308452044, 0, 1, -0, -0.0308452044, 0, -0.999524176)
			SPAWNPOINT = "Snowy"
		elseif MyLevel == 1050 or MyLevel <= 1099 or _G.Select_Mob_Farm == "Winter Warrior [Lv. 1050]" then -- Winter Warrior [Lv. 1050]
			Ms = "Winter Warrior [Lv. 1050]"
			NameQuest = "SnowMountainQuest"
			LevelQuest = 2
			NameMon = "Winter Warrior"
			CFrameQuest = CFrame.new(604.964966, 401.457062, -5371.69287, 0.353063971, 1.89520435e-08, -0.935599446, -5.81846002e-08, 1, -1.70033754e-09, 0.935599446, 5.50377841e-08, 0.353063971)
			CFrameMon = CFrame.new(1223.7417, 454.575226, -5170.02148, 0.473996818, 2.56845354e-08, 0.880526543, -5.62456428e-08, 1, 1.10811016e-09, -0.880526543, -5.00510211e-08, 0.473996818)
			SPAWNPOINT = "Snowy"
		elseif MyLevel == 1100 or MyLevel <= 1124 or _G.Select_Mob_Farm == "Lab Subordinate [Lv. 1100]" then -- Lab Subordinate [Lv. 1100]
			Ms = "Lab Subordinate [Lv. 1100]"
			NameQuest = "IceSideQuest"
			LevelQuest = 1
			NameMon = "Lab Subordinate"
			CFrameQuest = CFrame.new(-6060.10693, 15.9868021, -4904.7876, -0.411000341, -5.06538868e-07, 0.91163528, 1.26306062e-07, 1, 6.12581289e-07, -0.91163528, 3.66916197e-07, -0.411000341)
			CFrameMon = CFrame.new(-5769.2041, 37.9288292, -4468.38721, -0.569419742, -2.49055017e-08, 0.822046936, -6.96206541e-08, 1, -1.79282633e-08, -0.822046936, -6.74401548e-08, -0.569419742)
			SPAWNPOINT = "CircleIslandIce"
		elseif MyLevel == 1125 or MyLevel <= 1174 or _G.Select_Mob_Farm == "Horned Warrior [Lv. 1125]" then -- Horned Warrior [Lv. 1125]
			Ms = "Horned Warrior [Lv. 1125]"
			NameQuest = "IceSideQuest"
			LevelQuest = 2
			NameMon = "Horned Warrior"
			CFrameQuest = CFrame.new(-6060.10693, 15.9868021, -4904.7876, -0.411000341, -5.06538868e-07, 0.91163528, 1.26306062e-07, 1, 6.12581289e-07, -0.91163528, 3.66916197e-07, -0.411000341)
			CFrameMon = CFrame.new(-6400.85889, 24.7645149, -5818.63574, -0.964845479, 8.65926566e-08, -0.262817472, 3.98261392e-07, 1, -1.13260398e-06, 0.262817472, -1.19745812e-06, -0.964845479)
			SPAWNPOINT = "CircleIslandIce"
		elseif MyLevel == 1175 or MyLevel <= 1199 or _G.Select_Mob_Farm == "Magma Ninja [Lv. 1175]" then -- Magma Ninja [Lv. 1175]
			Ms = "Magma Ninja [Lv. 1175]"
			NameQuest = "FireSideQuest"
			LevelQuest = 1
			NameMon = "Magma Ninja"
			CFrameQuest = CFrame.new(-5431.09473, 15.9868021, -5296.53223, 0.831796765, 1.15322464e-07, -0.555080295, -1.10814341e-07, 1, 4.17010995e-08, 0.555080295, 2.68240168e-08, 0.831796765)
			CFrameMon = CFrame.new(-5496.65576, 58.6890411, -5929.76855, -0.885073781, 0, -0.465450764, 0, 1.00000012, -0, 0.465450764, 0, -0.885073781)
			SPAWNPOINT = "CircleIslandFire"
		elseif MyLevel == 1200 or MyLevel <= 1249 or _G.Select_Mob_Farm == "Lava Pirate [Lv. 1200]" then -- Lava Pirate [Lv. 1200]
			Ms = "Lava Pirate [Lv. 1200]"
			NameQuest = "FireSideQuest"
			LevelQuest = 2
			NameMon = "Lava Pirate"
			CFrameQuest = CFrame.new(-5431.09473, 15.9868021, -5296.53223, 0.831796765, 1.15322464e-07, -0.555080295, -1.10814341e-07, 1, 4.17010995e-08, 0.555080295, 2.68240168e-08, 0.831796765)
			CFrameMon = CFrame.new(-5169.71729, 34.1234779, -4669.73633, -0.196780294, 0, 0.98044765, 0, 1.00000012, -0, -0.98044765, 0, -0.196780294)
			SPAWNPOINT = "CircleIslandFire"
		elseif MyLevel == 1250 or MyLevel <= 1274 or _G.Select_Mob_Farm == "Ship Deckhand [Lv. 1250]" then -- Ship Deckhand [Lv. 1250]
			Ms = "Ship Deckhand [Lv. 1250]"
			NameQuest = "ShipQuest1"
			LevelQuest = 1
			NameMon = "Ship Deckhand"
			CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016, -0.244533166, -0, -0.969640911, -0, 1.00000012, -0, 0.96964103, 0, -0.244533136)
			CFrameMon = CFrame.new(1163.80872, 138.288452, 33058.4258, -0.998580813, 5.49076979e-08, -0.0532564968, 5.57436763e-08, 1, -1.42118655e-08, 0.0532564968, -1.71604082e-08, -0.998580813)
			SPAWNPOINT = "Ship"
        elseif MyLevel == 1275 or MyLevel <= 1299 or _G.Select_Mob_Farm == "Ship Engineer [Lv. 1275]"  then -- Ship Engineer [Lv. 1275]
			Ms = "Ship Engineer [Lv. 1275]"
			NameQuest = "ShipQuest1"
			LevelQuest = 2
			NameMon = "Ship Engineer"
			CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016, -0.244533166, -0, -0.969640911, -0, 1.00000012, -0, 0.96964103, 0, -0.244533136)
			CFrameMon = CFrame.new(916.666504, 44.0920448, 32917.207, -0.99746871, -4.85034697e-08, -0.0711069331, -4.8925461e-08, 1, 4.19294288e-09, 0.0711069331, 7.66126895e-09, -0.99746871)
			SPAWNPOINT = "Ship"
        elseif MyLevel == 1300 or MyLevel <= 1324 or _G.Select_Mob_Farm == "Ship Steward [Lv. 1300]" then -- Ship Steward [Lv. 1300]
			Ms = "Ship Steward [Lv. 1300]"
			NameQuest = "ShipQuest2"
			LevelQuest = 1
			NameMon = "Ship Steward"
			CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125, -0.869560242, 1.51905191e-08, -0.493826836, 1.44108379e-08, 1, 5.38534195e-09, 0.493826836, -2.43357912e-09, -0.869560242)
			CFrameMon = CFrame.new(918.743286, 129.591064, 33443.4609, -0.999792814, -1.7070947e-07, -0.020350717, -1.72559169e-07, 1, 8.91351277e-08, 0.020350717, 9.2628369e-08, -0.999792814)
			SPAWNPOINT = "Ship"
        elseif MyLevel == 1325 or MyLevel <= 1349 or _G.Select_Mob_Farm == "Ship Officer [Lv. 1325]" then -- Ship Officer [Lv. 1325]
			Ms = "Ship Officer [Lv. 1325]"
			NameQuest = "ShipQuest2"
			LevelQuest = 2
			NameMon = "Ship Officer"
			CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125, -0.869560242, 1.51905191e-08, -0.493826836, 1.44108379e-08, 1, 5.38534195e-09, 0.493826836, -2.43357912e-09, -0.869560242)
			CFrameMon = CFrame.new(786.051941, 181.474106, 33303.2969, 0.999285698, -5.32193063e-08, 0.0377905183, 5.68968588e-08, 1, -9.62386864e-08, -0.0377905183, 9.83201005e-08, 0.999285698)
			SPAWNPOINT = "Ship"
        elseif MyLevel == 1350 or MyLevel <= 1374 or _G.Select_Mob_Farm == "Arctic Warrior [Lv. 1350]" then -- Arctic Warrior [Lv. 1350]
			Ms = "Arctic Warrior [Lv. 1350]"
			NameQuest = "FrostQuest"
			LevelQuest = 1
			NameMon = "Arctic Warrior"
			CFrameQuest = CFrame.new(5669.43506, 28.2117786, -6482.60107, 0.888092756, 1.02705066e-07, 0.459664226, -6.20391774e-08, 1, -1.03572376e-07, -0.459664226, 6.34646895e-08, 0.888092756)
			CFrameMon = CFrame.new(5995.07471, 57.3188477, -6183.47314, 0.702747107, -1.53454167e-07, -0.711440146, -1.08168464e-07, 1, -3.22542007e-07, 0.711440146, 3.03620908e-07, 0.702747107)
			SPAWNPOINT = "IceCastle"
        elseif MyLevel == 1375 or MyLevel <= 1424 or _G.Select_Mob_Farm == "Snow Lurker [Lv. 1375]" then -- Snow Lurker [Lv. 1375]
			Ms = "Snow Lurker [Lv. 1375]"
			NameQuest = "FrostQuest"
			LevelQuest = 2
			NameMon = "Snow Lurker"
			CFrameQuest = CFrame.new(5669.43506, 28.2117786, -6482.60107, 0.888092756, 1.02705066e-07, 0.459664226, -6.20391774e-08, 1, -1.03572376e-07, -0.459664226, 6.34646895e-08, 0.888092756)
			CFrameMon = CFrame.new(5518.00684, 60.5559731, -6828.80518, -0.650781393, -3.64292951e-08, 0.759265184, -4.07668654e-09, 1, 4.44854642e-08, -0.759265184, 2.58550248e-08, -0.650781393)
			SPAWNPOINT = "IceCastle"
		elseif MyLevel == 1425 or MyLevel <= 1449 or _G.Select_Mob_Farm == "Sea Soldier [Lv. 1425]" then -- Sea Soldier [Lv. 1425]
			Ms = "Sea Soldier [Lv. 1425]"
			NameQuest = "ForgottenQuest"
			LevelQuest = 1
			NameMon = "Sea Soldier"
			CFrameQuest = CFrame.new(-3052.99097, 236.881363, -10148.1943, -0.997911751, 4.42321983e-08, 0.064591676, 4.90968759e-08, 1, 7.37270085e-08, -0.064591676, 7.67442998e-08, -0.997911751)
			CFrameMon = CFrame.new(-3029.78467, 66.944252, -9777.38184, -0.998552859, 1.09555076e-08, 0.0537791774, 7.79564235e-09, 1, -5.89660658e-08, -0.0537791774, -5.84614881e-08, -0.998552859)
			SPAWNPOINT = "ForgottenIsland"
		elseif MyLevel >= 1450 or _G.Select_Mob_Farm == "Water Fighter [Lv. 1450]" then -- Water Fighter [Lv. 1450]
			Ms = "Water Fighter [Lv. 1450]"
			NameQuest = "ForgottenQuest"
			LevelQuest = 2
			NameMon = "Water Fighter"
			CFrameQuest = CFrame.new(-3052.99097, 236.881363, -10148.1943, -0.997911751, 4.42321983e-08, 0.064591676, 4.90968759e-08, 1, 7.37270085e-08, -0.064591676, 7.67442998e-08, -0.997911751)
			CFrameMon = CFrame.new(-3262.00098, 298.699615, -10553.6943, -0.233570755, -4.57538185e-08, 0.972339869, -5.80986068e-08, 1, 3.30992194e-08, -0.972339869, -4.87605725e-08, -0.233570755)
			SPAWNPOINT = "ForgottenIsland"
		end
	elseif World3 then
		if MyLevel == 1500 or MyLevel <= 1524 or _G.Select_Mob_Farm == "Pirate Millionaire [Lv. 1500]" then
			Ms = "Pirate Millionaire [Lv. 1500]"
			NameQuest = "PiratePortQuest"
			LevelQuest = 1
			NameMon = "Pirate Millionaire"
			CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
			CFrameMon = CFrame.new(81.164993286133, 43.755737304688, 5724.7021484375)
			SPAWNPOINT = "Default"
		elseif MyLevel == 1525 or MyLevel <= 1574 or _G.Select_Mob_Farm == "Pistol Billionaire [Lv. 1525]" then
			Ms = "Pistol Billionaire [Lv. 1525]"
			NameQuest = "PiratePortQuest"
			LevelQuest = 2
			NameMon = "Pistol Billionaire"
			CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
			CFrameMon = CFrame.new(81.164993286133, 43.755737304688, 5724.7021484375)
			SPAWNPOINT = "Default"
		elseif MyLevel == 1575 or MyLevel <= 1599 or _G.Select_Mob_Farm == "Dragon Crew Warrior [Lv. 1575]" then
			Ms = "Dragon Crew Warrior [Lv. 1575]"
			NameQuest = "AmazonQuest"
			LevelQuest = 1
			NameMon = "Dragon Crew Warrior"
			CFrameQuest = CFrame.new(5832.83594, 51.6806107, -1101.51563, 0.898790359, -0, -0.438378751, 0, 1, -0, 0.438378751, 0, 0.898790359)
			CFrameMon = CFrame.new(6241.9951171875, 51.522083282471, -1243.9771728516)
			SPAWNPOINT = "Hydra3"
		elseif MyLevel == 1600 or MyLevel <= 1624 or _G.Select_Mob_Farm == "Dragon Crew Archer [Lv. 1600]" then
			Ms = "Dragon Crew Archer [Lv. 1600]"
			NameQuest = "AmazonQuest"
			LevelQuest = 2
			NameMon = "Dragon Crew Archer"
			CFrameQuest = CFrame.new(5832.83594, 51.6806107, -1101.51563, 0.898790359, -0, -0.438378751, 0, 1, -0, 0.438378751, 0, 0.898790359)
			CFrameMon = CFrame.new(6488.9155273438, 383.38375854492, -110.66246032715)
			SPAWNPOINT = "Hydra3"
		elseif MyLevel == 1625 or MyLevel <= 1649 or _G.Select_Mob_Farm == "Female Islander [Lv. 1625]" then
			Ms = "Female Islander [Lv. 1625]"
			NameQuest = "AmazonQuest2"
			LevelQuest = 1
			NameMon = "Female Islander"
			CFrameQuest = CFrame.new(5448.86133, 601.516174, 751.130676, 0, 0, 1, 0, 1, -0, -1, 0, 0)
			CFrameMon = CFrame.new(4770.4990234375, 758.95520019531, 1069.8680419922)
			SPAWNPOINT = "Hydra1"
		elseif MyLevel == 1650 or MyLevel <= 1699 or _G.Select_Mob_Farm == "Giant Islander [Lv. 1650]" then
			Ms = "Giant Islander [Lv. 1650]"
			NameQuest = "AmazonQuest2"
			LevelQuest = 2
			NameMon = "Giant Islander"
			CFrameQuest = CFrame.new(5448.86133, 601.516174, 751.130676, 0, 0, 1, 0, 1, -0, -1, 0, 0)
			CFrameMon = CFrame.new(4530.3540039063, 656.75695800781, -131.60952758789)
			SPAWNPOINT = "Hydra1"
		elseif MyLevel == 1700 or MyLevel <= 1724 or _G.Select_Mob_Farm == "Marine Commodore [Lv. 1700]" then
			Ms = "Marine Commodore [Lv. 1700]"
			NameQuest = "MarineTreeIsland"
			LevelQuest = 1
			NameMon = "Marine Commodore"
			CFrameQuest = CFrame.new(2180.54126, 27.8156815, -6741.5498, -0.965929747, 0, 0.258804798, 0, 1, 0, -0.258804798, 0, -0.965929747)
			CFrameMon = CFrame.new(2490.0844726563, 190.4232635498, -7160.0502929688)
			SPAWNPOINT = "GreatTree"
		elseif MyLevel == 1725 or MyLevel <= 1774 or _G.Select_Mob_Farm == "Marine Rear Admiral [Lv. 1725]" then
			Ms = "Marine Rear Admiral [Lv. 1725]"
			NameQuest = "MarineTreeIsland"
			LevelQuest = 2
			NameMon = "Marine Rear Admiral"
			CFrameQuest = CFrame.new(2180.54126, 27.8156815, -6741.5498, -0.965929747, 0, 0.258804798, 0, 1, 0, -0.258804798, 0, -0.965929747)
			CFrameMon = CFrame.new(3951.3903808594, 229.11549377441, -6912.81640625)
			SPAWNPOINT = "GreatTree"
		elseif MyLevel == 1775 or MyLevel <= 1799 or _G.Select_Mob_Farm == "Fishman Raider [Lv. 1775]" then
			Ms = "Fishman Raider [Lv. 1775]"
			NameQuest = "DeepForestIsland3"
			LevelQuest = 1
			NameMon = "Fishman Raider"
			CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
			CFrameMon = CFrame.new(-10322.400390625, 390.94473266602, -8580.0908203125)
			SPAWNPOINT = "PineappleTown"
		elseif MyLevel == 1800 or MyLevel <= 1824 or _G.Select_Mob_Farm == "Fishman Captain [Lv. 1800]" then
			Ms = "Fishman Captain [Lv. 1800]"
			NameQuest = "DeepForestIsland3"
			LevelQuest = 2
			NameMon = "Fishman Captain"
			CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
			CFrameMon = CFrame.new(-11194.541992188, 442.02795410156, -8608.806640625)
			SPAWNPOINT = "PineappleTown"
		elseif MyLevel == 1825 or MyLevel <= 1849 or _G.Select_Mob_Farm == "Forest Pirate [Lv. 1825]" then
			Ms = "Forest Pirate [Lv. 1825]"
			NameQuest = "DeepForestIsland"
			LevelQuest = 1
			NameMon = "Forest Pirate"
			CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)
			CFrameMon = CFrame.new(-13225.809570313, 428.19387817383, -7753.1245117188)
			SPAWNPOINT = "BigMansion"
		elseif MyLevel == 1850 or MyLevel <= 1899 or _G.Select_Mob_Farm == "Mythological Pirate [Lv. 1850]" then
			Ms = "Mythological Pirate [Lv. 1850]"
			NameQuest = "DeepForestIsland"
			LevelQuest = 2
			NameMon = "Mythological Pirate"
			CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)
			CFrameMon = CFrame.new(-13869.172851563, 564.95251464844, -7084.4135742188)
			SPAWNPOINT = "BigMansion"
		elseif MyLevel == 1900 or MyLevel <= 1924 or _G.Select_Mob_Farm == "Jungle Pirate [Lv. 1900]" then
			Ms = "Jungle Pirate [Lv. 1900]"
			NameQuest = "DeepForestIsland2"
			LevelQuest = 1
			NameMon = "Jungle Pirate"
			CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
			CFrameMon = CFrame.new(-11982.221679688, 376.32522583008, -10451.415039063)
			SPAWNPOINT = "PineappleTown"
		elseif MyLevel == 1925 or MyLevel <= 1974 or _G.Select_Mob_Farm == "Musketeer Pirate [Lv. 1925]" then
			Ms = "Musketeer Pirate [Lv. 1925]"
			NameQuest = "DeepForestIsland2"
			LevelQuest = 2
			NameMon = "Musketeer Pirate"
			CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
			CFrameMon = CFrame.new(-13282.3046875, 496.23684692383, -9565.150390625)
			SPAWNPOINT = "PineappleTown"
		elseif MyLevel == 1975 or MyLevel <= 1999 or _G.Select_Mob_Farm == "Reborn Skeleton [Lv. 1975]" then
			Ms = "Reborn Skeleton [Lv. 1975]"
			NameQuest = "HauntedQuest1"
			LevelQuest = 1
			NameMon = "Reborn Skeleton"
			CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
			CFrameMon = CFrame.new(-8761.3154296875, 164.85829162598, 6161.1567382813)
			SPAWNPOINT = "HauntedCastle"
		elseif MyLevel == 2000 or MyLevel <= 2024 or _G.Select_Mob_Farm == "Living Zombie [Lv. 2000]" then
			Ms = "Living Zombie [Lv. 2000]"
			NameQuest = "HauntedQuest1"
			LevelQuest = 2
			NameMon = "Living Zombie"
			CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
			CFrameMon = CFrame.new(-10093.930664063, 237.38233947754, 6180.5654296875)
			SPAWNPOINT = "HauntedCastle"
		elseif MyLevel == 2025 or MyLevel <= 2049 or _G.Select_Mob_Farm == "Demonic Soul [Lv. 2025]" then
			Ms = "Demonic Soul [Lv. 2025]"
			NameQuest = "HauntedQuest2"
			LevelQuest = 1
			NameMon = "Demonic Soul"
			CFrameQuest = CFrame.new(-9514.78027, 171.162918, 6078.82373, 0.301918149, 7.4535027e-09, 0.953333855, -3.22802141e-09, 1, -6.79604995e-09, -0.953333855, -1.02553133e-09, 0.301918149)
			CFrameMon = CFrame.new(-9466.72949, 171.162918, 6132.01514)
			SPAWNPOINT = "HauntedCastle"
		elseif MyLevel == 2050 or MyLevel <= 2074 or _G.Select_Mob_Farm == "Posessed Mummy [Lv. 2050]" then
			Ms = "Posessed Mummy [Lv. 2050]" 
			NameQuest = "HauntedQuest2"
			LevelQuest = 2
			NameMon = "Posessed Mummy"
			CFrameQuest = CFrame.new(-9514.78027, 171.162918, 6078.82373, 0.301918149, 7.4535027e-09, 0.953333855, -3.22802141e-09, 1, -6.79604995e-09, -0.953333855, -1.02553133e-09, 0.301918149)
			CFrameMon = CFrame.new(-9589.93848, 4.85058546, 6190.27197)
			SPAWNPOINT = "HauntedCastle"
		elseif MyLevel == 2075 or MyLevel <= 2099 or _G.Select_Mob_Farm == "Peanut Scout [Lv. 2075]" then
            Ms = "Peanut Scout [Lv. 2075]"
            NameQuest = "NutsIslandQuest"
            LevelQuest = 1
            NameMon = "Peanut Scout"
            CFrameQuest = CFrame.new(-2103.9375, 38.139019012451, -10192.702148438)
            CFrameMon = CFrame.new(-2150.587890625, 122.49767303467, -10358.994140625)
			SPAWNPOINT = "Peanut"
		elseif MyLevel == 2100 or MyLevel <= 2124 or _G.Select_Mob_Farm == "Peanut President [Lv. 2100]" then
            Ms = "Peanut President [Lv. 2100]"
            NameQuest = "NutsIslandQuest"
            LevelQuest = 2
            NameMon = "Peanut President"
            CFrameQuest = CFrame.new(-2103.9375, 38.139019012451, -10192.702148438)
            CFrameMon = CFrame.new(-2150.587890625, 122.49767303467, -10358.994140625)
			SPAWNPOINT = "Peanut"
		elseif MyLevel == 2125 or MyLevel <= 2149 or _G.Select_Mob_Farm == "Ice Cream Chef [Lv. 2125]" then
            Ms = "Ice Cream Chef [Lv. 2125]"
            NameQuest = "IceCreamIslandQuest"
            LevelQuest = 1
            NameMon = "Ice Cream Chef"
            CFrameQuest = CFrame.new(-819.84533691406, 65.845329284668, -10965.487304688)
            CFrameMon = CFrame.new(-890.55895996094, 186.34135437012, -11127.306640625)
			SPAWNPOINT = "IceCream"
		elseif MyLevel == 2150 or MyLevel <= 2199 or _G.Select_Mob_Farm == "Ice Cream Commander [Lv. 2150]" then
            Ms = "Ice Cream Commander [Lv. 2150]"
            NameQuest = "IceCreamIslandQuest"
            LevelQuest = 2
            NameMon = "Ice Cream Commander"
            CFrameQuest = CFrame.new(-819.84533691406, 65.845329284668, -10965.487304688)
            CFrameMon = CFrame.new(-890.55895996094, 186.34135437012, -11127.306640625)
			SPAWNPOINT = "IceCream"
		elseif MyLevel == 2200 or MyLevel <= 2224 or _G.Select_Mob_Farm == "Cookie Crafter [Lv. 2200]" then
            Ms = "Cookie Crafter [Lv. 2200]"
            NameQuest = "CakeQuest1"
            LevelQuest = 1
            NameMon = "Cookie Crafter"
            CFrameQuest = CFrame.new(-2021.5509033203125, 37.798221588134766, -12028.103515625)
            CFrameMon = CFrame.new(-2273.00244140625, 90.22590637207031, -12151.62109375)
			SPAWNPOINT = "Loaf"
		elseif MyLevel == 2225 or MyLevel <= 2249 or _G.Select_Mob_Farm == "Cake Guard [Lv. 2225]" then
            Ms = "Cake Guard [Lv. 2225]"
            NameQuest = "CakeQuest1"
            LevelQuest = 2
            NameMon = "Cake Guard"
            CFrameQuest = CFrame.new(-2021.5509033203125, 37.798221588134766, -12028.103515625)
            CFrameMon = CFrame.new(-1442.373046875, 158.14111328125, -12277.37109375)
			SPAWNPOINT = "Loaf"
		elseif MyLevel == 2250 or MyLevel <= 2274 or _G.Select_Mob_Farm == "Baking Staff [Lv. 2250]" then
            Ms = "Baking Staff [Lv. 2250]"
            NameQuest = "CakeQuest2"
            LevelQuest = 1
            NameMon = "Baking Staff"
            CFrameQuest = CFrame.new(-1927.9107666015625, 37.79813003540039, -12843.78515625)
            CFrameMon = CFrame.new(-1837.2803955078125, 129.0594482421875, -12934.5498046875)
			SPAWNPOINT = "Loaf"
		elseif MyLevel == 2275 or MyLevel <= 2299 or _G.Select_Mob_Farm == "Head Baker [Lv. 2275]" then
            Ms = "Head Baker [Lv. 2275]"
            NameQuest = "CakeQuest2"
            LevelQuest = 2
            NameMon = "Head Baker"
            CFrameQuest = CFrame.new(-1927.9107666015625, 37.79813003540039, -12843.78515625)
            CFrameMon = CFrame.new(-2203.302490234375, 109.90937042236328, -12788.7333984375)
			SPAWNPOINT = "Loaf"
		elseif MyLevel == 2300 or MyLevel <= 2324 or _G.Select_Mob_Farm == "Cocoa Warrior [Lv. 2300]" then
            Ms = "Cocoa Warrior [Lv. 2300]"
            NameQuest = "ChocQuest1"
            LevelQuest = 1
            NameMon = "Cocoa Warrior"
            CFrameQuest = CFrame.new(231.13571166992188, 24.734268188476562, -12195.1162109375)
            CFrameMon = CFrame.new(231.13571166992188, 24.734268188476562, -12195.1162109375)
			SPAWNPOINT = "Chocolate"
		elseif MyLevel == 2325 or MyLevel <= 2349 or _G.Select_Mob_Farm == "Chocolate Bar Battler [Lv. 2325]" then
            Ms = "Chocolate Bar Battler [Lv. 2325]"
            NameQuest = "ChocQuest1"
            LevelQuest = 2
            NameMon = "Chocolate Bar Battler"
            CFrameQuest = CFrame.new(231.13571166992188, 24.734268188476562, -12195.1162109375)
            CFrameMon = CFrame.new(231.13571166992188, 24.734268188476562, -12195.1162109375)
			SPAWNPOINT = "Chocolate"
		elseif MyLevel == 2350 or MyLevel <= 2374 or _G.Select_Mob_Farm == "Sweet Thief [Lv. 2350]" then
            Ms = "Sweet Thief [Lv. 2350]"
            NameQuest = "ChocQuest2"
            LevelQuest = 1
            NameMon = "Sweet Thief"
            CFrameQuest = CFrame.new(147.52256774902344, 24.793832778930664, -12775.3583984375)
            CFrameMon = CFrame.new(147.52256774902344, 24.793832778930664, -12775.3583984375)
			SPAWNPOINT = "Chocolate"
		elseif MyLevel >= 2375 or _G.Select_Mob_Farm == "Candy Rebel [Lv. 2375]" then
            Ms = "Candy Rebel [Lv. 2375]"
            NameQuest = "ChocQuest2"
            LevelQuest = 2
            NameMon = "Candy Rebel"
            CFrameQuest = CFrame.new(147.52256774902344, 24.793832778930664, -12775.3583984375)
            CFrameMon = CFrame.new(147.52256774902344, 24.793832778930664, -12775.3583984375)
			SPAWNPOINT = "Chocolate"
		end
    end
end

function CheckBossQuest()
    if _G.Select_Boss == "Saber Expert [Lv. 200] [Boss]" then
        MsBoss = "Saber Expert [Lv. 200] [Boss]"
        NameBoss = "Saber Expert"
        CFrameBoss = CFrame.new(-1458.89502, 29.8870335, -50.633564, 0.858821094, 1.13848939e-08, 0.512275636, -4.85649254e-09, 1, -1.40823326e-08, -0.512275636, 9.6063415e-09, 0.858821094)
    elseif _G.Select_Boss == "The Saw [Lv. 100] [Boss]" then
        MsBoss = "The Saw [Lv. 100] [Boss]"
        NameBoss = "The Saw"
        CFrameBoss = CFrame.new(-683.519897, 13.8534927, 1610.87854, -0.290192783, 6.88365773e-08, 0.956968188, 6.98413629e-08, 1, -5.07531119e-08, -0.956968188, 5.21077759e-08, -0.290192783)
    elseif _G.Select_Boss == "Greybeard [Lv. 750] [Raid Boss]" then
        MsBoss = "Greybeard [Lv. 750] [Raid Boss]"
        NameBoss = "Greybeard"
        CFrameBoss = CFrame.new(-4955.72949, 80.8163834, 4305.82666, -0.433646321, -1.03394289e-08, 0.901083171, -3.0443168e-08, 1, -3.17633075e-09, -0.901083171, -2.88092288e-08, -0.433646321)
    elseif _G.Select_Boss == "The Gorilla King [Lv. 25] [Boss]" then
        MsBoss = "The Gorilla King [Lv. 25] [Boss]"
        NameBoss = "The Gorilla King"
        NameQuestBoss = "JungleQuest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-1604.12012, 36.8521118, 154.23732, 0.0648873374, -4.70858913e-06, -0.997892559, 1.41431883e-07, 1, -4.70933674e-06, 0.997892559, 1.64442184e-07, 0.0648873374)
        CFrameBoss = CFrame.new(-1223.52808, 6.27936459, -502.292664, 0.310949147, -5.66602516e-08, 0.950426519, -3.37275488e-08, 1, 7.06501808e-08, -0.950426519, -5.40241736e-08, 0.310949147)
    elseif _G.Select_Boss == "Bobby [Lv. 55] [Boss]" then
        MsBoss = "Bobby [Lv. 55] [Boss]"
        NameBoss = "Bobby"
        NameQuestBoss = "BuggyQuest1"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-1139.59717, 4.75205183, 3825.16211, -0.959730506, -7.5857054e-09, 0.280922383, -4.06310328e-08, 1, -1.11807175e-07, -0.280922383, -1.18718916e-07, -0.959730506)
        CFrameBoss = CFrame.new(-1147.65173, 32.5966301, 4156.02588, 0.956680477, -1.77109952e-10, -0.29113996, 5.16530874e-10, 1, 1.08897802e-09, 0.29113996, -1.19218679e-09, 0.956680477)
    elseif _G.Select_Boss == "Yeti [Lv. 110] [Boss]" then
        MsBoss = "Yeti [Lv. 110] [Boss]"
        NameBoss = "Yeti"
        NameQuestBoss = "SnowQuest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(1384.90247, 87.3078308, -1296.6825, 0.280209213, 2.72035177e-08, -0.959938943, -6.75690828e-08, 1, 8.6151708e-09, 0.959938943, 6.24481444e-08, 0.280209213)
        CFrameBoss = CFrame.new(1221.7356, 138.046906, -1488.84082, 0.349343032, -9.49245944e-08, 0.936994851, 6.29478194e-08, 1, 7.7838429e-08, -0.936994851, 3.17894653e-08, 0.349343032)
    elseif _G.Select_Boss == "Mob Leader [Lv. 120] [Boss]" then
        MsBoss = "Mob Leader [Lv. 120] [Boss]"
        NameBoss = "Mob Leader"
        CFrameBoss = CFrame.new(-2848.59399, 7.4272871, 5342.44043, -0.928248107, -8.7248246e-08, 0.371961564, -7.61816636e-08, 1, 4.44474857e-08, -0.371961564, 1.29216433e-08, -0.92824)
    elseif _G.Select_Boss == "Vice Admiral [Lv. 130] [Boss]" then
        MsBoss = "Vice Admiral [Lv. 130] [Boss]"
        NameBoss = "Vice Admiral"
        NameQuestBoss = "MarineQuest2"
        LevelQuestBoss = 2
        CFrameQuestBoss = CFrame.new(-5035.42285, 28.6520386, 4324.50293, -0.0611100644, -8.08395768e-08, 0.998130739, -1.57416586e-08, 1, 8.00271849e-08, -0.998130739, -1.08217701e-08, -0.0611100644)
        CFrameBoss = CFrame.new(-5078.45898, 99.6520691, 4402.1665, -0.555574954, -9.88630566e-11, 0.831466436, -6.35508286e-08, 1, -4.23449258e-08, -0.831466436, -7.63661632e-08, -0.555574954)
    elseif _G.Select_Boss == "Warden [Lv. 175] [Boss]" then
        MsBoss = "Warden [Lv. 175] [Boss]"
        NameBoss = "Warden"
        NameQuestBoss = "ImpelQuest"
        LevelQuestBoss = 1
        CFrameQuestBoss = CFrame.new(4851.35059, 5.68744135, 743.251282, -0.538484037, -6.68303741e-08, -0.842635691, 1.38001752e-08, 1, -8.81300792e-08, 0.842635691, -5.90851599e-08, -0.538484037)
        CFrameBoss = CFrame.new(5232.5625, 5.26856995, 747.506897, 0.943829298, -4.5439414e-08, 0.330433697, 3.47818627e-08, 1, 3.81658154e-08, -0.330433697, -2.45289105e-08, 0.943829298)
    elseif _G.Select_Boss == "Chief Warden [Lv. 200] [Boss]" then
        MsBoss = "Chief Warden [Lv. 200] [Boss]"
        NameBoss = "Chief Warden"
        NameQuestBoss = "ImpelQuest"
        LevelQuestBoss = 2
        CFrameQuestBoss = CFrame.new(4851.35059, 5.68744135, 743.251282, -0.538484037, -6.68303741e-08, -0.842635691, 1.38001752e-08, 1, -8.81300792e-08, 0.842635691, -5.90851599e-08, -0.538484037)
        CFrameBoss = CFrame.new(5232.5625, 5.26856995, 747.506897, 0.943829298, -4.5439414e-08, 0.330433697, 3.47818627e-08, 1, 3.81658154e-08, -0.330433697, -2.45289105e-08, 0.943829298)
    elseif _G.Select_Boss == "Swan [Lv. 225] [Boss]" then
        MsBoss = "Swan [Lv. 225] [Boss]"
        NameBoss = "Swan"
        NameQuestBoss = "ImpelQuest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(4851.35059, 5.68744135, 743.251282, -0.538484037, -6.68303741e-08, -0.842635691, 1.38001752e-08, 1, -8.81300792e-08, 0.842635691, -5.90851599e-08, -0.538484037)
        CFrameBoss = CFrame.new(5232.5625, 5.26856995, 747.506897, 0.943829298, -4.5439414e-08, 0.330433697, 3.47818627e-08, 1, 3.81658154e-08, -0.330433697, -2.45289105e-08, 0.943829298)
    elseif _G.Select_Boss == "Magma Admiral [Lv. 350] [Boss]" then
        MsBoss = "Magma Admiral [Lv. 350] [Boss]"
        NameBoss = "Magma Admiral"
        NameQuestBoss = "MagmaQuest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-5317.07666, 12.2721891, 8517.41699, 0.51175487, -2.65508806e-08, -0.859131515, -3.91131572e-08, 1, -5.42026761e-08, 0.859131515, 6.13418294e-08, 0.51175487)
        CFrameBoss = CFrame.new(-5530.12646, 22.8769703, 8859.91309, 0.857838571, 2.23414389e-08, 0.513919294, 1.53689133e-08, 1, -6.91265853e-08, -0.513919294, 6.71978384e-08, 0.857838571)
    elseif _G.Select_Boss == "Fishman Lord [Lv. 425] [Boss]" then
        MsBoss = "Fishman Lord [Lv. 425] [Boss]"
        NameBoss = "Fishman Lord"
        NameQuestBoss = "FishmanQuest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(61123.0859, 18.5066795, 1570.18018, 0.927145958, 1.0624845e-07, 0.374700129, -6.98219367e-08, 1, -1.10790765e-07, -0.374700129, 7.65569368e-08, 0.927145958)
        CFrameBoss = CFrame.new(61351.7773, 31.0306778, 1113.31409, 0.999974668, 0, -0.00714713801, 0, 1.00000012, 0, 0.00714714266, 0, 0.999974549)
    elseif _G.Select_Boss == "Wysper [Lv. 500] [Boss]" then
        MsBoss = "Wysper [Lv. 500] [Boss]"
        NameBoss = "Wysper"
        NameQuestBoss = "SkyExp1Quest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-7862.94629, 5545.52832, -379.833954, 0.462944925, 1.45838088e-08, -0.886386991, 1.0534996e-08, 1, 2.19553424e-08, 0.886386991, -1.95022007e-08, 0.462944925)
        CFrameBoss = CFrame.new(-7925.48389, 5550.76074, -636.178345, 0.716468513, -1.22915289e-09, 0.697619379, 3.37381434e-09, 1, -1.70304748e-09, -0.697619379, 3.57381835e-09, 0.716468513)
    elseif _G.Select_Boss == "Thunder God [Lv. 575] [Boss]" then
        MsBoss = "Thunder God [Lv. 575] [Boss]"
        NameBoss = "Thunder God"
        NameQuestBoss = "SkyExp2Quest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-7902.78613, 5635.99902, -1411.98706, -0.0361216255, -1.16895912e-07, 0.999347389, 1.44533963e-09, 1, 1.17024491e-07, -0.999347389, 5.6715117e-09, -0.0361216255)
        CFrameBoss = CFrame.new(-7917.53613, 5616.61377, -2277.78564, 0.965189934, 4.80563429e-08, -0.261550069, -6.73089886e-08, 1, -6.46515304e-08, 0.261550069, 8.00056768e-08, 0.965189934)
    elseif _G.Select_Boss == "Cyborg [Lv. 675] [Boss]" then
        MsBoss = "Cyborg [Lv. 675] [Boss]"
        NameBoss = "Cyborg"
        NameQuestBoss = "FountainQuest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(5253.54834, 38.5361786, 4050.45166, -0.0112687312, -9.93677887e-08, -0.999936521, 2.55291371e-10, 1, -9.93769547e-08, 0.999936521, -1.37512213e-09, -0.0112687312)
        CFrameBoss = CFrame.new(6041.82813, 52.7112198, 3907.45142, -0.563162148, 1.73805248e-09, -0.826346457, -5.94632716e-08, 1, 4.26280238e-08, 0.826346457, 7.31437524e-08, -0.563162148)
    -- New World
    elseif _G.Select_Boss == "Diamond [Lv. 750] [Boss]" then
        MsBoss = "Diamond [Lv. 750] [Boss]"
        NameBoss = "Diamond"
        NameQuestBoss = "Area1Quest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-424.080078, 73.0055847, 1836.91589, 0.253544956, -1.42165932e-08, 0.967323601, -6.00147771e-08, 1, 3.04272909e-08, -0.967323601, -6.5768397e-08, 0.253544956)
        CFrameBoss = CFrame.new(-1736.26587, 198.627731, -236.412857, -0.997808516, 0, -0.0661673471, 0, 1, 0, 0.0661673471, 0, -0.997808516)
    elseif _G.Select_Boss == "Jeremy [Lv. 850] [Boss]" then
        MsBoss = "Jeremy [Lv. 850] [Boss]"
        NameBoss = "Jeremy"
        NameQuestBoss = "Area2Quest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(632.698608, 73.1055908, 918.666321, -0.0319722369, 8.96074881e-10, -0.999488771, 1.36326533e-10, 1, 8.92172336e-10, 0.999488771, -1.07732087e-10, -0.0319722369)
        CFrameBoss = CFrame.new(2203.76953, 448.966034, 752.731079, -0.0217453763, 0, -0.999763548, 0, 1, 0, 0.999763548, 0, -0.0217453763)
    elseif _G.Select_Boss == "Fajita [Lv. 925] [Boss]" then
        MsBoss = "Fajita [Lv. 925] [Boss]"
        NameBoss = "Fajita"
        NameQuestBoss = "MarineQuest3"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-2442.65015, 73.0511475, -3219.11523, -0.873540044, 4.2329841e-08, -0.486752301, 5.64383384e-08, 1, -1.43220786e-08, 0.486752301, -3.99823996e-08, -0.873540044)
        CFrameBoss = CFrame.new(-2297.40332, 115.449463, -3946.53833, 0.961227536, -1.46645796e-09, -0.275756449, -2.3212845e-09, 1, -1.34094433e-08, 0.275756449, 1.35296352e-08, 0.961227536)
    elseif _G.Select_Boss == "Don Swan [Lv. 1000] [Boss]" then
        MsBoss = "Don Swan [Lv. 1000] [Boss]"
        NameBoss = "Don Swan"
        CFrameBoss = CFrame.new(2288.802, 15.1870775, 863.034607, 0.99974072, -8.41247214e-08, -0.0227668174, 8.4774733e-08, 1, 2.75850098e-08, 0.0227668174, -2.95079072e-08, 0.99974072)
    elseif _G.Select_Boss == "Smoke Admiral [Lv. 1150] [Boss]" then
        MsBoss = "Smoke Admiral [Lv. 1150] [Boss]"
        NameBoss = "Smoke Admiral"
        NameQuestBoss = "IceSideQuest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-6059.96191, 15.9868021, -4904.7373, -0.444992423, -3.0874483e-09, 0.895534337, -3.64098796e-08, 1, -1.4644522e-08, -0.895534337, -3.91229982e-08, -0.444992423)
        CFrameBoss = CFrame.new(-5115.72754, 23.7664986, -5338.2207, 0.251453817, 1.48345061e-08, -0.967869282, 4.02796978e-08, 1, 2.57916977e-08, 0.967869282, -4.54708946e-08, 0.251453817)
    elseif _G.Select_Boss == "Cursed Captain [Lv. 1325] [Raid Boss]" then
        MsBoss = "Cursed Captain [Lv. 1325] [Raid Boss]"
        NameBoss = "Cursed Captain"
        CFrameBoss = CFrame.new(916.928589, 181.092773, 33422, -0.999505103, 9.26310495e-09, 0.0314563364, 8.42916226e-09, 1, -2.6643713e-08, -0.0314563364, -2.63653774e-08, -0.999505103)
    elseif _G.Select_Boss == "Darkbeard [Lv. 1000] [Raid Boss]" then
        MsBoss = "Darkbeard [Lv. 1000] [Raid Boss]"
        NameBoss = "Darkbeard"
        CFrameBoss = CFrame.new(3876.00366, 24.6882591, -3820.21777, -0.976951957, 4.97356325e-08, 0.213458836, 4.57335361e-08, 1, -2.36868622e-08, -0.213458836, -1.33787044e-08, -0.976951957)
    elseif _G.Select_Boss == "Order [Lv. 1250] [Raid Boss]" then
        MsBoss = "Order [Lv. 1250] [Raid Boss]"
        NameBoss = "Order"
        CFrameBoss = CFrame.new(-6221.15039, 16.2351036, -5045.23584, -0.380726993, 7.41463495e-08, 0.924687505, 5.85604774e-08, 1, -5.60738549e-08, -0.924687505, 3.28013137e-08, -0.380726993)
    elseif _G.Select_Boss == "Awakened Ice Admiral [Lv. 1400] [Boss]" then
        MsBoss = "Awakened Ice Admiral [Lv. 1400] [Boss]"
        NameBoss = "Awakened Ice Admiral"
        NameQuestBoss = "FrostQuest"
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(5669.33203, 28.2118053, -6481.55908, 0.921275556, -1.25320829e-08, 0.388910472, 4.72230788e-08, 1, -7.96414241e-08, -0.388910472, 9.17372489e-08, 0.921275556)
        CFrameBoss = CFrame.new(6407.33936, 340.223785, -6892.521, 0.49051559, -5.25310213e-08, -0.871432424, -2.76146022e-08, 1, -7.58250565e-08, 0.871432424, 6.12576301e-08, 0.49051559)
    elseif _G.Select_Boss == "Tide Keeper [Lv. 1475] [Boss]" then
        MsBoss = "Tide Keeper [Lv. 1475] [Boss]"
         NameBoss = "Tide Keeper"
        NameQuestBoss = "ForgottenQuest"             
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-3053.89648, 236.881363, -10148.2324, -0.985987961, -3.58504737e-09, 0.16681771, -3.07832915e-09, 1, 3.29612559e-09, -0.16681771, 2.73641976e-09, -0.985987961)
        CFrameBoss = CFrame.new(-3570.18652, 123.328949, -11555.9072, 0.465199202, -1.3857326e-08, 0.885206044, 4.0332897e-09, 1, 1.35347511e-08, -0.885206044, -2.72606271e-09, 0.465199202)
    -- Thire World
    elseif _G.Select_Boss == "Stone [Lv. 1550] [Boss]" then
        MsBoss = "Stone [Lv. 1550] [Boss]"
        NameBoss = "Stone"
        NameQuestBoss = "PiratePortQuest"             
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-290, 44, 5577)
        CFrameBoss = CFrame.new(-1085, 40, 6779)
    elseif _G.Select_Boss == "Island Empress [Lv. 1675] [Boss]" then
        MsBoss = "Island Empress [Lv. 1675] [Boss]"
         NameBoss = "Island Empress"
        NameQuestBoss = "AmazonQuest2"             
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(5443, 602, 752)
        CFrameBoss = CFrame.new(5659, 602, 244)
    elseif _G.Select_Boss == "Kilo Admiral [Lv. 1750] [Boss]" then
        MsBoss = "Kilo Admiral [Lv. 1750] [Boss]"
        NameBoss = "Kilo Admiral"
        NameQuestBoss = "MarineTreeIsland"             
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(2178, 29, -6737)
        CFrameBoss =CFrame.new(2846, 433, -7100)
    elseif _G.Select_Boss == "Captain Elephant [Lv. 1875] [Boss]" then
        MsBoss = "Captain Elephant [Lv. 1875] [Boss]"
        NameBoss = "Captain Elephant"
        NameQuestBoss = "DeepForestIsland"             
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-13232, 333, -7631)
        CFrameBoss = CFrame.new(-13221, 325, -8405)
    elseif _G.Select_Boss == "Beautiful Pirate [Lv. 1950] [Boss]" then
        MsBoss = "Beautiful Pirate [Lv. 1950] [Boss]"
        NameBoss = "Beautiful Pirate"
        NameQuestBoss = "DeepForestIsland2"             
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-12686, 391, -9902)
        CFrameBoss = CFrame.new(5182, 23, -20)
    elseif _G.Select_Boss == "Cake Queen [Lv. 2175] [Boss]" then
        MsBoss = "Cake Queen [Lv. 2175] [Boss]"
        NameBoss = "Cake Queen"
        NameQuestBoss = "IceCreamIslandQuest"             
        LevelQuestBoss = 3
        CFrameQuestBoss = CFrame.new(-716, 382, -11010)
        CFrameBoss = CFrame.new(-821, 66, -10965)
    elseif _G.Select_Boss == "rip_indra True Form [Lv. 5000] [Raid Boss]" then
        MsBoss = "rip_indra True Form [Lv. 5000] [Raid Boss]"
        NameBoss = "rip_indra True Form"
        CFrameBoss = CFrame.new(-5359, 424, -2735)
    elseif _G.Select_Boss == "Longma [Lv. 2000] [Boss]" then
        MsBoss = "Longma [Lv. 2000] [Boss]"
        NameBoss = "Longma"
        CFrameBoss = CFrame.new(-10248.3936, 353.79129, -9306.34473)
    elseif _G.Select_Boss == "Soul Reaper [Lv. 2100] [Raid Boss]" then
        MsBoss = "Soul Reaper [Lv. 2100] [Raid Boss]"
        NameBoss = "Soul Reaper"
        CFrameBoss = CFrame.new(-9515.62109, 315.925537, 6691.12012)
    end
end

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

getgenv().ToTarget = function(p)
    task.spawn(function()
        pcall(function()
            if game:GetService("Players").LocalPlayer:DistanceFromCharacter(p.Position) <= 250 then 
                game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = p
            elseif not game.Players.LocalPlayer.Character:FindFirstChild("Root")then 
                local K = Instance.new("Part",game.Players.LocalPlayer.Character)
                K.Size = Vector3.new(1,0.5,1)
                K.Name = "Root"
                K.Anchored = true
                K.Transparency = 1
                K.CanCollide = false
                K.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,20,0)
            end
            local U = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-p.Position).Magnitude
            local z = game:service("TweenService")
            local B = TweenInfo.new((p.Position-game.Players.LocalPlayer.Character.Root.Position).Magnitude/300,Enum.EasingStyle.Linear)
            local S,g = pcall(function()
            local q = z:Create(game.Players.LocalPlayer.Character.Root,B,{CFrame = p})
            q:Play()
        end)
        if not S then 
            return g
        end
        game.Players.LocalPlayer.Character.Root.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
            if S and game.Players.LocalPlayer.Character:FindFirstChild("Root") then 
                pcall(function()
                    if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-p.Position).Magnitude >= 20 then 
                        spawn(function()
                            pcall(function()
                                if (game.Players.LocalPlayer.Character.Root.Position-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 150 then 
                                    game.Players.LocalPlayer.Character.Root.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
                                else 
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame=game.Players.LocalPlayer.Character.Root.CFrame
                                end
                            end)
                        end)
                    elseif (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-p.Position).Magnitude >= 10 and(game.Players.LocalPlayer.Character.HumanoidRootPart.Position-p.Position).Magnitude < 20 then 
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = p
                    elseif (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-p.Position).Magnitude < 10 then 
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = p
                    end
                end)
            end
	    end)
    end)
end

function StopTween(target)
	if not target then
		_G.StopTween = true
		wait()
		getgenv().ToTarget(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame)
		wait()
		if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
			game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
		end
		_G.StopTween = false
		_G.Clip = false
	end
end

function UseCode(Text)
	game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(Text)
end

function toTarget(targetPos, targetCFrame)
    local tweenfunc = {}
    local tween_s = game:service"TweenService"
    local info = TweenInfo.new((targetPos - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).Magnitude/300, Enum.EasingStyle.Linear)
    local tween = tween_s:Create(game:GetService("Players").LocalPlayer.Character["HumanoidRootPart"], info, {CFrame = targetCFrame * CFrame.fromAxisAngle(Vector3.new(1,0,0), math.rad(0))})
    tween:Play()

    function tweenfunc:Stop()
        tween:Cancel()
        return tween
    end

    if not tween then return tween end
    return tweenfunc
end

local plr = game.Players.LocalPlayer

local CbFw = debug.getupvalues(require(plr.PlayerScripts.CombatFramework))
local CbFw2 = CbFw[2]

function GetCurrentBlade() 
	local p13 = CbFw2.activeController
	local ret = p13.blades[1]
	if not ret then return end
	while ret.Parent ~= game.Players.LocalPlayer.Character do ret=ret.Parent end
	return ret
end

function Hop()
	local PlaceID = game.PlaceId
	local AllIDs = {}
	local foundAnything = ""
	local actualHour = os.date("!*t").hour
	local Deleted = false
	function TPReturner()
		local Site;
		if foundAnything == "" then
			Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
		else
			Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
		end
		local ID = ""
		if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
			foundAnything = Site.nextPageCursor
		end
		local num = 0;
		for i,v in pairs(Site.data) do
			local Possible = true
			ID = tostring(v.id)
			if tonumber(v.maxPlayers) > tonumber(v.playing) then
				for _,Existing in pairs(AllIDs) do
					if num ~= 0 then
						if ID == tostring(Existing) then
							Possible = false
						end
					else
						if tonumber(actualHour) ~= tonumber(Existing) then
							local delFile = pcall(function()
								AllIDs = {}
								table.insert(AllIDs, actualHour)
							end)
						end
					end
					num = num + 1
				end
				if Possible == true then
					table.insert(AllIDs, ID)
					wait()
					pcall(function()
						wait()
						game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
					end)
					wait(4)
				end
			end
		end
	end
	function Teleport() 
		while wait() do
			pcall(function()
				TPReturner()
				if foundAnything ~= "" then
					TPReturner()
				end
			end)
		end
	end
	Teleport()
end

function SkyJumpNoCoolDown()
	if _G.Infinit_SkyJump then
		for i,v in next, getgc() do
			if game.Players.LocalPlayer.Character.Geppo then
				if typeof(v) == "function" and getfenv(v).script == game.Players.LocalPlayer.Character.Geppo then
					for i2,v2 in next, getupvalues(v) do
						if tostring(v2) == "0" then
							repeat wait(.1)
								setupvalue(v,i2,0)
							until not _G.Infinit_SkyJump
						end
					end
				end
			end
		end
	end
end

function InfAbility()
	if _G.Infinit_Ability then
		if not game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility") then
			local inf = Instance.new("ParticleEmitter")
			inf.Acceleration = Vector3.new(0,0,0)
			inf.Archivable = true
			inf.Drag = 20
			inf.EmissionDirection = Enum.NormalId.Top
			inf.Enabled = true
			inf.Lifetime = NumberRange.new(0.2,0.2)
			inf.LightInfluence = 0
			inf.LockedToPart = true
			inf.Name = "Agility"
			inf.Rate = 500
			local numberKeypoints2 = {
				NumberSequenceKeypoint.new(0, 0); 
				NumberSequenceKeypoint.new(1, 4); 
			}

			inf.Size = NumberSequence.new(numberKeypoints2)
			inf.RotSpeed = NumberRange.new(999, 9999)
			inf.Rotation = NumberRange.new(0, 0)
			inf.Speed = NumberRange.new(30, 30)
			inf.SpreadAngle = Vector2.new(360,360)
			inf.Texture = "rbxassetid://243098098"
			inf.VelocityInheritance = 0
			inf.ZOffset = 2
			inf.Transparency = NumberSequence.new(0)
			inf.Color = ColorSequence.new(Color3.fromRGB(0, 255, 255),Color3.fromRGB(0, 255, 255))
			inf.Parent = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart
		end
	else
		if game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility") then
			game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility"):Destroy()
		end
	end
end

_G.Dodge_No_CoolDown = false
function DodgeNoCoolDown()
	if _G.Dodge_No_CoolDown then
		for i,v in next, getgc() do
			if game.Players.LocalPlayer.Character.Dodge then
				if typeof(v) == "function" and getfenv(v).script == game.Players.LocalPlayer.Character.Dodge then
					for i2,v2 in next, getupvalues(v) do
						if tostring(v2) == "0.4" then
							repeat wait(.1)
								setupvalue(v,i2,0)
							until not _G.Dodge_No_CoolDown
						end
					end
				end
			end
		end
	end
end

local LocalPlayer = game:GetService'Players'.LocalPlayer
local originalstam = LocalPlayer.Character.Energy.Value
function InfinitEnergy()
	game:GetService'Players'.LocalPlayer.Character.Energy.Changed:connect(function()
		if _G.Infinit_Energy then
			LocalPlayer.Character.Energy.Value = originalstam
		end 
	end)
end

function SoruNoCoolDown()
	for i, v in pairs(getgc()) do
		if type(v) == "function" and getfenv(v).script == game.Players.LocalPlayer.Character:WaitForChild("Soru") then
			for i2,v2 in pairs(debug.getupvalues(v)) do
				if type(v2) == 'table' then
					if v2.LastUse then
						repeat wait()
							setupvalue(v, i2, {LastAfter = 0,LastUse = 0})
						until not _G.Infinit_Soru
					end
				end
			end
		end
	end
end

function RemoveSpaces(str)
    return str:gsub(" Fruit", "")
end

local function formatNumber(number)
	local i, k, j = tostring(number):match("(%-?%d?)(%d*)(%.?.*)")
	return i..k:reverse():gsub("(%d%d%d)", "%1,"):reverse()..j
 end

---------------------------------------------------------------

spawn(function()
	while wait() do
		repeat wait() until game.CoreGui:FindFirstChild('RobloxPromptGui')
		local lp,po,ts = game:GetService('Players').LocalPlayer,game.CoreGui.RobloxPromptGui.promptOverlay,game:GetService('TeleportService')							
		po.ChildAdded:connect(function(a)
			if a.Name == 'ErrorPrompt' then
				repeat
					ts:Teleport(game.PlaceId)
					wait(2)
				until false
			end
		end)
	end
end)

spawn(function()
	pcall(function()
		game:GetService("RunService").Stepped:Connect(function()
		  	if _G.Auto_Farm_Level or _G.Auto_New_World or _G.Auto_Third_World or _G.Auto_Farm_Chest or _G.Auto_Farm_Boss or _G.Auto_Elite_Hunter or _G.Auto_Cake_Prince or _G.Auto_Farm_All_Boss or _G.Auto_Saber or _G.Auto_Pole or _G.Auto_Farm_Scrap_and_Leather or _G.Auto_Farm_Angel_Wing or _G.Auto_Factory_Farm or _G.Auto_Farm_Ectoplasm or _G.Auto_Bartilo_Quest or _G.Auto_Rengoku or _G.Auto_Farm_Radioactive or _G.Auto_Farm_Vampire_Fang or _G.Auto_Farm_Mystic_Droplet or _G.Auto_Farm_GunPowder or _G.Auto_Farm_Dragon_Scales or _G.Auto_Evo_Race_V2 or _G.Auto_Swan_Glasses or _G.Auto_Dragon_Trident or _G.Auto_Soul_Reaper or _G.Auto_Farm_Fish_Tail or _G.Auto_Farm_Mini_Tusk or _G.Auto_Farm_Magma_Ore or _G.Auto_Farm_Bone or _G.Auto_Farm_Conjured_Cocoa or _G.Auto_Open_Dough_Dungeon or _G.Auto_Rainbow_Haki or _G.Auto_Musketeer_Hat or _G.Auto_Holy_Torch or _G.Auto_Canvander or _G.Auto_Twin_Hook or _G.Auto_Serpent_Bow or _G.Auto_Fully_Death_Step or _G.Auto_Fully_SharkMan_Karate or _G.Teleport_to_Player or _G.Auto_Kill_Player_Melee or _G.Auto_Kill_Player_Gun or _G.Start_Tween_Island or _G.Auto_Next_Island or _G.Auto_Kill_Law then
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
			if _G.Auto_Farm_Level or _G.Auto_New_World or _G.Auto_Third_World or _G.Auto_Farm_Chest or _G.Auto_Farm_Boss or _G.Auto_Elite_Hunter or _G.Auto_Cake_Prince or _G.Auto_Farm_All_Boss or _G.Auto_Saber or _G.Auto_Pole or _G.Auto_Farm_Scrap_and_Leather or _G.Auto_Farm_Angel_Wing or _G.Auto_Factory_Farm or _G.Auto_Farm_Ectoplasm or _G.Auto_Bartilo_Quest or _G.Auto_Rengoku or _G.Auto_Farm_Radioactive or _G.Auto_Farm_Vampire_Fang or _G.Auto_Farm_Mystic_Droplet or _G.Auto_Farm_GunPowder or _G.Auto_Farm_Dragon_Scales or _G.Auto_Evo_Race_V2 or _G.Auto_Swan_Glasses or _G.Auto_Dragon_Trident or _G.Auto_Soul_Reaper or _G.Auto_Farm_Fish_Tail or _G.Auto_Farm_Mini_Tusk or _G.Auto_Farm_Magma_Ore or _G.Auto_Farm_Bone or _G.Auto_Farm_Conjured_Cocoa or _G.Auto_Open_Dough_Dungeon or _G.Auto_Rainbow_Haki or _G.Auto_Musketeer_Hat or _G.Auto_Holy_Torch or _G.Auto_Canvander or _G.Auto_Twin_Hook or _G.Auto_Serpent_Bow or _G.Auto_Fully_Death_Step or _G.Auto_Fully_SharkMan_Karate or _G.Teleport_to_Player or _G.Auto_Kill_Player_Melee or _G.Auto_Kill_Player_Gun or _G.Start_Tween_Island or _G.Auto_Next_Island or _G.Auto_Kill_Law then
				for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
					if v:IsA("BasePart") then
						v.CanCollide = false    
					end
				end
			end
		end)
	end)
end)

local Client = game.Players.LocalPlayer
local STOP = require(Client.PlayerScripts.CombatFramework.Particle)
local STOPRL = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib)
spawn(function()
	while task.wait() do
		pcall(function()
			if not shared.orl then shared.orl = STOPRL.wrapAttackAnimationAsync end
			if not shared.cpc then shared.cpc = STOP.play end
				STOPRL.wrapAttackAnimationAsync = function(a,b,c,d,func)
				local Hits = STOPRL.getBladeHits(b,c,d)
				if Hits then
                    if _G.Auto_Farm_Level or _G.Auto_New_World or _G.Auto_Third_World or _G.Auto_Farm_Boss or _G.Auto_Elite_Hunter or _G.Auto_Cake_Prince or _G.Auto_Farm_All_Boss or _G.Auto_Saber or _G.Auto_Pole or _G.Auto_Farm_Scrap_and_Leather or _G.Auto_Farm_Angel_Wing or _G.Auto_Factory_Farm or _G.Auto_Farm_Ectoplasm or _G.Auto_Bartilo_Quest or _G.Auto_Rengoku or _G.Auto_Farm_Radioactive or _G.Auto_Farm_Vampire_Fang or _G.Auto_Farm_Mystic_Droplet or _G.Auto_Farm_GunPowder or _G.Auto_Farm_Dragon_Scales or _G.Auto_Evo_Race_V2 or _G.Auto_Swan_Glasses or _G.Auto_Dragon_Trident or _G.Auto_Soul_Reaper or _G.Auto_Farm_Fish_Tail or _G.Auto_Farm_Mini_Tusk or _G.Auto_Farm_Magma_Ore or _G.Auto_Farm_Bone or _G.Auto_Farm_Conjured_Cocoa or _G.Auto_Open_Dough_Dungeon or _G.Auto_Rainbow_Haki or _G.Auto_Musketeer_Hat or _G.Auto_Holy_Torch or _G.Auto_Canvander or _G.Auto_Twin_Hook or _G.Auto_Serpent_Bow or _G.Auto_Fully_Death_Step or _G.Auto_Fully_SharkMan_Karate then
                        STOP.play = function() end
                        a:Play(0.01,0.01,0.01)
                        func(Hits)
                        STOP.play = shared.cpc
                        wait(a.length * 0.5)
                        a:Stop()
                    else
                        a:Play()
                    end
				end
			end
		end)
	end
end)

spawn(function()
    while wait() do
        if setscriptable then
            setscriptable(game.Players.LocalPlayer, "SimulationRadius", true)
            game.Players.LocalPlayer.SimulationRadius = math.huge
        end
    end
end)

spawn(function()
	while wait() do
		for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
			if v:IsA("Tool") then
				if v:FindFirstChild("RemoteFunctionShoot") then 
					SelectToolWeaponGun = v.Name
				end
			end
		end
		for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do  
			if v:IsA("Tool") then
				if v:FindFirstChild("RemoteFunctionShoot") then 
					SelectToolWeaponGun = v.Name
				end
			end
		end
	end
end)

spawn(function()
	local gg = getrawmetatable(game)
	local old = gg.__namecall
	setreadonly(gg,false)
	gg.__namecall = newcclosure(function(...)
		local method = getnamecallmethod()
		local args = {...}
		if tostring(method) == "FireServer" then
			if tostring(args[1]) == "RemoteEvent" then
				if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
					if UseSkillMasteryDevilFruit then
						args[2] = PositionSkillMasteryDevilFruit
						return old(unpack(args))
					elseif AimSkillNearest then
						args[2] = AimBotSkillPosition
						return old(unpack(args))
					end
				end
			end
		end
		return old(...)
	end)
end)

spawn(function()
	game:GetService("RunService").RenderStepped:Connect(function()
        if UseGun then
			pcall(function()
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    if v.Name == Ms then
						local args = {
							[1] = "TAP",
							[2] = v.HumanoidRootPart.Position
						}
						
						game:GetService("Players").LocalPlayer.Character.Humanoid:FindFirstChild("Soul Guitar"):InvokeServer(unpack(args))
                        local args = {
                            [1] = v.HumanoidRootPart.Position,
                            [2] = v.HumanoidRootPart
                        }
                        game:GetService("Players").LocalPlayer.Character[SelectToolWeaponGun].RemoteFunctionShoot:InvokeServer(unpack(args))
                    end
                end
            end)
        end
    end)
end)

spawn(function()
	game:GetService("RunService").RenderStepped:Connect(function()
        if UseGunKillPlayer then
			pcall(function()
                for i,v in pairs(game:GetService("Workspace").Characters:GetChildren()) do
                    if v.Name == _G.Select_Player then
                        local args = {
                            [1] = v.HumanoidRootPart.Position,
                            [2] = v.HumanoidRootPart
                        }
                        game:GetService("Players").LocalPlayer.Character[SelectToolWeaponGun].RemoteFunctionShoot:InvokeServer(unpack(args))
                    end
                end
            end)
        end
    end)
end)

local lp = game:GetService('Players').LocalPlayer
local mouse = lp:GetMouse()
spawn(function()
	while wait() do
		if _G.Aimbot_Skill_Fov then
			pcall(function()
				local MaxDist, Closest = math.huge
				for i,v in pairs(game:GetService("Players"):GetChildren()) do 
					local Head = v.Character:FindFirstChild("HumanoidRootPart")
					local Pos, Vis = game.Workspace.CurrentCamera.WorldToScreenPoint(game.Workspace.CurrentCamera, Head.Position)
					local MousePos, TheirPos = Vector2.new(mouse.X, mouse.Y), Vector2.new(Pos.X, Pos.Y)
					local Dist = (TheirPos - MousePos).Magnitude
					if Dist < MaxDist and Dist <= _G.Select_Size_Fov and v.Name ~= game.Players.LocalPlayer.Name then
						MaxDist = Dist
						_G.Aim_Players = v
					end
				end
			end)
		end
	end
end)

spawn(function()
	local gg = getrawmetatable(game)
	local old = gg.__namecall
	setreadonly(gg,false)
	gg.__namecall = newcclosure(function(...)
		local method = getnamecallmethod()
		local args = {...}
		if tostring(method) == "FireServer" then
			if tostring(args[1]) == "RemoteEvent" then
				if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
					if _G.Aimbot_Skill_Fov then
						args[2] = _G.Aim_Players.Character.HumanoidRootPart.Position
						return old(unpack(args))
					end
				end
			end
		end
		return old(...)
	end)
end)

--------------------------------------------

local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/hajibeza/RIPPERMAIN/main/RIPPERPCGUI.lua"))()
local Wait = library.subs.Wait

local PepsisWorld = library:CreateWindow({
    Name = "ไก่ตัน",
    Themeable = {
    Info = "Discord Server: "
    }
})

local MainTab = PepsisWorld:CreateTab({
    Name = "หลัก"
})

local MainSection = MainTab:CreateSection({
    Name = "ออโต้ฟาร์ม",
	Side = "Left"
})

MainSection:AddToggle({
    Name = "ออโต้ฟาร์ม",
    Flag = "Auto_Farm_Level",
	Value = _G.Settings.Auto_Farm_Level,
    Callback = function(value)
        _G.Auto_Farm_Level = value    
		_G.Settings.Auto_Farm_Level = value
		saveSettings()
        StopTween(_G.Auto_Farm_Level)
    end
})

spawn(function()
    game:GetService("RunService").Heartbeat:Connect(function() CheckQuest()
		pcall(function()
			if _G.Select_Bring_Mob_Mode == "Bring Mob [Normal]" then
				for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if _G.Auto_Farm_Level and StartMagnet and v.Name == Ms and (v.HumanoidRootPart.Position - PosMon.Position).magnitude <= 350 then
						v.HumanoidRootPart.CFrame = PosMon
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					end
				end
			elseif _G.Select_Bring_Mob_Mode == "Bring Mob [Extra]" then
				for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if _G.Auto_Farm_Level and StartMagnet and v.Name ~= "Ice Admiral [Lv. 700] [Boss]" and v.Name ~= "Don Swan [Lv. 3000] [Boss]" and v.Name ~= "Saber Expert [Lv. 200] [Boss]" and v.Name ~= "Longma [Lv. 2000] [Boss]" and (v.HumanoidRootPart.Position - PosMon.Position).magnitude <= 350 then
						v.HumanoidRootPart.CFrame = PosMon
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					end
				end
			end
		end)
    end)
end)

spawn(function()
    game:GetService("RunService").Heartbeat:Connect(function() CheckQuest()
		pcall(function()
			for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
				if _G.Auto_Farm_Level and MasteryBFMagnetActive and v.Name == Ms and (v.HumanoidRootPart.Position - PosMonMasteryFruit.Position).magnitude <= 350 then
					v.HumanoidRootPart.CFrame = PosMonMasteryFruit
					v.HumanoidRootPart.CanCollide = false
					v.HumanoidRootPart.Size = Vector3.new(50,50,50)
					if v.Humanoid:FindFirstChild("Animator") then
						v.Humanoid.Animator:Destroy()
					end
					sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
				end
			end
		end)
    end)
end)

spawn(function()
    game:GetService("RunService").Heartbeat:Connect(function() CheckQuest()
		pcall(function()
			for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
				if _G.Auto_Farm_Level and MasteryGunMagnetActive and v.Name == Ms and (v.HumanoidRootPart.Position - PosMonMasteryGun.Position).magnitude <= 350 then
					v.HumanoidRootPart.CFrame = PosMonMasteryGun
					v.HumanoidRootPart.CanCollide = false
					v.HumanoidRootPart.Size = Vector3.new(50,50,50)
					if v.Humanoid:FindFirstChild("Animator") then
						v.Humanoid.Animator:Destroy()
					end
					sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
				end
			end
		end)
    end)
end)

spawn(function()
    while wait() do
        if _G.Auto_Farm_Level then
			if _G.Select_Mode_Farm == "Normal Mode" then
				pcall(function()
					if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
						StartMagnet = false
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
					end
					if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
						StartMagnet = false
						CheckQuest()
						repeat wait() getgenv().ToTarget(CFrameQuest) until (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_Farm_Level
						if (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
							wait(1.2)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",NameQuest,LevelQuest)
							wait(0.5)
						end
					elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
						CheckQuest()
						if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
									if v.Name == Ms then
										repeat wait()
											if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
												EquipWeapon(_G.Select_Weapon)
												AutoHaki()
												PosMon = v.HumanoidRootPart.CFrame
												v.HumanoidRootPart.CanCollide = false
												v.Humanoid.WalkSpeed = 0
												v.Head.CanCollide = false
												v.HumanoidRootPart.Size = Vector3.new(50,50,50)
												StartMagnet = true
												getgenv().ToTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Select_Distance,0))
												game:GetService'VirtualUser':CaptureController()
												game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											else
												StartMagnet = false
												game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
											end
										until not _G.Auto_Farm_Level or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
									end
								end
							end
						else
							StartMagnet = false
							if game:GetService("ReplicatedStorage"):FindFirstChild(Ms) then
								getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild(Ms).HumanoidRootPart.CFrame * CFrame.new(0,20,0))
							else	
								getgenv().ToTarget(CFrameMon)
							end
						end
					end
				end)
			elseif _G.Select_Mode_Farm == "Fast Mode" then
				pcall(function()
					if game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT then
						if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
							StartMagnet = false
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
						end
						if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
							StartMagnet = false
							CheckQuest()
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",NameQuest,LevelQuest)
						elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
							CheckQuest()
							if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
										if v.Name == Ms then
											repeat wait()
												if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
													EquipWeapon(_G.Select_Weapon)
													AutoHaki()
													PosMon = v.HumanoidRootPart.CFrame
													v.HumanoidRootPart.CanCollide = false
													v.Humanoid.WalkSpeed = 0
													v.Head.CanCollide = false
													v.HumanoidRootPart.Size = Vector3.new(50,50,50)
													StartMagnet = true
													getgenv().ToTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Select_Distance,0))
													game:GetService'VirtualUser':CaptureController()
													game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
												else
													StartMagnet = false
													game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
												end
											until not _G.Auto_Farm_Level or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
										end
									end
								end
							else
								StartMagnet = false
								if game:GetService("ReplicatedStorage"):FindFirstChild(Ms) then
									getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild(Ms).HumanoidRootPart.CFrame * CFrame.new(0,20,0))
								else	
									getgenv().ToTarget(CFrameMon)
								end
							end
						end
					else
						repeat task.wait()
							game.Players.LocalPlayer.Character.Head:Destroy()
							wait(0.5)
							game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrameQuest
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
						until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
					end
                end)
            elseif _G.Select_Mode_Farm == "No Quest" then
				pcall(function()
                	CheckQuest()
					if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
								if v.Name == Ms then
									if v.Humanoid.Health > 0 then
										repeat wait()
											EquipWeapon(_G.Select_Weapon)
											AutoHaki()
											PosMon = v.HumanoidRootPart.CFrame
											v.HumanoidRootPart.CanCollide = false
											v.Humanoid.WalkSpeed = 0
											v.Head.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											StartMagnet = true
											getgenv().ToTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Select_Distance,0))
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
										until not _G.Auto_Farm_Level or v.Humanoid.Health <= 0 or not v.Parent
									end
								end
							end
						end
					else
						StartMagnet = false
						if game:GetService("ReplicatedStorage"):FindFirstChild(Ms) then
							getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild(Ms).HumanoidRootPart.CFrame * CFrame.new(0,20,0))
						else	
							getgenv().ToTarget(CFrameMon)
						end
					end
				end)
            elseif _G.Select_Mode_Farm == "Fruit Mastery Mode" then
				pcall(function()
					if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
						MasteryBFMagnetActive = false
						CheckQuest()
						repeat wait() getgenv().ToTarget(CFrameQuest) until (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_Farm_Level
						if (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 30 then
							wait(1.1)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", NameQuest, LevelQuest)
						end
					elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
						CheckQuest()
						if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
							pcall(function()
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == Ms then
										repeat wait()
											if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
												HealthMin = v.Humanoid.MaxHealth * _G.Select_Health/100
												if v.Humanoid.Health <= HealthMin then
													EquipWeapon(game.Players.LocalPlayer.Data.DevilFruit.Value)
													AutoHaki()
													v.Head.CanCollide = false
													v.HumanoidRootPart.CanCollide = false
													v.HumanoidRootPart.Size = Vector3.new(2,2,1)
													getgenv().ToTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,20,0))
													PositionSkillMasteryDevilFruit = v.HumanoidRootPart.Position
													UseSkillMasteryDevilFruit = true
													DevilFruitMastery = game:GetService("Players").LocalPlayer.Character[game.Players.LocalPlayer.Data.DevilFruit.Value].Level.Value
													if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon-Dragon") then
														if _G.Skill_Z and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= 1 then
															game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
															wait(.1)
															game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
														end
														if _G.Skill_X and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= 1 then
															game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
															wait(.1)
															game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
														end   
													elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Human-Human: Buddha") then
														if _G.Skill_Z and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= 1 and game.Players.LocalPlayer.Character.HumanoidRootPart.Size == Vector3.new(7.6, 7.676, 3.686) then
														else
															game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
															wait(.1)
															game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
														end
														if _G.Skill_X and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= 1 then
															game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
															wait(.1)
															game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
														end
														if _G.Skill_C and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= 1 then
															game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
															wait(.1)
															game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
														end  
													elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild(game.Players.LocalPlayer.Data.DevilFruit.Value) then
														game:GetService("Players").LocalPlayer.Character:FindFirstChild(game.Players.LocalPlayer.Data.DevilFruit.Value).MousePos.Value = v.HumanoidRootPart.Position
														if _G.Skill_Z and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= 1 then
															game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
															wait(.1)
															game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
														end
														if _G.Skill_X and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= 1 then
															game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
															wait(.1)
															game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
														end
														if _G.Skill_C and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= 1 then
															game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
															wait(.1)
															game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
														end
														if _G.Skill_V and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= 1 then
															game:service('VirtualInputManager'):SendKeyEvent(true, "V", false, game)
															wait(.1)
															game:service('VirtualInputManager'):SendKeyEvent(false, "V", false, game)
														end
													end
												else
													UseSkillMasteryDevilFruit = true
													EquipWeapon(_G.Select_Weapon)
													AutoHaki()
													getgenv().ToTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Select_Distance,0))
													game:GetService'VirtualUser':CaptureController()
													game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
													v.Head.CanCollide = false
													v.HumanoidRootPart.CanCollide = false
													v.HumanoidRootPart.Size = Vector3.new(40,40,40)
												end
												MasteryBFMagnetActive = true
												PosMonMasteryFruit = v.HumanoidRootPart.CFrame
											else
												MasteryBFMagnetActive = false
												game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
											end
										until v.Humanoid.Health <= 0 or  _G.Auto_Farm_Level == false or game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == false
										UseSkillMasteryDevilFruit = true
									end
								end
							end)
						else
							MasteryBFMagnetActive = false
							if game:GetService("ReplicatedStorage"):FindFirstChild(Ms) then
								getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild(Ms).HumanoidRootPart.CFrame * CFrame.new(0,20,0))
							else	
								getgenv().ToTarget(CFrameMon)
							end
						end 
					end
				end)
			elseif _G.Select_Mode_Farm == "Gun Mastery Mode" then
				pcall(function()
					if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
						MasteryGunMagnetActive = false
						CheckQuest()
						repeat wait() getgenv().ToTarget(CFrameQuest) until (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_Farm_Level
						if (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 30 then
							wait(1.1)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", NameQuest, LevelQuest)
						end
					elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
						CheckQuest()
						if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v.Name == Ms then
									repeat wait()
										if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
											HealthMin = v.Humanoid.MaxHealth * _G.Select_Health/100
											if v.Humanoid.Health <= HealthMin and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
												AutoHaki()
												EquipWeapon(SelectToolWeaponGun)
												v.HumanoidRootPart.CanCollide = false
												getgenv().ToTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Select_Distance,0))
												UseGun = true
												game:GetService("Players").LocalPlayer.Character[SelectToolWeaponGun].Cooldown.Value = 0
												game:GetService("VirtualUser"):CaptureController()
												game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
											else
												AutoHaki()
												EquipWeapon(_G.Select_Weapon)
												v.Head.CanCollide = false
												v.HumanoidRootPart.CanCollide = false
												v.HumanoidRootPart.Size = Vector3.new(60,60,60)
												getgenv().ToTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Select_Distance,0))
												UseGun = false
												game:GetService("VirtualUser"):CaptureController()
												game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
											end
											MasteryGunMagnetActive = true 
											PosMonMasteryGun = v.HumanoidRootPart.CFrame
										else
											UseGun = false
											MasteryGunMagnetActive = false
											game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
										end
									until v.Humanoid.Health <= 0 or _G.Auto_Farm_Level == false or game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == false
									UseGun = false
									MasteryGunMagnetActive = false
								end
							end
						else
							if game:GetService("ReplicatedStorage"):FindFirstChild(Ms) then
								getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild(Ms).HumanoidRootPart.CFrame * CFrame.new(0,20,0))
							else	
								getgenv().ToTarget(CFrameMon)
							end
						end 
					end
				end)
			end
		end
    end
end)

local SettingSection = MainTab:CreateSection({
    Name = "การตั้งค่า",
	Side = "Right"
})

SettingSection:AddSlider({
    Name = "Select Distance",
    Flag = "Select_Distance",
    Value = _G.Settings.Select_Distance,
    Min = 1,
    Max = 100,
    Textbox = true,
    Format = function(value)
        _G.Select_Distance = value
		_G.Settings.Select_Distance = value
		saveSettings()
		return "Distance : " .. tostring(value)
    end
})



SettingSection:AddDropdown({
    Name = "เลือกโหมด นำม็อบ",
    Flag = "Select_Mode_Bring_Mob",
	Value = _G.Settings.Select_Bring_Mob_Mode,
    List = {"Bring Mob [Normal]","Bring Mob [Extra]"},
    Callback = function(value)
        _G.Select_Bring_Mob_Mode = value
		_G.Settings.Select_Bring_Mob_Mode = value
		saveSettings()
    end
})

SettingSection:AddToggle{
    Name = "โจมตีเร็ว [ปกติ]",
    Flag = "Fast_Attack_[Normal]",
    Value = _G.Settings.Normal_Fast_Attack,
    Callback  = function(value)
        _G.Normal_Fast_Attack = value
		_G.Settings.Normal_Fast_Attack = value
		saveSettings()
    end
}

local CameraShaker = require(game.ReplicatedStorage.Util.CameraShaker)
for i,v in pairs(getreg()) do
    if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework then
        for x,w in pairs(debug.getupvalues(v)) do
             if typeof(w) == "table" then
                spawn(function()
                    game:GetService("RunService").RenderStepped:Connect(function()
                        if _G.Normal_Fast_Attack then
                            pcall(function()
								if game.Players.LocalPlayer.Character:FindFirstChild("Combat") or game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") or game.Players.LocalPlayer.Character:FindFirstChild("Electro") or game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") or game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") or game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Character:FindFirstChild("Sharkman Karate") then
									w.activeController.increment = 3
								else
									w.activeController.increment = 4
								end             
                                CameraShaker:Stop()
                                w.activeController.timeToNextAttack = -(math.huge^math.huge^math.huge)
                                w.activeController.attacking = false
								w.activeController.timeToNextBlock = 0
                                w.activeController.blocking = false                            
                                w.activeController.hitboxMagnitude = 50
    		                    w.activeController.humanoid.AutoRotate = true
    	                      	w.activeController.focusStart = 0
                            end)
                        end
                    end)
                end)
            end
        end
    end
end

SettingSection:AddToggle{
    Name = "โจมตีเร็ว [พิเศษ]",
    Flag = "Fast_Attack_[Extra]",
    Value = _G.Settings.Extra_Fast_Attack,
    Callback  = function(value)
        _G.Extra_Fast_Attack = value
        _G.Settings.Extra_Fast_Attack = value
        saveSettings()
    end
}

spawn(function()
	while task.wait() do
        if _G.Extra_Fast_Attack then
			pcall(function()
				wait(0.2)
				local AC = CbFw2.activeController
				for i = 1,1 do 
					local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
						plr.Character,
						{plr.Character.HumanoidRootPart},
						60
					)
					local cac = {}
					local hash = {}
					for k, v in pairs(bladehit) do
						if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then
							table.insert(cac, v.Parent.HumanoidRootPart)
							hash[v.Parent] = true
						end
					end
					bladehit = cac
					if #bladehit > 0 then
						local u8 = debug.getupvalue(AC.attack, 5)
						local u9 = debug.getupvalue(AC.attack, 6)
						local u7 = debug.getupvalue(AC.attack, 4)
						local u10 = debug.getupvalue(AC.attack, 7)
						local u12 = (u8 * 798405 + u7 * 727595) % u9
						local u13 = u7 * 798405
						(function()
							u12 = (u12 * u9 + u13) % 1099511627776
							u8 = math.floor(u12 / u9)
							u7 = u12 - u8 * u9
						end)()
						u10 = u10 + 1
						debug.setupvalue(AC.attack, 5, u8)
						debug.setupvalue(AC.attack, 6, u9)
						debug.setupvalue(AC.attack, 4, u7)
						debug.setupvalue(AC.attack, 7, u10)
						if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] then 
							game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
							game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
							game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "") 
						end
					end
				end
			end)
        end
	end
end)

SettingSection:AddToggle{
    Name = "Auto Set Spawn",
    Flag = "Auto_Set_Spawn",
    Value = _G.Settings.Auto_Set_Spawn,
    Callback  = function(value)
        _G.Auto_Set_Spawn = value
        _G.Settings.Auto_Set_Spawn = value
        saveSettings()
    end
}

spawn(function()
	while wait(0.1) do
		if _G.Auto_Set_Spawn then
			pcall(function()
				if game:GetService("Players").LocalPlayer.Character.Humanoid.Health > 0 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
				end
			end)
		end
	end
end)

Code = {
	"EXP_5B",
	"CONTROL",
	"UPDATE11",
	"XMASEXP",
	"1BILLION",
	"ShutDownFix2",
	"UPD14",
	"STRAWHATMAINE",
	"TantaiGaming",
	"Colosseum",
	"Axiore",
	"Sub2Daigrock",
	"Sky Island 3",
	"Sub2OfficialNoobie",
	"SUB2NOOBMASTER123",
	"THEGREATACE",
	"Fountain City",
	"BIGNEWS",
	"FUDD10",
	"SUB2GAMERROBOT_EXP1",
	"UPD15",
	"2BILLION",
	"UPD16",
	"3BVISITS",
	"fudd10_v2",
	"Starcodeheo",
	"Magicbus",
	"JCWK",
	"Bluxxy",
	"Sub2Fer999",
	"Enyu_is_Pro"
}

SettingSection:AddSlider({
    Name = "Select Level to Redeem All Code",
    Flag = "Select_Level_to_Redeem_All_Code",
    Value = _G.Settings.Select_Level_to_Redeem_All_Code,
    Min = 1,
    Max = 2300,
    Textbox = true,
    Format = function(value)
		_G.Select_Level_to_Redeem_All_Code = value
		_G.Settings.Select_Level_to_Redeem_All_Code = value
		saveSettings()
		return "Redeem All Code At Level : " .. tostring(value)
    end
})

SettingSection:AddToggle{
    Name = "Auto Redeem All Code",
    Flag = "Auto_Redeem_All_Code",
    Value = _G.Settings.Auto_Redeem_All_Code,
    Callback  = function(value)
        _G.Auto_Redeem_All_Code = value
		_G.Settings.Auto_Redeem_All_Code = value
		saveSettings()
    end
}

spawn(function()
    while wait(5) do
        if _G.Auto_Redeem_All_Code then
            MyLevel = game.Players.localPlayer.Data.Level.value
            if MyLevel >= _G.Select_Level_to_Redeem_All_Code - 1 then
                for i,v in pairs(Code) do
                    pcall(function()
                        local args = {
                            [1] = v
                        }
                        game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(unpack(args))
                    end)
                end
                break
            end
        end
    end
end)

SettingSection:AddButton({
	Name = "Redeem All Code",
	Callback = function()
		for i,v in pairs(Code) do
			UseCode(v) 
		end
	end
})

WeaponList = {}
for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
	if v:IsA("Tool") then
		table.insert(WeaponList ,v.Name)
	end
end

SettingSection:AddDropdown({
    Name = "เลือกอาวุธ",
    Flag = "Select_Weapon",
	Value = _G.Settings.Select_Weapon,
    List = WeaponList,
    Callback = function(value)
        _G.Select_Weapon = value
		_G.Settings.Select_Weapon = value
		saveSettings()
    end
})

SettingSection:AddButton({
	Name = "รีเฟรชอาวุธ",
	Callback = function()
		table.clear(WeaponList)
		for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
			if v:IsA("Tool") then
				table.insert(WeaponList ,v.Name)
			end
		end
	end
})


	spawn(function()
		while wait() do
			if _G.Auto_Factory_Farm then
				pcall(function()
					if game.Workspace.Enemies:FindFirstChild("Core") then
						_G.FactoryCore = true
						_G.Auto_Farm_Level = false
						for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
							if _G.FactoryCore and v.Name == "Core" and v.Humanoid.Health > 0 then
								repeat wait()
									AutoHaki()
									EquipWeapon(_G.Select_Weapon)
									getgenv().ToTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,10,10))
									game:GetService'VirtualUser':CaptureController()
									game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
								until not _G.FactoryCore or v.Humanoid.Health <= 0 or _G.Auto_Factory_Farm == false
							end
						end
					elseif game.ReplicatedStorage:FindFirstChild("Core") and game.ReplicatedStorage:FindFirstChild("Core"):FindFirstChild("Humanoid") then
						_G.FactoryCore = true
						_G.Auto_Farm_Level = false
						getgenv().ToTarget(CFrame.new(502.7349853515625, 143.0749053955078, -379.078125))
					elseif _G.Auto_Farm_Level then
						_G.FactoryCore = false
						_G.Auto_Farm_Level = true
					end
				end)
			end
		end
	end)


local FightingStyleSection = MainTab:CreateSection({
    Name = "FightingStyle",
	Side = "Right"
})

FightingStyleSection:AddToggle{
    Name = "Auto Superhuman",
    Flag = "Auto_Superhuman",
    Value = _G.Settings.Auto_Superhuman,
    Callback  = function(value)
        _G.Auto_Superhuman = value
		_G.Settings.Auto_Superhuman = value
		saveSettings()
    end
}

FightingStyleSection:AddToggle{
    Name = "Auto Fully Superhuman",
    Flag = "Auto_Fully_Superhuman",
    Value = _G.Settings.Auto_Fully_Superhuman,
    Callback  = function(value)
        _G.Auto_Fully_Superhuman = value
		_G.Settings.Auto_Fully_Superhuman = value
		saveSettings()
    end
}

spawn(function()
    while wait(.25) do
        if _G.Auto_Superhuman or _G.Auto_Fully_Superhuman and game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then 
			pcall(function()
				if game:GetService("Players").LocalPlayer.Data.Beli.Value >= 500000 and (game.Players.LocalPlayer.Character:FindFirstChild("Combat") or game.Players.LocalPlayer.Backpack:FindFirstChild("Combat")) then
					_G.Select_Weapon = "Combat"
					local args = {
						[1] = "BuyElectro"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end   
				if game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") then
					_G.Select_Weapon = "Superhuman"
				end  
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value <= 299  then
					_G.Select_Weapon = "Black Leg"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value <= 299  then
					_G.Select_Weapon = "Electro"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value <= 299  then
					_G.Select_Weapon = "Fishman Karate"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value <= 299  then
					_G.Select_Weapon = "Dragon Claw"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 300  then
					local args = {
						[1] = "BuyFishmanKarate"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 300  then
					local args = {
						[1] = "BuyFishmanKarate"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 300  then
					local args = {
						[1] = "BuyBlackLeg"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value >= 300  then
					local args = {
						[1] = "BuySuperhuman"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 300  then
					local args = {
						[1] = "BuySuperhuman"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end 
			end)
        end
    end
end)

FightingStyleSection:AddToggle{
    Name = "Auto Death Step",
    Flag = "Auto_Death_Step",
    Value = _G.Settings.Auto_Death_Step,
    Callback  = function(value)
        _G.Auto_Death_Step = value
		_G.Settings.Auto_Death_Step = value
		saveSettings()
		StopTween(_G.Auto_Death_Step)
    end
}

spawn(function()
	while wait() do
		if _G.Auto_Death_Step then
			if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Death Step") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Death Step") then
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 450 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
					_G.Select_Weapon = "Death Step"
				end  
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg") and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 450 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
					_G.Select_Weapon = "Death Step"
				end  
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value <= 449 then
					_G.Select_Weapon = "Black Leg"
				end 
			else 
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
			end
		end
	end
end)

FightingStyleSection:AddToggle{
    Name = "Auto Fully Death Step",
    Flag = "Auto_Fully_Death_Step",
    Value = _G.Settings.Auto_Fully_Death_Step,
    Callback  = function(value)
        _G.Auto_Fully_Death_Step = value
		_G.Settings.Auto_Fully_Death_Step = value
		saveSettings()
    end
}

spawn(function()
	while wait() do
		if _G.Auto_Fully_Death_Step then
			pcall(function()
				if not game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") or not game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") or not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Death Step") or not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Death Step") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
				end				
				if game:GetService("Workspace").Map.IceCastle.Hall.LibraryDoor.PhoeyuDoor.Transparency == 0 then  
					if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Library Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Library Key") then
						EquipWeapon("Library Key")
						repeat wait() getgenv().ToTarget(CFrame.new(6371.2001953125, 296.63433837890625, -6841.18115234375)) until (CFrame.new(6371.2001953125, 296.63433837890625, -6841.18115234375).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_Fully_Death_Step
						if (CFrame.new(6371.2001953125, 296.63433837890625, -6841.18115234375).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
							wait(1.2)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep",true)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
							wait(0.5)
						end
					elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 450 or game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 450 then   
						if game:GetService("ReplicatedStorage"):FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]") then
							if game:GetService("Workspace").Enemies:FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]") then 	
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Awakened Ice Admiral [Lv. 1400] [Boss]" then    
										repeat wait()
											AutoHaki()
											EquipWeapon(_G.Select_Weapon)
											v.Head.CanCollide = false
											v.Humanoid.WalkSpeed = 0
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											getgenv().ToTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Select_Distance,0))
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
										until not v.Parent or v.Humanoid.Health <= 0 or _G.Auto_Fully_Death_Step == false or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Library Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Library Key")
									end
								end
							else
								repeat wait() getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]").HumanoidRootPart.CFrame) until game:GetService("Workspace").Enemies:FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]")
							end
						else 
							Hop()
						end
					end
				else 
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
				end
			end)
		end
	end
end)

FightingStyleSection:AddToggle{
    Name = "Auto Sharkman Karate",
    Flag = "Auto_SharkMan_Karate",
    Value = _G.Settings.Auto_SharkMan_Karate,
    Callback  = function(value)
        _G.Auto_SharkMan_Karate = value
		_G.Settings.Auto_SharkMan_Karate = value
		saveSettings()
		StopTween(_G.Auto_SharkMan_Karate)
    end
}

spawn(function()
	while wait() do
		if _G.Auto_SharkMan_Karate then
			if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Sharkman Karate") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Sharkman Karate") then
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
					_G.Select_Weapon = "Sharkman Karate"
				end  
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate") and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
					_G.Select_Weapon = "Sharkman Karate"
				end  
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value <= 400 then
					_G.Select_Weapon = "Fishman Karate"
				end 
			else 
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
			end
		end
	end
end)

FightingStyleSection:AddToggle{
    Name = "Auto Fully Sharkman Karate",
    Flag = "Auto_Fully_SharkMan_Karate",
    Value = _G.Settings.Auto_Fully_SharkMan_Karate,
    Callback  = function(value)
        _G.Auto_Fully_SharkMan_Karate = value
		_G.Settings.Auto_Fully_SharkMan_Karate = value
		saveSettings()
    end
}

spawn(function()
	while wait() do
		if _G.Auto_Fully_SharkMan_Karate then
			pcall(function()
				if not game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") or not game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
				end		
				if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate"), "keys") then  
					if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Water Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Water Key") then
						repeat wait() getgenv().ToTarget(-2604.6958, 239.432526, -10315.1982, 0.0425701365, 0, -0.999093413, 0, 1, 0, 0.999093413, 0, 0.0425701365) until (CFrame.new(-2604.6958, 239.432526, -10315.1982, 0.0425701365, 0, -0.999093413, 0, 1, 0, 0.999093413, 0, 0.0425701365).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_Fully_SharkMan_Karate
						if (CFrame.new(-2604.6958, 239.432526, -10315.1982, 0.0425701365, 0, -0.999093413, 0, 1, 0, 0.999093413, 0, 0.0425701365).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
							wait(1.2)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
							wait(0.5)
						end
					elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 400 or game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 400 then   
						if game:GetService("ReplicatedStorage"):FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") then
							if game:GetService("Workspace").Enemies:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") then 	
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Tide Keeper [Lv. 1475] [Boss]" then    
										repeat wait()
											AutoHaki()
											EquipWeapon(_G.Select_Weapon)
											v.Head.CanCollide = false
											v.Humanoid.WalkSpeed = 0
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											getgenv().ToTarget(v.HumanoidRootPart.CFrame * CFrame.new(0,_G.Select_Distance,0))
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
										until not v.Parent or v.Humanoid.Health <= 0 or _G.Auto_Fully_SharkMan_Karate == false or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Water Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Water Key")
									end
								end
							else
								repeat wait() getgenv().ToTarget(game:GetService("ReplicatedStorage"):FindFirstChild("Tide Keeper [Lv. 1475] [Boss]").HumanoidRootPart.CFrame) until game:GetService("Workspace").Enemies:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]")
							end
						else
							Hop()
						end
					end
				else 
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
				end
			end)
		end
	end
end)

FightingStyleSection:AddToggle{
    Name = "Auto Electric Claw",
    Flag = "Auto_Electric_Claw",
    Value = _G.Settings.Auto_Electric_Claw,
    Callback  = function(value)
        _G.Auto_Electric_Claw = value
		_G.Settings.Auto_Electric_Claw = value
		saveSettings()
    end
}

spawn(function()
	while wait() do 
		if _G.Auto_Electric_Claw then
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") or game.Players.LocalPlayer.Character:FindFirstChild("Electro") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw") or game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw") then
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
					_G.Select_Weapon = "Electric Claw"
				end  
				if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
					_G.Select_Weapon = "Electric Claw"
				end  
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value <= 399 then
					_G.Select_Weapon = "Electro"
				end 
			else
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
			end
		end
	end
end)

FightingStyleSection:AddToggle{
    Name = "Auto Dragon Talon",
    Flag = "Auto_Dragon_Talon",
    Value = _G.Settings.Auto_Dragon_Talon,
    Callback  = function(value)
        _G.Auto_Dragon_Talon = value
		_G.Settings.Auto_Dragon_Talon = value
		saveSettings()
    end
}

spawn(function()
	while wait() do
		if _G.Auto_Dragon_Talon then
			if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Talon") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Talon") then
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
					_G.Select_Weapon = "Dragon Talon"
				end  
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw") and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
					_G.Select_Weapon = "Dragon Talon"
				end  
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value <= 399 then
					_G.Select_Weapon = "Dragon Claw"
				end 
			else 
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2")
			end
		end
	end
end)

FightingStyleSection:AddToggle{
    Name = "Auto God Human",
    Flag = "Auto_God_Human",
    Value = _G.Settings.Auto_God_Human,
    Callback  = function(value)
        _G.Auto_God_Human = value
		_G.Settings.Auto_God_Human = value
		saveSettings()
    end
}

spawn(function()
    while task.wait() do
		if _G.Auto_God_Human then
			pcall(function()
				if game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Death Step") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Death Step") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Sharkman Karate") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Sharkman Karate") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") or game.Players.LocalPlayer.Character:FindFirstChild("Electro") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw") or game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Talon") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Talon") or game.Players.LocalPlayer.Character:FindFirstChild("Godhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Godhuman") then
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman",true) == 1 then
						if game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") and game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") and game.Players.LocalPlayer.Character:FindFirstChild("Superhuman").Level.Value >= 400 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
						end
					else
						game.StarterGui:SetCore("SendNotification", {
							Title = "Notification", 
							Text = "Not Have Superhuman" ,
							Icon = "http://www.roblox.com/asset/?id=9956697825",
							Duration = 2.5
						})
					end
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep",true) == 1 then
						if game.Players.LocalPlayer.Backpack:FindFirstChild("Death Step") and game.Players.LocalPlayer.Backpack:FindFirstChild("Death Step").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Death Step") and game.Players.LocalPlayer.Character:FindFirstChild("Death Step").Level.Value >= 400 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
						end
					else
						game.StarterGui:SetCore("SendNotification", {
							Title = "Notification", 
							Text = "Not Have Death Step" ,
							Icon = "http://www.roblox.com/asset/?id=9956697825",
							Duration = 2.5
						})
					end
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true) == 1 then
						if game.Players.LocalPlayer.Backpack:FindFirstChild("Sharkman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Sharkman Karate").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Sharkman Karate") and game.Players.LocalPlayer.Character:FindFirstChild("Sharkman Karate").Level.Value >= 400 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
						end
					else
						game.StarterGui:SetCore("SendNotification", {
							Title = "Notification", 
							Text = "Not Have SharkMan Karate" ,
							Icon = "http://www.roblox.com/asset/?id=9956697825",
							Duration = 2.5
						})
					end
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw",true) == 1 then
						if game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw").Level.Value >= 400 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
						end
					else
						game.StarterGui:SetCore("SendNotification", {
							Title = "Notification", 
							Text = "Not Have Electric Claw" ,
							Icon = "http://www.roblox.com/asset/?id=9956697825",
							Duration = 2.5
						})
					end
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon",true) == 1 then
						if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Talon") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Talon").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Dragon Talon") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Talon").Level.Value >= 400 then
							if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman",true), "Bring") then
								game.StarterGui:SetCore("SendNotification", {
									Title = "Notification", 
									Text = "Not Have Enough Material" ,
									Icon = "http://www.roblox.com/asset/?id=9956697825",
									Duration = 2.5
								})
							else
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman")
							end
						end
					else
						game.StarterGui:SetCore("SendNotification", {
							Title = "Notification", 
							Text = "Not Have Dragon Talon" ,
							Icon = "http://www.roblox.com/asset/?id=9956697825",
							Duration = 2.5
						})
					end
				else
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
				end
			end)
		end
	end
end)


local StatsSection = PlayerTab:CreateSection({
    Name = "สถิติ",Kaitun
	Side = "Left"
})

StatsSection:AddToggle{
    Name = "Auto Stats Kaitun",
    Flag = "Auto_Stats_Kaitun",
    Value = _G.Settings.Auto_Stats_Kaitun,
    Callback  = function(value)
        _G.Auto_Stats_Kaitun = value
        _G.Settings.Auto_Stats_Kaitun = value
        saveSettings()
    end
}

spawn(function()
	while wait() do
		pcall(function()
			if _G.Auto_Stats_Kaitun then
				if World1 then
					local args = {
						[1] = "AddPoint",
						[2] = "ระยะประชิด",
						[3] = _G.Point
						}
						
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				elseif World2 then
					local args = {
						[1] = "AddPoint",
						[2] = "ระยะประชิด",
						[3] = _G.Point
						}
						
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					local args = {
						[1] = "AddPoint",
						[2] = "ป้องกัน",
						[3] = _G.Point
						}
						
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
			end
		end)
	end
end)

StatsSection:AddToggle{
    Name = "สถิติอัตโนมัติระยะประชิด",
    Flag = "Auto_Stats_Melee",
    Value = _G.Settings.Auto_Stats_Melee,
    Callback  = function(value)
        _G.Auto_Stats_Melee = value
        _G.Settings.Auto_Stats_Melee = value
        saveSettings()
    end
}

spawn(function()
	while wait() do
		if _G.Auto_Stats_Melee then
			local args = {
				[1] = "AddPoint",
				[2] = "ระยะประชิด",
				[3] = _G.Point
			}
						
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end
end)

StatsSection:AddToggle{
    Name = "การป้องกันสถิติอัตโนมัติ",
    Flag = "Auto_Stats_Defense",
    Value = _G.Settings.Auto_Stats_Defense,
    Callback  = function(value)
        _G.Auto_Stats_Defense = value
        _G.Settings.Auto_Stats_Defense = value
        saveSettings()
    end
}

spawn(function()
	while wait() do
		if _G.Auto_Stats_Defense then
			local args = {
				[1] = "AddPoint",
				[2] = "ป้องกัน",
				[3] = _G.Point
			}
						
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end
end)

StatsSection:AddToggle{
    Name = "ดาบสถิติอัตโนมัติ",
    Flag = "Auto_Stats_Sword",
    Value = _G.Settings.Auto_Stats_Sword,
    Callback  = function(value)
        _G.Auto_Stats_Sword = value
        _G.Settings.Auto_Stats_Sword = value
        saveSettings()
    end
}

spawn(function()
	while wait() do
		if _G.Auto_Stats_Sword then
			local args = {
				[1] = "AddPoint",
				[2] = "ดาบ",
				[3] = _G.Point
			}
						
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end
end)

StatsSection:AddToggle{
    Name = "ปืนสถิติอัตโนมัติ",
    Flag = "Auto_Stats_Gun",
    Value = _G.Settings.Auto_Stats_Gun,
    Callback  = function(value)
        _G.Auto_Stats_Gun = value
        _G.Settings.Auto_Stats_Gun = value
        saveSettings()
    end
}

spawn(function()
	while wait() do
		if _G.Auto_Stats_Gun then
			local args = {
				[1] = "AddPoint",
				[2] = "ปืน",
				[3] = _G.Point
			}
						
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end
end)

StatsSection:AddToggle{
    Name = "ผลปีศาจผลสถิติอัตโนมัติ",
    Flag = "Auto_Stats_Devil_Fruit",
    Value = _G.Settings.Auto_Stats_Devil_Fruit,
    Callback  = function(value)
        _G.Auto_Stats_Devil_Fruit = value
        _G.Settings.Auto_Stats_Devil_Fruit = value
        saveSettings()
    end
}

spawn(function()
	while wait() do
		if _G.Auto_Stats_Devil_Fruit then
			local args = {
				[1] = "AddPoint",
				[2] = "ผลไม้ปีศาจ",
				[3] = _G.Point
			}
						
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end
end)

StatsSection:AddSlider({
    Name = "เลือกจุด",
    Flag = "Select_Point",
    Value = _G.Settings.Point,
    Min = 1,
    Max = 100,
    Textbox = true,
    Format = function(value)
		_G.Point = value
		_G.Settings.Point = value
		saveSettings()
		return "Point : " .. tostring(value)
    end
})

WeaponLaw = {}
for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
	if v:IsA("Tool") then
		table.insert(WeaponLaw ,v.Name)
	end
end

LawDungeonSection:AddDropdown({
    Name = "เลือกอาวุธ",
    Flag = "Select_Weapon",
    List = WeaponLaw,
	Value = _G.Settings.Select_Weapon_Law_Raid,
    Callback = function(value)
        _G.Select_Weapon_Law_Raid = value
		_G.Settings.Select_Weapon_Law_Raid = value
        saveSettings()
    end
})

LawDungeonSection:AddButton({
	Name = "รีเฟรชอาวุธ",
	Callback = function()
		table.clear(WeaponLaw)
		for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
			if v:IsA("Tool") then
				table.insert(WeaponLaw ,v.Name)
			end
		end
	end
})

local ShopTab = PepsisWorld:CreateTab({
    Name = "ร้านค้า,"
})

local DevilFruitShopSection = ShopTab:CreateSection({
    Name = "ร้านผลไม้ปีศาจ",
	Side = "Left"
})

local Remote_GetFruits = game.ReplicatedStorage:FindFirstChild("Remotes").CommF_:InvokeServer("GetFruits");

Table_DevilFruitSniper = {}
ShopDevilSell = {}

for i,v in next,Remote_GetFruits do
	table.insert(Table_DevilFruitSniper,v.Name)
	if v.OnSale then 
		table.insert(ShopDevilSell,v.Name)
	end
end

DevilFruitShopSection:AddDropdown({
    Name = "เลือกผลปีศาจ",
    Flag = "Select_Devil_Fruit",
    List = Table_DevilFruitSniper,
	Value = _G.Settings.Select_Devil_Fruit,
    Callback = function(value)
        _G.Select_Devil_Fruit = value
		_G.Settings.Select_Devil_Fruit = value
        saveSettings()
    end
})

DevilFruitShopSection:AddToggle({
    Name = "ซื้อผลไม้ปีศาจอัตโนมัติ",
    Flag = "Auto_Buy_Devil_Fruit",
    Value = _G.Settings.Auto_Buy_Devil_Fruit,
    Callback = function(value)
        _G.Auto_Buy_Devil_Fruit = value    
		_G.Settings.Auto_Buy_Devil_Fruit = value
        saveSettings()
    end
})

spawn(function()
	while wait() do
		if _G.Auto_Buy_Devil_Fruit then
			pcall(function()
				local string_1 = "ซื้อผลไม้ดิบ";
				local string_2 = _G.Select_Devil_Fruit;
				local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
				Target:InvokeServer(string_1, string_2);
			end)
		end                              
	end
end)

DevilFruitShopSection:AddToggle({
    Name = "ผลไม้สุ่มอัตโนมัติ",
    Flag = "Auto_Random_Fruit",
    Value = _G.Settings.Auto_Random_Fruit,
    Callback = function(value)
        _G.Auto_Random_Fruit = value    
		_G.Settings.Auto_Random_Fruit = value
        saveSettings()
    end
})

spawn(function()
	while wait() do
		if _G.Auto_Random_Fruit then	
			local args = {
				[1] = "Cousin",
				[2] = "ซื้อ"
			}
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end
end)

DevilFruitShopSection:AddToggle({
    Name = "นำผลไม้อัตโนมัติ",
    Flag = "Auto_Bring_Fruit",
    Value = _G.Settings.Auto_Bring_Fruit,
    Callback = function(value)
        _G.Auto_Bring_Fruit = value    
		_G.Settings.Auto_Bring_Fruit = value
        saveSettings()
    end
})

spawn(function()
	while wait() do
		if _G.Auto_Bring_Fruit then
			pcall(function()
				for i,v in pairs(game:GetService("Workspace"):GetChildren()) do
					if v:IsA("Tool") and string.find(v.Name,"Fruit") then 
						wait(2)
						firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart,v.Handle,0)    
					end
				end
			end)
		end
	end
end)

DevilFruitShopSection:AddToggle({
    Name = "ผลไม้เก็บอัตโนมัติ",
    Flag = "Auto_Store_Fruit",
    Value = _G.Settings.Auto_Store_Fruit,
    Callback = function(value)
        _G.Auto_Store_Fruit = value    
		_G.Settings.Auto_Store_Fruit = value
        saveSettings()
    end
})

spawn(function()
    while wait() do
        if _G.Auto_Store_Fruit then wait()
            for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                if string.find(v.Name,"Fruit") then
                    local FruitName = RemoveSpaces(v.Name)
                    if v.Name == "Bird: Falcon Fruit" then
                        NameFruit = "Bird-Bird: Falcon"
                    elseif v.Name == "Bird: Phoenix Fruit" then
                        NameFruit = "Bird-Bird: Phoenix"
                    elseif v.Name == "Human: Buddha Fruit" then
                        NameFruit = "Human-Human: Buddha"
                    else
                        NameFruit = FruitName.."-"..FruitName
                    end

                    local string_1 = "getInventoryFruits";
                    local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                    for i1,v1 in pairs(Target:InvokeServer(string_1)) do
                        if v1.Name == NameFruit then
                            HaveFruitInStore = true
                        end
                    end
                    if not Have then
                        local string_1 = "ร้านผลไม้";
                        local string_2 = NameFruit;
                        local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                        Target:InvokeServer(string_1, string_2);
                    end
                    HaveFruitInStore = false
                end
            end
        end
    end
end)

local AbilityShopSection = ShopTab:CreateSection({
    Name = "ความสามารถ",
	Side = "Right"
})

AbilityShopSection:AddButton({
    Name = "Buy Geppo",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Geppo")
    end
})

AbilityShopSection:AddButton({
    Name = "Buy Buso Haki",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Buso")
    end
})

AbilityShopSection:AddButton({
    Name = "Buy Soru",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Soru")
    end
})

AbilityShopSection:AddButton({
    Name = "Buy Ken Haki",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk","Buy")
    end
})

local FightingStyleShopSection = ShopTab:CreateSection({
    Name = "สไตล์การต่อสู้",
	Side = "Left"
})

FightingStyleShopSection:AddButton({
    Name = "Buy Black Leg",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
    end
})

FightingStyleShopSection:AddButton({
    Name = "Buy Electro",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
    end
})

FightingStyleShopSection:AddButton({
    Name = "Buy Fishman Karate",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
    end
})

FightingStyleShopSection:AddButton({
    Name = "Buy DragonClaw",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","1")
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2")
    end
})

FightingStyleShopSection:AddButton({
    Name = "Buy SuperHuman",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
    end
})

FightingStyleShopSection:AddButton({
    Name = "Buy Death Step",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
    end
})

FightingStyleShopSection:AddButton({
    Name = "Buy Sharkman Karate",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true)
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
    end
})

FightingStyleShopSection:AddButton({
    Name = "Buy Electric Claw",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
    end
})

FightingStyleShopSection:AddButton({
    Name = "Buy Dragon Talon",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
    end
})

FightingStyleShopSection:AddButton({
    Name = "Buy God Human",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman")
    end
})

local AccessoryShopSection = ShopTab:CreateSection({
    Name = "Accessory Shop",
	Side = "Right"
})

AccessoryShopSection:AddButton({
    Name = "Buy Tomoe Ring",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Tomoe Ring")
    end
})

AccessoryShopSection:AddButton({
    Name = "Buy Black Cape",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Black Cape")
    end
})

AccessoryShopSection:AddButton({
    Name = "Buy Swordsman Hat",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Swordsman Hat")
    end
})

local SwordShopSection = ShopTab:CreateSection({
    Name = "Sword Shop",
	Side = "Left"
})

SwordShopSection:AddButton({
    Name = "Buy Cutlass",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Cutlass")
    end
})

SwordShopSection:AddButton({
    Name = "Buy Katana",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Katana")
    end
})

SwordShopSection:AddButton({
    Name = "Buy Iron Mace",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Iron Mace")
    end
})

SwordShopSection:AddButton({
    Name = "Buy Duel Katana",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Duel Katana")
    end
})

SwordShopSection:AddButton({
    Name = "Buy Duel Katana",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Duel Katana")
    end
})

SwordShopSection:AddButton({
    Name = "Buy Triple Katana",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Triple Katana")
    end
})

SwordShopSection:AddButton({
    Name = "Buy Pipe",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Pipe")
    end
})

SwordShopSection:AddButton({
    Name = "Buy Dual-Headed Blade",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Dual-Headed Blade")
    end
})

SwordShopSection:AddButton({
    Name = "Buy Bisento",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Bisento")
    end
})

SwordShopSection:AddButton({
    Name = "Buy Soul Cane",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Soul Cane")
    end
})

local GunShopSection = ShopTab:CreateSection({
    Name = "Gun Shop",
	Side = "Right"
})

GunShopSection:AddButton({
    Name = "Buy Slingshot",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Slingshot")
    end
})

GunShopSection:AddButton({
    Name = "Buy Musket",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Musket")
    end
})

GunShopSection:AddButton({
    Name = "Buy Flintlock",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Flintlock")
    end
})

GunShopSection:AddButton({
    Name = "Buy Refined Flintlock",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Refined Flintlock")
    end
})

GunShopSection:AddButton({
    Name = "Buy Cannon",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Cannon")
    end
})

GunShopSection:AddButton({
    Name = "Buy Kabucha",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Slingshot","1")
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Slingshot","2")
    end
})

local RacefragmentSection = ShopTab:CreateSection({
    Name = "Race&Fragment Shop",
	Side = "Right"
})

RacefragmentSection:AddButton({
    Name = "Buy Race Ghoul",
    Callback = function()
		local args = {
			[1] = "Ectoplasm",
			[2] = "BuyCheck",
			[3] = 4
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		local args = {
			[1] = "Ectoplasm",
			[2] = "Change",
			[3] = 4
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end
})

RacefragmentSection:AddButton({
    Name = "Buy Cyborg",
    Callback = function()
		local args = {
			[1] = "CyborgTrainer",
			[2] = "Buy"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end
})

RacefragmentSection:AddButton({
    Name = "Buy Random Race",
    Callback = function()
		local args = {
			[1] = "BlackbeardReward",
			[2] = "Reroll",
			[3] = "2"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end
})

RacefragmentSection:AddButton({
    Name = "Buy Reset Stats",
    Callback = function()
		local args = {
			[1] = "BlackbeardReward",
			[2] = "Refund",
			[3] = "2"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end
})

local MiscTab = PepsisWorld:CreateTab({
    Name = "Misc"
})

local JoinSection = MiscTab:CreateSection({
    Name = "Join",
	Side = "Right"
})

JoinSection:AddButton({
    Name = "Join Pirates Team",
    Callback = function()
		local args = {
			[1] = "SetTeam",
			[2] = "Pirates"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args)) 
		local args = {
			[1] = "BartiloQuestProgress"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end
})

JoinSection:AddButton({
    Name = "Join Marines Team",
    Callback = function()
		local args = {
			[1] = "SetTeam",
			[2] = "Marines"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		local args = {
			[1] = "BartiloQuestProgress"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end
})

JoinSection:AddButton({
    Name = "Rejoin",
    Callback = function()
		local ts = game:GetService("TeleportService")
		local p = game:GetService("Players").LocalPlayer
		ts:Teleport(game.PlaceId, p)
    end
})

JoinSection:AddButton({
    Name = "Sever Hop",
    Callback = function()
		Hop()
    end
})

local OpenMenuSection = MiscTab:CreateSection({
    Name = "เปิดเมนู",
	Side = "Right"
})

OpenMenuSection:AddButton({
    Name = "รายการสิ่งของ",
    Callback = function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryWeapons")
		game.Players.localPlayer.PlayerGui.Main.Inventory.Visible = true
    end
})

OpenMenuSection:AddButton({
    Name = "Devil Fruit Shop",
    Callback = function()
		local args = {
			[1] = "GetFruits"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		game.Players.localPlayer.PlayerGui.Main.FruitShop.Visible = true
    end
})

OpenMenuSection:AddButton({
    Name = "Title Name",
    Callback = function()
		local args = {
			[1] = "getTitles"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		game.Players.localPlayer.PlayerGui.Main.Titles.Visible = true
    end
})

OpenMenuSection:AddButton({
    Name = "Color Haki",
    Callback = function()
		game.Players.localPlayer.PlayerGui.Main.Colors.Visible = true
    end
})

local MainMiscSection = MiscTab:CreateSection({
    Name = "Main Misc",
	Side = "Left"
})

MainMiscSection:AddToggle({
    Name = "หน้าจอสีขาว",
    Flag = "White_Screen",
    Value = _G.Settings.White_Screen,
    Callback = function(value)
        _G.White_Screen = value
		_G.Settings.White_Screen = value
		saveSettings()
		if _G.White_Screen then
			game:GetService("RunService"):Set3dRenderingEnabled(false)
		else
			game:GetService("RunService"):Set3dRenderingEnabled(true)
		end
    end
})

