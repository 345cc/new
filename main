-- important var

local controller = game.Players["Enity_4x4"]
local Players = game:GetService("Players")
local bot = Players.LocalPlayer
local char = bot.Character or bot.CharacterAdded:Wait()
local RNG = Random.new(tick())
local MainEvent = game:GetService('ReplicatedStorage'):WaitForChild("MainEvent")



-- cfgs

local prefix = "!"

-- function

local ok = {}
local function getplayer(Name)
	Name = Name:lower():gsub(" ","")
	for _,x in next, Players:GetPlayers() do
		if x ~= bot then
			if x.Name:lower():match("^"..Name) then
				return x
			elseif x.DisplayName:lower():match("^"..Name) then
				return x
			elseif Name == "me" then
				return controller
			end
		end
	end
end

function rand180()
	return math.random(-180, 180)
end

local part = Instance.new("Part", workspace)
part.Position = Vector3.new(9999,9999,9999)
part.Size = Vector3.new(25,1,25)
part.Transparency = 0.2
part.Anchored = true

bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame = part.CFrame * CFrame.new(0,2,0)
-- control
controller.Chatted:Connect(function(msg)
	msg = msg:lower()
	if string.sub(msg,1,3) == "/e " then
		msg = string.sub(msg,4)
	end
	if string.sub(msg,1,1) == prefix then
		local cmd
		local space = string.find(msg," ")
		if space then
			cmd = string.sub(msg,2,space-1)
		else
			cmd = string.sub(msg,2)
		end
		if cmd == "test" then
			print("test")
		end
		if cmd == "fixposition" then
			bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame = part.CFrame * CFrame.new(0,2,0)
		end

		if cmd == "bringme" then
			bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame = controller.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame
		end
		if cmd == "fling" then
			local angle = 0
			local oldpos = game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame
			local Time = os.clock()
			local var = string.sub(msg,space+1)
			local target = getplayer(var)
			if target == nil then return end
			local TRootPart = target.Character:FindFirstChildOfClass("Humanoid").RootPart
			local THumanoid = target.Character:FindFirstChildOfClass("Humanoid")
			local Humanoid = char and char:FindFirstChildOfClass("Humanoid")
			--

			local THead = target.Character.Head

			--
			local RootPart = Humanoid and Humanoid.RootPart
			local FPos = function(BasePart, Pos, Ang)
				char:FindFirstChildOfClass("Humanoid").RootPart.CFrame = CFrame.new(BasePart.Position) * Pos * Ang
				char:SetPrimaryPartCFrame(CFrame.new(BasePart.Position) * Pos * Ang)
				char:FindFirstChildOfClass("Humanoid").RootPart.Velocity = Vector3.new(2^14,2^14,2^14)
				char:FindFirstChildOfClass("Humanoid").RootPart.RotVelocity = Vector3.new(2^14,2^14,2^14)
			end

			local SFBasePart = function(BasePart)
				local TimeToWait = 4
				local Time = tick()
				local Angle = 0

				repeat
					if RootPart and THumanoid then
						if BasePart.Velocity.Magnitude < 50 then
							Angle = Angle + 100

							FPos(BasePart, CFrame.new(0, 1.5, 0) + THumanoid.MoveDirection * BasePart.Velocity.Magnitude / 1.25, CFrame.Angles(math.rad(Angle),0 ,0))
							task.wait()

							FPos(BasePart, CFrame.new(0, -1.5, 0) + THumanoid.MoveDirection * BasePart.Velocity.Magnitude / 1.25, CFrame.Angles(math.rad(Angle), 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(2.25, 1.5, -2.25) + THumanoid.MoveDirection * BasePart.Velocity.Magnitude / 1.25, CFrame.Angles(math.rad(Angle), 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(-2.25, -1.5, 2.25) + THumanoid.MoveDirection * BasePart.Velocity.Magnitude / 1.25, CFrame.Angles(math.rad(Angle), 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(0, 1.5, 0) + THumanoid.MoveDirection,CFrame.Angles(math.rad(Angle), 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(0, -1.5, 0) + THumanoid.MoveDirection,CFrame.Angles(math.rad(Angle), 0, 0))
							task.wait()
						else
							FPos(BasePart, CFrame.new(0, 1.5, THumanoid.WalkSpeed), CFrame.Angles(math.rad(90), 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(0, -1.5, -THumanoid.WalkSpeed), CFrame.Angles(0, 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(0, 1.5, THumanoid.WalkSpeed), CFrame.Angles(math.rad(90), 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(0, 1.5, TRootPart.Velocity.Magnitude / 1.25), CFrame.Angles(math.rad(90), 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(0, -1.5, -TRootPart.Velocity.Magnitude / 1.25), CFrame.Angles(0, 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(0, 1.5, TRootPart.Velocity.Magnitude / 1.25), CFrame.Angles(math.rad(90), 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(0, -1.5, 0), CFrame.Angles(math.rad(90), 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(0, -1.5, 0), CFrame.Angles(0, 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(0, -1.5 ,0), CFrame.Angles(math.rad(-90), 0, 0))
							task.wait()

							FPos(BasePart, CFrame.new(0, -1.5, 0), CFrame.Angles(0, 0, 0))
							task.wait()
						end
					else
						break
					end
				until BasePart.Velocity.Magnitude > 500 or BasePart.Parent ~= target.Character or target.Parent ~= Players or not target.Character == TCharacter or THumanoid.Sit or Humanoid.Health <= 0 or tick() > Time + TimeToWait
			end


			Humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)

			if TRootPart and THead then
				if (TRootPart.CFrame.p - THead.CFrame.p).Magnitude > 5 then
					SFBasePart(THead)
				else
					SFBasePart(TRootPart)
				end
			elseif TRootPart and not THead then
				SFBasePart(TRootPart)
			elseif not TRootPart and THead then
				SFBasePart(target.Character.Head)
			else
				return print("Target is losing all body bro")
			end

			Humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
			workspace.CurrentCamera.CameraSubject = Humanoid

			repeat
				RootPart.CFrame = oldpos * CFrame.new(0, .5, 0)
				char:SetPrimaryPartCFrame(oldpos * CFrame.new(0, .5, 0))
				Humanoid:ChangeState("GettingUp")
				table.foreach(char:GetChildren(), function(_, x)
					if x:IsA("BasePart") then
						x.Velocity, x.RotVelocity = Vector3.new(), Vector3.new()
					end
				end)
				task.wait()
			until (RootPart.Position - oldpos.p).Magnitude < 25
		end
		if cmd == "rejoin" then
			game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, game.JobId, bot)
		end
		if cmd == "checkplayer" then
			local oldpos = game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame
			local Time = os.clock()
			local var = string.sub(msg,space+1)
			local target = getplayer(var)
			if target == nil then 
				game.ReplicatedStorage.DefaultChatSystemChatEvents.SayMessageRequest:FireServer(target.Name.. " is logged.", "All")
			end
			game.ReplicatedStorage.DefaultChatSystemChatEvents.SayMessageRequest:FireServer(target.Name.. " is on the server.", "All")
			bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame = controller.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame
			wait(2)
			bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame = oldpos
		end
		if cmd == "bring" then
			local var = string.sub(msg,space+1)
			local target = getplayer(var)
			local Humanoid = char:WaitForChild("Humanoid")
			if target == nil then end
			local TimeToWait = 15
			local Time = tick()
			local oldpos = char:FindFirstChildOfClass("Humanoid").RootPart.CFrame 
			local FPos = function(BasePart, Pos)
				char:FindFirstChildOfClass("Humanoid").RootPart.CFrame = CFrame.new(BasePart.Position) * Pos
				char:SetPrimaryPartCFrame(CFrame.new(BasePart.Position) * Pos )
			end
			for i = 1,4 do
				if target.Character:FindFirstChildOfClass("Humanoid").Health <= 15 then
					bot.Character:FindFirstChildOfClass("Humanoid"):UnequipTools()
					break
				else
					
				end
				bot.Character:FindFirstChildOfClass("Humanoid"):EquipTool(bot.Backpack["[Knife]"])
				local oldpos = bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame 
				bot.Character["[Knife]"]:Activate()
				wait(1.4)
				for i = 1,30 do
					if target.Character:FindFirstChildOfClass("Humanoid").Health <= 15 then
						break
					end
					FPos(target.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame, CFrame.new(0, 0, 0) + target.Character:FindFirstChildOfClass("Humanoid").MoveDirection * target.Character:FindFirstChildOfClass("Humanoid").RootPart.Velocity.Magnitude / math.random(16,20))
					task.wait()
				end
				bot.Character:FindFirstChildOfClass("Humanoid"):UnequipTools()
				bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame = oldpos
				wait(0.5)
			end
			if target.Character:FindFirstChildOfClass("Humanoid").Health >= 15 then
				print("failed to bring player (health error)")
			else
				
			end 
			repeat
				bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame = target.Character.Head.CFrame
				local args = {
					[1] = "Grabbing",
					[2] = false
				}
				game:GetService("ReplicatedStorage"):WaitForChild("MainEvent"):FireServer(unpack(args))
				game:GetService("RunService").Heartbeat:Wait()
			until target.Character:FindFirstChild("GRABBING_CONSTRAINT") or tick() > Time + TimeToWait
			bot.Character:FindFirstChildOfClass("Humanoid"):UnequipTools()
			for i = 1,20 do
				bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame = controller.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame
				task.wait()
			end
			local args = {
				[1] = "Grabbing",
				[2] = false
			}
			game:GetService("ReplicatedStorage"):WaitForChild("MainEvent"):FireServer(unpack(args))
			wait(0.5)
			bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame = oldpos
		end
		if cmd == "hurt" then
			local var = string.sub(msg,space+1)
			local target = getplayer(var)
			local Humanoid = char:WaitForChild("Humanoid")
			if target == nil then end
			local TimeToWait = 5
			local Time = tick()
			local oldpos = char:FindFirstChildOfClass("Humanoid").RootPart.CFrame 
			local FPos = function(BasePart, Pos)
				char:FindFirstChildOfClass("Humanoid").RootPart.CFrame = CFrame.new(BasePart.Position) * Pos
				char:SetPrimaryPartCFrame(CFrame.new(BasePart.Position) * Pos )
			end
			for i = 1,4 do
				if target.Character:FindFirstChildOfClass("Humanoid").Health <= 15 then
					bot.Character:FindFirstChildOfClass("Humanoid"):UnequipTools()
					break
				end
				bot.Character:FindFirstChildOfClass("Humanoid"):EquipTool(bot.Backpack["[Knife]"])
				local oldpos = bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame 
				bot.Character["[Knife]"]:Activate()
				wait(1.4)
				for i = 1,20 do
					if target.Character:FindFirstChildOfClass("Humanoid").Health <= 15 then
						break
					end
					FPos(target.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame, CFrame.new(0, 0, 0) + target.Character:FindFirstChildOfClass("Humanoid").MoveDirection * target.Character:FindFirstChildOfClass("Humanoid").RootPart.Velocity.Magnitude / math.random(16,20))
					game:GetService("RunService").Heartbeat:Wait()
				end
				bot.Character:FindFirstChildOfClass("Humanoid"):UnequipTools()
				bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame = oldpos
				wait(0.5)
			end
			bot.Character:FindFirstChildOfClass("Humanoid"):UnequipTools()
			bot.Character:FindFirstChildOfClass("Humanoid").RootPart.CFrame = oldpos
		end

	end
end)
