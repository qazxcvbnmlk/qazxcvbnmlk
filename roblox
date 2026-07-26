-- Load Rayfield UI Library
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

-- Create Main Window
local Window = Rayfield:CreateWindow({
   Name = "Ultimate Game Hub 👑",
   LoadingTitle = "Loading Hub...",
   LoadingSubtitle = "Developer Edition",
   ConfigurationSaving = {
      Enabled = false
   },
   Discord = {
      Enabled = false
   },
   KeySystem = false
})

-- Create Tabs
local SpooferTab = Window:CreateTab("Visual Spoofer", 4483362458)
local WeaponTab  = Window:CreateTab("Weapons", 4483362458)

-- Variables & Configurations
local TargetSpeedText = "900Qi Speed"
local TargetWinsText = "90Qi"
local TargetRebirthsValue = 30
local TargetFloatingText = "+9Qi"
local TargetProgressBarText = "120Qi / 3000Qi"
local TargetLevelText = "Level 2000"

local SpooferActive = false

-- 1. SPOOFER TAB TOGGLE
SpooferTab:CreateToggle({
   Name = "Enable God-Mode Visual Spoofer",
   CurrentValue = false,
   Flag = "SpooferToggle",
   Callback = function(Value)
      SpooferActive = Value
      if Value then
         Rayfield:Notify({
            Title = "Spoofer Activated",
            Content = "900Qi Speed, 90Qi Wins, Level 2000, and [OWNER👑] Title are live!",
            Duration = 3,
            Image = 4483362458,
         })
      end
   end,
})

-- Background Loop for Spoofer Actions
task.spawn(function()
   local Players = game:GetService("Players")
   local LocalPlayer = Players.LocalPlayer

   while task.wait(0.05) do
      if SpooferActive then
         -- A. Overhead Owner Title
         local character = LocalPlayer.Character
         if character and character:FindFirstChild("Head") then
            local head = character.Head
            if not head:FindFirstChild("OwnerTitleGui") then
               local billboard = Instance.new("BillboardGui")
               billboard.Name = "OwnerTitleGui"
               billboard.Size = UDim2.new(0, 200, 0, 50)
               billboard.StudsOffset = Vector3.new(0, 2.5, 0)
               billboard.AlwaysOnTop = true
               billboard.Parent = head
               
               local label = Instance.new("TextLabel")
               label.Size = UDim2.new(1, 0, 1, 0)
               label.BackgroundTransparency = 1
               label.Text = "[OWNER👑]"
               label.TextColor3 = Color3.fromRGB(255, 215, 0)
               label.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
               label.TextStrokeTransparency = 0
               label.Font = Enum.Font.SourceSansBold
               label.TextSize = 26
               label.Parent = billboard
            end
         end

         -- B. Screen UI Texts (Speed, Level, Wins, Progress Bar)
         local playerGui = LocalPlayer:FindFirstChild("PlayerGui")
         if playerGui then
            for _, v in pairs(playerGui:GetDescendants()) do
               if v:IsA("TextLabel") or v:IsA("TextBox") then
                  local currentText = v.Text
                  
                  if currentText:find("Level") and not currentText:find("Multiplier") then
                     v.Text = TargetLevelText
                  end
                  
                  if currentText:find("/") and (currentText:find("Qi") or currentText:find("M") or currentText:find("K")) then
                     if v.Parent.Name:lower():find("bar") or v.Name:lower():find("xp") or v.Name:lower():find("progress") or currentText:find("120Qi") then
                        v.Text = TargetProgressBarText
                     end
                  end
                  
                  if currentText:find("Speed") and not currentText:find("Multiplier") and not currentText:find("+") then
                     v.Text = TargetSpeedText
                  end
                  
                  if currentText:find("317") or currentText == "90Qi" or (v.Parent.Name:lower():find("win") and currentText:find("K")) then
                     v.Text = TargetWinsText
                  end
               end
            end
         end

         -- C. Floating Indicators (+9Qi)
         if character then
            for _, child in pairs(character:GetDescendants()) do
               if child:IsA("TextLabel") or child:IsA("TextBox") then
                  local txt = child.Text
                  if txt:find("+") and (txt:find("K") or txt:find("M") or txt:find("B") or txt:find("T")) then
                     child.Text = TargetFloatingText
                     child.TextColor3 = Color3.fromRGB(0, 255, 255)
                  end
               end
            end
         end

         -- D. Leaderboard Stats
         local leaderstats = LocalPlayer:FindFirstChild("leaderstats") or LocalPlayer:FindFirstChild("Leaderstats")
         if leaderstats then
            for _, stat in pairs(leaderstats:GetChildren()) do
               local name = stat.Name:lower()
               if name:find("speed") or name:find("step") then
                  pcall(function() stat.Value = 900000000000000000000000000 end)
               elseif name:find("win") then
                  pcall(function() stat.Value = 90000000000000000000000000 end)
               elseif name:find("rebirth") then
                  pcall(function() stat.Value = TargetRebirthsValue end)
               end
            end
         end
      end
   end
end)

-- 2. WEAPONS TAB BUTTON
WeaponTab:CreateButton({
   Name = "Give Combat Blaster Tool",
   Callback = function()
      local Players = game:GetService("Players")
      local LocalPlayer = Players.LocalPlayer
      
      -- Remove duplicate if existing
      if LocalPlayer.Backpack:FindFirstChild("CombatBlaster") then
         LocalPlayer.Backpack.CombatBlaster:Destroy()
      end
      
      local GunTool = Instance.new("Tool")
      GunTool.Name = "CombatBlaster"
      GunTool.RequiresHandle = true
      GunTool.Grip = CFrame.new(0, -0.2, 0.4) * CFrame.Angles(math.rad(-90), 0, 0)

      local Handle = Instance.new("Part")
      Handle.Name = "Handle"
      Handle.Size = Vector3.new(0.4, 0.6, 1.5)
      Handle.Color = Color3.fromRGB(30, 30, 35)
      Handle.Material = Enum.Material.Metal
      Handle.Parent = GunTool

      local Barrel = Instance.new("Part")
      Barrel.Name = "Barrel"
      Barrel.Size = Vector3.new(0.3, 0.3, 1.2)
      Barrel.Color = Color3.fromRGB(0, 255, 255)
      Barrel.Material = Enum.Material.Neon
      Barrel.Position = Handle.Position + Vector3.new(0, 0.2, -0.8)
      Barrel.Parent = GunTool

      local Weld = Instance.new("WeldConstraint")
      Weld.Part0 = Handle
      Weld.Part1 = Barrel
      Weld.Parent = Handle

      GunTool.Parent = LocalPlayer.Backpack

      Rayfield:Notify({
         Title = "Weapon Equipped",
         Content = "Combat Blaster has been added to your inventory!",
         Duration = 3,
         Image = 4483362458,
      })
   end,
})
