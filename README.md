_G.Executed = true
repeat wait() until game:IsLoaded()

_- [ Variables ] -_
local Players = game:GetService("Players");     
local Lighting = game:GetService("Lighting");
local ReplicatedStorage = game:GetService("ReplicatedStorage");
local CoreGui = game:GetService("CoreGui");
local ScriptContext = game:GetService("ScriptContext");
local VRService = game:GetService("VRService");
local VirtualUser = game:GetService("VirtualUser");
local RunService = game:GetService("RunService");
local HttpService = game:GetService("HttpService");
local UserInputService = game:GetService("UserInputService");
local MarketplaceService = game:GetService("MarketplaceService");
local VirtualInputManager = game:GetService("VirtualInputManager")
local CurrentCamera = workspace.CurrentCamera;

local LocalPlayer = Players.LocalPlayer;
local PlayerGui = LocalPlayer:FindFirstChildOfClass("PlayerGui")
local Mouse = LocalPlayer:GetMouse();
local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait(); 

local inGroup = LocalPlayer:IsInGroup(2726951) and true or false
local VIP = MarketplaceService:UserOwnsGamePassAsync(LocalPlayer.UserId, 2465866) and true or false

local VehicleInformation = ReplicatedStorage:FindFirstChild("VehicleInformation");
local HelicopterContainer = ReplicatedStorage:FindFirstChild("HelicopterContainer")
local CarCollection = workspace:FindFirstChild("CarCollection");
local rF = ReplicatedStorage:FindFirstChild("rF");
local rE = ReplicatedStorage:FindFirstChild("rE");

_- [ Libraries ] -_
local Notification = loadstring(game:HttpGet("https://raw.githubusercontent.com/saucekid/UI-Libraries/main/NotificationLib.lua"))()
function err(txt)
    Notification.Notify("Error", txt, "rbxassetid://1491260682", {
        Duration = 3,
        TitleSettings = {
            BackgroundColor3 = Color3.fromRGB(200, 200 , 200),
            TextColor3 = Color3.fromRGB(255, 0, 0),
            TextScaled = true,
            TextWrapped = true,
            TextSize = 14,
            Font = Enum.Font.SourceSansBold,
            TextXAlignment = Enum.TextXAlignment.Left,
            TextYAlignment = Enum.TextYAlignment.Center
        },
        DescriptionSettings = {
            BackgroundColor3 = Color3.fromRGB(200, 200 ,200),
            TextColor3 = Color3.fromRGB(240, 240, 240),
            TextScaled = true,
            TextWrapped = true,
            TextSize = 14,
            Font = Enum.Font.SourceSansBold,
            TextXAlignment = Enum.TextXAlignment.Left,
            TextYAlignment = Enum.TextYAlignment.Top,
        },
        IconSettings = {
            BackgroundTransparency = 1,
            BackgroundColor3 = Color3.fromRGB(255, 255, 255),               
        },
        GradientSettings = {
            GradientEnabled = false,
            SolidColorEnabled = true,
            SolidColor = Color3.fromRGB(255,0,0),
            Retract = true,
            Extend = false,
        },
        Main = {
            BorderColor3 = Color3.fromRGB(255, 0, 0),
            BackgroundColor3 = Color3.fromRGB(30, 30, 30),
            BackgroundTransparency = 0.05,
            Rounding = false,
            BorderSizePixel = 1
        }
    })
end

local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/saucekid/UI-Libraries/main/hub-lib.lua"))()
library.theme = {
    fontsize = 15,
    font = Enum.Font.Code,
    background = "rbxassetid://0",
    backgroundcolor = Color3.fromRGB(20, 20, 20),
    tabstextcolor = Color3.fromRGB(230, 230, 230),
    bordercolor = Color3.fromRGB(60, 60, 60),
    accentcolor = Color3.fromRGB(160,32,240),
    accentcolor2 = Color3.fromRGB(255, 255, 255),
    outlinecolor = Color3.fromRGB(60, 60, 60),
    outlinecolor2 = Color3.fromRGB(0, 0, 0),
    sectorcolor = Color3.fromRGB(30, 30, 30),
    toptextcolor = Color3.fromRGB(255, 255, 255),
    topheight = 48,
    topcolor = Color3.fromRGB(30, 30, 30),
    topcolor2 = Color3.fromRGB(30, 30, 30),
    buttoncolor = Color3.fromRGB(49, 49, 49),
    buttoncolor2 = Color3.fromRGB(39, 39, 39),
    itemscolor = Color3.fromRGB(170, 170, 170),
    itemscolor2 = Color3.fromRGB(200, 200, 200)
}

if not CarCollection or not rF or not rE then return err("Wrong game") else Notification.Notify("CC2 Script", "Created By Hyperglox#1238", Players:GetUserThumbnailAsync(LocalPlayer.UserId, Enum.ThumbnailType.HeadShot, Enum.ThumbnailSize.Size420x420)); wait(1) end -- check

if ReplicatedStorage:FindFirstChild("ClientError") then
    ReplicatedStorage.ClientError:Destroy()
end

_- [ Toggles ] -_
flags = {
    invincible = {},
    autofarm = {},
    silent = {},
    autoescape = {},
    tweentp = {},
    flying = {},
    jump = {},
    crashaura = {},
    tankaura = {},
    carspeed = {value = 0},
    tweenspeed = {value = 500},
    boostspeed = {value = 100},
    vflyspeed = {value = 1},
    jumppower = {value = 10},
    crashaurarange = {value = 70},
    tankaurarange = {value = 70},
    bodypaint = {value = "Gold"}
}

for _,flag in pairs(flags) do 
    if not flag["value"] then flag.value = false end
    setmetatable(flag, { -- im pro
        __call = function(self, b)
            self.value = b
        end
    })
end
