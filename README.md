local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local player = Players.LocalPlayer

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "Snowhub"
ScreenGui.Parent = game:GetService("CoreGui")

local vinho = Color3.fromRGB(120, 0, 40)

local function createStyle(size)
    local Background = Instance.new("Frame", ScreenGui)
    Background.Size = UDim2.new(1,0,1,0)
    Background.BackgroundColor3 = Color3.fromRGB(0,0,0)
    Background.BackgroundTransparency = 1
    Background.BorderSizePixel = 0

    local Frame = Instance.new("Frame", Background)
    Frame.Size = size
    Frame.Position = UDim2.new(0.5,0,0.5,50)
    Frame.AnchorPoint = Vector2.new(0.5,0.5)
    Frame.BackgroundColor3 = Color3.fromRGB(20,10,15)
    Frame.BorderSizePixel = 0

    Instance.new("UICorner", Frame).CornerRadius = UDim.new(0,18)

    local Stroke = Instance.new("UIStroke", Frame)
    Stroke.Color = vinho
    Stroke.Thickness = 3
    Stroke.Transparency = 1

    return Background, Frame, Stroke
end

local function openAnim(bg, frame, stroke)
    TweenService:Create(bg, TweenInfo.new(0.4), {
        BackgroundTransparency = 0.3
    }):Play()

    TweenService:Create(frame, TweenInfo.new(0.5, Enum.EasingStyle.Quart), {
        Position = UDim2.new(0.5,0,0.5,0)
    }):Play()

    TweenService:Create(stroke, TweenInfo.new(0.5), {
        Transparency = 0
    }):Play()
end

local function closeAnim(bg, frame, stroke)
    TweenService:Create(frame, TweenInfo.new(0.4, Enum.EasingStyle.Quad), {
        Position = UDim2.new(0.5,0,0.5,50)
    }):Play()

    TweenService:Create(stroke, TweenInfo.new(0.3), {
        Transparency = 1
    }):Play()

    TweenService:Create(bg, TweenInfo.new(0.4), {
        BackgroundTransparency = 1
    }):Play()
end

local bg, frame, stroke = createStyle(UDim2.new(0,450,0,260))

local Title = Instance.new("TextLabel", frame)
Title.Size = UDim2.new(1,0,0,45)
Title.BackgroundTransparency = 1
Title.Text = "SNOW HUB"
Title.Font = Enum.Font.Bangers
Title.TextScaled = true
Title.TextColor3 = vinho

local Welcome = Instance.new("TextLabel", frame)
Welcome.Size = UDim2.new(1,-40,0,40)
Welcome.Position = UDim2.new(0,20,0,70)
Welcome.BackgroundTransparency = 1
Welcome.Text = "Bem-vindo, "..player.Name
Welcome.Font = Enum.Font.Bangers
Welcome.TextScaled = true
Welcome.TextColor3 = Color3.fromRGB(255,255,255)
Welcome.TextTransparency = 1

openAnim(bg, frame, stroke)

TweenService:Create(Welcome, TweenInfo.new(0.6), {
    TextTransparency = 0
}):Play()

local Btn1 = Instance.new("TextButton", frame)
Btn1.Size = UDim2.new(1,-60,0,45)
Btn1.Position = UDim2.new(0,30,0,120)
Btn1.Text = "RUBY PUBLIC"
Btn1.Font = Enum.Font.Bangers
Btn1.TextSize = 22
Btn1.TextColor3 = Color3.fromRGB(255,255,255)
Btn1.BackgroundColor3 = vinho
Btn1.BorderSizePixel = 0
Btn1.AutoButtonColor = false
Instance.new("UICorner", Btn1).CornerRadius = UDim.new(0,14)

local Btn2 = Btn1:Clone()
Btn2.Parent = frame
Btn2.Position = UDim2.new(0,30,0,175)
Btn2.Text = "SNOW PAiD"

Btn1.MouseButton1Click:Connect(function()
    closeAnim(bg, frame, stroke)
    task.wait(0.4)
    ScreenGui:Destroy()
    loadstring(game:HttpGet(
        "https://pastebin.com/raw/nrM7wSyf"
    ))()
end)

Btn2.MouseButton1Click:Connect(function()

    Btn2.BackgroundColor3 = Color3.fromRGB(60,0,20)
    Btn2.TextSize = 18

    for i = 10, 1, -1 do
        Btn2.Text = "Snow Paid\nExecutando em "..i.."s"
        task.wait(1)
    end

    closeAnim(bg, frame, stroke)
    task.wait(0.4)
    ScreenGui:Destroy()

    loadstring(game:HttpGet(
        "https://raw.githubusercontent.com/Snowbytes-cloud/snow-paid-2026/refs/heads/main/README.md"
    ))()

end)
