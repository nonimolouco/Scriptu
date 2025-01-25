-- Configurações
local playerName = game.Players.LocalPlayer.Name -- Nome do jogador que poderá usar o carro
local carModelName = "CarroDeDrift" -- Nome do modelo do carro
local driftForce = 10000 -- Força do drift

-- Função para criar o carro
local function createCar()
    -- Criar o carro (use um modelo existente da Toolbox ou crie seu próprio modelo e ajuste aqui)
    local car = Instance.new("Model")
    car.Name = carModelName

    -- Base do carro
    local base = Instance.new("Part")
    base.Size = Vector3.new(6, 1, 10)
    base.Position = Vector3.new(0, 5, 0)
    base.Anchored = false
    base.Name = "Base"
    base.Parent = car
    car.PrimaryPart = base

    -- Adicionar uma VehicleSeat
    local seat = Instance.new("VehicleSeat")
    seat.Size = Vector3.new(2, 1, 2)
    seat.Position = base.Position + Vector3.new(0, 1, 0)
    seat.Anchored = false
    seat.Name = "Seat"
    seat.Parent = car
    seat.MaxSpeed = 200
    seat.Torque = 4000

    -- Adicionar rodas (opcional, para personalizar)
    for i = 1, 4 do
        local wheel = Instance.new("Part")
        wheel.Size = Vector3.new(2, 2, 2)
        wheel.Shape = Enum.PartType.Cylinder
        wheel.Name = "Wheel" .. i
        wheel.Parent = car
    end

    car.Parent = workspace
    return car, seat
end

-- Função para ativar drift automaticamente
local function enableDrift(seat)
    local bodyVelocity = Instance.new("BodyVelocity")
    bodyVelocity.MaxForce = Vector3.new(1, 0, 1) * 1e6 -- Permite movimento apenas em XZ
    bodyVelocity.Velocity = Vector3.zero
    body
