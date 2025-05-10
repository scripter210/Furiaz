local userInput = game:GetService("UserInputService")
local player = game.Players.LocalPlayer
local gui = script.Parent
local frame = gui:WaitForChild("KeyFrame")

local keyBox = frame:WaitForChild("KeyBox")
local confirmBtn = frame:WaitForChild("ConfirmButton")
local statusLabel = frame:WaitForChild("StatusLabel")

local correctKey = "12345"  -- Senha correta
local keyAccepted = false  -- Variável para verificar se a senha está correta

-- Abrir o painel com a tecla P
userInput.InputBegan:Connect(function(input, gameProcessed)
    if gameProcessed then return end
    if input.KeyCode == Enum.KeyCode.P then
        frame.Visible = true  -- Exibe o painel
    elseif input.KeyCode == Enum.KeyCode.Unknown and input.KeyCode.Name == "Ç" then
        frame.Visible = false  -- Esconde o painel
    end
end)

-- Funcionalidade para verificar a senha
confirmBtn.MouseButton1Click:Connect(function()
    local enteredKey = keyBox.Text  -- Texto digitado na caixa de texto
    if enteredKey == correctKey then
        statusLabel.Text = "✔ Acesso Liberado"
        statusLabel.TextColor3 = Color3.fromRGB(0, 255, 0)  -- Verde para senha correta
        keyAccepted = true
    else
        statusLabel.Text = "✖ Senha Incorreta"
        statusLabel.TextColor3 = Color3.fromRGB(255, 0, 0)  -- Vermelho para senha incorreta
        keyAccepted = false
    end
end)
