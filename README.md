function love.load()
    menuVisible = true
    options = {
        "Ativar velocidade 100",
        ""Voar",
        "Teleportar"
    }
    selectedOption = 1
end

function love.draw()
    if menuVisible then
        love.graphics.print("=== Mod Menu ===", 100, 100)
        for i, option in ipairs(options) do
            local prefix = (i == selectedOption) and "> " or "  "
            love.graphics.print(prefix .. option, 100, 100 + i * 20)
        end
    end
end

function love.keypressed(key)
    if key == "up" then
        selectedOption = selectedOption - 1
        if selectedOption < 1 then selectedOption = #options end
    elseif key == "down" then
        selectedOption = selectedOption + 1
        if selectedOption > #options then selectedOption = 1 end
    elseif key == "return" then
        print("Selecionado:", options[selectedOption])
         fly
    elseif key == "m" then
        menuVisible = not menuVisible
    end
end
