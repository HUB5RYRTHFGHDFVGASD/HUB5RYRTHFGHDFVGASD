local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("VBX HUB", "DarkTheme")

local Main = Window:NewTab("feKill")
local MainSection = Main:NewSection("feKill")
--fe kill
MainSection:NewButton("kill,bring", "ButtonInfo", function()
    loadstring("\108\111\97\100\115\116\114\105\110\103\40\103\97\109\101\58\72\116\116\112\71\101\116\40\39\104\116\116\112\115\58\47\47\112\97\115\116\101\98\105\110\46\99\111\109\47\114\97\119\47\68\56\117\81\76\49\109\84\39\41\41\40\41\10")()
end)
--inff
MainSection:NewButton("infiniteyield1", "ButtonInfo", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
end)

--fe drop item
MainSection:NewButton("fe drop item", "ButtonInfo", function()
    -- Gui to Lua
-- Version: 3.2

-- Instances:

local DropGUI = Instance.new("ScreenGui")
local main = Instance.new("Frame")
local DropTool = Instance.new("TextButton")
local Equip = Instance.new("TextButton")
local Version = Instance.new("TextButton")
local Cred = Instance.new("TextButton")

--Properties:

DropGUI.Name = "Drop GUI"
DropGUI.Parent = game.CoreGui
DropGUI.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

main.Name = "main"
main.Parent = DropGUI
main.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
main.Position = UDim2.new(0.0809101239, 0, 0.203790441, 0)
main.Size = UDim2.new(0, 150, 0, 128)
main.Active = true
main.Draggable = true

DropTool.Name = "Drop Tool"
DropTool.Parent = main
DropTool.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
DropTool.Position = UDim2.new(0.0597826242, 0, 0.119906127, 0)
DropTool.Size = UDim2.new(0, 55, 0, 50)
DropTool.Font = Enum.Font.SourceSans
DropTool.Text = "Drop"
DropTool.TextColor3 = Color3.fromRGB(0, 0, 0)
DropTool.TextScaled = true
DropTool.TextSize = 14.000
DropTool.TextWrapped = true
DropTool.MouseButton1Down:Connect(function()
	game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Parent = game.Workspace
end)

Equip.Name = "Equip"
Equip.Parent = main
Equip.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
Equip.Position = UDim2.new(0.55251956, 0, 0.119906083, 0)
Equip.Size = UDim2.new(0, 58, 0, 50)
Equip.Font = Enum.Font.SourceSans
Equip.Text = "Equip"
Equip.TextColor3 = Color3.fromRGB(0, 0, 0)
Equip.TextScaled = true
Equip.TextSize = 14.000
Equip.TextWrapped = true
Equip.MouseButton1Down:Connect(function()
	game.Players.LocalPlayer.Backpack:FindFirstChildOfClass("Tool").Parent = game.Players.LocalPlayer.Character
end)

Version.Name = "Version"
Version.Parent = main
Version.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
Version.Position = UDim2.new(0, 0, 0.999885917, 0)
Version.Size = UDim2.new(0, 151, 0, 34)
Version.Font = Enum.Font.SourceSans
Version.Text = "Version 1"
Version.TextColor3 = Color3.fromRGB(0, 0, 0)
Version.TextScaled = true
Version.TextSize = 14.000
Version.TextWrapped = true

Cred.Name = "Cred"
Cred.Parent = main
Cred.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
Cred.Position = UDim2.new(0, 0, -0.266169071, 0)
Cred.Size = UDim2.new(0, 151, 0, 34)
Cred.Font = Enum.Font.SourceSans
Cred.Text = "Script made by WarriorRoberr"
Cred.TextColor3 = Color3.fromRGB(0, 0, 0)
Cred.TextSize = 14.000
Cred.TextWrapped = true
end)

--INVISIBLITY
MainSection:NewButton("Invisibility", "ButtonInfo", function()
    --[[Invisibility Toggle

You can find the orginal concept here: https://v3rmillion.net/showthread.php?tid=544634

This method clones the character locally, teleports the real character to a safe location, then sets the character to the clone.
Basically, your real character is in the sky while you are on the ground.


Because of the way this works, games with a decent anti-cheat will fuck this up.
If you turn it off, you have to go to a safe place before going invisible.

Written by: BitingTheDust ; https://v3rmillion.net/member.php?action=profile&uid=1628149
]]
--Settings:
local ScriptStarted = false
local Keybind = "E" --Set to whatever you want, has to be the name of a KeyCode Enum.
local Transparency = true --Will make you slightly transparent when you are invisible. No reason to disable.
local NoClip = false --Will make your fake character no clip.

local Player = game:GetService("Players").LocalPlayer
local RealCharacter = Player.Character or Player.CharacterAdded:Wait()

local IsInvisible = false

RealCharacter.Archivable = true
local FakeCharacter = RealCharacter:Clone()
local Part
Part = Instance.new("Part", workspace)
Part.Anchored = true
Part.Size = Vector3.new(200, 1, 200)
Part.CFrame = CFrame.new(0, -500, 0) --Set this to whatever you want, just far away from the map.
Part.CanCollide = true
FakeCharacter.Parent = workspace
FakeCharacter.HumanoidRootPart.CFrame = Part.CFrame * CFrame.new(0, 5, 0)

for i, v in pairs(RealCharacter:GetChildren()) do
  if v:IsA("LocalScript") then
      local clone = v:Clone()
      clone.Disabled = true
      clone.Parent = FakeCharacter
  end
end
if Transparency then
  for i, v in pairs(FakeCharacter:GetDescendants()) do
      if v:IsA("BasePart") then
          v.Transparency = 0.7
      end
  end
end
local CanInvis = true
function RealCharacterDied()
  CanInvis = false
  RealCharacter:Destroy()
  RealCharacter = Player.Character
  CanInvis = true
  isinvisible = false
  FakeCharacter:Destroy()
  workspace.CurrentCamera.CameraSubject = RealCharacter.Humanoid

  RealCharacter.Archivable = true
  FakeCharacter = RealCharacter:Clone()
  Part:Destroy()
  Part = Instance.new("Part", workspace)
  Part.Anchored = true
  Part.Size = Vector3.new(200, 1, 200)
  Part.CFrame = CFrame.new(9999, 9999, 9999) --Set this to whatever you want, just far away from the map.
  Part.CanCollide = true
  FakeCharacter.Parent = workspace
  FakeCharacter.HumanoidRootPart.CFrame = Part.CFrame * CFrame.new(0, 5, 0)

  for i, v in pairs(RealCharacter:GetChildren()) do
      if v:IsA("LocalScript") then
          local clone = v:Clone()
          clone.Disabled = true
          clone.Parent = FakeCharacter
      end
  end
  if Transparency then
      for i, v in pairs(FakeCharacter:GetDescendants()) do
          if v:IsA("BasePart") then
              v.Transparency = 0.7
          end
      end
  end
 RealCharacter.Humanoid.Died:Connect(function()
 RealCharacter:Destroy()
 FakeCharacter:Destroy()
 end)
 Player.CharacterAppearanceLoaded:Connect(RealCharacterDied)
end
RealCharacter.Humanoid.Died:Connect(function()
 RealCharacter:Destroy()
 FakeCharacter:Destroy()
 end)
Player.CharacterAppearanceLoaded:Connect(RealCharacterDied)
local PseudoAnchor
game:GetService "RunService".RenderStepped:Connect(
  function()
      if PseudoAnchor ~= nil then
          PseudoAnchor.CFrame = Part.CFrame * CFrame.new(0, 5, 0)
      end
       if NoClip then
      FakeCharacter.Humanoid:ChangeState(11)
       end
  end
)

PseudoAnchor = FakeCharacter.HumanoidRootPart
local function Invisible()
  if IsInvisible == false then
      local StoredCF = RealCharacter.HumanoidRootPart.CFrame
      RealCharacter.HumanoidRootPart.CFrame = FakeCharacter.HumanoidRootPart.CFrame
      FakeCharacter.HumanoidRootPart.CFrame = StoredCF
      RealCharacter.Humanoid:UnequipTools()
      Player.Character = FakeCharacter
      workspace.CurrentCamera.CameraSubject = FakeCharacter.Humanoid
      PseudoAnchor = RealCharacter.HumanoidRootPart
      for i, v in pairs(FakeCharacter:GetChildren()) do
          if v:IsA("LocalScript") then
              v.Disabled = false
          end
      end

      IsInvisible = true
  else
      local StoredCF = FakeCharacter.HumanoidRootPart.CFrame
      FakeCharacter.HumanoidRootPart.CFrame = RealCharacter.HumanoidRootPart.CFrame
     
      RealCharacter.HumanoidRootPart.CFrame = StoredCF
     
      FakeCharacter.Humanoid:UnequipTools()
      Player.Character = RealCharacter
      workspace.CurrentCamera.CameraSubject = RealCharacter.Humanoid
      PseudoAnchor = FakeCharacter.HumanoidRootPart
      for i, v in pairs(FakeCharacter:GetChildren()) do
          if v:IsA("LocalScript") then
              v.Disabled = true
          end
      end
      IsInvisible = false
  end
end

game:GetService("UserInputService").InputBegan:Connect(
  function(key, gamep)
      if gamep then
          return
      end
      if key.KeyCode.Name:lower() == Keybind:lower() and CanInvis and RealCharacter and FakeCharacter then
          if RealCharacter:FindFirstChild("HumanoidRootPart") and FakeCharacter:FindFirstChild("HumanoidRootPart") then
              Invisible()
          end
      end
  end
)
local Sound = Instance.new("Sound",game:GetService("SoundService"))
Sound.SoundId = "rbxassetid://232127604"
Sound:Play()
game:GetService("StarterGui"):SetCore("SendNotification",{["Title"] = "Invisible Toggle Loaded",["Text"] = "Press "..Keybind.." to become change visibility.",["Duration"] = 20,["Button1"] = "Okay."})
end)
--FE FLING
local Main = Window:NewTab("feFLING")
local MainSection = Main:NewSection("feFLING")
--REALGUN
MainSection:NewButton("REALGUN", "CODE IN DC", function()
local HatChar = game.Players.LocalPlayer.Character






HumanDied = false
local reanim
function noplsmesh(hat)
_G.OldCF=workspace.Camera.CFrame
oldchar=game.Players.LocalPlayer.Character
game.Players.LocalPlayer.Character=workspace[game.Players.LocalPlayer.Name]
for i,v in next, workspace[game.Players.LocalPlayer.Name][hat]:GetDescendants() do
if v:IsA('Mesh') or v:IsA('SpecialMesh') then
v:Remove()
end
end

end
_G.ClickFling=false -- Set this to true if u want.
loadstring(game:HttpGet(('https://raw.githubusercontent.com/OofHead-FE/nexo-before-deleted/main/NexoPD'),true))()



IT = Instance.new
CF = CFrame.new
VT = Vector3.new
RAD = math.rad
C3 = Color3.new
UD2 = UDim2.new
BRICKC = BrickColor.new
ANGLES = CFrame.Angles
EULER = CFrame.fromEulerAnglesXYZ
COS = math.cos
ACOS = math.acos
SIN = math.sin
ASIN = math.asin
ABS = math.abs
MRANDOM = math.random
FLOOR = math.floor

speed = 1
sine = 1
srv = game:GetService('RunService')

function hatset(yes,part,c1,c0,nm)
reanim[yes].Handle.AccessoryWeld.Part1=reanim[part]
reanim[yes].Handle.AccessoryWeld.C1=c1 or CFrame.new()
reanim[yes].Handle.AccessoryWeld.C0=c0 or CFrame.new()--3bbb322dad5929d0d4f25adcebf30aa5
if nm==true then
noplsmesh(yes)
end
end

--put the hat script converted below

reanim = game.Players.LocalPlayer.Character.CWExtra.NexoPD
RJ = reanim.HumanoidRootPart.RootJoint
RS = reanim.Torso['Right Shoulder']
LS = reanim.Torso['Left Shoulder']
RH = reanim.Torso['Right Hip']
LH = reanim.Torso['Left Hip']
Root = reanim.HumanoidRootPart
NECK = reanim.Torso.Neck
NECK.C0 = CF(0,1,0)*ANGLES(RAD(0),RAD(0),RAD(0))
NECK.C1 = CF(0,-0.5,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RJ.C1 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RJ.C0 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RS.C1 = CF(-0,0.5,0)*ANGLES(RAD(0),RAD(0),RAD(0))
LS.C1 = CF(0,0.5,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RH.C1 = CF(0.5,1,0)*ANGLES(RAD(0),RAD(0),RAD(0))
LH.C1 = CF(-0.5,1,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RH.C0 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
LH.C0 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
RS.C0 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))
LS.C0 = CF(0,0,0)*ANGLES(RAD(0),RAD(0),RAD(0))

Mode='1'

mousechanger=game.Players.LocalPlayer:GetMouse().KeyDown:Connect(function(k)
if k == 'f' then-- first mode
Mode='1'
elseif k == 'r' then-- first mode
Mode='2'
end
end)



attacklol=game.Players.LocalPlayer:GetMouse().Button1Down:Connect(function()
if Mode == '1' then
Mode='Attack0'
wait(0.07) -- time of attack u can edit this
Mode='Attack1'
wait(.1)
Mode='Attack3'
wait(.2)
Mode ='1'
elseif Mode == '2' then
Mode='Attack0'
wait(0.07) -- time of attack u can edit this
Mode='Attack1'
wait(.1)
Mode='Attack3'
wait(.2)
Mode ='2'
end
end)

reanim['Necklace'].Handle.AccessoryWeld.C0 = reanim['Necklace'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),0+0*math.cos(sine/13),1.7+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
reanim['rol_icebrainAccessory'].Handle.AccessoryWeld.C0 = reanim['rol_icebrainAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),2.6+0*math.cos(sine/13),1.7+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
reanim['Pink Hair'].Handle.AccessoryWeld.C0 = reanim['Pink Hair'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),4+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
reanim['LavanderHair'].Handle.AccessoryWeld.C0 = reanim['LavanderHair'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),-1.5+0*math.cos(sine/13),5.5+0*math.cos(sine/13))*ANGLES(RAD(90+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
reanim['Pal Hair'].Handle.AccessoryWeld.C0 = reanim['Pal Hair'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),-1.5+0*math.cos(sine/13),1.5+0*math.cos(sine/13))*ANGLES(RAD(90+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
reanim['Robloxclassicred'].Handle.AccessoryWeld.C0 = reanim['Robloxclassicred'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
reanim['Kate Hair'].Handle.AccessoryWeld.C0 = reanim['Kate Hair'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),-1.5+0*math.cos(sine/13),3.5+0*math.cos(sine/13))*ANGLES(RAD(90+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
coroutine.wrap(function()
hatset('Necklace','Right Arm',CFrame.new(),reanim['Necklace'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),0+0*math.cos(sine/13),1.7+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),1),true)
hatset('rol_icebrainAccessory','Right Arm',CFrame.new(),reanim['rol_icebrainAccessory'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),2.6+0*math.cos(sine/13),1.7+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),1),true)
hatset('Pink Hair','Right Arm',CFrame.new(),reanim['Pink Hair'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),4+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),1),true)
hatset('LavanderHair','Right Arm',CFrame.new(),reanim['LavanderHair'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),-1.5+0*math.cos(sine/13),5.5+0*math.cos(sine/13))*ANGLES(RAD(90+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),1),true)
hatset('Kate Hair','Right Arm',CFrame.new(),reanim['Kate Hair'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),-1.5+0*math.cos(sine/13),3.5+0*math.cos(sine/13))*ANGLES(RAD(90+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),1),true)
hatset('Pal Hair','Right Arm',CFrame.new(),reanim['Pal Hair'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),-1.5+0*math.cos(sine/13),1.5+0*math.cos(sine/13))*ANGLES(RAD(90+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),1),true)
hatset('Robloxclassicred','Right Arm',CFrame.new(),reanim['Robloxclassicred'].Handle.AccessoryWeld.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),1),true)
while true do -- anim changer
if HumanDied then mousechanger:Disconnect() attacklol:Disconnect() break end
sine = sine + speed
local rlegray = Ray.new(reanim["Right Leg"].Position + Vector3.new(0, 0.5, 0), Vector3.new(0, -2, 0))
local rlegpart, rlegendPoint = workspace:FindPartOnRay(rlegray, char)
local llegray = Ray.new(reanim["Left Leg"].Position + Vector3.new(0, 0.5, 0), Vector3.new(0, -2, 0))
local llegpart, llegendPoint = workspace:FindPartOnRay(llegray, char)
local rightvector = (Root.Velocity * Root.CFrame.rightVector).X + (Root.Velocity * Root.CFrame.rightVector).Z
local lookvector = (Root.Velocity * Root.CFrame.lookVector).X + (Root.Velocity * Root.CFrame.lookVector).Z
if lookvector > reanim.Humanoid.WalkSpeed then
lookvector = reanim.Humanoid.WalkSpeed
end
if lookvector < -reanim.Humanoid.WalkSpeed then
lookvector = -reanim.Humanoid.WalkSpeed
end
if rightvector > reanim.Humanoid.WalkSpeed then
rightvector = reanim.Humanoid.WalkSpeed
end
if rightvector < -reanim.Humanoid.WalkSpeed then
rightvector = -reanim.Humanoid.WalkSpeed
end
local lookvel = lookvector / reanim.Humanoid.WalkSpeed
local rightvel = rightvector / reanim.Humanoid.WalkSpeed
if Mode == '1' then
if Root.Velocity.y > 1 then -- jump
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RS.C0 = RS.C0:Lerp(CF(3+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(95+0*math.sin(sine/13))),.3)
LS.C0 = LS.C0:Lerp(CF(-3+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(-85+0*math.sin(sine/13))),.3)
RH.C0 = RH.C0:Lerp(CF(1+0*math.cos(sine/13),-0.6+-0.1*math.cos(sine/13),-0.5+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
LH.C0 = LH.C0:Lerp(CF(-1+0*math.cos(sine/13),-0.89+-0.1*math.cos(sine/13),0.3+0*math.cos(sine/13))*ANGLES(RAD(-15+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
elseif Root.Velocity.y < -1 then -- fall
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-4+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RS.C0 = RS.C0:Lerp(CF(3+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(130+0*math.sin(sine/13))),.3)
LS.C0 = LS.C0:Lerp(CF(-3+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(-118+0*math.sin(sine/13))),.3)
RH.C0 = RH.C0:Lerp(CF(1+0*math.cos(sine/13),-0.6+-0.1*math.cos(sine/13),-0.5+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
LH.C0 = LH.C0:Lerp(CF(-1+0*math.cos(sine/13),-0.89+-0.1*math.cos(sine/13),0.3+0*math.cos(sine/13))*ANGLES(RAD(-15+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
elseif Root.Velocity.Magnitude < 2 then -- idle

NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RS.C0 = RS.C0:Lerp(CF(3+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(61+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(-51+0*math.sin(sine/13))),.3)
LS.C0 = LS.C0:Lerp(CF(-1.5+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),-2+0.1*math.cos(sine/13))*ANGLES(RAD(56+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(1+0*math.sin(sine/13))),.3)
RH.C0 = RH.C0:Lerp(CF(1+0*math.cos(sine/13),-1+-0.1*math.cos(sine/13)+(rlegendPoint.Y+1-reanim['Right Leg'].Position.Y),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(-6+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
LH.C0 = LH.C0:Lerp(CF(-1+0*math.cos(sine/13),-1+-0.1*math.cos(sine/13)+(llegendPoint.Y+1-reanim['Left Leg'].Position.Y),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(23+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
elseif Root.Velocity.Magnitude < 200 then -- walk

NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RS.C0 = RS.C0:Lerp(CF(3+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(61+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(-51+0*math.sin(sine/13))),.3)
LS.C0 = LS.C0:Lerp(CF(-1.5+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),-2+0.1*math.cos(sine/13))*ANGLES(RAD(56+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(1+0*math.sin(sine/13))),.3)
RH.C0 = RH.C0:Lerp(CF(1+0*math.cos(sine/8),-1+0.5*math.cos(sine/8),0+0*math.cos(sine/8))*ANGLES(RAD(0*1+50*math.sin(sine/8))*lookvel,RAD(0+0*math.cos(sine/8)),RAD(0+25*math.sin(sine/8))*rightvel),.3)
LH.C0 = LH.C0:Lerp(CF(-1+0*math.cos(sine/8),-1+-0.5*math.cos(sine/8),0+0*math.cos(sine/8))*ANGLES(RAD(0*1+-50*math.sin(sine/8))*lookvel,RAD(0+0*math.cos(sine/8)),RAD(0+-25*math.sin(sine/8))*rightvel),.3)
end
elseif Mode == '2' then
if Root.Velocity.y > 1 then -- jump
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-15+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RS.C0 = RS.C0:Lerp(CF(1.5+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(43+0*math.sin(sine/13))),.3)
LS.C0 = LS.C0:Lerp(CF(-1.5+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(-51+0*math.sin(sine/13))),.3)
RH.C0 = RH.C0:Lerp(CF(1+0*math.cos(sine/13),-1+-0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-24+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
LH.C0 = LH.C0:Lerp(CF(-1+0*math.cos(sine/13),-1+-0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(23+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
elseif Root.Velocity.y < -1 then -- fall
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(12+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RS.C0 = RS.C0:Lerp(CF(1.5+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(121+0*math.sin(sine/13))),.3)
LS.C0 = LS.C0:Lerp(CF(-1.5+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(-122+0*math.sin(sine/13))),.3)
RH.C0 = RH.C0:Lerp(CF(1+0*math.cos(sine/13),-1+-0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(24+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
LH.C0 = LH.C0:Lerp(CF(-1+0*math.cos(sine/13),-1+-0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-24+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
elseif Root.Velocity.Magnitude < 2 then -- idle
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RS.C0 = RS.C0:Lerp(CF(1.5+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(212+14*math.cos(sine/13)),RAD(0+12*math.cos(sine/13)),RAD(0+0*math.sin(sine/13))),.3)
LS.C0 = LS.C0:Lerp(CF(-1.5+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(-51+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(39+14*math.sin(sine/13))),.3)
RH.C0 = RH.C0:Lerp(CF(1+0*math.cos(sine/13),-1+-0.1*math.cos(sine/13)+(rlegendPoint.Y+1-reanim['Right Leg'].Position.Y),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
LH.C0 = LH.C0:Lerp(CF(-1+0*math.cos(sine/13),-1+-0.1*math.cos(sine/13)+(llegendPoint.Y+1-reanim['Left Leg'].Position.Y),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
elseif Root.Velocity.Magnitude < 200 then -- walk
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RS.C0 = RS.C0:Lerp(CF(1.5+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(212+14*math.cos(sine/13)),RAD(0+12*math.cos(sine/13)),RAD(0+0*math.sin(sine/13))),.3)
LS.C0 = LS.C0:Lerp(CF(-1.5+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),0+0.1*math.cos(sine/13))*ANGLES(RAD(-51+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(39+14*math.sin(sine/13))),.3)
RH.C0 = RH.C0:Lerp(CF(1+0*math.cos(sine/8),-1+0.5*math.cos(sine/8),0+0*math.cos(sine/8))*ANGLES(RAD(0*1+50*math.sin(sine/8))*lookvel,RAD(0+0*math.cos(sine/8)),RAD(0+25*math.sin(sine/8))*rightvel),.3)
LH.C0 = LH.C0:Lerp(CF(-1+0*math.cos(sine/8),-1+-0.5*math.cos(sine/8),0+0*math.cos(sine/8))*ANGLES(RAD(0*1+-50*math.sin(sine/8))*lookvel,RAD(0+0*math.cos(sine/8)),RAD(0+-25*math.sin(sine/8))*rightvel),.3)

end
elseif Mode == 'Attack0' then --attack clerp 
NECK.C0 = NECK.C0:Lerp(CF(0+0*math.cos(sine/13),1+0*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RJ.C0 = RJ.C0:Lerp(CF(0+0*math.cos(sine/13),0+0.1*math.cos(sine/13),0+0*math.cos(sine/13))*ANGLES(RAD(-4+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
RS.C0 = RS.C0:Lerp(CF(0.6+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),-1.5+0.1*math.cos(sine/13))*ANGLES(RAD(85+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(1+0*math.sin(sine/13))),.3)
LS.C0 = LS.C0:Lerp(CF(-0.5+0.1*math.sin(sine/13),0.5+0.1*math.sin(sine/13),-5+0.1*math.cos(sine/13))*ANGLES(RAD(92+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.sin(sine/13))),.3)
RH.C0 = RH.C0:Lerp(CF(1+0*math.cos(sine/13),-0.6+-0.1*math.cos(sine/13),-0.5+0*math.cos(sine/13))*ANGLES(RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)
LH.C0 = LH.C0:Lerp(CF(-1+0*math.cos(sine/13),-0.89+-0.1*math.cos(sine/13),0.3+0*math.cos(sine/13))*ANGLES(RAD(-15+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13)),RAD(0+0*math.cos(sine/13))),.3)

elseif Mode == 'Attack1' then --attack clerp 
elseif Mode == 'Attack3' then --attack clerp 


end
srv.RenderStepped:Wait()
end
end)()
--template by fx 8320
end)

--all Fling script

MainSection:NewButton("Pendulum Hubs", "ButtonInfo", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Tescalus/Pendulum-Hubs-Source/main/Pendulum%20Hub%20V5.lua"))()
end)



--FE Gaint

MainSection:NewButton("FE Gaint", "", function()
    loadstring(game:HttpGet("https://🤡🤡🤡🤡🤡🤡🤡.tk/scripts/just_grass_giant.lua"))()
end)

MainSection:NewButton("FE Gaming setup", "", function()
    loadstring(game:HttpGet(('https://pastebin.com/raw/9qnY2Fwp'),true))()
end)


--Fe DinoBlox


MainSection:NewButton("Fe DinoBlox", "code in discord", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/PYXDYT/DinoBlox/main/FE%20Script'),true))()
end)
