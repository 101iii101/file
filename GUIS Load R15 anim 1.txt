local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local Debris = game:GetService("Debris")

local Player = Players.LocalPlayer
local PlayerGui = game.CoreGui

local NotificationGui = Instance.new("ScreenGui")
NotificationGui.Name = "NotificationSystem"
NotificationGui.Parent = PlayerGui
NotificationGui.ResetOnSpawn = false

local activeNotifications = {}
local notificationCount = 0

local NOTIFICATION_WIDTH = 280
local NOTIFICATION_HEIGHT = 70
local NOTIFICATION_SPACING = 8
local SLIDE_DISTANCE = 350
local ANIMATION_SPEED = 0.6

local function createNotification(title, content, duration)
    notificationCount = notificationCount + 1

    local notificationFrame = Instance.new("Frame")
    notificationFrame.Name = "Notification_" .. notificationCount
    notificationFrame.Size = UDim2.new(0, NOTIFICATION_WIDTH, 0, NOTIFICATION_HEIGHT)
    notificationFrame.BackgroundColor3 = Color3.fromRGB(27, 27, 27)
    notificationFrame.BackgroundTransparency = 0.15
    notificationFrame.BorderSizePixel = 0
    notificationFrame.Parent = NotificationGui

    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 8)
    corner.Parent = notificationFrame

    local stroke = Instance.new("UIStroke")
    stroke.Color = Color3.fromRGB(60, 60, 60)
    stroke.Thickness = 1.2
    stroke.Transparency = 0.2
    stroke.Parent = notificationFrame

    local shadow = Instance.new("Frame")
    shadow.Size = UDim2.new(1, 4, 1, 4)
    shadow.Position = UDim2.new(0, -2, 0, -2)
    shadow.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    shadow.BackgroundTransparency = 0.85
    shadow.BorderSizePixel = 0
    shadow.ZIndex = notificationFrame.ZIndex - 1
    shadow.Parent = notificationFrame

    local shadowCorner = Instance.new("UICorner")
    shadowCorner.CornerRadius = UDim.new(0, 8)
    shadowCorner.Parent = shadow

    local titleLabel = Instance.new("TextLabel")
    titleLabel.Name = "Title"
    titleLabel.Size = UDim2.new(1, -16, 0, 22)
    titleLabel.Position = UDim2.new(0, 8, 0, 6)
    titleLabel.BackgroundTransparency = 1
    titleLabel.Text = title
    titleLabel.TextColor3 = Color3.fromRGB(240, 240, 240)
    titleLabel.TextSize = 16
    titleLabel.TextXAlignment = Enum.TextXAlignment.Left
    titleLabel.TextYAlignment = Enum.TextYAlignment.Center
    titleLabel.Font = Enum.Font.GothamSemibold
    titleLabel.Parent = notificationFrame

    local contentLabel = Instance.new("TextLabel")
    contentLabel.Name = "Content"
    contentLabel.Size = UDim2.new(1, -16, 0, 20)
    contentLabel.Position = UDim2.new(0, 8, 0, 30)
    contentLabel.BackgroundTransparency = 1
    contentLabel.Text = content
    contentLabel.TextColor3 = Color3.fromRGB(190, 190, 190)
    contentLabel.TextSize = 13
    contentLabel.TextXAlignment = Enum.TextXAlignment.Left
    contentLabel.TextYAlignment = Enum.TextYAlignment.Center
    contentLabel.Font = Enum.Font.GothamMedium
    contentLabel.Parent = notificationFrame

    local closeButton = Instance.new("TextButton")
    closeButton.Size = UDim2.new(1, 0, 1, 0)
    closeButton.Position = UDim2.new(0, 0, 0, 0)
    closeButton.BackgroundTransparency = 1
    closeButton.Text = ""
    closeButton.Parent = notificationFrame

    local yPosition = (#activeNotifications * (NOTIFICATION_HEIGHT + NOTIFICATION_SPACING)) + 50
    notificationFrame.Position = UDim2.new(1, SLIDE_DISTANCE, 0, yPosition)
    table.insert(activeNotifications, notificationFrame)

    local function updatePositions()
        for i, notification in ipairs(activeNotifications) do
            local newY = ((i - 1) * (NOTIFICATION_HEIGHT + NOTIFICATION_SPACING)) + 50
            local tweenInfo = TweenInfo.new(ANIMATION_SPEED, Enum.EasingStyle.Quart, Enum.EasingDirection.Out)
            local tween = TweenService:Create(notification, tweenInfo, {
                Position = UDim2.new(1, -NOTIFICATION_WIDTH - 20, 0, newY)
            })
            tween:Play()
        end
    end

    local slideInTween = TweenService:Create(notificationFrame, 
        TweenInfo.new(ANIMATION_SPEED, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
        {Position = UDim2.new(1, -NOTIFICATION_WIDTH - 20, 0, yPosition)}
    )
    slideInTween:Play()

    local function removeNotification()
        for i, notification in ipairs(activeNotifications) do
            if notification == notificationFrame then
                table.remove(activeNotifications, i)
                break
            end
        end

        local slideOutTween = TweenService:Create(notificationFrame,
            TweenInfo.new(ANIMATION_SPEED, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
            {Position = UDim2.new(1, SLIDE_DISTANCE, 0, notificationFrame.Position.Y.Offset)}
        )
        slideOutTween:Play()

        slideOutTween.Completed:Connect(function()
            notificationFrame:Destroy()
            updatePositions()
        end)
    end

    closeButton.MouseButton1Click:Connect(removeNotification)

    if duration and duration > 0 then
        task.wait(duration)
        if notificationFrame.Parent then
            removeNotification()
        end
    end
end

getgenv().Notify = function(options)
    local title = options.Title or "Notification"
    local content = options.Content or "No content provided"
    local duration = options.Duration or 5
    task.spawn(function()
        createNotification(title, content, duration)
    end)
end