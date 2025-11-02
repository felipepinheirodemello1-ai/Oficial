-- 🏔️ TERRAIN EDITOR SIMPLES
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local Mouse = player:GetMouse()
local Terrain = workspace.Terrain

-- Criar GUI
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player.PlayerGui

-- Botão principal
local mainBtn = Instance.new("TextButton")
mainBtn.Size = UDim2.new(0, 50, 0, 50)
mainBtn.Position = UDim2.new(0, 10, 0, 10)
mainBtn.Text = "🏔️"
mainBtn.BackgroundColor3 = Color3.fromRGB(0, 100, 150)
mainBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
mainBtn.Font = Enum.Font.GothamBold
mainBtn.TextSize = 20
mainBtn.Parent = screenGui

-- Material selecionado
local materialAtual = Enum.Material.Grass

-- Função para trocar material (CORRIGIDA)
local function TrocarMaterial(posicao)
    local sucesso, erro = pcall(function()
        -- Criar uma parte no lugar para substituir o terreno
        local parte = Instance.new("Part")
        parte.Size = Vector3.new(4, 4, 4)
        parte.Position = posicao
        parte.Anchored = true
        parte.Material = materialAtual
        
        -- Cor baseada no material
        if materialAtual == Enum.Material.Grass then
            parte.BrickColor = BrickColor.new("Bright green")
        elseif materialAtual == Enum.Material.Slate then
            parte.BrickColor = BrickColor.new("Dark stone grey")
        elseif materialAtual == Enum.Material.Ice then
            parte.BrickColor = BrickColor.new("Light blue")
        elseif materialAtual == Enum.Material.Water then
            parte.BrickColor = BrickColor.new("Bright blue")
        elseif materialAtual == Enum.Material.Brick then
            parte.BrickColor = BrickColor.new("Bright red")
        end
        
        parte.Parent = workspace
    end)
    
    if not sucesso then
        warn("Erro: " .. tostring(erro))
    end
end

-- Conectar clique do mouse
Mouse.Button1Down:Connect(function()
    if Mouse.Target then
        TrocarMaterial(Mouse.Hit.Position)
    end
end)

-- Interface simples
local function CriarInterface()
    -- Remover interface anterior se existir
    if screenGui:FindFirstChild("MatInterface") then
        screenGui.MatInterface:Destroy()
    end

    local frame = Instance.new("Frame")
    frame.Name = "MatInterface"
    frame.Size = UDim2.new(0, 150, 0, 200)
    frame.Position = UDim2.new(0, 70, 0, 10)
    frame.BackgroundColor3 = Color3.fromRGB(40, 40, 50)
    frame.Parent = screenGui

    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 8)
    corner.Parent = frame

    -- Título
    local titulo = Instance.new("TextLabel")
    titulo.Size = UDim2.new(1, 0, 0, 30)
    titulo.Text = "🧱 Materiais"
    titulo.TextColor3 = Color3.fromRGB(255, 255, 255)
    titulo.BackgroundColor3 = Color3.fromRGB(0, 100, 150)
    titulo.Font = Enum.Font.GothamBold
    titulo.TextSize = 14
    titulo.Parent = frame

    local tituloCorner = Instance.new("UICorner")
    tituloCorner.CornerRadius = UDim.new(0, 8)
    tituloCorner.Parent = titulo

    -- Materiais
    local materiais = {
        {"🌿 Grama", Enum.Material.Grass},
        {"🪨 Pedra", Enum.Material.Slate},
        {"⏣ Gelo", Enum.Material.Ice},
        {"🌊 Água", Enum.Material.Water},
        {"🧱 Tijolo", Enum.Material.Brick}
    }

    for i, material in ipairs(materiais) do
        local btn = Instance.new("TextButton")
        btn.Size = UDim2.new(1, -10, 0, 30)
        btn.Position = UDim2.new(0, 5, 0, (i-1)*35 + 40)
        btn.Text = material[1]
        btn.BackgroundColor3 = Color3.fromRGB(60, 60, 80)
        btn.TextColor3 = Color3.fromRGB(255, 255, 255)
        btn.Font = Enum.Font.Gotham
        btn.TextSize = 12
        btn.Parent = frame

        local btnCorner = Instance.new("UICorner")
        btnCorner.CornerRadius = UDim.new(0, 6)
        btnCorner.Parent = btn

        btn.MouseButton1Click:Connect(function()
            materialAtual = material[2]
            print("Material selecionado: " .. material[1])
        end)
    end
end

-- Abrir interface
mainBtn.MouseButton1Click:Connect(CriarInterface)

print("✅ Terrain Editor Pronto!")
print("🎯 Clique no botão 🏔️ e escolha um material")
print("🎯 Depois clique em qualquer lugar do mapa!")
