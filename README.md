--[[
 ▄▄▄▄   ▓██   ██▓     █████▒ ██▀███   ██▓▄▄▄█████▓▓█████ 
▓█████▄  ▒██  ██▒   ▓██   ▒ ▓██ ▒ ██▒▓██▒▓  ██▒ ▓▒▓█   ▀ 
▒██▒ ▄██  ▒██ ██░   ▒████ ░ ▓██ ░▄█ ▒▒██▒▒ ▓██░ ▒░▒███   
▒██░█▀    ░ ▐██▓░   ░▓█▒  ░ ▒██▀▀█▄  ░██░░ ▓██▓ ░ ▒▓█  ▄ 
░▓█  ▀█▓  ░ ██▒▓░   ░▒█░    ░██▓ ▒██▒░██░  ▒██▒ ░ ░▒████▒
░▒▓███▀▒   ██▒▒▒     ▒ ░    ░ ▒▓ ░▒▓░░▓    ▒ ░░   ░░ ▒░ ░
▒░▒   ░  ▓██ ░▒░     ░        ░▒ ░ ▒░ ▒ ░    ░     ░ ░  ░
 ░    ░  ▒ ▒ ░░      ░ ░      ░░   ░  ▒ ░  ░         ░   
 ░       ░ ░                   ░      ░              ░  ░
      ░  ░ ░                                              

          .:+*#%%#####*++++-.
                :#%%*+*+-.....
             .=%%+++:..
           .=%#++=.
          -%%+++.
      .  =%%++-          ....
      #%+#%++=.        .:#%%%*:
      :#@%#+=          :*+:-*%#:
       .*@@#.         .-%*::-%%#.
        .-%@@%-.      .=%%--%%%-   
          .:--=*+-:.:-#%%%%%%%%*.                      
               .:-*#%%%%%%%%%%%%%-                     
                  .+%%%*+*%%%%%%%%+...                 
                  .+%@@%%%%*#%%%%%%%%%*-.              
                   .*%@%%%%%%%%%%%%%%%%%#-.            
                   .*%%%%%%%%%%%+#%%%%%%%%%*-.         
                  .=%%%%%%%%%%%%@%*%%%%%####=-==
                  :*%%%%%%%%%%%%%%%*#%%%%#+=-==+
                 .+=*%#%%%%%%%%%%%%%**%%#+**+-:-
                .-=::*-%%%%%%%%%%%%###*-*%###+:
                ...:..%%%%%%%%%%%%%%#:=*+-:.
                     *%%%%%%%%%%%%%%%%.
                    :#%%%%%%%%%%%%%%%%+
                   .*%%%%%%%%%%%%%%%%%#.
                  .=%%%%%%%%%%%%%%%%%%#:
                  .+%%%%%%%%%%%%%%%%%%%*.
                    :+*#%%%@%%%%%%%%%%%%#:.
                      ..:==+*#%#*=-:.:-+***:.

]]--

local player = game.Players.LocalPlayer
local workspace = game:GetService("Workspace")
local soundService = game:GetService("SoundService")

-- Drapeau pour vérifier si l'objet a déjà été supprimé
local hasDestroyed = false

-- Fonction pour supprimer __RainEmitter et __RainSoundGroup une seule fois
local function destroyRainEffects()
    if hasDestroyed then
        return -- Ne rien faire si les effets ont déjà été supprimés
    end

    -- Supprimer __RainEmitter dans Camera si présent
    local camera = workspace:FindFirstChild("Camera")
    if camera then
        local rainEmitter = camera:FindFirstChild("__RainEmitter")
        if rainEmitter then
            rainEmitter:Destroy()
            print("__RainEmitter a été supprimé.")
        end
    end

    -- Supprimer __RainSoundGroup dans SoundService si présent
    local rainSoundGroup = soundService:FindFirstChild("__RainSoundGroup")
    if rainSoundGroup then
        rainSoundGroup:Destroy()
        print("__RainSoundGroup a été supprimé.")
    end

    -- Mettre à jour le drapeau pour empêcher la suppression répétée
    hasDestroyed = true
end

-- Détection de la première exécution
game:GetService("RunService").Heartbeat:Connect(function()
    -- Vérifie si __RainEmitter est toujours là et le supprime
    if not hasDestroyed then
        destroyRainEffects()
    end
end)

