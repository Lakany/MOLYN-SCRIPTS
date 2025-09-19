-- Auto-Exec Script for Specific Place IDs
-- يعمل تلقائياً عند الدخول إلى أماكن محددة في روبلوكس

local PlaceHandlers = {
    ["17453916834"] = {
        code = 
        [[THE SCRIPT]],
        enabled = true
    },
    
    ["1234567"] = {
        code = 
        [[THE SCRIPT]],
        enabled = true
    },
    
    ["8910111"] = {
        code = 
        [[THE SCRIPT]],
        enabled = true
    }
}

-- التنفيذ الرئيسي بدون أي إخراج
local function executePlaceSpecificCode()
    local currentPlaceId = tostring(game.PlaceId)
    
    if PlaceHandlers[currentPlaceId] and PlaceHandlers[currentPlaceId].enabled then
        local success, errorMessage = pcall(function()
            loadstring(PlaceHandlers[currentPlaceId].code)()
        end)
        
        -- معالجة الأخطاء بصمت (بدون إظهار warns)
        if not success then
            -- يمكن إضافة تسجيل للأخطاء هنا بدون إظهار للمستخدم
        end
    end
end

-- بدء التنفيذ مع التأكد من عدم وجود أي إخراج
executePlaceSpecificCode()

-- إضافة أكواد إضافية هنا (يمكن نسخ السطور أعلاه وإضافة أماكن جديدة)
