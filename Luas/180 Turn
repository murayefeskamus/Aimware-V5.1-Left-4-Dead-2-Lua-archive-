-- 180 Turn 
local ref = gui.Reference("Misc", "General", "Extra")
local gb  = gui.Groupbox(ref, "180 Turn", 295, 395, 300, 0)

local enable  = gui.Checkbox(gb, "t180.enable", "Enable 180 Turn", false)
local keybind = gui.Keybox(gb, "t180.key", "Turn Key", 0)

local was_pressed = false

callbacks.Register("CreateMove", "turn180", function(cmd)
    if not enable:GetValue() then return end

    local is_pressed = keybind:GetValue() ~= 0 and input.IsButtonDown(keybind:GetValue())

    if is_pressed and not was_pressed then
        local ang = engine.GetViewAngles()
        
        local new_yaw = ang.y + 180
        if new_yaw > 180 then new_yaw = new_yaw - 360 end
        if new_yaw < -180 then new_yaw = new_yaw + 360 end

        engine.SetViewAngles(EulerAngles(ang.x, new_yaw, 0))
    end

    was_pressed = is_pressed
end)
