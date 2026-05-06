local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
   Name = "LUCKI HUB",
   LoadingTitle = "Loading Lucki Hub...",
   LoadingSubtitle = "by Your Name",
   ConfigurationSaving = {
      Enabled = true,
      FolderName = "LuckiHubConfig"
   }
})

local MainTab = Window:CreateTab("Main", 4483362458) -- Main Tab icon

-- SPEED SETTINGS
MainTab:CreateSlider({
   Name = "WalkSpeed Settings",
   Range = {16, 200},
   Increment = 1,
   Suffix = "Speed",
   CurrentValue = 16,
   Flag = "SpeedSlider", 
   Callback = function(Value)
      game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value
   end,
})

-- COMBAT BUTTONS
MainTab:CreateSection("Combat")

MainTab:CreateToggle({
   Name = "Auto Bat (Combat)",
   CurrentValue = false,
   Flag = "AutoBat", 
   Callback = function(Value)
      _G.AutoBat = Value
      while _G.AutoBat do
         local tool = game.Players.LocalPlayer.Character:FindFirstChild("Bat") or game.Players.LocalPlayer.Backpack:FindFirstChild("Bat")
         if tool then
            game.Players.LocalPlayer.Character.Humanoid:EquipTool(tool)
            tool:Activate()
         end
         task.wait(0.1)
      end
   end,
})

MainTab:CreateButton({
   Name = "Auto Steal",
   Callback = function()
      Rayfield:Notify({
         Title = "Auto Steal",
         Content = "Looking for Brainrot to steal...",
         Duration = 3,
         Image = 4483362458,
      })
      -- This is where the game's specific "Steal" code goes
   end,
})
