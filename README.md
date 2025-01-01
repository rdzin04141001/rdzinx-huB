local player = game.Players.LocalPlayer
local workspace = game.Workspace
local fruits = workspace.Fruits
local enemies = workspace.Enemies
local shop = workspace.Shop

local function coletarFrutas()
for _, fruit in pairs(fruits:GetChildren()) do
if fruit:IsA("Model") and fruit:FindFirstChild("Tool") then
local distance = (player.Character.HumanoidRootPart.Position - fruit.Position).Magnitude
if distance < 10 then
player.Character.HumanoidRootPart.CFrame = fruit.CFrame
wait(0.5)
player.Character.Humanoid:EquipTool(fruit.Tool)
end
end
end
end

local function farmarEXP()
for _, enemy in pairs(enemies:GetChildren()) do
if enemy:IsA("Model") and enemy:FindFirstChild("Humanoid") then
local distance = (player.Character.HumanoidRootPart.Position - enemy.HumanoidRootPart.Position).Magnitude
if distance < 10 then
player.Character.HumanoidRootPart.CFrame = enemy.HumanoidRootPart.CFrame
wait(0.5)
player.Character.Humanoid:Attack()
end
end
end
end

local function comprarItens()
for _, item in pairs(shop:GetChildren()) do
if item:IsA("Model") and item:FindFirstChild("Tool") then
player.Character.HumanoidRootPart.CFrame = item.CFrame
wait(0.5)
player.Character.Humanoid:EquipTool(item.Tool)
end
end
end

while true do
coletarFrutas()
farmarEXP()
comprarItens()
wait(1)
end
