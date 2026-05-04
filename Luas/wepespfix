some fix 


local font = draw.CreateFont("Tahoma", 13, 700)

local WEAPONS = {
    CRifle_M60 = { label = "M60", r = 255, g = 200, b = 0 },
    CGrenadeLauncher = { label = "GRENADE LAUNCHER", r = 0, g = 255, b = 100 },
}

local function DrawOutlinedText(x, y, r, g, b, text)
    draw.SetFont(font)
    draw.Color(0, 0, 0, 255)
    draw.Text(x-1, y-1, text)
    draw.Text(x+1, y-1, text)
    draw.Text(x-1, y+1, text)
    draw.Text(x+1, y+1, text)
    draw.Color(r, g, b, 255)
    draw.Text(x, y, text)
end

callbacks.Register("Draw", "weapon_esp", function()
    for cls, info in pairs(WEAPONS) do
        local ok, ents = pcall(function()
            return entities.FindByClass(cls)
        end)
        if ok and ents then
            for _, ent in pairs(ents) do
                if not ent:IsDormant() then
                    local origin = ent:GetAbsOrigin()
                    if origin then
                        local sx, sy = client.WorldToScreen(
                            Vector3(origin.x, origin.y, origin.z + 10))
                        if sx then
                            DrawOutlinedText(sx, sy, info.r, info.g, info.b, info.label)
                        end
                    end
                end
            end
        end
    end
end)
