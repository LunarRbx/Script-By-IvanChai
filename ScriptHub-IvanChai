local Start=os.clock()

local UI=loadstring(game:HttpGetAsync'https://raw.githubusercontent.com/max9597/Scripts/lt2/uisD')():Initiate();

local demo4=UI:CreateTab(5181994100,'Main');
local HumanoidSectionTab4=demo4:CreateSection()
local PlSettings=HumanoidSectionTab4:CreateSubSection('Player Settings');
local Rewards=HumanoidSectionTab4:CreateSubSection('Player Rewards');

local Trades=UI:CreateTab(5181994100,'TradeScam');
local TradeSC=Trades:CreateSection()
local TradeScam=TradeSC:CreateSubSection('TradeScam');

local ListMenu=UI:CreateTab(5181994100,'Value Huge');
local HumanoidSectionTabList=ListMenu:CreateSection()
local ListHuge=HumanoidSectionTabList:CreateSubSection('HugeList');
local InfoHuge=HumanoidSectionTabList:CreateSubSection('Info Huge');

local demo=UI:CreateTab(5181994100,'AutoFarm');
local HumanoidSectionTab=demo:CreateSection()
local HumanoidSection=HumanoidSectionTab:CreateSubSection('AutoFarm Settings');
local StatsTracker=HumanoidSectionTab:CreateSubSection('Stats Tracker');

local demo2=UI:CreateTab(12534722366,'Egg');
local HumanoidSectionTab2=demo2:CreateSection()
local HumanoidSection2=HumanoidSectionTab2:CreateSubSection('AutoEggs Settings');

local demo3=UI:CreateTab(5181994100,'Pets');
local HumanoidSectionTab3=demo3:CreateSection()
local HumanoidSection3=HumanoidSectionTab3:CreateSubSection('Auto Golden/Rainbow');

local Boost=UI:CreateTab(5181994100,'AutoBoost');
local ABoost=Boost:CreateSection()
local AutoBoost=ABoost:CreateSubSection('Boosts');

local Library = require(game:GetService("ReplicatedStorage").Library)
local Network = Library.Network
local World = Library.Save.Get().World
local Directory = Library.Directory
local NP
List = game:HttpGet('https://raw.githubusercontent.com/LunarRbx/Script-By-IvanChai/main/ListPets-CosmicValue')
PetP = string.split(List, "**")
GetEquipped = Library.PetCmds.GetEquipped
LP = game:GetService("Players").LocalPlayer
PF = LP.PlayerGui.Inventory.Frame.Main.Pets.Normal
RS = game:GetService("ReplicatedStorage")
PetD = {}
Last_World = ""
_G.Enable = {
    ["Auto Claim Gift"] = false,
    ["Auto Claim Reward"] = false,
    ["Auto Claim VIP Reward"] = false,
    ["Auto Farm"] = false,
    ["Auto Egg"] = false,
    ["Auto Golden"] = false,
    ["Auto Rainbow"] = false,
    ["Auto Triple Coins"] = false,
    ["Auto Triple Damage"] = false,
    ["Auto Super Lucky"] = false,
    ["Auto Ultra Lucky"] = false,
    ["Auto Farm Heart"] = false,
    ["Auto Claim Mail"] = false
}

--Выебал_PSX.Exe
if not _G.k then
    hookfunction(getupvalue(Network.Invoke, 1), function() return true end)
    _G.k = true
end

--Value Huge
function GetPetZ(Pet)
    for i,v in pairs(PetP) do
        if string.find(v, Pet) then
            temp = string.split(v, " | ")
        end
    end
    _G.Name:UpdateHeader(temp[1])
    _G.Value:UpdateHeader(temp[2])
    _G.GemValue:UpdateHeader(temp[3])
end
for i,v in pairs(PetP) do
    if string.find(v, "Huge") then
        temp = string.split(v, " | ")
        if temp[1] ~= "" then
            table.insert(PetD,temp[1])
        end
    end
end
ListHuge:CreateDropDown(function(L)
    GetPetZ(L)
end,PetD,'Select Huge',false);

TradeScam:CreateButton('Trade Scam Off/On',function()
    if LP.PlayerGui.Trading.Frame.Trade.Client.Pets.Visible then
        LP.PlayerGui.Trading.Frame.Trade.Client.Pets.Visible = false
    else
        LP.PlayerGui.Trading.Frame.Trade.Client.Pets.Visible = true
    end
end,true,false,'Hint'); --animation,hint toggle,hint

_G.Name = InfoHuge:CreateButton('---------',function()
end,false,false,'Hint'); --animation,hint toggle,hint
_G.Value = InfoHuge:CreateButton('---------',function()
end,false,false,'Hint'); --animation,hint toggle,hint
_G.GemValue = InfoHuge:CreateButton('---------',function()
end,false,false,'Hint'); --animation,hint toggle,hint

--AntiAFK
game:GetService("Players").LocalPlayer.Idled:connect(function()
    game:GetService("VirtualUser"):ClickButton2(Vector2.new())
end)


--Получение монет сразу в инвентарь
getsenv(LP.PlayerScripts.Scripts.Game.Orbs).AddOrb=function(a,aa) Network.Fire('Claim Orbs', {tostring(a)}) end
getsenv(LP.PlayerScripts.Scripts.Game.Lootbags).Add=function(a,aa) Network.Fire('Collect Lootbags', {tostring(a)}) end

--Забирание подарков
TempG = 1
Rewards:CreateToggle('Auto Claim Gift',false,function(toggle2)
    _G.Enable["Auto Claim Gift"] = toggle2
	if toggle2 then
        spawn(function()
            while _G.Enable["Auto Claim Gift"] do
                Network.Invoke("Redeem Free Gift", TempG)
                if TempG < 12 then
                    TempG = TempG+1
                else
                    TempG = 1
                end
                wait(.1)
            end
        end)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в 

--Авто получение вип и обычной награды
Rewards:CreateToggle('Auto Claim Reward',false,function(toggle2)
    _G.Enable["Auto Claim Reward"] = toggle2
	if toggle2 then
        spawn(function()
            while _G.Enable["Auto Claim Reward"] do
                Network.Fire("Rewards Redeemed")
                wait(1)
            end
        end)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

Rewards:CreateToggle('Auto Claim VIP Reward',false,function(toggle2)
    _G.Enable["Auto Claim VIP Reward"] = toggle2
	if toggle2 then
        spawn(function()
            while _G.Enable["Auto Claim VIP Reward"] do
                Network.Invoke("Redeem VIP Rewards")
                wait(1)
            end
        end)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке
Rewards:CreateToggle('Auto Claim Mail',false,function(toggle)
    _G.Enable["Auto Claim Mail"] = toggle
    spawn(function()
        while _G.Enable["Auto Claim Mail"] do
            Network.Invoke("Claim All Mail")
            wait(5)
        end
    end)
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

--Получение монеток
function GetCoin()
    a = {}
    for i,v in pairs(Library.Things.Coins:GetChildren()) do
        if v:GetAttribute("Area") == Location then
            table.insert(a, v:GetAttribute("ID"))
        end
    end
    return a[math.random(1,#a)]
end
function GetHeartCoin()
    b = {}
    for i,v in pairs(Library.Things.Coins:GetChildren()) do
        if string.find(v:GetAttribute("Name"),"Heart Pile") then
            table.insert(b, v:GetAttribute("ID"))
        end
    end
    if not b == {} then 
        return b[math.random(1,#b)]
    else
        return nil
    end
end

--Получение петов
function Pet()
    allPets = {}
    temp = GetEquipped()
    for i=1, #temp do
        table.insert(allPets, temp[i].uid) 
    end
    return allPets
end

-- ZONE
Zone = {}
for i,v in pairs(Library.Directory.Areas) do
    table.insert(Zone, v.name)
end
Method = "Method"
--Авто фарм
HumanoidSection:CreateToggle('AutoFarm Enable',false,function(toggle)
    _G.Enable["Auto Farm"] = toggle
	if toggle then
        spawn(function()
            while _G.Enable["Auto Farm"] do
                if Method ~= "Method" then
                    if Method == "Multi-target" then
                        task.wait(SpeedAF/10)
                        for z,d in pairs(Pet()) do
                            Coin = GetCoin()
                            task.spawn(function()
                               Network.Invoke("Join Coin",Coin,{d})
                            end)
                            Network.Fire("Farm Coin",Coin,d)
                            if game.PlaceId == 10321372166 then
                                wait(0.1)
                            end
                        end
                    elseif Method == "Single" then
                        task.wait(SpeedAF/50)
                        Coin = GetCoin()
                        task.spawn(function()
                            Network.Invoke("Join Coin",Coin,Pet())
                        end)
                        for i,v in pairs(Pet()) do
                            Network.Fire("Farm Coin",Coin,v)
                        end
                        if game.PlaceId == 10321372166 then
                                wait(0.1)
                        end
                    end
                else
                    task.wait()
                end
            end
        end)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

--Авто фарм Сердец
HumanoidSection:CreateToggle('AutoFarm Heart Enable',false,function(toggle)
    _G.Enable["Auto Farm Heart"] = toggle
	if toggle then
        spawn(function()
            while _G.Enable["Auto Farm Heart"] do
                task.wait(SpeedAF/10)
                for z,d in pairs(Pet()) do
                    CoinZ = GetHeartCoin()
                    if not CoinZ == nil then
                        task.spawn(function()
                            Network.Invoke("Join Coin",CoinZ,{d})
                        end)
                        Network.Fire("Farm Coin",CoinZ,d)
                        if game.PlaceId == 10321372166 then
                            wait(0.1)
                        end
                    end
                end
            end
        end)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

StatsTracker:CreateButton('Stats Tracker',function()
	loadstring(game:HttpGet('https://pastebin.com/raw/dPXXyp4A'))()
end,true,false,'Hint'); --animation,hint toggle,hint

HumanoidSection:CreateDropDown(function(L)
    Method = L
end,{"Multi-target","Single"},'Method',false);

HumanoidSection:CreateDropDown(function(L)
    Location = L
end,Zone,'Location',false);

HumanoidSection:CreateSlider('Speed Farm',function(Speed)
	SpeedAF = Speed
end,5,20,8,true,'Hint'); --Минимум,Максимум,Стандартное значение,Вкл/Откл подсказок,текст в подсказке

-- EGGS

Eggs = {}
for ii,vv in pairs(Library.Directory.Eggs) do
    if not string.find(ii, "Golden") then
        table.insert(Eggs, ii)
    end
end

HumanoidSection2:CreateToggle('AutoOpen Enable',false,function(toggle2)
    _G.Enable["Auto Egg"] = toggle2
	if toggle2 then
        spawn(function()
            while _G.Enable["Auto Egg"] do
                if Golden then
                    wait(.1)
                    Network.Invoke("Buy Egg",'Golden '..Egg,Triple,Octuple)
                else
                    wait(.1)
                    Network.Invoke("Buy Egg",Egg,Triple,Octuple)
                end
            end
        end)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

HumanoidSection2:CreateDropDown(function(E)
    Egg = E
end,Eggs,'Eggs',false);

--Golden/Basic
HumanoidSection2:CreateToggle('Golden eggs',false,function(toggle)
    Golden = toggle
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

--Triple/Octuple
HumanoidSection2:CreateToggle('Triple eggs',false,function(toggleTr)
    Triple = toggleTr
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

HumanoidSection2:CreateToggle('Octuple eggs',false,function(toggleOc)
    Octuple = toggleOc
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

--Auto Golden/Rainbow
function GetPet()
    Pet = {
        ["Basic"] = {},
        ["Golden"] = {},
        ["Rainbow"] = {},
        ["HC_Basic"] = {},
        ["HC_Golden"] = {},
        ["HC_Rainbow"] = {}
    }
    for qq,q in pairs(Library.Save.Get().Pets) do
        if Directory.Pets[q.id].rarity ~= "Event" and Directory.Pets[q.id].rarity ~= "Exclusive" then
            if q.dm ~= true then
                if not LP.PlayerGui.Inventory.Frame.Main.Pets.Normal[q.uid].HC.Visible then
                    if q.g == true then
                        if not Pet["Golden"][q.id] then
                            Pet["Golden"][q.id] = {}
                        end
                        table.insert(Pet["Golden"][q.id], q.uid)
                    elseif q.r == true then
                        if not Pet["Rainbow"][q.id] then
                            Pet["Rainbow"][q.id] = {}
                        end
                        table.insert(Pet["Rainbow"][q.id], q.uid)
                    else
                        if not Pet["Basic"][q.id] then
                            Pet["Basic"][q.id] = {}
                        end
                        table.insert(Pet["Basic"][q.id], q.uid)
                    end
                else
                    if q.g == true then
                        if not Pet["HC_Golden"][q.id] then
                            Pet["HC_Golden"][q.id] = {}
                        end
                        table.insert(Pet["HC_Golden"][q.id], q.uid)
                    elseif q.r == true then
                        if not Pet["HC_Rainbow"][q.id] then
                            Pet["HC_Rainbow"][q.id] = {}
                        end
                        table.insert(Pet["HC_Rainbow"][q.id], q.uid)
                    else
                        if not Pet["HC_Basic"][q.id] then
                            Pet["HC_Basic"][q.id] = {}
                        end
                        table.insert(Pet["HC_Basic"][q.id], q.uid)
                    end
                end
            end
        end
    end
    return Pet
end

HumanoidSection3:CreateToggle('Auto Golden',false,function(toggle)
    _G.Enable["Auto Golden"] = toggle
    while toggle do
        PList = GetPet()
        TempWorldPet = "Basic"
        if game.PlaceId == 10321372166 then
            TempWorldPet = "HC_Basic"
        end
        for i,v in pairs(PList[TempWorldPet]) do
            temp_pets = {}
            for ii,vv in pairs(v) do
                if #temp_pets<NP then
                    table.insert(temp_pets, vv)
                end
            end
            if #temp_pets == NP then
                if _G.Enable["Auto Golden"] == false then
                    break
                end
                print(Network.Invoke("Use Golden Machine", temp_pets))
            end
            task.wait(1)
        end
        task.wait(1)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

HumanoidSection3:CreateToggle('Auto Rainbow',false,function(toggle)
    _G.Enable["Auto Rainbow"] = toggle
    while toggle do
        PList = GetPet()
        TempWorldPet = "Golden"
        if game.PlaceId == 10321372166 then
            TempWorldPet = "HC_Golden"
        end
        for i,v in pairs(PList[TempWorldPet]) do
            temp_pets = {}
            for ii,vv in pairs(v) do
                if #temp_pets<NP then
                    table.insert(temp_pets, vv)
                end
            end
            if #temp_pets == NP then
                if _G.Enable["Auto Rainbow"] == false then
                    break
                end
                print(Network.Invoke("Use Rainbow Machine", temp_pets))
            end
            task.wait(1)
        end
        task.wait(1)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке
if game.PlaceId == 10321372166 then
    Use = 10
else
    Use = 6
end
HumanoidSection3:CreateSlider('Use pets',function(P)
	NP = P
end,1,Use,Use,false,'Hint'); --Минимум,Максимум,Стандартное значение,Вкл/Откл подсказок,текст в подсказке

--Авто бусты
AutoBoost:CreateToggle('Auto Triple Coins',false,function(toggle)
    _G.Enable["Auto Triple Coins"] = toggle
	if toggle then
        spawn(function()
            while _G.Enable["Auto Triple Coins"] and not Library.Save.Get().Boosts["Triple Coins"] do
                Network.Fire("Activate Boost", "Triple Coins")
                wait(1)
            end
        end)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

AutoBoost:CreateToggle('Auto Triple Damage',false,function(toggle)
    _G.Enable["Auto Triple Damage"] = toggle
	if toggle then
        spawn(function()
            while _G.Enable["Auto Triple Damage"] and not Library.Save.Get().Boosts["Triple Damage"] do
                Network.Fire("Activate Boost", "Triple Damage")
                wait(1)
            end
        end)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

AutoBoost:CreateToggle('Auto Super Lucky',false,function(toggle)
    _G.Enable["Auto Super Lucky"] = toggle
	if toggle then
        spawn(function()
            while _G.Enable["Auto Super Lucky"] and not Library.Save.Get().Boosts["Super Lucky"] do
                Network.Fire("Activate Boost", "Super Lucky")
                wait(1)
            end
        end)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

AutoBoost:CreateToggle('Auto Ultra Lucky',false,function(toggle)
    _G.Enable["Auto Ultra Lucky"] = toggle
	if toggle then
        spawn(function()
            while _G.Enable["Auto Ultra Lucky"] and not Library.Save.Get().Boosts["Ultra Lucky"] do
                Network.Fire("Activate Boost", "Ultra Lucky")
                wait(1)
            end
        end)
    end
end,false,false,'Hint'); --Базовое значение, Вкл/Откл подсказок, Текст в подсказке

warn("Script Enable in: "..string.format("%.2f", os.clock()-Start).." second");
