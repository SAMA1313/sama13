-- Script para Auto-Farm, Pegar Frutas, Espadas e Maestria no Blox Fruits

-- Configurações iniciais
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local currentQuest = nil
local farmingEnabled = true  -- Ativar/desativar o auto-farming
local fruta = nil  -- Para armazenar a fruta que o jogador pegará

-- Função para iniciar o auto-farming (atacar inimigos)
function startAutoFarm()
    while farmingEnabled do
        -- Encontrar inimigos próximos
        local mobs = {}
        for _, mob in pairs(workspace:GetChildren()) do
            if mob:FindFirstChild("Humanoid") and mob.Humanoid.Health > 0 then
                table.insert(mobs, mob)
            end
        end

        -- Atacar o primeiro inimigo encontrado
        if #mobs > 0 then
            local target = mobs[1]
            attackTarget(target)
        end

        -- Verificar
