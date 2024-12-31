-- List of admin players
local adminList = {"YourUsername"} -- Replace "YourUsername" with your Roblox username

-- Function to check if a player is an admin
local function isAdmin(playerName)
    return table.find(adminList, playerName) ~= nil
end

-- Function to set a player's team
local function setTeam(targetPlayer, teamName)
    if targetPlayer and targetPlayer.Team then
        if teamName:lower() == "prisoner" then
            targetPlayer.Team = game.Teams["Prisoner"]
        elseif teamName:lower() == "citizen" then
            targetPlayer.Team = game.Teams["Citizen"]
        end
    end
end

-- Function to make a player invincible
local function makeGod(targetPlayer)
    if targetPlayer and targetPlayer.Character and targetPlayer.Character:FindFirstChild("Humanoid") then
        targetPlayer.Character.Humanoid.MaxHealth = math.huge
        targetPlayer.Character.Humanoid.Health = math.huge
    end
end

-- Function to ban a player
local function banPlayer(targetPlayer)
    if targetPlayer then
        targetPlayer:Kick("You have been banned by an admin.")
    end
end

-- Function to set a player's walk speed
local function setWalkSpeed(targetPlayer, speed)
    if targetPlayer and targetPlayer.Character and targetPlayer.Character:FindFirstChild("Humanoid") then
        targetPlayer.Character.Humanoid.WalkSpeed = tonumber(speed) or 16
    end
end

-- Handle chat commands
game.Players.LocalPlayer.Chatted:Connect(function(message)
    local args = string.split(message, " ")
    local command = args[1]:lower()
    local playerName = game.Players.LocalPlayer.Name

    if not isAdmin(playerName) then return end -- Check if the player is an admin

    if command == ":team" then
        local targetName = args[2]
        local teamName = args[3]
        local targetPlayer = game.Players:FindFirstChild(targetName)
        if targetPlayer and teamName then
            setTeam(targetPlayer, teamName)
        end

    elseif command == ":god" then
        local targetPlayer = game.Players.LocalPlayer
        makeGod(targetPlayer)

    elseif command == ":ban" then
        local targetName = args[2]
        local targetPlayer = game.Players:FindFirstChild(targetName)
        if targetPlayer then
            banPlayer(targetPlayer)
        end

    elseif command == ":ws" then
        local targetName = args[2]
        local speed = args[3]
        local targetPlayer = game.Players:FindFirstChild(targetName)
        if targetPlayer and speed then
            setWalkSpeed(targetPlayer, speed)
        end
    end
end)
