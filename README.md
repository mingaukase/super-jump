local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

local jumpHeight = 450 -- Aumentei o pulo para ser muito mais alto
local gravityScale = 1.5 -- Ajustei para uma queda mais suave
local walkSpeed = 30 -- Velocidade de caminhada no chão

-- Função para alterar a gravidade
game:GetService("Workspace").Gravity = gravityScale * 196.2 -- 196.2 é a gravidade padrão no Roblox

-- Configurando a força de pulo
humanoid.JumpHeight = jumpHeight
humanoid.UseJumpPower = true
humanoid.JumpPower = 200 -- Força de pulo bem alta para garantir o aumento

-- Definindo a velocidade de caminhada
humanoid.WalkSpeed = walkSpeed -- Velocidade de movimento no chão

-- Atualizando o player caso ele morra ou respawne
player.CharacterAdded:Connect(function()
    character = player.Character or player.CharacterAdded:Wait()
    humanoid = character:WaitForChild("Humanoid")
    humanoid.JumpHeight = jumpHeight
    humanoid.UseJumpPower = true
    humanoid.JumpPower = 200
    humanoid.WalkSpeed = walkSpeed
end)
