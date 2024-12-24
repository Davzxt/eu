local function createESP(player)
    local highlight = Instance.new("Highlight")
    highlight.Parent = player.Character or player.CharacterAdded:Wait()
    
    local billboardGui = Instance.new("BillboardGui")
    billboardGui.Adornee = player.Character:WaitForChild("Head")
    billboardGui.Size = UDim2.new(0, 100, 0, 50)
    billboardGui.StudsOffset = Vector3.new(0, 3, 0)
    billboardGui.Parent = player.Character
    
    local textLabel = Instance.new("TextLabel")
    textLabel.Text = player.Name
    textLabel.Size = UDim2.new(1, 0, 1, 0)
    textLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    textLabel.BackgroundTransparency = 1
    textLabel.Parent = billboardGui
end

local function onPlayerAdded(player)
    player.CharacterAdded:Connect(function()
        createESP(player)
    end)
end

game.Players.PlayerAdded:Connect(onPlayerAdded)

for _, player in pairs(game.Players:GetPlayers()) do
    onPlayerAdded(player)
end
