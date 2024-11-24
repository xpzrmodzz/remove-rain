local player = game.Players.LocalPlayer
local workspace = game:GetService("Workspace")
local soundService = game:GetService("SoundService")

-- Drapeau pour s'assurer que le code s'exécute une seule fois
local hasDestroyed = false

-- Fonction pour supprimer les objets une seule fois
local function destroyRainEffects()
    if hasDestroyed then
        return -- Si l'effet a déjà été supprimé, on arrête l'exécution
    end

    -- Supprimer __RainEmitter dans Camera
    local camera = workspace:FindFirstChild("Camera")
    if camera then
        local rainEmitter = camera:FindFirstChild("__RainEmitter")
        if rainEmitter then
            rainEmitter:Destroy()
            print("__RainEmitter a été supprimé.")
        else
            print("__RainEmitter n'existe pas sous Camera.")
        end
    else
        print("Camera n'existe pas dans workspace.")
    end

    -- Supprimer __RainSoundGroup dans SoundService
    local rainSoundGroup = soundService:FindFirstChild("__RainSoundGroup")
    if rainSoundGroup then
        rainSoundGroup:Destroy()
        print("__RainSoundGroup a été supprimé.")
    else
        print("__RainSoundGroup n'existe pas dans SoundService.")
    end

    -- Marquer que l'effet a été supprimé
    hasDestroyed = true
end

-- Appeler la fonction pour supprimer les objets
destroyRainEffects()
