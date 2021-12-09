--[000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001]

local GA_lib_installed = false
file.Enumerate(function(filename)
    if filename == "libraries/ga_lib.lua" then
        local f = file.Open("libraries/ga_lib.lua", "r")
        local cver = string.match(f:Read(),"%d+")
        print("Current ga_lib [" .. cver .. "]")
        f:Close()
        
        local body = http.Get("https://raw.githubusercontent.com/G-A-Development-Team/libs/main/libs.lua")
        local lver = string.match(body,"%d+")
        print("Latest ga_lib [" .. lver .. "]")
        if lver > cver then
          file.Delete("libraries/ga_lib.lua")
          file.Write("libraries/ga_lib.lua", body)
        end
        
        GA_lib_installed = true
    end
end)
if not GA_lib_installed then
    local body = http.Get("https://raw.githubusercontent.com/G-A-Development-Team/libs/main/libs.lua")
    
    file.Write("libraries/ga_lib.lua", body)
end
RunScript("libraries/ga_lib.lua")


local varPrefix = "cloudy-"
local w_windows = {}

local private = {
  w_make = function(name, size)
    local width   = size[1]
    local height  = size[2]
    local screenWidth, screenHeight = draw.GetScreenSize()
    local window  = gui.Window(varPrefix .. name, name, ((screenWidth/2) - (width/2)), ((screenHeight/2) - (height/2)), width, height)
    
    table.insert(w_windows, window)
    
    return window
  end
}

Cloudy = {
  Window = {
      Make = function(name, size)
        private.w_make(name, size)
      end,
  },
  DebugVars = function()
    print("w_windows:")
    print_table(w_windows)
  end
}

local function main()
  Cloudy.Window.Make("Alfred", {800, 800})
  --Cloudy.Window.Make("Jen", {800, 800})
  Cloudy.DebugVars()
end
main()
