-- Aluminium Menu для BloxStrike (Roblox)
-- Вставь этот код в LocalScript внутри StarterGui или выполни в игроке

local Players = game:GetService("Players")
local Player = Players.LocalPlayer
local Mouse = Player:GetMouse()

-- Создаём главный GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "AluminiumMenu"
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = Player:WaitForChild("PlayerGui")

-- Главное окно (640x420, скруглённые углы)
local Menu = Instance.new("Frame")
Menu.Name = "MainFrame"
Menu.Size = UDim2.new(0, 640, 0, 420)
Menu.Position = UDim2.new(0.5, -320, 0.5, -210) -- центр экрана
Menu.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Menu.BackgroundTransparency = 0
Menu.BorderSizePixel = 0
Menu.ClipsDescendants = true
Menu.Parent = ScreenGui

-- Скругление через UICorner
local Corner = Instance.new("UICorner")
Corner.CornerRadius = UDim.new(0, 28)
Corner.Parent = Menu

-- Тень для красоты (необязательно)
local Shadow = Instance.new("Shadow")
Shadow.Color = Color3.fromRGB(0, 0, 0)
Shadow.Transparency = 0.4
Shadow.Offset = Vector2.new(0, 8)
Shadow.Size = 20
Shadow.Parent = Menu

-- ========== HEADER ==========
local Header = Instance.new("Frame")
Header.Name = "Header"
Header.Size = UDim2.new(1, 0, 0, 64)
Header.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Header.BorderSizePixel = 0
Header.Parent = Menu

-- ЧЁРНАЯ ПОЛОСА (нижняя граница хедера)
local BottomLine = Instance.new("Frame")
BottomLine.Name = "BlackLine"
BottomLine.Size = UDim2.new(1, 0, 0, 4)
BottomLine.Position = UDim2.new(0, 0, 1, -4)
BottomLine.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
BottomLine.BorderSizePixel = 0
BottomLine.Parent = Header

-- Заголовок "Aluminium"
local Title = Instance.new("TextLabel")
Title.Name = "Title"
Title.Size = UDim2.new(0, 200, 1, 0)
Title.Position = UDim2.new(0, 20, 0, 0)
Title.BackgroundTransparency = 1
Title.Text = "Aluminium"
Title.TextColor3 = Color3.fromRGB(20, 20, 20)
Title.TextSize = 28
Title.TextXAlignment = Enum.TextXAlignment.Left
Title.Font = Enum.Font.GothamBold
Title.Parent = Header

-- Маленький бейдж "BLOXSTRIKE"
local Badge = Instance.new("TextLabel")
Badge.Name = "Badge"
Badge.Size = UDim2.new(0, 90, 0, 24)
Badge.Position = UDim2.new(0, 160, 0, 20)
Badge.BackgroundColor3 = Color3.fromRGB(235, 235, 235)
Badge.BackgroundTransparency = 0
Badge.Text = "BLOXSTRIKE"
Badge.TextColor3 = Color3.fromRGB(30, 30, 30)
Badge.TextSize = 13
Badge.TextXAlignment = Enum.TextXAlignment.Center
Badge.Font = Enum.Font.GothamMedium
Badge.BorderSizePixel = 0
local BadgeCorner = Instance.new("UICorner")
BadgeCorner.CornerRadius = UDim.new(0, 12)
BadgeCorner.Parent = Badge
Badge.Parent = Header

-- Правая часть: статус-точка
local StatusDot = Instance.new("Frame")
StatusDot.Name = "StatusDot"
StatusDot.Size = UDim2.new(0, 12, 0, 12)
StatusDot.Position = UDim2.new(1, -40, 0.5, -6)
StatusDot.BackgroundColor3 = Color3.fromRGB(46, 204, 113) -- зелёный
StatusDot.BorderSizePixel = 0
local DotCorner = Instance.new("UICorner")
DotCorner.CornerRadius = UDim.new(1, 0)
DotCorner.Parent = StatusDot
StatusDot.Parent = Header

-- Текст "ACTIVE" рядом с точкой
local StatusText = Instance.new("TextLabel")
StatusText.Name = "StatusText"
StatusText.Size = UDim2.new(0, 60, 0, 20)
StatusText.Position = UDim2.new(1, -110, 0.5, -10)
StatusText.BackgroundTransparency = 1
StatusText.Text = "ACTIVE"
StatusText.TextColor3 = Color3.fromRGB(80, 80, 80)
StatusText.TextSize = 13
StatusText.TextXAlignment = Enum.TextXAlignment.Right
StatusText.Font = Enum.Font.GothamMedium
StatusText.Parent = Header

-- ========== BODY (контент) ==========
local Body = Instance.new("Frame")
Body.Name = "Body"
Body.Size = UDim2.new(1, 0, 1, -64)
Body.Position = UDim2.new(0, 0, 0, 64)
Body.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Body.BorderSizePixel = 0
Body.Parent = Menu

-- Заголовок секции
local SectionLabel = Instance.new("TextLabel")
SectionLabel.Name = "SectionLabel"
SectionLabel.Size = UDim2.new(1, -40, 0, 28)
SectionLabel.Position = UDim2.new(0, 20, 0, 16)
SectionLabel.BackgroundTransparency = 1
SectionLabel.Text = "⚡ FEATURES"
SectionLabel.TextColor3 = Color3.fromRGB(40, 40, 40)
SectionLabel.TextSize = 18
SectionLabel.TextXAlignment = Enum.TextXAlignment.Left
SectionLabel.Font = Enum.Font.GothamBold
SectionLabel.Parent = Body

-- Сетка функций (4 фичи)
local Features = {
    {Name = "Aimbot", Default = true},
    {Name = "ESP", Default = false},
    {Name = "Wallhack", Default = true},
    {Name = "Fly", Default = false}
}

local Grid = Instance.new("Frame")
Grid.Name = "Grid"
Grid.Size = UDim2.new(1, -40, 0, 160)
Grid.Position = UDim2.new(0, 20, 0, 56)
Grid.BackgroundTransparency = 1
Grid.Parent = Body

-- UIListLayout для сетки (2 колонки)
local GridLayout = Instance.new("UIGridLayout")
GridLayout.CellSize = UDim2.new(0, 250, 0, 44)
GridLayout.CellPadding = UDim2.new(0, 20, 0, 12)
GridLayout.FillDirection = Enum.FillDirection.Horizontal
GridLayout.HorizontalAlignment = Enum.HorizontalAlignment.Left
GridLayout.VerticalAlignment = Enum.VerticalAlignment.Top
GridLayout.SortOrder = Enum.SortOrder.LayoutOrder
GridLayout.Parent = Grid

-- Создаём элементы
for _, data in ipairs(Features) do
    local Item = Instance.new("Frame")
    Item.Name = data.Name .. "Item"
    Item.Size = UDim2.new(0, 250, 0, 44)
    Item.BackgroundColor3 = Color3.fromRGB(248, 249, 251)
    Item.BorderSizePixel = 0
    local ItemCorner = Instance.new("UICorner")
    ItemCorner.CornerRadius = UDim.new(0, 12)
    ItemCorner.Parent = Item
    Item.Parent = Grid

    -- Чекбокс (имитация toggle)
    local Toggle = Instance.new("ImageLabel")
    Toggle.Name = "Toggle"
    Toggle.Size = UDim2.new(0, 20, 0, 20)
    Toggle.Position = UDim2.new(0, 12, 0.5, -10)
    Toggle.BackgroundColor3 = data.Default and Color3.fromRGB(30, 30, 30) or Color3.fromRGB(200, 200, 200)
    Toggle.BackgroundTransparency = 0
    local ToggleCorner = Instance.new("UICorner")
    ToggleCorner.CornerRadius = UDim.new(0, 6)
    ToggleCorner.Parent = Toggle
    -- Иконка галочки (если включено)
    if data.Default then
        local Check = Instance.new("TextLabel")
        Check.Size = UDim2.new(1, 0, 1, 0)
        Check.BackgroundTransparency = 1
        Check.Text = "✓"
        Check.TextColor3 = Color3.fromRGB(255, 255, 255)
        Check.TextSize = 18
        Check.TextXAlignment = Enum.TextXAlignment.Center
        Check.Font = Enum.Font.GothamBold
        Check.Parent = Toggle
    end
    Toggle.Parent = Item

    -- Название
    local Label = Instance.new("TextLabel")
    Label.Name = "Label"
    Label.Size = UDim2.new(1, -48, 1, 0)
    Label.Position = UDim2.new(0, 44, 0, 0)
    Label.BackgroundTransparency = 1
    Label.Text = data.Name
    Label.TextColor3 = Color3.fromRGB(25, 25, 25)
    Label.TextSize = 16
    Label.TextXAlignment = Enum.TextXAlignment.Left
    Label.Font = Enum.Font.GothamMedium
    Label.Parent = Item

    -- Статус (ON/OFF)
    local Status = Instance.new("TextLabel")
    Status.Name = "Status"
    Status.Size = UDim2.new(0, 44, 1, 0)
    Status.Position = UDim2.new(1, -52, 0, 0)
    Status.BackgroundTransparency = 1
    Status.Text = data.Default and "ON" or "OFF"
    Status.TextColor3 = data.Default and Color3.fromRGB(0, 180, 50) or Color3.fromRGB(180, 50, 50)
    Status.TextSize = 13
    Status.TextXAlignment = Enum.TextXAlignment.Right
    Status.Font = Enum.Font.GothamMedium
    Status.Parent = Item
end

-- Кнопка "Закрыть" (нижний правый угол)
local CloseBtn = Instance.new("TextButton")
CloseBtn.Name = "CloseBtn"
CloseBtn.Size = UDim2.new(0, 110, 0, 36)
CloseBtn.Position = UDim2.new(1, -130, 1, -52)
CloseBtn.BackgroundColor3 = Color3.fromRGB(235, 235, 235)
CloseBtn.Text = "✕ Закрыть"
CloseBtn.TextColor3 = Color3.fromRGB(40, 40, 40)
CloseBtn.TextSize = 15
CloseBtn.Font = Enum.Font.GothamMedium
CloseBtn.BorderSizePixel = 0
local BtnCorner = Instance.new("UICorner")
BtnCorner.CornerRadius = UDim.new(0, 10)
BtnCorner.Parent = CloseBtn
CloseBtn.Parent = Body

-- Обработчик закрытия
CloseBtn.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
end)

-- Перетаскивание окна (удобно)
local dragging = false
local dragStart
local startPos

Header.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = true
        dragStart = input.Position
        startPos = Menu.Position
    end
end)

Header.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = false
    end
end)

game:GetService("RunService").RenderStepped:Connect(function()
    if dragging then
        local mousePos = Mouse.ViewSizeX / 2
        local delta = Mouse.X - (mousePos - 320) -- хитро для центрирования
        -- Простой вариант: двигаем по смещению
        local offset = UDim2.new(0, Mouse.X - 320 - (Menu.AbsolutePosition.X - (Menu.AbsoluteSize.X / 2)), 0, Mouse.Y - 210 - (Menu.AbsolutePosition.Y - (Menu.AbsoluteSize.Y / 2)))
        Menu.Position = UDim2.new(0.5, offset.X.Offset, 0.5, offset.Y.Offset)
    end
end)

print("Aluminium Menu загружен для BloxStrike!")
