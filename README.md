local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/WhoIsDanix/Andronema/master/main.lua"))()

local window = Library:Create("CC2", {
    MainFrame = Color3.fromRGB(45, 45, 63),
    TopBar = Color3.fromRGB(30, 30, 42),
    TabBar = Color3.fromRGB(30, 30, 42),
    Label = Color3.fromRGB(67, 67, 95),
    LabelHighlighted = Color3.fromRGB(49, 49, 70),
    Button = Color3.fromRGB(67, 67, 95),
    Toggle = Color3.fromRGB(67, 67, 95),
    TextBox = Color3.fromRGB(67, 67, 95),
    Slider = Color3.fromRGB(67, 67, 95)
})
local main = window:CreateTab("Main | TAB")

main:CreateLabel("CC2 Script | Made By Hyperglox#1238")
main:CreateLabel("Discord Server | https://discord.gg/8Dh8hHeEXE")
local DiscordServer = main:CreateButton("Test Button", function()
    warn("Coming Soon...")
end)

if window:IsDestroyed() then
    warn("Gui Has Been Destroyed!")
end
