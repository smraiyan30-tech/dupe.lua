# dupe.lua
-- Simple Dupe GUI by smraiyan30-tech
local Player = game.Players.LocalPlayer
local PlayerGui = Player:WaitForChild("PlayerGui")

-- পুরোনো GUI থাকলে রিমুভ করবে
if PlayerGui:FindFirstChild("SM_DupeGui") then
    PlayerGui.SM_DupeGui:Destroy()
end

-- মূল GUI ডিজাইন
local ScreenGui = Instance.new("ScreenGui", PlayerGui)
ScreenGui.Name = "SM_DupeGui"

local MainFrame = Instance.new("Frame", ScreenGui)
MainFrame.Size = UDim2.new(0, 260, 0, 160)
MainFrame.Position = UDim2.new(0.5, -130, 0.4, 0)
MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
MainFrame.BorderSizePixel = 0
MainFrame.Active = true
MainFrame.Draggable = true -- প্লেয়াররা মাউস দিয়ে সরাতে পারবে

local UICorner = Instance.new("UICorner", MainFrame)
UICorner.CornerRadius = UDim.new(0, 10)

-- টাইটেল বার
local Title = Instance.new("TextLabel", MainFrame)
Title.Size = UDim2.new(1, 0, 0, 40)
Title.Text = "SM RAIYAN DUPE HUB"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.BackgroundColor3 = Color3.fromRGB(0, 102, 204)
Title.Font = Enum.Font.SourceSansBold
Title.TextSize = 20
Instance.new("UICorner", Title).CornerRadius = UDim.new(0, 10)

-- বন্ধ করার বাটন (Close)
local CloseBtn = Instance.new("TextButton", MainFrame)
CloseBtn.Size = UDim2.new(0, 30, 0, 30)
CloseBtn.Position = UDim2.new(1, -35, 0, 5)
CloseBtn.Text = "X"
CloseBtn.TextColor3 = Color3.new(1, 1, 1)
CloseBtn.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
CloseBtn.MouseButton1Click:Connect(function() ScreenGui:Destroy() end)
Instance.new("UICorner", CloseBtn)

-- নির্দেশিকা
local Info = Instance.new("TextLabel", MainFrame)
Info.Size = UDim2.new(1, 0, 0, 30)
Info.Position = UDim2.new(0, 0, 0.3, 0)
Info.Text = "হাতে আইটেম নিন এবং নিচের বাটনে চাপ দিন"
Info.TextColor3 = Color3.fromRGB(180, 180, 180)
Info.BackgroundTransparency = 1
Info.TextSize = 12

-- ডুপ্লিকেট বাটন
local DupeButton = Instance.new("TextButton", MainFrame)
DupeButton.Size = UDim2.new(0.8, 0, 0, 45)
DupeButton.Position = UDim2.new(0.1, 0, 0.6, 0)
DupeButton.Text = "DUPE (দ্বিগুণ করুন)"
DupeButton.BackgroundColor3 = Color3.fromRGB(0, 180, 100)
DupeButton.TextColor3 = Color3.new(1, 1, 1)
DupeButton.Font = Enum.Font.SourceSansBold
DupeButton.TextSize = 18
Instance.new("UICorner", DupeButton)

-- ডুপ্লিকেট লজিক
DupeButton.MouseButton1Click:Connect(function()
    local tool = Player.Character and Player.Character:FindFirstChildOfClass("Tool")
    
    if tool then
        -- আইটেম ক্লোন করা
        local clone = tool:Clone()
        clone.Parent = Player.Backpack
        
        DupeButton.Text = "✅ সফল হয়েছে!"
        DupeButton.BackgroundColor3 = Color3.fromRGB(0, 100, 50)
        task.wait(1)
        DupeButton.Text = "DUPE (দ্বিগুণ করুন)"
        DupeButton.BackgroundColor3 = Color3.fromRGB(0, 180, 100)
    else
        DupeButton.Text = "❌ আগে হাতে আইটেম নিন!"
        DupeButton.BackgroundColor3 = Color3.fromRGB(150, 0, 0)
        task.wait(1.5)
        DupeButton.Text = "DUPE (দ্বিগুণ করুন)"
        DupeButton.BackgroundColor3 = Color3.fromRGB(0, 180, 100)
    end
end)
