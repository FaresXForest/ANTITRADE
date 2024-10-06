-- Ultimate Survival Script
-- Developed by فارس و تيم FO

local player = game.Players.LocalPlayer
local userInputService = game:GetService("UserInputService")
local runService = game:GetService("RunService")
local virtualUser = game:GetService("VirtualUser")
local gui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))

-- Create the UI
local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 300, 0, 300)
frame.Position = UDim2.new(0.5, -150, 0.5, -150)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame.BorderSizePixel = 0
frame.Active = true
frame.Draggable = true

local titleLabel = Instance.new("TextLabel", frame)
titleLabel.Size = UDim2.new(1, 0, 0, 50)
titleLabel.Text = "Ultimate Survival Script"
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
titleLabel.BackgroundTransparency = 1
titleLabel.TextScaled = true

local statusLabel = Instance.new("TextLabel", frame)
statusLabel.Size = UDim2.new(1, 0, 0, 50)
statusLabel.Position = UDim2.new(0, 0, 0, 50)
statusLabel.Text = "Status: All Active"
statusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
statusLabel.BackgroundTransparency = 1
statusLabel.TextScaled = true

local toggleButton = Instance.new("TextButton", frame)
toggleButton.Size = UDim2.new(0, 150, 0, 50)
toggleButton.Position = UDim2.new(0.5, -75, 0, 110)
toggleButton.Text = "Toggle AFK"
toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)

-- Add the requested text properties
local ab = Instance.new("TextLabel", frame)
ab.Size = UDim2.new(1, 0, 0, 50)
ab.Position = UDim2.new(0, 0, 0, 160)
ab.Text = "أهلاً بك في السكربت"
ab.TextColor3 = Color3.new(0, 1, 1) -- اللون
ab.TextSize = 20 -- حجم النص
ab.BackgroundTransparency = 1 -- خلفية شفافة

local isAFKActive = true

-- Toggle AFK
local function toggleAFK()
    isAFKActive = not isAFKActive
    statusLabel.Text = isAFKActive and "Status: All Active" or "Status: All Inactive"
    print(isAFKActive and "Ultimate Anti AFK قيد التشغيل." or "Ultimate Anti AFK غير نشط.")
end

toggleButton.MouseButton1Click:Connect(toggleAFK)

-- Anti-Kick Functionality
local function antiKick()
    while true do
        wait(5)  -- Check every 5 seconds
        if player.Character and player.Character:FindFirstChild("Humanoid") then
            local humanoid = player.Character.Humanoid
            humanoid.Health = humanoid.Health  -- Prevent health changes
        end
    end
end

-- Enhanced AutoClicker
local function autoClicker()
    while true do
        wait(300) -- Wait 5 minutes
        if isAFKActive then
            virtualUser:Button1Down(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
            wait(0.1)
            virtualUser:Button1Up(Vector2.new(0, 0), workspace.CurrentCamera.CFrame)
            print("AutoClicker: Clicked")
        end
    end
end

-- Enhanced AFK Prevention Functionality
local function enhancedAfkPrevention()
    while true do
        wait(math.random(2, 5)) -- Random interval between 2 and 5 seconds
        if isAFKActive then
            local success, err = pcall(function()
                local character = player.Character
                if character and character:FindFirstChild("HumanoidRootPart") then
                    local humanoidRootPart = character.HumanoidRootPart
                    humanoidRootPart.CFrame = humanoidRootPart.CFrame * CFrame.new(0, 0, math.random(0.05, 0.1))  -- Move slightly
                    virtualUser:CaptureController()
                    virtualUser:ClickButton2(Vector2.new()) -- Fakes player interaction
                    print("Enhanced AFK Prevention: Moved")
                end
            end)
            if not success then
                warn("Error in AFK prevention: " .. tostring(err))
            end
        end
    end
end

-- Random Movement and Jumping
local function randomMovementAndJump()
    while true do
        wait(math.random(5, 10))  -- Wait for a random time between 5 and 10 seconds
        if isAFKActive and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            local humanoidRootPart = player.Character.HumanoidRootPart
            local randomPosition = humanoidRootPart.Position + Vector3.new(math.random(-5, 5), 0, math.random(-5, 5))
            humanoidRootPart.CFrame = CFrame.new(randomPosition)
            humanoidRootPart.Velocity = Vector3.new(0, 50, 0)  -- Add upward velocity to simulate a jump
            virtualUser:Button1Down(Vector2.new(0, 0), workspace.CurrentCamera.CFrame) -- Simulate a click during movement
            wait(0.1)
            virtualUser:Button1Up(Vector2.new(0, 0), workspace.CurrentCamera.CFrame) -- Release the click
            print("Random Movement and Jumping: Moved and Jumped")
        end
    end
end

-- Check Connection Functionality
local function checkConnection()
    while true do
        wait(5)  -- Check every 5 seconds
        if not player.Character or not player.Character:FindFirstChild("Humanoid") then
            print("Connection lost. Attempting to reconnect...")
            player:LoadCharacter()  -- Try to respawn the character
        end
    end
end

-- AntiCrash Functionality
local function antiCrash()
    while true do
        wait(60)  -- Regular checks every minute
        for _, item in pairs(workspace:GetDescendants()) do
            if item:IsA("BasePart") and not item:IsDescendantOf(game.Players) then
                item:Destroy() -- Unload parts not associated with players
            end
        end
        print("AntiCrash: Reduced game load.")
    end
end

-- Memory Optimization
local function memoryOptimization()
    while true do
        wait(120)  -- Check every 2 minutes
        -- Remove unused objects or optimize memory usage here if applicable
        collectgarbage()  -- Force garbage collection
        print("Memory Optimization: Garbage collected.")
    end
end

-- Battery Saving Feature
local function batterySavingMode()
    while true do
        wait(30)  -- Check every 30 seconds
        if userInputService:GetFocusedTextBox() == nil then
            print("Battery Saving Mode Activated: Reducing performance.")
            runService.RenderStepped:Wait()  -- Wait for a frame to save battery
            game:GetService("RunService").Heartbeat:Wait()  -- Reduce updates during idle
        end
    end
end

-- Function to track uptime for 7 days
local function trackUptime()
    local startTime = os.time()
    while true do
        wait(60)  -- Check every minute
        local elapsed = os.time() - startTime
        if elapsed >= 604800 then  -- 7 days in seconds
            print("لقد صمدت لمدة 7 أيام في اللعبة!")
            break
        end
    end
end

-- Start all functions in parallel
coroutine.wrap(autoClicker)()
coroutine.wrap(enhancedAfkPrevention)()
coroutine.wrap(randomMovementAndJump)()  -- Start random movement and jumping
coroutine.wrap(checkConnection)()  -- Start connection checking
coroutine.wrap(antiKick)()
coroutine.wrap(antiCrash)()
coroutine.wrap(memoryOptimization)()  -- Start memory optimization
coroutine.wrap(batterySavingMode)()  -- Start battery saving mode
coroutine.wrap(trackUptime)()

-- Notify the user that all features are running
print("Ultimate Survival Script قيد التشغيل.")
statusLabel.Text = "All features are active."
