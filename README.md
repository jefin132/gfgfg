local autoFarm = true -- Ativa/Desativa o auto farm
local delay = 5 -- Delay entre cada ação (em segundos)

-- Funções
local function farm()
    -- Código para coletar frutas
    game:GetService("ReplicatedStorage").Events.HarvestFruit:FireServer()
    wait(delay)
end

local function buyFruits()
    -- Código para comprar frutas
    game:GetService("ReplicatedStorage").Events.BuyFruit:FireServer()
    wait(delay)
end

-- Loop principal
while autoFarm do
    farm()
    buyFruits()
    wait(delay)
end

-- Comandos adicionais
game:GetService("StarterPlayerScripts").PlayerChatted:Connect(function(player, message)
    if message:lower() == "parar" then
        autoFarm = false
    elseif message:lower() == "iniciar" then
        autoFarm = true
    end
end)
