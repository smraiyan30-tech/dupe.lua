# dupe.lua
-- Normal Player Friendly Dupe Script by el_raiyan7
local Player = game.Players.LocalPlayer
local PlayerGui = Player:WaitForChild("PlayerGui")

-- পুরোনো GUI মুছে ফেলা
if PlayerGui:FindFirstChild("PlayerDupeGui") then
    PlayerGui.PlayerDupeGui:Destroy()
end

-- GUI ডিজাইন
local ScreenGui = Instance.new("ScreenGui", PlayerGui)
ScreenGui.Name = "PlayerDupeGui"

local MainFrame = Instance.new("Frame", ScreenGui)
MainFrame.Size = UDim2.new(0, 250, 0, 180)
MainFrame.Position = UDim2.new(0.5, -125, 0.4, 0)
MainFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
MainFrame.BorderSizePixel = 0
MainFrame.Active = true
MainFrame.Draggable = true

local UICorner = Instance.new("UICorner", MainFrame)
UICorner.CornerRadius = UDim.new(0, 15)

local Title = Instance.new("TextLabel", MainFrame)
Title.Size = UDim2.new(1, 0, 0, 40)
Title.Text = "🎁 FREE ITEM DUPE 🎁"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.BackgroundColor3 = Color3.fromRGB(0, 120, 215)
Title.Font = Enum.Font.GothamBold
Title.TextSize = 18

local Instruction = Instance.new("TextLabel", MainFrame)
Instruction.Size = UDim2.new(1, 0, 0, 40)
Instruction.Position = UDim2.new(0, 0, 0.25, 0)
Instruction.Text = "আইটেমটি হাতে (Equip) নিয়ে নিচে ক্লিক করুন"
Instruction.TextColor3 = Color3.fromRGB(200, 200, 200)
Instruction.BackgroundTransparency = 1
Instruction.TextSize = 12

local DupeButton = Instance.new("TextButton", MainFrame)
DupeButton.Size = UDim2.new(0.8, 0, 0.3, 0)
DupeButton.Position = UDim2.new(0.1, 0, 0.55, 0)
DupeButton.Text = "DUPE (দ্বিগুণ করুন)"
DupeButton.BackgroundColor3 = Color3.fromRGB(0, 200, 100)
DupeButton.TextColor3 = Color3.new(1, 1, 1)
DupeButton.Font = Enum.Font.GothamBold
DupeButton.TextSize = 16

local BtnCorner = Instance.new("UICorner", DupeButton)
BtnCorner.CornerRadius = UDim.new(0, 8)

-- ডুপ্লিকেট করার আসল কোড
DupeButton.MouseButton1Click:Connect(function()
    local char = Player.Character
    local tool = char and char:FindFirstChildOfClass("Tool")
    
    if tool then
        -- একবার ক্লিকে আইটেমটি দ্বিগুণ হবে
        local clone = tool:Clone()
        clone.Parent = Player.Backpack
        
        DupeButton.Text = "✅ সফল হয়েছে!"
        task.wait(1)
        DupeButton.Text = "DUPE (দ্বিগুণ করুন)"
    else
        DupeButton.Text = "❌ হাতে কিছু নিন!"
        DupeButton.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
        task.wait(1)
        DupeButton.BackgroundColor3 = Color3.fromRGB(0, 200, 100)
        DupeButton.Text = "DUPE (দ্বিগুণ করুন)"
    end
end)
