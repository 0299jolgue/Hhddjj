-- RemoteSpy Lite – para ver eventos
local mt = getrawmetatable(game)
setreadonly(mt, false)

local old = mt.__namecall
mt.__namecall = newcclosure(function(self, ...)
    local method = getnamecallmethod()
    if method == "FireServer" or method == "InvokeServer" then
        print("📡 Remote detectado:", self:GetFullName(), "com args:", ...)
    end
    return old(self, ...)
end)

print("🔍 RemoteSpy ativado! Agora ative o bloqueio da base e veja o console.")
