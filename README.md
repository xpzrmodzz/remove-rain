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

-- On commence par obtenir les services nécessaires
local workspace = game:GetService("Workspace")
local player = game.Players.LocalPlayer

-- Fonction qui vérifie l'existence des objets et les manipule si disponibles
local function handleRainEffects()
    -- Cherche l'objet __RainEmitter sous Camera
    local camera = workspace:FindFirstChild("Camera")
    
    if camera then
        local rainEmitter = camera:FindFirstChild("__RainEmitter")
        
        if rainEmitter then
            -- Vérifier si RainStraight existe sous __RainEmitter
            local rainStraight = rainEmitter:FindFirstChild("RainStraight")
            
            if rainStraight then
                -- Si RainStraight existe, on peut l'utiliser
              
                -- Exemple de manipulation (comme désactiver RainStraight)
                rainStraight.Enabled = false
            else
                -- Si RainStraight n'existe pas, afficher un message d'erreur
                print("")
            end
            
            -- Maintenant, tentons de détruire RainEmitter (si c'est ce que tu souhaites)
            rainEmitter:Destroy()
            print("__RainEmitter a été supprimé.")
            
        else
            -- Si __RainEmitter n'existe pas sous Camera, afficher un message d'erreur
            print("")
        end
    else
        -- Si Camera n'existe pas dans workspace, afficher un message d'erreur
        print("")
    end
end

-- Appeler la fonction pour gérer les effets de pluie
handleRainEffects()


