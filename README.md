-- EDITOR DE SCRIPTS PARA CELULAR - COMPACTO
local Players = game:GetService("Players")
local player = Players.LocalPlayer

-- Criar a GUI
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "ScriptEditorMobile"
screenGui.Parent = player.PlayerGui

-- Botão para abrir o editor (pequeno e discreto)
local openBtn = Instance.new("TextButton")
openBtn.Size = UDim2.new(0, 45, 0, 45)
openBtn.Position = UDim2.new(0, 5, 0, 5)
openBtn.Text = "📝"
openBtn.BackgroundColor3 = Color3.fromRGB(0, 100, 200)
openBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
openBtn.Font = Enum.Font.GothamBold
openBtn.TextSize = 18
openBtn.ZIndex = 100
openBtn.Parent = screenGui

-- Arredondar botão
local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(1, 0)
corner.Parent = openBtn

-- Função para criar o editor mobile
local function criarEditorMobile()
    -- Remover editor anterior se existir
    if screenGui:FindFirstChild("EditorMobile") then
        screenGui.EditorMobile:Destroy()
    end
    
    -- Criar frame principal (menor para celular)
    local editorFrame = Instance.new("Frame")
    editorFrame.Name = "EditorMobile"
    editorFrame.Size = UDim2.new(0.9, 0, 0.7, 0) -- 90% da largura, 70% da altura
    editorFrame.Position = UDim2.new(0.05, 0, 0.15, 0) -- Centralizado
    editorFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
    editorFrame.ZIndex = 90
    editorFrame.Parent = screenGui
    
    -- Borda arredondada
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 12)
    corner.Parent = editorFrame
    
    -- Header compacto
    local header = Instance.new("Frame")
    header.Size = UDim2.new(1, 0, 0, 35)
    header.BackgroundColor3 = Color3.fromRGB(0, 100, 200)
    header.ZIndex = 91
    header.Parent = editorFrame
    
    local headerCorner = Instance.new("UICorner")
    headerCorner.CornerRadius = UDim.new(0, 12)
    headerCorner.Parent = header
    
    -- Título compacto
    local title = Instance.new("TextLabel")
    title.Size = UDim2.new(0.6, 0, 1, 0)
    title.Position = UDim2.new(0, 8, 0, 0)
    title.Text = "📱 Editor"
    title.TextColor3 = Color3.fromRGB(255, 255, 255)
    title.BackgroundTransparency = 1
    title.Font = Enum.Font.GothamBold
    title.TextSize = 14
    title.ZIndex = 92
    title.Parent = header
    
    -- Botão FECHAR (X) - Pequeno
    local closeBtn = Instance.new("TextButton")
    closeBtn.Size = UDim2.new(0, 25, 0, 25)
    closeBtn.Position = UDim2.new(1, -30, 0.5, -12)
    closeBtn.Text = "✕"
    closeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    closeBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
    closeBtn.Font = Enum.Font.GothamBold
    closeBtn.TextSize = 12
    closeBtn.ZIndex = 92
    closeBtn.Parent = header
    
    local closeCorner = Instance.new("UICorner")
    closeCorner.CornerRadius = UDim.new(1, 0)
    closeCorner.Parent = closeBtn
    
    -- Área do editor (compacta)
    local editorArea = Instance.new("Frame")
    editorArea.Size = UDim2.new(1, -10, 1, -85)
    editorArea.Position = UDim2.new(0, 5, 0, 40)
    editorArea.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
    editorArea.ZIndex = 91
    editorArea.Parent = editorFrame
    
    local editorCorner = Instance.new("UICorner")
    editorCorner.CornerRadius = UDim.new(0, 8)
    editorCorner.Parent = editorArea
    
    -- Caixa de texto do editor (fonte menor para mobile)
    local textBox = Instance.new("TextBox")
    textBox.Size = UDim2.new(1, -10, 1, -10)
    textBox.Position = UDim2.new(0, 5, 0, 5)
    textBox.Text = "print(\"Olá!\")\n-- Toque para digitar\n-- Use botões abaixo"
    textBox.BackgroundColor3 = Color3.fromRGB(10, 10, 15)
    textBox.TextColor3 = Color3.fromRGB(255, 255, 255)
    textBox.Font = Enum.Font.Code
    textBox.TextSize = 12  -- Texto menor para mobile
    textBox.TextXAlignment = Enum.TextXAlignment.Left
    textBox.TextYAlignment = Enum.TextYAlignment.Top
    textBox.MultiLine = true
    textBox.TextWrapped = true
    textBox.ClearTextOnFocus = false
    textBox.ZIndex = 92
    textBox.Parent = editorArea
    
    -- Barra de ferramentas compacta
    local toolbar = Instance.new("Frame")
    toolbar.Size = UDim2.new(1, -10, 0, 35)
    toolbar.Position = UDim2.new(0, 5, 1, -40)
    toolbar.BackgroundColor3 = Color3.fromRGB(40, 40, 50)
    toolbar.ZIndex = 91
    toolbar.Parent = editorFrame
    
    local toolbarCorner = Instance.new("UICorner")
    toolbarCorner.CornerRadius = UDim.new(0, 8)
    toolbarCorner.Parent = toolbar
    
    -- Botões compactos para mobile
    local runBtn = Instance.new("TextButton")
    runBtn.Size = UDim2.new(0.3, -5, 0, 25)
    runBtn.Position = UDim2.new(0, 5, 0.5, -12)
    runBtn.Text = "▶️ Exec"
    runBtn.BackgroundColor3 = Color3.fromRGB(0, 150, 0)
    runBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    runBtn.Font = Enum.Font.GothamBold
    runBtn.TextSize = 11
    runBtn.ZIndex = 92
    runBtn.Parent = toolbar
    
    local runCorner = Instance.new("UICorner")
    runCorner.CornerRadius = UDim.new(0, 6)
    runCorner.Parent = runBtn
    
    local clearBtn = Instance.new("TextButton")
    clearBtn.Size = UDim2.new(0.3, -5, 0, 25)
    clearBtn.Position = UDim2.new(0.33, 0, 0.5, -12)
    clearBtn.Text = "🧹 Limpar"
    clearBtn.BackgroundColor3 = Color3.fromRGB(150, 100, 0)
    clearBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    clearBtn.Font = Enum.Font.GothamBold
    clearBtn.TextSize = 11
    clearBtn.ZIndex = 92
    clearBtn.Parent = toolbar
    
    local clearCorner = Instance.new("UICorner")
    clearCorner.CornerRadius = UDim.new(0, 6)
    clearCorner.Parent = clearBtn
    
    -- Status compacto
    local status = Instance.new("TextLabel")
    status.Size = UDim2.new(0.34, -5, 0, 25)
    status.Position = UDim2.new(0.66, 0, 0.5, -12)
    status.Text = "✅ Pronto"
    status.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    status.TextColor3 = Color3.fromRGB(255, 255, 255)
    status.Font = Enum.Font.Gotham
    status.TextSize = 10
    status.ZIndex = 92
    status.Parent = toolbar
    
    local statusCorner = Instance.new("UICorner")
    statusCorner.CornerRadius = UDim.new(0, 6)
    statusCorner.Parent = status
    
    -- FUNÇÕES DOS BOTÕES
    
    -- BOTÃO FECHAR
    closeBtn.MouseButton1Click:Connect(function()
        editorFrame:Destroy()
    end)
    
    -- BOTÃO EXECUTAR
    runBtn.MouseButton1Click:Connect(function()
        local codigo = textBox.Text
        status.Text = "⚡ Exec..."
        
        local sucesso, erro = pcall(function()
            loadstring(codigo)()
        end)
        
        if sucesso then
            status.Text = "✅ OK"
        else
            status.Text = "❌ Erro"
        end
    end)
    
    -- BOTÃO LIMPAR
    clearBtn.MouseButton1Click:Connect(function()
        textBox.Text = ""
        status.Text = "🧹 Limpo"
    end)
    
    -- Fechar ao tocar fora (opcional para mobile)
    local function fecharAoTocarFora(input)
        if input.UserInputType == Enum.UserInputType.Touch then
            local pos = Vector2.new(input.Position.X, input.Position.Y)
            local absolutePosition = editorFrame.AbsolutePosition
            local absoluteSize = editorFrame.AbsoluteSize
            
            if pos.X < absolutePosition.X or pos.X > absolutePosition.X + absoluteSize.X or
               pos.Y < absolutePosition.Y or pos.Y > absolutePosition.Y + absoluteSize.Y then
                editorFrame:Destroy()
            end
        end
    end
    
    -- Conectar evento de toque (opcional)
    -- game:GetService("UserInputService").InputBegan:Connect(fecharAoTocarFora)
end

-- Conectar botão de abrir
openBtn.MouseButton1Click:Connect(criarEditorMobile)

print("==================================")
print("📱 EDITOR MOBILE CARREGADO!")
print("✅ Otimizado para celular")
print("✅ Interface compacta")
print("✅ Toque no botão 📝")
print("==================================")

-- Manter após respawn
player.CharacterAdded:Connect(function()
    if not player.PlayerGui:FindFirstChild("ScriptEditorMobile") then
        screenGui.Parent = player.PlayerGui
    end
end)

-- Versão ainda mais compacta para testes rápidos
local function criarEditorMini()
    if screenGui:FindFirstChild("EditorMini") then
        screenGui.EditorMini:Destroy()
        return
    end
    
    local miniFrame = Instance.new("Frame")
    miniFrame.Name = "EditorMini"
    miniFrame.Size = UDim2.new(0.8, 0, 0, 150) -- Muito compacto
    miniFrame.Position = UDim2.new(0.1, 0, 0, 60)
    miniFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
    miniFrame.ZIndex = 90
    miniFrame.Parent = screenGui
    
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 8)
    corner.Parent = miniFrame
    
    -- Header mini
    local miniHeader = Instance.new("Frame")
    miniHeader.Size = UDim2.new(1, 0, 0, 25)
    miniHeader.BackgroundColor3 = Color3.fromRGB(0, 100, 200)
    miniHeader.ZIndex = 91
    miniHeader.Parent = miniFrame
    
    local miniTitle = Instance.new("TextLabel")
    miniTitle.Size = UDim2.new(0.6, 0, 1, 0)
    miniTitle.Text = "📝 Mini Editor"
    miniTitle.TextColor3 = Color3.fromRGB(255, 255, 255)
    miniTitle.BackgroundTransparency = 1
    miniTitle.Font = Enum.Font.GothamBold
    miniTitle.TextSize = 12
    miniTitle.ZIndex = 92
    miniTitle.Parent = miniHeader
    
    local miniClose = Instance.new("TextButton")
    miniClose.Size = UDim2.new(0, 20, 0, 20)
    miniClose.Position = UDim2.new(1, -25, 0.5, -10)
    miniClose.Text = "X"
    miniClose.TextColor3 = Color3.fromRGB(255, 255, 255)
    miniClose.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
    miniClose.Font = Enum.Font.GothamBold
    miniClose.TextSize = 10
    miniClose.ZIndex = 92
    miniClose.Parent = miniHeader
    
    miniClose.MouseButton1Click:Connect(function()
        miniFrame:Destroy()
    end)
    
    -- Área de código mini
    local miniTextBox = Instance.new("TextBox")
    miniTextBox.Size = UDim2.new(1, -10, 1, -35)
    miniTextBox.Position = UDim2.new(0, 5, 0, 30)
    miniTextBox.Text = "print(\"Teste\")"
    miniTextBox.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
    miniTextBox.TextColor3 = Color3.fromRGB(255, 255, 255)
    miniTextBox.Font = Enum.Font.Code
    miniTextBox.TextSize = 11
    miniTextBox.TextXAlignment = Enum.TextXAlignment.Left
    miniTextBox.TextYAlignment = Enum.TextYAlignment.Top
    miniTextBox.MultiLine = true
    miniTextBox.ZIndex = 92
    miniTextBox.Parent = miniFrame
    
    -- Botão executar mini
    local miniRun = Instance.new("TextButton")
    miniRun.Size = UDim2.new(1, -10, 0, 20)
    miniRun.Position = UDim2.new(0, 5, 1, -25)
    miniRun.Text = "⚡ Executar Código"
    miniRun.BackgroundColor3 = Color3.fromRGB(0, 150, 0)
    miniRun.TextColor3 = Color3.fromRGB(255, 255, 255)
    miniRun.Font = Enum.Font.GothamBold
    miniRun.TextSize = 10
    miniRun.ZIndex = 92
    miniRun.Parent = miniFrame
    
    miniRun.MouseButton1Click:Connect(function()
        loadstring(miniTextBox.Text)()
    end)
end

-- Botão para editor mini (opcional)
local miniBtn = Instance.new("TextButton")
miniBtn.Size = UDim2.new(0, 40, 0, 40)
miniBtn.Position = UDim2.new(0, 50, 0, 5)
miniBtn.Text = "🔧"
miniBtn.BackgroundColor3 = Color3.fromRGB(100, 100, 200)
miniBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
miniBtn.Font = Enum.Font.GothamBold
miniBtn.TextSize = 16
miniBtn.ZIndex = 100
miniBtn.Parent = screenGui

local miniCorner = Instance.new("UICorner")
miniCorner.CornerRadius = UDim.new(1, 0)
miniCorner.Parent = miniBtn

miniBtn.MouseButton1Click:Connect(criarEditorMini)
