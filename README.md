if not _G.isRunning then
_G.isRunning = true

local zaza = 0
spawn(function()
OldNamecall = hookmetamethod(game, "__namecall", function(self, ...)
  local args = {...}
  if getnamecallmethod() == "FireServer" and self.Name == "Damage" then
  zaza = args[2]
end
  return OldNamecall(self, unpack(args))
end)
end)
local plr = game:GetService("Players").LocalPlayer
local mouse = plr:GetMouse()

mouse.KeyDown:connect(function(key)
if key == "z" then
if zaza ~= 0 then
spawn(function()
game.StarterGui:SetCore("SendNotification", {
Title = "100000$ has been deposited"; -- the title (ofc)
Text = ""; -- what the text says (ofc)
Icon = ""; -- the image if u want. 
Duration = 1.5; -- how long the notification should in secounds
})
for i = 0,999 do
local args = {
    [1] = {
        ["BodyPart"] = workspace.Baddies.Zombie.HeadBox,
        ["Force"] = 0,
        ["GibPower"] = 0,
        ["Damage"] = 0
    },
    [2] = zaza
}

workspace.Baddies.Zombie.Humanoid.Damage:FireServer(unpack(args))

end

local args = {
    [1] = "/w goodluck3646 hey",
    [2] = "All"
}

game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(unpack(args))

end)


else

game.StarterGui:SetCore("SendNotification", {
Title = "Hey Bro"; -- the title (ofc)
Text = "You Gotta Shoot A Zombie First"; -- what the text says (ofc)
Icon = ""; -- the image if u want. 
Duration = 1.5; -- how long the notification should in secounds
})
end

end
end)
else 
game.StarterGui:SetCore("SendNotification", {
Title = "script already runnin"; -- the title (ofc)
Text = ""; -- what the text says (ofc)
Icon = ""; -- the image if u want. 
Duration = 1.5; -- how long the notification should in secounds
})
end
