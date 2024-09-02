# gm_proxi

### _G.proxi

<details>
<summary>Base Lib</summary>

`DEBUG` \
A boolean representing whether or not the module is in debug mode

`_R` \
A reference to the debug registry

`FRAME_UNDEFINED` \
For use in the FrameStageNotify hooks \
Value of -1

`FRAME_START` \
For use in the FrameStageNotify hooks \
Value of 0

`FRAME_NET_UPDATE_START` \
For use in the FrameStageNotify hooks \
Value of 1

`FRAME_NET_UPDATE_POSTDATAUPDATE_START` \
For use in the FrameStageNotify hooks \
Value of 2

`FRAME_NET_UPDATE_POSTDATAUPDATE_END` \
For use in the FrameStageNotify hooks \
Value of 3

`FRAME_NET_UPDATE_END` \
For use in the FrameStageNotify hooks \
Value of 4

`FRAME_RENDER_START` \
For use in the FrameStageNotify hooks \
Value of 5

`FRAME_RENDER_END` \
For use in the FrameStageNotify hooks \
Value of 6

`DisableAnimInterp(bool Disable)` \
Enables/Disables interpolation via CSequenceTransitioner::CheckForSequenceChange

`Disconnect(string DisconnectReason)` \
Disconnects from the server with a custom message

`StartPrediction(CUserCmd Command)` \
Starts engine prediction with the provided CUserCmd

`EndPrediction()` \
Stops engine prediction

`FullUpdate()` \
Forces a full network update

`number GetChokedCommands()` \
Returns the amount of choked/lost packets/commands

`ConVar GetConVar(string Name)` \
Alternative to _G.GetConVar

`number GetFlowIncoming()` \
Returns the incoming data latency of the net channel

`number GetFlowOutgoing()` \
Returns the outgoing data latency of the net channel

`SetPredictionAngles(Angle PredictionAngles)` \
Sets local view angles to be used during prediction

`Angle GetPredictionAngles()` \
Returns local view angles to be used during prediction

`SetSequenceNumber(number SequenceNumber)` \
Sets outgoing sequence number on the net channel

`number GetSequenceNumber()` \
Returns outgoing sequence number on the net channel

`SetViewAngles(Angle ViewAngles)` \
Sets view angles directly in the engine

`Angle GetViewAngles()` \
Returns view angles used by the engine

`bool RunOnClient(string Code, string Identifier = "[C]", bool HandleError = true)` \
Alternative to _G.RunString on client state \
Returns `true` on success, `false` on error

`bool RunOnMenu(string Code, string Identifier = "[C]", bool HandleError = true)` \
Alternative to _G.RunString on menu state \
Returns `true` on success, `false` on error

`SendConsoleCommand(string Command)` \
Runs a concommand on the server without running it on the client

`SendLuaError(string Error)` \
Sends a Lua Error event to the server without throwing an error on the client

`SetCurTime(number Time)` \
Spoofs _G.CurTime to return the given number until the next tick

`SetFrameTime(number Time)` \
Spoofs _G.FrameTime and _G.RealFrameTime to return the given number until the next tick

</details>

<details>
<summary>Debug Lib</summary>

`string, any getupvalue(function Function, number Index)` \
Same as _G.debug.getupvalue

`string setupvalue(function Function, number Index, any Value)` \
Same as _G.debug.setupvalue

`string, any getlocal(thread Thread = CurrentThread, number Level, number Index)` \
Same as _G.debug.getlocal

`string setlocal(thread Thread = CurrentThread, number Level, number Index, any Value)` \
Same as _G.debug.setlocal

`table getinfo(function FunctionOrStackLevel, string Fields = "flnSu", function Function)` \
Same as _G.debug.getinfo

`table getmetatable(any Object)` \
Same as _G.debug.getmetatable

</details>

<details>
<summary>Net Lib</summary>

`bool Start(string MessageName)` \
Same as _G.net.Start

`SendToServer()` \
Same as _G.net.SendToServer

`string NetworkIDToString(number ID)` \
Same as _G.util.NetworkIDToString

`number NetworkStringToID(string NetworkString)` \
Same as _G.util.NetworkStringToID

`WriteBit(bool Value)` \
Same as _G.net.WriteBit

`WriteBool(bool Value)` \
Same as _G.net.WriteBool

`WriteColor(table Color, bool WriteAlpha)` \
Same as _G.net.WriteColor

`WriteFloat(number Value)` \
Same as _G.net.WriteFloat

`WriteInt(number Value, number BitCount)` \
Same as _G.net.WriteInt

`WriteUInt(number Value, number BitCount)` \
Same as _G.net.WriteUInt

`WriteString(string Value)` \
Same as _G.net.WriteString

`WriteEntity(Entity Entity)` \
Same as _G.net.WriteEntity

`WriteVector(Vector Vector)` \
Same as _G.net.WriteVector

`WriteNormal(Vector Normal)` \
Same as _G.net.WriteVector \
Does not normalize the Vector

`WriteAngle(Angle Angle)` \
Same as _G.net.WriteAngle

`WriteMatrix(VMatrix Matrix)` \
Same as _G.net.WriteMatrix \
Temporarily disabled, does not write anything

</details>

### Registry Changes

<details>
<summary>Entity</summary>

`any GetDTNetVar(string NetVar, number Force)` \
Returns a data entry from the entity's network variable datatable \
The values for Force are:

| Value | Type |
| --- | --- |
| 0 | Integer |
| 1 | Float |
| 2 | Vector |
| 3 | Vector2 |
| 4 | String |
| 5 | Entity |

`SetDTNetVar(string NetVar, any Value)` \
Sets a data entry on the entity's network variable datatable to the given value

`SetInterpolationEnabled(bool Enabled)` \
Sets whether or not this entity should be interpolated

</details>

<details>
<summary>CUserCmd</summary>

`bool GetInWorldClicker()` \
Returns if the command is using world clicker

`SetInWorldClicker(bool WorldClicker)` \
Sets whether or not the command is using world clicker

`Vector GetWorldClickerAngles()` \
Returns the world clicking direction of the command

`SetWorldClickerAngles(Vector Angles)` \
Sets the world clicking direction of the command

`SetCommandNumber(number CommandNumber)` \
Sets the command number on the command

`SetTickCount(number TickCount)` \
Sets the tick count on the command

`number GetRandomSeed()` \
Returns the random seed of the command

`SetRandomSeed(number RandomSeed)` \
Sets the random seed of the command \
Internally moves command number forward until desired seed is reached

`bool GetIsTyping()` \
Returns if the command is set to be in the typing (Chatbox open) state

`SetIsTyping(bool Type)` \
Sets the typing (Chatbox open) state of the command

`bool HasBeenPredicted()` \
Returns if the command has already been predicted

`bool IsKeyCodeDown(number KeyCode)` \
Returns if a key code is being pressed

`AddKeyCode(number KeyCode)` \
Adds a key code to the command's pressed key list \
There is a limit of 5 keys being pressed for any given command. If all slots are full, the first slot will be overridden

`RemoveKeyCode(number KeyCode)` \
Removes a key come from the command's pressed key list

</details>

<details>
<summary>ConVar</summary>

`SendValue(any Value)` \
Spoofs a convar change event on the server \
Accepted value types are: `string`, `number`, `bool`, `Angle`, `Vector`

`SetFlags(number Flags)` \
Force sets the flags on the convar

`ForceHasMin(bool HasMin)` \
Force whether or not the convar has a minimum value

`ForceHasMax(bool HasMax)` \
Force whether or not the convar has a maximum value

`ForceMin(number Min)` \
Forces the minimum value of the convar to the given value

`ForceMax(number Max)` \
Forces the maximum value of the convar to the given value

`ForceInt(number Integer)` \
Forces the value of the convar to the given integer

`ForceFloat(number Float)` \
Forces the value of the convar to the given float

`ForceBool(bool Value)` \
Forces the value of the convar to the given bool

`ForceString(string Value)` \
Forces the value of the convar to the given string

</details>

<details>
<summary>proxi_bf_read</summary>

`Seek(number Location)` \
Sets the buffer front to the given location

`SeekRelative(number Location)` \
Sets the buffer front to the given location

`Reset()` \
Resets the buffer to the beginning

`number GetBitsLeft()` \
Returns the amount of bits until the end of the buffer

`number GetBytesLeft()` \
Returns the amount of bytes until the end of the buffer

`number GetBitsRead()` \
Returns the amount of bits read from the buffer so far

`number GetBytesRead()` \
Returns the amount of bytes read from the buffer so far

`number GetCurBit()` \
Returns the current bit index in the buffer

`number ReadBit()` \
Reads a bit from the buffer

`bool ReadBit()` \
Reads a bool from the buffer

`number ReadByte()` \
Reads a byte (8 bits) from the buffer

`number ReadWord()` \
Reads a word (16 bits) from the buffer

`number ReadFloat()` \
Reads a float (32 bits) from the buffer

`number ReadDouble()` \
Reads a double (64 bits) from the buffer

`number ReadInt(number BitCount)` \
Reads an integer from the buffer

`number ReadUInt(number BitCount)` \
Reads an unsigned integer from the buffer

`string ReadData(number Length)` \
Reads a string of Length length from the buffer at 1 byte per character

`string ReadString()` \
Reads a string from the buffer at a length of 65,356

`Color ReadColor(bool HasAlpha = true)` \
Reads a Color from the buffer at 8 bits per property

`Vector ReadVector()` \
Reads a Vector from the buffer

`Vector ReadNormal()` \
Reads a normalized Vector from the buffer

`Angle ReadAngle()` \
Reads an Angle from the buffer

`Entity ReadEntity()` \
Reads an Entity from the buffer (16 bits)

`VMatrix ReadMatrix()` \
Reads a VMatrix from the buffer \
Temporarily disabled, does not read nor return anything

</details>

### Hooks

<details>
<summary>Hooks</summary>

`PreFrameStageNotify(number Stage)` \
Called before ClientDLL::FrameStageNotify \
Stage enumerations are declared in _G.proxi as shown above

`PostFrameStageNotify(number Stage)` \
Called after ClientDLL::FrameStageNotify \
Stage enumerations are declared in _G.proxi as shown above

`DispatchEffect(string EffectName, CEffectData Effect)` \
Called before an effect is activated \
Return `true` to prevent the effect from being activated

`CreateMoveEx(CUserCmd Command, bool SendPacket)` \
Called after CreateMove inside updated prediction \
First return value is a bool for whether or not to update engine view angles \
Second return value is a bool for whether or not to choke the packet. proxi supports up to 21 choked ticks

`SendStringCmd(string Command)` \
Called whenever a concommand is ran on the client \
Return `false` to prevent the command event from being sent to the server

`ShouldSendLuaError(string Error)` \
Called whenever a Lua error happens \
Return `false` to prevent the error from being sent to the server \
Return a string to change the error message to something else

`OutgoingNetMessage(proxi_bf_read Buffer)` \
Called before a net message is sent to the server \
Return `false` to prevent the net message from being sent

</details>
