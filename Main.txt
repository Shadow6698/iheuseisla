-- Carregar Rayfield
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
    Name = "Avatar Hub - Rayfield",
    LoadingTitle = "Carregando Avatares 3D",
    LoadingSubtitle = "by Nightmare",
    ConfigurationSaving = { Enabled = false },
    Discord = { Enabled = false },
    KeySystem = false,
})

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer

-- ============ ABA SKINS 3D ============
local Tab = Window:CreateTab("Skins 3D", 4483362458)

-- Funções
local function EquiparAvatarPorID(avatarID, nome)
    local args = { avatarID }
    local success, result = pcall(function()
        return ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("Wear"):InvokeServer(unpack(args))
    end)
    if success then
        Rayfield:Notify({
            Title = "Avatar Equipado",
            Content = nome .. " equipado com sucesso!",
            Duration = 5
        })
    else
        Rayfield:Notify({
            Title = "Erro",
            Content = "Falha ao equipar " .. nome,
            Duration = 5
        })
    end
end

local function EquiparPartesCorpo(partes)
    local args = { partes }
    local success, result = pcall(function()
        return ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("ChangeCharacterBody"):InvokeServer(unpack(args))
    end)
    if success then
        Rayfield:Notify({
            Title = "Avatar Resetado",
            Content = "Partes aplicadas com sucesso!",
            Duration = 5
        })
    else
        Rayfield:Notify({
            Title = "Erro",
            Content = "Falha ao aplicar partes",
            Duration = 5
        })
    end
end

-- Lista de avatares
local Avatares = {
    {124948425515124,"Gato de Manga"},
    {117098257036480,"Tung Saur"},
    {99459753608381,"Tralaleiro"},
    {123609977175226,"Monstro S.A"},
    {80468697076178,"Trenzinho"},
    {11941741105,"Dino"},
    {15742966010,"Pou Idoso"},
    {15645197933,"Pou Normal"},
    {13913442669,"Esquilo Negro"},
    {14426409309,"Gorilão"},
    {116061646255634,"Steve do K9"},
    {135484442995560,"Village Totoso"},
    {106240936270355,"Parry Noiado"},
    {82742105178956,"Bob Dono da Boca"},
    {114583627550420,"Krakudin do Pó"},
    {131077718703383,"Pato da Coca"},
    {94113768850801,"Sapo da Makonha"},
    {116926408164867,"Urso com Cólica KKJ"},
    {113388690106030,"FDP do Mine"},
    {133241040400728,"Bora dar um trago?"},
    {81758359166942,"Noiado KKJ"},
    {77013984520332,"Coco/Boxt@"},
    {71797333686800,"Coelho"},
    {73215892129281,"Hipopótamo"},
    {108557570415453,"Ratatui"},
    {71251793812515,"Galinha"},
    {92979204778377,"Peppa Pig"},
    {94944293759578,"Pinguim"},
    {87442757321244,"Sid"},
    {111436158728716,"Puga Grande"},
    {120960401202173,"SHREK AMALDIÇOADO"},
    {108052868536435,"Mosquito Grande"},
    {106596990206151,"Noob Invertido"},
    {135132836238349,"Pato(a)"},
    {18656467256,"Cachorro Chihuahua"},
    {18994959003,"Gato Sla"},
    {77506186615650,"Gato Fei"},
    {18234669337,"Bruh?"},
    {75183593514657,"Simon Amarelo"},
    {76155710249925,"Simon Azul"},
    {106583662991726,"Kaguei"},
    {128739728423758,"Skeleto que já fumou todas"},
    {17247216094,"Carro do Bob Marley KKJ"},
    {116152555682007,"Dogão Grosso"},
    {119818753007043,"Burro do Krlh"},
    {94881693032770,"Caracolzin Puto"},
    {18322091668,"Mim de Papai"},
    {90344674037297,"Zumbizin Filho da Puta"}
}

-- Lista de corpos
local Corpos = {
    {"Mini REPO",{117101023704825,125767940563838,137301494386930,87357384184710,133391239416999,111818794467824}},
    {"Mini Garanhão",{124355047456535,120507500641962,82273782655463,113625313757230,109182039511426,0}},
    {"Stick",{14731384498,14731377938,14731377894,14731377875,14731377941,14731382899}},
    {"Chunky-Bug",{15527827600,15527827578,15527831669,15527836067,15527827184,15527827599}},
    {"Cursed-Spider",{134555168634906,100269043793774,125607053187319,122504853343598,95907982259204,91289185840375}},
    {"Possessed-Horror",{122800511983371,132465361516275,125155800236527,83070163355072,102906187256945,78311422507297}}
}

-- Criar botões para cada avatar
for _, dados in ipairs(Avatares) do
    local id, nome = dados[1], dados[2]
    Tab:CreateButton({
        Name = nome,
        Callback = function()
            EquiparAvatarPorID(id, nome)
        end
    })
end

-- Criar seção para corpos
local SectionCorpos = Tab:CreateSection("Avatares de Corpo (resetam o avatar)")

-- Criar botões para cada corpo
for _, dados in ipairs(Corpos) do
    local nome, partes = dados[1], dados[2]
    Tab:CreateButton({
        Name = nome,
        Callback = function()
            EquiparPartesCorpo(partes)
        end
    })
end

-- ============ ABA INFO ============
local InfoTab = Window:CreateTab("Info", 10723415903)

InfoTab:CreateSection("Informações do Script")

InfoTab:CreateParagraph({
    Title = "TikTok thzin0x",
    Content = "Creator do script"
})

InfoTab:CreateParagraph({
    Title = "Colaborações",
    Content = "Troll, Thurr, Linux Hub"
})

InfoTab:CreateParagraph({
    Title = "Você está usando",
    Content = "SHADOWS HUB"
})

InfoTab:CreateParagraph({
    Title = "Novidades",
    Content = "Auto Kart Fling e Stephanny throw v1!"
})

InfoTab:CreateButton({
    Name = "Versão Experimental",
    Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/wx-sources/spacecomm/refs/heads/main/experimental"))()
    end
})

InfoTab:CreateSection("Rejoin")

InfoTab:CreateButton({
    Name = "Rejoin",
    Callback = function()
        local TeleportService = game:GetService("TeleportService")
        TeleportService:TeleportToPlaceInstance(game.PlaceId, game.JobId, LocalPlayer)
    end
})

-- ============ ABA TROLL ============
local TrollTab = Window:CreateTab("Scripts Trolls", 13364900349)

-- Variáveis globais para controlar os scripts
cancelExpansion = false
expansionSound = nil
expansionModel = nil
originalSky = nil

-- Player Config Section
TrollTab:CreateSection("Player Config")

local TrollDefaults = {Speed = 16, Jump = 50, Gravity = 196.2}
local function GetHumanoid()
    local char = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
    return char:FindFirstChildOfClass("Humanoid") or char:WaitForChild("Humanoid")
end

TrollTab:CreateSlider({
    Name = "Speed Player",
    Range = {16, 1000},
    Increment = 1,
    Suffix = "Speed",
    CurrentValue = TrollDefaults.Speed,
    Flag = "SpeedSlider",
    Callback = function(Value)
        local hum = GetHumanoid()
        if hum then hum.WalkSpeed = Value end
    end
})

TrollTab:CreateSlider({
    Name = "Jump Power",
    Range = {50, 1000},
    Increment = 1,
    Suffix = "Jump",
    CurrentValue = TrollDefaults.Jump,
    Flag = "JumpSlider",
    Callback = function(Value)
        local hum = GetHumanoid()
        if hum then hum.JumpPower = Value end
    end
})

TrollTab:CreateSlider({
    Name = "Gravity",
    Range = {0, 1000},
    Increment = 1,
    Suffix = "Gravity",
    CurrentValue = TrollDefaults.Gravity,
    Flag = "GravitySlider",
    Callback = function(Value)
        workspace.Gravity = Value
    end
})

TrollTab:CreateButton({
    Name = "Resetar Status",
    Callback = function()
        local hum = GetHumanoid()
        if hum then
            hum.WalkSpeed = TrollDefaults.Speed
            hum.JumpPower = TrollDefaults.Jump
        end
        workspace.Gravity = TrollDefaults.Gravity
        
        Rayfield:Notify({
            Title = "Status Resetados",
            Content = "Speed, Jump e Gravity voltaram ao normal",
            Duration = 3
        })
    end
})

local InfiniteJumpEnabled = false
local InfiniteJumpConn = nil

TrollTab:CreateToggle({
    Name = "Infinite Jump",
    CurrentValue = false,
    Flag = "InfiniteJumpToggle",
    Callback = function(Value)
        InfiniteJumpEnabled = Value
        if InfiniteJumpConn then
            InfiniteJumpConn:Disconnect()
            InfiniteJumpConn = nil
        end
        if Value then
            InfiniteJumpConn = game:GetService("UserInputService").JumpRequest:Connect(function()
                local hum = GetHumanoid()
                if hum and InfiniteJumpEnabled then
                    hum:ChangeState(Enum.HumanoidStateType.Jumping)
                end
            end)
        end
    end
})

-- Black Hole Section
TrollTab:CreateSection("Black Hole")

TrollTab:CreateButton({
    Name = "Black Hole",
    Callback = function()
        local Lighting = game:GetService("Lighting")
        local Workspace = game:GetService("Workspace")

        local angle = 1
        local radius = 10
        local blackHoleActive = false

        local function setupPlayer()
            local character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
            local humanoidRootPart = character:WaitForChild("HumanoidRootPart")

            local Folder = Instance.new("Folder", Workspace)
            local Part = Instance.new("Part", Folder)
            local Attachment1 = Instance.new("Attachment", Part)
            Part.Anchored = true
            Part.CanCollide = false
            Part.Transparency = 1

            return humanoidRootPart, Attachment1
        end

        local humanoidRootPart, Attachment1 = setupPlayer()

        if not getgenv().Network then
            getgenv().Network = {
                BaseParts = {},
                Velocity = Vector3.new(14.46262424, 14.46262424, 14.46262424)
            }

            Network.RetainPart = function(part)
                if typeof(part) == "Instance" and part:IsA("BasePart") and part:IsDescendantOf(Workspace) then
                    table.insert(Network.BaseParts, part)
                    part.CustomPhysicalProperties = PhysicalProperties.new(0, 0, 0, 0, 0)
                    part.CanCollide = false
                end
            end

            local function EnablePartControl()
                LocalPlayer.ReplicationFocus = Workspace
                RunService.Heartbeat:Connect(function()
                    sethiddenproperty(LocalPlayer, "SimulationRadius", math.huge)
                    for _, part in pairs(Network.BaseParts) do
                        if part:IsDescendantOf(Workspace) then
                            part.Velocity = Network.Velocity
                        end
                    end
                end)
            end

            EnablePartControl()
        end

        local function ForcePart(v)
            if v:IsA("Part") and not v.Anchored and not v.Parent:FindFirstChild("Humanoid") and not v.Parent:FindFirstChild("Head") and v.Name ~= "Handle" then
                for _, x in next, v:GetChildren() do
                    if x:IsA("BodyAngularVelocity") or x:IsA("BodyForce") or x:IsA("BodyGyro") or x:IsA("BodyPosition") or x:IsA("BodyThrust") or x:IsA("BodyVelocity") or x:IsA("RocketPropulsion") then
                        x:Destroy()
                    end
                end
                if v:FindFirstChild("Attachment") then
                    v:FindFirstChild("Attachment"):Destroy()
                end
                if v:FindFirstChild("AlignPosition") then
                    v:FindFirstChild("AlignPosition"):Destroy()
                end
                if v:FindFirstChild("Torque") then
                    v:FindFirstChild("Torque"):Destroy()
                end
                v.CanCollide = false
                
                local Torque = Instance.new("Torque", v)
                Torque.Torque = Vector3.new(1000000, 1000000, 1000000)
                local AlignPosition = Instance.new("AlignPosition", v)
                local Attachment2 = Instance.new("Attachment", v)
                Torque.Attachment0 = Attachment2
                AlignPosition.MaxForce = math.huge
                AlignPosition.MaxVelocity = math.huge
                AlignPosition.Responsiveness = 500
                AlignPosition.Attachment0 = Attachment2
                AlignPosition.Attachment1 = Attachment1
            end
        end

        blackHoleActive = true
        
        for _, v in next, Workspace:GetDescendants() do
            ForcePart(v)
        end

        Workspace.DescendantAdded:Connect(function(v)
            if blackHoleActive then
                ForcePart(v)
            end
        end)

        spawn(function()
            while blackHoleActive and RunService.RenderStepped:Wait() do
                angle = angle + math.rad(2)
                local offsetX = math.cos(angle) * radius
                local offsetZ = math.sin(angle) * radius
                Attachment1.WorldCFrame = humanoidRootPart.CFrame * CFrame.new(offsetX, 0, offsetZ)
            end
        end)
        
        Rayfield:Notify({
            Title = "Black Hole Ativo",
            Content = "Black Hole foi ativado!",
            Duration = 5
        })
    end
})

-- Shadows Section
TrollTab:CreateSection("Shadows")

TrollTab:CreateButton({
    Name = "Expansão SHADOWS",
    Callback = function()
        local TextChatService = game:GetService("TextChatService")
        local Lighting = game:GetService("Lighting")
        
        -- Reset da variável de cancelamento
        cancelExpansion = false

        -- Aviso no chat
        if TextChatService.ChatVersion == Enum.ChatVersion.TextChatService then 
            TextChatService.TextChannels.RBXGeneral:SendAsync(
                "hi\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\rServer: Expansão BY Shadows"
            )
        end

        -- Função para ativar Expansão de Domínio
        local function ativarDominio()
            local char = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
            local hrp = char:WaitForChild("HumanoidRootPart")

            local dominio = Instance.new("Model", workspace)
            dominio.Name = "InfiniteVoid"
            expansionModel = dominio

            local esfera = Instance.new("Part")
            esfera.Shape = Enum.PartType.Ball
            esfera.Size = Vector3.new(300, 300, 300)
            esfera.Position = hrp.Position
            esfera.Anchored = true
            esfera.CanCollide = false
            esfera.Material = Enum.Material.ForceField
            esfera.Transparency = 0.3
            esfera.Color = Color3.fromRGB(0, 0, 0)
            esfera.Parent = dominio

            local luz = Instance.new("PointLight", esfera)
            luz.Color = Color3.fromRGB(0, 153, 255)
            luz.Brightness = 10
            luz.Range = 300

            local ps = Instance.new("ParticleEmitter", esfera)
            ps.Texture = "rbxassetid://243660364"
            ps.Color = ColorSequence.new(Color3.fromRGB(0, 153, 255))
            ps.LightEmission = 1
            ps.Size = NumberSequence.new(3)
            ps.Transparency = NumberSequence.new(0.2)
            ps.Rate = 1000
            ps.Lifetime = NumberRange.new(2)
            ps.Speed = NumberRange.new(0)
            ps.VelocitySpread = 180

            local som = Instance.new("Sound", esfera)
            som.SoundId = "rbxassetid://1843527678"
            som.Volume = 2
            som.Looped = true
            som:Play()
            expansionSound = som

            originalSky = Lighting:FindFirstChildOfClass("Sky")
            if originalSky then
                originalSky.Parent = nil
            end

            local newSky = Instance.new("Sky", Lighting)
            newSky.SkyboxBk = "rbxassetid://159454299"
            newSky.SkyboxDn = "rbxassetid://159454296"
            newSky.SkyboxFt = "rbxassetid://159454293"
            newSky.SkyboxLf = "rbxassetid://159454286"
            newSky.SkyboxRt = "rbxassetid://159454300"
            newSky.SkyboxUp = "rbxassetid://159454288"
        end

        ativarDominio()
        
        Rayfield:Notify({
            Title = "Expansão SHADOWS",
            Content = "Expansão de Domínio foi ativada!",
            Duration = 5
        })
    end
})

TrollTab:CreateButton({
    Name = "SHADOWS PAROU",
    Callback = function()
        cancelExpansion = true

        if expansionSound then
            expansionSound:Stop()
            expansionSound:Destroy()
            expansionSound = nil
        end

        if expansionModel and expansionModel.Parent then
            expansionModel:Destroy()
            expansionModel = nil
        end

        local Lighting = game:GetService("Lighting")
        local currentSky = Lighting:FindFirstChildOfClass("Sky")
        if currentSky then currentSky:Destroy() end

        if originalSky then
            originalSky.Parent = Lighting
            originalSky = nil
        end

        local TextChatService = game:GetService("TextChatService")
        if TextChatService.ChatVersion == Enum.ChatVersion.TextChatService then
            TextChatService.TextChannels.RBXGeneral:SendAsync("[SHADOWS PAROU]")
        end
        
        Rayfield:Notify({
            Title = "SHADOWS Parado",
            Content = "Expansão foi cancelada!",
            Duration = 3
        })
    end
})

-- Avatar Effects Section
TrollTab:CreateSection("Avatar Effects")

TrollTab:CreateButton({
    Name = "Ficar Invisível",
    Callback = function()
        local args = {
            [1] = {
                [1] = 102344834840946,
                [2] = 70400527171038,
                [3] = 0,
                [4] = 0,
                [5] = 0,
                [6] = 0
            }
        }

        ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("ChangeCharacterBody"):InvokeServer(unpack(args))
        ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("Wear"):InvokeServer(111858803548721)
        
        Rayfield:Notify({
            Title = "Invisibilidade",
            Content = "Você ficou invisível!",
            Duration = 3
        })
    end
})

-- RGB Character
local colors = { "Bright red", "Lime green", "Bright blue", "Bright yellow", "Bright cyan", "Hot pink", "Royal purple" }
local rgbEnabled = false

local function changeColor(color)
    local args = { color }
    ReplicatedStorage:WaitForChild("Remotes"):WaitForChild("ChangeBodyColor"):FireServer(unpack(args))
end

local function toggleRGBCharacter(enabled)
    rgbEnabled = enabled
    if rgbEnabled then
        spawn(function()
            while rgbEnabled do
                for _, color in ipairs(colors) do
                    if not rgbEnabled then return end
                    changeColor(color)
                    wait(0.5)
                end
            end
        end)
    end 
end

TrollTab:CreateToggle({
    Name = "RGB Character",
    CurrentValue = false,
    Flag = "RGBCharacterToggle",
    Callback = function(Value)
        toggleRGBCharacter(Value)
    end
})

-- RGB Hair
local hairColors = {
    Color3.new(1, 1, 0), Color3.new(0, 0, 1), Color3.new(1, 0, 1), Color3.new(1, 1, 1),
    Color3.new(0, 1, 0), Color3.new(0.5, 0, 1), Color3.new(1, 0.647, 0), Color3.new(0, 1, 1)
}
local hairRgbActive = false

local function changeHairColor()
    local i = 1
    spawn(function()
        while hairRgbActive do
            if not hairRgbActive then break end
            local args = { [1] = "ChangeHairColor2", [2] = hairColors[i] }
            ReplicatedStorage:WaitForChild("RE"):WaitForChild("1Max1y"):FireServer(unpack(args))
            wait(0.1)
            i = i % #hairColors + 1
        end
    end)
end

TrollTab:CreateToggle({
    Name = "Cabelo RGB",
    CurrentValue = false,
    Flag = "RGBHairToggle",
    Callback = function(Value)
        hairRgbActive = Value
        if hairRgbActive then
            changeHairColor()
        end
    end
})

-- Troll Player Section
local PlayerSection = TrollTab:CreateSection("Troll Player")

-- Variables for player targeting
local selectedPlayerName = nil
local methodKill = "Bus"

-- Função para obter lista de jogadores
local function getPlayerList()
    local players = Players:GetPlayers()
    local playerNames = {}
    for _, player in ipairs(players) do
        if player ~= LocalPlayer then
            table.insert(playerNames, player.Name)
        end
    end
    return playerNames
end

-- Função shutdown
local function playerCorrupt()
    local targetPlayer = Players:FindFirstChild(getgenv().Target)
    if not targetPlayer then
        warn("Erro: Nenhum jogador alvo selecionado")
        return
    end
    if not targetPlayer.Character or not targetPlayer.Character:FindFirstChild("HumanoidRootPart") then
        warn("Erro: Jogador alvo sem personagem ou HumanoidRootPart")
        return
    end

    local args = { [1] = "ClearAllTools" }
    ReplicatedStorage.RE["1Clea1rTool1s"]:FireServer(unpack(args))
    local args = { [1] = "PickingTools", [2] = "Couch" }
    ReplicatedStorage.RE:FindFirstChild("1Too1l"):InvokeServer(unpack(args))

    local couch = LocalPlayer.Backpack:WaitForChild("Couch", 2)
    if not couch then
        warn("Erro: Sofá não encontrado no Backpack")
        return
    end

    couch.Name = "Chaos.Couch"
    local seat1 = couch:FindFirstChild("Seat1")
    local seat2 = couch:FindFirstChild("Seat2")
    local handle = couch:FindFirstChild("Handle")
    if seat1 and seat2 and handle then
        seat1.Disabled = true
        seat2.Disabled = true
        handle.Name = "Handle "
    else
        warn("Erro: Componentes do sofá não encontrados")
        return
    end
    couch.Parent = LocalPlayer.Character

    local tet = Instance.new("BodyVelocity", seat1)
    tet.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
    tet.P = 1250
    tet.Velocity = Vector3.new(0, 0, 0)
    tet.Name = "#mOVOOEPF$#@F$#GERE..>V<<<<EW<V<<W"

    repeat
        for m = 1, 35 do
            local pos = { x = 0, y = 0, z = 0 }
            local tRoot = targetPlayer.Character and targetPlayer.Character.HumanoidRootPart
            if not tRoot then break end
            pos.x = tRoot.Position.X + (tRoot.Velocity.X / 2)
            pos.y = tRoot.Position.Y + (tRoot.Velocity.Y / 2)
            pos.z = tRoot.Position.Z + (tRoot.Velocity.Z / 2)
            seat1.CFrame = CFrame.new(Vector3.new(pos.x, pos.y, pos.z)) * CFrame.new(-2, 2, 0)
            task.wait()
        end
        tet:Destroy()
        couch.Parent = LocalPlayer.Backpack
        task.wait()
        couch:FindFirstChild("Handle ").Name = "Handle"
        task.wait(0.2)
        couch.Parent = LocalPlayer.Character
        task.wait()
        couch.Parent = LocalPlayer.Backpack
        couch.Handle.Name = "Handle "
        task.wait(0.2)
        couch.Parent = LocalPlayer.Character
        tet = Instance.new("BodyVelocity", seat1)
        tet.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
        tet.P = 1250
        tet.Velocity = Vector3.new(0, 0, 0)
        tet.Name = "#mOVOOEPF$#@F$#GERE..>V<<<<EW<V<<W"
    until targetPlayer.Character and targetPlayer.Character.Humanoid and targetPlayer.Character.Humanoid.Sit == true
    task.wait()
    couch.Parent = LocalPlayer.Backpack
    seat1.CFrame = CFrame.new(Vector3.new(0/0, 0/0, 0/0))
    seat2.CFrame.new(Vector3.new(0/0, 0/0, 0/0))
    couch.Parent = LocalPlayer.Character
    task.wait(0.1)
    couch.Parent = LocalPlayer.Backpack
    task.wait(2)
    local bv = seat1:FindFirstChild("#mOVOOEPF$#@F$#GERE..>V<<<<EW<V<<W")
    if bv then bv:Destroy() end
    ReplicatedStorage.RE["1Clea1rTool1s"]:FireServer("ClearAllTools")
end

local killDropdown = TrollTab:CreateDropdown({
    Name = "Selecionar Jogador",
    Options = getPlayerList(),
    Default = "",
    Callback = function(value)
        selectedPlayerName = value
        getgenv().Target = value
        print("Jogador selecionado: " .. tostring(value))
    end
})

TrollTab:CreateButton({
    Name = "Atualizar Player List",
    Callback = function()
        local tablePlayers = Players:GetPlayers()
        local newPlayers = {}
        if killDropdown and #tablePlayers > 0 then
            for _, player in ipairs(tablePlayers) do
                if player.Name ~= LocalPlayer.Name then
                    table.insert(newPlayers, player.Name)
                end
            end
            killDropdown:Set(newPlayers)
            print("Lista de jogadores atualizada: ", table.concat(newPlayers, ", "))
            if selectedPlayerName and not Players:FindFirstChild(selectedPlayerName) then
                selectedPlayerName = nil
                getgenv().Target = nil
                killDropdown:SetValue("")
                print("Seleção resetada, jogador não está mais no servidor.")
            end
        else
            print("Erro: Dropdown não encontrado ou nenhum jogador disponível.")
        end
    end
})

TrollTab:CreateButton({
    Name = "Teleportar até o Player",
    Callback = function()
        if not selectedPlayerName or not Players:FindFirstChild(selectedPlayerName) then
            print("Erro: Player não selecionado ou não existe")
            return
        end
        local character = LocalPlayer.Character
        local humanoidRootPart = character and character:FindFirstChild("HumanoidRootPart")
        if not humanoidRootPart then
            warn("Erro: HumanoidRootPart do jogador local não encontrado")
            return
        end

        local targetPlayer = Players:FindFirstChild(selectedPlayerName)
        if targetPlayer and targetPlayer.Character and targetPlayer.Character:FindFirstChild("HumanoidRootPart") then
            humanoidRootPart.CFrame = targetPlayer.Character.HumanoidRootPart.CFrame
        else
            print("Erro: Player alvo não encontrado ou sem HumanoidRootPart")
        end
    end
})

TrollTab:CreateToggle({
    Name = "Spectar Player",
    CurrentValue = false,
    Flag = "SpectatePlayerToggle",
    Callback = function(value)
        local Camera = workspace.CurrentCamera

        local function UpdateCamera()
            if value then
                local targetPlayer = Players:FindFirstChild(selectedPlayerName)
                if targetPlayer and targetPlayer.Character then
                    local humanoid = targetPlayer.Character:FindFirstChild("Humanoid")
                    if humanoid then
                        Camera.CameraSubject = humanoid
                    end
                end
            else
                if LocalPlayer.Character then
                    local humanoid = LocalPlayer.Character:FindFirstChild("Humanoid")
                    if humanoid then
                        Camera.CameraSubject = humanoid
                    end
                end
            end
        end

        if value then
            if not getgenv().CameraConnection then
                getgenv().CameraConnection = RunService.Heartbeat:Connect(UpdateCamera)
            end
        else
            if getgenv().CameraConnection then
                getgenv().CameraConnection:Disconnect()
                getgenv().CameraConnection = nil
            end
            UpdateCamera()
        end
    end
})

local MethodSection = TrollTab:CreateSection("Métodos")

TrollTab:CreateDropdown({
    Name = "Selecionar Método para Matar",
    Options = {"Bus", "Couch", "Couch Sem ir até o alvo [BETA]"},
    Default = "",
    Callback = function(value)
        methodKill = value
        print("Método selecionado: " .. tostring(value))
    end
})

-- Função Kill Player com diferentes métodos
local function KillPlayerCouch()
    -- Implementação do método Couch padrão
    local character = LocalPlayer.Character
    local humanoidRootPart = character and character:FindFirstChild("HumanoidRootPart")
    if not humanoidRootPart then
        warn("Erro: HumanoidRootPart do jogador local não encontrado")
        return
    end
    
    -- Lógica do couch kill aqui
    print("Executando método Couch padrão")
end

local function KillWithCouch()
    -- Implementação do método Couch Beta
    print("Executando método Couch Beta")
end

TrollTab:CreateButton({
    Name = "Matar Player",
    Callback = function()
        if not selectedPlayerName or not Players:FindFirstChild(selectedPlayerName) then
            print("Erro: Player não selecionado ou não existe")
            return
        end
        if methodKill == "Couch" then
            KillPlayerCouch()
        elseif methodKill == "Couch Sem ir até o alvo [BETA]" then
            KillWithCouch()
        else
            -- Método de ônibus
            local character = LocalPlayer.Character
            local humanoidRootPart = character and character:FindFirstChild("HumanoidRootPart")
            if not humanoidRootPart then
                warn("Erro: HumanoidRootPart do jogador local não encontrado")
                return
            end

            local originalPosition = humanoidRootPart.CFrame

            local function GetBus()
                local vehicles = game.Workspace:FindFirstChild("Vehicles")
                if vehicles then
                    return vehicles:FindFirstChild(LocalPlayer.Name .. "Car")
                end
                return nil
            end

            local bus = GetBus()

            if not bus then
                humanoidRootPart.CFrame = CFrame.new(1118.81, 75.998, -1138.61)
                task.wait(0.5)
                local remoteEvent = ReplicatedStorage:FindFirstChild("RE")
                if remoteEvent and remoteEvent:FindFirstChild("1Ca1r") then
                    remoteEvent["1Ca1r"]:FireServer("PickingCar", "SchoolBus")
                end
                task.wait(1)
                bus = GetBus()
            end

            if bus then
                local seat = bus:FindFirstChild("Body") and bus.Body:FindFirstChild("VehicleSeat")
                if seat and character:FindFirstChildOfClass("Humanoid") and not character.Humanoid.Sit then
                    repeat
                        humanoidRootPart.CFrame = seat.CFrame * CFrame.new(0, 2, 0)
                        task.wait()
                    until character.Humanoid.Sit or not bus.Parent
                    if character.Humanoid.Sit or not bus.Parent then
                        for k, v in pairs(bus.Body:GetChildren()) do
                            if v:IsA("Seat") then
                                v.CanTouch = false
                            end
                        end
                    end
                end
            end

            local function TrackPlayer()
                while true do
                    if selectedPlayerName then
                        local targetPlayer = Players:FindFirstChild(selectedPlayerName)
                        if targetPlayer and targetPlayer.Character and targetPlayer.Character:FindFirstChild("HumanoidRootPart") then
                            local targetHumanoid = targetPlayer.Character:FindFirstChildOfClass("Humanoid")
                            if targetHumanoid and targetHumanoid.Sit then
                                if character.Humanoid then
                                    bus:SetPrimaryPartCFrame(CFrame.new(Vector3.new(9999, -450, 9999)))
                                    print("Jogador sentou, levando ônibus para o void!")
                                    task.wait(0.2)

                                    local function simulateJump()
                                        local humanoid = character and character:FindFirstChildWhichIsA("Humanoid")
                                        if humanoid then
                                            humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
                                        end
                                    end

                                    simulateJump()
                                    print("Simulando pulo!")
                                    task.wait(0.5)
                                    humanoidRootPart.CFrame = originalPosition
                                    print("Player voltou para a posição inicial.")
                                end
                                break
                            else
                                local targetRoot = targetPlayer.Character.HumanoidRootPart
                                local time = tick() * 35
                                local lateralOffset = math.sin(time) * 4
                                local frontBackOffset = math.cos(time) * 20
                                bus:SetPrimaryPartCFrame(targetRoot.CFrame * CFrame.new(lateralOffset, 0, frontBackOffset))
                            end
                        end
                    end
                    RunService.RenderStepped:Wait()
                end
            end

            spawn(TrackPlayer)
        end
    end
})

TrollTab:CreateButton({
    Name = "Shutdown Player",
    Callback = function()
        playerCorrupt()
    end
})

-- Função Bring Player (similar ao kill mas traz o jogador)
local function BringPlayerLLL()
    print("Executando Bring Player - Couch padrão")
end

local function BringWithCouch()
    print("Executando Bring Player - Couch Beta")
end

TrollTab:CreateButton({
    Name = "Puxar Player",
    Callback = function()
        if not selectedPlayerName or not Players:FindFirstChild(selectedPlayerName) then
            print("Erro: Player não selecionado ou não existe")
            return
        end
        if methodKill == "Couch" then
            BringPlayerLLL()
        elseif methodKill == "Couch Sem ir até o alvo [BETA]" then
            BringWithCouch()
        else
            -- Método de ônibus para bring
            local character = LocalPlayer.Character
            local humanoidRootPart = character and character:FindFirstChild("HumanoidRootPart")
            if not humanoidRootPart then
                warn("Erro: HumanoidRootPart do jogador local não encontrado")
                return
            end

            local originalPosition = humanoidRootPart.CFrame

            local function GetBus()
                local vehicles = game.Workspace:FindFirstChild("Vehicles")
                if vehicles then
                    return vehicles:FindFirstChild(LocalPlayer.Name .. "Car")
                end
                return nil
            end

            local bus = GetBus()

            if not bus then
                humanoidRootPart.CFrame = CFrame.new(1118.81, 75.998, -1138.61)
                task.wait(0.5)
                local remoteEvent = ReplicatedStorage:FindFirstChild("RE")
                if remoteEvent and remoteEvent:FindFirstChild("1Ca1r") then
                    remoteEvent["1Ca1r"]:FireServer("PickingCar", "SchoolBus")
                end
                task.wait(1)
                bus = GetBus()
            end

            if bus then
                local seat = bus:FindFirstChild("Body") and bus.Body:FindFirstChild("VehicleSeat")
                if seat and character:FindFirstChildOfClass("Humanoid") and not character.Humanoid.Sit then
                    repeat
                        humanoidRootPart.CFrame = seat.CFrame * CFrame.new(0, 2, 0)
                        task.wait()
                    until character.Humanoid.Sit or not bus.Parent
                end
            end

            local function TrackPlayer()
                while true do
                    if selectedPlayerName then
                        local targetPlayer = Players:FindFirstChild(selectedPlayerName)
                        if targetPlayer and targetPlayer.Character and targetPlayer.Character:FindFirstChild("HumanoidRootPart") then
                            local targetHumanoid = targetPlayer.Character:FindFirstChildOfClass("Humanoid")
                            if targetHumanoid and targetHumanoid.Sit then
                                if character.Humanoid then
                                    bus:SetPrimaryPartCFrame(originalPosition)
                                    task.wait(0.7)
                                    local args = { [1] = "DeleteAllVehicles" }
                                    ReplicatedStorage.RE:FindFirstChild("1Ca1r"):FireServer(unpack(args))
                                end
                                break
                            else
                                local targetRoot = targetPlayer.Character.HumanoidRootPart
                                local time = tick() * 35
                                local lateralOffset = math.sin(time) * 4
                                local frontBackOffset = math.cos(time) * 20
                                bus:SetPrimaryPartCFrame(targetRoot.CFrame * CFrame.new(lateralOffset, 0, frontBackOffset))
                            end
                        end
                    end
                    RunService.RenderStepped:Wait()
                end
            end

            spawn(TrackPlayer)
        end
    end
})

-- House Ban Kill Function
local function houseBanKill()
    if not selectedPlayerName then
        print("Nenhum jogador selecionado!")
        return
    end

    local Player = game.Players.LocalPlayer
    local Backpack = Player.Backpack
    local Character = Player.Character
    local Humanoid = Character:FindFirstChildOfClass("Humanoid")
    local RootPart = Character:FindFirstChild("HumanoidRootPart")
    local Houses = game.Workspace:FindFirstChild("001_Lots")
    local OldPos = RootPart.CFrame
    local Angles = 0
    local Vehicles = workspace.Vehicles
    local Pos

    function Check()
        if Player and Character and Humanoid and RootPart and Vehicles then
            return true
        else
            return false
        end
    end

    local selectedPlayer = game.Players:FindFirstChild(selectedPlayerName)
    if selectedPlayer and selectedPlayer.Character then
        if Check() then
            local House = Houses:FindFirstChild(Player.Name .. "House")
            if not House then
                local EHouse
                local availableHouses = {}
                
                -- Coletar todas as casas disponíveis ("For Sale")
                for _, Lot in pairs(Houses:GetChildren()) do
                    if Lot.Name == "For Sale" then
                        for _, num in pairs(Lot:GetDescendants()) do
                            if num:IsA("NumberValue") and num.Name == "Number" and num.Value < 25 and num.Value > 10 then
                                table.insert(availableHouses, {Lot = Lot, Number = num.Value})
                                break
                            end
                        end
                    end
                end

                -- Escolher uma casa aleatória da lista
                if #availableHouses > 0 then
                    local randomHouse = availableHouses[math.random(1, #availableHouses)]
                    EHouse = randomHouse.Lot
                    local houseNumber = randomHouse.Number

                    -- Teleportar para o BuyDetector e clicar
                    local BuyDetector = EHouse:FindFirstChild("BuyHouse")
                    Pos = BuyDetector.Position
                    if BuyDetector and BuyDetector:IsA("BasePart") then
                        RootPart.CFrame = BuyDetector.CFrame + Vector3.new(0, -6, 0)
                        task.wait(0.5)
                        local ClickDetector = BuyDetector:FindFirstChild("ClickDetector")
                        if ClickDetector then
                            fireclickdetector(ClickDetector)
                        end
                    end

                    -- Disparar o novo remote event para construir a casa
                    task.wait(0.5)
                    local args = {
                        houseNumber, -- Número da casa aleatória
                        "056_House" -- Tipo da casa
                    }
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Lot:BuildProperty"):FireServer(unpack(args))
                else
                    print("Nenhuma casa disponível para compra!")
                    return
                end
            end

            task.wait(0.5)
            local PreHouse = Houses:FindFirstChild(Player.Name .. "House")
            if PreHouse then
                task.wait(0.5)
                local Number
                for i, x in pairs(PreHouse:GetDescendants()) do
                    if x.Name == "Number" and x:IsA("NumberValue") then
                        Number = x
                    end
                end
                task.wait(0.5)
                game:GetService("ReplicatedStorage").RE:FindFirstChild("1Gettin1gHous1e"):FireServer("PickingCustomHouse", "049_House", Number.Value)
            end

            task.wait(0.5)
            local PCar = Vehicles:FindFirstChild(Player.Name .. "Car")
            if not PCar then
                if Check() then
                    RootPart.CFrame = CFrame.new(1118.81, 75.998, -1138.61)
                    task.wait(0.5)
                    game:GetService("ReplicatedStorage").RE:FindFirstChild("1Ca1r"):FireServer("PickingCar", "SchoolBus")
                    task.wait(0.5)
                    local PCar = Vehicles:FindFirstChild(Player.Name .. "Car")
                    task.wait(0.5)
                    local Seat = PCar:FindFirstChild("Body") and PCar.Body:FindFirstChild("VehicleSeat")
                    if Seat then
                        repeat
                            task.wait()
                            RootPart.CFrame = Seat.CFrame * CFrame.new(0, math.random(-1, 1), 0)
                        until Humanoid.Sit
                    end
                end
            end

            task.wait(0.5)
            local PCar = Vehicles:FindFirstChild(Player.Name .. "Car")
            if PCar then
                if not Humanoid.Sit then
                    local Seat = PCar:FindFirstChild("Body") and PCar.Body:FindFirstChild("VehicleSeat")
                    if Seat then
                        repeat
                            task.wait()
                            RootPart.CFrame = Seat.CFrame * CFrame.new(0, math.random(-1, 1), 0)
                        until Humanoid.Sit
                    end
                end

                local Target = selectedPlayer
                local TargetC = Target.Character
                local TargetH = TargetC:FindFirstChildOfClass("Humanoid")
                local TargetRP = TargetC:FindFirstChild("HumanoidRootPart")
                if TargetC and TargetH and TargetRP then
                    if not TargetH.Sit then
                        while not TargetH.Sit do
                            task.wait()
                            local Fling = function(alvo, pos, angulo)
                                PCar:SetPrimaryPartCFrame(CFrame.new(alvo.Position) * pos * angulo)
                            end
                            Angles = Angles + 100
                            Fling(TargetRP, CFrame.new(0, 1.5, 0) + TargetH.MoveDirection * TargetRP.Velocity.Magnitude / 1.10, CFrame.Angles(math.rad(Angles), 0, 0))
                            Fling(TargetRP, CFrame.new(0, -1.5, 0) + TargetH.MoveDirection * TargetRP.Velocity.Magnitude / 1.10, CFrame.Angles(math.rad(Angles), 0, 0))
                            Fling(TargetRP, CFrame.new(2.25, 1.5, -2.25) + TargetH.MoveDirection * TargetRP.Velocity.Magnitude / 1.10, CFrame.Angles(math.rad(Angles), 0, 0))
                            Fling(TargetRP, CFrame.new(-2.25, -1.5, 2.25) + TargetH.MoveDirection * TargetRP.Velocity.Magnitude / 1.10, CFrame.Angles(math.rad(Angles), 0, 0))
                            Fling(TargetRP, CFrame.new(0, 1.5, 0) + TargetH.MoveDirection * TargetRP.Velocity.Magnitude / 1.10, CFrame.Angles(math.rad(Angles), 0, 0))
                            Fling(TargetRP, CFrame.new(0, -1.5, 0) + TargetH.MoveDirection * TargetRP.Velocity.Magnitude / 1.10, CFrame.Angles(math.rad(Angles), 0, 0))
                        end
                        task.wait(0.2)
                        local House = Houses:FindFirstChild(Player.Name .. "House")
                        PCar:SetPrimaryPartCFrame(CFrame.new(House.HouseSpawnPosition.Position))
                        task.wait(0.2)
                        local pedro = Region3.new(game.Players.LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(30, 30, 30), game.Players.LocalPlayer.Character.HumanoidRootPart.Position + Vector3.new(30, 30, 30))
                        local a = workspace:FindPartsInRegion3(pedro, game.Players.LocalPlayer.Character.HumanoidRootPart, math.huge)
                        for i, v in pairs(a) do
                            if v.Name == "HumanoidRootPart" then
                                local b = game:GetService("Players"):FindFirstChild(v.Parent.Name)
                                local args = {
                                    [1] = "BanPlayerFromHouse",
                                    [2] = b,
                                    [3] = v.Parent
                                }
                                game:GetService("ReplicatedStorage").RE:FindFirstChild("1Playe1rTrigge1rEven1t"):FireServer(unpack(args))
                                local args = {
                                    [1] = "DeleteAllVehicles"
                                }
                                game:GetService("ReplicatedStorage").RE:FindFirstChild("1Ca1r"):FireServer(unpack(args))
                            end
                        end
                    end
                end
            end
        end
    end
end

TrollTab:CreateButton({
    Name = "House Ban Kill",
    Callback = houseBanKill
})

-- Auto Fling System
local flingActive = false

TrollTab:CreateToggle({
    Name = "Auto Fling",
    CurrentValue = false,
    Flag = "AutoFlingToggle",
    Callback = function(state)
        flingActive = state
        if state and selectedPlayerName then
            local target = Players:FindFirstChild(selectedPlayerName)
            if not target or not target.Character then return end
            local root = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            local tRoot = target.Character and target.Character:FindFirstChild("HumanoidRootPart")
            if not root or not tRoot then return end
            local char = LocalPlayer.Character
            local hum = char:FindFirstChildOfClass("Humanoid")
            local original = root.CFrame

            local args = {"ClearAllTools"}
            game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Clea1rTool1s"):FireServer(unpack(args))
            task.wait(0.2)

            local args = {[1] = "PickingTools", [2] = "Couch"}
            game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l"):InvokeServer(unpack(args))
            task.wait(0.3)
            
            local tool = LocalPlayer.Backpack:FindFirstChild("Couch")
            if tool then
                tool.Parent = char
            end
            task.wait(0.2)
            game:GetService("VirtualInputManager"):SendKeyEvent(true, Enum.KeyCode.F, false, game)
            task.wait(0.25)

            workspace.FallenPartsDestroyHeight = 0/0
            local bv = Instance.new("BodyVelocity")
            bv.Name = "FlingForce"
            bv.Velocity = Vector3.new(9e8, 9e8, 9e8)
            bv.MaxForce = Vector3.new(1/0, 1/0, 1/0)
            bv.Parent = root
            hum:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
            hum.PlatformStand = false
            workspace.CurrentCamera.CameraSubject = target.Character:FindFirstChild("Head") or tRoot or hum

            task.spawn(function()
                local angle = 0
                local parts = {root}
                while flingActive and target and target.Character and target.Character:FindFirstChildOfClass("Humanoid") do
                    local tHum = target.Character:FindFirstChildOfClass("Humanoid")
                    if tHum.Sit then break end
                    angle += 50

                    for _, part in ipairs(parts) do
                        local pos_x = target.Character.HumanoidRootPart.Position.X
                        local pos_y = target.Character.HumanoidRootPart.Position.Y
                        local pos_z = target.Character.HumanoidRootPart.Position.Z
                        pos_x = pos_x + (target.Character.HumanoidRootPart.Velocity.X / 1.5)
                        pos_y = pos_y + (target.Character.HumanoidRootPart.Velocity.Y / 1.5)
                        pos_z = pos_z + (target.Character.HumanoidRootPart.Velocity.Z / 1.5)
                        root.CFrame = CFrame.new(pos_x, pos_y, pos_z) * CFrame.Angles(math.rad(angle), 0, 0)
                    end

                    root.Velocity = Vector3.new(9e8, 9e8, 9e8)
                    root.RotVelocity = Vector3.new(9e8, 9e8, 9e8)
                    task.wait()
                end
                flingActive = false
                bv:Destroy()
                hum:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
                hum.PlatformStand = false
                root.CFrame = original
                workspace.CurrentCamera.CameraSubject = hum
                for _, p in pairs(char:GetDescendants()) do
                    if p:IsA("BasePart") then
                        p.Velocity = Vector3.zero
                        p.RotVelocity = Vector3.zero
                    end
                end
                hum:UnequipTools()
            end)
        end
    end
})

-- Fling Ball Function
local function FlingBall(target)
    local players = game:GetService("Players")
    local player = players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")
    local hrp = character:WaitForChild("HumanoidRootPart")
    local backpack = player:WaitForChild("Backpack")
    local ServerBalls = workspace.WorkspaceCom:WaitForChild("001_SoccerBalls")

    local function GetBall()
        if not backpack:FindFirstChild("SoccerBall") then
            game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l"):InvokeServer("PickingTools", "SoccerBall")
        end
        repeat task.wait() until backpack:FindFirstChild("SoccerBall")
        backpack.SoccerBall.Parent = character
        repeat task.wait() until ServerBalls:FindFirstChild("Soccer" .. player.Name)
        character.SoccerBall.Parent = backpack
        return ServerBalls:FindFirstChild("Soccer" .. player.Name)
    end

    local Ball = ServerBalls:FindFirstChild("Soccer" .. player.Name) or GetBall()
    Ball.CanCollide = false
    Ball.Massless = true
    Ball.CustomPhysicalProperties = PhysicalProperties.new(0.0001, 0, 0)

    if target ~= player then
        local tchar = target.Character
        if tchar and tchar:FindFirstChild("HumanoidRootPart") and tchar:FindFirstChild("Humanoid") then
            local troot = tchar.HumanoidRootPart
            local thum = tchar.Humanoid

            if Ball:FindFirstChildWhichIsA("BodyVelocity") then
                Ball:FindFirstChildWhichIsA("BodyVelocity"):Destroy()
            end

            local bv = Instance.new("BodyVelocity")
            bv.Name = "FlingPower"
            bv.Velocity = Vector3.new(9e8, 9e8, 9e8)
            bv.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
            bv.P = 9e900
            bv.Parent = Ball

            workspace.CurrentCamera.CameraSubject = thum
            local StartTime = os.time()
            repeat
                if troot.Velocity.Magnitude > 0 then
                    local pos_x = troot.Position.X + (troot.Velocity.X / 1.5)
                    local pos_y = troot.Position.Y + (troot.Velocity.Y / 1.5)
                    local pos_z = troot.Position.Z + (troot.Velocity.Z / 1.5)
                    local position = Vector3.new(pos_x, pos_y, pos_z)
                    Ball.CFrame = CFrame.new(position)
                    Ball.Orientation += Vector3.new(45, 60, 30)
                else
                    for i, v in pairs(tchar:GetChildren()) do
                        if v:IsA("BasePart") and v.CanCollide and not v.Anchored then
                            Ball.CFrame = v.CFrame
                            task.wait(1/6000)
                        end
                    end
                end
                task.wait(1/6000)
            until troot.Velocity.Magnitude > 1000 or thum.Health <= 0 or not tchar:IsDescendantOf(workspace) or target.Parent ~= players
            workspace.CurrentCamera.CameraSubject = humanoid
        end
    end
end

TrollTab:CreateButton({
    Name = "Fling Ball",
    Callback = function()
        if selectedPlayerName then
            FlingBall(game:GetService("Players")[selectedPlayerName])
        end
    end
})

-- Fling System using gun
local FlingSystem = { power = 1e16, damage = 9999999999999999999999999999998, interval = 0.02 }

local function clearTools()
    local ClearEvent = ReplicatedStorage.RE:FindFirstChild("1Clea1rTool1s")
    if ClearEvent then
        ClearEvent:FireServer("ClearAllTools")
    end
end

local function requestAssault()
    local ToolEvent = ReplicatedStorage.RE:FindFirstChild("1Too1l")
    if ToolEvent then
        ToolEvent:InvokeServer("PickingTools", "Assault")
    end
end

local function hasWeapon()
    return LocalPlayer.Backpack:FindFirstChild("Assault") or (LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Assault"))
end

local function equipWeapon()
    local weapon = LocalPlayer.Backpack:FindFirstChild("Assault")
    if weapon and LocalPlayer.Character then
        local humanoid = LocalPlayer.Character:FindFirstChild("Humanoid")
        if humanoid then
            humanoid:EquipTool(weapon)
            return true
        end
    end
    return false
end

local function getGunScript()
    if LocalPlayer.Character then
        local weapon = LocalPlayer.Character:FindFirstChild("Assault") or LocalPlayer.Backpack:FindFirstChild("Assault")
        if weapon then
            return weapon:FindFirstChild("GunScript_Local")
        end
    end
    return nil
end

local function executeShot(targetPart)
    local gunScript = getGunScript()
    local FireEvent = ReplicatedStorage.RE:FindFirstChild("1Gu1n")
    if not gunScript or not targetPart or not FireEvent then return end

    local muzzle = gunScript:FindFirstChild("MuzzleEffect")
    local hit = gunScript:FindFirstChild("HitEffect")
    if not muzzle or not hit then return end

    local args = {
        targetPart,
        targetPart,
        Vector3.new(FlingSystem.power, FlingSystem.power, FlingSystem.power),
        targetPart.Position,
        muzzle,
        hit,
        0,
        0,
        { false },
        {
            FlingSystem.damage,
            Vector3.new(5000, 5000, 5000),
            BrickColor.new(29),
            0.25,
            Enum.Material.SmoothPlastic,
            0.25
        },
        true,
        false
    }

    FireEvent:FireServer(unpack(args))
end

local function getSelectedTarget()
    if not selectedPlayerName then return nil end
    local player = Players:FindFirstChild(selectedPlayerName)
    if player and player.Character then
        local humanoid = player.Character:FindFirstChild("Humanoid")
        local rootPart = player.Character:FindFirstChild("HumanoidRootPart")
        if humanoid and humanoid.Health > 0 and rootPart then
            return { player = player, part = rootPart }
        end
    end
    return nil
end

local function flingTarget()
    local target = getSelectedTarget()
    if not target then return end

    executeShot(target.part)

    local char = target.player.Character
    if not char then return end

    local head = char:FindFirstChild("Head")
    if head then executeShot(head) end

    local torso = char:FindFirstChild("Torso") or char:FindFirstChild("UpperTorso")
    if torso then executeShot(torso) end
end

local function maintainWeapon()
    if not hasWeapon() then
        clearTools()
        task.wait(0.1)
        requestAssault()
        task.wait(0.2)

        local attempts = 0
        while not hasWeapon() and attempts < 20 do
            task.wait(0.1)
            attempts = attempts + 1
        end

        if hasWeapon() then
            equipWeapon()
        end
    end
end

-- Função Stephannythrow editada para permitir parar
function Stephannythrow()
    getgenv().StopStephanny = false  -- Reset ao iniciar
    maintainWeapon()
    task.spawn(function()
        while not getgenv().StopStephanny do
            maintainWeapon()
            if hasWeapon() and getGunScript() then
                pcall(flingTarget) -- evita erro se target desaparecer no meio do loop
            end
            task.wait(FlingSystem.interval)
        end
    end)
end

TrollTab:CreateButton({
    Name = "Bug Player",
    Callback = function()
        Stephannythrow()
    end
})

TrollTab:CreateButton({
    Name = "Parar o Bug",
    Callback = function()
        getgenv().StopStephanny = true
    end
})

-- Fling Boat Section
local FlingBoatSection = TrollTab:CreateSection("Fling Boat")

TrollTab:CreateButton({
    Name = "Fling - Boat",
    Callback = function()
        if not selectedPlayerName or not game.Players:FindFirstChild(selectedPlayerName) then
            warn("Nenhum jogador selecionado ou não existe")
            return
        end

        local Player = game.Players.LocalPlayer
        local Character = Player.Character
        local Humanoid = Character and Character:FindFirstChildOfClass("Humanoid")
        local RootPart = Character and Character:FindFirstChild("HumanoidRootPart")
        local Vehicles = game.Workspace:FindFirstChild("Vehicles")

        if not Humanoid or not RootPart then
            warn("Humanoid ou RootPart inválido")
            return
        end

        local function spawnBoat()
            RootPart.CFrame = CFrame.new(1754, -2, 58)
            task.wait(0.5)
            game:GetService("ReplicatedStorage").RE:FindFirstChild("1Ca1r"):FireServer("PickingBoat", "MilitaryBoatFree")
            task.wait(1)
            return Vehicles:FindFirstChild(Player.Name.."Car")
        end

        local PCar = Vehicles:FindFirstChild(Player.Name.."Car") or spawnBoat()
        if not PCar then
            warn("Falha ao spawnar o barco")
            return
        end

        local Seat = PCar:FindFirstChild("Body") and PCar.Body:FindFirstChild("VehicleSeat")
        if not Seat then
            warn("Assento não encontrado")
            return
        end

        repeat 
            task.wait(0.1)
            RootPart.CFrame = Seat.CFrame * CFrame.new(0, 1, 0)
        until Humanoid.SeatPart == Seat

        print("Barco spawnado!")

        local TargetPlayer = game.Players:FindFirstChild(selectedPlayerName)
        if not TargetPlayer or not TargetPlayer.Character then
            warn("Jogador não encontrado")
            return
        end

        local TargetC = TargetPlayer.Character
        local TargetH = TargetC:FindFirstChildOfClass("Humanoid")
        local TargetRP = TargetC:FindFirstChild("HumanoidRootPart")

        if not TargetRP or not TargetH then
            warn("Humanoid ou RootPart do alvo não encontrado")
            return
        end

        local Spin = Instance.new("BodyAngularVelocity")
        Spin.Name = "Spinning"
        Spin.Parent = PCar.PrimaryPart
        Spin.MaxTorque = Vector3.new(0, math.huge, 0)
        Spin.AngularVelocity = Vector3.new(0, 369, 0) 

        print("Fling ativo!")

        local function moveCar(TargetRP, offset)
            if PCar and PCar.PrimaryPart then
                PCar:SetPrimaryPartCFrame(CFrame.new(TargetRP.Position + offset))
            end
        end

        task.spawn(function()
            while PCar and PCar.Parent and TargetRP and TargetRP.Parent do
                task.wait(0.01) 
                
                moveCar(TargetRP, Vector3.new(0, 1, 0))  
                moveCar(TargetRP, Vector3.new(0, -2.25, 5))  
                moveCar(TargetRP, Vector3.new(0, 2.25, 0.25))  
                moveCar(TargetRP, Vector3.new(-2.25, -1.5, 2.25))  
                moveCar(TargetRP, Vector3.new(0, 1.5, 0))  
                moveCar(TargetRP, Vector3.new(0, -1.5, 0))  

                if PCar and PCar.PrimaryPart then
                    local Rotation = CFrame.Angles(
                        math.rad(math.random(-369, 369)),  
                        math.rad(math.random(-369, 369)), 
                        math.rad(math.random(-369, 369))
                    )
                    PCar:SetPrimaryPartCFrame(CFrame.new(TargetRP.Position + Vector3.new(0, 1.5, 0)) * Rotation)
                end
            end

            if Spin and Spin.Parent then
                Spin:Destroy()
                print("Fling desativado")
            end
        end)
    end
})

TrollTab:CreateButton({
    Name = "Desligar Fling - Boat",
    Callback = function()
        local Player = game.Players.LocalPlayer
        local Character = Player.Character
        local RootPart = Character and Character:FindFirstChild("HumanoidRootPart")
        local Humanoid = Character and Character:FindFirstChildOfClass("Humanoid")
        local Vehicles = game.Workspace:FindFirstChild("Vehicles")

        if not RootPart or not Humanoid then
            warn("Nenhum RootPart ou Humanoid encontrado!")
            return
        end

        Humanoid.PlatformStand = true
        print("Jogador paralisado para reduzir efeitos do spin.")

        for _, obj in pairs(RootPart:GetChildren()) do
            if obj:IsA("BodyAngularVelocity") or obj:IsA("BodyVelocity") then
                obj:Destroy()
            end
        end
        print("Spin e forças removidas do jogador.")

        game:GetService("ReplicatedStorage").RE:FindFirstChild("1Ca1r"):FireServer("DeleteAllVehicles")
        task.wait(0.5)

        local PCar = Vehicles and Vehicles:FindFirstChild(Player.Name.."Car")
        if PCar and PCar.PrimaryPart then
            for _, obj in pairs(PCar.PrimaryPart:GetChildren()) do
                if obj:IsA("BodyAngularVelocity") or obj:IsA("BodyVelocity") then
                    obj:Destroy()
                end
            end
            print("Spin removido do barco.")
        end

        task.wait(1)

        local safePos = Vector3.new(0, 1000, 0)
        local bp = Instance.new("BodyPosition", RootPart)
        bp.Position = safePos
        bp.MaxForce = Vector3.new(math.huge, math.huge, math.huge)

        local bg = Instance.new("BodyGyro", RootPart)
        bg.CFrame = RootPart.CFrame
        bg.MaxTorque = Vector3.new(math.huge, math.huge, math.huge)

        print("Jogador está preso na coordenada segura.")

        task.wait(3)

        bp:Destroy()
        bg:Destroy()
        Humanoid.PlatformStand = false

        print("Jogador liberado, seguro na posição.")
    end
})

-- Click and Auto Kill Methods Section
local ClickKillSection = TrollTab:CreateSection("Click and Auto Kill Methods")

-- Auto Kart Fling
local function AutoKartFling()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local backpack = player:WaitForChild("Backpack")
    local root = character:WaitForChild("HumanoidRootPart")

    -- === Spin a 500 ===
    local bav = Instance.new("BodyAngularVelocity")
    bav.AngularVelocity = Vector3.new(0, 500, 0)
    bav.MaxTorque = Vector3.new(0, math.huge, 0)
    bav.P = 1000
    bav.Parent = root

    -- === Complemento PickingTools e ShoppingCart ===
    local args = {"PickingTools", "ShoppingCart"}
    game:GetService("ReplicatedStorage"):WaitForChild("RE"):WaitForChild("1Too1l"):InvokeServer(unpack(args))

    -- === Função para equipar ferramentas com 'cart' no nome ===
    local function equipCartTools()
        for _, tool in pairs(backpack:GetChildren()) do
            if tool:IsA("Tool") and string.find(string.lower(tool.Name), "cart") then
                player.Character.Humanoid:EquipTool(tool)
            end
        end
    end

    -- Equipar inicialmente
    equipCartTools()

    -- Monitorar o backpack para novas ferramentas
    backpack.ChildAdded:Connect(function(child)
        if child:IsA("Tool") and string.find(string.lower(child.Name), "cart") then
            player.Character.Humanoid:EquipTool(child)
        end
    end)
end

TrollTab:CreateButton({
    Name = "[🛒🔥] Auto Kart Fling",
    Callback = function()
        AutoKartFling()
    end
})

-- Click Fling Functions
TrollTab:CreateButton({
    Name = "Click Fling Portas [Beta]",
    Callback = function()
        local Players = game:GetService("Players")
        local Workspace = game:GetService("Workspace")
        local RunService = game:GetService("RunService")
        local UserInputService = game:GetService("UserInputService")

        local LocalPlayer = Players.LocalPlayer
        local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
        local HRP = Character:WaitForChild("HumanoidRootPart")

        -- Alvo invisível (BlackHole)
        local BlackHole = Instance.new("Part")
        BlackHole.Size = Vector3.new(100000, 100000, 100000)
        BlackHole.Transparency = 1
        BlackHole.Anchored = true
        BlackHole.CanCollide = false
        BlackHole.Name = "BlackHoleTarget"
        BlackHole.Parent = Workspace

        -- Attachment base no BlackHole
        local baseAttachment = Instance.new("Attachment")
        baseAttachment.Name = "Luscaa_BlackHoleAttachment"
        baseAttachment.Parent = BlackHole

        -- Atualiza posição do BlackHole
        RunService.Heartbeat:Connect(function()
            BlackHole.CFrame = HRP.CFrame
        end)

        -- Lista de portas controladas
        local ControlledDoors = {}

        -- Prepara uma porta para ser controlada
        local function SetupPart(part)
            if not part:IsA("BasePart") or part.Anchored or not string.find(part.Name, "Door") then return end
            if part:FindFirstChild("Luscaa_Attached") then return end

            part.CanCollide = false

            for _, obj in ipairs(part:GetChildren()) do
                if obj:IsA("AlignPosition") or obj:IsA("Torque") or obj:IsA("Attachment") then
                    obj:Destroy()
                end
            end

            local marker = Instance.new("BoolValue", part)
            marker.Name = "Luscaa_Attached"

            local a1 = Instance.new("Attachment", part)

            local align = Instance.new("AlignPosition", part)
            align.Attachment0 = a1
            align.Attachment1 = baseAttachment
            align.MaxForce = 1e20
            align.MaxVelocity = math.huge
            align.Responsiveness = 99999

            local torque = Instance.new("Torque", part)
            torque.Attachment0 = a1
            torque.RelativeTo = Enum.ActuatorRelativeTo.World
            torque.Torque = Vector3.new(
                math.random(-10e5, 10e5) * 10000,
                math.random(-10e5, 10e5) * 10000,
                math.random(-10e5, 10e5) * 10000
            )

            table.insert(ControlledDoors, {Part = part, Align = align})
        end

        -- Detecta e prepara portas existentes
        for _, obj in ipairs(Workspace:GetDescendants()) do
            if obj:IsA("BasePart") and string.find(obj.Name, "Door") then
                SetupPart(obj)
            end
        end

        -- Novas portas no futuro
        Workspace.DescendantAdded:Connect(function(obj)
            if obj:IsA("BasePart") and string.find(obj.Name, "Door") then
                SetupPart(obj)
            end
        end)

        -- Flinga jogador com timeout e retorno
        local function FlingPlayer(player)
            local char = player.Character
            if not char then return end
            local targetHRP = char:FindFirstChild("HumanoidRootPart")
            if not targetHRP then return end

            local targetAttachment = targetHRP:FindFirstChild("SHNMAX_TargetAttachment")
            if not targetAttachment then
                targetAttachment = Instance.new("Attachment", targetHRP)
                targetAttachment.Name = "SHNMAX_TargetAttachment"
            end

            for _, data in ipairs(ControlledDoors) do
                if data.Align then
                    data.Align.Attachment1 = targetAttachment
                end
            end

            local start = tick()
            local flingDetected = false

            while tick() - start < 5 do
                if targetHRP.Velocity.Magnitude >= 20 then
                    flingDetected = true
                    break
                end
                RunService.Heartbeat:Wait()
            end

            -- Sempre retorna as portas
            for _, data in ipairs(ControlledDoors) do
                if data.Align then
                    data.Align.Attachment1 = baseAttachment
                end
            end
        end

        -- Clique (funciona no mobile)
        UserInputService.TouchTap:Connect(function(touchPositions, processed)
            if processed then return end
            local pos = touchPositions[1]
            local camera = Workspace.CurrentCamera
            local unitRay = camera:ScreenPointToRay(pos.X, pos.Y)
            local raycast = Workspace:Raycast(unitRay.Origin, unitRay.Direction * 1000)

            if raycast and raycast.Instance then
                local hit = raycast.Instance
                local player = Players:GetPlayerFromCharacter(hit:FindFirstAncestorOfClass("Model"))
                if player and player ~= LocalPlayer then
                    FlingPlayer(player)
                end
            end
        end)
    end
})

TrollTab:CreateButton({
    Name = "Click Fling Admin [Beta]",
    Callback = function()
        local Players = game:GetService("Players")
        local Workspace = game:GetService("Workspace")
        local RunService = game:GetService("RunService")
        local UserInputService = game:GetService("UserInputService")

        local LocalPlayer = Players.LocalPlayer
        local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
        local HRP = Character:WaitForChild("HumanoidRootPart")

        -- Alvo invisível (BlackHole)
        local BlackHole = Instance.new("Part")
        BlackHole.Size = Vector3.new(100000, 100000, 100000)
        BlackHole.Transparency = 1
        BlackHole.Anchored = true
        BlackHole.CanCollide = false
        BlackHole.Name = "BlackHoleTarget"
        BlackHole.Parent = Workspace

        -- Attachment base no BlackHole
        local baseAttachment = Instance.new("Attachment")
        baseAttachment.Name = "Luscaa_BlackHoleAttachment"
        baseAttachment.Parent = BlackHole

        -- Atualiza posição do BlackHole
        RunService.Heartbeat:Connect(function()
            BlackHole.CFrame = HRP.CFrame
        end)

        -- Lista de portas controladas
        local ControlledDoors = {}

        -- Prepara uma porta para ser controlada
        local function SetupPart(part)
            if not part:IsA("BasePart") or part.Anchored or not string.find(part.Name, "Door") then return end
            if part:FindFirstChild("Luscaa_Attached") then return end

            part.CanCollide = false
            part.Transparency = 1 -- ← Apenas isso foi adicionado

            for _, obj in ipairs(part:GetChildren()) do
                if obj:IsA("AlignPosition") or obj:IsA("Torque") or obj:IsA("Attachment") then
                    obj:Destroy()
                end
            end

            local marker = Instance.new("BoolValue", part)
            marker.Name = "Luscaa_Attached"

            local a1 = Instance.new("Attachment", part)

            local align = Instance.new("AlignPosition", part)
            align.Attachment0 = a1
            align.Attachment1 = baseAttachment
            align.MaxForce = 1e20
            align.MaxVelocity = math.huge
            align.Responsiveness = 99999

            local torque = Instance.new("Torque", part)
            torque.Attachment0 = a1
            torque.RelativeTo = Enum.ActuatorRelativeTo.World
            torque.Torque = Vector3.new(
                math.random(-10e5, 10e5) * 10000,
                math.random(-10e5, 10e5) * 10000,
                math.random(-10e5, 10e5) * 10000
            )

            table.insert(ControlledDoors, {Part = part, Align = align})
        end

        -- Detecta e prepara portas existentes
        for _, obj in ipairs(Workspace:GetDescendants()) do
            if obj:IsA("BasePart") and string.find(obj.Name, "Door") then
                SetupPart(obj)
            end
        end

        -- Novas portas no futuro
        Workspace.DescendantAdded:Connect(function(obj)
            if obj:IsA("BasePart") and string.find(obj.Name, "Door") then
                SetupPart(obj)
            end
        end)

        -- Flinga jogador com timeout e retorno
        local function FlingPlayer(player)
            local char = player.Character
            if not char then return end
            local targetHRP = char:FindFirstChild("HumanoidRootPart")
            if not targetHRP then return end

            local targetAttachment = targetHRP:FindFirstChild("SHNMAX_TargetAttachment")
            if not targetAttachment then
                targetAttachment = Instance.new("Attachment", targetHRP)
                targetAttachment.Name = "SHNMAX_TargetAttachment"
            end

            for _, data in ipairs(ControlledDoors) do
                if data.Align then
                    data.Align.Attachment1 = targetAttachment
                end
            end

            local start = tick()
            local flingDetected = false

            while tick() - start < 5 do
                if targetHRP.Velocity.Magnitude >= 20 then
                    flingDetected = true
                    break
                end
                RunService.Heartbeat:Wait()
            end

            -- Sempre retorna as portas
            for _, data in ipairs(ControlledDoors) do
                if data.Align then
                    data.Align.Attachment1 = baseAttachment
                end
            end
        end

        -- Clique (funciona no mobile)
        UserInputService.TouchTap:Connect(function(touchPositions, processed)
            if processed then return end
            local pos = touchPositions[1]
            local camera = Workspace.CurrentCamera
            local unitRay = camera:ScreenPointToRay(pos.X, pos.Y)
            local raycast = Workspace:Raycast(unitRay.Origin, unitRay.Direction * 1000)

            if raycast and raycast.Instance then
                local hit = raycast.Instance
                local player = Players:GetPlayerFromCharacter(hit:FindFirstAncestorOfClass("Model"))
                if player and player ~= LocalPlayer then
                    FlingPlayer(player)
                end
            end
        end)
    end
})

-- Click Tool Functions
TrollTab:CreateButton({
    Name = "Click Fling Couch (Tool)",
    Callback = function()
        local jogadores = game:GetService("Players")
        local rep = game:GetService("ReplicatedStorage")
        local entrada = game:GetService("UserInputService")
        local eu = jogadores.LocalPlayer
        local cam = workspace.CurrentCamera

        local podeClicar = true
        local ferramentaEquipada = false
        local NOME_FERRAMENTA = "Click Fling Couch"

        local mochila = eu:WaitForChild("Backpack")

        if not mochila:FindFirstChild(NOME_FERRAMENTA) and not (eu.Character and eu.Character:FindFirstChild(NOME_FERRAMENTA)) then
            local ferramenta = Instance.new("Tool")
            ferramenta.Name = NOME_FERRAMENTA
            ferramenta.RequiresHandle = false
            ferramenta.CanBeDropped = false

            ferramenta.Equipped:Connect(function()
                ferramentaEquipada = true
            end)

            ferramenta.Unequipped:Connect(function()
                ferramentaEquipada = false
            end)

            ferramenta.Parent = mochila
        end

        local function jogarComSofa(alvo)
            if not ferramentaEquipada then return end
            if not alvo or not alvo.Character or alvo == eu then return end

            local jogando = true
            local raiz = eu.Character and eu.Character:FindFirstChild("HumanoidRootPart")
            local alvoRaiz = alvo.Character and alvo.Character:FindFirstChild("HumanoidRootPart")
            if not raiz or not alvoRaiz then return end

            local boneco = eu.Character
            local humano = boneco:FindFirstChildOfClass("Humanoid")
            local posOriginal = raiz.CFrame

            rep:WaitForChild("RE"):WaitForChild("1Clea1rTool1s"):FireServer("ClearAllTools")
            task.wait(0.2)

            rep.RE:FindFirstChild("1Too1l"):InvokeServer("PickingTools", "Couch")
            task.wait(0.3)

            local sofa = eu.Backpack:FindFirstChild("Couch")
            if sofa then
                sofa.Parent = boneco
            end
            task.wait(0.1)

            game:GetService("VirtualInputManager"):SendKeyEvent(true, Enum.KeyCode.F, false, game)
            task.wait(0.25)

            workspace.FallenPartsDestroyHeight = 0/0

            local forca = Instance.new("BodyVelocity")
            forca.Name = "ForcaJogada"
            forca.Velocity = Vector3.new(9e8, 9e8, 9e8)
            forca.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
            forca.Parent = raiz

            humano:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
            humano.PlatformStand = false
            cam.CameraSubject = alvo.Character:FindFirstChild("Head") or alvoRaiz or humano

            task.spawn(function()
                local angulo = 0
                local partes = {raiz}
                while jogando and alvo and alvo.Character and alvo.Character:FindFirstChildOfClass("Humanoid") do
                    local alvoHum = alvo.Character:FindFirstChildOfClass("Humanoid")
                    if alvoHum.Sit then break end
                    angulo += 50

                    for _, parte in ipairs(partes) do
                        local hrp = alvo.Character.HumanoidRootPart
                        local pos = hrp.Position + hrp.Velocity / 1.5
                        raiz.CFrame = CFrame.new(pos) * CFrame.Angles(math.rad(angulo), 0, 0)
                    end

                    raiz.Velocity = Vector3.new(9e8, 9e8, 9e8)
                    raiz.RotVelocity = Vector3.new(9e8, 9e8, 9e8)
                    task.wait()
                end

                jogando = false
                forca:Destroy()
                humano:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
                humano.PlatformStand = false
                raiz.CFrame = posOriginal
                cam.CameraSubject = humano

                for _, p in pairs(boneco:GetDescendants()) do
                    if p:IsA("BasePart") then
                        p.Velocity = Vector3.zero
                        p.RotVelocity = Vector3.zero
                    end
                end

                humano:UnequipTools()
                rep.RE:FindFirstChild("1Too1l"):InvokeServer("PickingTools", "Couch")
            end)

            while jogando do
                task.wait()
            end
        end

        entrada.TouchTap:Connect(function(toques, processado)
            if processado or not podeClicar or not ferramentaEquipada then return end

            local pos = toques[1]
            local raio = cam:ScreenPointToRay(pos.X, pos.Y)
            local acerto = workspace:Raycast(raio.Origin, raio.Direction * 1000)

            if acerto and acerto.Instance then
                local alvo = jogadores:GetPlayerFromCharacter(acerto.Instance:FindFirstAncestorOfClass("Model"))
                if alvo and alvo ~= eu then
                    podeClicar = false
                    jogarComSofa(alvo)
                    task.delay(2, function()
                        podeClicar = true
                    end)
                end
            end
        end)
    end
})

TrollTab:CreateButton({
    Name = "Click Fling Ball (Tool)",
    Callback = function()
        local jogadores = game:GetService("Players")
        local rep = game:GetService("ReplicatedStorage")
        local mundo = game:GetService("Workspace")
        local entrada = game:GetService("UserInputService")
        local cam = mundo.CurrentCamera
        local eu = jogadores.LocalPlayer

        local NOME_FERRAMENTA = "Click Fling Ball"
        local ferramentaEquipada = false

        local mochila = eu:WaitForChild("Backpack")
        if not mochila:FindFirstChild(NOME_FERRAMENTA) then
            local ferramenta = Instance.new("Tool")
            ferramenta.Name = NOME_FERRAMENTA
            ferramenta.RequiresHandle = false
            ferramenta.CanBeDropped = false

            ferramenta.Equipped:Connect(function()
                ferramentaEquipada = true
            end)

            ferramenta.Unequipped:Connect(function()
                ferramentaEquipada = false
            end)

            ferramenta.Parent = mochila
        end

        -- Função FlingBall (bola)
        local function FlingBallTool(target)
            local players = game:GetService("Players")
            local player = players.LocalPlayer
            local character = player.Character or player.CharacterAdded:Wait()
            local humanoid = character:WaitForChild("Humanoid")
            local hrp = character:WaitForChild("HumanoidRootPart")
            local backpack = player:WaitForChild("Backpack")
            local ServerBalls = workspace.WorkspaceCom:WaitForChild("001_SoccerBalls")

            local function GetBall()
                if not backpack:FindFirstChild("SoccerBall") and not character:FindFirstChild("SoccerBall") then
                    game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l"):InvokeServer("PickingTools", "SoccerBall")
                end

                repeat task.wait() until backpack:FindFirstChild("SoccerBall") or character:FindFirstChild("SoccerBall")

                local ballTool = backpack:FindFirstChild("SoccerBall")
                if ballTool then
                    ballTool.Parent = character
                end

                repeat task.wait() until ServerBalls:FindFirstChild("Soccer" .. player.Name)

                return ServerBalls:FindFirstChild("Soccer" .. player.Name)
            end

            local Ball = ServerBalls:FindFirstChild("Soccer" .. player.Name) or GetBall()
            Ball.CanCollide = false
            Ball.Massless = true
            Ball.CustomPhysicalProperties = PhysicalProperties.new(0.0001, 0, 0)

            if target ~= player then
                local tchar = target.Character
                if tchar and tchar:FindFirstChild("HumanoidRootPart") and tchar:FindFirstChild("Humanoid") then
                    local troot = tchar.HumanoidRootPart
                    local thum = tchar.Humanoid

                    if Ball:FindFirstChildWhichIsA("BodyVelocity") then
                        Ball:FindFirstChildWhichIsA("BodyVelocity"):Destroy()
                    end

                    local bv = Instance.new("BodyVelocity")
                    bv.Name = "FlingPower"
                    bv.Velocity = Vector3.new(9e8, 9e8, 9e8)
                    bv.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
                    bv.P = 9e900
                    bv.Parent = Ball

                    workspace.CurrentCamera.CameraSubject = thum

                    repeat
                        if troot.Velocity.Magnitude > 0 then
                            local pos = troot.Position + (troot.Velocity / 1.5)
                            Ball.CFrame = CFrame.new(pos)
                            Ball.Orientation += Vector3.new(45, 60, 30)
                        else
                            for i, v in pairs(tchar:GetChildren()) do
                                if v:IsA("BasePart") and v.CanCollide and not v.Anchored then
                                    Ball.CFrame = v.CFrame
                                    task.wait(1/6000)
                                end
                            end
                        end
                        task.wait(1/6000)
                    until troot.Velocity.Magnitude > 1000 or thum.Health <= 0 or not tchar:IsDescendantOf(workspace) or target.Parent ~= players

                    workspace.CurrentCamera.CameraSubject = humanoid
                end
            end
        end

        -- Toque na tela para aplicar a bola
        entrada.TouchTap:Connect(function(toques, processado)
            if not ferramentaEquipada or processado then return end
            local pos = toques[1]
            local raio = cam:ScreenPointToRay(pos.X, pos.Y)
            local hit = mundo:Raycast(raio.Origin, raio.Direction * 1000)
            if hit and hit.Instance then
                local modelo = hit.Instance:FindFirstAncestorOfClass("Model")
                local jogador = jogadores:GetPlayerFromCharacter(modelo)
                if jogador and jogador ~= eu then
                    FlingBallTool(jogador)
                end
            end
        end)
    end
})

TrollTab:CreateButton({
    Name = "Click Fling Admin v2 (Tool)",
    Callback = function()
        local jogadores = game:GetService("Players")
        local rep = game:GetService("ReplicatedStorage")
        local mundo = game:GetService("Workspace")
        local entrada = game:GetService("UserInputService")
        local cam = mundo.CurrentCamera
        local eu = jogadores.LocalPlayer

        local NOME_FERRAMENTA = "Admin Fling"
        local ferramentaEquipada = false

        local mochila = eu:WaitForChild("Backpack")

        for _, ferramentaExistente in pairs(mochila:GetChildren()) do
            if ferramentaExistente:IsA("Tool") and ferramentaExistente.Name:lower():find("fling") then
                ferramentaExistente.Name = "Admin Fling"
            end
        end

        if not mochila:FindFirstChild(NOME_FERRAMENTA) then
            local ferramenta = Instance.new("Tool")
            ferramenta.Name = NOME_FERRAMENTA
            ferramenta.RequiresHandle = true
            ferramenta.CanBeDropped = false

            local handle = Instance.new("Part")
            handle.Name = "Handle"
            handle.Size = Vector3.new(1, 1, 1)
            handle.Transparency = 1
            handle.Parent = ferramenta

            local decal = Instance.new("Decal")
            decal.Texture = "rbxassetid://775552544"
            decal.Face = Enum.NormalId.Front
            decal.Parent = handle

            ferramenta.Equipped:Connect(function()
                ferramentaEquipada = true
            end)

            ferramenta.Unequipped:Connect(function()
                ferramentaEquipada = false
            end)

            ferramenta.Parent = mochila
        end

        local function FlingBallAdmin(target)
            local player = jogadores.LocalPlayer
            local character = player.Character or player.CharacterAdded:Wait()
            local humanoid = character:WaitForChild("Humanoid")
            local hrp = character:WaitForChild("HumanoidRootPart")
            local backpack = player:WaitForChild("Backpack")
            local ServerBalls = mundo:WaitForChild("WorkspaceCom"):WaitForChild("001_SoccerBalls")

            local function GetBall()
                if not backpack:FindFirstChild("SoccerBall") and not character:FindFirstChild("SoccerBall") then
                    rep.RE:FindFirstChild("1Too1l"):InvokeServer("PickingTools", "SoccerBall")
                end
                repeat task.wait() until backpack:FindFirstChild("SoccerBall") or character:FindFirstChild("SoccerBall")
                local ballTool = backpack:FindFirstChild("SoccerBall")
                if ballTool then ballTool.Parent = character end
                repeat task.wait() until ServerBalls:FindFirstChild("Soccer" .. player.Name)
                return ServerBalls:FindFirstChild("Soccer" .. player.Name)
            end

            local Ball = ServerBalls:FindFirstChild("Soccer" .. player.Name) or GetBall()
            Ball.CanCollide = false
            Ball.Massless = true
            Ball.Transparency = 1             -- BOLA INVISÍVEL
            Ball.CustomPhysicalProperties = PhysicalProperties.new(0.0001, 0, 0)

            if target ~= player then
                local tchar = target.Character
                if tchar and tchar:FindFirstChild("HumanoidRootPart") and tchar:FindFirstChild("Humanoid") then
                    local troot = tchar.HumanoidRootPart
                    local thum = tchar.Humanoid
                    if Ball:FindFirstChildWhichIsA("BodyVelocity") then
                        Ball:FindFirstChildWhichIsA("BodyVelocity"):Destroy()
                    end
                    local bv = Instance.new("BodyVelocity")
                    bv.Name = "FlingPower"
                    bv.Velocity = Vector3.new(9e8, 9e8, 9e8)
                    bv.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
                    bv.P = 9e900
                    bv.Parent = Ball
                    mundo.CurrentCamera.CameraSubject = thum

                    repeat
                        if troot.Velocity.Magnitude > 0 then
                            local pos = troot.Position + (troot.Velocity / 1.5)
                            Ball.CFrame = CFrame.new(pos)
                            Ball.Orientation += Vector3.new(45, 60, 30)
                        else
                            for _, v in pairs(tchar:GetChildren()) do
                                if v:IsA("BasePart") and v.CanCollide and not v.Anchored then
                                    Ball.CFrame = v.CFrame
                                    task.wait(1/6000)
                                end
                            end
                        end
                        task.wait(1/6000)
                    until troot.Velocity.Magnitude > 1000 or thum.Health <= 0 or not tchar:IsDescendantOf(mundo) or target.Parent ~= jogadores

                    mundo.CurrentCamera.CameraSubject = humanoid
                end
            end
        end

        entrada.TouchTap:Connect(function(toques, processado)
            if not ferramentaEquipada or processado then return end
            local pos = toques[1]
            local raio = cam:ScreenPointToRay(pos.X, pos.Y)
            local hit = mundo:Raycast(raio.Origin, raio.Direction * 1000)
            if hit and hit.Instance then
                local modelo = hit.Instance:FindFirstAncestorOfClass("Model")
                local jogador = jogadores:GetPlayerFromCharacter(modelo)
                if jogador and jogador ~= eu then
                    FlingBallAdmin(jogador)
                end
            end
        end)
    end
})

TrollTab:CreateButton({
    Name = "Click Kill Couch (Tool)",
    Callback = function()
        local jogadores = game:GetService("Players")
        local rep = game:GetService("ReplicatedStorage")
        local loop = game:GetService("RunService")
        local mundo = game:GetService("Workspace")
        local entrada = game:GetService("UserInputService")

        local eu = jogadores.LocalPlayer
        local cam = mundo.CurrentCamera

        local NOME_FERRAMENTA = "Click Kill Couch"
        local ferramentaEquipada = false
        local nomeAlvo = nil
        local loopTP = nil
        local sofaEquipado = false
        local base = nil
        local posInicial = nil
        local raiz = nil

        local mochila = eu:WaitForChild("Backpack")
        if not mochila:FindFirstChild(NOME_FERRAMENTA) then
            local ferramenta = Instance.new("Tool")
            ferramenta.Name = NOME_FERRAMENTA
            ferramenta.RequiresHandle = false
            ferramenta.CanBeDropped = false

            ferramenta.Equipped:Connect(function()
                ferramentaEquipada = true
            end)

            ferramenta.Unequipped:Connect(function()
                ferramentaEquipada = false
                nomeAlvo = nil
                limparSofa()
            end)

            ferramenta.Parent = mochila
        end

        function limparSofa()
            if loopTP then
                loopTP:Disconnect()
                loopTP = nil
            end

            if sofaEquipado then
                local boneco = eu.Character
                if boneco then
                    local sofa = boneco:FindFirstChild("Couch")
                    if sofa then
                        sofa.Parent = eu.Backpack
                        sofaEquipado = false
                    end
                end
            end

            if base then
                base:Destroy()
                base = nil
            end

            if getgenv().AntiSit then
                getgenv().AntiSit:Set(false)
            end

            local humano = eu.Character and eu.Character:FindFirstChildOfClass("Humanoid")
            if humano then
                humano:SetStateEnabled(Enum.HumanoidStateType.Physics, true)
                humano:ChangeState(Enum.HumanoidStateType.GettingUp)
            end

            if posInicial and raiz then
                raiz.CFrame = posInicial
                posInicial = nil
            end
        end

        function pegarSofa()
            local boneco = eu.Character
            if not boneco then return end
            local mochila = eu.Backpack

            if not mochila:FindFirstChild("Couch") and not boneco:FindFirstChild("Couch") then
                local args = { "PickingTools", "Couch" }
                rep.RE["1Too1l"]:InvokeServer(unpack(args))
                task.wait(0.1)
            end

            local sofa = mochila:FindFirstChild("Couch") or boneco:FindFirstChild("Couch")
            if sofa then
                sofa.Parent = boneco
                sofaEquipado = true
            end
        end

        function posAleatoriaAbaixo(boneco)
            local rp = boneco:FindFirstChild("HumanoidRootPart")
            if not rp then return Vector3.new() end
            local offset = Vector3.new(math.random(-2, 2), -5.1, math.random(-2, 2))
            return rp.Position + offset
        end

        function tpAbaixo(alvo)
            if not alvo or not alvo.Character or not alvo.Character:FindFirstChild("HumanoidRootPart") then return end

            local meuBoneco = eu.Character
            local minhaRaiz = meuBoneco and meuBoneco:FindFirstChild("HumanoidRootPart")
            local humano = meuBoneco and meuBoneco:FindFirstChildOfClass("Humanoid")

            if not minhaRaiz or not humano then return end

            humano:SetStateEnabled(Enum.HumanoidStateType.Physics, false)

            if not base then
                base = Instance.new("Part")
                base.Size = Vector3.new(10, 1, 10)
                base.Anchored = true
                base.CanCollide = true
                base.Transparency = 0.5
                base.Parent = mundo
            end

            local destino = posAleatoriaAbaixo(alvo.Character)
            base.Position = destino
            minhaRaiz.CFrame = CFrame.new(destino)

            humano:SetStateEnabled(Enum.HumanoidStateType.Physics, true)
        end

        function arremessarComSofa(alvo)
            if not alvo then return end
            nomeAlvo = alvo.Name
            local boneco = eu.Character
            if not boneco then return end

            posInicial = boneco:FindFirstChild("HumanoidRootPart") and boneco.HumanoidRootPart.CFrame
            raiz = boneco:FindFirstChild("HumanoidRootPart")
            pegarSofa()

            loopTP = loop.Heartbeat:Connect(function()
                local alvoAtual = jogadores:FindFirstChild(nomeAlvo)
                if not alvoAtual or not alvoAtual.Character or not alvoAtual.Character:FindFirstChild("Humanoid") then
                    limparSofa()
                    return
                end
                if getgenv().AntiSit then
                    getgenv().AntiSit:Set(true)
                end
                tpAbaixo(alvoAtual)
            end)

            task.spawn(function()
                local alvoAtual = jogadores:FindFirstChild(nomeAlvo)
                while alvoAtual and alvoAtual.Character and alvoAtual.Character:FindFirstChild("Humanoid") do
                    task.wait(0.05)
                    if alvoAtual.Character.Humanoid.SeatPart then
                        local buraco = CFrame.new(265.46, -450.83, -59.93)
                        alvoAtual.Character.HumanoidRootPart.CFrame = buraco
                        eu.Character.HumanoidRootPart.CFrame = buraco
                        task.wait(0.4)
                        limparSofa()
                        task.wait(0.2)
                        if posInicial then
                            eu.Character.HumanoidRootPart.CFrame = posInicial
                        end
                        break
                    end
                end
            end)
        end

        entrada.TouchTap:Connect(function(toques, processado)
            if not ferramentaEquipada or processado then return end
            local pos = toques[1]
            local raio = cam:ScreenPointToRay(pos.X, pos.Y)
            local hit = mundo:Raycast(raio.Origin, raio.Direction * 1000)
            if hit and hit.Instance then
                local modelo = hit.Instance:FindFirstAncestorOfClass("Model")
                local jogador = jogadores:GetPlayerFromCharacter(modelo)
                if jogador and jogador ~= eu then
                    arremessarComSofa(jogador)
                end
            end
        end)
    end
})

-- Garantir humanoid após respawn
LocalPlayer.CharacterAdded:Connect(function()
    GetHumanoid()
end)
