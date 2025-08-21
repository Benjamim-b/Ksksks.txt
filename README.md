--// Criando ScreenGui
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "MenuScript"
screenGui.Parent = playerGui

--// Botão Ícone (abrir/fechar)
local iconButton = Instance.new("TextButton")
iconButton.Name = "IconButton"
iconButton.Size = UDim2.new(0, 40, 0, 40) -- quadrado pequeno
iconButton.Position = UDim2.new(0, 10, 0, 10)
iconButton.Text = "≡" -- símbolo de menu
iconButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
iconButton.TextColor3 = Color3.fromRGB(255,255,255)
iconButton.Parent = screenGui

local iconCorner = Instance.new("UICorner")
iconCorner.CornerRadius = UDim.new(0, 6)
iconCorner.Parent = iconButton

--// Frame do Menu
local menuFrame = Instance.new("Frame")
menuFrame.Name = "MenuFrame"
menuFrame.Size = UDim2.new(0, 200, 0, 200)
menuFrame.Position = UDim2.new(0, 60, 0, 10)
menuFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
menuFrame.Visible = false
menuFrame.Parent = screenGui

local frameCorner = Instance.new("UICorner")
frameCorner.CornerRadius = UDim.new(0, 8)
frameCorner.Parent = menuFrame

--// Função abrir/fechar menu
local aberto = false
iconButton.MouseButton1Click:Connect(function()
	aberto = not abertomessageBox:GetPropertyChangedSignal("Text"):Connect(function() messageVal.Value = messageBox.Text end)
