pcall(function()

if not game.Players.LocalPlayer.Character or game.Players.LocalPlayer.Character:WaitForChild("Humanoid").RigType ~= Enum.HumanoidRigType.R15 then 
game.StarterGui:SetCore("SendNotification", {Title = "R6", Text = "You're on R6, bro. Change to R15!", Duration = 60})
return end

local st = os.clock()
local TweenService = game:GetService("TweenService")
cloneref = cloneref or function(o) return o end
local GazeGoGui = cloneref(game:GetService("CoreGui")) or game:GetService("CoreGui") or game.Players.LocalPlayer:WaitForChild("PlayerGui")


local Notifbro = {}

function Notify(titletxt, text, time)
    
    coroutine.wrap(function()
        local GUI = Instance.new("ScreenGui")
        local Main = Instance.new("Frame", GUI)
        local title = Instance.new("TextLabel", Main)
        local message = Instance.new("TextLabel", Main)

        GUI.Name = "BackgroundNotif"
        GUI.Parent = GazeGoGui

        local sw = workspace.CurrentCamera.ViewportSize.X
        local sh = workspace.CurrentCamera.ViewportSize.Y
        local nh = sh / 7
        local nw = sw / 5

        Main.Name = "MainFrame"
        Main.BackgroundColor3 = Color3.new(0.156863, 0.156863, 0.156863)
        Main.BackgroundTransparency = 0.2
        Main.BorderSizePixel = 0
        Main.Size = UDim2.new(0, nw, 0, nh)

        title.BackgroundColor3 = Color3.new(0, 0, 0)
        title.BackgroundTransparency = 0.9
        title.Size = UDim2.new(1, 0, 0, nh / 2)
        title.Font = Enum.Font.GothamBold
        title.Text = titletxt
        title.TextColor3 = Color3.new(1, 1, 1)
        title.TextScaled = true

        message.BackgroundColor3 = Color3.new(0, 0, 0)
        message.BackgroundTransparency = 1
        message.Position = UDim2.new(0, 0, 0, nh / 2)
        message.Size = UDim2.new(1, 0, 1, -nh / 2)
        message.Font = Enum.Font.Gotham
        message.Text = text
        message.TextColor3 = Color3.new(1, 1, 1)
        message.TextScaled = true

        local offset = 50
        for _, notif in ipairs(Notifbro) do
            offset = offset + notif.Size.Y.Offset + 10
        end

        Main.Position = UDim2.new(1, 5, 0, offset)
        table.insert(Notifbro, Main)

        task.wait(0.1)
        Main:TweenPosition(UDim2.new(1, -nw, 0, offset), Enum.EasingDirection.Out, Enum.EasingStyle.Bounce, 0.5, true)
        Main:TweenSize(UDim2.new(0, nw * 1.06, 0, nh * 1.06), Enum.EasingDirection.Out, Enum.EasingStyle.Elastic, 0.5, true)
        task.wait(0.5)
        Main:TweenSize(UDim2.new(0, nw, 0, nh), Enum.EasingDirection.Out, Enum.EasingStyle.Elastic, 0.2, true)

        task.wait(time)

        Main:TweenSize(UDim2.new(0, nw * 1.06, 0, nh * 1.06), Enum.EasingDirection.In, Enum.EasingStyle.Elastic, 0.2, true)
        task.wait(0.2)
        Main:TweenSize(UDim2.new(0, nw, 0, nh), Enum.EasingDirection.In, Enum.EasingStyle.Elastic, 0.2, true)
        task.wait(0.2)
        Main:TweenPosition(UDim2.new(1, 5, 0, offset), Enum.EasingDirection.In, Enum.EasingStyle.Bounce, 0.5, true)
        task.wait(0.5)

        GUI:Destroy()
        for i, notif in ipairs(Notifbro) do
            if notif == Main then
                table.remove(Notifbro, i)
                break
            end
        end

        for i, notif in ipairs(Notifbro) do
            local newOffset = 50 + (nh + 10) * (i - 1)
            notif:TweenPosition(UDim2.new(1, -nw, 0, newOffset), Enum.EasingDirection.Out, Enum.EasingStyle.Bounce, 0.5, true)
        end
    end)() -- Invoke the coroutine immediately
end

task.wait()

local guiName = "GazeVerificator"

if GazeGoGui:FindFirstChild(guiName) then
    Notify("Error","Script Already Executed", 1)
    return
end

local screenGui = Instance.new("ScreenGui")
screenGui.Name = guiName
screenGui.Parent = GazeGoGui

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 0, 0, 0)
frame.Visible = false
frame.Parent = screenGui

print("Running Script, May Lags A Bit")

local TweenService = game:GetService("TweenService")
local camera = workspace.CurrentCamera -- Get the camera for viewport size

-- Function to get dynamic sizes based on screen size
local function getScaledSize(relativeWidth, relativeHeight)
    local viewportSize = camera.ViewportSize
    return UDim2.new(0, viewportSize.X * relativeWidth, 0, viewportSize.Y * relativeHeight)
end

-- Create ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "DraggableGui"
screenGui.Parent = game.CoreGui



-- Create Frame (Menu)
local frame = Instance.new("TextButton")
frame.Name = "GazeBro"
frame.Text = ""
frame.Size = getScaledSize(0.3, 0.4) -- Frame is 30% of width and 40% of height
frame.Position = UDim2.new(0.5, -frame.Size.X.Offset / 2, 0.5, -frame.Size.Y.Offset / 2) -- Centered
frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
frame.BackgroundTransparency = 0.2
frame.BorderSizePixel = 2
frame.BorderColor3 = Color3.new(0, 0, 0)
frame.Active = true
frame.Draggable = true
frame.Parent = screenGui
local labelSize = UDim2.new(1, 0, 0.1, 0) -- 10% of frame's height
-- Create GAZE text label
local gazeLabel = Instance.new("TextLabel")
gazeLabel.Name = "GazeLabel"
gazeLabel.Text = "GAZE"
gazeLabel.Font = Enum.Font.SourceSansBold
gazeLabel.TextScaled = true -- Scale text
gazeLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
gazeLabel.BackgroundTransparency = 1
gazeLabel.Size = labelSize
gazeLabel.Position = UDim2.new(0, 0, 0, 0)
gazeLabel.Parent = frame

-- Create Search Bar
local searchBar = Instance.new("TextBox")
searchBar.Name = "SearchBar"
searchBar.Text = ""
searchBar.PlaceholderText = "Search..."
searchBar.Font = Enum.Font.SourceSans
searchBar.TextScaled = true -- Scale text
searchBar.TextColor3 = Color3.fromRGB(200, 200, 200)
searchBar.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
searchBar.BorderSizePixel = 0
searchBar.Size = UDim2.new(0.9, 0, 0.2, 0) -- 10% of frame's height
searchBar.Position = UDim2.new(0.05, 0, 0.10, 0)
searchBar.ClearTextOnFocus = true
searchBar.Parent = frame

-- Create Scroll Frame
local scrollFrame = Instance.new("ScrollingFrame")
scrollFrame.Name = "ScrollFrame"
scrollFrame.Size = UDim2.new(0.9, 0, 0.7, 0) -- 70% of frame's height
scrollFrame.Position = UDim2.new(0.05, 0, 0.3, 0)
scrollFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
scrollFrame.BorderSizePixel = 0
scrollFrame.ScrollBarThickness = 0 -- Hide the scroll bar
scrollFrame.ScrollingDirection = Enum.ScrollingDirection.Y -- Vertical scrolling only
scrollFrame.CanvasSize = UDim2.new(0, 0, 0, 0)
scrollFrame.ScrollBarImageTransparency = 1 -- Make the scroll bar invisible
scrollFrame.Parent = frame

local TweenService = game:GetService("TweenService")
local buttons = {}

local function createTheButton(text, callback)
    local button = Instance.new("TextButton")
    button.Text = text
    button.Font = Enum.Font.SourceSansBold
    button.TextScaled = true -- Scale text
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    button.Size = UDim2.new(1, 0, 0, 40) -- Fixed height for buttons
    button.Position = UDim2.new(1, 0, 0, #buttons * 45) -- Start off-screen to the right
    button.BackgroundTransparency = 1 -- Start fully transparent
    button.BorderSizePixel = 0
    button.Parent = scrollFrame

    button.MouseButton1Click:Connect(callback)

    -- Tween for fade-in effect
    local tweenInfo = TweenInfo.new(0.1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
    local goal = {
        Position = UDim2.new(0, 0, 0, #buttons * 45), -- Target position
        BackgroundTransparency = 0 -- Fully opaque
    }
    local tween = TweenService:Create(button, tweenInfo, goal)
    tween:Play()

    table.insert(buttons, button)
    scrollFrame.CanvasSize = UDim2.new(0, 0, 0, #buttons * 45) -- Update canvas size
end

-- Example button

-- Search functionality
searchBar:GetPropertyChangedSignal("Text"):Connect(function()
    local searchText = searchBar.Text:lower()
    local order = 0
    for _, button in ipairs(buttons) do
        if searchText == "" or button.Text:lower():find(searchText) then
            button.Visible = true
            button.Position = UDim2.new(0, 0, 0, order * 45) -- 5px spacing
            order += 1
        else
            button.Visible = false
        end
    end
    scrollFrame.CanvasSize = UDim2.new(0, 0, 0, order * 45)
end)


local normalSize = getScaledSize(0.3, 0.4) -- Normal size: 30% width, 40% height
local normalPosition = UDim2.new(0.5, -normalSize.X.Offset / 2, 0.5, -normalSize.Y.Offset / 2) -- Centered for normal size
local smallerSize = getScaledSize(0.15, 0.2) -- Smaller size: 15% width, 20% height
local smallerPosition = UDim2.new(0.5, -smallerSize.X.Offset / 2, 0.5, -smallerSize.Y.Offset / 2) -- Centered for smaller size
local isSmall = false
local clickCount = 0
local tweenInfo = TweenInfo.new(0.1, Enum.EasingStyle.Bounce, Enum.EasingDirection.Out)

-- Function to handle the frame shrinking and expanding
local function handleDoubleClick()
    if isSmall then
        -- Restore to normal size and position
        local tween = TweenService:Create(frame, tweenInfo, {Size = normalSize, Position = normalPosition})
        tween:Play()
        for _, child in ipairs(frame:GetChildren()) do
        if child:IsA("GuiObject") and not child:IsA("TextLabel") then
            child.Visible = true
            task.wait()
        else 
            child.Size = labelSize
            task.wait()
        end
    end
    else
        -- Shrink size and adjust position
        local tween = TweenService:Create(frame, tweenInfo, {Size = smallerSize, Position = smallerPosition})
        tween:Play()
        for _, child in ipairs(frame:GetChildren()) do
        if child:IsA("GuiObject") and not child:IsA("TextLabel") then
            child.Visible = false
            task.wait()
            else 
            child.Size = smallerSize
            task.wait()
        end
    end
    end
    isSmall = not isSmall
end




frame.MouseButton1Click:Connect(function()
    clickCount += 1
    if clickCount == 1 then
        -- Reset click count after 0.5 seconds if no second click
        task.delay(0.5, function()
            clickCount = 0
        end)
    elseif clickCount == 2 then
        -- Handle double-click
        handleDoubleClick()
        clickCount = 0
    end
end)

  
  local CurrentIdle = "None"
local CurrentWalk = "None"
local CurrentRun = "None"
local CurrentJump = "None"
local CurrentFall = "None"
local CurrentSwimIdle = "None"
local CurrentSwim = "None"
local CurrentClimb = "None"
local HttpService = game:GetService("HttpService")


local Players = game:GetService("Players")
local speaker = Players.LocalPlayer
    local Char = speaker.Character
        local Animate = Char.Animate


local function Wait1()
 local player = game.Players.LocalPlayer
  local character = player.Character or player.CharacterAdded:Wait()
   local humanoid = character:WaitForChild("Humanoid")
    while humanoid.Health <= 2 do
      task.wait(0.3) -- Wait for 0.1 seconds before checking again
       end
        end
        
        



local function Wait2()
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
    while humanoid:GetState() == Enum.HumanoidStateType.Dead or 
          humanoid:GetState() == Enum.HumanoidStateType.Ragdoll do
        task.wait(0.3)  -- wait for a short period before checking again
    end
end





local lastAnimations = {} -- Table to store last used animations




local function StopAnim()
    local speaker = Players.LocalPlayer
    local Char = speaker.Character
    local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")

    -- Stop all playing animation tracks
    for _, v in next, Hum:GetPlayingAnimationTracks() do
    
        v:Stop()
    end
    end

local function refresh()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")

    humanoid:ChangeState(Enum.HumanoidStateType.GettingUp)
    
end

local function refreshswim()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")

    humanoid:ChangeState(Enum.HumanoidStateType.GettingUp)
    task.wait(0.1)
    humanoid:ChangeState(Enum.HumanoidStateType.Swimming)
    
end


local function refreshclimb()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")

    humanoid:ChangeState(Enum.HumanoidStateType.GettingUp)
    task.wait(0.1)
    humanoid:ChangeState(Enum.HumanoidStateType.Climbing)
    
end
task.wait()
-- Define the animations table with animation IDs
local Animations = {
    Idle = {
["2016 Animation (mm2)"] = {"387947158", "387947464"},
Astronaut = {"891621366", "891633237"},
["Adidas Community"] = {"122257458498464", "102357151005774"},
Bold = {"16738333868", "16738334710"},
Borock = {"3293641938", "3293642554"},
Bubbly = {"910004836", "910009958"},
Cartoony = {"742637544", "742638445"},
Confident = {"1069977950", "1069987858"},
["Catwalk Glam"] = {"133806214992291","94970088341563"},
Cowboy = {"1014390418", "1014398616"},
["Drooling Zombie"] = {"3489171152", "3489171152"},
Elder = {"10921101664", "10921102574"},
Ghost = {"616006778","616008087"},
Knight = {"657595757", "657568135"},
Levitation = {"616006778", "616008087"},
Mage = {"707742142", "707855907"},
MrToilet = {"4417977954", "4417978624"},
Ninja = {"656117400", "656118341"},
NFL = {"92080889861410", "74451233229259"},
OldSchool = {"10921230744", "10921232093"},
Patrol = {"1149612882", "1150842221"},
Pirate = {"750781874", "750782770"},
["Default Retarget"] = {"95884606664820", "95884606664820"},
["Very Long"] = {"18307781743", "18307781743"},
Sway = {"560832030", "560833564"},
Popstar = {"1212900985", "1150842221"},
Princess = {"941003647", "941013098"},
R6 = {"12521158637","12521162526"},
["R15 Reanimated"] = {"4211217646", "4211218409"},
Realistic = {"17172918855", "17173014241"},
Robot = {"616088211", "616089559"},
Sneaky = {"1132473842", "1132477671"},
["Sports (Adidas)"] = {"18537376492", "18537371272"},
Soldier = {"3972151362", "3972151362"},
Stylish = {"616136790", "616138447"},
["Stylized Female"] = {"4708191566", "4708192150"},
Superhero = {"10921288909", "10921290167"},
Toy = {"782841498", "782845736"},
Udzal = {"3303162274", "3303162549"},
Vampire = {"1083445855", "1083450166"},
Werewolf = {"1083195517", "1083214717"},
["Wicked (Popular)"] = {"118832222982049", "76049494037641"},
["No Boundaries (Walmart)"] = {"18747067405", "18747063918"},
Zombie = {"616158929", "616160636"},
    },
    Walk = {
Astronaut = "891667138",
["Adidas Community"] = "122150855457006",
Bold = "16738340646",
Bubbly = "910034870",
Cartoony = "742640026",
Confident = "1070017263",
Cowboy = "1014421541",
["Catwalk Glam"] = "109168724482748",
["Drooling Zombie"] = "3489174223",
Elder = "10921111375",
Ghost = "616013216",
Knight = "10921127095",
Levitation = "616013216",
Mage = "707897309",
Ninja = "656121766",
NFL = "110358958299415",
OldSchool = "10921244891",
Patrol = "1151231493",
Pirate = "750785693",
["Default Retarget"] = "115825677624788",
Popstar = "1212980338",
Princess = "941028902",
R6 = "12518152696",
["R15 Reanimated"] = "4211223236",
["2016 Animation (mm2)"] = "387947975",
Robot = "616095330",
Sneaky = "1132510133",
["Sports (Adidas)"] = "18537392113",
Stylish = "616146177",
["Stylized Female"] = "4708193840",
Superhero = "10921298616",
Toy = "782843345",
Udzal = "3303162967",
Vampire = "1083473930",
Werewolf = "1083178339",
["Wicked (Popular)"] = "92072849924640",
["No Boundaries (Walmart)"] = "18747074203",
Zombie = "616168032",
    },
    Run = {
["2016 Animation (mm2)"] = "387947975",
["Adidas Community"] = "82598234841035",
Astronaut = "10921039308",
Bold = "16738337225",
Bubbly = "10921057244",
Cartoony = "10921076136",
Confident = "1070001516",
Cowboy = "1014401683",
["Catwalk Glam"] = "81024476153754",
["Drooling Zombie"] = "3489173414",
Elder = "10921104374",
Ghost = "616013216",
["Heavy Run (Udzal / Borock)"] = "3236836670",
Knight = "10921121197",
Levitation = "616010382",
Mage = "10921148209",
MrToilet = "4417979645",
Ninja = "656118852",
NFL = "117333533048078",
OldSchool = "10921240218",
Patrol = "1150967949",
Pirate = "750783738",
["Default Retarget"] = "102294264237491",
Popstar = "1212980348",
Princess = "941015281",
R6 = "12518152696",
["R15 Reanimated"] = "4211220381",
Robot = "10921250460",
Sneaky = "1132494274",
["Sports (Adidas)"] = "18537384940",
Stylish = "10921276116",
["Stylized Female"] = "4708192705",
Superhero = "10921291831",
Toy = "10921306285",
Vampire = "10921320299",
Werewolf = "10921336997",
["Wicked (Popular)"] = "72301599441680",
["No Boundaries (Walmart)"] = "18747070484",
Zombie = "616163682",
    },
    Jump = {
    Astronaut = "891627522",
["Adidas Community"] = "656117878",
    Bold = "16738336650",
    Bubbly = "910016857",
    Cartoony = "742637942",
    ["Catwalk Glam"] = "116936326516985",
    Confident = "1069984524",
    Cowboy = "1014394726",
    Elder = "10921107367",
    Ghost = "616008936",
    Knight = "910016857",
    Levitation = "616008936",
    Mage = "10921149743",
    Ninja = "656117878",
    NFL = "119846112151352",
    OldSchool = "10921242013",
    Patrol = "1148811837",
    Pirate = "750782230",
    ["Default Retarget"] = "117150377950987",
    Popstar = "1212954642",
    Princess = "941008832",
    Robot = "616090535",
    ["R15 Reanimated"] = "4211219390",
    R6 = "12520880485",
    Sneaky = "1132489853",
    ["Sports (Adidas)"] = "18537380791",
    Stylish = "616139451",
    ["Stylized Female"] = "4708188025",
    Superhero = "10921294559",
    Toy = "10921308158",
    Vampire = "1083455352",
    Werewolf = "1083218792",
    ["Wicked (Popular)"] = "104325245285198",
    ["No Boundaries (Walmart)"] = "18747069148",
    Zombie = "616161997",
},
    Fall = {
    Astronaut = "891617961",
["Adidas Community"] = "98600215928904",
    Bold = "16738333171",
    Bubbly = "910001910",
    Cartoony = "742637151",
    ["Catwalk Glam"] = "92294537340807",
    Confident = "1069973677",
    Cowboy = "1014384571",
    Elder = "10921105765",
    Knight = "10921122579",
    Levitation = "616005863",
    Mage = "707829716",
    Ninja = "656115606",
    NFL = "129773241321032",
    OldSchool = "10921241244",
    Patrol = "1148863382",
    Pirate = "750780242",
    ["Default Retarget"] = "110205622518029",
    Popstar = "1212900995",
    Princess = "941000007",
    Robot = "616087089",
    ["R15 Reanimated"] = "4211216152",
    R6 = "12520972571",
    Sneaky = "1132469004",
    ["Sports (Adidas)"] = "18537367238",
    Stylish = "616134815",
    ["Stylized Female"] = "4708186162",
    Superhero = "10921293373",
    Toy = "782846423",
    Vampire = "1083443587",
    Werewolf = "1083189019",
    ["Wicked (Popular)"] = "121152442762481",
    ["No Boundaries (Walmart)"] = "18747062535",
    Zombie = "616157476",
},
    SwimIdle = {
    Astronaut = "891663592",
["Adidas Community"] = "109346520324160",
    Bold = "16738339817",
    Bubbly = "910030921",
    Cartoony = "10921079380",
    ["Catwalk Glam"] = "98854111361360",
    Confident = "1070012133",
    CowBoy = "1014411816",
    Elder = "10921110146",
    Mage = "707894699",
    Ninja = "656118341",
    NFL = "79090109939093",
    Patrol = "1151221899",
    Knight = "10921125935",
    OldSchool = "10921244018",
    Levitation = "10921139478",
    Patrol = "1151221899",
    Popstar = "1212998578",
    Princess = "941025398",
    Pirate = "750785176",
    R6 = "12518152696",
    Robot = "10921253767",
    Sneaky = "1132506407",
    ["Sports (Adidas)"] = "18537387180",
    Stylish = "10921281964",
    Stylized = "4708190607",
    SuperHero = "10921297391",
    Toy = "10921310341",
    Vampire = "10921325443",
    Werewolf ="10921341319",
    ["Wicked (Popular)"] = "113199415118199",
    ["No Boundaries (Walmart)"] = "18747071682",
    
    
},
    Swim = {
    Astronaut = "891663592",
["Adidas Community"] = "133308483266208",
    Bubbly = "910028158",
    Bold = "16738339158",
    Cartoony = "10921079380",
    ["Catwalk Glam"] = "134591743181628",
    CowBoy = "1014406523",
    Confident = "1070009914",
    Elder = "10921108971",
    Knight = "10921125160",
    Mage = "707876443",
    NFL = "132697394189921",
    OldSchool = "10921243048",
    PopStar = "1212998578",
    Princess = "941018893",
    Pirate = "750784579",
    Patrol = "1151204998",
    R6 = "12518152696",
    Robot = "10921253142",
    Levitation = "10921138209",
    Stylish = "10921281000",
    SuperHero = "10921295495",
    Sneaky = "1132500520",
    ["Sports (Adidas)"] = "18537389531",
    Toy = "10921309319",
    Vampire = "10921324408",
    Werewolf = "10921340419",
    ["Wicked (Popular)"] = "99384245425157",
    ["No Boundaries (Walmart)"] = "18747073181",
    Zombie = "616165109",
    
},
   Climb = {
Astronaut = "10921032124",
["Adidas Community"] = "88763136693023",
Bold = "16738332169",
Cartoony = "742636889",
["Catwalk Glam"] = "119377220967554",
Confident = "1069946257",
CowBoy = "1014380606",
Elder = "845392038",
Ghost = "616003713",
Knight = "10921125160",
Levitation = "10921132092",
Mage = "707826056",
Ninja = "656114359",
NFL = "134630013742019",
OldSchool = "10921229866",
Patrol = "1148811837",
Popstar = "1213044953",
Princess = "940996062",
R6 = "12520982150",
["Reanimated R15"] = "4211214992",
Robot = "616086039",
Sneaky = "1132461372",
["Sports (Adidas)"] = "18537363391",
Stylish = "10921271391",
["Stylized Female"] = "4708184253",
SuperHero = "10921286911",
Toy = "10921300839",
Vampire = "1083439238",
WereWolf = "10921329322",
["Wicked (Popular)"] = "131326830509784",
["No Boundaries (Walmart)"] = "18747060903",
Zombie = "616156119"
}}



local function loadAnimation(animationId)
    -- Get the local player's character
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()

    -- Create a new animation instance
    local animation = Instance.new("Animation")
    animation.AnimationId = "rbxassetid://" .. tostring(animationId)

    -- Load the animation into the humanoid
    local humanoid = character:WaitForChild("Humanoid")
    local animationTrack = humanoid:LoadAnimation(animation)

    return animationTrack
end



for animationType, animationSets in pairs(Animations) do
    for setName, ids in pairs(animationSets) do
        if type(ids) == "table" then
            for _, id in ipairs(ids) do
                local anim = loadAnimation(id)
                
            end
        else
            local anim = loadAnimation(ids)
            
        end
    end
end



local HttpService = game:GetService("HttpService")

-- Save the last animations to a file


-- Call this function whenever `lastAnimations` is updated



local function Buy(gamePassID)
    local MarketplaceService = game:GetService("MarketplaceService")
    local success, errorMessage = pcall(function()
        MarketplaceService:PromptGamePassPurchase(game:GetService("Players").LocalPlayer, gamePassID)
    end)
    
    if not success then
        setclipboard("https://www.roblox.com/game-pass/" .. gamePassID)
        Notify("Copied", "Gamepass Link", 5)
    end
end

-- Function to reset idle animation
local function ResetIdle()


    local speaker = Players.LocalPlayer
    local Char = speaker.Character
    local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")
    -- Stop all playing animation tracks
    for _, v in next, Hum:GetPlayingAnimationTracks() do
    
    
        v:Stop()
    end

    -- Disable idle Animation
    pcall(function()
    local Animate = Char.Animate
    Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=0"
    Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=0"
    end)
end

-- Function to reset walk animation
local function ResetWalk()

    local speaker = Players.LocalPlayer
    local Char = speaker.Character
    local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")

    -- Stop all playing animation tracks
    for _, v in next, Hum:GetPlayingAnimationTracks() do
    
        v:Stop()
    end

    -- Disable walk Animation
    pcall(function()
    local Animate = Char.Animate
    Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=0"
    end)
end

-- Function to reset run animation

local function ResetRun()

    local speaker = Players.LocalPlayer
    local Char = speaker.Character
    local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")

    -- Stop all playing animation tracks
    for _, v in next, Hum:GetPlayingAnimationTracks() do
    
        v:Stop()
    end

    -- Dont Change it to task.wait
    wait(0.1)

    -- Disable run Animation
    pcall(function()
    local Animate = Char.Animate
    Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=0"
    end)
end

local function ResetJump()

    local speaker = Players.LocalPlayer
    local Char = speaker.Character
    local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")

    -- Stop all playing animation tracks
    for _, v in next, Hum:GetPlayingAnimationTracks() do
    
        v:Stop()
    end

    -- Dont Change it to task.wait
    wait(0.1)
pcall(function()
    -- Disable jump Animation
    local Animate = Char.Animate
    Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=0"
    end)
end

-- Function to reset fall animation
local function ResetFall()

    local speaker = Players.LocalPlayer
    local Char = speaker.Character
    local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")

    -- Stop all playing animation tracks
    for _, v in next, Hum:GetPlayingAnimationTracks() do
    
        v:Stop()
    end

    -- Disable fall Animation
    pcall(function()
    local Animate = Char.Animate
    Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=0"
    end)
end

local function ResetSwim()

    local speaker = Players.LocalPlayer
    local Char = speaker.Character
    local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")

    -- Stop all playing animation tracks
    for _, v in next, Hum:GetPlayingAnimationTracks() do
    
        v:Stop()
    end
pcall(function()
    -- Disable swim Animation
    local Animate = Char.Animate
    if Animate.swim then
    Animate.swim.Swim.AnimationId = "http://www.roblox.com/asset/?id=0"
    end
    end)
end



local function ResetSwimIdle()

    local speaker = Players.LocalPlayer
    local Char = speaker.Character
    local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")

    -- Stop all playing animation tracks
    for _, v in next, Hum:GetPlayingAnimationTracks() do
    
        v:Stop()
    end
pcall(function()
    -- Disable swim idle Animation
    local Animate = Char.Animate
    if Animate.swimidle then
    Animate.swimidle.SwimIdle.AnimationId = "http://www.roblox.com/asset/?id=0"
    end
    end)
end


local function ResetClimb()

    local speaker = Players.LocalPlayer
    local Char = speaker.Character
    local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")

    -- Stop all playing animation tracks
    for _, v in next, Hum:GetPlayingAnimationTracks() do
    
        v:Stop()
    end
pcall(function()
    -- Disable swim idle Animation
    local Animate = Char.Animate
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=0"
    end)
end

-- Function to set swim animation based on animation ID
local function setSwimAnimation(animationId)
    local speaker = Players.LocalPlayer
    local Char = speaker.Character
    local Animate = Char:FindFirstChild("Animate")

    if not Animate then return end

    lastAnimations.Swim = animationId
    ResetSwim()
    Animate.swim.Swim.AnimationId = "http://www.roblox.com/asset/?id=" .. animationId
    refreshswim()
end

-- Function to set animation based on animation type and ID
local function setAnimation(animationType, animationId)
local function saveLastAnimations(lasyAnimations)
    local data = HttpService:JSONEncode(lastAnimations)
    writefile("MeWhenUrMom.json", data)
end


    local speaker = Players.LocalPlayer
    local Char = speaker.Character
    local Animate = Char:FindFirstChild("Animate")
local function freeze()
    local player = cloneref(game:GetService("Players")).LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
    humanoid.PlatformStand = true

    if player and player.Character then
        task.spawn(function()
            for i, part in ipairs(player.Character:GetDescendants()) do
                if part:IsA("BasePart") and not part.Anchored then
                    part.Anchored = true
                end
            end
        end)
    end
end

local function unfreeze()
    local player = cloneref(game:GetService("Players")).LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
    humanoid.PlatformStand = false

    if player and player.Character then
        task.spawn(function()
            for i, part in ipairs(player.Character:GetDescendants()) do
                if part:IsA("BasePart") and part.Anchored then
                    part.Anchored = false
                    
                end
            end
        end)
    end
end

    if not Animate then return end
freeze()
task.wait(0.1)

    if animationType == "Idle" then
        lastAnimations.Idle = animationId
        
        ResetIdle()
        Animate.idle.Animation1.AnimationId = "http://www.roblox.com/asset/?id=" .. animationId[1]
        Animate.idle.Animation2.AnimationId = "http://www.roblox.com/asset/?id=" .. animationId[2]
        refresh()
     
        
    elseif animationType == "Walk" then
        lastAnimations.Walk = animationId
        ResetWalk()
        Animate.walk.WalkAnim.AnimationId = "http://www.roblox.com/asset/?id=" .. animationId
        refresh()
       
        
    elseif animationType == "Run" then
        lastAnimations.Run = animationId
        ResetRun()
        Animate.run.RunAnim.AnimationId = "http://www.roblox.com/asset/?id=" .. animationId
        refresh()
        
        
    elseif animationType == "Jump" then
        lastAnimations.Jump = animationId
        ResetJump()
        Animate.jump.JumpAnim.AnimationId = "http://www.roblox.com/asset/?id=" .. animationId
        refresh()
        
        
    elseif animationType == "Fall" then
        lastAnimations.Fall = animationId
        ResetFall()
           Animate.fall.FallAnim.AnimationId = "http://www.roblox.com/asset/?id=" .. animationId
        refresh()
        
        
    elseif animationType == "Swim" then
    lastAnimations.Swim = animationId
    if Animate.swim then
    ResetSwim()
    Animate.swim.Swim.AnimationId = "http://www.roblox.com/asset/?id=" .. animationId
    refreshswim()
    end
    
elseif animationType == "SwimIdle" then
    lastAnimations.SwimIdle = animationId
    if Animate.swimidle then
    ResetSwimIdle()
    Animate.swimidle.SwimIdle.AnimationId = "http://www.roblox.com/asset/?id=" .. animationId
    refreshswim()
    end
    
    elseif animationType == "Climb" then
    lastAnimations.Climb = animationId
    ResetClimb()
    Animate.climb.ClimbAnim.AnimationId = "http://www.roblox.com/asset/?id=" .. animationId
    refreshclimb()
end  
saveLastAnimations(lastAnimations)
wait()
unfreeze()
end

local function createButton(tab, text, animationType, animationId)
createTheButton(text .. " - " .. animationType , function()
  setAnimation(animationType, animationId)
  Notify(animationType,text,1)
  end)
  end

local HttpService = game:GetService("HttpService")

local function loadLastAnimations()
    print("Checking if MeWhenUrMom.json exists...")
    if isfile("MeWhenUrMom.json") then
        local data = readfile("MeWhenUrMom.json")
        Notify("Yippe", "Saved Animation Found, loading it", 10)

        local lastAnimationsData = HttpService:JSONDecode(data)
if lastAnimationsData.Idle then
    setAnimation("Idle", lastAnimationsData.Idle)
end

if lastAnimationsData.Walk then
    setAnimation("Walk", lastAnimationsData.Walk)
end

if lastAnimationsData.Run then
    setAnimation("Run", lastAnimationsData.Run)
end

if lastAnimationsData.Jump then
    setAnimation("Jump", lastAnimationsData.Jump)
end

if lastAnimationsData.Fall then
    setAnimation("Fall", lastAnimationsData.Fall)
end

if lastAnimationsData.Climb then
    setAnimation("Climb", lastAnimationsData.Climb)
end

if lastAnimationsData.Swim then
    setAnimation("Swim", lastAnimationsData.Swim)
end

if lastAnimationsData.SwimIdle then
    setAnimation("SwimIdle", lastAnimationsData.SwimIdle)
end
        
    else
        Notify("First?", "No Saved Animations Found", 5)
    end
end


loadLastAnimations()



local function PlayEmote(animationId)
StopAnim()
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
    local animation = Instance.new("Animation")
    animation.AnimationId = "rbxassetid://" .. animationId
    local animationTrack = humanoid:LoadAnimation(animation)
    animationTrack:Play()
    local function onMoved()
    local moveDirection = humanoid.MoveDirection
    if moveDirection.Magnitude > 0 then
        animationTrack:Stop()
    end
end
    local checkMovement
    checkMovement = game:GetService("RunService").RenderStepped:Connect(onMoved)
end


local function ZeroPlayEmote(animationId)
StopAnim()
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
    local animation = Instance.new("Animation")
    animation.AnimationId = "rbxassetid://" .. animationId
    local animationTrack = humanoid:LoadAnimation(animation)
    animationTrack:Play()
    animationTrack:AdjustSpeed(0)
    local function onMoved()
    local moveDirection = humanoid.MoveDirection
    if moveDirection.Magnitude > 0 then
        animationTrack:Stop()
    end
end
    local checkMovement
    checkMovement = game:GetService("RunService").RenderStepped:Connect(onMoved)
end


local function FPlayEmote(animationId)
StopAnim()
    local Players = game:GetService("Players")
    local player = Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")

    local animation = Instance.new("Animation")
    animation.AnimationId = "rbxassetid://" .. animationId
    local animationTrack = humanoid:LoadAnimation(animation)
    animationTrack:Play()
    local function freezeAnimation()
        animationTrack:AdjustSpeed(0) -- Freeze the animation by setting speed to 0
    end
    task.delay(animationTrack.Length * 0.9, freezeAnimation)

    

    -- Optional: Unfreeze or resume animation (if needed)
    -- animationTrack:AdjustSpeed(1) -- Resume animation

    local function onMoved()
        local moveDirection = humanoid.MoveDirection
        if moveDirection.Magnitude > 0 then
            animationTrack:Stop()
        end
    end

    local checkMovement = game:GetService("RunService").RenderStepped:Connect(onMoved)

    -- Example: Freeze the animation after 2 seconds
    
end





local function UpdaLabel(type,name)
if type == "Idle" then
        CurrentIdle = name
    elseif type == "Walk" then
        CurrentWalk = name
    elseif type == "Run" then
        CurrentRun = name
    elseif type == "Jump" then
        CurrentJump = name
    elseif type == "Fall" then
        CurrentFall = name
    elseif type == "SwimIdle" then
        CurrentSwimIdle = name
    elseif type == "Swim" then
    CurrentSwim = name
    elseif type == "Climb" then
    CurrentClimb = name
    end
end
       
                
                
                  
                  

  





local function AddR6Emote(name, id)
loadAnimation(id)
    createTheButton(name .. "- R6 Emote", function()
        PlayEmote(id)
    end)
end

local function AddEmote(name, id, price)
loadAnimation(id)
    createTheButton(name .. "- Emote", function()
        PlayEmote(id)
    end)
end


local function ZeroAddEmote(name, id, price)
loadAnimation(id)
    createTheButton(name .. "- Emote", function()
        ZeroPlayEmote(id)
    end)
end

local function AddFEmote(name, id, price)
loadAnimation(id)
    createTheButton(name .. "- Emote", function()
        FPlayEmote(id)
    end)
end

-- Define a local function

-- Define a function that takes another function as an argument and calls it
local function callFunction(func)
    if type(func) == "function" then
        func()
    else
        warn("The argument provided is not a function")
    end
end






local function AddDonate(Price, Id)
    createTheButton("Donate " .. Price .. " Robux", function()
        Buy(Id)
    end)
end





local function createButton(tab, text, animationType, animationId)
createTheButton(text .. " - " .. animationType , function()
  setAnimation(animationType, animationId)
  Notify(animationType,text,1)
  end)
  end



for name, ids in pairs(Animations.Idle) do
task.wait((1/3) * game:GetService("RunService").RenderStepped:Wait())
    createButton(Idle, name, "Idle", ids)
  
end

for name, id in pairs(Animations.Walk) do
task.wait((1/3) * game:GetService("RunService").RenderStepped:Wait())
    createButton(Walk, name, "Walk", id)
   
end

for name, id in pairs(Animations.Run) do
task.wait((1/3) * game:GetService("RunService").RenderStepped:Wait())
    createButton(Run, name, "Run", id)
    
end

for name, id in pairs(Animations.Jump) do
task.wait((1/3) * game:GetService("RunService").RenderStepped:Wait())
    createButton(Jump, name, "Jump", id)
   
end

for name, id in pairs(Animations.Fall) do
task.wait((1/3) * game:GetService("RunService").RenderStepped:Wait())
    createButton(Fall, name, "Fall", id)
 
end

for name, id in pairs(Animations.SwimIdle) do
task.wait((1/3) * game:GetService("RunService").RenderStepped:Wait())
    createButton(SwimIdle, name, "SwimIdle", id)

end

for name, id in pairs(Animations.Swim) do
task.wait((1/3) * game:GetService("RunService").RenderStepped:Wait())
    createButton(Swim, name, "Swim", id)

end

for name, id in pairs(Animations.Climb) do
task.wait((1/3) * game:GetService("RunService").RenderStepped:Wait())
    createButton(Climb, name, "Climb", id)
    
end





Players.LocalPlayer.CharacterAdded:Connect(function(character)
Wait1()
Wait2()


wait()
    if lastAnimations.Idle then
    setAnimation("Idle", lastAnimations.Idle)
end

if lastAnimations.Walk then
    setAnimation("Walk", lastAnimations.Walk)
end

if lastAnimations.Run then
    setAnimation("Run", lastAnimations.Run)
end

if lastAnimations.Jump then
    setAnimation("Jump", lastAnimations.Jump)
end

if lastAnimations.Fall then
    setAnimation("Fall", lastAnimations.Fall)
end

if lastAnimations.Climb then
    setAnimation("Climb", lastAnimations.Climb)
end

if lastAnimations.Swim then
    setAnimation("Swim", lastAnimations.Swim)
end

if lastAnimations.SwimIdle then
    setAnimation("SwimIdle", lastAnimations.SwimIdle)
end

end)




AddDonate(20, 1131371530)
AddDonate(200, 1131065702)
AddDonate(183, 1129915318)
AddDonate(2000, 1128299749)
AddEmote("Dance 1", 12521009666)
AddEmote("Dance 2", 12521169800)
AddEmote("Dance 3", 12521178362)
AddEmote("Cheer", 12521021991)
AddEmote("Laugh", 12521018724)
AddEmote("Point", 12521007694)
AddEmote("Wave", 12521004586)




AddFEmote("Soldier - Assault Fire", 4713811763)
AddEmote("Soldier - Assault Aim", 4713633512)
AddEmote("Zombie - Attack", 3489169607)
AddFEmote("Zombie - Death", 3716468774)
AddEmote("Roblox - Sleep", 2695918332)
AddEmote("Roblox - Quake", 2917204509)
AddEmote("Roblox - Rifle Reload", 3972131105)
ZeroAddEmote("Accurate T Pose", 2516930867)






Notify("PLEASE", "Donate me, im poor :(", 1)
local lt = os.clock() - st
Notify("loaded", string.format("in %.3f seconds.", lt), 5)

Notify("Changelog", "added 'Adidas Community'", 30)
end)