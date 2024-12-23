-- Configuração do título desejado
local novoTitulo = "Dono do Jogo"

-- Função para alterar o título
local function alterarTitulo()
    -- Obtém o jogador local
    local player = game.Players.LocalPlayer
    -- Aguarda o personagem carregar
    local character = player.Character or player.CharacterAdded:Wait()
    local head = character:WaitForChild("Head") -- Obtém a cabeça do personagem

    -- Procura pela GUI do título
    local titleGui = head:FindFirstChild("TitleGui") -- Substitua pelo nome real do GUI
    if titleGui then
        local titleText = titleGui:FindFirstChild("TitleLabel") -- Substitua pelo nome do texto
        if titleText then
            titleText.Text = novoTitulo -- Altera o texto do título
            print("Título alterado para: " .. novoTitulo)
        else
            warn("Label do título não encontrado!")
        end
    else
        warn("GUI do título não encontrado na cabeça!")
    end
end

-- Conectar o botão à função
local button = script.Parent -- O botão em que o script está anexado
button.MouseButton1Click:Connect(function()
    alterarTitulo() -- Chama a função ao clicar no botão
end)
