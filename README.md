local Material = loadstring(game:HttpGet("https://raw.githubusercontent.com/Kinlei/MaterialLua/master/Module.lua"))()

local UI = Material.Load({
     Title = "Getting Started",
     Style = 3,
     SizeX = 400,
     SizeY = 100,
     Theme = "Light"
})

local Page = UI.New({
    Title = "Main"
})

Page.Button({
    Text = "Click Me!",
    Callback = function()
       print("Clicked!") 
    end
})
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
Notification.Notify("CC2", "Made By HYperglox")
