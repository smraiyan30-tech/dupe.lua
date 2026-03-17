# dupe.lua
-- Admin Extreme Duplicator by el_raiyan7
local Player = game.Players.LocalPlayer
local PlayerGui = Player:WaitForChild("PlayerGui")

-- পুরোনো GUI থাকলে ডিলিট করে দেবে
if PlayerGui:FindFirstChild("ExtremeDupeGui") then
    PlayerGui.ExtremeDupeGui:Destroy()
end

-- GUI Setup
local ScreenGui = Instance.new("ScreenGui", PlayerGui)
ScreenGui.Name = "ExtremeDupeGui"

local MainFrame = Instance.new("Frame", ScreenGui)
MainFrame.Size = UDim2.new(0, 220, 0, 150)
MainFrame.Position = UDim2.new(0.5, -110, 0.4, 0)
MainFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
MainFrame.BorderSizePixel = 2
MainFrame.Active = true
MainFrame.Draggable = true

local Title = Instance.new("TextLabel", MainFrame)
Title.Size = UDim2.new(1, 0, 0, 30)
Title.Text = "EL_RAIYAN7 DUPE HUB"
Title.TextColor3 = Color3.fromRGB(255, 255, 0)
Title.BackgroundColor3 = Color3.fromRGB(30, 30, 30)

local CountLabel = Instance.new("TextLabel", MainFrame)
CountLabel.Size = UDim2.new(1, 0, 0, 30)
CountLabel.Position = UDim2.new(0, 0, 0.3, 0)
CountLabel.Text = "Items Duplicated: 0"
CountLabel.TextColor3 = Color3.new(1, 1, 1)
CountLabel.BackgroundTransparency = 1

local DupeButton = Instance.new("TextButton", MainFrame)
DupeButton.Size = UDim2.new(0.8, 0, 0.3, 0)
DupeButton.Position = UDim2.new(0.1, 0, 0.6, 0)
DupeButton.Text = "START MULTIPLY"
DupeButton.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
DupeButton.TextColor3 = Color3.new(1, 1, 1)

-- লজিক এবং ভেরিয়েবল
local isDuplicationOn = false
local totalCount = 0

DupeButton.MouseButton1Click:Connect(function()
    isDuplicationOn = not isDuplicationOn
    
    if isDuplicationOn then
        DupeButton.Text = "STOPPING..."
        DupeButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
        
        -- দ্রুত ডুপ্লিকেট করার জন্য লুপ
        task.spawn(function()
            while isDuplicationOn do
                local char = Player.Character
                local tool = char and char:FindFirstChildOfClass("Tool")
                
                if tool then
                    -- এক ক্লিকে ৫টি করে কপি তৈরি হবে (যাতে গেম ক্রাশ না করে)
                    for i = 1, 5 do 
                        local clone = tool:Clone()
                        clone.Parent = Player.Backpack
                        totalCount = totalCount + 1
                    end
                    CountLabel.Text = "Items Duplicated: " .. totalCount
                end
                task.wait(0.01) -- অনেক দ্রুত কাজ করবে
            end
        end)
    else
        DupeButton.Text = "START MULTIPLY"
        DupeButton.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
    end
end)
