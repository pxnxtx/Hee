local Lighting = game:GetService("Lighting")
local RunService = game:GetService("RunService")
local LocalPlayer = game:GetService("Players").LocalPlayer
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local TextService = game:GetService("TextService")
local Camera = game:GetService("Workspace").CurrentCamera
local Mouse = LocalPlayer:GetMouse()
local httpService = game:GetService("HttpService")

local RenderStepped = RunService.RenderStepped

local ProtectGui = protectgui or (syn and syn.protect_gui) or function() end

local Themes = {
	Names = {
		"Astromy Theme 1",
		"Astromy Theme 2",
		"Astromy Theme 3",
		"Astromy Theme 4",
		"Astromy Theme 5",
		"Amethyst",
		"Crimson Dark",
		"Ember",
		"Neon Crimson",		
		"Neon Orange",
		"Dark Typewriter",
		"VSC Dark High Contrast",
		"Dark",
		"Darker",
		"Light",
		"Aqua",
		"Amethyst",
		"Amethyst Dark",
		"Rose",
		"Sakura",
	},
	["Astromy Theme 1"] = {
		Accent = Color3.fromHex("#FF0059"),
    AcrylicMain = Color3.fromHex("#0B090B"),
    AcrylicBorder = Color3.fromHex("#2A2A2A"),
    AcrylicGradient = ColorSequence.new(Color3.fromHex("#282828"), Color3.fromHex("#262328")),
    AcrylicNoise = 1,
    TitleBarLine = Color3.fromHex("#2A2A2A"),
    Tab = Color3.fromHex("#889C9F"),
    Element = Color3.fromHex("#889C9F"),
    ElementBorder = Color3.fromHex("#110F0F"),
    InElementBorder = Color3.fromHex("#5A5A5A"),
    ElementTransparency = 0.87,
    ToggleSlider = Color3.fromHex("#787878"),
    ToggleToggled = Color3.fromHex("#0B090B"),
    SliderRail = Color3.fromHex("#787878"),
    DropdownFrame = Color3.fromHex("#A0A0A0"),
    DropdownHolder = Color3.fromHex("#0B090B"),
    DropdownBorder = Color3.fromHex("#110F0F"),
    DropdownOption = Color3.fromHex("#787878"),
    Keybind = Color3.fromHex("#787878"),
    Input = Color3.fromHex("#A0A0A0"),
    InputFocused = Color3.fromHex("#0A0A0A"),
    InputIndicator = Color3.fromHex("#969696"),
    Dialog = Color3.fromHex("#171414"),
    DialogHolder = Color3.fromHex("#110F0F"),
    DialogHolderLine = Color3.fromHex("#1E1E1E"),
    DialogButton = Color3.fromHex("#202122"),
    DialogButtonBorder = Color3.fromHex("#505050"),
    DialogBorder = Color3.fromHex("#2A2A2A"),
    DialogInput = Color3.fromHex("#373737"),
    DialogInputLine = Color3.fromHex("#A0A0A0"),
    Text = Color3.fromHex("#F0F0F0"),
    SubText = Color3.fromHex("#AAAAAA"),
    Hover = Color3.fromHex("#787878"),
    HoverChange = 0.07
	},
	["Astromy Theme 2"] = {
		Accent = Color3.fromHex("#FF3232"),
    AcrylicMain = Color3.fromHex("#141414"),
    AcrylicBorder = Color3.fromHex("#FF3232"),
    AcrylicGradient = ColorSequence.new(Color3.fromHex("#320000"), Color3.fromHex("#1E0000")),
    AcrylicNoise = 0.8,
    TitleBarLine = Color3.fromHex("#781414"),
    Tab = Color3.fromHex("#FF3C3C"),
    Element = Color3.fromHex("#282828"),
    ElementBorder = Color3.fromHex("#FF3232"),
    InElementBorder = Color3.fromHex("#781414"),
    ElementTransparency = 0.85,
    ToggleSlider = Color3.fromHex("#FF3232"),
    ToggleToggled = Color3.fromHex("#280000"),
    SliderRail = Color3.fromHex("#781414"),
    DropdownFrame = Color3.fromHex("#282828"),
    DropdownHolder = Color3.fromHex("#1E1E1E"),
    DropdownBorder = Color3.fromHex("#FF3232"),
    DropdownOption = Color3.fromHex("#282828"),
    Keybind = Color3.fromHex("#FF3232"),
    Input = Color3.fromHex("#282828"),
    InputFocused = Color3.fromHex("#3C0000"),
    InputIndicator = Color3.fromHex("#FF4646"),
    Dialog = Color3.fromHex("#1E1E1E"),
    DialogHolder = Color3.fromHex("#280000"),
    DialogHolderLine = Color3.fromHex("#140000"),
    DialogButton = Color3.fromHex("#FF3232"),
    DialogButtonBorder = Color3.fromHex("#FF3232"),
    DialogBorder = Color3.fromHex("#781414"),
    DialogInput = Color3.fromHex("#282828"),
    DialogInputLine = Color3.fromHex("#FF3232"),
    Text = Color3.fromHex("#FFFFFF"),
    SubText = Color3.fromHex("#B4B4B4"),
    Hover = Color3.fromHex("#FF3C3C"),
    HoverChange = 0.05
	},
	["Astromy Theme 3"] = {
		Accent = Color3.fromHex("#B400FF"),
    AcrylicMain = Color3.fromHex("#0F0A19"),
    AcrylicBorder = Color3.fromHex("#B400FF"),
    AcrylicGradient = ColorSequence.new(Color3.fromHex("#3C005A"), Color3.fromHex("#1E0032")),
    AcrylicNoise = 0.75,
    TitleBarLine = Color3.fromHex("#64008C"),
    Tab = Color3.fromHex("#C800FF"),
    Element = Color3.fromHex("#1E1428"),
    ElementBorder = Color3.fromHex("#B400FF"),
    InElementBorder = Color3.fromHex("#64008C"),
    ElementTransparency = 0.85,
    ToggleSlider = Color3.fromHex("#B400FF"),
    ToggleToggled = Color3.fromHex("#28003C"),
    SliderRail = Color3.fromHex("#64008C"),
    DropdownFrame = Color3.fromHex("#1E1428"),
    DropdownHolder = Color3.fromHex("#140A1E"),
    DropdownBorder = Color3.fromHex("#B400FF"),
    DropdownOption = Color3.fromHex("#1E1428"),
    Keybind = Color3.fromHex("#B400FF"),
    Input = Color3.fromHex("#1E1428"),
    InputFocused = Color3.fromHex("#46005A"),
    InputIndicator = Color3.fromHex("#C832FF"),
    Dialog = Color3.fromHex("#140A1E"),
    DialogHolder = Color3.fromHex("#320050"),
    DialogHolderLine = Color3.fromHex("#1E003C"),
    DialogButton = Color3.fromHex("#B400FF"),
    DialogButtonBorder = Color3.fromHex("#B400FF"),
    DialogBorder = Color3.fromHex("#64008C"),
    DialogInput = Color3.fromHex("#1E1428"),
    DialogInputLine = Color3.fromHex("#B400FF"),
    Text = Color3.fromHex("#FFFFFF"),
    SubText = Color3.fromHex("#BEAADC"),
    Hover = Color3.fromHex("#C81EFF"),
    HoverChange = 0.06
	},
	["Astromy Theme 4"] = {
		Accent = Color3.fromHex("#50C8FF"),
    AcrylicMain = Color3.fromHex("#0A141E"),
    AcrylicBorder = Color3.fromHex("#50C8FF"),
    AcrylicGradient = ColorSequence.new(Color3.fromHex("#14283C"), Color3.fromHex("#0A141E")),
    AcrylicNoise = 0.78,
    TitleBarLine = Color3.fromHex("#286482"),
    Tab = Color3.fromHex("#5AD2FF"),
    Element = Color3.fromHex("#19232D"),
    ElementBorder = Color3.fromHex("#50C8FF"),
    InElementBorder = Color3.fromHex("#286482"),
    ElementTransparency = 0.85,
    ToggleSlider = Color3.fromHex("#50C8FF"),
    ToggleToggled = Color3.fromHex("#0A3250"),
    SliderRail = Color3.fromHex("#286482"),
    DropdownFrame = Color3.fromHex("#19232D"),
    DropdownHolder = Color3.fromHex("#141E28"),
    DropdownBorder = Color3.fromHex("#50C8FF"),
    DropdownOption = Color3.fromHex("#19232D"),
    Keybind = Color3.fromHex("#50C8FF"),
    Input = Color3.fromHex("#19232D"),
    InputFocused = Color3.fromHex("#144664"),
    InputIndicator = Color3.fromHex("#78E6FF"),
    Dialog = Color3.fromHex("#141E28"),
    DialogHolder = Color3.fromHex("#0A3250"),
    DialogHolderLine = Color3.fromHex("#051E3C"),
    DialogButton = Color3.fromHex("#50C8FF"),
    DialogButtonBorder = Color3.fromHex("#50C8FF"),
    DialogBorder = Color3.fromHex("#286482"),
    DialogInput = Color3.fromHex("#19232D"),
    DialogInputLine = Color3.fromHex("#50C8FF"),
    Text = Color3.fromHex("#F0FAFF"),
    SubText = Color3.fromHex("#AAC8DC"),
    Hover = Color3.fromHex("#64DCFF"),
    HoverChange = 0.05
	},
	["Astromy Theme 5"] = {
		Accent = Color3.fromHex("#64FF64"),
    AcrylicMain = Color3.fromHex("#0F190F"),
    AcrylicBorder = Color3.fromHex("#64FF64"),
    AcrylicGradient = ColorSequence.new(Color3.fromHex("#1E3C1E"), Color3.fromHex("#0A1E0A")),
    AcrylicNoise = 0.8,
    TitleBarLine = Color3.fromHex("#328C32"),
    Tab = Color3.fromHex("#78FF78"),
    Element = Color3.fromHex("#192319"),
    ElementBorder = Color3.fromHex("#64FF64"),
    InElementBorder = Color3.fromHex("#328C32"),
    ElementTransparency = 0.85,
    ToggleSlider = Color3.fromHex("#64FF64"),
    ToggleToggled = Color3.fromHex("#143214"),
    SliderRail = Color3.fromHex("#328C32"),
    DropdownFrame = Color3.fromHex("#192319"),
    DropdownHolder = Color3.fromHex("#141E14"),
    DropdownBorder = Color3.fromHex("#64FF64"),
    DropdownOption = Color3.fromHex("#192319"),
    Keybind = Color3.fromHex("#64FF64"),
    Input = Color3.fromHex("#192319"),
    InputFocused = Color3.fromHex("#1E501E"),
    InputIndicator = Color3.fromHex("#8CFF8C"),
    Dialog = Color3.fromHex("#141E14"),
    DialogHolder = Color3.fromHex("#1E461E"),
    DialogHolderLine = Color3.fromHex("#0A280A"),
    DialogButton = Color3.fromHex("#64FF64"),
    DialogButtonBorder = Color3.fromHex("#64FF64"),
    DialogBorder = Color3.fromHex("#328C32"),
    DialogInput = Color3.fromHex("#192319"),
    DialogInputLine = Color3.fromHex("#64FF64"),
    Text = Color3.fromHex("#FFFFFF"),
    SubText = Color3.fromHex("#BEE6BE"),
    Hover = Color3.fromHex("#82FF82"),
    HoverChange = 0.05
	},
	["VSC Dark High Contrast"] = {
		Accent = Color3.fromHex("#569cd6"), -- Based on keyword color

		AcrylicMain = Color3.fromHex("#000000"), -- editor.background
		AcrylicBorder = Color3.fromHex("#FFFFFF"), -- Based on editor.foreground
		AcrylicGradient = ColorSequence.new(Color3.fromHex("#000000"), Color3.fromHex("#000000")),
		AcrylicNoise = 1,

		TitleBarLine = Color3.fromHex("#FFFFFF"),
		Tab = Color3.fromHex("#FFFFFF"),

		Element = Color3.fromHex("#000000"),
		ElementBorder = Color3.fromHex("#FFFFFF"),
		InElementBorder = Color3.fromHex("#569cd6"),
		ElementTransparency = 0,

		ToggleSlider = Color3.fromHex("#569cd6"),
		ToggleToggled = Color3.fromHex("#000000"),

		SliderRail = Color3.fromHex("#569cd6"),

		DropdownFrame = Color3.fromHex("#000000"),
		DropdownHolder = Color3.fromHex("#000000"),
		DropdownBorder = Color3.fromHex("#FFFFFF"),
		DropdownOption = Color3.fromHex("#FFFFFF"),

		Keybind = Color3.fromHex("#000000"),

		Input = Color3.fromHex("#000000"),
		InputFocused = Color3.fromHex("#000000"),
		InputIndicator = Color3.fromHex("#7c7c7c"), -- Based on editorWhitespace.foreground

		Dialog = Color3.fromHex("#000000"),
		DialogHolder = Color3.fromHex("#000000"),
		DialogHolderLine = Color3.fromHex("#FFFFFF"),
		DialogButton = Color3.fromHex("#000000"),
		DialogButtonBorder = Color3.fromHex("#FFFFFF"),
		DialogBorder = Color3.fromHex("#FFFFFF"),
		DialogInput = Color3.fromHex("#000000"),
		DialogInputLine = Color3.fromHex("#569cd6"),

		Text = Color3.fromHex("#FFFFFF"), -- editor.foreground
		SubText = Color3.fromHex("#9D9D9D"), -- descriptionForeground
		Hover = Color3.fromHex("#383a49"), -- Based on actionBar.toggledBackground
		HoverChange = 0.1
	},
	["Dark Typewriter"] = {
		Accent = Color3.fromRGB(109, 180, 120),

		AcrylicMain = Color3.fromRGB(38, 38, 38),
		AcrylicBorder = Color3.fromRGB(85, 85, 85),
		AcrylicGradient = ColorSequence.new(Color3.fromRGB(38, 38, 38), Color3.fromRGB(38, 38, 38)),
		AcrylicNoise = 1,

		TitleBarLine = Color3.fromRGB(189, 189, 189),
		Tab = Color3.fromRGB(109, 180, 120),

		Element = Color3.fromRGB(42, 42, 42),
		ElementBorder = Color3.fromRGB(51, 51, 51),
		InElementBorder = Color3.fromRGB(51, 51, 51),
		ElementTransparency = 0,

		ToggleSlider = Color3.fromRGB(103, 169, 113),
		ToggleToggled = Color3.fromRGB(255, 255, 255),

		SliderRail = Color3.fromRGB(51, 51, 51),

		DropdownFrame = Color3.fromRGB(68, 68, 68),
		DropdownHolder = Color3.fromRGB(68, 68, 68),
		DropdownBorder = Color3.fromRGB(38, 38, 38),
		DropdownOption = Color3.fromRGB(153, 200, 255),

		Keybind = Color3.fromRGB(54, 54, 54),

		Input = Color3.fromRGB(27, 27, 27),
		InputFocused = Color3.fromRGB(51, 51, 51),
		InputIndicator = Color3.fromRGB(197, 184, 161),

		Dialog = Color3.fromRGB(38, 38, 38),
		DialogHolder = Color3.fromRGB(58, 52, 46),
		DialogHolderLine = Color3.fromRGB(40, 40, 40),
		DialogButton = Color3.fromRGB(42, 42, 42),
		DialogButtonBorder = Color3.fromRGB(51, 51, 51),
		DialogBorder = Color3.fromRGB(189, 189, 189),
		DialogInput = Color3.fromRGB(27, 27, 27),
		DialogInputLine = Color3.fromRGB(197, 184, 161),

		Text = Color3.fromRGB(197, 184, 161),
		SubText = Color3.fromRGB(158, 158, 158),
		Hover = Color3.fromRGB(149, 149, 149),
		HoverChange = 0.04
	},
	["Amethyst Maru"] = {
		Name = "Amethyst Maru",
		Accent = Color3.fromHex("#1e6dbf"), -- Dark blue accent

		AcrylicMain = Color3.fromHex("#001a33"), -- Dark blue background
		AcrylicBorder = Color3.fromHex("#004080"), -- Slightly lighter border
		AcrylicGradient = ColorSequence.new(Color3.fromHex("#001a33"), Color3.fromHex("#001a33")),
		AcrylicNoise = 0.92,

		TitleBarLine = Color3.fromHex("#004080"),
		Tab = Color3.fromHex("#a1c4e6"), -- Light blue text

		Element = Color3.fromHex("#00264d"),
		ElementBorder = Color3.fromHex("#004080"),
		InElementBorder = Color3.fromHex("#1e6dbf"),
		ElementTransparency = 0.85,

		ToggleSlider = Color3.fromHex("#0055a3"),
		ToggleToggled = Color3.fromHex("#001a33"),

		SliderRail = Color3.fromHex("#0055a3"),

		DropdownFrame = Color3.fromHex("#00264d"),
		DropdownHolder = Color3.fromHex("#00264d"),
		DropdownBorder = Color3.fromHex("#004080"),
		DropdownOption = Color3.fromHex("#a1c4e6"),

		Keybind = Color3.fromHex("#00264d"),

		Input = Color3.fromHex("#001933"),
		InputFocused = Color3.fromHex("#001933"),
		InputIndicator = Color3.fromHex("#7fa1bf"),

		Dialog = Color3.fromHex("#00264d"),
		DialogHolder = Color3.fromHex("#001a33"),
		DialogHolderLine = Color3.fromHex("#004080"),
		DialogButton = Color3.fromHex("#00264d"),
		DialogButtonBorder = Color3.fromHex("#004080"),
		DialogBorder = Color3.fromHex("#004080"),
		DialogInput = Color3.fromHex("#001933"),
		DialogInputLine = Color3.fromHex("#1e6dbf"),

		Text = Color3.fromHex("#a1c4e6"), -- Light blue text for readability
		SubText = Color3.fromHex("#7fa1bf"),
		Hover = Color3.fromHex("#004080"),
		HoverChange = 0.1
	},
	["Amethyst Dark"] = {
		Name = "Amethyst Dark",
		Accent = Color3.fromHex("#b133ff"),

		AcrylicMain = Color3.fromHex("#120024"),
		AcrylicBorder = Color3.fromHex("#4d057b"),
		AcrylicGradient = ColorSequence.new(Color3.fromHex("#120024"), Color3.fromHex("#120024")),
		AcrylicNoise = 0.92,

		TitleBarLine = Color3.fromHex("#4d057b"),
		Tab = Color3.fromHex("#e9d9f2"),

		Element = Color3.fromHex("#25013c"),
		ElementBorder = Color3.fromHex("#4d057b"),
		InElementBorder = Color3.fromHex("#b133ff"),
		ElementTransparency = 0.85,

		ToggleSlider = Color3.fromHex("#7d16bf"),
		ToggleToggled = Color3.fromHex("#120024"),

		SliderRail = Color3.fromHex("#7d16bf"),

		DropdownFrame = Color3.fromHex("#25013c"),
		DropdownHolder = Color3.fromHex("#25013c"),
		DropdownBorder = Color3.fromHex("#4d057b"),
		DropdownOption = Color3.fromHex("#e9d9f2"),

		Keybind = Color3.fromHex("#25013c"),

		Input = Color3.fromHex("#180030"),
		InputFocused = Color3.fromHex("#180030"),
		InputIndicator = Color3.fromHex("#9e85ad"),

		Dialog = Color3.fromHex("#25013c"),
		DialogHolder = Color3.fromHex("#120024"),
		DialogHolderLine = Color3.fromHex("#4d057b"),
		DialogButton = Color3.fromHex("#25013c"),
		DialogButtonBorder = Color3.fromHex("#4d057b"),
		DialogBorder = Color3.fromHex("#4d057b"),
		DialogInput = Color3.fromHex("#180030"),
		DialogInputLine = Color3.fromHex("#b133ff"),

		Text = Color3.fromHex("#e9d9f2"),
		SubText = Color3.fromHex("#9e85ad"),
		Hover = Color3.fromHex("#4d057b"),
		HoverChange = 0.1
	},
	["Crimson Dark"] = {
		Name = "Crimson Dark",
		Accent = Color3.fromHex("#ff3333"), -- Bright Crimson Red

		AcrylicMain = Color3.fromHex("#240000"), -- Deep Maroon
		AcrylicBorder = Color3.fromHex("#7b0505"), -- Dark Red
		AcrylicGradient = ColorSequence.new(Color3.fromHex("#240000"), Color3.fromHex("#240000")),
		AcrylicNoise = 0.92,

		TitleBarLine = Color3.fromHex("#7b0505"), -- Dark Red
		Tab = Color3.fromHex("#f2d9d9"), -- Soft Pinkish White

		Element = Color3.fromHex("#3c0101"), -- Deep Red
		ElementBorder = Color3.fromHex("#7b0505"), -- Dark Red
		InElementBorder = Color3.fromHex("#ff3333"), -- Bright Crimson
		ElementTransparency = 0.85,

		ToggleSlider = Color3.fromHex("#bf1616"), -- Rich Red
		ToggleToggled = Color3.fromHex("#240000"), -- Deep Maroon

		SliderRail = Color3.fromHex("#bf1616"), -- Rich Red

		DropdownFrame = Color3.fromHex("#3c0101"), -- Deep Red
		DropdownHolder = Color3.fromHex("#3c0101"), -- Deep Red
		DropdownBorder = Color3.fromHex("#7b0505"), -- Dark Red
		DropdownOption = Color3.fromHex("#f2d9d9"), -- Soft Pinkish White

		Keybind = Color3.fromHex("#3c0101"), -- Deep Red

		Input = Color3.fromHex("#300000"), -- Dark Maroon
		InputFocused = Color3.fromHex("#300000"), -- Dark Maroon
		InputIndicator = Color3.fromHex("#ad8585"), -- Muted Red

		Dialog = Color3.fromHex("#3c0101"), -- Deep Red
		DialogHolder = Color3.fromHex("#240000"), -- Deep Maroon
		DialogHolderLine = Color3.fromHex("#7b0505"), -- Dark Red
		DialogButton = Color3.fromHex("#3c0101"), -- Deep Red
		DialogButtonBorder = Color3.fromHex("#7b0505"), -- Dark Red
		DialogBorder = Color3.fromHex("#7b0505"), -- Dark Red
		DialogInput = Color3.fromHex("#300000"), -- Dark Maroon
		DialogInputLine = Color3.fromHex("#ff3333"), -- Bright Crimson

		Text = Color3.fromHex("#f2d9d9"), -- Soft Pinkish White
		SubText = Color3.fromHex("#ad8585"), -- Muted Red
		Hover = Color3.fromHex("#7b0505"), -- Dark Red
		HoverChange = 0.1
	},
	["Neon Crimson"] = {
		Name = "Neon Crimson",
		Accent = Color3.fromHex("#ff0055"), -- Neon Red-Pink

		AcrylicMain = Color3.fromHex("#0a0005"), -- Deep Black-Red
		AcrylicBorder = Color3.fromHex("#910027"), -- Intense Deep Red
		AcrylicGradient = ColorSequence.new(Color3.fromHex("#0a0005"), Color3.fromHex("#0a0005")),
		AcrylicNoise = 0.92,

		TitleBarLine = Color3.fromHex("#910027"), -- Deep Red Border
		Tab = Color3.fromHex("#ffccd9"), -- Soft Neon Pink

		Element = Color3.fromHex("#220007"), -- Dark Red-Black
		ElementBorder = Color3.fromHex("#910027"), -- Intense Deep Red
		InElementBorder = Color3.fromHex("#ff0055"), -- Neon Red-Pink
		ElementTransparency = 0.85,

		ToggleSlider = Color3.fromHex("#d40040"), -- Bright Crimson
		ToggleToggled = Color3.fromHex("#0a0005"), -- Deep Black-Red

		SliderRail = Color3.fromHex("#d40040"), -- Bright Crimson

		DropdownFrame = Color3.fromHex("#220007"), -- Dark Red-Black
		DropdownHolder = Color3.fromHex("#220007"), -- Dark Red-Black
		DropdownBorder = Color3.fromHex("#910027"), -- Intense Deep Red
		DropdownOption = Color3.fromHex("#ffccd9"), -- Soft Neon Pink

		Keybind = Color3.fromHex("#220007"), -- Dark Red-Black

		Input = Color3.fromHex("#140005"), -- Deep Black-Red
		InputFocused = Color3.fromHex("#140005"), -- Deep Black-Red
		InputIndicator = Color3.fromHex("#ff8099"), -- Soft Neon Red

		Dialog = Color3.fromHex("#220007"), -- Dark Red-Black
		DialogHolder = Color3.fromHex("#0a0005"), -- Deep Black-Red
		DialogHolderLine = Color3.fromHex("#910027"), -- Intense Deep Red
		DialogButton = Color3.fromHex("#220007"), -- Dark Red-Black
		DialogButtonBorder = Color3.fromHex("#910027"), -- Intense Deep Red
		DialogBorder = Color3.fromHex("#910027"), -- Intense Deep Red
		DialogInput = Color3.fromHex("#140005"), -- Deep Black-Red
		DialogInputLine = Color3.fromHex("#ff0055"), -- Neon Red-Pink

		Text = Color3.fromHex("#ffccd9"), -- Soft Neon Pink
		SubText = Color3.fromHex("#ff8099"), -- Soft Neon Red
		Hover = Color3.fromHex("#910027"), -- Intense Deep Red
		HoverChange = 0.1
	},
	["Neon Orange"] = {
		Name = "Neon Orange",
		Accent = Color3.fromHex("#ff6a00"), -- Bright Orange

		AcrylicMain = Color3.fromHex("#0a0500"), -- Deep Black-Orange
		AcrylicBorder = Color3.fromHex("#913200"), -- Deep Orange
		AcrylicGradient = ColorSequence.new(Color3.fromHex("#0a0500"), Color3.fromHex("#0a0500")),
		AcrylicNoise = 0.92,

		TitleBarLine = Color3.fromHex("#913200"), -- Deep Orange Border
		Tab = Color3.fromHex("#ffd9cc"), -- Soft Orange-White

		Element = Color3.fromHex("#220e00"), -- Dark Orange-Black
		ElementBorder = Color3.fromHex("#913200"), -- Deep Orange
		InElementBorder = Color3.fromHex("#ff6a00"), -- Bright Orange
		ElementTransparency = 0.85,

		ToggleSlider = Color3.fromHex("#d45500"), -- Medium Orange
		ToggleToggled = Color3.fromHex("#0a0500"), -- Deep Black-Orange

		SliderRail = Color3.fromHex("#d45500"), -- Medium Orange

		DropdownFrame = Color3.fromHex("#220e00"), -- Dark Orange-Black
		DropdownHolder = Color3.fromHex("#220e00"), -- Dark Orange-Black
		DropdownBorder = Color3.fromHex("#913200"), -- Deep Orange
		DropdownOption = Color3.fromHex("#ffd9cc"), -- Soft Orange-White

		Keybind = Color3.fromHex("#220e00"), -- Dark Orange-Black

		Input = Color3.fromHex("#140800"), -- Deep Black-Orange
		InputFocused = Color3.fromHex("#140800"), -- Deep Black-Orange
		InputIndicator = Color3.fromHex("#ffa280"), -- Soft Orange

		Dialog = Color3.fromHex("#220e00"), -- Dark Orange-Black
		DialogHolder = Color3.fromHex("#0a0500"), -- Deep Black-Orange
		DialogHolderLine = Color3.fromHex("#913200"), -- Deep Orange
		DialogButton = Color3.fromHex("#220e00"), -- Dark Orange-Black
		DialogButtonBorder = Color3.fromHex("#913200"), -- Deep Orange
		DialogBorder = Color3.fromHex("#913200"), -- Deep Orange
		DialogInput = Color3.fromHex("#140800"), -- Deep Black-Orange
		DialogInputLine = Color3.fromHex("#ff6a00"), -- Bright Orange

		Text = Color3.fromHex("#ffd9cc"), -- Soft Orange-White
		SubText = Color3.fromHex("#ffa280"), -- Soft Orange
		Hover = Color3.fromHex("#913200"), -- Deep Orange
		HoverChange = 0.1
	},
	Ember = {
		Name = "Ember",
		Accent = Color3.fromRGB(217, 87, 0), -- Dark orange accent

		AcrylicMain = Color3.fromRGB(20, 20, 20),
		AcrylicBorder = Color3.fromRGB(130, 100, 70), -- Adjusted for orange theme
		AcrylicGradient = ColorSequence.new(Color3.fromRGB(180, 100, 40), Color3.fromRGB(90, 40, 15)), -- Orange gradient
		AcrylicNoise = 0.92,

		TitleBarLine = Color3.fromRGB(120, 90, 60),
		Tab = Color3.fromRGB(180, 150, 120),

		Element = Color3.fromRGB(160, 130, 100), -- Changed to dark orange
		ElementBorder = Color3.fromRGB(80, 60, 40),
		InElementBorder = Color3.fromRGB(120, 100, 80),
		ElementTransparency = 0.87,

		ToggleSlider = Color3.fromRGB(160, 130, 100),
		ToggleToggled = Color3.fromRGB(0, 0, 0),

		SliderRail = Color3.fromRGB(160, 130, 100),

		DropdownFrame = Color3.fromRGB(200, 170, 140),
		DropdownHolder = Color3.fromRGB(90, 60, 30),
		DropdownBorder = Color3.fromRGB(75, 50, 25),
		DropdownOption = Color3.fromRGB(160, 130, 100),

		Keybind = Color3.fromRGB(160, 130, 100),

		Input = Color3.fromRGB(160, 130, 100),
		InputFocused = Color3.fromRGB(35, 20, 10),
		InputIndicator = Color3.fromRGB(190, 160, 130),
		InputIndicatorFocus = Color3.fromRGB(217, 87, 0), -- Dark orange focus

		Dialog = Color3.fromRGB(90, 60, 30),
		DialogHolder = Color3.fromRGB(75, 45, 20),
		DialogHolderLine = Color3.fromRGB(65, 40, 15),
		DialogButton = Color3.fromRGB(90, 60, 30),
		DialogButtonBorder = Color3.fromRGB(120, 90, 60),
		DialogBorder = Color3.fromRGB(110, 80, 50),
		DialogInput = Color3.fromRGB(100, 70, 40),
		DialogInputLine = Color3.fromRGB(200, 170, 140),

		Text = Color3.fromRGB(240, 240, 240),
		SubText = Color3.fromRGB(170, 170, 170),
		Hover = Color3.fromRGB(160, 130, 100),
		HoverChange = 0.04,
	},
	Dark = {
		Name = "Dark",
		Accent = Color3.fromRGB(96, 205, 255),

		AcrylicMain = Color3.fromRGB(60, 60, 60),
		AcrylicBorder = Color3.fromRGB(90, 90, 90),
		AcrylicGradient = ColorSequence.new(Color3.fromRGB(40, 40, 40), Color3.fromRGB(40, 40, 40)),
		AcrylicNoise = 0.9,

		TitleBarLine = Color3.fromRGB(75, 75, 75),
		Tab = Color3.fromRGB(120, 120, 120),

		Element = Color3.fromRGB(120, 120, 120),
		ElementBorder = Color3.fromRGB(35, 35, 35),
		InElementBorder = Color3.fromRGB(90, 90, 90),
		ElementTransparency = 0.87,

		ToggleSlider = Color3.fromRGB(120, 120, 120),
		ToggleToggled = Color3.fromRGB(0, 0, 0),

		SliderRail = Color3.fromRGB(120, 120, 120),

		DropdownFrame = Color3.fromRGB(160, 160, 160),
		DropdownHolder = Color3.fromRGB(45, 45, 45),
		DropdownBorder = Color3.fromRGB(35, 35, 35),
		DropdownOption = Color3.fromRGB(120, 120, 120),

		Keybind = Color3.fromRGB(120, 120, 120),

		Input = Color3.fromRGB(160, 160, 160),
		InputFocused = Color3.fromRGB(10, 10, 10),
		InputIndicator = Color3.fromRGB(150, 150, 150),

		Dialog = Color3.fromRGB(45, 45, 45),
		DialogHolder = Color3.fromRGB(35, 35, 35),
		DialogHolderLine = Color3.fromRGB(30, 30, 30),
		DialogButton = Color3.fromRGB(45, 45, 45),
		DialogButtonBorder = Color3.fromRGB(80, 80, 80),
		DialogBorder = Color3.fromRGB(70, 70, 70),
		DialogInput = Color3.fromRGB(55, 55, 55),
		DialogInputLine = Color3.fromRGB(160, 160, 160),

		Text = Color3.fromRGB(240, 240, 240),
		SubText = Color3.fromRGB(170, 170, 170),
		Hover = Color3.fromRGB(120, 120, 120),
		HoverChange = 0.07,
	},
	Darker = {
		Name = "Darker",
		Accent = Color3.fromRGB(72, 138, 182),

		AcrylicMain = Color3.fromRGB(30, 30, 30),
		AcrylicBorder = Color3.fromRGB(60, 60, 60),
		AcrylicGradient = ColorSequence.new(Color3.fromRGB(25, 25, 25), Color3.fromRGB(15, 15, 15)),
		AcrylicNoise = 0.94,

		TitleBarLine = Color3.fromRGB(65, 65, 65),
		Tab = Color3.fromRGB(100, 100, 100),

		Element = Color3.fromRGB(70, 70, 70),
		ElementBorder = Color3.fromRGB(25, 25, 25),
		InElementBorder = Color3.fromRGB(55, 55, 55),
		ElementTransparency = 0.82,

		DropdownFrame = Color3.fromRGB(120, 120, 120),
		DropdownHolder = Color3.fromRGB(35, 35, 35),
		DropdownBorder = Color3.fromRGB(25, 25, 25),

		Dialog = Color3.fromRGB(35, 35, 35),
		DialogHolder = Color3.fromRGB(25, 25, 25),
		DialogHolderLine = Color3.fromRGB(20, 20, 20),
		DialogButton = Color3.fromRGB(35, 35, 35),
		DialogButtonBorder = Color3.fromRGB(55, 55, 55),
		DialogBorder = Color3.fromRGB(50, 50, 50),
		DialogInput = Color3.fromRGB(45, 45, 45),
		DialogInputLine = Color3.fromRGB(120, 120, 120),
	},
	Light = {
		Name = "Light",
		Accent = Color3.fromRGB(0, 103, 192),

		AcrylicMain = Color3.fromRGB(200, 200, 200),
		AcrylicBorder = Color3.fromRGB(120, 120, 120),
		AcrylicGradient = ColorSequence.new(Color3.fromRGB(255, 255, 255), Color3.fromRGB(255, 255, 255)),
		AcrylicNoise = 0.96,

		TitleBarLine = Color3.fromRGB(160, 160, 160),
		Tab = Color3.fromRGB(90, 90, 90),

		Element = Color3.fromRGB(255, 255, 255),
		ElementBorder = Color3.fromRGB(180, 180, 180),
		InElementBorder = Color3.fromRGB(150, 150, 150),
		ElementTransparency = 0.65,

		ToggleSlider = Color3.fromRGB(40, 40, 40),
		ToggleToggled = Color3.fromRGB(255, 255, 255),

		SliderRail = Color3.fromRGB(40, 40, 40),

		DropdownFrame = Color3.fromRGB(200, 200, 200),
		DropdownHolder = Color3.fromRGB(240, 240, 240),
		DropdownBorder = Color3.fromRGB(200, 200, 200),
		DropdownOption = Color3.fromRGB(150, 150, 150),

		Keybind = Color3.fromRGB(120, 120, 120),

		Input = Color3.fromRGB(200, 200, 200),
		InputFocused = Color3.fromRGB(100, 100, 100),
		InputIndicator = Color3.fromRGB(80, 80, 80),
		InputIndicatorFocus = Color3.fromRGB(0, 103, 192),

		Dialog = Color3.fromRGB(255, 255, 255),
		DialogHolder = Color3.fromRGB(240, 240, 240),
		DialogHolderLine = Color3.fromRGB(228, 228, 228),
		DialogButton = Color3.fromRGB(255, 255, 255),
		DialogButtonBorder = Color3.fromRGB(190, 190, 190),
		DialogBorder = Color3.fromRGB(140, 140, 140),
		DialogInput = Color3.fromRGB(250, 250, 250),
		DialogInputLine = Color3.fromRGB(160, 160, 160),

		Text = Color3.fromRGB(0, 0, 0),
		SubText = Color3.fromRGB(40, 40, 40),
		Hover = Color3.fromRGB(50, 50, 50),
		HoverChange = 0.16,
	},
	Aqua = {
		Name = "Aqua",
		Accent = Color3.fromRGB(60, 165, 165),

		AcrylicMain = Color3.fromRGB(20, 20, 20),
		AcrylicBorder = Color3.fromRGB(50, 100, 100),
		AcrylicGradient = ColorSequence.new(Color3.fromRGB(60, 140, 140), Color3.fromRGB(40, 80, 80)),
		AcrylicNoise = 0.92,

		TitleBarLine = Color3.fromRGB(60, 120, 120),
		Tab = Color3.fromRGB(140, 180, 180),

		Element = Color3.fromRGB(110, 160, 160),
		ElementBorder = Color3.fromRGB(40, 70, 70),
		InElementBorder = Color3.fromRGB(80, 110, 110),
		ElementTransparency = 0.84,

		ToggleSlider = Color3.fromRGB(110, 160, 160),
		ToggleToggled = Color3.fromRGB(0, 0, 0),

		SliderRail = Color3.fromRGB(110, 160, 160),

		DropdownFrame = Color3.fromRGB(160, 200, 200),
		DropdownHolder = Color3.fromRGB(40, 80, 80),
		DropdownBorder = Color3.fromRGB(40, 65, 65),
		DropdownOption = Color3.fromRGB(110, 160, 160),

		Keybind = Color3.fromRGB(110, 160, 160),

		Input = Color3.fromRGB(110, 160, 160),
		InputFocused = Color3.fromRGB(20, 10, 30),
		InputIndicator = Color3.fromRGB(130, 170, 170),
		InputIndicatorFocus = Color3.fromRGB(60, 165, 165),

		Dialog = Color3.fromRGB(40, 80, 80),
		DialogHolder = Color3.fromRGB(30, 60, 60),
		DialogHolderLine = Color3.fromRGB(25, 50, 50),
		DialogButton = Color3.fromRGB(40, 80, 80),
		DialogButtonBorder = Color3.fromRGB(80, 110, 110),
		DialogBorder = Color3.fromRGB(50, 100, 100),
		DialogInput = Color3.fromRGB(45, 90, 90),
		DialogInputLine = Color3.fromRGB(130, 170, 170),

		Text = Color3.fromRGB(240, 240, 240),
		SubText = Color3.fromRGB(170, 170, 170),
		Hover = Color3.fromRGB(110, 160, 160),
		HoverChange = 0.04,
	},
	Amethyst = {
		Name = "Amethyst",
		Accent = Color3.fromRGB(97, 62, 167),

		AcrylicMain = Color3.fromRGB(20, 20, 20),
		AcrylicBorder = Color3.fromRGB(110, 90, 130),
		AcrylicGradient = ColorSequence.new(Color3.fromRGB(85, 57, 139), Color3.fromRGB(40, 25, 65)),
		AcrylicNoise = 0.92,

		TitleBarLine = Color3.fromRGB(95, 75, 110),
		Tab = Color3.fromRGB(160, 140, 180),

		Element = Color3.fromRGB(140, 120, 160),
		ElementBorder = Color3.fromRGB(60, 50, 70),
		InElementBorder = Color3.fromRGB(100, 90, 110),
		ElementTransparency = 0.87,

		ToggleSlider = Color3.fromRGB(140, 120, 160),
		ToggleToggled = Color3.fromRGB(0, 0, 0),

		SliderRail = Color3.fromRGB(140, 120, 160),

		DropdownFrame = Color3.fromRGB(170, 160, 200),
		DropdownHolder = Color3.fromRGB(60, 45, 80),
		DropdownBorder = Color3.fromRGB(50, 40, 65),
		DropdownOption = Color3.fromRGB(140, 120, 160),

		Keybind = Color3.fromRGB(140, 120, 160),

		Input = Color3.fromRGB(140, 120, 160),
		InputFocused = Color3.fromRGB(20, 10, 30),
		InputIndicator = Color3.fromRGB(170, 150, 190),
		InputIndicatorFocus = Color3.fromRGB(97, 62, 167),

		Dialog = Color3.fromRGB(60, 45, 80),
		DialogHolder = Color3.fromRGB(45, 30, 65),
		DialogHolderLine = Color3.fromRGB(40, 25, 60),
		DialogButton = Color3.fromRGB(60, 45, 80),
		DialogButtonBorder = Color3.fromRGB(95, 80, 110),
		DialogBorder = Color3.fromRGB(85, 70, 100),
		DialogInput = Color3.fromRGB(70, 55, 85),
		DialogInputLine = Color3.fromRGB(175, 160, 190),

		Text = Color3.fromRGB(240, 240, 240),
		SubText = Color3.fromRGB(170, 170, 170),
		Hover = Color3.fromRGB(140, 120, 160),
		HoverChange = 0.04,
	},
	Rose = {
		Name = "Rose",
		Accent = Color3.fromRGB(180, 55, 90),

		AcrylicMain = Color3.fromRGB(40, 40, 40),
		AcrylicBorder = Color3.fromRGB(130, 90, 110),
		AcrylicGradient = ColorSequence.new(Color3.fromRGB(190, 60, 135), Color3.fromRGB(165, 50, 70)),
		AcrylicNoise = 0.92,

		TitleBarLine = Color3.fromRGB(140, 85, 105),
		Tab = Color3.fromRGB(180, 140, 160),

		Element = Color3.fromRGB(200, 120, 170),
		ElementBorder = Color3.fromRGB(110, 70, 85),
		InElementBorder = Color3.fromRGB(120, 90, 90),
		ElementTransparency = 0.86,

		ToggleSlider = Color3.fromRGB(200, 120, 170),
		ToggleToggled = Color3.fromRGB(0, 0, 0),

		SliderRail = Color3.fromRGB(200, 120, 170),

		DropdownFrame = Color3.fromRGB(200, 160, 180),
		DropdownHolder = Color3.fromRGB(120, 50, 75),
		DropdownBorder = Color3.fromRGB(90, 40, 55),
		DropdownOption = Color3.fromRGB(200, 120, 170),

		Keybind = Color3.fromRGB(200, 120, 170),

		Input = Color3.fromRGB(200, 120, 170),
		InputFocused = Color3.fromRGB(20, 10, 30),
		InputIndicator = Color3.fromRGB(170, 150, 190),
		InputIndicatorFocus = Color3.fromRGB(180, 55, 90),

		Dialog = Color3.fromRGB(120, 50, 75),
		DialogHolder = Color3.fromRGB(95, 40, 60),
		DialogHolderLine = Color3.fromRGB(90, 35, 55),
		DialogButton = Color3.fromRGB(120, 50, 75),
		DialogButtonBorder = Color3.fromRGB(155, 90, 115),
		DialogBorder = Color3.fromRGB(100, 70, 90),
		DialogInput = Color3.fromRGB(135, 55, 80),
		DialogInputLine = Color3.fromRGB(190, 160, 180),

		Text = Color3.fromRGB(240, 240, 240),
		SubText = Color3.fromRGB(170, 170, 170),
		Hover = Color3.fromRGB(200, 120, 170),
		HoverChange = 0.04,
	},
	Sakura = {
		Name = "Sakura",
		Accent = Color3.fromRGB(252, 209, 215),

		AcrylicMain = Color3.fromRGB(40, 40, 40),
		AcrylicBorder = Color3.fromRGB(130, 90, 110),
		AcrylicGradient = ColorSequence.new{
			ColorSequenceKeypoint.new(0, Color3.fromRGB(252, 209, 215)),
			ColorSequenceKeypoint.new(0.25, Color3.fromRGB(255, 231, 222)),
			ColorSequenceKeypoint.new(0.50, Color3.fromRGB(233, 177, 205)),
			ColorSequenceKeypoint.new(0.75, Color3.fromRGB(195, 130, 158)),
			ColorSequenceKeypoint.new(1, Color3.fromRGB(86, 33, 53)),
		},
		AcrylicNoise = 0.92,

		TitleBarLine = Color3.fromRGB(140, 85, 105),
		Tab = Color3.fromRGB(132, 89, 95),

		Element = Color3.fromRGB(220, 140, 190),
		ElementBorder = Color3.fromRGB(110, 70, 85),
		InElementBorder = Color3.fromRGB(120, 90, 90),
		ElementTransparency = 0.86,

		ToggleSlider = Color3.fromRGB(252, 209, 215),
		ToggleToggled = Color3.fromRGB(252, 209, 215),
		TransparenToggle = 0.5,

		SliderRail = Color3.fromRGB(252, 209, 215),

		DropdownFrame = Color3.fromRGB(252, 209, 215),
		DropdownHolder = Color3.fromRGB(156, 103, 123),
		DropdownBorder = Color3.fromRGB(90, 40, 55),
		DropdownOption = Color3.fromRGB(252, 209, 215),

		Keybind = Color3.fromRGB(200, 120, 170),

		Input = Color3.fromRGB(200, 120, 170),
		InputFocused = Color3.fromRGB(200, 200, 200),
		InputIndicator = Color3.fromRGB(170, 150, 190),
		InputIndicatorFocus = Color3.fromRGB(252,209,215),

		Dialog = Color3.fromRGB(120, 50, 75),
		DialogHolder = Color3.fromRGB(95, 40, 60),
		DialogHolderLine = Color3.fromRGB(90, 35, 55),
		DialogButton = Color3.fromRGB(120, 50, 75),
		DialogButtonBorder = Color3.fromRGB(155, 90, 115),
		DialogBorder = Color3.fromRGB(100, 70, 90),
		DialogInput = Color3.fromRGB(135, 55, 80),
		DialogInputLine = Color3.fromRGB(190, 160, 180),

		Text = Color3.fromRGB(240, 240, 240),
		SubText = Color3.fromRGB(220, 220, 220),
		Hover = Color3.fromRGB(200, 120, 170),
		HoverChange = 0.04,
	}
}

local Library = {
	Version = "1.1.0",

	OpenFrames = {},
	Options = {},
	Themes = Themes.Names,

	Window = nil,
	WindowFrame = nil,
	Unloaded = false,

	Creator = nil,

	DialogOpen = false,
	UseAcrylic = false,
	Acrylic = false,
	Transparency = true,
	MinimizeKeybind = nil,
	MinimizerIcon = nil,
	MinimizeKey = Enum.KeyCode.LeftControl,
}

local function isMotor(value)
	local motorType = tostring(value):match("^Motor%((.+)%)$")

	if motorType then
		return true, motorType
	else
		return false
	end
end

local Connection = {}

Connection.__index = Connection

function Connection.new(signal, handler)
	return setmetatable({
		signal = signal,
		connected = true,
		_handler = handler,
	}, Connection)
end

function Connection:disconnect()
	if self.connected then
		self.connected = false

		for index, connection in pairs(self.signal._connections) do
			if connection == self then
				table.remove(self.signal._connections, index)
				return
			end
		end
	end
end

local Signal = {}
Signal.__index = Signal

function Signal.new()
	return setmetatable({
		_connections = {},
		_threads = {},
	}, Signal)
end

function Signal:fire(...)
	for _, connection in pairs(self._connections) do
		connection._handler(...)
	end

	for _, thread in pairs(self._threads) do
		coroutine.resume(thread, ...)
	end

	self._threads = {}
end

function Signal:connect(handler)
	local connection = Connection.new(self, handler)
	table.insert(self._connections, connection)
	return connection
end

function Signal:wait()
	table.insert(self._threads, coroutine.running())
	return coroutine.yield()
end

local Linear = {}
Linear.__index = Linear

function Linear.new(targetValue, options)
	assert(targetValue, "Missing argument #1: targetValue")

	options = options or {}

	return setmetatable({
		_targetValue = targetValue,
		_velocity = options.velocity or 1,
	}, Linear)
end

function Linear:step(state, dt)
	local position = state.value
	local velocity = self._velocity -- Linear motion ignores the state's velocity
	local goal = self._targetValue

	local dPos = dt * velocity

	local complete = dPos >= math.abs(goal - position)
	position = position + dPos * (goal > position and 1 or -1)
	if complete then
		position = self._targetValue
		velocity = 0
	end

	return {
		complete = complete,
		value = position,
		velocity = velocity,
	}
end

local Instant = {}
Instant.__index = Instant

function Instant.new(targetValue)
	return setmetatable({
		_targetValue = targetValue,
	}, Instant)
end

function Instant:step()
	return {
		complete = true,
		value = self._targetValue,
	}
end

local VELOCITY_THRESHOLD = 0.001
local POSITION_THRESHOLD = 0.001

local EPS = 0.0001

local Spring = {}
Spring.__index = Spring

function Spring.new(targetValue, options)
	assert(targetValue, "Missing argument #1: targetValue")
	options = options or {}

	return setmetatable({
		_targetValue = targetValue,
		_frequency = options.frequency or 4,
		_dampingRatio = options.dampingRatio or 1,
	}, Spring)
end

function Spring:step(state, dt)
	-- Cache frequently used values and operations
	local d = self._dampingRatio
	local f = self._frequency * 2 * math.pi
	local g = self._targetValue
	local p0 = state.value
	local v0 = state.velocity or 0
	local offset = p0 - g
	local decay = math.exp(-d * f * dt)
	local p1, v1

	-- Pre-calculate common products
	local f_dt = f * dt
	local f_squared = f * f

	-- Move conditional branches outside for better prediction
	if d == 1 then -- Critically damped
		p1 = (offset * (1 + f_dt) + v0 * dt) * decay + g
		v1 = (v0 * (1 - f_dt) - offset * (f_squared * dt)) * decay
	elseif d < 1 then -- Underdamped
		local c = math.sqrt(1 - d * d)
		local c_squared = c * c
		local f_c = f * c
		local f_c_dt = f_c * dt

		local i = math.cos(f_c_dt)
		local j = math.sin(f_c_dt)

		-- Optimize z calculation
		local z
		if c > EPS then
			z = j / c
		else
			local a = dt * f
			local a_squared = a * a
			local a_cubed = a_squared * a
			local c_squared_squared = c_squared * c_squared
			z = a + ((a_squared * c_squared_squared / 20 - c_squared) * a_cubed) / 6
		end

		-- Optimize y calculation
		local y
		if f_c > EPS then
			y = j / f_c
		else
			local b = f_c
			local b_squared = b * b
			local dt_squared = dt * dt
			local dt_cubed = dt_squared * dt
			y = dt + ((dt_squared * b_squared * b_squared / 20 - b_squared) * dt_cubed) / 6
		end

		p1 = (offset * (i + d * z) + v0 * y) * decay + g
		v1 = (v0 * (i - z * d) - offset * (z * f)) * decay
	else -- Overdamped
		local c = math.sqrt(d * d - 1)
		local r1 = -f * (d - c)
		local r2 = -f * (d + c)
		local co2 = (v0 - offset * r1) / (2 * f * c)
		local co1 = offset - co2
		local e1 = co1 * math.exp(r1 * dt)
		local e2 = co2 * math.exp(r2 * dt)
		p1 = e1 + e2 + g
		v1 = e1 * r1 + e2 * r2
	end

	-- Combine the threshold check for early returns
	if math.abs(v1) < VELOCITY_THRESHOLD and math.abs(p1 - g) < POSITION_THRESHOLD then
		return {
			complete = true,
			value = g,
			velocity = v1,
		}
	end

	return {
		complete = false,
		value = p1,
		velocity = v1,
	}
end

local noop = function() end

local BaseMotor = {}
BaseMotor.__index = BaseMotor

function BaseMotor.new()
	return setmetatable({
		_onStep = Signal.new(),
		_onStart = Signal.new(),
		_onComplete = Signal.new(),
	}, BaseMotor)
end

function BaseMotor:onStep(handler)
	return self._onStep:connect(handler)
end

function BaseMotor:onStart(handler)
	return self._onStart:connect(handler)
end

function BaseMotor:onComplete(handler)
	return self._onComplete:connect(handler)
end

function BaseMotor:start()
	if not self._connection then
		self._connection = RunService.RenderStepped:Connect(function(deltaTime)
			self:step(deltaTime)
		end)
	end
end

function BaseMotor:stop()
	if self._connection then
		self._connection:Disconnect()
		self._connection = nil
	end
end

BaseMotor.destroy = BaseMotor.stop

BaseMotor.step = noop
BaseMotor.getValue = noop
BaseMotor.setGoal = noop

function BaseMotor:__tostring()
	return "Motor"
end

local SingleMotor = setmetatable({}, BaseMotor)
SingleMotor.__index = SingleMotor

function SingleMotor.new(initialValue, useImplicitConnections)
	assert(initialValue, "Missing argument #1: initialValue")
	assert(typeof(initialValue) == "number", "initialValue must be a number!")

	local self = setmetatable(BaseMotor.new(), SingleMotor)

	if useImplicitConnections ~= nil then
		self._useImplicitConnections = useImplicitConnections
	else
		self._useImplicitConnections = true
	end

	self._goal = nil
	self._state = {
		complete = true,
		value = initialValue,
	}

	return self
end

function SingleMotor:step(deltaTime)
	if self._state.complete then
		return true
	end

	local newState = self._goal:step(self._state, deltaTime)

	self._state = newState
	self._onStep:fire(newState.value)

	if newState.complete then
		if self._useImplicitConnections then
			self:stop()
		end

		self._onComplete:fire()
	end

	return newState.complete
end

function SingleMotor:getValue()
	return self._state.value
end

function SingleMotor:setGoal(goal)
	self._state.complete = false
	self._goal = goal

	self._onStart:fire()

	if self._useImplicitConnections then
		self:start()
	end
end

function SingleMotor:__tostring()
	return "Motor(Single)"
end

local GroupMotor = setmetatable({}, BaseMotor)
GroupMotor.__index = GroupMotor

local function toMotor(value)
	if isMotor(value) then
		return value
	end

	local valueType = typeof(value)

	if valueType == "number" then
		return SingleMotor.new(value, false)
	elseif valueType == "table" then
		return GroupMotor.new(value, false)
	end

	error(("Unable to convert %q to motor; type %s is unsupported"):format(value, valueType), 2)
end

function GroupMotor.new(initialValues, useImplicitConnections)
	assert(initialValues, "Missing argument #1: initialValues")
	assert(typeof(initialValues) == "table", "initialValues must be a table!")
	assert(
		not initialValues.step,
		'initialValues contains disallowed property "step". Did you mean to put a table of values here?'
	)

	local self = setmetatable(BaseMotor.new(), GroupMotor)

	if useImplicitConnections ~= nil then
		self._useImplicitConnections = useImplicitConnections
	else
		self._useImplicitConnections = true
	end

	self._complete = true
	self._motors = {}

	for key, value in pairs(initialValues) do
		self._motors[key] = toMotor(value)
	end

	return self
end

function GroupMotor:step(deltaTime)
	if self._complete then
		return true
	end

	local allMotorsComplete = true

	for _, motor in pairs(self._motors) do
		local complete = motor:step(deltaTime)
		if not complete then
			-- If any of the sub-motors are incomplete, the group motor will not be complete either
			allMotorsComplete = false
		end
	end

	self._onStep:fire(self:getValue())

	if allMotorsComplete then
		if self._useImplicitConnections then
			self:stop()
		end

		self._complete = true
		self._onComplete:fire()
	end

	return allMotorsComplete
end

function GroupMotor:setGoal(goals)
	assert(not goals.step, 'goals contains disallowed property "step". Did you mean to put a table of goals here?')

	self._complete = false
	self._onStart:fire()

	for key, goal in pairs(goals) do
		local motor = assert(self._motors[key], ("Unknown motor for key %s"):format(key))
		motor:setGoal(goal)
	end

	if self._useImplicitConnections then
		self:start()
	end
end

function GroupMotor:getValue()
	local values = {}

	for key, motor in pairs(self._motors) do
		values[key] = motor:getValue()
	end

	return values
end

function GroupMotor:__tostring()
	return "Motor(Group)"
end

local Flipper = {
	SingleMotor = SingleMotor,
	GroupMotor = GroupMotor,

	Instant = Instant,
	Linear = Linear,
	Spring = Spring,

	isMotor = isMotor,
}

local Creator = {
	Registry = {},
	Signals = {},
	TransparencyMotors = {},
	DefaultProperties = {
		ScreenGui = {
			ResetOnSpawn = false,
			ZIndexBehavior = Enum.ZIndexBehavior.Sibling,
		},
		Frame = {
			BackgroundColor3 = Color3.new(1, 1, 1),
			BorderColor3 = Color3.new(0, 0, 0),
			BorderSizePixel = 0,
		},
		ScrollingFrame = {
			BackgroundColor3 = Color3.new(1, 1, 1),
			BorderColor3 = Color3.new(0, 0, 0),
			ScrollBarImageColor3 = Color3.new(0, 0, 0),
		},
		TextLabel = {
			BackgroundColor3 = Color3.new(1, 1, 1),
			BorderColor3 = Color3.new(0, 0, 0),
			Font = Enum.Font.SourceSans,
			Text = "",
			TextColor3 = Color3.new(0, 0, 0),
			BackgroundTransparency = 1,
			TextSize = 14,
			AutoLocalize = false,
		},
		TextButton = {
			BackgroundColor3 = Color3.new(1, 1, 1),
			BorderColor3 = Color3.new(0, 0, 0),
			AutoButtonColor = false,
			Font = Enum.Font.SourceSans,
			Text = "",
			TextColor3 = Color3.new(0, 0, 0),
			TextSize = 14,
		},
		TextBox = {
			BackgroundColor3 = Color3.new(1, 1, 1),
			BorderColor3 = Color3.new(0, 0, 0),
			ClearTextOnFocus = false,
			Font = Enum.Font.SourceSans,
			Text = "",
			TextColor3 = Color3.new(0, 0, 0),
			TextSize = 14,
		},
		ImageLabel = {
			BackgroundTransparency = 1,
			BackgroundColor3 = Color3.new(1, 1, 1),
			BorderColor3 = Color3.new(0, 0, 0),
			BorderSizePixel = 0,
		},
		ImageButton = {
			BackgroundColor3 = Color3.new(1, 1, 1),
			BorderColor3 = Color3.new(0, 0, 0),
			AutoButtonColor = false,
		},
		CanvasGroup = {
			BackgroundColor3 = Color3.new(1, 1, 1),
			BorderColor3 = Color3.new(0, 0, 0),
			BorderSizePixel = 0,
		},
	},
}

local function ApplyCustomProps(Object, Props)
	if Props.ThemeTag then
		Creator.AddThemeObject(Object, Props.ThemeTag)
	end
end

function Creator.AddSignal(Signal, Function)
	local Connected = Signal:Connect(Function)
	table.insert(Creator.Signals, Connected)
	return Connected
end

function Creator.Disconnect()
	for Idx = #Creator.Signals, 1, -1 do
		local Connection = table.remove(Creator.Signals, Idx)
		if Connection.Disconnect then
			Connection:Disconnect()
		end
	end
end

function Creator.UpdateTheme()
	for Instance, Object in next, Creator.Registry do
		for Property, ColorIdx in next, Object.Properties do
			local Theme_Property = Creator.GetThemeProperty(ColorIdx)
			if Theme_Property then
				Instance[Property] = Theme_Property
			end
		end
	end

	for _, Motor in next, Creator.TransparencyMotors do
		Motor:setGoal(Flipper.Instant.new(Creator.GetThemeProperty("ElementTransparency")))
	end
end

function Creator.AddThemeObject(Object, Properties)
	local Idx = #Creator.Registry + 1
	local Data = {
		Object = Object,
		Properties = Properties,
		Idx = Idx,
	}

	Creator.Registry[Object] = Data
	Creator.UpdateTheme()
	return Object
end

function Creator.OverrideTag(Object, Properties)
	Creator.Registry[Object].Properties = Properties
	Creator.UpdateTheme()
end

function Creator.GetThemeProperty(Property)
	if Themes[Library.Theme][Property] then
		return Themes[Library.Theme][Property]
	end
	return Themes["Dark"][Property]
end

function Creator.New(Name, Properties, Children)
	local Object = Instance.new(Name)

	-- Default properties
	for Name, Value in next, Creator.DefaultProperties[Name] or {} do
		Object[Name] = Value
	end

	-- Properties
	for Name, Value in next, Properties or {} do
		if Name ~= "ThemeTag" then
			Object[Name] = Value
		end
	end

	-- Children
	for _, Child in next, Children or {} do
		Child.Parent = Object
	end

	ApplyCustomProps(Object, Properties)
	return Object
end

function Creator.SpringMotor(Initial, Instance, Prop, IgnoreDialogCheck, ResetOnThemeChange)
	IgnoreDialogCheck = IgnoreDialogCheck or false
	ResetOnThemeChange = ResetOnThemeChange or false
	local Motor = Flipper.SingleMotor.new(Initial)
	Motor:onStep(function(value)
		Instance[Prop] = value
	end)

	if ResetOnThemeChange then
		table.insert(Creator.TransparencyMotors, Motor)
	end

	local function SetValue(Value, Ignore)
		Ignore = Ignore or false
		if not IgnoreDialogCheck then
			if not Ignore then
				if Prop == "BackgroundTransparency" and Library.DialogOpen then
					return
				end
			end
		end
		Motor:setGoal(Flipper.Spring.new(Value, { frequency = 8 }))
	end

	return Motor, SetValue
end

Library.Creator = Creator

local New = Creator.New


local LibraryID = "Roblox/Ui"

local PanelParent = LocalPlayer.PlayerGui
local Panel = PanelParent:FindFirstChild(LibraryID)
if Panel then
	Panel:Destroy()
end

local GUI = New("ScreenGui", {
	Parent = PanelParent,
	Name = LibraryID,
})

Library.GUI = GUI
ProtectGui(GUI)

function Library:SafeCallbackToggles(Title, Function, ...)
	if not Function then
		return
	end

	local Success, Event = pcall(Function, ...)
	if not Success then
		local _, i = Event:find(":%d+: ")

		if not i then
			return Library:Notify({
				Title = "Interface",
				Content = "Callback error",
				SubContent = Title,
				Duration = 5,
			})
		end

		return Library:Notify({
			Title = "Interface",
			Content = "Callback error",
			SubContent = Title,
			Duration = 5,
		})
	end
end
function Library:SafeCallback(Function, ...)
	if not Function then
		return
	end

	local Success, Event = pcall(Function, ...)
	if not Success then
		local _, i = Event:find(":%d+: ")

		if not i then
			return Library:Notify({
				Title = "Interface",
				Content = "Callback error",
				SubContent = Event,
				Duration = 5,
			})
		end

		return Library:Notify({
			Title = "Interface",
			Content = "Callback error",
			SubContent = Event:sub(i + 1),
			Duration = 5,
		})
	end
end

function Library:Round(Number, Factor)
	if Factor == 0 then
		return math.floor(Number)
	end
	Number = tostring(Number)
	return Number:find("%.") and tonumber(Number:sub(1, Number:find("%.") + Factor)) or Number
end

local function map(value, inMin, inMax, outMin, outMax)
	return (value - inMin) * (outMax - outMin) / (inMax - inMin) + outMin
end

local function viewportPointToWorld(location, distance)
	local unitRay = game:GetService("Workspace").CurrentCamera:ScreenPointToRay(location.X, location.Y)
	return unitRay.Origin + unitRay.Direction * distance
end

local function getOffset()
	local viewportSizeY = game:GetService("Workspace").CurrentCamera.ViewportSize.Y
	return map(viewportSizeY, 0, 2560, 8, 56)
end

local viewportPointToWorld, getOffset = unpack({ viewportPointToWorld, getOffset })

local BlurFolder = Instance.new("Folder", game:GetService("Workspace").CurrentCamera)

local function createAcrylic()
	local Part = Creator.New("Part", {
		Name = "Body",
		Color = Color3.new(0, 0, 0),
		Material = Enum.Material.Glass,
		Size = Vector3.new(1, 1, 0),
		Anchored = true,
		CanCollide = false,
		Locked = true,
		CastShadow = false,
		Transparency = 0.98,
	}, {
		Creator.New("SpecialMesh", {
			MeshType = Enum.MeshType.Brick,
			Offset = Vector3.new(0, 0, -0.000001),
		}),
	})

	return Part
end

function AcrylicBlur()
	local function createAcrylicBlur(distance)
		local cleanups = {}

		distance = distance or 0.001
		local positions = {
			topLeft = Vector2.new(),
			topRight = Vector2.new(),
			bottomRight = Vector2.new(),
		}
		local model = createAcrylic()
		model.Parent = BlurFolder

		local function updatePositions(size, position)
			positions.topLeft = position
			positions.topRight = position + Vector2.new(size.X, 0)
			positions.bottomRight = position + size
		end

		local function render()
			local res = game:GetService("Workspace").CurrentCamera
			if res then
				res = res.CFrame
			end
			local cond = res
			if not cond then
				cond = CFrame.new()
			end

			local camera = cond
			local topLeft = positions.topLeft
			local topRight = positions.topRight
			local bottomRight = positions.bottomRight

			local topLeft3D = viewportPointToWorld(topLeft, distance)
			local topRight3D = viewportPointToWorld(topRight, distance)
			local bottomRight3D = viewportPointToWorld(bottomRight, distance)

			local width = (topRight3D - topLeft3D).Magnitude
			local height = (topRight3D - bottomRight3D).Magnitude

			model.CFrame =
				CFrame.fromMatrix((topLeft3D + bottomRight3D) / 2, camera.XVector, camera.YVector, camera.ZVector)
			model.Mesh.Scale = Vector3.new(width, height, 0)
		end

		local function onChange(rbx)
			local offset = getOffset()
			local size = rbx.AbsoluteSize - Vector2.new(offset, offset)
			local position = rbx.AbsolutePosition + Vector2.new(offset / 2, offset / 2)

			updatePositions(size, position)
			task.spawn(render)
		end

		local function renderOnChange()
			local camera = game:GetService("Workspace").CurrentCamera
			if not camera then
				return
			end

			table.insert(cleanups, camera:GetPropertyChangedSignal("CFrame"):Connect(render))
			table.insert(cleanups, camera:GetPropertyChangedSignal("ViewportSize"):Connect(render))
			table.insert(cleanups, camera:GetPropertyChangedSignal("FieldOfView"):Connect(render))
			task.spawn(render)
		end

		model.Destroying:Connect(function()
			for _, item in cleanups do
				pcall(function()
					item:Disconnect()
				end)
			end
		end)

		renderOnChange()

		return onChange, model
	end

	return function(distance)
		local Blur = {}
		local onChange, model = createAcrylicBlur(distance)

		local comp = Creator.New("Frame", {
			BackgroundTransparency = 1,
			Size = UDim2.fromScale(1, 1),
		})

		Creator.AddSignal(comp:GetPropertyChangedSignal("AbsolutePosition"), function()
			onChange(comp)
		end)

		Creator.AddSignal(comp:GetPropertyChangedSignal("AbsoluteSize"), function()
			onChange(comp)
		end)

		Blur.AddParent = function(Parent)
			Creator.AddSignal(Parent:GetPropertyChangedSignal("Visible"), function()
				Blur.SetVisibility(Parent.Visible)
			end)
		end

		Blur.SetVisibility = function(Value)
			model.Transparency = Value and 0.98 or 1
		end

		Blur.Frame = comp
		Blur.Model = model

		return Blur
	end
end

function AcrylicPaint()
	local New = Creator.New
	local AcrylicBlur = AcrylicBlur()

	return function(props)
		local AcrylicPaint = {}

		AcrylicPaint.Frame = New("Frame", {
			Size = UDim2.fromScale(1, 1),
			BackgroundTransparency = 0.9,
			BackgroundColor3 = Color3.fromRGB(255, 255, 255),
			BorderSizePixel = 0,
		}, {
			New("ImageLabel", {
				Image = "rbxassetid://8992230677",
				ScaleType = "Slice",
				SliceCenter = Rect.new(Vector2.new(99, 99), Vector2.new(99, 99)),
				AnchorPoint = Vector2.new(0.5, 0.5),
				Size = UDim2.new(1, 120, 1, 116),
				Position = UDim2.new(0.5, 0, 0.5, 0),
				BackgroundTransparency = 1,
				ImageColor3 = Color3.fromRGB(0, 0, 0),
				ImageTransparency = 0.7,
			}),

			New("UICorner", {
				CornerRadius = UDim.new(0, 8),
			}),

			New("Frame", {
				BackgroundTransparency = 0.45,
				Size = UDim2.fromScale(1, 1),
				Name = "Background",
				ThemeTag = {
					BackgroundColor3 = "AcrylicMain",
				},
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(0, 8),
				}),
			}),

			New("Frame", {
				BackgroundColor3 = Color3.fromRGB(255, 255, 255),
				BackgroundTransparency = 0.4,
				Size = UDim2.fromScale(1, 1),
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(0, 8),
				}),

				New("UIGradient", {
					Rotation = 90,
					ThemeTag = {
						Color = "AcrylicGradient",
					},
				}),
			}),

			New("ImageLabel", {
				Image = "rbxassetid://9968344105",
				ImageTransparency = 0.98,
				ScaleType = Enum.ScaleType.Tile,
				TileSize = UDim2.new(0, 128, 0, 128),
				Size = UDim2.fromScale(1, 1),
				BackgroundTransparency = 1,
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(0, 8),
				}),
			}),

			New("ImageLabel", {
				Image = "rbxassetid://9968344227",
				ImageTransparency = 0.9,
				ScaleType = Enum.ScaleType.Tile,
				TileSize = UDim2.new(0, 128, 0, 128),
				Size = UDim2.fromScale(1, 1),
				BackgroundTransparency = 1,
				ThemeTag = {
					ImageTransparency = "AcrylicNoise",
				},
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(0, 8),
				}),
			}),

			New("Frame", {
				BackgroundTransparency = 1,
				Size = UDim2.fromScale(1, 1),
				ZIndex = 2,
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(0, 8),
				}),
				New("UIStroke", {
					Transparency = 0.5,
					Thickness = 1,
					ThemeTag = {
						Color = "AcrylicBorder",
					},
				}),
			}),
		})

		local Blur

		if Library.UseAcrylic then
			Blur = AcrylicBlur()
			Blur.Frame.Parent = AcrylicPaint.Frame
			AcrylicPaint.Model = Blur.Model
			AcrylicPaint.AddParent = Blur.AddParent
			AcrylicPaint.SetVisibility = Blur.SetVisibility
		end

		return AcrylicPaint
	end
end

local Acrylic = {
	AcrylicBlur = AcrylicBlur(),
	CreateAcrylic = createAcrylic,
	AcrylicPaint = AcrylicPaint(),
}

function Acrylic.init()
	local baseEffect = Instance.new("DepthOfFieldEffect")
	baseEffect.FarIntensity = 0
	baseEffect.InFocusRadius = 0.1
	baseEffect.NearIntensity = 1

	local depthOfFieldDefaults = {}

	function Acrylic.Enable()
		for _, effect in pairs(depthOfFieldDefaults) do
			effect.Enabled = false
		end
		baseEffect.Parent = game:GetService("Lighting")
	end

	function Acrylic.Disable()
		for _, effect in pairs(depthOfFieldDefaults) do
			effect.Enabled = effect.enabled
		end
		baseEffect.Parent = nil
	end

	local function registerDefaults()
		local function register(object)
			if object:IsA("DepthOfFieldEffect") then
				depthOfFieldDefaults[object] = { enabled = object.Enabled }
			end
		end

		for _, child in pairs(game:GetService("Lighting"):GetChildren()) do
			register(child)
		end

		if game:GetService("Workspace").CurrentCamera then
			for _, child in pairs(game:GetService("Workspace").CurrentCamera:GetChildren()) do
				register(child)
			end
		end
	end

	registerDefaults()
	Acrylic.Enable()
end

local Components = {
	Assets = {
		Close = "rbxassetid://9886659671",
		Min = "rbxassetid://9886659276",
		Max = "rbxassetid://9886659406",
		Restore = "rbxassetid://9886659001",
	},
}

local New = Creator.New
local Spring = Flipper.Spring.new
local Instant = Flipper.Instant.new
local AddSignal = Creator.AddSignal

Components.Element = function(Title, Desc, Parent, Hover, Options)
	local Element = { Original = { Text = "" } }
	local Options = Options or {}

	Element.TitleLabel = New("TextLabel", {
		FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json", Enum.FontWeight.Medium, Enum.FontStyle.Normal),
		Text = Title,
		TextColor3 = Color3.fromRGB(240, 240, 240),
		TextSize = 13,
		TextXAlignment = Enum.TextXAlignment.Left,
		Size = UDim2.new(1, 0, 0, 14),
		BackgroundColor3 = Color3.fromRGB(255, 255, 255),
		BackgroundTransparency = 1,
		AutoLocalize = false,
		ThemeTag = {
			TextColor3 = "Text",
		},
	})

	Element.DescLabel = New("TextLabel", {
		FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json"),
		Text = Desc,
		TextColor3 = Color3.fromRGB(200, 200, 200),
		TextSize = 12,
		TextWrapped = true,
		TextXAlignment = Enum.TextXAlignment.Left,
		BackgroundColor3 = Color3.fromRGB(255, 255, 255),
		AutomaticSize = Enum.AutomaticSize.Y,
		BackgroundTransparency = 1,
		Size = UDim2.new(1, 0, 0, 14),
		AutoLocalize = false,
		ThemeTag = {
			TextColor3 = "SubText",
		},
	})

	Element.LabelHolder = New("Frame", {
		AutomaticSize = Enum.AutomaticSize.Y,
		BackgroundColor3 = Color3.fromRGB(255, 255, 255),
		BackgroundTransparency = 1,
		Position = UDim2.fromOffset(10, 0),
		Size = UDim2.new(1, -28, 0, 0),
	}, {
		New("UIListLayout", {
			SortOrder = Enum.SortOrder.LayoutOrder,
			VerticalAlignment = Enum.VerticalAlignment.Center,
		}),
		New("UIPadding", {
			PaddingBottom = UDim.new(0, 13),
			PaddingTop = UDim.new(0, 13),
		}),
		Element.TitleLabel,
		Element.DescLabel,
	})

	Element.Border = New("UIStroke", {
		Transparency = 0.5,
		ApplyStrokeMode = Enum.ApplyStrokeMode.Border,
		Color = Color3.fromRGB(0, 0, 0),
		ThemeTag = {
			Color = "ElementBorder",
		},
	})

	Element.Frame = New("TextButton", {
		Visible = Options.Visible and Options.Visible or true,
		Size = UDim2.new(1, 0, 0, 0),
		BackgroundTransparency = 0.89,
		BackgroundColor3 = Color3.fromRGB(130, 130, 130),
		Parent = Parent,
		AutomaticSize = Enum.AutomaticSize.Y,
		Text = "",
		LayoutOrder = 7,
		ThemeTag = {
			BackgroundColor3 = "Element",
			BackgroundTransparency = "ElementTransparency",
		},
	}, {
		New("UICorner", {
			CornerRadius = UDim.new(0, 4),
		}),
		Element.Border,
		Element.LabelHolder,
	})

	function Element:SetTitle(Set)
		Element.TitleLabel.Text = Set
	end

	function Element:Visible(Bool)
		Element.Frame.Visible = Bool
	end

	function Element:SetDesc(Set)
		if Set == nil then
			Set = ""
		end
		if Set == "" then
			Element.DescLabel.Visible = false
		else
			Element.DescLabel.Visible = true
		end
		Element.DescLabel.Text = Set
	end

	function Element:AddText(Add)
		if not string.find(Element.TitleLabel.Text, Add, 1, true) then
			Element.TitleLabel.Text = Element.TitleLabel.Text .. "" .. Add
		end
	end

	function Element:GetOriginalText()
		return Element.Original.Text
	end

	function Element:GetTitle()
		return Element.TitleLabel.Text
	end

	function Element:GetDesc()
		return Element.DescLabel.Text
	end

	function Element:Destroy()
		Element.Frame:Destroy()
	end

	Element:SetTitle(Title)
	Element:SetDesc(Desc)

	Element.Original.Text = Title

	if Hover then
		local Themes = Library.Themes
		local Motor, SetTransparency = Creator.SpringMotor(
			Creator.GetThemeProperty("ElementTransparency"),
			Element.Frame,
			"BackgroundTransparency",
			false,
			true
		)

		Creator.AddSignal(Element.Frame.MouseEnter, function()
			SetTransparency(Creator.GetThemeProperty("ElementTransparency") - Creator.GetThemeProperty("HoverChange"))
		end)
		Creator.AddSignal(Element.Frame.MouseLeave, function()
			SetTransparency(Creator.GetThemeProperty("ElementTransparency"))
		end)
		Creator.AddSignal(Element.Frame.MouseButton1Down, function()
			SetTransparency(Creator.GetThemeProperty("ElementTransparency") + Creator.GetThemeProperty("HoverChange"))
		end)
		Creator.AddSignal(Element.Frame.MouseButton1Up, function()
			SetTransparency(Creator.GetThemeProperty("ElementTransparency") - Creator.GetThemeProperty("HoverChange"))
		end)
	end

	return Element
end
Components.Section = function(Title, Parent)
	local Section = {}

	Section.Layout = New("UIListLayout", {
		Padding = UDim.new(0, 5),
	})

	Section.Container = New("Frame", {
		Size = UDim2.new(1, 0, 0, 26),
		Position = UDim2.fromOffset(0, 24),
		BackgroundTransparency = 1,
	}, {
		Section.Layout,
	})

	Section.Root = New("Frame", {
		BackgroundTransparency = 1,
		Size = UDim2.new(1, 0, 0, 26),
		LayoutOrder = 7,
		Parent = Parent,
	}, {
		New("TextLabel", {
			RichText = true,
			Text = Title,
			TextTransparency = 0,
			FontFace = Font.new("rbxassetid://12187365364", Enum.FontWeight.SemiBold, Enum.FontStyle.Normal),
			TextSize = 18,
			TextXAlignment = "Left",
			TextYAlignment = "Center",
			Size = UDim2.new(1, -16, 0, 18),
			Position = UDim2.fromOffset(0, 2),
			AutoLocalize = false,
			ThemeTag = {
				TextColor3 = "Text",
			},
		}),
		Section.Container,
	})

	Creator.AddSignal(Section.Layout:GetPropertyChangedSignal("AbsoluteContentSize"), function()
		Section.Container.Size = UDim2.new(1, 0, 0, Section.Layout.AbsoluteContentSize.Y)
		Section.Root.Size = UDim2.new(1, 0, 0, Section.Layout.AbsoluteContentSize.Y + 25)
	end)

	return Section
end
Components.Tab = (function()
	local Components = Components

	local TabModule = {
		Window = nil,
		Tabs = {},
		Containers = {},
		SelectedTab = 0,
		TabCount = 0,
		Callback = function()end
	}

	function TabModule:Init(Window)
		TabModule.Window = Window
		return TabModule
	end

	function TabModule:GetCurrentTabPos()
		local TabHolderPos = TabModule.Window.TabHolder.AbsolutePosition.Y
		local TabPos = TabModule.Tabs[TabModule.SelectedTab].Frame.AbsolutePosition.Y

		return TabPos - TabHolderPos
	end

	function TabModule:New(Title, Icon, Parent)
		local Window = TabModule.Window
		local Elements = Library.Elements

		TabModule.TabCount = TabModule.TabCount + 1
		local TabIndex = TabModule.TabCount

		local Tab = {
			Selected = false,
			Name = Title,
			Type = "Tab",
		}

		if Library:GetIcon(Icon) then
			Icon = Library:GetIcon(Icon)
		end

		if Icon == "" or nil then
			Icon = nil
		end

		Tab.Frame = New("TextButton", {
			Size = UDim2.new(1, 0, 0, 34),
			BackgroundTransparency = 1,
			Parent = Parent,
			ThemeTag = {
				BackgroundColor3 = "Tab",
			},
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(0, 6),
			}),
			New("TextLabel", {
				AnchorPoint = Vector2.new(0, 0.5),
				Position = Icon and UDim2.new(0, 30, 0.5, 0) or UDim2.new(0, 12, 0.5, 0),
				Text = Title,
				RichText = true,
				TextColor3 = Color3.fromRGB(255, 255, 255),
				TextTransparency = 0,
				FontFace = Font.new(
					"rbxasset://fonts/families/GothamSSm.json",
					Enum.FontWeight.Regular,
					Enum.FontStyle.Normal
				),
				TextSize = 12,
				TextXAlignment = "Left",
				TextYAlignment = "Center",
				Size = UDim2.new(1, -12, 1, 0),
				BackgroundTransparency = 1,
				AutoLocalize = false,
				ThemeTag = {
					TextColor3 = "Text",
				},
			}),
			New("ImageLabel", {
				AnchorPoint = Vector2.new(0, 0.5),
				Size = UDim2.fromOffset(16, 16),
				Position = UDim2.new(0, 8, 0.5, 0),
				BackgroundTransparency = 1,
				Image = Icon and Icon or nil,
				ThemeTag = {
					ImageColor3 = "Text",
				},
			}),
		})

		local ContainerLayout = New("UIListLayout", {
			Padding = UDim.new(0, 5),
			SortOrder = Enum.SortOrder.LayoutOrder,
		})

		Tab.ContainerFrame = New("ScrollingFrame", {
			Size = UDim2.fromScale(1, 1),
			BackgroundTransparency = 1,
			Parent = Window.ContainerHolder,
			Visible = false,
			BottomImage = "rbxassetid://6889812791",
			MidImage = "rbxassetid://6889812721",
			TopImage = "rbxassetid://6276641225",
			ScrollBarImageColor3 = Color3.fromRGB(255, 255, 255),
			ScrollBarImageTransparency = 0.95,
			ScrollBarThickness = 3,
			BorderSizePixel = 0,
			CanvasSize = UDim2.fromScale(0, 0),
			ScrollingDirection = Enum.ScrollingDirection.Y,
		}, {
			ContainerLayout,
			New("UIPadding", {
				PaddingRight = UDim.new(0, 10),
				PaddingLeft = UDim.new(0, 1),
				PaddingTop = UDim.new(0, 1),
				PaddingBottom = UDim.new(0, 1),
			}),
		})

		Creator.AddSignal(ContainerLayout:GetPropertyChangedSignal("AbsoluteContentSize"), function()
			Tab.ContainerFrame.CanvasSize = UDim2.new(0, 0, 0, ContainerLayout.AbsoluteContentSize.Y + 2)
		end)

		Tab.Motor, Tab.SetTransparency = Creator.SpringMotor(1, Tab.Frame, "BackgroundTransparency")

		Creator.AddSignal(Tab.Frame.MouseEnter, function()
			Tab.SetTransparency(Tab.Selected and 0.85 or 0.89)
		end)
		Creator.AddSignal(Tab.Frame.MouseLeave, function()
			Tab.SetTransparency(Tab.Selected and 0.89 or 1)
		end)
		Creator.AddSignal(Tab.Frame.MouseButton1Down, function()
			Tab.SetTransparency(0.92)
		end)
		Creator.AddSignal(Tab.Frame.MouseButton1Up, function()
			Tab.SetTransparency(Tab.Selected and 0.85 or 0.89)
		end)
		Creator.AddSignal(Tab.Frame.MouseButton1Click, function()
			TabModule:SelectTab(TabIndex)
			TabModule.Callback(TabIndex)
		end)

		TabModule.Containers[TabIndex] = Tab.ContainerFrame
		TabModule.Tabs[TabIndex] = Tab

		Tab.Container = Tab.ContainerFrame
		Tab.ScrollFrame = Tab.Container

		function Tab:AddSection(SectionTitle)
			local Section = { Type = "Section" }

			local SectionFrame = Components.Section(SectionTitle, Tab.Container)
			Section.Container = SectionFrame.Container
			Section.ScrollFrame = Tab.Container

			setmetatable(Section, Elements)
			return Section
		end

		setmetatable(Tab, Elements)
		return Tab
	end

	function TabModule:GetCurrentTab()
		return self.SelectedTab
	end

	function TabModule:SelectTab(Tab)
		local Window = TabModule.Window

		TabModule.SelectedTab = Tab

		for _, TabObject in next, TabModule.Tabs do
			TabObject.SetTransparency(1)
			TabObject.Selected = false
		end
		TabModule.Tabs[Tab].SetTransparency(0.89)
		TabModule.Tabs[Tab].Selected = true

		Window.TabDisplay.Text = TabModule.Tabs[Tab].Name
		Window.SelectorPosMotor:setGoal(Spring(TabModule:GetCurrentTabPos(), { frequency = 6 }))

		task.spawn(function()
			Window.ContainerHolder.Parent = Window.ContainerAnim

			Window.ContainerPosMotor:setGoal(Spring(15, { frequency = 10 }))
			Window.ContainerBackMotor:setGoal(Spring(1, { frequency = 10 }))
			task.wait(0.12)
			for _, Container in next, TabModule.Containers do
				Container.Visible = false
			end
			TabModule.Containers[Tab].Visible = true
			Window.ContainerPosMotor:setGoal(Spring(0, { frequency = 5 }))
			Window.ContainerBackMotor:setGoal(Spring(0, { frequency = 8 }))
			task.wait(0.12)
			Window.ContainerHolder.Parent = Window.ContainerCanvas
		end)
	end

	return TabModule
end)()
Components.Button = function(Theme, Parent, DialogCheck)
	DialogCheck = DialogCheck or false
	local Button = {}

	Button.Title = New("TextLabel", {
		FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json"),
		TextColor3 = Color3.fromRGB(200, 200, 200),
		TextSize = 14,
		TextWrapped = true,
		TextXAlignment = Enum.TextXAlignment.Center,
		TextYAlignment = Enum.TextYAlignment.Center,
		BackgroundColor3 = Color3.fromRGB(255, 255, 255),
		AutomaticSize = Enum.AutomaticSize.Y,
		BackgroundTransparency = 1,
		Size = UDim2.fromScale(1, 1),
		AutoLocalize = false,
		ThemeTag = {
			TextColor3 = "Text",
		},
	})

	Button.HoverFrame = New("Frame", {
		Size = UDim2.fromScale(1, 1),
		BackgroundTransparency = 1,
		ThemeTag = {
			BackgroundColor3 = "Hover",
		},
	}, {
		New("UICorner", {
			CornerRadius = UDim.new(0, 4),
		}),
	})

	Button.Frame = New("TextButton", {
		Size = UDim2.new(0, 0, 0, 32),
		Parent = Parent,
		ThemeTag = {
			BackgroundColor3 = "DialogButton",
		},
	}, {
		New("UICorner", {
			CornerRadius = UDim.new(0, 4),
		}),
		New("UIStroke", {
			ApplyStrokeMode = Enum.ApplyStrokeMode.Border,
			Transparency = 0.65,
			ThemeTag = {
				Color = "DialogButtonBorder",
			},
		}),
		Button.HoverFrame,
		Button.Title,
	})

	local Motor, SetTransparency = Creator.SpringMotor(1, Button.HoverFrame, "BackgroundTransparency", DialogCheck)
	Creator.AddSignal(Button.Frame.MouseEnter, function()
		SetTransparency(0.97)
	end)
	Creator.AddSignal(Button.Frame.MouseLeave, function()
		SetTransparency(1)
	end)
	Creator.AddSignal(Button.Frame.MouseButton1Down, function()
		SetTransparency(1)
	end)
	Creator.AddSignal(Button.Frame.MouseButton1Up, function()
		SetTransparency(0.97)
	end)

	return Button
end
Components.Dialog = (function()
	local Spring = Flipper.Spring.new
	local Instant = Flipper.Instant.new
	local New = Creator.New

	local Dialog = {
		Window = nil,
	}

	function Dialog:Init(Window)
		Dialog.Window = Window
		return Dialog
	end

	function Dialog:Create()
		local NewDialog = {
			Buttons = 0,
		}

		NewDialog.TintFrame = New("TextButton", {
			Text = "",
			Size = UDim2.fromScale(1, 1),
			BackgroundColor3 = Color3.fromRGB(0, 0, 0),
			BackgroundTransparency = 1,
			Parent = Dialog.Window.Root,
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(0, 8),
			}),
		})

		local TintMotor, TintTransparency = Creator.SpringMotor(1, NewDialog.TintFrame, "BackgroundTransparency", true)

		NewDialog.ButtonHolder = New("Frame", {
			Size = UDim2.new(1, -40, 1, -40),
			AnchorPoint = Vector2.new(0.5, 0.5),
			Position = UDim2.fromScale(0.5, 0.5),
			BackgroundTransparency = 1,
		}, {
			New("UIListLayout", {
				Padding = UDim.new(0, 10),
				FillDirection = Enum.FillDirection.Horizontal,
				HorizontalAlignment = Enum.HorizontalAlignment.Center,
				SortOrder = Enum.SortOrder.LayoutOrder,
			}),
		})

		NewDialog.ButtonHolderFrame = New("Frame", {
			Size = UDim2.new(1, 0, 0, 70),
			Position = UDim2.new(0, 0, 1, -70),
			ThemeTag = {
				BackgroundColor3 = "DialogHolder",
			},
		}, {
			New("Frame", {
				Size = UDim2.new(1, 0, 0, 1),
				ThemeTag = {
					BackgroundColor3 = "DialogHolderLine",
				},
			}),
			NewDialog.ButtonHolder,
		})

		NewDialog.Title = New("TextLabel", {
			FontFace = Font.new(
				"rbxasset://fonts/families/GothamSSm.json",
				Enum.FontWeight.SemiBold,
				Enum.FontStyle.Normal
			),
			Text = "Dialog",
			TextColor3 = Color3.fromRGB(240, 240, 240),
			TextSize = 22,
			TextXAlignment = Enum.TextXAlignment.Left,
			Size = UDim2.new(1, 0, 0, 22),
			Position = UDim2.fromOffset(20, 25),
			BackgroundColor3 = Color3.fromRGB(255, 255, 255),
			BackgroundTransparency = 1,
			AutoLocalize = false,
			ThemeTag = {
				TextColor3 = "Text",
			},
		})

		NewDialog.Scale = New("UIScale", {
			Scale = 1,
		})

		local ScaleMotor, Scale = Creator.SpringMotor(1.1, NewDialog.Scale, "Scale")

		NewDialog.Root = New("CanvasGroup", {
			Size = UDim2.fromOffset(300, 165),
			AnchorPoint = Vector2.new(0.5, 0.5),
			Position = UDim2.fromScale(0.5, 0.5),
			GroupTransparency = 1,
			Parent = NewDialog.TintFrame,
			ThemeTag = {
				BackgroundColor3 = "Dialog",
			},
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(0, 8),
			}),
			New("UIStroke", {
				Transparency = 0.5,
				ThemeTag = {
					Color = "DialogBorder",
				},
			}),
			NewDialog.Scale,
			NewDialog.Title,
			NewDialog.ButtonHolderFrame,
		})

		local RootMotor, RootTransparency = Creator.SpringMotor(1, NewDialog.Root, "GroupTransparency")

		function NewDialog:Open()
			Library.DialogOpen = true
			NewDialog.Scale.Scale = 1.1
			TintTransparency(0.75)
			RootTransparency(0)
			Scale(1)
		end

		function NewDialog:Close()
			Library.DialogOpen = false
			TintTransparency(1)
			RootTransparency(1)
			Scale(1.1)
			NewDialog.Root.UIStroke:Destroy()
			task.wait(0.15)
			NewDialog.TintFrame:Destroy()
		end

		function NewDialog:Button(Title, Callback)
			NewDialog.Buttons = NewDialog.Buttons + 1
			Title = Title or "Button"
			Callback = Callback or function() end

			local Button = Components.Button("", NewDialog.ButtonHolder, true)
			Button.Title.Text = Title

			for _, Btn in next, NewDialog.ButtonHolder:GetChildren() do
				if Btn:IsA("TextButton") then
					Btn.Size =
						UDim2.new(1 / NewDialog.Buttons, -(((NewDialog.Buttons - 1) * 10) / NewDialog.Buttons), 0, 32)
				end
			end

			Creator.AddSignal(Button.Frame.MouseButton1Click, function()
				Library:SafeCallback(Callback)
				pcall(function()
					NewDialog:Close()
				end)
			end)

			return Button
		end

		return NewDialog
	end

	return Dialog
end)()
Components.Notification = (function()
	local Spring = Flipper.Spring.new
	local Instant = Flipper.Instant.new
	local New = Creator.New

	local Notification = {}

	function Notification:Init(GUI)
		Notification.Holder = New("Frame", {
			Position = UDim2.new(1, -30, 1, -30),
			Size = UDim2.new(0, 310, 1, -30),
			AnchorPoint = Vector2.new(1, 1),
			BackgroundTransparency = 1,
			Parent = GUI,
		}, {
			New("UIListLayout", {
				HorizontalAlignment = Enum.HorizontalAlignment.Center,
				SortOrder = Enum.SortOrder.LayoutOrder,
				VerticalAlignment = Enum.VerticalAlignment.Bottom,
				Padding = UDim.new(0, 20),
			}),
		})
	end

	function Notification:New(Config)
		Config.Title = Config.Title or "Title"
		Config.Content = Config.Content or "Content"
		Config.SubContent = Config.SubContent or ""
		Config.Duration = Config.Duration or nil
		Config.Buttons = Config.Buttons or {}
		local NewNotification = {
			Closed = false,
		}

		NewNotification.AcrylicPaint = Acrylic.AcrylicPaint()

		NewNotification.Title = New("TextLabel", {
			Position = UDim2.new(0, 14, 0, 17),
			Text = Config.Title,
			RichText = true,
			TextColor3 = Color3.fromRGB(255, 255, 255),
			TextTransparency = 0,
			FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json"),
			TextSize = 13,
			TextXAlignment = "Left",
			TextYAlignment = "Center",
			Size = UDim2.new(1, -12, 0, 12),
			TextWrapped = true,
			BackgroundTransparency = 1,
			AutoLocalize = false,
			ThemeTag = {
				TextColor3 = "Text",
			},
		})

		NewNotification.ContentLabel = New("TextLabel", {
			FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json"),
			Text = Config.Content,
			TextColor3 = Color3.fromRGB(240, 240, 240),
			TextSize = 14,
			TextXAlignment = Enum.TextXAlignment.Left,
			AutomaticSize = Enum.AutomaticSize.Y,
			Size = UDim2.new(1, 0, 0, 14),
			BackgroundColor3 = Color3.fromRGB(255, 255, 255),
			BackgroundTransparency = 1,
			TextWrapped = true,
			AutoLocalize = false,
			ThemeTag = {
				TextColor3 = "Text",
			},
		})

		NewNotification.SubContentLabel = New("TextLabel", {
			FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json"),
			Text = Config.SubContent,
			TextColor3 = Color3.fromRGB(240, 240, 240),
			TextSize = 14,
			TextXAlignment = Enum.TextXAlignment.Left,
			AutomaticSize = Enum.AutomaticSize.Y,
			Size = UDim2.new(1, 0, 0, 14),
			BackgroundColor3 = Color3.fromRGB(255, 255, 255),
			BackgroundTransparency = 1,
			TextWrapped = true,
			AutoLocalize = false,
			ThemeTag = {
				TextColor3 = "SubText",
			},
		})

		NewNotification.LabelHolder = New("Frame", {
			AutomaticSize = Enum.AutomaticSize.Y,
			BackgroundColor3 = Color3.fromRGB(255, 255, 255),
			BackgroundTransparency = 1,
			Position = UDim2.fromOffset(14, 40),
			Size = UDim2.new(1, -28, 0, 0),
		}, {
			New("UIListLayout", {
				SortOrder = Enum.SortOrder.LayoutOrder,
				VerticalAlignment = Enum.VerticalAlignment.Center,
				Padding = UDim.new(0, 3),
			}),
			NewNotification.ContentLabel,
			NewNotification.SubContentLabel,
		})

		NewNotification.CloseButton = New("TextButton", {
			Text = "",
			Position = UDim2.new(1, -14, 0, 13),
			Size = UDim2.fromOffset(20, 20),
			AnchorPoint = Vector2.new(1, 0),
			BackgroundTransparency = 1,
		}, {
			New("ImageLabel", {
				Image = Components.Close,
				Size = UDim2.fromOffset(16, 16),
				Position = UDim2.fromScale(0.5, 0.5),
				AnchorPoint = Vector2.new(0.5, 0.5),
				BackgroundTransparency = 1,
				ThemeTag = {
					ImageColor3 = "Text",
				},
			}),
		})

		NewNotification.Root = New("Frame", {
			BackgroundTransparency = 1,
			Size = UDim2.new(1, 0, 1, 0),
			Position = UDim2.fromScale(1, 0),
		}, {
			NewNotification.AcrylicPaint.Frame,
			NewNotification.Title,
			NewNotification.CloseButton,
			NewNotification.LabelHolder,
		})

		if Config.Content == "" then
			NewNotification.ContentLabel.Visible = false
		end

		if Config.SubContent == "" then
			NewNotification.SubContentLabel.Visible = false
		end

		NewNotification.Holder = New("Frame", {
			BackgroundTransparency = 1,
			Size = UDim2.new(1, 0, 0, 200),
			Parent = Notification.Holder,
		}, {
			NewNotification.Root,
		})

		local RootMotor = Flipper.GroupMotor.new({
			Scale = 1,
			Offset = 60,
		})

		RootMotor:onStep(function(Values)
			NewNotification.Root.Position = UDim2.new(Values.Scale, Values.Offset, 0, 0)
		end)

		Creator.AddSignal(NewNotification.CloseButton.MouseButton1Click, function()
			NewNotification:Close()
		end)

		function NewNotification:Open()
			local ContentSize = NewNotification.LabelHolder.AbsoluteSize.Y
			NewNotification.Holder.Size = UDim2.new(1, 0, 0, 58 + ContentSize)

			RootMotor:setGoal({
				Scale = Spring(0, { frequency = 5 }),
				Offset = Spring(0, { frequency = 5 }),
			})
		end

		function NewNotification:Close()
			if not NewNotification.Closed then
				NewNotification.Closed = true
				task.spawn(function()
					RootMotor:setGoal({
						Scale = Spring(1, { frequency = 5 }),
						Offset = Spring(60, { frequency = 5 }),
					})
					task.wait(0.4)
					if Library.UseAcrylic then
						NewNotification.AcrylicPaint.Model:Destroy()
					end
					NewNotification.Holder:Destroy()
				end)
			end
		end

		NewNotification:Open()
		if Config.Duration then
			task.delay(Config.Duration, function()
				NewNotification:Close()
			end)
		end
		return NewNotification
	end

	return Notification
end)()
Components.Textbox = function(Parent, Acrylic)
	Acrylic = Acrylic or false
	local Textbox = {}

	Textbox.Input = New("TextBox", {
		FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json"),
		TextColor3 = Color3.fromRGB(200, 200, 200),
		TextSize = 14,
		TextXAlignment = Enum.TextXAlignment.Left,
		TextYAlignment = Enum.TextYAlignment.Center,
		BackgroundColor3 = Color3.fromRGB(255, 255, 255),
		AutomaticSize = Enum.AutomaticSize.Y,
		BackgroundTransparency = 1,
		Size = UDim2.fromScale(1, 1),
		Position = UDim2.fromOffset(10, 0),
		ThemeTag = {
			TextColor3 = "Text",
			PlaceholderColor3 = "SubText",
		},
	})

	Textbox.Container = New("Frame", {
		BackgroundTransparency = 1,
		ClipsDescendants = true,
		Position = UDim2.new(0, 6, 0, 0),
		Size = UDim2.new(1, -12, 1, 0),
	}, {
		Textbox.Input,
	})

	Textbox.Indicator = New("Frame", {
		Size = UDim2.new(1, -4, 0, 1),
		Position = UDim2.new(0, 2, 1, 0),
		AnchorPoint = Vector2.new(0, 1),
		BackgroundTransparency = Acrylic and 0.5 or 0,
		ThemeTag = {
			BackgroundColor3 = Acrylic and "InputIndicator" or "DialogInputLine",
		},
	})

	Textbox.Frame = New("Frame", {
		Size = UDim2.new(0, 0, 0, 30),
		BackgroundTransparency = Acrylic and 0.9 or 0,
		Parent = Parent,
		ThemeTag = {
			BackgroundColor3 = Acrylic and "Input" or "DialogInput",
		},
	}, {
		New("UICorner", {
			CornerRadius = UDim.new(0, 4),
		}),
		New("UIStroke", {
			ApplyStrokeMode = Enum.ApplyStrokeMode.Border,
			Transparency = Acrylic and 0.5 or 0.65,
			ThemeTag = {
				Color = Acrylic and "InElementBorder" or "DialogButtonBorder",
			},
		}),
		Textbox.Indicator,
		Textbox.Container,
	})

	local function Update()
		local PADDING = 2
		local Reveal = Textbox.Container.AbsoluteSize.X

		if not Textbox.Input:IsFocused() or Textbox.Input.TextBounds.X <= Reveal - 2 * PADDING then
			Textbox.Input.Position = UDim2.new(0, PADDING, 0, 0)
		else
			local Cursor = Textbox.Input.CursorPosition
			if Cursor ~= -1 then
				local subtext = string.sub(Textbox.Input.Text, 1, Cursor - 1)
				local width = TextService:GetTextSize(
					subtext,
					Textbox.Input.TextSize,
					Textbox.Input.Font,
					Vector2.new(math.huge, math.huge)
				).X

				local CurrentCursorPos = Textbox.Input.Position.X.Offset + width
				if CurrentCursorPos < PADDING then
					Textbox.Input.Position = UDim2.fromOffset(PADDING - width, 0)
				elseif CurrentCursorPos > Reveal - PADDING - 1 then
					Textbox.Input.Position = UDim2.fromOffset(Reveal - width - PADDING - 1, 0)
				end
			end
		end
	end

	task.spawn(Update)

	Creator.AddSignal(Textbox.Input:GetPropertyChangedSignal("Text"), Update)
	Creator.AddSignal(Textbox.Input:GetPropertyChangedSignal("CursorPosition"), Update)

	Creator.AddSignal(Textbox.Input.Focused, function()
		Update()
		Textbox.Indicator.Size = UDim2.new(1, -2, 0, 2)
		Textbox.Indicator.Position = UDim2.new(0, 1, 1, 0)
		Textbox.Indicator.BackgroundTransparency = 0
		Creator.OverrideTag(Textbox.Frame, { BackgroundColor3 = Acrylic and "InputFocused" or "DialogHolder" })
		Creator.OverrideTag(Textbox.Indicator, { BackgroundColor3 = "InputIndicatorFocus" })
	end)

	Creator.AddSignal(Textbox.Input.FocusLost, function()
		Update()
		Textbox.Indicator.Size = UDim2.new(1, -4, 0, 1)
		Textbox.Indicator.Position = UDim2.new(0, 2, 1, 0)
		Textbox.Indicator.BackgroundTransparency = 0.5
		Creator.OverrideTag(Textbox.Frame, { BackgroundColor3 = Acrylic and "Input" or "DialogInput" })
		Creator.OverrideTag(Textbox.Indicator, { BackgroundColor3 = Acrylic and "InputIndicator" or "DialogInputLine" })
	end)

	return Textbox
end
Components.TitleBar = function(Config)
	local TitleBar = {}

	local function BarButton(Icon, Pos, Parent, Callback)
		local Button = {
			Callback = Callback or function() end,
		}

		Button.Frame = New("TextButton", {
			Size = UDim2.new(0, 34, 1, -8),
			AnchorPoint = Vector2.new(1, 0),
			BackgroundTransparency = 1,
			Parent = Parent,
			Position = Pos,
			Text = "",
			ThemeTag = {
				BackgroundColor3 = "Text",
			},
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(0, 7),
			}),
			New("ImageLabel", {
				Image = Icon,
				Size = UDim2.fromOffset(16, 16),
				Position = UDim2.fromScale(0.5, 0.5),
				AnchorPoint = Vector2.new(0.5, 0.5),
				BackgroundTransparency = 1,
				Name = "Icon",
				ThemeTag = {
					ImageColor3 = "Text",
				},
			}),
		})

		local Motor, SetTransparency = Creator.SpringMotor(1, Button.Frame, "BackgroundTransparency")

		AddSignal(Button.Frame.MouseEnter, function()
			SetTransparency(0.94)
		end)
		AddSignal(Button.Frame.MouseLeave, function()
			SetTransparency(1, true)
		end)
		AddSignal(Button.Frame.MouseButton1Down, function()
			SetTransparency(0.96)
		end)
		AddSignal(Button.Frame.MouseButton1Up, function()
			SetTransparency(0.94)
		end)
		AddSignal(Button.Frame.MouseButton1Click, Button.Callback)

		Button.SetCallback = function(Func)
			Button.Callback = Func
		end

		return Button
	end

	TitleBar.Frame = New("Frame", {
		Size = UDim2.new(1, 0, 0, 42),
		BackgroundTransparency = 1,
		Parent = Config.Parent,
	}, {
		New("Frame", {
			Size = UDim2.new(1, -16, 1, 0),
			Position = UDim2.new(0, 16, 0, 0),
			BackgroundTransparency = 1,
		}, {
			New("UIListLayout", {
				Padding = UDim.new(0, 5),
				FillDirection = Enum.FillDirection.Horizontal,
				SortOrder = Enum.SortOrder.LayoutOrder,
			}),
			New("TextLabel", {
				RichText = true,
				Text = Config.Title,
				FontFace = Font.new(
					"rbxasset://fonts/families/GothamSSm.json",
					Enum.FontWeight.Regular,
					Enum.FontStyle.Normal
				),
				TextSize = 12,
				TextXAlignment = "Left",
				TextYAlignment = "Center",
				Size = UDim2.fromScale(0, 1),
				AutomaticSize = Enum.AutomaticSize.X,
				BackgroundTransparency = 1,
				AutoLocalize = false,
				ThemeTag = {
					TextColor3 = "Text",
				},
			}),
			New("TextLabel", {
				RichText = true,
				Text = Config.SubTitle,
				TextTransparency = 0.4,
				FontFace = Font.new(
					"rbxasset://fonts/families/GothamSSm.json",
					Enum.FontWeight.Regular,
					Enum.FontStyle.Normal
				),
				TextSize = 12,
				TextXAlignment = "Left",
				TextYAlignment = "Center",
				Size = UDim2.fromScale(0, 1),
				AutomaticSize = Enum.AutomaticSize.X,
				BackgroundTransparency = 1,
				AutoLocalize = false,
				ThemeTag = {
					TextColor3 = "Text",
				},
			}),
		}),
		New("Frame", {
			BackgroundTransparency = 0.5,
			Size = UDim2.new(1, 0, 0, 1),
			Position = UDim2.new(0, 0, 1, 0),
			ThemeTag = {
				BackgroundColor3 = "TitleBarLine",
			},
		}),
	})

	TitleBar.CloseButton = BarButton(Components.Assets.Close, UDim2.new(1, -4, 0, 4), TitleBar.Frame, function()
		Library.Window:Dialog({
			Title = "Close",
			Content = "Are you sure you want to unload the interface?",
			Buttons = {
				{
					Title = "Yes",
					Callback = function()
						Library:Destroy()
					end,
				},
				{
					Title = "No",
				},
			},
		})
	end)
	TitleBar.MaxButton = BarButton(Components.Assets.Max, UDim2.new(1, -40, 0, 4), TitleBar.Frame, function()
		Config.Window.Maximize(not Config.Window.Maximized)
	end)
	TitleBar.MinButton = BarButton(Components.Assets.Min, UDim2.new(1, -80, 0, 4), TitleBar.Frame, function()
		Library.Window:Minimize()
	end)

	return TitleBar
end
Components.Window = (function()
	local Spring = Flipper.Spring.new
	local Instant = Flipper.Instant.new
	local New = Creator.New

	return function(Config)
		local Window = {
			Minimized = false,
			Maximized = false,
			Size = Config.Size,
			CurrentPos = 0,
			TabWidth = 0,
			Position = UDim2.fromOffset(
				Camera.ViewportSize.X / 2 - Config.Size.X.Offset / 2,
				Camera.ViewportSize.Y / 2 - Config.Size.Y.Offset / 2
			),
		}

		local Dragging, DragInput, MousePos, StartPos = false
		local Resizing, ResizePos = false
		local MinimizeNotif = false

		Window.AcrylicPaint = Acrylic.AcrylicPaint()
		Window.TabWidth = Config.TabWidth

		local Selector = New("Frame", {
			Size = UDim2.fromOffset(4, 0),
			BackgroundColor3 = Color3.fromRGB(76, 194, 255),
			Position = UDim2.fromOffset(0, 17),
			AnchorPoint = Vector2.new(0, 0.5),
			ThemeTag = {
				BackgroundColor3 = "Accent",
			},
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(0, 2),
			}),
		})

		local OFFSETY = 120

		local ResizeStartFrame = New("Frame", {
			Size = UDim2.fromOffset(20, 20),
			BackgroundTransparency = 1,
			Position = UDim2.new(1, -20, 1, -20),
		})

		Window.TabHolder = New("ScrollingFrame", {
			Size = UDim2.fromScale(1, 1),
			BackgroundTransparency = 1,
			ScrollBarImageTransparency = 1,
			ScrollBarThickness = 0,
			BorderSizePixel = 0,
			CanvasSize = UDim2.fromScale(0, 0),
			ScrollingDirection = Enum.ScrollingDirection.Y,
		}, {
			New("UIListLayout", {
				Padding = UDim.new(0, 4),
			}),
		})

		local Icon = New("TextButton", {
			BackgroundTransparency = 1,
			Size = UDim2.new(0, Window.TabWidth, 0, Window.TabWidth),
			Position = UDim2.new(0, 12, 0, (Window.TabWidth/4)- 20),
			BorderSizePixel = 0
		}, {
			New("UIPadding", {
				PaddingBottom = UDim.new(0, 2),
				PaddingLeft = UDim.new(0, 2),
				PaddingRight = UDim.new(0, 2),
				PaddingTop = UDim.new(0, 2),
			}),
			New("ImageLabel", {
				Image = "rbxassetid://80202054463905",
				Size = UDim2.new(1, 0, 1, 0),
				BackgroundTransparency = 1,
			}, {
				New("UIAspectRatioConstraint", {
					AspectRatio = 1,
					AspectType = Enum.AspectType.FitWithinMaxSize,
				})
			})
		})

		local TabFrame = New("Frame", {
			Size = UDim2.new(0, Window.TabWidth, 1, -66 + -OFFSETY), -- []-66
			Position = UDim2.new(0, 12, 0, 54 + OFFSETY), --54
			BackgroundTransparency = 1,
			ClipsDescendants = true,
		}, {
			Window.TabHolder,
			Selector,
		})

		Window.TabDisplay = New("TextLabel", {
			RichText = true,
			Text = "Tab",
			TextTransparency = 0,
			FontFace = Font.new("rbxassetid://12187365364", Enum.FontWeight.SemiBold, Enum.FontStyle.Normal),
			TextSize = 28,
			TextXAlignment = "Left",
			TextYAlignment = "Center",
			Size = UDim2.new(1, -16, 0, 28),
			Position = UDim2.fromOffset(Window.TabWidth + 26, 56),
			BackgroundTransparency = 1,
			AutoLocalize = false,
			ThemeTag = {
				TextColor3 = "Text",
			},
		})

		Window.ContainerHolder = New("Frame", {
			Size = UDim2.fromScale(1, 1),
			BackgroundTransparency = 1,
		})

		Window.ContainerAnim = New("CanvasGroup", {
			Size = UDim2.fromScale(1, 1),
			BackgroundTransparency = 1,
		})

		Window.ContainerCanvas = New("Frame", {
			Size = UDim2.new(1, -Window.TabWidth - 32, 1, -102),
			Position = UDim2.fromOffset(Window.TabWidth + 26, 90),
			BackgroundTransparency = 1,
		}, {
			Window.ContainerAnim,
			Window.ContainerHolder
		})

		Window.Root = New("Frame", {
			BackgroundTransparency = 1,
			Size = Window.Size,
			Position = Window.Position,
			Parent = Config.Parent,
		}, {
			Window.AcrylicPaint.Frame,
			Window.TabDisplay,
			Window.ContainerCanvas,
			TabFrame,
			ResizeStartFrame,
			Icon
		})

		Window.TitleBar = Components.TitleBar({
			Title = Config.Title,
			SubTitle = Config.SubTitle,
			Parent = Window.Root,
			Window = Window,
		})

		if Library.UseAcrylic then
			Window.AcrylicPaint.AddParent(Window.Root)
		end

		local SizeMotor = Flipper.GroupMotor.new({
			X = Window.Size.X.Offset,
			Y = Window.Size.Y.Offset,
		})

		local PosMotor = Flipper.GroupMotor.new({
			X = Window.Position.X.Offset,
			Y = Window.Position.Y.Offset,
		})

		Window.SelectorPosMotor = Flipper.SingleMotor.new(17)
		Window.SelectorSizeMotor = Flipper.SingleMotor.new(0)
		Window.ContainerBackMotor = Flipper.SingleMotor.new(0)
		Window.ContainerPosMotor = Flipper.SingleMotor.new(94)

		SizeMotor:onStep(function(values)
			Window.Root.Size = UDim2.new(0, values.X, 0, values.Y)
		end)

		PosMotor:onStep(function(values)
			Window.Root.Position = UDim2.new(0, values.X, 0, values.Y)
		end)

		local LastValue = 0
		local LastTime = 0
		Window.SelectorPosMotor:onStep(function(Value)
			Selector.Position = UDim2.new(0, 0, 0, Value + 17)
			local Now = tick()
			local DeltaTime = Now - LastTime

			if LastValue ~= nil then
				Window.SelectorSizeMotor:setGoal(Spring((math.abs(Value - LastValue) / (DeltaTime * 60)) + 16))
				LastValue = Value
			end
			LastTime = Now
		end)

		Window.SelectorSizeMotor:onStep(function(Value)
			Selector.Size = UDim2.new(0, 4, 0, Value)
		end)

		Window.ContainerBackMotor:onStep(function(Value)
			Window.ContainerAnim.GroupTransparency = Value
		end)

		Window.ContainerPosMotor:onStep(function(Value)
			Window.ContainerAnim.Position = UDim2.fromOffset(0, Value)
		end)

		local OldSizeX
		local OldSizeY
		Window.Maximize = function(Value, NoPos, Instant)
			Window.Maximized = Value
			Window.TitleBar.MaxButton.Frame.Icon.Image = Value and Components.Assets.Restore or Components.Assets.Max

			if Value then
				OldSizeX = Window.Size.X.Offset
				OldSizeY = Window.Size.Y.Offset
			end
			local SizeX = Value and Camera.ViewportSize.X or OldSizeX
			local SizeY = Value and Camera.ViewportSize.Y or OldSizeY
			SizeMotor:setGoal({
				X = Flipper[Instant and "Instant" or "Spring"].new(SizeX, { frequency = 6 }),
				Y = Flipper[Instant and "Instant" or "Spring"].new(SizeY, { frequency = 6 }),
			})
			Window.Size = UDim2.fromOffset(SizeX, SizeY)

			if not NoPos then
				PosMotor:setGoal({
					X = Spring(Value and 0 or Window.Position.X.Offset, { frequency = 6 }),
					Y = Spring(Value and 0 or Window.Position.Y.Offset, { frequency = 6 }),
				})
			end
		end

		Creator.AddSignal(Window.TitleBar.Frame.InputBegan, function(Input)
			if
				Input.UserInputType == Enum.UserInputType.MouseButton1
				or Input.UserInputType == Enum.UserInputType.Touch
			then
				Dragging = true
				MousePos = Input.Position
				StartPos = Window.Root.Position

				if Window.Maximized then
					StartPos = UDim2.fromOffset(
						Mouse.X - (Mouse.X * ((OldSizeX - 100) / Window.Root.AbsoluteSize.X)),
						Mouse.Y - (Mouse.Y * (OldSizeY / Window.Root.AbsoluteSize.Y))
					)
				end

				Input.Changed:Connect(function()
					if Input.UserInputState == Enum.UserInputState.End then
						Dragging = false
					end
				end)
			end
		end)

		Creator.AddSignal(Window.TitleBar.Frame.InputChanged, function(Input)
			if
				Input.UserInputType == Enum.UserInputType.MouseMovement
				or Input.UserInputType == Enum.UserInputType.Touch
			then
				DragInput = Input
			end
		end)

		Creator.AddSignal(ResizeStartFrame.InputBegan, function(Input)
			if
				Input.UserInputType == Enum.UserInputType.MouseButton1
				or Input.UserInputType == Enum.UserInputType.Touch
			then
				Resizing = true
				ResizePos = Input.Position
			end
		end)

		Creator.AddSignal(UserInputService.InputChanged, function(Input)
			if Input == DragInput and Dragging then
				local Delta = Input.Position - MousePos
				Window.Position = UDim2.fromOffset(StartPos.X.Offset + Delta.X, StartPos.Y.Offset + Delta.Y)
				PosMotor:setGoal({
					X = Instant(Window.Position.X.Offset),
					Y = Instant(Window.Position.Y.Offset),
				})

				if Window.Maximized then
					Window.Maximize(false, true, true)
				end
			end

			if
				(Input.UserInputType == Enum.UserInputType.MouseMovement or Input.UserInputType == Enum.UserInputType.Touch)
				and Resizing
			then
				local Delta = Input.Position - ResizePos
				local StartSize = Window.Size

				local TargetSize = Vector3.new(StartSize.X.Offset, StartSize.Y.Offset, 0) + Vector3.new(1, 1, 0) * Delta
				local TargetSizeClamped =
					Vector2.new(math.clamp(TargetSize.X, 470, 2048), math.clamp(TargetSize.Y, 380, 2048))

				SizeMotor:setGoal({
					X = Flipper.Instant.new(TargetSizeClamped.X),
					Y = Flipper.Instant.new(TargetSizeClamped.Y),
				})
			end
		end)

		Creator.AddSignal(UserInputService.InputEnded, function(Input)
			if Resizing == true or Input.UserInputType == Enum.UserInputType.Touch then
				Resizing = false
				Window.Size = UDim2.fromOffset(SizeMotor:getValue().X, SizeMotor:getValue().Y)
			end
		end)

		Creator.AddSignal(Window.TabHolder.UIListLayout:GetPropertyChangedSignal("AbsoluteContentSize"), function()
			Window.TabHolder.CanvasSize = UDim2.new(0, 0, 0, Window.TabHolder.UIListLayout.AbsoluteContentSize.Y)
		end)

		Creator.AddSignal(UserInputService.InputBegan, function(Input)
			if
				type(Library.MinimizeKeybind) == "table"
				and Library.MinimizeKeybind.Type == "Keybind"
				and not UserInputService:GetFocusedTextBox()
			then
				if Input.KeyCode.Name == Library.MinimizeKeybind.Value then
					Window:Minimize()
				end
			elseif Input.KeyCode == Library.MinimizeKey and not UserInputService:GetFocusedTextBox() then
				Window:Minimize()
			end
		end)

		function Window:ToggleInterface()
			Window.Minimized = not Window.Minimized
			Window.Root.Visible = not Window.Minimized
		end

		function Window:Minimize()
			Window.Minimized = not Window.Minimized
			Window.Root.Visible = not Window.Minimized
			if not MinimizeNotif then
				MinimizeNotif = true
				local Key = Library.MinimizeKeybind and Library.MinimizeKeybind.Value or Library.MinimizeKey.Name
				Library:Notify({
					Title = "Interface",
					Content = "Press " .. Key .. " to toggle the interface.",
					Duration = 6
				})
			end
			--pcall(SwapIco)
		end

		function Window:Destroy()
			if Library.UseAcrylic then
				Window.AcrylicPaint.Model:Destroy()
			end
			Window.Root:Destroy()
		end

		local DialogModule = Components.Dialog:Init(Window)
		function Window:Dialog(Config)
			local Dialog = DialogModule:Create()
			Dialog.Title.Text = Config.Title

			local Content = New("TextLabel", {
				FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json"),
				Text = Config.Content,
				TextColor3 = Color3.fromRGB(240, 240, 240),
				TextSize = 14,
				TextXAlignment = Enum.TextXAlignment.Left,
				TextYAlignment = Enum.TextYAlignment.Top,
				Size = UDim2.new(1, -40, 1, 0),
				Position = UDim2.fromOffset(20, 60),
				BackgroundTransparency = 1,
				Parent = Dialog.Root,
				ClipsDescendants = false,
				AutoLocalize = false,
				ThemeTag = {
					TextColor3 = "Text",
				},
			})

			New("UISizeConstraint", {
				MinSize = Vector2.new(300, 165),
				MaxSize = Vector2.new(620, math.huge),
				Parent = Dialog.Root,
			})

			Dialog.Root.Size = UDim2.fromOffset(Content.TextBounds.X + 40, 165)
			if Content.TextBounds.X + 40 > Window.Size.X.Offset - 120 then
				Dialog.Root.Size = UDim2.fromOffset(Window.Size.X.Offset - 120, 165)
				Content.TextWrapped = true
				Dialog.Root.Size = UDim2.fromOffset(Window.Size.X.Offset - 120, Content.TextBounds.Y + 150)
			end

			for _, Button in next, Config.Buttons do
				Dialog:Button(Button.Title, Button.Callback)
			end

			Dialog:Open()
		end

		local TabModule = Components.Tab:Init(Window)
		function Window:AddTab(TabConfig)
			return TabModule:New(TabConfig.Title, TabConfig.Icon, Window.TabHolder)
		end

		function Window:GetCurrentTab()
			return TabModule:GetCurrentTab()
		end

		function Window:TabChanged(func)
			TabModule.Callback = func
		end

		function Window:SelectTab(Tab)
			TabModule:SelectTab(Tab)
		end

		Creator.AddSignal(Window.TabHolder:GetPropertyChangedSignal("CanvasPosition"), function()
			LastValue = TabModule:GetCurrentTabPos() + 16
			LastTime = 0
			Window.SelectorPosMotor:setGoal(Instant(TabModule:GetCurrentTabPos()))
		end)

		return Window
	end
end)()

local ElementsTable = {}

ElementsTable.Button = (function()
	local Element = {}
	Element.__index = Element
	Element.__type = "Button"

	function Element:New(Config)
		assert(Config.Title, "Button - Missing Title")
		Config.Callback = Config.Callback or function() end

		local ButtonFrame = Components.Element(Config.Title, Config.Description, self.Container, true, Config)

		local ButtonIco = New("ImageLabel", {
			Image = "rbxassetid://10709791437",
			Size = UDim2.fromOffset(16, 16),
			AnchorPoint = Vector2.new(1, 0.5),
			Position = UDim2.new(1, -10, 0.5, 0),
			BackgroundTransparency = 1,
			Parent = ButtonFrame.Frame,
			ThemeTag = {
				ImageColor3 = "Text",
			},
		})

		Creator.AddSignal(ButtonFrame.Frame.MouseButton1Click, function()
			Library:SafeCallback(Config.Callback)
		end)

		return ButtonFrame
	end

	return Element
end)()
ElementsTable.Toggle = (function()
	local Element = {}
	Element.__index = Element
	Element.__type = "Toggle"

	function Element:New(Idx, Config)
		assert(Config.Title, "Toggle - Missing Title")

		local Toggle = {
			OriginalTitle = Config.Title,
			OriginalDesc = Config.Description,
			Value = Config.Default or false,
			Callback = Config.Callback or function(Value) end,
			Type = "Toggle",
		}

		local ToggleFrame = Components.Element(Config.Title, Config.Description, self.Container, true, Config)
		ToggleFrame.DescLabel.Size = UDim2.new(1, -54, 0, 14)

		Toggle.SetTitle = ToggleFrame.SetTitle
		Toggle.AddText = ToggleFrame.AddText
		Toggle.SetDesc = ToggleFrame.SetDesc
		Toggle.Visible = ToggleFrame.Visible
		Toggle.GetOriginalText = ToggleFrame.GetOriginalText
		Toggle.Elements = ToggleFrame

		local ToggleCircle = New("ImageLabel", {
			AnchorPoint = Vector2.new(0, 0.5),
			Size = UDim2.fromOffset(14, 14),
			Position = UDim2.new(0, 2, 0.5, 0),
			Image = "http://www.roblox.com/asset/?id=12266946128",
			ImageTransparency = 0.5,
			ThemeTag = {
				ImageColor3 = "ToggleSlider",
			},
		})

		local ToggleBorder = New("UIStroke", {
			Transparency = 0.5,
			ThemeTag = {
				Color = "ToggleSlider",
			},
		})

		local ToggleSlider = New("Frame", {
			Size = UDim2.fromOffset(36, 18),
			AnchorPoint = Vector2.new(1, 0.5),
			Position = UDim2.new(1, -10, 0.5, 0),
			Parent = ToggleFrame.Frame,
			BackgroundTransparency = 1,
			ThemeTag = {
				BackgroundColor3 = "Accent",
			},
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(0, 9),
			}),
			ToggleBorder,
			ToggleCircle,
		})

		function Toggle:OnChanged(Func)
			Toggle.Changed = Func
			Func(Toggle.Value)
		end

		function Toggle:SetValue(Value)
			Value = not not Value
			Toggle.Value = Value

			Creator.OverrideTag(ToggleBorder, { Color = Toggle.Value and "Accent" or "ToggleSlider" })
			Creator.OverrideTag(ToggleCircle, { ImageColor3 = Toggle.Value and "ToggleToggled" or "ToggleSlider" })
			TweenService:Create(
				ToggleCircle,
				TweenInfo.new(0.25, Enum.EasingStyle.Quint, Enum.EasingDirection.Out),
				{ Position = UDim2.new(0, Toggle.Value and 19 or 2, 0.5, 0) }
			):Play()
			TweenService:Create(
				ToggleSlider,
				TweenInfo.new(0.25, Enum.EasingStyle.Quint, Enum.EasingDirection.Out),
				{ BackgroundTransparency = Toggle.Value and 0.45 or 1 }
			):Play()
			ToggleCircle.ImageTransparency = Toggle.Value and 0 or 0.5

			Library:SafeCallbackToggles(Config.Title, Toggle.Callback, Toggle.Value)
			Library:SafeCallbackToggles(Config.Title, Toggle.Changed, Toggle.Value)
		end

		function Toggle:GetValue()
			return self.Value
		end

		function Toggle:Destroy()
			ToggleFrame:Destroy()
			Library.Options[Idx] = nil
		end

		Creator.AddSignal(ToggleFrame.Frame.MouseButton1Click, function()
			Toggle:SetValue(not Toggle.Value)
		end)

		Toggle:SetValue(Toggle.Value)

		Library.Options[Idx] = Toggle	
		return Toggle
	end

	return Element
end)()
ElementsTable.Dropdown = (function()
	local Element = {}
	Element.__index = Element
	Element.__type = "Dropdown"

	function Element:New(Idx, Config)

		local Dropdown = {
			Values = Config.Values,
			Value = Config.Default,
			Multi = Config.Multi,
			Buttons = {},
			Opened = false,
			Type = "Dropdown",
			Callback = Config.Callback or function() end,
			Searchable = Config.Searchable or false
		}

		if Dropdown.Multi and Config.AllowNull then
			Dropdown.Value = {}
		end

		local DropdownFrame = Components.Element(Config.Title, Config.Description, self.Container, false, Config)
		DropdownFrame.DescLabel.Size = UDim2.new(1, -170, 0, 14)

		Dropdown.SetTitle = DropdownFrame.SetTitle
		Dropdown.SetDesc = DropdownFrame.SetDesc
		Dropdown.Visible = DropdownFrame.Visible
		Dropdown.Elements = DropdownFrame

		local DropdownDisplay = New("TextBox", {
			FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json", Enum.FontWeight.Regular, Enum.FontStyle.Normal),
			Text = "",
			PlaceholderText = "Value",
			PlaceholderColor3 = Color3.fromRGB(240, 240, 240),
			TextColor3 = Color3.fromRGB(240, 240, 240),
			TextSize = 14,
			AutomaticSize = Enum.AutomaticSize.Y,
			TextYAlignment = Enum.TextYAlignment.Center,
			TextXAlignment = Enum.TextXAlignment.Left,
			Size = UDim2.new(1, -40, 0.5, 0),
			Position = UDim2.new(0, 8, 0.5, 0),
			AnchorPoint = Vector2.new(0, 0.5),
			BackgroundColor3 = Color3.fromRGB(255, 255, 255),
			BackgroundTransparency = 1,
			TextTruncate = Enum.TextTruncate.AtEnd,
			Interactable = false,
			AutoLocalize = false,
			ThemeTag = {
				TextColor3 = "Text",
				PlaceholderColor3 = "Text"
			},
		})

		local DropdownIco = New("ImageLabel", {
			Image = "rbxassetid://10709790948",
			Size = UDim2.fromOffset(16, 16),
			AnchorPoint = Vector2.new(1, 0.5),
			Position = UDim2.new(1, -8, 0.5, 0),
			BackgroundTransparency = 1,
			Rotation = 90,
			ThemeTag = {
				ImageColor3 = "SubText",
			},
		})

		local DropdownInner = New("TextButton", {
			Size = UDim2.fromOffset(160, 30),
			Position = UDim2.new(1, -10, 0.5, 0),
			AnchorPoint = Vector2.new(1, 0.5),
			BackgroundTransparency = 0.9,
			Parent = DropdownFrame.Frame,
			AutoLocalize = false,
			ThemeTag = {
				BackgroundColor3 = "DropdownFrame",
			},
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(0, 5),
			}),
			New("UIStroke", {
				Transparency = 0.5,
				ApplyStrokeMode = Enum.ApplyStrokeMode.Border,
				ThemeTag = {
					Color = "InElementBorder",
				},
			}),
			DropdownIco,
			DropdownDisplay,
		})

		local DropdownListLayout = New("UIListLayout", {
			Padding = UDim.new(0, 3),
		})

		local DropdownScrollFrame = New("ScrollingFrame", {
			Size = UDim2.new(1, -5, 1, -10),
			Position = UDim2.fromOffset(5, 5),
			BackgroundTransparency = 1,
			BottomImage = "rbxassetid://6889812791",
			MidImage = "rbxassetid://6889812721",
			TopImage = "rbxassetid://6276641225",
			ScrollBarImageColor3 = Color3.fromRGB(255, 255, 255),
			ScrollBarImageTransparency = 0.75,
			ScrollBarThickness = 5,
			BorderSizePixel = 0,
			CanvasSize = UDim2.fromScale(0, 0),
			ScrollingDirection = Enum.ScrollingDirection.Y,
		}, {
			DropdownListLayout,
		})

		local DropdownHolderFrame = New("Frame", {
			Size = UDim2.fromScale(1, 0.6),
			ThemeTag = {
				BackgroundColor3 = "DropdownHolder",
			},
		}, {
			DropdownScrollFrame,
			New("UICorner", {
				CornerRadius = UDim.new(0, 7),
			}),
			New("UIStroke", {
				ApplyStrokeMode = Enum.ApplyStrokeMode.Border,
				ThemeTag = {
					Color = "DropdownBorder",
				},
			}),
			New("ImageLabel", {
				BackgroundTransparency = 1,
				Image = "http://www.roblox.com/asset/?id=5554236805",
				ScaleType = Enum.ScaleType.Slice,
				SliceCenter = Rect.new(23, 23, 277, 277),
				Size = UDim2.fromScale(1, 1) + UDim2.fromOffset(30, 30),
				Position = UDim2.fromOffset(-15, -15),
				ImageColor3 = Color3.fromRGB(0, 0, 0),
				ImageTransparency = 0.1,
			}),
		})

		local DropdownHolderCanvas = New("Frame", {
			BackgroundTransparency = 1,
			Size = UDim2.fromOffset(170, 300),
			Parent = Library.GUI,
			Visible = false,
		}, {
			DropdownHolderFrame,
			New("UISizeConstraint", {
				MinSize = Vector2.new(170, 0),
			}),
		})

		-- SEARCHABLE BOX --

		local Border = New("UIStroke", {
			ApplyStrokeMode = Enum.ApplyStrokeMode.Border,
			Color = Color3.fromRGB(0, 0, 0),
			ThemeTag = {
				Color = "ElementBorder",
			},
		})

		local searchIcon = New("ImageLabel", {
			Image = "rbxassetid://10734943674",
			Size = UDim2.fromOffset(18, 18),
			AnchorPoint = Vector2.new(0, 0.5),
			Position = UDim2.new(0, 4, 0.5, 0),
			BackgroundTransparency = 1,
			Rotation = 0,
			ThemeTag = {
				ImageColor3 = "SubText",
			},
		})

		local SearchBase = New("Frame", {
			Visible = false,
			Size = UDim2.new(0, 170, 0, 30),
			Parent = Library.GUI,
			AutomaticSize = Enum.AutomaticSize.Y,
			ThemeTag = {
				BackgroundColor3 = "DropdownHolder",
			},
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(0, 4),
			}),
			searchIcon,
			Border,
		})

		local DropdownSearch = New("TextBox", {
			FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json", Enum.FontWeight.Regular, Enum.FontStyle.Normal),
			Text = "",
			PlaceholderText = "Search...",
			PlaceholderColor3 = Color3.fromRGB(240, 240, 240),
			Parent = SearchBase,
			TextColor3 = Color3.fromRGB(240, 240, 240),
			TextSize = 14,
			TextYAlignment = Enum.TextYAlignment.Center,
			TextXAlignment = Enum.TextXAlignment.Left,
			Size = UDim2.new(1, -20, 1, 0),
			Position = UDim2.new(0.5, 18, 0.5, 0),
			AnchorPoint = Vector2.new(0.5, 0.5),
			BackgroundColor3 = Color3.fromRGB(255, 255, 255),
			BackgroundTransparency = 1,
			LayoutOrder = 7,
			TextTruncate = Enum.TextTruncate.AtEnd,
			Interactable = true,
			AutoLocalize = false,
			ThemeTag = {
				TextColor3 = "Text",
				PlaceholderColor3 = "Text"
			},
		})

		table.insert(Library.OpenFrames, DropdownHolderCanvas)

		local XADD = 195
		local DEFAULT_Y_OFFSET_WITH_OBJ = -5
		local DEFAULT_Y_OFFSET_WITHOUT_OBJ = 18
		local MAX_DROPDOWN_ITEMS = 5

		local MoveList = {
			{ Instance = DropdownHolderCanvas, YOffset = 35}, -- no custom offset
			{ Instance = SearchBase, YOffset = 0 }, -- custom Y offset
		}

		local function RecalculateListPosition()
			local Add = 0
			local availableSpace = Camera.ViewportSize.Y - DropdownInner.AbsolutePosition.Y
			local neededSpace = DropdownHolderCanvas.AbsoluteSize.Y - 5

			if availableSpace < neededSpace then
				Add = neededSpace - availableSpace + 40
			end

			local defaultYOffset = (DEFAULT_Y_OFFSET_WITH_OBJ - Add) or DEFAULT_Y_OFFSET_WITHOUT_OBJ
			local baseX = DropdownInner.AbsolutePosition.X - 1 + XADD
			local baseY = DropdownInner.AbsolutePosition.Y + defaultYOffset

			for _, entry in ipairs(MoveList) do
				local inst = entry.Instance
				local xOffset = entry.XOffset or 0
				local yOffset = entry.YOffset or 0

				inst.Position = UDim2.fromOffset(baseX + xOffset, baseY + yOffset)
			end
		end


		local ListSizeX = 0
		local function RecalculateListSize()
			if #Dropdown.Values > MAX_DROPDOWN_ITEMS then
				DropdownHolderCanvas.Size = UDim2.fromOffset(ListSizeX, (39 * MAX_DROPDOWN_ITEMS) - 13)
			else
				DropdownHolderCanvas.Size = UDim2.fromOffset(ListSizeX, DropdownListLayout.AbsoluteContentSize.Y + 10)
			end
		end

		local function RecalculateCanvasSize()
			DropdownScrollFrame.CanvasSize = UDim2.fromOffset(0, DropdownListLayout.AbsoluteContentSize.Y)
		end

		RecalculateListPosition()
		RecalculateListSize()

		Creator.AddSignal(DropdownInner:GetPropertyChangedSignal("AbsolutePosition"), RecalculateListPosition)

		Creator.AddSignal(DropdownInner.MouseButton1Click, function()
			if Dropdown.Opened then
				Dropdown:Close()
				return
			end
			Dropdown:Open()
		end)

		Creator.AddSignal(DropdownSearch:GetPropertyChangedSignal("Text"), function()
			local Text = DropdownSearch.Text
			if #Text == 0 then
				for _, Element in next, DropdownScrollFrame:GetChildren() do
					if not Element:IsA("UIListLayout") then
						local Value = Element.ButtonLabel.Text
						local Similar = Value:lower():match(Text:lower()) or Value:lower() == Text:lower()
						Element.Visible = true
					end
				end
			end
			for _, Element in next, DropdownScrollFrame:GetChildren() do
				if not Element:IsA("UIListLayout") then
					local Value = Element.ButtonLabel.Text
					local Similar = Value:lower():match(Text:lower()) or Value:lower() == Text:lower()
					Element.Visible = Similar and true or false
				end
			end
			-- TweenService:Create(
			-- 	DropdownHolderCanvas,
			-- 	TweenInfo.new(0.3, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
			-- 	{ Size = UDim2.fromOffset(ListSizeX, DropdownListLayout.AbsoluteContentSize.Y + 10) }
			-- ):Play()

			RecalculateListPosition()
			RecalculateListSize()
		end)

		Creator.AddSignal(DropdownSearch.Focused, function()
			DropdownSearch.Text = ""
		end)

		Creator.AddSignal(DropdownSearch.FocusLost, function(Enter, Input)
			if #DropdownSearch.Text > 0 then
				local Tick = tick()
				repeat wait() until tick() - Tick > 5 or DropdownSearch:IsFocused()
				if not DropdownSearch:IsFocused() then
					DropdownSearch.Text = ""
					-- Dropdown:Display()
				end
			end
		end)

		Creator.AddSignal(UserInputService.InputBegan, function(Input)
			if
				Input.UserInputType == Enum.UserInputType.MouseButton1
				or Input.UserInputType == Enum.UserInputType.Touch
			then
				local AbsPos, AbsSize = DropdownHolderFrame.AbsolutePosition, DropdownHolderFrame.AbsoluteSize
				if
					Mouse.X < AbsPos.X
					or Mouse.X > AbsPos.X + AbsSize.X
					or Mouse.Y < (AbsPos.Y - 20 - 1)
					or Mouse.Y > AbsPos.Y + AbsSize.Y
				then
					-- Dropdown:Close()
				end
			end
		end)

		local ScrollFrame = self.ScrollFrame
		function Dropdown:Open()
			Dropdown.Opened = true
			SearchBase.Visible = true
			-- DropdownDisplay.Interactable = Dropdown.Searchable and true or false
			ScrollFrame.ScrollingEnabled = false
			DropdownHolderCanvas.Visible = true
			TweenService:Create(
				DropdownHolderFrame,
				TweenInfo.new(0.3, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
				{ Size = UDim2.fromScale(1, 1) }
			):Play()
			TweenService:Create(
				DropdownIco,
				TweenInfo.new(0.3, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
				{ Rotation = -90 }
			):Play()
			-- if Dropdown.Searchable then
			-- 	DropdownDisplay:CaptureFocus()
			-- end
		end

		function Dropdown:Close()
			Dropdown.Opened = false
			SearchBase.Visible = false
			ScrollFrame.ScrollingEnabled = true
			DropdownDisplay.Interactable = false
			DropdownHolderFrame.Size = UDim2.fromScale(1, 0.6)
			DropdownHolderCanvas.Visible = false
			TweenService:Create(
				DropdownIco,
				TweenInfo.new(0.3, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
				{ Rotation = 90 }
			):Play()
			DropdownSearch:ReleaseFocus(false)
			Dropdown:Display()
		end

		function Dropdown:Display()
			local Values = Dropdown.Values
			local Str = ""

			if Config.Multi then
				for Idx, Value in next,Values do
					if Dropdown.Value[Value] then
						Str = Str .. Value .. ", "
					end
				end
				Str = Str:sub(1, #Str - 2)
			else
				Str = Dropdown.Value or ""
			end

			DropdownDisplay.PlaceholderText = (Str == "" and "--" or Str)
		end

		function Dropdown:GetActiveValues()
			if Config.Multi then
				local T = {}

				for Value, Bool in next, Dropdown.Value do
					table.insert(T, Value)
				end

				return T
			else
				return Dropdown.Value and 1 or 0
			end
		end

		function Dropdown:SetActiveValues(Value)
			Dropdown.Value = Value

			Library:SafeCallback(Dropdown.Callback, Dropdown.Value)
			Library:SafeCallback(Dropdown.Changed, Dropdown.Value)

			Dropdown:BuildDropdownList()
		end

		function Dropdown:BuildDropdownList()
			local Values = Dropdown.Values
			local Buttons = {}

			for _, Element in next, DropdownScrollFrame:GetChildren() do
				if not Element:IsA("UIListLayout") then
					Element:Destroy()
				end
			end

			local Count = 0

			for Idx, Value in next, Values do
				local Table = {}

				Count = Count + 1

				local ButtonSelector = New("Frame", {
					Size = UDim2.fromOffset(4, 14),
					BackgroundColor3 = Color3.fromRGB(76, 194, 255),
					Position = UDim2.fromOffset(-1, 16),
					AnchorPoint = Vector2.new(0, 0.5),
					ThemeTag = {
						BackgroundColor3 = "Accent",
					},
				}, {
					New("UICorner", {
						CornerRadius = UDim.new(0, 2),
					}),
				})

				local ButtonLabel = New("TextLabel", {
					FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json"),
					Text = Value,
					TextColor3 = Color3.fromRGB(200, 200, 200),
					TextSize = 13,
					TextXAlignment = Enum.TextXAlignment.Left,
					BackgroundColor3 = Color3.fromRGB(255, 255, 255),
					AutomaticSize = Enum.AutomaticSize.Y,
					BackgroundTransparency = 1,
					Size = UDim2.fromScale(1, 1),
					Position = UDim2.fromOffset(10, 0),
					Name = "ButtonLabel",
					AutoLocalize = false,
					ThemeTag = {
						TextColor3 = "Text",
					},
				})

				local Button = New("TextButton", {
					Size = UDim2.new(1, -5, 0, 32),
					BackgroundTransparency = 1,
					ZIndex = 23,
					Text = "",
					Parent = DropdownScrollFrame,
					ThemeTag = {
						BackgroundColor3 = "DropdownOption",
					},
				}, {
					ButtonSelector,
					ButtonLabel,
					New("UICorner", {
						CornerRadius = UDim.new(0, 6),
					}),
				})

				local Selected

				if Config.Multi then
					Selected = Dropdown.Value[Value]
				else
					Selected = Dropdown.Value == Value
				end

				local BackMotor, SetBackTransparency = Creator.SpringMotor(1, Button, "BackgroundTransparency")
				local SelMotor, SetSelTransparency = Creator.SpringMotor(1, ButtonSelector, "BackgroundTransparency")
				local SelectorSizeMotor = Flipper.SingleMotor.new(6)

				SelectorSizeMotor:onStep(function(value)
					ButtonSelector.Size = UDim2.new(0, 4, 0, value)
				end)

				Creator.AddSignal(Button.MouseEnter, function()
					SetBackTransparency(Selected and 0.85 or 0.89)
				end)
				Creator.AddSignal(Button.MouseLeave, function()
					SetBackTransparency(Selected and 0.89 or 1)
				end)
				Creator.AddSignal(Button.MouseButton1Down, function()
					SetBackTransparency(0.92)
				end)
				Creator.AddSignal(Button.MouseButton1Up, function()
					SetBackTransparency(Selected and 0.85 or 0.89)
				end)

				function Table:UpdateButton()
					if Config.Multi then
						Selected = Dropdown.Value[Value]
						if Selected then
							SetBackTransparency(0.89)
						end
					else
						Selected = Dropdown.Value == Value
						SetBackTransparency(Selected and 0.89 or 1)
					end

					SelectorSizeMotor:setGoal(Flipper.Spring.new(Selected and 14 or 6, { frequency = 6 }))
					SetSelTransparency(Selected and 0 or 1)
				end

				AddSignal(Button.Activated, function()
					local Try = not Selected

					if Dropdown:GetActiveValues() == 1 and not Try and not Config.AllowNull then
					else
						if Config.Multi then
							Selected = Try
							Dropdown.Value[Value] = Selected and true or nil
						else
							Selected = Try
							Dropdown.Value = Selected and Value or nil

							for _, OtherButton in next, Buttons do
								OtherButton:UpdateButton()
							end
						end

						Table:UpdateButton()

						if Dropdown.Searchable and #DropdownDisplay.Text > 0 then

						else
							Dropdown:Display()
						end

						Library:SafeCallback(Dropdown.Callback, Dropdown.Value)
						Library:SafeCallback(Dropdown.Changed, Dropdown.Value)
					end
				end)

				Table:UpdateButton()
				Dropdown:Display()

				Buttons[Button] = Table
			end

			ListSizeX = 0
			for Button, Table in next, Buttons do
				if Button.ButtonLabel then
					if Button.ButtonLabel.TextBounds.X > ListSizeX then
						ListSizeX = Button.ButtonLabel.TextBounds.X
					end
				end
			end
			ListSizeX = ListSizeX + 30

			RecalculateCanvasSize()
			RecalculateListSize()
		end

		function Dropdown:SetValues(NewValues)
			if NewValues then
				Dropdown.Values = NewValues
			end

			Dropdown:BuildDropdownList()
		end

		function Dropdown:OnChanged(Func)
			Dropdown.Changed = Func
			Func(Dropdown.Value)
		end

		function Dropdown:SetValue(Val)
			if Dropdown.Multi then
				local nTable = {}

				for Value, Bool in next, Val do
					if table.find(Dropdown.Values, Value) then
						nTable[Value] = true
					end
				end

				Dropdown.Value = nTable
			else
				if not Val then
					Dropdown.Value = nil
				elseif table.find(Dropdown.Values, Val) then
					Dropdown.Value = Val
				end
			end

			Dropdown:BuildDropdownList()

			Library:SafeCallback(Dropdown.Callback, Dropdown.Value)
			Library:SafeCallback(Dropdown.Changed, Dropdown.Value)
		end

		function Dropdown:GetValue()
			return self.Value
		end

		function Dropdown:Destroy()
			DropdownFrame:Destroy()
			Library.Options[Idx] = nil
		end

		Dropdown:BuildDropdownList()
		Dropdown:Display()

		local Defaults = {}

		if type(Config.Default) == "string" then
			local Idx = table.find(Dropdown.Values, Config.Default)
			if Idx then
				table.insert(Defaults, Idx)
			end
		elseif type(Config.Default) == "table" then
			for _, Value in next, Config.Default do
				local Idx = table.find(Dropdown.Values, Value)
				if Idx then
					table.insert(Defaults, Idx)
				end
			end
		elseif type(Config.Default) == "number" and Dropdown.Values[Config.Default] ~= nil then
			table.insert(Defaults, Config.Default)
		end

		if next(Defaults) then
			for i = 1, #Defaults do
				local Index = Defaults[i]
				if Config.Multi then
					Dropdown.Value[Dropdown.Values[Index]] = true
				else
					Dropdown.Value = Dropdown.Values[Index]
				end

				if not Config.Multi then
					break
				end
			end

			Dropdown:BuildDropdownList()
			Dropdown:Display()
		end

		Library.Options[Idx] = Dropdown
		return Dropdown
	end

	return Element
end)()
ElementsTable.Paragraph = (function()
	local Paragraph = {}
	Paragraph.__index = Paragraph
	Paragraph.__type = "Paragraph"

	function Paragraph:New(Config)
		assert(Config.Title, "Paragraph - Missing Title")
		Config.Content = Config.Content or ""

		local Paragraph = Components.Element(Config.Title, Config.Content, Paragraph.Container, false, Config)
		Paragraph.Frame.BackgroundTransparency = 0.92
		Paragraph.Border.Transparency = 0.6

		Paragraph.SetTitle = Paragraph.SetTitle
		Paragraph.SetDesc = Paragraph.SetDesc
		Paragraph.Visible = Paragraph.Visible
		Paragraph.Elements = Paragraph

		return Paragraph
	end

	return Paragraph
end)()
ElementsTable.Slider = (function()
	local Element = {}
	Element.__index = Element
	Element.__type = "Slider"

	function Element:New(Idx, Config)
		assert(Config.Title, "Slider - Missing Title.")
		assert(Config.Default, "Slider - Missing default value.")
		assert(Config.Min, "Slider - Missing minimum value.")
		assert(Config.Max, "Slider - Missing maximum value.")
		assert(Config.Rounding, "Slider - Missing rounding value.")

		local Slider = {
			Value = nil,
			Min = Config.Min,
			Max = Config.Max,
			Rounding = Config.Rounding,
			Callback = Config.Callback or function(Value) end,
			Type = "Slider",
		}

		local Dragging = false

		local SliderFrame = Components.Element(Config.Title, Config.Description, self.Container, false, Config)
		SliderFrame.DescLabel.Size = UDim2.new(1, -170, 0, 14)

		Slider.Elements = SliderFrame
		Slider.SetTitle = SliderFrame.SetTitle
		Slider.SetDesc = SliderFrame.SetDesc
		Slider.Visible = SliderFrame.Visible

		local SliderDot = New("ImageLabel", {
			AnchorPoint = Vector2.new(0, 0.5),
			Position = UDim2.new(0, -7, 0.5, 0),
			Size = UDim2.fromOffset(14, 14),
			Image = "http://www.roblox.com/asset/?id=12266946128",
			ThemeTag = {
				ImageColor3 = "Accent",
			},
		})

		local SliderRail = New("Frame", {
			BackgroundTransparency = 1,
			Position = UDim2.fromOffset(7, 0),
			Size = UDim2.new(1, -14, 1, 0),
		}, {
			SliderDot,
		})

		local SliderFill = New("Frame", {
			Size = UDim2.new(0, 0, 1, 0),
			ThemeTag = {
				BackgroundColor3 = "Accent",
			},
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(1, 0),
			}),
		})

		local SliderDisplay = New("TextBox", {
			FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json"),
			Text = Config.Default,
			PlaceholderText = "",
			TextSize = 12,
			TextWrapped = true,
			TextXAlignment = Enum.TextXAlignment.Right,
			BackgroundColor3 = Color3.fromRGB(255, 255, 255),
			BackgroundTransparency = 1,
			Size = UDim2.new(0, 100, 0, 14),
			Position = UDim2.new(0, -4, 0.5, 0),
			AnchorPoint = Vector2.new(1, 0.5),
			ThemeTag = {
				TextColor3 = "SubText",
			},
		})

		local SliderInner = New("Frame", {
			Size = UDim2.new(1, 0, 0, 4),
			AnchorPoint = Vector2.new(1, 0.5),
			Position = UDim2.new(1, -10, 0.5, 0),
			BackgroundTransparency = 0.4,
			Parent = SliderFrame.Frame,
			ThemeTag = {
				BackgroundColor3 = "SliderRail",
			},
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(1, 0),
			}),
			New("UISizeConstraint", {
				MaxSize = Vector2.new(150, math.huge),
			}),
			SliderDisplay,
			SliderFill,
			SliderRail,
		})

		AddSignal(SliderDisplay.FocusLost, function(enter)
			local Text = SliderDisplay.Text
			if not enter then return end
			Slider:SetValue(tonumber(Text))
		end)

		AddSignal(SliderDisplay:GetPropertyChangedSignal("Text"), function()
			if #SliderDisplay.Text > 0 and tonumber(SliderDisplay.Text) then
				Slider:SetValue(SliderDisplay.Text)
			end
		end)

		Creator.AddSignal(SliderDot.InputBegan, function(Input)
			if Input.UserInputType == Enum.UserInputType.MouseButton1
				or Input.UserInputType == Enum.UserInputType.Touch
			then
				Dragging = true
			end
		end)

		Creator.AddSignal(SliderDot.InputEnded, function(Input)
			if
				Input.UserInputType == Enum.UserInputType.MouseButton1
				or Input.UserInputType == Enum.UserInputType.Touch
			then
				Dragging = false
			end
		end)

		Creator.AddSignal(UserInputService.InputChanged, function(Input)
			if
				Dragging
				and (
					Input.UserInputType == Enum.UserInputType.MouseMovement
						or Input.UserInputType == Enum.UserInputType.Touch
				)
			then
				local SizeScale =
					math.clamp((Input.Position.X - SliderRail.AbsolutePosition.X) / SliderRail.AbsoluteSize.X, 0, 1)
				Slider:SetValue(Slider.Min + ((Slider.Max - Slider.Min) * SizeScale))
			end
		end)

		function Slider:OnChanged(Func)
			Slider.Changed = Func
			Func(Slider.Value)
		end

		function Slider:SetValue(Value)
			Value = Value or self.Value

			if (not tonumber(Value)) and Value:len() > 0 then
				Value = self.Value
			end

			self.Value = Library:Round(math.clamp(Value, Slider.Min, Slider.Max), Slider.Rounding) or 0
			SliderDot.Position = UDim2.new((self.Value - Slider.Min) / (Slider.Max - Slider.Min), -7, 0.5, 0)
			SliderFill.Size = UDim2.fromScale((self.Value - Slider.Min) / (Slider.Max - Slider.Min), 1)
			SliderDisplay.Text = tostring(self.Value)

			Library:SafeCallback(Slider.Callback, self.Value)
			Library:SafeCallback(Slider.Changed, self.Value)
		end

		function Slider:GetValue()
			return self.Value
		end

		function Slider:Destroy()
			SliderFrame:Destroy()
			Library.Options[Idx] = nil
		end

		Slider:SetValue(Config.Default)

		Library.Options[Idx] = Slider
		return Slider
	end

	return Element
end)()
ElementsTable.Keybind = (function()
	local Element = {}
	Element.__index = Element
	Element.__type = "Keybind"

	function Element:New(Idx, Config)
		assert(Config.Title, "KeyBind - Missing Title")
		assert(Config.Default, "KeyBind - Missing default value.")

		local Keybind = {
			Value = Config.Default,
			Toggled = false,
			Mode = Config.Mode or "Toggle",
			Type = "Keybind",
			Callback = Config.Callback or function(Value) end,
			ChangedCallback = Config.ChangedCallback or function(New) end,
		}

		local Picking = false

		local KeybindFrame = Components.Element(Config.Title, Config.Description, self.Container, true)

		Keybind.SetTitle = KeybindFrame.SetTitle
		Keybind.SetDesc = KeybindFrame.SetDesc
		Keybind.Visible = KeybindFrame.Visible
		Keybind.Elements = KeybindFrame

		local KeybindDisplayLabel = New("TextLabel", {
			FontFace = Font.new("rbxasset://fonts/families/GothamSSm.json", Enum.FontWeight.Regular, Enum.FontStyle.Normal),
			Text = Config.Default,
			TextColor3 = Color3.fromRGB(240, 240, 240),
			TextSize = 13,
			TextXAlignment = Enum.TextXAlignment.Center,
			Size = UDim2.new(0, 0, 0, 14),
			Position = UDim2.new(0, 0, 0.5, 0),
			AnchorPoint = Vector2.new(0, 0.5),
			BackgroundColor3 = Color3.fromRGB(255, 255, 255),
			AutomaticSize = Enum.AutomaticSize.X,
			BackgroundTransparency = 1,
			AutoLocalize = false,
			ThemeTag = {
				TextColor3 = "Text",
			},
		})

		local KeybindDisplayFrame = New("TextButton", {
			Size = UDim2.fromOffset(0, 30),
			Position = UDim2.new(1, -10, 0.5, 0),
			AnchorPoint = Vector2.new(1, 0.5),
			BackgroundTransparency = 0.9,
			Parent = KeybindFrame.Frame,
			AutomaticSize = Enum.AutomaticSize.X,
			ThemeTag = {
				BackgroundColor3 = "Keybind",
			},
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(0, 5),
			}),
			New("UIPadding", {
				PaddingLeft = UDim.new(0, 8),
				PaddingRight = UDim.new(0, 8),
			}),
			New("UIStroke", {
				Transparency = 0.5,
				ApplyStrokeMode = Enum.ApplyStrokeMode.Border,
				ThemeTag = {
					Color = "InElementBorder",
				},
			}),
			KeybindDisplayLabel,
		})

		function Keybind:GetState()
			if UserInputService:GetFocusedTextBox() and Keybind.Mode ~= "Always" then
				return false
			end

			if Keybind.Mode == "Always" then
				return true
			elseif Keybind.Mode == "Hold" then
				if Keybind.Value == "None" then
					return false
				end

				local Key = Keybind.Value

				if Key == "MouseLeft" or Key == "MouseRight" then
					return Key == "MouseLeft" and UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton1)
						or Key == "MouseRight"
						and UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton2)
				else
					return UserInputService:IsKeyDown(Enum.KeyCode[Keybind.Value])
				end
			else
				return Keybind.Toggled
			end
		end

		function Keybind:SetValue(Key, Mode)
			Key = Key or Keybind.Key
			Mode = Mode or Keybind.Mode

			KeybindDisplayLabel.Text = Key
			Keybind.Value = Key
			Keybind.Mode = Mode
		end

		function Keybind:GetValue()
			return self.Value
		end

		function Keybind:OnClick(Callback)
			Keybind.Clicked = Callback
		end

		function Keybind:OnChanged(Callback)
			Keybind.Changed = Callback
			Callback(Keybind.Value)
		end

		function Keybind:DoClick()
			Library:SafeCallback(Keybind.Callback, Keybind.Toggled)
			Library:SafeCallback(Keybind.Clicked, Keybind.Toggled)
		end

		function Keybind:Destroy()
			KeybindFrame:Destroy()
			Library.Options[Idx] = nil
		end

		Creator.AddSignal(KeybindDisplayFrame.InputBegan, function(Input)
			if
				Input.UserInputType == Enum.UserInputType.MouseButton1
				or Input.UserInputType == Enum.UserInputType.Touch
			then
				Picking = true
				KeybindDisplayLabel.Text = "..."

				wait(0.2)

				local Event
				Event = UserInputService.InputBegan:Connect(function(Input)
					local Key

					if Input.UserInputType == Enum.UserInputType.Keyboard then
						Key = Input.KeyCode.Name
					elseif Input.UserInputType == Enum.UserInputType.MouseButton1 then
						Key = "MouseLeft"
					elseif Input.UserInputType == Enum.UserInputType.MouseButton2 then
						Key = "MouseRight"
					end

					local EndedEvent
					EndedEvent = UserInputService.InputEnded:Connect(function(Input)
						if
							Input.KeyCode.Name == Key
							or Key == "MouseLeft" and Input.UserInputType == Enum.UserInputType.MouseButton1
							or Key == "MouseRight" and Input.UserInputType == Enum.UserInputType.MouseButton2
						then
							Picking = false

							KeybindDisplayLabel.Text = Key
							Keybind.Value = Key

							Library:SafeCallback(Keybind.ChangedCallback, Input.KeyCode or Input.UserInputType)
							Library:SafeCallback(Keybind.Changed, Input.KeyCode or Input.UserInputType)

							Event:Disconnect()
							EndedEvent:Disconnect()
						end
					end)
				end)
			end
		end)

		Creator.AddSignal(UserInputService.InputBegan, function(Input)
			if not Picking and not UserInputService:GetFocusedTextBox() then
				if Keybind.Mode == "Toggle" then
					local Key = Keybind.Value

					if Key == "MouseLeft" or Key == "MouseRight" then
						if
							Key == "MouseLeft" and Input.UserInputType == Enum.UserInputType.MouseButton1
							or Key == "MouseRight" and Input.UserInputType == Enum.UserInputType.MouseButton2
						then
							Keybind.Toggled = not Keybind.Toggled
							Keybind:DoClick()
						end
					elseif Input.UserInputType == Enum.UserInputType.Keyboard then
						if Input.KeyCode.Name == Key then
							Keybind.Toggled = not Keybind.Toggled
							Keybind:DoClick()
						end
					end
				end
			end
		end)

		Library.Options[Idx] = Keybind
		return Keybind
	end

	return Element
end)()
ElementsTable.Colorpicker = (function()
	local Element = {}
	Element.__index = Element
	Element.__type = "Colorpicker"

	function Element:New(Idx, Config)
		assert(Config.Title, "Colorpicker - Missing Title")
		assert(Config.Default, "AddColorPicker: Missing default value.")

		local Colorpicker = {
			Value = Config.Default,
			Transparency = Config.Transparency or 0,
			Type = "Colorpicker",
			Title = type(Config.Title) == "string" and Config.Title or "Colorpicker",
			Callback = Config.Callback or function(Color) end,
		}

		function Colorpicker:SetHSVFromRGB(Color)
			local H, S, V = Color3.toHSV(Color)
			Colorpicker.Hue = H
			Colorpicker.Sat = S
			Colorpicker.Vib = V
		end

		Colorpicker:SetHSVFromRGB(Colorpicker.Value)

		local ColorpickerFrame = Components.Element(Config.Title, Config.Description, self.Container, true)

		Colorpicker.SetTitle = ColorpickerFrame.SetTitle
		Colorpicker.SetDesc = ColorpickerFrame.SetDesc
		Colorpicker.Visible = ColorpickerFrame.Visible
		Colorpicker.Elements = ColorpickerFrame

		local DisplayFrameColor = New("Frame", {
			Size = UDim2.fromScale(1, 1),
			BackgroundColor3 = Colorpicker.Value,
			Parent = ColorpickerFrame.Frame,
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(0, 4),
			}),
		})

		local DisplayFrame = New("ImageLabel", {
			Size = UDim2.fromOffset(26, 26),
			Position = UDim2.new(1, -10, 0.5, 0),
			AnchorPoint = Vector2.new(1, 0.5),
			Parent = ColorpickerFrame.Frame,
			Image = "http://www.roblox.com/asset/?id=14204231522",
			ImageTransparency = 0.45,
			ScaleType = Enum.ScaleType.Tile,
			TileSize = UDim2.fromOffset(40, 40),
		}, {
			New("UICorner", {
				CornerRadius = UDim.new(0, 4),
			}),
			DisplayFrameColor,
		})

		local function CreateColorDialog()
			local Dialog = Components.Dialog:Create()
			Dialog.Title.Text = Colorpicker.Title
			Dialog.Root.Size = UDim2.fromOffset(430, 330)

			local Hue, Sat, Vib = Colorpicker.Hue, Colorpicker.Sat, Colorpicker.Vib
			local Transparency = Colorpicker.Transparency

			local function CreateInput()
				local Box = Components.Textbox()
				Box.Frame.Parent = Dialog.Root
				Box.Frame.Size = UDim2.new(0, 90, 0, 32)

				return Box
			end

			local function CreateInputLabel(Text, Pos)
				return New("TextLabel", {
					FontFace = Font.new(
						"rbxasset://fonts/families/GothamSSm.json",
						Enum.FontWeight.Medium,
						Enum.FontStyle.Normal
					),
					Text = Text,
					TextColor3 = Color3.fromRGB(240, 240, 240),
					TextSize = 13,
					TextXAlignment = Enum.TextXAlignment.Left,
					Size = UDim2.new(1, 0, 0, 32),
					Position = Pos,
					BackgroundTransparency = 1,
					Parent = Dialog.Root,
					AutoLocalize = false,
					ThemeTag = {
						TextColor3 = "Text",
					},
				})
			end

			local function GetRGB()
				local Value = Color3.fromHSV(Hue, Sat, Vib)
				return { R = math.floor(Value.r * 255), G = math.floor(Value.g * 255), B = math.floor(Value.b * 255) }
			end

			local SatCursor = New("ImageLabel", {
				Size = UDim2.new(0, 18, 0, 18),
				ScaleType = Enum.ScaleType.Fit,
				AnchorPoint = Vector2.new(0.5, 0.5),
				BackgroundTransparency = 1,
				Image = "http://www.roblox.com/asset/?id=4805639000",
			})

			local SatVibMap = New("ImageLabel", {
				Size = UDim2.fromOffset(180, 160),
				Position = UDim2.fromOffset(20, 55),
				Image = "rbxassetid://4155801252",
				BackgroundColor3 = Colorpicker.Value,
				BackgroundTransparency = 0,
				Parent = Dialog.Root,
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(0, 4),
				}),
				SatCursor,
			})

			local OldColorFrame = New("Frame", {
				BackgroundColor3 = Colorpicker.Value,
				Size = UDim2.fromScale(1, 1),
				BackgroundTransparency = Colorpicker.Transparency,
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(0, 4),
				}),
			})

			local OldColorFrameChecker = New("ImageLabel", {
				Image = "http://www.roblox.com/asset/?id=14204231522",
				ImageTransparency = 0.45,
				ScaleType = Enum.ScaleType.Tile,
				TileSize = UDim2.fromOffset(40, 40),
				BackgroundTransparency = 1,
				Position = UDim2.fromOffset(112, 220),
				Size = UDim2.fromOffset(88, 24),
				Parent = Dialog.Root,
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(0, 4),
				}),
				New("UIStroke", {
					Thickness = 2,
					Transparency = 0.75,
				}),
				OldColorFrame,
			})

			local DialogDisplayFrame = New("Frame", {
				BackgroundColor3 = Colorpicker.Value,
				Size = UDim2.fromScale(1, 1),
				BackgroundTransparency = 0,
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(0, 4),
				}),
			})

			local DialogDisplayFrameChecker = New("ImageLabel", {
				Image = "http://www.roblox.com/asset/?id=14204231522",
				ImageTransparency = 0.45,
				ScaleType = Enum.ScaleType.Tile,
				TileSize = UDim2.fromOffset(40, 40),
				BackgroundTransparency = 1,
				Position = UDim2.fromOffset(20, 220),
				Size = UDim2.fromOffset(88, 24),
				Parent = Dialog.Root,
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(0, 4),
				}),
				New("UIStroke", {
					Thickness = 2,
					Transparency = 0.75,
				}),
				DialogDisplayFrame,
			})

			local SequenceTable = {}

			for Color = 0, 1, 0.1 do
				table.insert(SequenceTable, ColorSequenceKeypoint.new(Color, Color3.fromHSV(Color, 1, 1)))
			end

			local HueSliderGradient = New("UIGradient", {
				Color = ColorSequence.new(SequenceTable),
				Rotation = 90,
			})

			local HueDragHolder = New("Frame", {
				Size = UDim2.new(1, 0, 1, -10),
				Position = UDim2.fromOffset(0, 5),
				BackgroundTransparency = 1,
			})

			local HueDrag = New("ImageLabel", {
				Size = UDim2.fromOffset(14, 14),
				Image = "http://www.roblox.com/asset/?id=12266946128",
				Parent = HueDragHolder,
				ThemeTag = {
					ImageColor3 = "DialogInput",
				},
			})

			local HueSlider = New("Frame", {
				Size = UDim2.fromOffset(12, 190),
				Position = UDim2.fromOffset(210, 55),
				Parent = Dialog.Root,
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(1, 0),
				}),
				HueSliderGradient,
				HueDragHolder,
			})

			local HexInput = CreateInput()
			HexInput.Frame.Position = UDim2.fromOffset(Config.Transparency and 260 or 240, 55)
			CreateInputLabel("Hex", UDim2.fromOffset(Config.Transparency and 360 or 340, 55))

			local RedInput = CreateInput()
			RedInput.Frame.Position = UDim2.fromOffset(Config.Transparency and 260 or 240, 95)
			CreateInputLabel("Red", UDim2.fromOffset(Config.Transparency and 360 or 340, 95))

			local GreenInput = CreateInput()
			GreenInput.Frame.Position = UDim2.fromOffset(Config.Transparency and 260 or 240, 135)
			CreateInputLabel("Green", UDim2.fromOffset(Config.Transparency and 360 or 340, 135))

			local BlueInput = CreateInput()
			BlueInput.Frame.Position = UDim2.fromOffset(Config.Transparency and 260 or 240, 175)
			CreateInputLabel("Blue", UDim2.fromOffset(Config.Transparency and 360 or 340, 175))

			local AlphaInput
			if Config.Transparency then
				AlphaInput = CreateInput()
				AlphaInput.Frame.Position = UDim2.fromOffset(260, 215)
				CreateInputLabel("Alpha", UDim2.fromOffset(360, 215))
			end

			local TransparencySlider, TransparencyDrag, TransparencyColor
			if Config.Transparency then
				local TransparencyDragHolder = New("Frame", {
					Size = UDim2.new(1, 0, 1, -10),
					Position = UDim2.fromOffset(0, 5),
					BackgroundTransparency = 1,
				})

				TransparencyDrag = New("ImageLabel", {
					Size = UDim2.fromOffset(14, 14),
					Image = "http://www.roblox.com/asset/?id=12266946128",
					Parent = TransparencyDragHolder,
					ThemeTag = {
						ImageColor3 = "DialogInput",
					},
				})

				TransparencyColor = New("Frame", {
					Size = UDim2.fromScale(1, 1),
				}, {
					New("UIGradient", {
						Transparency = NumberSequence.new({
							NumberSequenceKeypoint.new(0, 0),
							NumberSequenceKeypoint.new(1, 1),
						}),
						Rotation = 270,
					}),
					New("UICorner", {
						CornerRadius = UDim.new(1, 0),
					}),
				})

				TransparencySlider = New("Frame", {
					Size = UDim2.fromOffset(12, 190),
					Position = UDim2.fromOffset(230, 55),
					Parent = Dialog.Root,
					BackgroundTransparency = 1,
				}, {
					New("UICorner", {
						CornerRadius = UDim.new(1, 0),
					}),
					New("ImageLabel", {
						Image = "http://www.roblox.com/asset/?id=14204231522",
						ImageTransparency = 0.45,
						ScaleType = Enum.ScaleType.Tile,
						TileSize = UDim2.fromOffset(40, 40),
						BackgroundTransparency = 1,
						Size = UDim2.fromScale(1, 1),
						Parent = Dialog.Root,
					}, {
						New("UICorner", {
							CornerRadius = UDim.new(1, 0),
						}),
					}),
					TransparencyColor,
					TransparencyDragHolder,
				})
			end

			local function Display()
				SatVibMap.BackgroundColor3 = Color3.fromHSV(Hue, 1, 1)
				HueDrag.Position = UDim2.new(0, -1, Hue, -6)
				SatCursor.Position = UDim2.new(Sat, 0, 1 - Vib, 0)
				DialogDisplayFrame.BackgroundColor3 = Color3.fromHSV(Hue, Sat, Vib)

				HexInput.Input.Text = "#" .. Color3.fromHSV(Hue, Sat, Vib):ToHex()
				RedInput.Input.Text = GetRGB()["R"]
				GreenInput.Input.Text = GetRGB()["G"]
				BlueInput.Input.Text = GetRGB()["B"]

				if Config.Transparency then
					TransparencyColor.BackgroundColor3 = Color3.fromHSV(Hue, Sat, Vib)
					DialogDisplayFrame.BackgroundTransparency = Transparency
					TransparencyDrag.Position = UDim2.new(0, -1, 1 - Transparency, -6)
					AlphaInput.Input.Text = Library:Round((1 - Transparency) * 100, 0) .. "%"
				end
			end

			Creator.AddSignal(HexInput.Input.FocusLost, function(Enter)
				if Enter then
					local Success, Result = pcall(Color3.fromHex, HexInput.Input.Text)
					if Success and typeof(Result) == "Color3" then
						Hue, Sat, Vib = Color3.toHSV(Result)
					end
				end
				Display()
			end)

			Creator.AddSignal(RedInput.Input.FocusLost, function(Enter)
				if Enter then
					local CurrentColor = GetRGB()
					local Success, Result = pcall(Color3.fromRGB, RedInput.Input.Text, CurrentColor["G"], CurrentColor["B"])
					if Success and typeof(Result) == "Color3" then
						if tonumber(RedInput.Input.Text) <= 255 then
							Hue, Sat, Vib = Color3.toHSV(Result)
						end
					end
				end
				Display()
			end)

			Creator.AddSignal(GreenInput.Input.FocusLost, function(Enter)
				if Enter then
					local CurrentColor = GetRGB()
					local Success, Result =
						pcall(Color3.fromRGB, CurrentColor["R"], GreenInput.Input.Text, CurrentColor["B"])
					if Success and typeof(Result) == "Color3" then
						if tonumber(GreenInput.Input.Text) <= 255 then
							Hue, Sat, Vib = Color3.toHSV(Result)
						end
					end
				end
				Display()
			end)

			Creator.AddSignal(BlueInput.Input.FocusLost, function(Enter)
				if Enter then
					local CurrentColor = GetRGB()
					local Success, Result =
						pcall(Color3.fromRGB, CurrentColor["R"], CurrentColor["G"], BlueInput.Input.Text)
					if Success and typeof(Result) == "Color3" then
						if tonumber(BlueInput.Input.Text) <= 255 then
							Hue, Sat, Vib = Color3.toHSV(Result)
						end
					end
				end
				Display()
			end)

			if Config.Transparency then
				Creator.AddSignal(AlphaInput.Input.FocusLost, function(Enter)
					if Enter then
						pcall(function()
							local Value = tonumber(AlphaInput.Input.Text)
							if Value >= 0 and Value <= 100 then
								Transparency = 1 - Value * 0.01
							end
						end)
					end
					Display()
				end)
			end

			Creator.AddSignal(SatVibMap.InputBegan, function(Input)
				if
					Input.UserInputType == Enum.UserInputType.MouseButton1
					or Input.UserInputType == Enum.UserInputType.Touch
				then
					while UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton1) do
						local MinX = SatVibMap.AbsolutePosition.X
						local MaxX = MinX + SatVibMap.AbsoluteSize.X
						local MouseX = math.clamp(Mouse.X, MinX, MaxX)

						local MinY = SatVibMap.AbsolutePosition.Y
						local MaxY = MinY + SatVibMap.AbsoluteSize.Y
						local MouseY = math.clamp(Mouse.Y, MinY, MaxY)

						Sat = (MouseX - MinX) / (MaxX - MinX)
						Vib = 1 - ((MouseY - MinY) / (MaxY - MinY))
						Display()

						RenderStepped:Wait()
					end
				end
			end)

			Creator.AddSignal(HueSlider.InputBegan, function(Input)
				if
					Input.UserInputType == Enum.UserInputType.MouseButton1
					or Input.UserInputType == Enum.UserInputType.Touch
				then
					while UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton1) do
						local MinY = HueSlider.AbsolutePosition.Y
						local MaxY = MinY + HueSlider.AbsoluteSize.Y
						local MouseY = math.clamp(Mouse.Y, MinY, MaxY)

						Hue = ((MouseY - MinY) / (MaxY - MinY))
						Display()

						RenderStepped:Wait()
					end
				end
			end)

			if Config.Transparency then
				Creator.AddSignal(TransparencySlider.InputBegan, function(Input)
					if Input.UserInputType == Enum.UserInputType.MouseButton1 then
						while UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton1) do
							local MinY = TransparencySlider.AbsolutePosition.Y
							local MaxY = MinY + TransparencySlider.AbsoluteSize.Y
							local MouseY = math.clamp(Mouse.Y, MinY, MaxY)

							Transparency = 1 - ((MouseY - MinY) / (MaxY - MinY))
							Display()

							RenderStepped:Wait()
						end
					end
				end)
			end

			Display()

			Dialog:Button("Done", function()
				Colorpicker:SetValue({ Hue, Sat, Vib }, Transparency)
			end)
			Dialog:Button("Cancel")
			Dialog:Open()
		end

		function Colorpicker:Display()
			Colorpicker.Value = Color3.fromHSV(Colorpicker.Hue, Colorpicker.Sat, Colorpicker.Vib)

			DisplayFrameColor.BackgroundColor3 = Colorpicker.Value
			DisplayFrameColor.BackgroundTransparency = Colorpicker.Transparency

			Element.Library:SafeCallback(Colorpicker.Callback, Colorpicker.Value)
			Element.Library:SafeCallback(Colorpicker.Changed, Colorpicker.Value)
		end

		function Colorpicker:SetValue(HSV, Transparency)
			local Color = Color3.fromHSV(HSV[1], HSV[2], HSV[3])

			Colorpicker.Transparency = Transparency or 0
			Colorpicker:SetHSVFromRGB(Color)
			Colorpicker:Display()
		end

		function Colorpicker:SetValueRGB(Color, Transparency)
			Colorpicker.Transparency = Transparency or 0
			Colorpicker:SetHSVFromRGB(Color)
			Colorpicker:Display()
		end

		function Colorpicker:OnChanged(Func)
			Colorpicker.Changed = Func
			Func(Colorpicker.Value)
		end

		function Colorpicker:Destroy()
			ColorpickerFrame:Destroy()
			Library.Options[Idx] = nil
		end

		Creator.AddSignal(ColorpickerFrame.Frame.MouseButton1Click, function()
			CreateColorDialog()
		end)

		Colorpicker:Display()

		Library.Options[Idx] = Colorpicker
		return Colorpicker
	end

	return Element
end)()
ElementsTable.Input = (function()
	local Element = {}
	Element.__index = Element
	Element.__type = "Input"

	function Element:New(Idx, Config)
		assert(Config.Title, "Input - Missing Title")
		Config.Callback = Config.Callback or function() end

		local Input = {
			Value = Config.Default or "",
			Numeric = Config.Numeric or false,
			Finished = Config.Finished or false,
			Callback = Config.Callback or function(Value) end,
			Type = "Input",
		}

		local InputFrame = Components.Element(Config.Title, Config.Description, self.Container, false)
		InputFrame.DescLabel.Size = UDim2.new(1, -170, 0, 14)

		Input.SetTitle = InputFrame.SetTitle
		Input.SetDesc = InputFrame.SetDesc
		Input.Visible = InputFrame.Visible
		Input.Elements = InputFrame

		local Textbox = Components.Textbox(InputFrame.Frame, true)
		Textbox.Frame.Position = UDim2.new(1, -10, 0.5, 0)
		Textbox.Frame.AnchorPoint = Vector2.new(1, 0.5)
		Textbox.Frame.Size = UDim2.fromOffset(160, 30)
		Textbox.Input.Text = Config.Default or ""
		Textbox.Input.PlaceholderText = Config.Placeholder or ""
		Textbox.MultiLine = Config.MultiLine or false

		local Box = Textbox.Input

		function Input:SetValue(Text)
			if Config.MaxLength and #Text > Config.MaxLength then
				Text = Text:sub(1, Config.MaxLength)
			end

			if Input.Numeric then
				local number = tonumber(Text)
				if not number and Text:len() > 0 then
					Text = Input.Value
				end
			end

			Input.Value = Text
			Box.Text = Text

			Library:SafeCallback(Input.Callback, Input.Value)
			Library:SafeCallback(Input.Changed, Input.Value)
		end

		function Input:GetValue()
			return self.Value
		end

		if Input.Finished then
			AddSignal(Box.FocusLost, function(enter)
				if not enter then
					return
				end
				Input:SetValue(Box.Text)
			end)
		else
			AddSignal(Box:GetPropertyChangedSignal("Text"), function()
				Input:SetValue(Box.Text)
			end)
		end

		function Input:OnChanged(Func)
			Input.Changed = Func
			Func(Input.Value)
		end

		function Input:Destroy()
			InputFrame:Destroy()
			Library.Options[Idx] = nil
		end

		Library.Options[Idx] = Input
		return Input
	end

	return Element
end)()

local NotificationModule = Components.Notification
NotificationModule:Init(GUI)

local New = Creator.New

local Icons = {
	["lucide-accessibility"] = "rbxassetid://10709751939",
	["lucide-activity"] = "rbxassetid://10709752035",
	["lucide-air-vent"] = "rbxassetid://10709752131",
	["lucide-airplay"] = "rbxassetid://10709752254",
	["lucide-alarm-check"] = "rbxassetid://10709752405",
	["lucide-alarm-clock"] = "rbxassetid://10709752630",
	["lucide-alarm-clock-off"] = "rbxassetid://10709752508",
	["lucide-alarm-minus"] = "rbxassetid://10709752732",
	["lucide-alarm-plus"] = "rbxassetid://10709752825",
	["lucide-album"] = "rbxassetid://10709752906",
	["lucide-alert-circle"] = "rbxassetid://10709752996",
	["lucide-alert-octagon"] = "rbxassetid://10709753064",
	["lucide-alert-triangle"] = "rbxassetid://10709753149",
	["lucide-align-center"] = "rbxassetid://10709753570",
	["lucide-align-center-horizontal"] = "rbxassetid://10709753272",
	["lucide-align-center-vertical"] = "rbxassetid://10709753421",
	["lucide-align-end-horizontal"] = "rbxassetid://10709753692",
	["lucide-align-end-vertical"] = "rbxassetid://10709753808",
	["lucide-align-horizontal-distribute-center"] = "rbxassetid://10747779791",
	["lucide-align-horizontal-distribute-end"] = "rbxassetid://10747784534",
	["lucide-align-horizontal-distribute-start"] = "rbxassetid://10709754118",
	["lucide-align-horizontal-justify-center"] = "rbxassetid://10709754204",
	["lucide-align-horizontal-justify-end"] = "rbxassetid://10709754317",
	["lucide-align-horizontal-justify-start"] = "rbxassetid://10709754436",
	["lucide-align-horizontal-space-around"] = "rbxassetid://10709754590",
	["lucide-align-horizontal-space-between"] = "rbxassetid://10709754749",
	["lucide-align-justify"] = "rbxassetid://10709759610",
	["lucide-align-left"] = "rbxassetid://10709759764",
	["lucide-align-right"] = "rbxassetid://10709759895",
	["lucide-align-start-horizontal"] = "rbxassetid://10709760051",
	["lucide-align-start-vertical"] = "rbxassetid://10709760244",
	["lucide-align-vertical-distribute-center"] = "rbxassetid://10709760351",
	["lucide-align-vertical-distribute-end"] = "rbxassetid://10709760434",
	["lucide-align-vertical-distribute-start"] = "rbxassetid://10709760612",
	["lucide-align-vertical-justify-center"] = "rbxassetid://10709760814",
	["lucide-align-vertical-justify-end"] = "rbxassetid://10709761003",
	["lucide-align-vertical-justify-start"] = "rbxassetid://10709761176",
	["lucide-align-vertical-space-around"] = "rbxassetid://10709761324",
	["lucide-align-vertical-space-between"] = "rbxassetid://10709761434",
	["lucide-anchor"] = "rbxassetid://10709761530",
	["lucide-angry"] = "rbxassetid://10709761629",
	["lucide-annoyed"] = "rbxassetid://10709761722",
	["lucide-aperture"] = "rbxassetid://10709761813",
	["lucide-apple"] = "rbxassetid://10709761889",
	["lucide-archive"] = "rbxassetid://10709762233",
	["lucide-archive-restore"] = "rbxassetid://10709762058",
	["lucide-armchair"] = "rbxassetid://10709762327",
	["lucide-anvil"] = "rbxassetid://77943964625400",
	["lucide-arrow-big-down"] = "rbxassetid://10747796644",
	["lucide-arrow-big-left"] = "rbxassetid://10709762574",
	["lucide-arrow-big-right"] = "rbxassetid://10709762727",
	["lucide-arrow-big-up"] = "rbxassetid://10709762879",
	["lucide-arrow-down"] = "rbxassetid://10709767827",
	["lucide-arrow-down-circle"] = "rbxassetid://10709763034",
	["lucide-arrow-down-left"] = "rbxassetid://10709767656",
	["lucide-arrow-down-right"] = "rbxassetid://10709767750",
	["lucide-arrow-left"] = "rbxassetid://10709768114",
	["lucide-arrow-left-circle"] = "rbxassetid://10709767936",
	["lucide-arrow-left-right"] = "rbxassetid://10709768019",
	["lucide-arrow-right"] = "rbxassetid://10709768347",
	["lucide-arrow-right-circle"] = "rbxassetid://10709768226",
	["lucide-arrow-up"] = "rbxassetid://10709768939",
	["lucide-arrow-up-circle"] = "rbxassetid://10709768432",
	["lucide-arrow-up-down"] = "rbxassetid://10709768538",
	["lucide-arrow-up-left"] = "rbxassetid://10709768661",
	["lucide-arrow-up-right"] = "rbxassetid://10709768787",
	["lucide-asterisk"] = "rbxassetid://10709769095",
	["lucide-at-sign"] = "rbxassetid://10709769286",
	["lucide-award"] = "rbxassetid://10709769406",
	["lucide-axe"] = "rbxassetid://10709769508",
	["lucide-axis-3d"] = "rbxassetid://10709769598",
	["lucide-baby"] = "rbxassetid://10709769732",
	["lucide-backpack"] = "rbxassetid://10709769841",
	["lucide-baggage-claim"] = "rbxassetid://10709769935",
	["lucide-banana"] = "rbxassetid://10709770005",
	["lucide-banknote"] = "rbxassetid://10709770178",
	["lucide-bar-chart"] = "rbxassetid://10709773755",
	["lucide-bar-chart-2"] = "rbxassetid://10709770317",
	["lucide-bar-chart-3"] = "rbxassetid://10709770431",
	["lucide-bar-chart-4"] = "rbxassetid://10709770560",
	["lucide-bar-chart-horizontal"] = "rbxassetid://10709773669",
	["lucide-barcode"] = "rbxassetid://10747360675",
	["lucide-baseline"] = "rbxassetid://10709773863",
	["lucide-bath"] = "rbxassetid://10709773963",
	["lucide-battery"] = "rbxassetid://10709774640",
	["lucide-battery-charging"] = "rbxassetid://10709774068",
	["lucide-battery-full"] = "rbxassetid://10709774206",
	["lucide-battery-low"] = "rbxassetid://10709774370",
	["lucide-battery-medium"] = "rbxassetid://10709774513",
	["lucide-beaker"] = "rbxassetid://10709774756",
	["lucide-bed"] = "rbxassetid://10709775036",
	["lucide-bed-double"] = "rbxassetid://10709774864",
	["lucide-bed-single"] = "rbxassetid://10709774968",
	["lucide-beer"] = "rbxassetid://10709775167",
	["lucide-bell"] = "rbxassetid://10709775704",
	["lucide-bell-minus"] = "rbxassetid://10709775241",
	["lucide-bell-off"] = "rbxassetid://10709775320",
	["lucide-bell-plus"] = "rbxassetid://10709775448",
	["lucide-bell-ring"] = "rbxassetid://10709775560",
	["lucide-bike"] = "rbxassetid://10709775894",
	["lucide-binary"] = "rbxassetid://10709776050",
	["lucide-bitcoin"] = "rbxassetid://10709776126",
	["lucide-bluetooth"] = "rbxassetid://10709776655",
	["lucide-bluetooth-connected"] = "rbxassetid://10709776240",
	["lucide-bluetooth-off"] = "rbxassetid://10709776344",
	["lucide-bluetooth-searching"] = "rbxassetid://10709776501",
	["lucide-bold"] = "rbxassetid://10747813908",
	["lucide-bomb"] = "rbxassetid://10709781460",
	["lucide-bone"] = "rbxassetid://10709781605",
	["lucide-book"] = "rbxassetid://10709781824",
	["lucide-book-open"] = "rbxassetid://10709781717",
	["lucide-bookmark"] = "rbxassetid://10709782154",
	["lucide-bookmark-minus"] = "rbxassetid://10709781919",
	["lucide-bookmark-plus"] = "rbxassetid://10709782044",
	["lucide-bot"] = "rbxassetid://10709782230",
	["lucide-box"] = "rbxassetid://10709782497",
	["lucide-box-select"] = "rbxassetid://10709782342",
	["lucide-boxes"] = "rbxassetid://10709782582",
	["lucide-briefcase"] = "rbxassetid://10709782662",
	["lucide-brush"] = "rbxassetid://10709782758",
	["lucide-bug"] = "rbxassetid://10709782845",
	["lucide-building"] = "rbxassetid://10709783051",
	["lucide-building-2"] = "rbxassetid://10709782939",
	["lucide-bus"] = "rbxassetid://10709783137",
	["lucide-cake"] = "rbxassetid://10709783217",
	["lucide-calculator"] = "rbxassetid://10709783311",
	["lucide-calendar"] = "rbxassetid://10709789505",
	["lucide-calendar-check"] = "rbxassetid://10709783474",
	["lucide-calendar-check-2"] = "rbxassetid://10709783392",
	["lucide-calendar-clock"] = "rbxassetid://10709783577",
	["lucide-calendar-days"] = "rbxassetid://10709783673",
	["lucide-calendar-heart"] = "rbxassetid://10709783835",
	["lucide-calendar-minus"] = "rbxassetid://10709783959",
	["lucide-calendar-off"] = "rbxassetid://10709788784",
	["lucide-calendar-plus"] = "rbxassetid://10709788937",
	["lucide-calendar-range"] = "rbxassetid://10709789053",
	["lucide-calendar-search"] = "rbxassetid://10709789200",
	["lucide-calendar-x"] = "rbxassetid://10709789407",
	["lucide-calendar-x-2"] = "rbxassetid://10709789329",
	["lucide-camera"] = "rbxassetid://10709789686",
	["lucide-camera-off"] = "rbxassetid://10747822677",
	["lucide-car"] = "rbxassetid://10709789810",
	["lucide-carrot"] = "rbxassetid://10709789960",
	["lucide-cast"] = "rbxassetid://10709790097",
	["lucide-charge"] = "rbxassetid://10709790202",
	["lucide-check"] = "rbxassetid://10709790644",
	["lucide-check-circle"] = "rbxassetid://10709790387",
	["lucide-check-circle-2"] = "rbxassetid://10709790298",
	["lucide-check-square"] = "rbxassetid://10709790537",
	["lucide-chef-hat"] = "rbxassetid://10709790757",
	["lucide-cherry"] = "rbxassetid://10709790875",
	["lucide-chevron-down"] = "rbxassetid://10709790948",
	["lucide-chevron-first"] = "rbxassetid://10709791015",
	["lucide-chevron-last"] = "rbxassetid://10709791130",
	["lucide-chevron-left"] = "rbxassetid://10709791281",
	["lucide-chevron-right"] = "rbxassetid://10709791437",
	["lucide-chevron-up"] = "rbxassetid://10709791523",
	["lucide-chevrons-down"] = "rbxassetid://10709796864",
	["lucide-chevrons-down-up"] = "rbxassetid://10709791632",
	["lucide-chevrons-left"] = "rbxassetid://10709797151",
	["lucide-chevrons-left-right"] = "rbxassetid://10709797006",
	["lucide-chevrons-right"] = "rbxassetid://10709797382",
	["lucide-chevrons-right-left"] = "rbxassetid://10709797274",
	["lucide-chevrons-up"] = "rbxassetid://10709797622",
	["lucide-chevrons-up-down"] = "rbxassetid://10709797508",
	["lucide-chrome"] = "rbxassetid://10709797725",
	["lucide-circle"] = "rbxassetid://10709798174",
	["lucide-circle-dot"] = "rbxassetid://10709797837",
	["lucide-circle-ellipsis"] = "rbxassetid://10709797985",
	["lucide-circle-slashed"] = "rbxassetid://10709798100",
	["lucide-citrus"] = "rbxassetid://10709798276",
	["lucide-clapperboard"] = "rbxassetid://10709798350",
	["lucide-clipboard"] = "rbxassetid://10709799288",
	["lucide-clipboard-check"] = "rbxassetid://10709798443",
	["lucide-clipboard-copy"] = "rbxassetid://10709798574",
	["lucide-clipboard-edit"] = "rbxassetid://10709798682",
	["lucide-clipboard-list"] = "rbxassetid://10709798792",
	["lucide-clipboard-signature"] = "rbxassetid://10709798890",
	["lucide-clipboard-type"] = "rbxassetid://10709798999",
	["lucide-clipboard-x"] = "rbxassetid://10709799124",
	["lucide-clock"] = "rbxassetid://10709805144",
	["lucide-clock-1"] = "rbxassetid://10709799535",
	["lucide-clock-10"] = "rbxassetid://10709799718",
	["lucide-clock-11"] = "rbxassetid://10709799818",
	["lucide-clock-12"] = "rbxassetid://10709799962",
	["lucide-clock-2"] = "rbxassetid://10709803876",
	["lucide-clock-3"] = "rbxassetid://10709803989",
	["lucide-clock-4"] = "rbxassetid://10709804164",
	["lucide-clock-5"] = "rbxassetid://10709804291",
	["lucide-clock-6"] = "rbxassetid://10709804435",
	["lucide-clock-7"] = "rbxassetid://10709804599",
	["lucide-clock-8"] = "rbxassetid://10709804784",
	["lucide-clock-9"] = "rbxassetid://10709804996",
	["lucide-cloud"] = "rbxassetid://10709806740",
	["lucide-cloud-cog"] = "rbxassetid://10709805262",
	["lucide-cloud-drizzle"] = "rbxassetid://10709805371",
	["lucide-cloud-fog"] = "rbxassetid://10709805477",
	["lucide-cloud-hail"] = "rbxassetid://10709805596",
	["lucide-cloud-lightning"] = "rbxassetid://10709805727",
	["lucide-cloud-moon"] = "rbxassetid://10709805942",
	["lucide-cloud-moon-rain"] = "rbxassetid://10709805838",
	["lucide-cloud-off"] = "rbxassetid://10709806060",
	["lucide-cloud-rain"] = "rbxassetid://10709806277",
	["lucide-cloud-rain-wind"] = "rbxassetid://10709806166",
	["lucide-cloud-snow"] = "rbxassetid://10709806374",
	["lucide-cloud-sun"] = "rbxassetid://10709806631",
	["lucide-cloud-sun-rain"] = "rbxassetid://10709806475",
	["lucide-cloudy"] = "rbxassetid://10709806859",
	["lucide-clover"] = "rbxassetid://10709806995",
	["lucide-code"] = "rbxassetid://10709810463",
	["lucide-code-2"] = "rbxassetid://10709807111",
	["lucide-codepen"] = "rbxassetid://10709810534",
	["lucide-codesandbox"] = "rbxassetid://10709810676",
	["lucide-coffee"] = "rbxassetid://10709810814",
	["lucide-cog"] = "rbxassetid://10709810948",
	["lucide-coins"] = "rbxassetid://10709811110",
	["lucide-columns"] = "rbxassetid://10709811261",
	["lucide-command"] = "rbxassetid://10709811365",
	["lucide-compass"] = "rbxassetid://10709811445",
	["lucide-component"] = "rbxassetid://10709811595",
	["lucide-concierge-bell"] = "rbxassetid://10709811706",
	["lucide-connection"] = "rbxassetid://10747361219",
	["lucide-contact"] = "rbxassetid://10709811834",
	["lucide-contrast"] = "rbxassetid://10709811939",
	["lucide-cookie"] = "rbxassetid://10709812067",
	["lucide-copy"] = "rbxassetid://10709812159",
	["lucide-copyleft"] = "rbxassetid://10709812251",
	["lucide-copyright"] = "rbxassetid://10709812311",
	["lucide-corner-down-left"] = "rbxassetid://10709812396",
	["lucide-corner-down-right"] = "rbxassetid://10709812485",
	["lucide-corner-left-down"] = "rbxassetid://10709812632",
	["lucide-corner-left-up"] = "rbxassetid://10709812784",
	["lucide-corner-right-down"] = "rbxassetid://10709812939",
	["lucide-corner-right-up"] = "rbxassetid://10709813094",
	["lucide-corner-up-left"] = "rbxassetid://10709813185",
	["lucide-corner-up-right"] = "rbxassetid://10709813281",
	["lucide-cpu"] = "rbxassetid://10709813383",
	["lucide-croissant"] = "rbxassetid://10709818125",
	["lucide-crop"] = "rbxassetid://10709818245",
	["lucide-cross"] = "rbxassetid://10709818399",
	["lucide-crosshair"] = "rbxassetid://10709818534",
	["lucide-crown"] = "rbxassetid://10709818626",
	["lucide-cup-soda"] = "rbxassetid://10709818763",
	["lucide-curly-braces"] = "rbxassetid://10709818847",
	["lucide-currency"] = "rbxassetid://10709818931",
	["lucide-container"] = "rbxassetid://17466205552",
	["lucide-database"] = "rbxassetid://10709818996",
	["lucide-delete"] = "rbxassetid://10709819059",
	["lucide-diamond"] = "rbxassetid://10709819149",
	["lucide-dice-1"] = "rbxassetid://10709819266",
	["lucide-dice-2"] = "rbxassetid://10709819361",
	["lucide-dice-3"] = "rbxassetid://10709819508",
	["lucide-dice-4"] = "rbxassetid://10709819670",
	["lucide-dice-5"] = "rbxassetid://10709819801",
	["lucide-dice-6"] = "rbxassetid://10709819896",
	["lucide-dices"] = "rbxassetid://10723343321",
	["lucide-diff"] = "rbxassetid://10723343416",
	["lucide-disc"] = "rbxassetid://10723343537",
	["lucide-divide"] = "rbxassetid://10723343805",
	["lucide-divide-circle"] = "rbxassetid://10723343636",
	["lucide-divide-square"] = "rbxassetid://10723343737",
	["lucide-dollar-sign"] = "rbxassetid://10723343958",
	["lucide-download"] = "rbxassetid://10723344270",
	["lucide-download-cloud"] = "rbxassetid://10723344088",
	["lucide-door-open"] = "rbxassetid://124179241653522",
	["lucide-droplet"] = "rbxassetid://10723344432",
	["lucide-droplets"] = "rbxassetid://10734883356",
	["lucide-drumstick"] = "rbxassetid://10723344737",
	["lucide-edit"] = "rbxassetid://10734883598",
	["lucide-edit-2"] = "rbxassetid://10723344885",
	["lucide-edit-3"] = "rbxassetid://10723345088",
	["lucide-egg"] = "rbxassetid://10723345518",
	["lucide-egg-fried"] = "rbxassetid://10723345347",
	["lucide-electricity"] = "rbxassetid://10723345749",
	["lucide-electricity-off"] = "rbxassetid://10723345643",
	["lucide-equal"] = "rbxassetid://10723345990",
	["lucide-equal-not"] = "rbxassetid://10723345866",
	["lucide-eraser"] = "rbxassetid://10723346158",
	["lucide-euro"] = "rbxassetid://10723346372",
	["lucide-expand"] = "rbxassetid://10723346553",
	["lucide-external-link"] = "rbxassetid://10723346684",
	["lucide-eye"] = "rbxassetid://10723346959",
	["lucide-eye-off"] = "rbxassetid://10723346871",
	["lucide-factory"] = "rbxassetid://10723347051",
	["lucide-fan"] = "rbxassetid://10723354359",
	["lucide-fast-forward"] = "rbxassetid://10723354521",
	["lucide-feather"] = "rbxassetid://10723354671",
	["lucide-figma"] = "rbxassetid://10723354801",
	["lucide-file"] = "rbxassetid://10723374641",
	["lucide-file-archive"] = "rbxassetid://10723354921",
	["lucide-file-audio"] = "rbxassetid://10723355148",
	["lucide-file-audio-2"] = "rbxassetid://10723355026",
	["lucide-file-axis-3d"] = "rbxassetid://10723355272",
	["lucide-file-badge"] = "rbxassetid://10723355622",
	["lucide-file-badge-2"] = "rbxassetid://10723355451",
	["lucide-file-bar-chart"] = "rbxassetid://10723355887",
	["lucide-file-bar-chart-2"] = "rbxassetid://10723355746",
	["lucide-file-box"] = "rbxassetid://10723355989",
	["lucide-file-check"] = "rbxassetid://10723356210",
	["lucide-file-check-2"] = "rbxassetid://10723356100",
	["lucide-file-clock"] = "rbxassetid://10723356329",
	["lucide-file-code"] = "rbxassetid://10723356507",
	["lucide-file-cog"] = "rbxassetid://10723356830",
	["lucide-file-cog-2"] = "rbxassetid://10723356676",
	["lucide-file-diff"] = "rbxassetid://10723357039",
	["lucide-file-digit"] = "rbxassetid://10723357151",
	["lucide-file-down"] = "rbxassetid://10723357322",
	["lucide-file-edit"] = "rbxassetid://10723357495",
	["lucide-file-heart"] = "rbxassetid://10723357637",
	["lucide-file-image"] = "rbxassetid://10723357790",
	["lucide-file-input"] = "rbxassetid://10723357933",
	["lucide-file-json"] = "rbxassetid://10723364435",
	["lucide-file-json-2"] = "rbxassetid://10723364361",
	["lucide-file-key"] = "rbxassetid://10723364605",
	["lucide-file-key-2"] = "rbxassetid://10723364515",
	["lucide-file-line-chart"] = "rbxassetid://10723364725",
	["lucide-file-lock"] = "rbxassetid://10723364957",
	["lucide-file-lock-2"] = "rbxassetid://10723364861",
	["lucide-file-minus"] = "rbxassetid://10723365254",
	["lucide-file-minus-2"] = "rbxassetid://10723365086",
	["lucide-file-output"] = "rbxassetid://10723365457",
	["lucide-file-pie-chart"] = "rbxassetid://10723365598",
	["lucide-file-plus"] = "rbxassetid://10723365877",
	["lucide-file-plus-2"] = "rbxassetid://10723365766",
	["lucide-file-question"] = "rbxassetid://10723365987",
	["lucide-file-scan"] = "rbxassetid://10723366167",
	["lucide-file-search"] = "rbxassetid://10723366550",
	["lucide-file-search-2"] = "rbxassetid://10723366340",
	["lucide-file-signature"] = "rbxassetid://10723366741",
	["lucide-file-spreadsheet"] = "rbxassetid://10723366962",
	["lucide-file-symlink"] = "rbxassetid://10723367098",
	["lucide-file-terminal"] = "rbxassetid://10723367244",
	["lucide-file-text"] = "rbxassetid://10723367380",
	["lucide-file-type"] = "rbxassetid://10723367606",
	["lucide-file-type-2"] = "rbxassetid://10723367509",
	["lucide-file-up"] = "rbxassetid://10723367734",
	["lucide-file-video"] = "rbxassetid://10723373884",
	["lucide-file-video-2"] = "rbxassetid://10723367834",
	["lucide-file-volume"] = "rbxassetid://10723374172",
	["lucide-file-volume-2"] = "rbxassetid://10723374030",
	["lucide-file-warning"] = "rbxassetid://10723374276",
	["lucide-file-x"] = "rbxassetid://10723374544",
	["lucide-file-x-2"] = "rbxassetid://10723374378",
	["lucide-files"] = "rbxassetid://10723374759",
	["lucide-film"] = "rbxassetid://10723374981",
	["lucide-filter"] = "rbxassetid://10723375128",
	["lucide-fingerprint"] = "rbxassetid://10723375250",
	["lucide-flag"] = "rbxassetid://10723375890",
	["lucide-flag-off"] = "rbxassetid://10723375443",
	["lucide-flag-triangle-left"] = "rbxassetid://10723375608",
	["lucide-flag-triangle-right"] = "rbxassetid://10723375727",
	["lucide-flame"] = "rbxassetid://10723376114",
	["lucide-flashlight"] = "rbxassetid://10723376471",
	["lucide-flashlight-off"] = "rbxassetid://10723376365",
	["lucide-flask-conical"] = "rbxassetid://10734883986",
	["lucide-flask-round"] = "rbxassetid://10723376614",
	["lucide-flip-horizontal"] = "rbxassetid://10723376884",
	["lucide-flip-horizontal-2"] = "rbxassetid://10723376745",
	["lucide-flip-vertical"] = "rbxassetid://10723377138",
	["lucide-flip-vertical-2"] = "rbxassetid://10723377026",
	["lucide-flower"] = "rbxassetid://10747830374",
	["lucide-flower-2"] = "rbxassetid://10723377305",
	["lucide-focus"] = "rbxassetid://10723377537",
	["lucide-folder"] = "rbxassetid://10723387563",
	["lucide-folder-archive"] = "rbxassetid://10723384478",
	["lucide-folder-check"] = "rbxassetid://10723384605",
	["lucide-folder-clock"] = "rbxassetid://10723384731",
	["lucide-folder-closed"] = "rbxassetid://10723384893",
	["lucide-folder-cog"] = "rbxassetid://10723385213",
	["lucide-folder-cog-2"] = "rbxassetid://10723385036",
	["lucide-folder-down"] = "rbxassetid://10723385338",
	["lucide-folder-edit"] = "rbxassetid://10723385445",
	["lucide-folder-heart"] = "rbxassetid://10723385545",
	["lucide-folder-input"] = "rbxassetid://10723385721",
	["lucide-folder-key"] = "rbxassetid://10723385848",
	["lucide-folder-lock"] = "rbxassetid://10723386005",
	["lucide-folder-minus"] = "rbxassetid://10723386127",
	["lucide-folder-open"] = "rbxassetid://10723386277",
	["lucide-folder-output"] = "rbxassetid://10723386386",
	["lucide-folder-plus"] = "rbxassetid://10723386531",
	["lucide-folder-search"] = "rbxassetid://10723386787",
	["lucide-folder-search-2"] = "rbxassetid://10723386674",
	["lucide-folder-symlink"] = "rbxassetid://10723386930",
	["lucide-folder-tree"] = "rbxassetid://10723387085",
	["lucide-folder-up"] = "rbxassetid://10723387265",
	["lucide-folder-x"] = "rbxassetid://10723387448",
	["lucide-folders"] = "rbxassetid://10723387721",
	["lucide-form-input"] = "rbxassetid://10723387841",
	["lucide-forward"] = "rbxassetid://10723388016",
	["lucide-frame"] = "rbxassetid://10723394389",
	["lucide-framer"] = "rbxassetid://10723394565",
	["lucide-frown"] = "rbxassetid://10723394681",
	["lucide-fuel"] = "rbxassetid://10723394846",
	["lucide-function-square"] = "rbxassetid://10723395041",
	["lucide-gamepad"] = "rbxassetid://10723395457",
	["lucide-gamepad-2"] = "rbxassetid://10723395215",
	["lucide-gauge"] = "rbxassetid://10723395708",
	["lucide-gavel"] = "rbxassetid://10723395896",
	["lucide-gem"] = "rbxassetid://10723396000",
	["lucide-ghost"] = "rbxassetid://10723396107",
	["lucide-gift"] = "rbxassetid://10723396402",
	["lucide-gift-card"] = "rbxassetid://10723396225",
	["lucide-git-branch"] = "rbxassetid://10723396676",
	["lucide-git-branch-plus"] = "rbxassetid://10723396542",
	["lucide-git-commit"] = "rbxassetid://10723396812",
	["lucide-git-compare"] = "rbxassetid://10723396954",
	["lucide-git-fork"] = "rbxassetid://10723397049",
	["lucide-git-merge"] = "rbxassetid://10723397165",
	["lucide-git-pull-request"] = "rbxassetid://10723397431",
	["lucide-git-pull-request-closed"] = "rbxassetid://10723397268",
	["lucide-git-pull-request-draft"] = "rbxassetid://10734884302",
	["lucide-glass"] = "rbxassetid://10723397788",
	["lucide-glass-2"] = "rbxassetid://10723397529",
	["lucide-glass-water"] = "rbxassetid://10723397678",
	["lucide-glasses"] = "rbxassetid://10723397895",
	["lucide-globe"] = "rbxassetid://10723404337",
	["lucide-globe-2"] = "rbxassetid://10723398002",
	["lucide-grab"] = "rbxassetid://10723404472",
	["lucide-graduation-cap"] = "rbxassetid://10723404691",
	["lucide-grape"] = "rbxassetid://10723404822",
	["lucide-grid"] = "rbxassetid://10723404936",
	["lucide-grip-horizontal"] = "rbxassetid://10723405089",
	["lucide-grip-vertical"] = "rbxassetid://10723405236",
	["lucide-hammer"] = "rbxassetid://10723405360",
	["lucide-hand"] = "rbxassetid://10723405649",
	["lucide-hand-metal"] = "rbxassetid://10723405508",
	["lucide-hard-drive"] = "rbxassetid://10723405749",
	["lucide-hard-hat"] = "rbxassetid://10723405859",
	["lucide-hash"] = "rbxassetid://10723405975",
	["lucide-haze"] = "rbxassetid://10723406078",
	["lucide-headphones"] = "rbxassetid://10723406165",
	["lucide-heart"] = "rbxassetid://10723406885",
	["lucide-heart-crack"] = "rbxassetid://10723406299",
	["lucide-heart-handshake"] = "rbxassetid://10723406480",
	["lucide-heart-off"] = "rbxassetid://10723406662",
	["lucide-heart-pulse"] = "rbxassetid://10723406795",
	["lucide-help-circle"] = "rbxassetid://10723406988",
	["lucide-hexagon"] = "rbxassetid://10723407092",
	["lucide-highlighter"] = "rbxassetid://10723407192",
	["lucide-history"] = "rbxassetid://10723407335",
	["lucide-home"] = "rbxassetid://10723407389",
	["lucide-hourglass"] = "rbxassetid://10723407498",
	["lucide-ice-cream"] = "rbxassetid://10723414308",
	["lucide-image"] = "rbxassetid://10723415040",
	["lucide-image-minus"] = "rbxassetid://10723414487",
	["lucide-image-off"] = "rbxassetid://10723414677",
	["lucide-image-plus"] = "rbxassetid://10723414827",
	["lucide-import"] = "rbxassetid://10723415205",
	["lucide-inbox"] = "rbxassetid://10723415335",
	["lucide-indent"] = "rbxassetid://10723415494",
	["lucide-indian-rupee"] = "rbxassetid://10723415642",
	["lucide-infinity"] = "rbxassetid://10723415766",
	["lucide-info"] = "rbxassetid://10723415903",
	["lucide-inspect"] = "rbxassetid://10723416057",
	["lucide-italic"] = "rbxassetid://10723416195",
	["lucide-japanese-yen"] = "rbxassetid://10723416363",
	["lucide-joystick"] = "rbxassetid://10723416527",
	["lucide-key"] = "rbxassetid://10723416652",
	["lucide-keyboard"] = "rbxassetid://10723416765",
	["lucide-lamp"] = "rbxassetid://10723417513",
	["lucide-lamp-ceiling"] = "rbxassetid://10723416922",
	["lucide-lamp-desk"] = "rbxassetid://10723417016",
	["lucide-lamp-floor"] = "rbxassetid://10723417131",
	["lucide-lamp-wall-down"] = "rbxassetid://10723417240",
	["lucide-lamp-wall-up"] = "rbxassetid://10723417356",
	["lucide-landmark"] = "rbxassetid://10723417608",
	["lucide-languages"] = "rbxassetid://10723417703",
	["lucide-laptop"] = "rbxassetid://10723423881",
	["lucide-laptop-2"] = "rbxassetid://10723417797",
	["lucide-lasso"] = "rbxassetid://10723424235",
	["lucide-lasso-select"] = "rbxassetid://10723424058",
	["lucide-laugh"] = "rbxassetid://10723424372",
	["lucide-layers"] = "rbxassetid://10723424505",
	["lucide-layout"] = "rbxassetid://10723425376",
	["lucide-layout-dashboard"] = "rbxassetid://10723424646",
	["lucide-layout-grid"] = "rbxassetid://10723424838",
	["lucide-layout-list"] = "rbxassetid://10723424963",
	["lucide-layout-template"] = "rbxassetid://10723425187",
	["lucide-leaf"] = "rbxassetid://10723425539",
	["lucide-library"] = "rbxassetid://10723425615",
	["lucide-life-buoy"] = "rbxassetid://10723425685",
	["lucide-lightbulb"] = "rbxassetid://10723425852",
	["lucide-lightbulb-off"] = "rbxassetid://10723425762",
	["lucide-line-chart"] = "rbxassetid://10723426393",
	["lucide-link"] = "rbxassetid://10723426722",
	["lucide-link-2"] = "rbxassetid://10723426595",
	["lucide-link-2-off"] = "rbxassetid://10723426513",
	["lucide-list"] = "rbxassetid://10723433811",
	["lucide-list-checks"] = "rbxassetid://10734884548",
	["lucide-list-end"] = "rbxassetid://10723426886",
	["lucide-list-minus"] = "rbxassetid://10723426986",
	["lucide-list-music"] = "rbxassetid://10723427081",
	["lucide-list-ordered"] = "rbxassetid://10723427199",
	["lucide-list-plus"] = "rbxassetid://10723427334",
	["lucide-list-start"] = "rbxassetid://10723427494",
	["lucide-list-video"] = "rbxassetid://10723427619",
	["lucide-list-todo"] = "rbxassetid://17376008003",
	["lucide-list-x"] = "rbxassetid://10723433655",
	["lucide-loader"] = "rbxassetid://10723434070",
	["lucide-loader-2"] = "rbxassetid://10723433935",
	["lucide-locate"] = "rbxassetid://10723434557",
	["lucide-locate-fixed"] = "rbxassetid://10723434236",
	["lucide-locate-off"] = "rbxassetid://10723434379",
	["lucide-lock"] = "rbxassetid://10723434711",
	["lucide-log-in"] = "rbxassetid://10723434830",
	["lucide-log-out"] = "rbxassetid://10723434906",
	["lucide-luggage"] = "rbxassetid://10723434993",
	["lucide-magnet"] = "rbxassetid://10723435069",
	["lucide-mail"] = "rbxassetid://10734885430",
	["lucide-mail-check"] = "rbxassetid://10723435182",
	["lucide-mail-minus"] = "rbxassetid://10723435261",
	["lucide-mail-open"] = "rbxassetid://10723435342",
	["lucide-mail-plus"] = "rbxassetid://10723435443",
	["lucide-mail-question"] = "rbxassetid://10723435515",
	["lucide-mail-search"] = "rbxassetid://10734884739",
	["lucide-mail-warning"] = "rbxassetid://10734885015",
	["lucide-mail-x"] = "rbxassetid://10734885247",
	["lucide-mails"] = "rbxassetid://10734885614",
	["lucide-map"] = "rbxassetid://10734886202",
	["lucide-map-pin"] = "rbxassetid://10734886004",
	["lucide-map-pin-off"] = "rbxassetid://10734885803",
	["lucide-maximize"] = "rbxassetid://10734886735",
	["lucide-maximize-2"] = "rbxassetid://10734886496",
	["lucide-medal"] = "rbxassetid://10734887072",
	["lucide-megaphone"] = "rbxassetid://10734887454",
	["lucide-megaphone-off"] = "rbxassetid://10734887311",
	["lucide-meh"] = "rbxassetid://10734887603",
	["lucide-menu"] = "rbxassetid://10734887784",
	["lucide-message-circle"] = "rbxassetid://10734888000",
	["lucide-message-square"] = "rbxassetid://10734888228",
	["lucide-mic"] = "rbxassetid://10734888864",
	["lucide-mic-2"] = "rbxassetid://10734888430",
	["lucide-mic-off"] = "rbxassetid://10734888646",
	["lucide-microscope"] = "rbxassetid://10734889106",
	["lucide-microwave"] = "rbxassetid://10734895076",
	["lucide-milestone"] = "rbxassetid://10734895310",
	["lucide-minimize"] = "rbxassetid://10734895698",
	["lucide-minimize-2"] = "rbxassetid://10734895530",
	["lucide-minus"] = "rbxassetid://10734896206",
	["lucide-minus-circle"] = "rbxassetid://10734895856",
	["lucide-minus-square"] = "rbxassetid://10734896029",
	["lucide-monitor"] = "rbxassetid://10734896881",
	["lucide-monitor-off"] = "rbxassetid://10734896360",
	["lucide-monitor-speaker"] = "rbxassetid://10734896512",
	["lucide-moon"] = "rbxassetid://10734897102",
	["lucide-more-horizontal"] = "rbxassetid://10734897250",
	["lucide-more-vertical"] = "rbxassetid://10734897387",
	["lucide-mountain"] = "rbxassetid://10734897956",
	["lucide-mountain-snow"] = "rbxassetid://10734897665",
	["lucide-mouse"] = "rbxassetid://10734898592",
	["lucide-mouse-pointer"] = "rbxassetid://10734898476",
	["lucide-mouse-pointer-2"] = "rbxassetid://10734898194",
	["lucide-mouse-pointer-click"] = "rbxassetid://10734898355",
	["lucide-move"] = "rbxassetid://10734900011",
	["lucide-move-3d"] = "rbxassetid://10734898756",
	["lucide-move-diagonal"] = "rbxassetid://10734899164",
	["lucide-move-diagonal-2"] = "rbxassetid://10734898934",
	["lucide-move-horizontal"] = "rbxassetid://10734899414",
	["lucide-move-vertical"] = "rbxassetid://10734899821",
	["lucide-music"] = "rbxassetid://10734905958",
	["lucide-music-2"] = "rbxassetid://10734900215",
	["lucide-music-3"] = "rbxassetid://10734905665",
	["lucide-music-4"] = "rbxassetid://10734905823",
	["lucide-navigation"] = "rbxassetid://10734906744",
	["lucide-navigation-2"] = "rbxassetid://10734906332",
	["lucide-navigation-2-off"] = "rbxassetid://10734906144",
	["lucide-navigation-off"] = "rbxassetid://10734906580",
	["lucide-network"] = "rbxassetid://10734906975",
	["lucide-newspaper"] = "rbxassetid://10734907168",
	["lucide-octagon"] = "rbxassetid://10734907361",
	["lucide-option"] = "rbxassetid://10734907649",
	["lucide-outdent"] = "rbxassetid://10734907933",
	["lucide-package"] = "rbxassetid://10734909540",
	["lucide-package-2"] = "rbxassetid://10734908151",
	["lucide-package-check"] = "rbxassetid://10734908384",
	["lucide-package-minus"] = "rbxassetid://10734908626",
	["lucide-package-open"] = "rbxassetid://10734908793",
	["lucide-package-plus"] = "rbxassetid://10734909016",
	["lucide-package-search"] = "rbxassetid://10734909196",
	["lucide-package-x"] = "rbxassetid://10734909375",
	["lucide-paint-bucket"] = "rbxassetid://10734909847",
	["lucide-paintbrush"] = "rbxassetid://10734910187",
	["lucide-paintbrush-2"] = "rbxassetid://10734910030",
	["lucide-palette"] = "rbxassetid://10734910430",
	["lucide-palmtree"] = "rbxassetid://10734910680",
	["lucide-paperclip"] = "rbxassetid://10734910927",
	["lucide-party-popper"] = "rbxassetid://10734918735",
	["lucide-pause"] = "rbxassetid://10734919336",
	["lucide-pause-circle"] = "rbxassetid://10735024209",
	["lucide-pause-octagon"] = "rbxassetid://10734919143",
	["lucide-pen-tool"] = "rbxassetid://10734919503",
	["lucide-pencil"] = "rbxassetid://10734919691",
	["lucide-percent"] = "rbxassetid://10734919919",
	["lucide-person-standing"] = "rbxassetid://10734920149",
	["lucide-phone"] = "rbxassetid://10734921524",
	["lucide-phone-call"] = "rbxassetid://10734920305",
	["lucide-phone-forwarded"] = "rbxassetid://10734920508",
	["lucide-phone-incoming"] = "rbxassetid://10734920694",
	["lucide-phone-missed"] = "rbxassetid://10734920845",
	["lucide-phone-off"] = "rbxassetid://10734921077",
	["lucide-phone-outgoing"] = "rbxassetid://10734921288",
	["lucide-pie-chart"] = "rbxassetid://10734921727",
	["lucide-piggy-bank"] = "rbxassetid://10734921935",
	["lucide-pin"] = "rbxassetid://10734922324",
	["lucide-pin-off"] = "rbxassetid://10734922180",
	["lucide-pipette"] = "rbxassetid://10734922497",
	["lucide-pizza"] = "rbxassetid://10734922774",
	["lucide-plane"] = "rbxassetid://10734922971",
	["lucide-plane-landing"] = "rbxassetid://17376029914",
	["lucide-play"] = "rbxassetid://10734923549",
	["lucide-play-circle"] = "rbxassetid://10734923214",
	["lucide-plus"] = "rbxassetid://10734924532",
	["lucide-plus-circle"] = "rbxassetid://10734923868",
	["lucide-plus-square"] = "rbxassetid://10734924219",
	["lucide-podcast"] = "rbxassetid://10734929553",
	["lucide-pointer"] = "rbxassetid://10734929723",
	["lucide-pound-sterling"] = "rbxassetid://10734929981",
	["lucide-power"] = "rbxassetid://10734930466",
	["lucide-power-off"] = "rbxassetid://10734930257",
	["lucide-printer"] = "rbxassetid://10734930632",
	["lucide-puzzle"] = "rbxassetid://10734930886",
	["lucide-quote"] = "rbxassetid://10734931234",
	["lucide-radio"] = "rbxassetid://10734931596",
	["lucide-radio-receiver"] = "rbxassetid://10734931402",
	["lucide-rectangle-horizontal"] = "rbxassetid://10734931777",
	["lucide-rectangle-vertical"] = "rbxassetid://10734932081",
	["lucide-recycle"] = "rbxassetid://10734932295",
	["lucide-redo"] = "rbxassetid://10734932822",
	["lucide-redo-2"] = "rbxassetid://10734932586",
	["lucide-refresh-ccw"] = "rbxassetid://10734933056",
	["lucide-refresh-cw"] = "rbxassetid://10734933222",
	["lucide-refrigerator"] = "rbxassetid://10734933465",
	["lucide-regex"] = "rbxassetid://10734933655",
	["lucide-repeat"] = "rbxassetid://10734933966",
	["lucide-repeat-1"] = "rbxassetid://10734933826",
	["lucide-reply"] = "rbxassetid://10734934252",
	["lucide-reply-all"] = "rbxassetid://10734934132",
	["lucide-rewind"] = "rbxassetid://10734934347",
	["lucide-rocket"] = "rbxassetid://10734934585",
	["lucide-rocking-chair"] = "rbxassetid://10734939942",
	["lucide-rotate-3d"] = "rbxassetid://10734940107",
	["lucide-rotate-ccw"] = "rbxassetid://10734940376",
	["lucide-rotate-cw"] = "rbxassetid://10734940654",
	["lucide-rss"] = "rbxassetid://10734940825",
	["lucide-ruler"] = "rbxassetid://10734941018",
	["lucide-russian-ruble"] = "rbxassetid://10734941199",
	["lucide-sailboat"] = "rbxassetid://10734941354",
	["lucide-save"] = "rbxassetid://10734941499",
	["lucide-scale"] = "rbxassetid://10734941912",
	["lucide-scale-3d"] = "rbxassetid://10734941739",
	["lucide-scaling"] = "rbxassetid://10734942072",
	["lucide-scan"] = "rbxassetid://10734942565",
	["lucide-scan-face"] = "rbxassetid://10734942198",
	["lucide-scan-line"] = "rbxassetid://10734942351",
	["lucide-scissors"] = "rbxassetid://10734942778",
	["lucide-screen-share"] = "rbxassetid://10734943193",
	["lucide-screen-share-off"] = "rbxassetid://10734942967",
	["lucide-shell"] = "rbxassetid://83825045910816",
	["lucide-scroll"] = "rbxassetid://10734943448",
	["lucide-search"] = "rbxassetid://10734943674",
	["lucide-send"] = "rbxassetid://10734943902",
	["lucide-separator-horizontal"] = "rbxassetid://10734944115",
	["lucide-separator-vertical"] = "rbxassetid://10734944326",
	["lucide-server"] = "rbxassetid://10734949856",
	["lucide-server-cog"] = "rbxassetid://10734944444",
	["lucide-server-crash"] = "rbxassetid://10734944554",
	["lucide-server-off"] = "rbxassetid://10734944668",
	["lucide-settings"] = "rbxassetid://10734950309",
	["lucide-settings-2"] = "rbxassetid://10734950020",
	["lucide-share"] = "rbxassetid://10734950813",
	["lucide-share-2"] = "rbxassetid://10734950553",
	["lucide-sheet"] = "rbxassetid://10734951038",
	["lucide-shield"] = "rbxassetid://10734951847",
	["lucide-shield-alert"] = "rbxassetid://10734951173",
	["lucide-shield-check"] = "rbxassetid://10734951367",
	["lucide-shield-close"] = "rbxassetid://10734951535",
	["lucide-shield-off"] = "rbxassetid://10734951684",
	["lucide-shirt"] = "rbxassetid://10734952036",
	["lucide-shopping-bag"] = "rbxassetid://10734952273",
	["lucide-shopping-cart"] = "rbxassetid://10734952479",
	["lucide-shovel"] = "rbxassetid://10734952773",
	["lucide-shower-head"] = "rbxassetid://10734952942",
	["lucide-shrink"] = "rbxassetid://10734953073",
	["lucide-shrub"] = "rbxassetid://10734953241",
	["lucide-shuffle"] = "rbxassetid://10734953451",
	["lucide-sidebar"] = "rbxassetid://10734954301",
	["lucide-sidebar-close"] = "rbxassetid://10734953715",
	["lucide-sidebar-open"] = "rbxassetid://10734954000",
	["lucide-sigma"] = "rbxassetid://10734954538",
	["lucide-signal"] = "rbxassetid://10734961133",
	["lucide-signal-high"] = "rbxassetid://10734954807",
	["lucide-signal-low"] = "rbxassetid://10734955080",
	["lucide-signal-medium"] = "rbxassetid://10734955336",
	["lucide-signal-zero"] = "rbxassetid://10734960878",
	["lucide-siren"] = "rbxassetid://10734961284",
	["lucide-skip-back"] = "rbxassetid://10734961526",
	["lucide-skip-forward"] = "rbxassetid://10734961809",
	["lucide-skull"] = "rbxassetid://10734962068",
	["lucide-slack"] = "rbxassetid://10734962339",
	["lucide-slash"] = "rbxassetid://10734962600",
	["lucide-slice"] = "rbxassetid://10734963024",
	["lucide-sliders"] = "rbxassetid://10734963400",
	["lucide-sliders-horizontal"] = "rbxassetid://10734963191",
	["lucide-smartphone"] = "rbxassetid://10734963940",
	["lucide-smartphone-charging"] = "rbxassetid://10734963671",
	["lucide-smile"] = "rbxassetid://10734964441",
	["lucide-smile-plus"] = "rbxassetid://10734964188",
	["lucide-snowflake"] = "rbxassetid://10734964600",
	["lucide-sofa"] = "rbxassetid://10734964852",
	["lucide-sort-asc"] = "rbxassetid://10734965115",
	["lucide-sort-desc"] = "rbxassetid://10734965287",
	["lucide-speaker"] = "rbxassetid://10734965419",
	["lucide-sprout"] = "rbxassetid://10734965572",
	["lucide-square"] = "rbxassetid://10734965702",
	["lucide-star"] = "rbxassetid://10734966248",
	["lucide-star-half"] = "rbxassetid://10734965897",
	["lucide-star-off"] = "rbxassetid://10734966097",
	["lucide-stethoscope"] = "rbxassetid://10734966384",
	["lucide-sticker"] = "rbxassetid://10734972234",
	["lucide-sticky-note"] = "rbxassetid://10734972463",
	["lucide-stop-circle"] = "rbxassetid://10734972621",
	["lucide-stretch-horizontal"] = "rbxassetid://10734972862",
	["lucide-stretch-vertical"] = "rbxassetid://10734973130",
	["lucide-strikethrough"] = "rbxassetid://10734973290",
	["lucide-subscript"] = "rbxassetid://10734973457",
	["lucide-sun"] = "rbxassetid://10734974297",
	["lucide-sun-dim"] = "rbxassetid://10734973645",
	["lucide-sun-medium"] = "rbxassetid://10734973778",
	["lucide-sun-moon"] = "rbxassetid://10734973999",
	["lucide-sun-snow"] = "rbxassetid://10734974130",
	["lucide-sunrise"] = "rbxassetid://10734974522",
	["lucide-sunset"] = "rbxassetid://10734974689",
	["lucide-superscript"] = "rbxassetid://10734974850",
	["lucide-swiss-franc"] = "rbxassetid://10734975024",
	["lucide-switch-camera"] = "rbxassetid://10734975214",
	["lucide-sword"] = "rbxassetid://10734975486",
	["lucide-swords"] = "rbxassetid://10734975692",
	["lucide-syringe"] = "rbxassetid://10734975932",
	["lucide-table"] = "rbxassetid://10734976230",
	["lucide-table-2"] = "rbxassetid://10734976097",
	["lucide-tablet"] = "rbxassetid://10734976394",
	["lucide-tag"] = "rbxassetid://10734976528",
	["lucide-tags"] = "rbxassetid://10734976739",
	["lucide-target"] = "rbxassetid://10734977012",
	["lucide-tent"] = "rbxassetid://10734981750",
	["lucide-terminal"] = "rbxassetid://10734982144",
	["lucide-terminal-square"] = "rbxassetid://10734981995",
	["lucide-text-cursor"] = "rbxassetid://10734982395",
	["lucide-text-cursor-input"] = "rbxassetid://10734982297",
	["lucide-thermometer"] = "rbxassetid://10734983134",
	["lucide-thermometer-snowflake"] = "rbxassetid://10734982571",
	["lucide-thermometer-sun"] = "rbxassetid://10734982771",
	["lucide-thumbs-down"] = "rbxassetid://10734983359",
	["lucide-thumbs-up"] = "rbxassetid://10734983629",
	["lucide-ticket"] = "rbxassetid://10734983868",
	["lucide-timer"] = "rbxassetid://10734984606",
	["lucide-timer-off"] = "rbxassetid://10734984138",
	["lucide-timer-reset"] = "rbxassetid://10734984355",
	["lucide-toggle-left"] = "rbxassetid://10734984834",
	["lucide-toggle-right"] = "rbxassetid://10734985040",
	["lucide-tornado"] = "rbxassetid://10734985247",
	["lucide-toy-brick"] = "rbxassetid://10747361919",
	["lucide-train"] = "rbxassetid://10747362105",
	["lucide-trash"] = "rbxassetid://10747362393",
	["lucide-trash-2"] = "rbxassetid://10747362241",
	["lucide-tree-deciduous"] = "rbxassetid://10747362534",
	["lucide-tree-pine"] = "rbxassetid://10747362748",
	["lucide-trees"] = "rbxassetid://10747363016",
	["lucide-trending-down"] = "rbxassetid://10747363205",
	["lucide-trending-up"] = "rbxassetid://10747363465",
	["lucide-triangle"] = "rbxassetid://10747363621",
	["lucide-trophy"] = "rbxassetid://10747363809",
	["lucide-truck"] = "rbxassetid://10747364031",
	["lucide-tv"] = "rbxassetid://10747364593",
	["lucide-tv-2"] = "rbxassetid://10747364302",
	["lucide-type"] = "rbxassetid://10747364761",
	["lucide-umbrella"] = "rbxassetid://10747364971",
	["lucide-underline"] = "rbxassetid://10747365191",
	["lucide-undo"] = "rbxassetid://10747365484",
	["lucide-undo-2"] = "rbxassetid://10747365359",
	["lucide-unlink"] = "rbxassetid://10747365771",
	["lucide-unlink-2"] = "rbxassetid://10747397871",
	["lucide-unlock"] = "rbxassetid://10747366027",
	["lucide-upload"] = "rbxassetid://10747366434",
	["lucide-upload-cloud"] = "rbxassetid://10747366266",
	["lucide-usb"] = "rbxassetid://10747366606",
	["lucide-user"] = "rbxassetid://10747373176",
	["lucide-user-check"] = "rbxassetid://10747371901",
	["lucide-user-cog"] = "rbxassetid://10747372167",
	["lucide-user-minus"] = "rbxassetid://10747372346",
	["lucide-user-plus"] = "rbxassetid://10747372702",
	["lucide-user-x"] = "rbxassetid://10747372992",
	["lucide-users"] = "rbxassetid://10747373426",
	["lucide-utensils"] = "rbxassetid://10747373821",
	["lucide-utensils-crossed"] = "rbxassetid://10747373629",
	["lucide-venetian-mask"] = "rbxassetid://10747374003",
	["lucide-verified"] = "rbxassetid://10747374131",
	["lucide-vibrate"] = "rbxassetid://10747374489",
	["lucide-vibrate-off"] = "rbxassetid://10747374269",
	["lucide-video"] = "rbxassetid://10747374938",
	["lucide-video-off"] = "rbxassetid://10747374721",
	["lucide-view"] = "rbxassetid://10747375132",
	["lucide-voicemail"] = "rbxassetid://10747375281",
	["lucide-volume"] = "rbxassetid://10747376008",
	["lucide-volume-1"] = "rbxassetid://10747375450",
	["lucide-volume-2"] = "rbxassetid://10747375679",
	["lucide-volume-x"] = "rbxassetid://10747375880",
	["lucide-wheat"] = "rbxassetid://80877624162595",
	["lucide-wallet"] = "rbxassetid://10747376205",
	["lucide-wand"] = "rbxassetid://10747376565",
	["lucide-wand-2"] = "rbxassetid://10747376349",
	["lucide-watch"] = "rbxassetid://10747376722",
	["lucide-waves"] = "rbxassetid://10747376931",
	["lucide-webcam"] = "rbxassetid://10747381992",
	["lucide-wifi"] = "rbxassetid://10747382504",
	["lucide-wifi-off"] = "rbxassetid://10747382268",
	["lucide-wind"] = "rbxassetid://10747382750",
	["lucide-wrap-text"] = "rbxassetid://10747383065",
	["lucide-wrench"] = "rbxassetid://10747383470",
	["lucide-x"] = "rbxassetid://10747384394",
	["lucide-x-circle"] = "rbxassetid://10747383819",
	["lucide-x-octagon"] = "rbxassetid://10747384037",
	["lucide-x-square"] = "rbxassetid://10747384217",
	["lucide-zoom-in"] = "rbxassetid://10747384552",
	["lucide-zoom-out"] = "rbxassetid://10747384679",
	["lucide-cat"] = "rbxassetid://16935650691",
	["lucide-message-circle-question"] = "rbxassetid://16970049192",
	["lucide-webhook"] = "rbxassetid://17320556264",
	["lucide-dumbbell"] = "rbxassetid://18273453053"
}

function Library:GetIcon(Name)
	if Name ~= nil and Icons["lucide-" .. Name] then
		return Icons["lucide-" .. Name]
	end
	return nil
end

local Elements = {}
Elements.__index = Elements
Elements.__namecall = function(Table, Key, ...)
	return Elements[Key](...)
end

for _, ElementComponent in pairs(ElementsTable) do
	Elements["Add" .. ElementComponent.__type] = function(self, Idx, Config)
		ElementComponent.Container = self.Container
		ElementComponent.Type = self.Type
		ElementComponent.ScrollFrame = self.ScrollFrame
		ElementComponent.Library = Library

		return ElementComponent:New(Idx, Config)
	end
end

Library.Elements = Elements

if RunService:IsStudio() then
	makefolder = function(...) return ... end;
	makefile = function(...) return ... end;
	isfile = function(...) return ... end;
	isfolder = function(...) return ... end;
	readfile = function(...) return ... end;
	writefile = function(...) return ... end;
	listfiles = function (...) return {...} end;
end

local SaveManager = {} do
	SaveManager.Folder = "FluentSettings"
	SaveManager.Ignore = {}
	SaveManager.Parser = {
		Toggle = {
			Save = function(idx, object) 
				return { type = "Toggle", idx = idx, value = object.Value } 
			end,
			Load = function(idx, data)
				if SaveManager.Options[idx] then 
					SaveManager.Options[idx]:SetValue(data.value)
				end
			end,
		},
		Slider = {
			Save = function(idx, object)
				return { type = "Slider", idx = idx, value = tostring(object.Value) }
			end,
			Load = function(idx, data)
				if SaveManager.Options[idx] then 
					SaveManager.Options[idx]:SetValue(data.value)
				end
			end,
		},
		Dropdown = {
			Save = function(idx, object)
				return { type = "Dropdown", idx = idx, value = object.Value, mutli = object.Multi }
			end,
			Load = function(idx, data)
				if SaveManager.Options[idx] then 
					SaveManager.Options[idx]:SetValue(data.value)
				end
			end,
		},
		Colorpicker = {
			Save = function(idx, object)
				return { type = "Colorpicker", idx = idx, value = object.Value:ToHex(), transparency = object.Transparency }
			end,
			Load = function(idx, data)
				if SaveManager.Options[idx] then 
					SaveManager.Options[idx]:SetValueRGB(Color3.fromHex(data.value), data.transparency)
				end
			end,
		},
		Keybind = {
			Save = function(idx, object)
				return { type = "Keybind", idx = idx, mode = object.Mode, key = object.Value }
			end,
			Load = function(idx, data)
				if SaveManager.Options[idx] then 
					SaveManager.Options[idx]:SetValue(data.key, data.mode)
				end
			end,
		},

		Input = {
			Save = function(idx, object)
				return { type = "Input", idx = idx, text = object.Value }
			end,
			Load = function(idx, data)
				if SaveManager.Options[idx] and type(data.text) == "string" then
					SaveManager.Options[idx]:SetValue(data.text)
				end
			end,
		},
	}

	function SaveManager:SetIgnoreIndexes(list)
		for _, key in next, list do
			self.Ignore[key] = true
		end
	end

	function SaveManager:SetFolder(folder)
		self.Folder = folder;
		self:BuildFolderTree()
	end

	function SaveManager:Save(name)
		if (not name) then
			return false, "no config file is selected"
		end

		local fullPath = self.Folder .. "/" .. name .. ".json"

		local data = {
			objects = {}
		}

		for idx, option in next, SaveManager.Options do
			if not self.Parser[option.Type] then continue end
			if self.Ignore[idx] then continue end

			table.insert(data.objects, self.Parser[option.Type].Save(idx, option))
		end	

		local success, encoded = pcall(httpService.JSONEncode, httpService, data)
		if not success then
			return false, "failed to encode data"
		end

		writefile(fullPath, encoded)
		return true
	end

	function SaveManager:Load(name)
		if (not name) then
			return false, "no config file is selected"
		end

		local file = self.Folder .. "/" .. name .. ".json"
		if not isfile(file) then return false, "Create Config Save File" end

		local success, decoded = pcall(httpService.JSONDecode, httpService, readfile(file))
		if not success then return false, "decode error" end

		for _, option in next, decoded.objects do
			if self.Parser[option.type] and not self.Ignore[option.idx] then
				task.spawn(function() self.Parser[option.type].Load(option.idx, option) end) -- task.spawn() so the config loading wont get stuck.
			end
		end

		Fluent.SettingLoaded = true

		return true, decoded
	end

	function SaveManager:IgnoreThemeSettings()
		self:SetIgnoreIndexes({ 
			"InterfaceTheme", "AcrylicToggle", "TransparentToggle", "MenuKeybind"
		})
	end

	function SaveManager:BuildFolderTree()
		local paths = {
			self.Folder,
			self.Folder .. "/"
		}

		for i = 1, #paths do
			local str = paths[i]
			if not isfolder(str) then
				makefolder(str)
			end
		end
	end

	function SaveManager:RefreshConfigList()
		local list = listfiles(self.Folder .. "/")

		local out = {}
		for i = 1, #list do
			local file = list[i]
			if file:sub(-5) == ".json" then
				local pos = file:find(".json", 1, true)
				local start = pos

				local char = file:sub(pos, pos)
				while char ~= "/" and char ~= "\\" and char ~= "" do
					pos = pos - 1
					char = file:sub(pos, pos)
				end

				if char == "/" or char == "\\" then
					local name = file:sub(pos + 1, start - 1)
					if name ~= "options" then
						table.insert(out, name)
					end
				end
			end
		end

		return out
	end

	function SaveManager:SetLibrary(library)
		self.Library = library
		self.Options = library.Options
	end

	function SaveManager:LoadAutoloadConfig()
		if isfile(self.Folder .. "/autoload.txt") then
			local name = readfile(self.Folder .. "/autoload.txt")

			local success, err = self:Load(name)
			if not success then
				return self.Library:Notify({
					Title = "Interface",
					Content = "Config loader",
					SubContent = "Failed to load autoload config: " .. err,
					Duration = 7
				})
			end

			self.Library:Notify({
				Title = "Interface",
				Content = "Config loader",
				SubContent = string.format("Auto loaded config %q", name),
				Duration = 7
			})
		end
	end

	function SaveManager:BuildConfigSection(tab)
		assert(self.Library, "Must set SaveManager.Library")

		local section = tab:AddSection("Configuration")

		section:AddInput("SaveManager_ConfigName",    { Title = "Config name" })
		section:AddDropdown(" ", { Title = "Config list", Values = self:RefreshConfigList(), AllowNull = true })

		section:AddButton({
			Title = "Create config",
			Callback = function()
				local name = SaveManager.Options.SaveManager_ConfigName.Value

				if name:gsub(" ", "") == "" then 
					return self.Library:Notify({
						Title = "Interface",
						Content = "Config loader",
						SubContent = "Invalid config name (empty)",
						Duration = 7
					})
				end

				local success, err = self:Save(name)
				if not success then
					return self.Library:Notify({
						Title = "Interface",
						Content = "Config loader",
						SubContent = "Failed to save config: " .. err,
						Duration = 7
					})
				end

				self.Library:Notify({
					Title = "Interface",
					Content = "Config loader",
					SubContent = string.format("Created config %q", name),
					Duration = 7
				})

				SaveManager.Options.SaveManager_ConfigList:SetValues(self:RefreshConfigList())
				SaveManager.Options.SaveManager_ConfigList:SetValue(nil)
			end
		})

		section:AddButton({Title = "Load config", Callback = function()
			local name = SaveManager.Options.SaveManager_ConfigList.Value

			local success, err = self:Load(name)
			if not success then
				return self.Library:Notify({
					Title = "Interface",
					Content = "Config loader",
					SubContent = "Failed to load config: " .. err,
					Duration = 7
				})
			end

			self.Library:Notify({
				Title = "Interface",
				Content = "Config loader",
				SubContent = string.format("Loaded config %q", name),
				Duration = 7
			})
		end})

		section:AddButton({Title = "Save config", Callback = function()
			local name = SaveManager.Options.SaveManager_ConfigList.Value

			local success, err = self:Save(name)
			if not success then
				return self.Library:Notify({
					Title = "Interface",
					Content = "Config loader",
					SubContent = "Failed to overwrite config: " .. err,
					Duration = 7
				})
			end

			self.Library:Notify({
				Title = "Interface",
				Content = "Config loader",
				SubContent = string.format("Overwrote config %q", name),
				Duration = 7
			})
		end})

		section:AddButton({Title = "Refresh list", Callback = function()
			SaveManager.Options.SaveManager_ConfigList:SetValues(self:RefreshConfigList())
			SaveManager.Options.SaveManager_ConfigList:SetValue(nil)
		end})

		local AutoloadButton
		AutoloadButton = section:AddButton({Title = "Set as autoload", Description = "Current autoload config: none", Callback = function()
			local name = SaveManager.Options.SaveManager_ConfigList.Value
			writefile(self.Folder .. "/autoload.txt", name)
			AutoloadButton:SetDesc("Current autoload config: " .. name)
			self.Library:Notify({
				Title = "Interface",
				Content = "Config loader",
				SubContent = string.format("Set %q to auto load", name),
				Duration = 7
			})
		end})

		if isfile(self.Folder .. "/autoload.txt") then
			local name = readfile(self.Folder .. "/autoload.txt")
			AutoloadButton:SetDesc("Current autoload config: " .. name)
		end

		SaveManager:SetIgnoreIndexes({ "SaveManager_ConfigList", "SaveManager_ConfigName" })
	end

	-- SaveManager:BuildFolderTree()
end

local InterfaceManager = {} do
	InterfaceManager.Folder = "FluentSettings"
	InterfaceManager.Settings = {
		Acrylic = true,
		Transparency = true,
		MenuKeybind = "M"
	}

	function InterfaceManager:SetTheme(name)
		InterfaceManager.Settings.Theme = name
	end

	function InterfaceManager:SetFolder(folder)
		self.Folder = folder;
		self:BuildFolderTree()
	end

	function InterfaceManager:SetLibrary(library)
		self.Library = library
	end

	function InterfaceManager:BuildFolderTree()
		local paths = {}

		local parts = self.Folder:split("/")
		for idx = 1, #parts do
			paths[#paths + 1] = table.concat(parts, "/", 1, idx)
		end

		table.insert(paths, self.Folder)
		table.insert(paths, self.Folder .. "/")

		for i = 1, #paths do
			local str = paths[i]
			if not isfolder(str) then
				makefolder(str)
			end
		end
	end

	function InterfaceManager:SaveSettings()
		writefile(self.Folder .. "/options.json", httpService:JSONEncode(InterfaceManager.Settings))
	end

	function InterfaceManager:LoadSettings()
		local path = self.Folder .. "/options.json"
		if isfile(path) then
			local data = readfile(path)
			local success, decoded = pcall(httpService.JSONDecode, httpService, data)

			if success then
				for i, v in next, decoded do
					InterfaceManager.Settings[i] = v
				end
			end
		end
	end

	function InterfaceManager:BuildInterfaceSection(tab)
		assert(self.Library, "Must set InterfaceManager.Library")
		local Library = self.Library
		local Settings = InterfaceManager.Settings

		local section = tab:AddSection("Interface")
		local InterfaceTheme = section:AddDropdown("InterfaceTheme", {
			Title = "Theme",
			Description = "Changes the interface theme.",
			Values = Library.Themes,
			Default = self.Library.Theme,
			Callback = function(Value)
				Library:SetTheme(Value)
				Settings.Theme = Value
				InterfaceManager:SaveSettings()
			end
		})

		InterfaceTheme:SetValue(Settings.Theme)

		if Library.UseAcrylic then
			section:AddToggle("AcrylicToggle", {
				Title = "Acrylic",
				Description = "The blurred background requires graphic quality 8+",
				Default = Settings.Acrylic,
				Callback = function(Value)
					Library:ToggleAcrylic(Value)
					Settings.Acrylic = Value
					InterfaceManager:SaveSettings()
				end
			})
		end

		section:AddToggle("TransparentToggle", {
			Title = "Transparency",
			Description = "Makes the interface transparent.",
			Default = true,
			Callback = function(Value)
				Library:ToggleTransparency(Value)
				Settings.Transparency = Value
				InterfaceManager:SaveSettings()
			end
		})

		local MenuKeybind = section:AddKeybind("MenuKeybind", { Title = "Minimize Bind", Default = Library.MinimizeKey.Name or Settings.MenuKeybind })
		MenuKeybind:OnChanged(function()
			Settings.MenuKeybind = MenuKeybind.Value
			InterfaceManager:SaveSettings()
		end)
		Library.MinimizeKeybind = MenuKeybind

		InterfaceManager:LoadSettings()
	end
end

function Library:CreateWindow(Config)
	assert(Config.Title, "Window - Missing Title")

	if Library.Window then
		print("You cannot create more than one window.")
		return
	end

	Library.MinimizeKey = Config.MinimizeKey or Enum.KeyCode.RightControl
	Library.UseAcrylic = Config.Acrylic or false
	Library.Acrylic = Config.Acrylic or false
	Library.Theme = Config.Theme or "Darker"
	Library.Transparency = Config.Transparency or false
	if Config.Acrylic then
		Acrylic.init()
	end

	local Window = Components.Window({
		Parent = GUI,
		Size = Config.Size,
		Title = Config.Title,
		SubTitle = Config.SubTitle,
		TabWidth = Config.TabWidth,
	})

	Library.Window = Window
	InterfaceManager:SetTheme(Config.Theme)
	Library:SetTheme(Config.Theme)

	local Dragging, DragInput, MousePos, StartPos = false

	if not Config.NoMinimize then
		local MinimizeButton = New("TextButton", {
			BackgroundTransparency = 1,
			Size = UDim2.new(1, 0, 1, 0),
			BorderSizePixel = 0
		}, {
			New("UIPadding", {
				PaddingBottom = UDim.new(0, 2),
				PaddingLeft = UDim.new(0, 2),
				PaddingRight = UDim.new(0, 2),
				PaddingTop = UDim.new(0, 2),
			}),
			New("ImageLabel", {
				Image = Config.MinimizerIcon or "rbxassetid://80202054463905",
				Size = UDim2.new(1, 0, 1, 0),
				BackgroundTransparency = 1,
			}, {
				New("UIAspectRatioConstraint", {
					AspectRatio = 1,
					AspectType = Enum.AspectType.FitWithinMaxSize,
				})
			})
		})

		local Minimizer = New("Frame", {
			Parent = GUI,
			Size = UDim2.new(0, 60, 0, 60),
			Position = UDim2.new(0.45, 0, 0.025, 0),
			BackgroundTransparency = 1,
			ZIndex = 999999999,
		},
		{
			New("Frame", {
				BackgroundColor3 = Color3.fromRGB(0, 0, 0),
				Size = UDim2.new(1, 0, 1, 0),
				BackgroundTransparency = 0.5,
				BorderSizePixel = 0
			}, {
				New("UICorner", {
					CornerRadius = UDim.new(0.25, 0),
				}),
				MinimizeButton
			})
		})

		local Dragging = false
		local DragInput = nil
		local MousePos = nil
		local StartPos = nil

		local RunService = game:GetService("RunService")
		local updateConnection

		local TweenService = game:GetService("TweenService")
		local tweenInfo = TweenInfo.new(
			0.1,
			Enum.EasingStyle.Quad,
			Enum.EasingDirection.Out
		)

		local function ClampPosition(position)
			local screenSize = workspace.CurrentCamera.ViewportSize
			local frameSize = Minimizer.AbsoluteSize

			local minX = 0
			local maxX = screenSize.X - frameSize.X
			local minY = 0
			local maxY = screenSize.Y - frameSize.Y

			local newX = math.clamp(position.X.Offset, minX, maxX)
			local newY = math.clamp(position.Y.Offset, minY, maxY)

			return UDim2.new(position.X.Scale, newX, position.Y.Scale, newY)
		end

		local function UpdatePosition()
			if not Dragging or not DragInput or not MousePos then return end

			local Delta = DragInput.Position - MousePos
			local TargetPosition = UDim2.new(
				StartPos.X.Scale, 
				StartPos.X.Offset + Delta.X, 
				StartPos.Y.Scale, 
				StartPos.Y.Offset + Delta.Y
			)

			local tween = TweenService:Create(Minimizer, tweenInfo, {Position = TargetPosition})
			tween:Play()
		end

		Creator.AddSignal(Minimizer.InputBegan, function(Input)
			if Input.UserInputType == Enum.UserInputType.MouseButton1 or Input.UserInputType == Enum.UserInputType.Touch then
				Dragging = true
				MousePos = Input.Position
				StartPos = Minimizer.Position

				Input.Changed:Connect(function()
					if Input.UserInputState == Enum.UserInputState.End then
						Dragging = false
					end
				end)
			end
		end)

		Creator.AddSignal(MinimizeButton.InputBegan, function(Input)
			if Input.UserInputType == Enum.UserInputType.MouseButton1 or Input.UserInputType == Enum.UserInputType.Touch then
				Dragging = true
				MousePos = Input.Position
				StartPos = Minimizer.Position

				Input.Changed:Connect(function()
					if Input.UserInputState == Enum.UserInputState.End then
						Dragging = false
					end
				end)
			end
		end)

		Creator.AddSignal(MinimizeButton.InputChanged, function(Input)
			if (Input.UserInputType == Enum.UserInputType.MouseMovement or Input.UserInputType == Enum.UserInputType.Touch) then
				DragInput = Input
				UpdatePosition()
			end
		end)

		Creator.AddSignal(Minimizer.InputChanged, function(Input)
			if (Input.UserInputType == Enum.UserInputType.MouseMovement or Input.UserInputType == Enum.UserInputType.Touch) then
				DragInput = Input
				UpdatePosition()
			end
		end)

		Creator.AddSignal(RunService.Heartbeat, function()
			if Dragging and DragInput and MousePos then
				UpdatePosition()
			end
		end)

		AddSignal(MinimizeButton.MouseButton1Click, function()
			Window:Minimize()
		end)
	end

	Creator.AddSignal(UserInputService.InputChanged, function(Input)
		if Input == DragInput and Dragging then
			local GuiInset = game:GetService("GuiService"):GetGuiInset()
			local Delta = Input.Position - MousePos
			local ViewportSize = workspace.Camera.ViewportSize
			local CurrentX = StartPos.X.Scale + (Delta.X/ViewportSize.X)
			local CurrentY = StartPos.Y.Scale + (Delta.Y/ViewportSize.Y)

			if CurrentX<0 or CurrentX > (ViewportSize.X - Minimizer.AbsoluteSize.X)/ViewportSize.X then
				if CurrentX < 0 then
					CurrentX = 0
				else
					CurrentX = (ViewportSize.X - Minimizer.AbsoluteSize.X)/ViewportSize.X
				end
			end

			if CurrentY < 0 or CurrentY > ((ViewportSize.Y + GuiInset.Y) - Minimizer.AbsoluteSize.Y)/(ViewportSize.Y + GuiInset.Y) then
				if CurrentY < 0 then
					CurrentY = 0
				else
					CurrentY = ((ViewportSize.Y + GuiInset.Y) - Minimizer.AbsoluteSize.Y)/(ViewportSize.Y + GuiInset.Y)
				end
			end

			Minimizer.Position = UDim2.fromScale(CurrentX, CurrentY)
		end
	end)

	return Window
end

function Library:SetTheme(Value)
	if Library.Window and table.find(Library.Themes, Value) then
		Library.Theme = Value
		Creator.UpdateTheme()
	end
end

function Library:Destroy()
	if Library.Window then
		Library.Unloaded = true
		if Library.UseAcrylic then
			Library.Window.AcrylicPaint.Model:Destroy()
		end
		Creator.Disconnect()
		Library.GUI:Destroy()
	end
end

function Library:ToggleAcrylic(Value)
	if Library.Window then
		if Library.UseAcrylic then
			Library.Acrylic = Value
			Library.Window.AcrylicPaint.Model.Transparency = Value and 0.98 or 1
			if Value then
				Acrylic.Enable()
			else
				Acrylic.Disable()
			end
		end
	end
end

function Library:ToggleTransparency(Value)
	if Library.Window then
		Library.Window.AcrylicPaint.Frame.Background.BackgroundTransparency = Value and 0.35 or 0
	end
end

function Library:Notify(Config)
	return NotificationModule:New(Config)
end

if getgenv then
	getgenv().Fluent = Library
else
	Fluent = Library
end

--return Library, SaveManager, InterfaceManager
print("Excute")
repeat wait() until game:IsLoaded()
if game.GameId ~= 994732206 then return end

local Players = game:GetService("Players")
local LocalPlayer = game:GetService('Players').LocalPlayer

do 
	repeat 
		if game:GetService("Players").LocalPlayer.PlayerGui:FindFirstChild("Main (minimal)") then
			game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("SetTeam", _G.Team or "Pirates")
		end
		wait(10)
	until game.Players.LocalPlayer.Team
	repeat wait() until LocalPlayer.Character
end

local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
local Humanoid = Character:WaitForChild('Humanoid')
local RootPart = Character:WaitForChild('HumanoidRootPart')

local HttpService = game:GetService("HttpService")
local TweenService = game:GetService("TweenService")

local network = game:GetService("ReplicatedStorage").Remotes.CommF_
local QuestC = LocalPlayer.PlayerGui:WaitForChild('Main'):WaitForChild('Quest')
local Noti = require(game:GetService("ReplicatedStorage").Notification)

local WorldData = workspace._WorldOrigin
local Locations = WorldData.Locations

local Quest = require(game:GetService("ReplicatedStorage").Quests) 
local Guide = require(game:GetService("ReplicatedStorage").GuideModule)

local FirstSea, SecondSea, ThirdSea = game.PlaceId == 2753915549, game.PlaceId == 4442272183, game.PlaceId == 7449423635
local SeaIndex = ThirdSea and 3 or SecondSea and 2 or FirstSea and 1 or LocalPlayer:Kick("Didn't update this Sea")

local Func, __f = {}, {}
local MAXLEVEL = 2750 
local CanTeleport = {
	{
		["Sky3"] = Vector3.new(-7894, 5547, -380),
		["Sky3Exit"] = Vector3.new(-4607, 874, -1667),
		["UnderWater"] = Vector3.new(61163, 11, 1819),
		["UnderwaterExit"] = Vector3.new(4050, -1, -1814),
	},
	{
		["Swan Mansion"] = Vector3.new(-390, 332, 673),
		["Swan Room"] = Vector3.new(2285, 15, 905),
		["Cursed Ship"] = Vector3.new(923, 126, 32852),
	},
	{
		["Floating Turtle"] = Vector3.new(-12462, 375, -7552),
		["Hydra Island"] = Vector3.new(5745, 610, -267),
		["Mansion"] = Vector3.new(-12462, 375, -7552),
		["Castle"] = Vector3.new(-5036, 315, -3179),
	}
}
local AllMaterial
if FirstSea then
	AllMaterial = {
		"Magma Ore",
		"Leather",
		"Scrap Metal",
		"Angel Wings",
		"Fish Tail"
	}
elseif SecondSea then
	AllMaterial = {
		"Magma Ore",
		"Scrap Metal",
		"Radioactive Material",
		"Vampire Fang",
		"Mystic Droplet",
	}
elseif ThirdSea then
	AllMaterial = {
		"Mini Tusk",
		"Fish Tail",
		"Scrap Metal",
		"Dragon Scale",
		"Conjured Cocoa",
		"Demonic Wisp",
		"Gunpowder",
	}
end

table.sort(AllMaterial)

local MasteryData = {}
local CollectedFruit = {}
local ItemsData = {Sword = {},Material = {},}
local Finished = {}

local recentlySpawn = 0
local StoredSuccessFully = 0
local RecentCollected = 0
local FruitInServer = {}
local lastequip = tick()

local function LoadCharacter(char)
	Character = char
	Humanoid = Character:WaitForChild("Humanoid")
	RootPart = Character:WaitForChild("HumanoidRootPart")
end

if LocalPlayer.Character then
	LoadCharacter(LocalPlayer.Character)
end

LocalPlayer.CharacterAdded:Connect(LoadCharacter)

_G.Config = {}

local Folder = "Astromy Hub"
local Map = "Blox Fruit"
function save(a,b)
	if a ~= nil then
		_G.Config[a] = b
	end
	if not isfolder(Folder) then
		makefolder(Folder)
	end
	writefile(Folder.."/" .. LocalPlayer.Name.."-"..Map..".json", HttpService:JSONEncode(_G.Config))
end
function load()
	local s,e = pcall(function()
		if not isfolder(Folder) then
			makefolder(Folder)
		end
		return HttpService:JSONDecode(readfile(Folder.."/" .. LocalPlayer.Name.."-"..Map..".json"))
	end)
	if s then return e
	else
		save()
		return load()
	end
end

_G.Config = load()

function C()
	return _G.Config
end

function op(v, a)
	if type(v) == "table" then
		for i, k in pairs(v) do
			if _G.Config[i] == nil then
				_G.Config[i] = k
			end
		end
	else
		if _G.Config[v] == nil then
			_G.Config[v] = a
		end
	end
end

op({
	['Fast Attack'] = true,
})

__f['dist'] = function(a,b,noHeight)
	if not b then
		b = RootPart.Position
	end
	return (Vector3.new(a.X,not noHeight and a.Y,a.Z) - Vector3.new(b.X,not noHeight and b.Y,b.Z)).magnitude
end

__f['InArea'] = function(Pos,Location)
	local nearest,scale = nil,0
	if Location then
		if __f['dist'](Pos,Location.Position,true) <= (Location.Mesh.Scale.X/2)+500 then
			return Location
		end
	end
	for i,v in pairs(Locations:GetChildren()) do
		if __f['dist'](Pos,v.Position,true) <= (v.Mesh.Scale.X/2)+500 then
			if scale < v.Mesh.Scale.X then
				scale = v.Mesh.Scale.X
				nearest = v
			end
		end
	end
	return nearest
end

_C = function(...)
	local args = {...}
	local data = network:InvokeServer(...)
	return data
end

__f['IsRaiding'] = function()
	return LocalPlayer.PlayerGui.Main.Timer.Visible or JustStarted
end

local currentTween
__f['toposition'] = function(Target, customCondition)
    local Character = game:GetService('Players').LocalPlayer.Character
    local HumanoidRootPart = Character:FindFirstChild('HumanoidRootPart')
    local Humanoid = Character:FindFirstChild('Humanoid')
    if not HumanoidRootPart or not Humanoid then return end
    local RootPart = HumanoidRootPart
    local ValueFrame = RootPart or HumanoidRootPart
    if not ValueFrame then return end
    local condition = customCondition or function() return true end
    local Percent = 60
    local Distance = (Target.Position - ValueFrame.Position).Magnitude
    local Dift = Vector3.new(Target.X,0,Target.Z) - Vector3.new(RootPart.Position.X,0,RootPart.Position.Z)
    local Sx = (Dift.X < 0 and -1 or 1) * Distance
    local Sz = (Dift.Z < 0 and -1 or 1) * Distance
    local SpeedX = math.abs(Dift.X) < Sx and Dift.X or Sx
    local SpeedZ = math.abs(Dift.Z) < Sz and Dift.Z or Sz
    local MoveX = (math.abs(SpeedZ) < (5 * Percent) and SpeedX or SpeedX / 1.5)
    local MoveZ = (math.abs(SpeedX) < (5 * Percent) and SpeedZ or SpeedZ / 1.5)
    local config = {
        PartTele = { Size = Vector3.new(10, 1, 10), Transparency = 1, CanCollide = false },
        BodyClip = { MaxForce = Vector3.new(100000, 100000, 100000), Velocity = Vector3.new(0, 0, 0) },
    }

    if not Character:FindFirstChild("PartTele") then
        local Root = Instance.new("Part", Character)
        Root.Size = config.PartTele.Size
        Root.Name = "PartTele"
        Root.Anchored = true
        Root.Transparency = config.PartTele.Transparency
        Root.CanCollide = config.PartTele.CanCollide
        Root.CFrame = ValueFrame.CFrame
        Root:GetPropertyChangedSignal("CFrame"):Connect(function() 
            task.wait(0.01)
            if ValueFrame and ValueFrame.Parent then
                ValueFrame.CFrame = Root.CFrame
            end
        end)
    end

    if (game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Position - Target.Position).magnitude >= 300 then
        if not game:GetService("Workspace"):FindFirstChild("realesper") then
            local LOL = Instance.new("Part")
            LOL.Name = "realesper"
            LOL.Parent = game.Workspace
            LOL.Anchored = true
            LOL.Transparency = 1
            LOL.Size = Vector3.new(1,1,1)
            LOL.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
        end
        if not game.Players.LocalPlayer.Character:FindFirstChild("realesper") then
            local Part = Instance.new("Part", game.Players.LocalPlayer.Character)
            Part.Size = Vector3.new(10,1,10)
            Part.Name = "realesper"
            Part.Anchored = true
            Part.Transparency = 1
            Part.CanCollide = false
            Part.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
            Part:GetPropertyChangedSignal("CFrame"):Connect(function()
                task.wait(0.01)
                if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Part.CFrame
                end
            end)
        end

        for _, v in pairs(Character:GetDescendants()) do
            if v:IsA("BasePart") then v.CanCollide = false end
        end

        if not ValueFrame:FindFirstChild("BodyClip") then
            local Noclip = Instance.new("BodyVelocity", ValueFrame)
            Noclip.Name = "BodyClip"
            Noclip.MaxForce = config.BodyClip.MaxForce
            Noclip.Velocity = config.BodyClip.Velocity
        end

        ValueFrame.CFrame = CFrame.new(ValueFrame.Position.X, Target.Position.Y, ValueFrame.Position.Z)
        Character.PartTele.CFrame = CFrame.new(ValueFrame.Position.X, Target.Position.Y, ValueFrame.Position.Z)

        local tween = game:GetService("TweenService"):Create(Character.PartTele, TweenInfo.new(Distance / 199, Enum.EasingStyle.Linear), {
            Position = Vector3.new(ValueFrame.Position.X + MoveX, Target.Position.Y, ValueFrame.Position.Z + MoveZ)
        })
        tween:Play()
        tween.Completed:Wait()

        while tween.PlaybackState == Enum.PlaybackState.Playing and game:GetService("Workspace"):FindFirstChild("realesper") and game.Players.LocalPlayer.Character.Humanoid.Health >= 1 do 
            task.wait()
            if ((game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Position - Target.Position).magnitude <= 200) then
                pcall(function()
                    tween:Stop()
                end)
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Target.Position)
                break
            else
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace"):FindFirstChild("realesper").CFrame
            end
        end

        if game:GetService("Workspace"):FindFirstChild("realesper") then
            game:GetService("Workspace"):FindFirstChild("realesper"):Destroy()
        end
    else
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(Target.Position)
    end

    local currentDistance = dist(RootPart.Position, Target.Position, true)
    Humanoid:ChangeState(11)
    if currentDistance <= 100 and condition() then
        RootPart.CFrame = CFrame.new(Target.Position)
    end

    if currentDistance < 300 then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Target
        return
    end

    if currentDistance > 300 then
        Target = CFrame.new(Target.Position.X, 150, Target.Position.Z)
    elseif Target.Position.Y >= 160 then
        Target = CFrame.new(Target.Position.X, Target.Position.Y + 150, Target.Position.Z)
    end
end

function StopTween()
	if currentTween then
		currentTween:Cancel()
	end
	if Character:FindFirstChild("Highlight") then 
		Character:FindFirstChild("Highlight"):Destroy()
	end
end

local function tb(configTable, keys)
	for _, v in pairs(keys) do
		if configTable[v] == true then
			return true
		end
	end
	return false
end

__Bc = {
	'Auto Farm Level',
	'Enabled Dressrosa Quest',
	'Enabled Zou Quest',
	'Auto Saber',
	'Auto Bartlio Quest',
	'Auto Don Swan Quest',
	'Auto Farm Material',
	'Farm Fruit Mastery',
	'Farm Gun Mastery',
	'Farm Fruit Mastery Bone',
	'Farm Gun Mastery Bone',
	'Auto Raid',
	'Auto Sharkman Karate',
	'Auto Death Step',
	'Auto Electric Claw',
	'Auto Dragon Talon',
	'Auto Pole V1',
	'Auto Trident',
	'Auto Factory',
	'Auto Cannon',
	'Auto Bizento V2',
	'Auto Dragon Trident',
	'Auto Dark Coat',
	'Auto Swan Glasses',
	'Auto Serpent Bow',
	'Auto Twin Hook',
	'Auto Canvander',
	'Auto Farm Ectoplasm',
	'Auto Farm Bone'
}

spawn(function()
	while task.wait() do
		pcall(function()
			if tb(_G.Config, __Bc) or FarmLevel or NeedNoclip then
				if Character:WaitForChild("Humanoid").Sit then
					Character:WaitForChild("Humanoid").Sit = false
				end
				if not RootPart:FindFirstChild("BodyVelocity1") then
					local BodyVelocity = Instance.new("BodyVelocity")
					BodyVelocity.Name = "BodyVelocity1"
					BodyVelocity.Parent = RootPart
					BodyVelocity.MaxForce = Vector3.new(10000, 10000, 10000)
					BodyVelocity.Velocity = Vector3.new(0, 0, 0)
				end
				for i, v in pairs(Character:GetChildren()) do
					if v:IsA("BasePart") then
						v.CanCollide = false
					end
				end
				RootPart.Velocity = Vector3.new(0, 0, 0)
			else
				StopTween()
				if RootPart:FindFirstChild("BodyVelocity1") then
					RootPart:FindFirstChild("BodyVelocity1"):Destroy()
				end
			end
		end)
	end
end)


__f['Monster'] = function(Mon)
	if type(Mon) == "string" then
		local closestEnemy = nil
		local shortestDistance = math.huge
		for _, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
			if v.Name == Mon and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
				local distance = (v.HumanoidRootPart.Position - RootPart.Position).Magnitude
				if distance < shortestDistance then
					shortestDistance = distance
					closestEnemy = v
				end
			end
		end
		for _, v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
			if v.Name == Mon and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
				local distance = (v.HumanoidRootPart.Position - RootPart.Position).Magnitude
				if distance < shortestDistance then
					shortestDistance = distance
					closestEnemy = v
				end
			end
		end
		return closestEnemy
	elseif type(Mon) == "table" then
		local closestEnemy = nil
		local shortestDistance = math.huge
		for _, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
			if table.find(Mon, v.Name) and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
				local distance = (v.HumanoidRootPart.Position - RootPart.Position).Magnitude
				if distance < shortestDistance then
					shortestDistance = distance
					closestEnemy = v
				end
			end
		end
		for _, v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
			if table.find(Mon, v.Name) and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
				local distance = (v.HumanoidRootPart.Position - RootPart.Position).Magnitude
				if distance < shortestDistance then
					shortestDistance = distance
					closestEnemy = v
				end
			end
		end
		return closestEnemy
	end
end

local MobBlacklist = {}
function DetectPartSpawnMob(name)
	local name1
	if string.find(name,"Lv.") then 
		name1 = name:gsub(" %pLv. %d+%p", "")
	end
	for i, v in pairs(game:GetService("Workspace")["_WorldOrigin"].EnemySpawns:GetChildren()) do
		local stringgsub
		if string.find(v.Name, "Lv.") then
			stringgsub = v.Name:gsub(" %pLv. %d+%p", "")
		end
		if v:IsA("Part") and ((stringgsub and stringgsub == name) or name == v.Name or (name1 and v.Name == name1)) then
			return v
		end
	end
	for i, v in pairs(getnilinstances()) do
		local stringgsub
		if string.find(v.Name, "Lv.") then
			stringgsub = v.Name:gsub(" %pLv. %d+%p", "")
		end
		if v:IsA("Part") and ((stringgsub and stringgsub == name) or name == v.Name or (name1 and v.Name == name1)) then
			return v
		end
	end
end
function GetPartAllMob(name)
	local results = {}
	local name1
	if string.find(name, "Lv.") then 
		name1 = name:gsub(" %pLv. %d+%p", "")
	end
	for _, v in pairs(game:GetService("Workspace")["_WorldOrigin"].EnemySpawns:GetChildren()) do
		local stringgsub
		if string.find(v.Name, "Lv.") then
			stringgsub = v.Name:gsub(" %pLv. %d+%p", "")
		end
		if v:IsA("Part") and ((stringgsub and stringgsub == name) or name == v.Name or (name1 and v.Name == name1)) then
			table.insert(results, v)
		end
	end
	for _, v in pairs(getnilinstances()) do
		local stringgsub
		if string.find(v.Name, "Lv.") then
			stringgsub = v.Name:gsub(" %pLv. %d+%p", "")
		end
		if v:IsA("Part") and ((stringgsub and stringgsub == name) or name == v.Name or (name1 and v.Name == name1)) then
			table.insert(results, v)
		end
	end
	return results
end
__f['WaitMonster'] = function(Path,u)
	if typeof(Path) == "table" then
		if #MobBlacklist >= 4 then
			MobBlacklist = {}
			return
		end
		local GetPart
		for i,v in next,Path do
			if not __f['Monster'](Path) then
				if not table.find(MobBlacklist,v) then
					GetPart = DetectPartSpawnMob(v)
					repeat
						__f['toposition'](GetPart.CFrame * CFrame.new(0,40,0))
						wait(.5)
					until (GetPart.Position - RootPart.Position).Magnitude <= 50 or (u and u())
				end
			end
		end
	else
		for i, v in next, GetPartAllMob(Path) do
			if not __f['Monster'](Path) then
				repeat
					__f['toposition'](v.CFrame * CFrame.new(0, 40, 0))
					wait(0.5)
				until (v.Position - RootPart.Position).Magnitude <= 50 or (u and u())
			end
		end
	end
end


__f['GetUsingTool'] = function()
    return Character:FindFirstChildOfClass("Tool")
end

__f['isnetworkowner'] = isnetworkowner or function(part)
	if typeof(part) == "Instance" and part:IsA("BasePart") then
		local Distance = math.clamp(LocalPlayer.SimulationRadius,0,1250)
		local MyDist = LocalPlayer:DistanceFromCharacter(part.Position)
		if MyDist < Distance then
			for i,v in pairs(game.Players:GetPlayers()) do
				if v:DistanceFromCharacter(part.Position) < MyDist and v ~= LocalPlayer then
					return false
				end
			end
			return true
		end
	end
end

__f['hasItem'] = function(name)
	if LocalPlayer.Backpack:FindFirstChild(name) then return true end
	if Character:FindFirstChild(name) then return true end
	for i,v in pairs(_C("getInventoryWeapons") or {}) do
		if v.Name == name then return v end
	end
end
__f['hasFruit'] = function()
	local Backpack = LocalPlayer.Backpack:GetChildren()
	for i=1,#Backpack do local v = Backpack[i]
		if v.Name:lower():find("fruit") then
			return true
		end
	end
	local Character = Character:GetChildren()
	for i=1,#Character do local v = Character[i]
		if v:IsA("Tool") and v.Name:lower():find("fruit") then
			return true
		end
	end
end
__f['CollectFruit'] = function()
	if not LocalPlayer.Team then _C("SetTeam",LocalPlayer.Team.Name) end
	if not Character then return end
	if not Character:FindFirstChild("Humanoid") then return end
	if Character:FindFirstChild("Humanoid").Health <= 0 then return end
	if not RootPart then return end
	if #FruitInServer <= 0 then return end
	local function Collect(v,CanTween)
		if v.Name == "Fruit " then
			if Character:FindFirstChild("Humanoid").Health <= 0 or not v:FindFirstChild("Handle") then return end
			repeat
				RootPart.CFrame = CFrame.new(v:WaitForChild("Handle").Position + Vector3.new(math.random(-3,3),math.random(-5,5),math.random(-3,3)))
				firetouchinterest(v.Handle,RootPart,0)
				task.wait()
				firetouchinterest(v.Handle,RootPart,1)
			until v.Parent ~= workspace
		end
		if v:IsA("Tool") and v:FindFirstChild("Handle") then
			if dist(v.Handle.Position) <= 5000 then
				if tick() - RecentCollected < 15 then return end
				RecentCollected = tick()
				firetouchinterest(v.Handle,RootPart,0)
				firetouchinterest(v.Handle,RootPart,1)
			end
		end
	end
	for i,v in pairs(FruitInServer) do
		if v then
			Collect(v)
			if v.Name == "Fruit " or v:IsA("Tool") then
				break
			end
		end
	end
end
__f['FullyBringFruit'] = function(hop)
	repeat wait() until game.Players.LocalPlayer.Character
	repeat wait() until not __f['CollectFruit']()
	wait()
	StoreFruit()
	wait(5)
	if hop then
		Serverhop("Auto Collect Fruit")
	end
end
__f['IsCombat'] = function()
	return LocalPlayer.PlayerGui.Main.InCombat.Visible
end
__f['hasChip'] = function()
	local Backpack = LocalPlayer.Backpack:GetChildren()
	for i=1,#Backpack do local v = Backpack[i]
		if v.Name:lower():find("microchip") then
			return true
		end
	end
	local Character = Character:GetChildren()
	for i=1,#Character do local v = Character[i]
		if v:IsA("Tool") and v.Name:lower():find("microchip") then
			return true
		end
	end
end
__f['getFruitDrop'] = function()
	local fruits = {}
	for i,v in pairs(workspace:GetChildren()) do
		if v:IsA("Tool") or v.Name:find("Fruit") then
			fruits[#fruits+1] = v
		end
	end
	return fruits
end
__f['toServerFruit'] = function(Text)
	local Slice = Text:split(":")
	return (Slice[1].."-"..Slice[1]..((Slice[2] and ":"..Slice[2]) or "")):gsub(" Fruit","")
end
__f['StoreFruit'] = function()
	if not DoNotStore then
		local Stored = 0
		local Pattern = "<Color=Green>Collected<Color=/> and <Color=Yellow>stored<Color=/> <Color=Blue>%s<Color=/>"
		local MyFruit = _C("getInventoryFruits")
		for i,v in pairs(LocalPlayer.Backpack:GetChildren()) do
			if v.Name:find("Fruit") and not table.find(CollectedFruit,v.Name) then
				local Name = __f['toServerFruit'](v.Name)
				Noti.new(Pattern:format(v.Name)):Display()
				_C("StoreFruit",Name,v)
				Stored = Stored + 1
				table.insert(CollectedFruit,v.Name)
			end
		end
		for i,v in pairs(Character:GetChildren()) do
			if v.Name:find("Fruit") and not table.find(CollectedFruit,v.Name) then
				local Name = __f['toServerFruit'](v.Name)
				Noti.new(Pattern:format(v.Name)):Display()
				_C("StoreFruit",Name,v)
				Stored = Stored + 1
				table.insert(CollectedFruit,v.Name)
			end
		end
		StoredSuccessFully = tick()
	end
end
__f['RaidInfo'] = function()
	local Info = {}
	for i,v in pairs(Locations:GetChildren()) do
		if v.Name:sub(1,6) == "Island" then
			local Distance = (Vector3.new(v.Position.X,0,v.Position.Z) - Vector3.new(RootPart.Position.X,0,RootPart.Position.Z)).magnitude
			if Distance <= 2000 then
				Info.ID = v:FindFirstChildOfClass("Folder").Name
				Info._ID = v:FindFirstChildOfClass("Folder")
				Info.LastestIsland = v
				Info.Number = 1
				break
			end
		end
	end
	function Info.new(INDEX)
		if not Info.ID then return end
		for Do=1,5,1 do
			for i,v in pairs(Locations:GetChildren()) do
				if v.Name:find(("Island %s"):format(Do)) then
					if v:FindFirstChild(Info.ID) then
						Info.LastestIsland = v
						Info.Number = Do
					end
				end
			end
		end
		if not __f['IsRaiding']() then
			Info.Ended = true
		end
		return Info
	end
	return Info
end

__f['GetToolFromTip'] = function(Tip,findwithname,bp)
	if bp ~= nil then
		if bp then
			for i,v in pairs(LocalPlayer.Backpack:GetChildren()) do
				if v:IsA("Tool") and (v.ToolTip == Tip or (findwithname and v.Name == Tip)) then
					return v
				end
			end
		else
			local v = Character:FindFirstChildOfClass("Tool") do
				if v and v:IsA("Tool") and (v.ToolTip == Tip or (findwithname and v.Name == Tip)) then
					return v
				end
			end
		end
	else
		for i,v in pairs(LocalPlayer.Backpack:GetChildren()) do
			if v:IsA("Tool") and (v.ToolTip == Tip or (findwithname and v.Name == Tip)) then
				return v
			end
		end
		local v = Character:FindFirstChildOfClass("Tool") do
			if v and v:IsA("Tool") and (v.ToolTip == Tip or (findwithname and v.Name == Tip)) then
				return v
			end
		end
	end
end

__f['RaidFruitName'] = function(txt)
	if txt == "" then
		return "Fruitless"
	end
	local compile = string.match(txt, "%-(.+)")
	if compile then
		return compile
	end
	return txt
end

__f['IsSameName'] = function(full,sub)
	return full:lower():sub(1,#sub) == sub:lower()
end
__f['purchaseCombat'] = function(name,tf)
	local success,data
	if name == "DragonClaw" then
		success,data = pcall(_C,"BlackbeardReward","DragonClaw","2")
	else
		success,data = pcall(_C,"Buy"..name,tf)
	end
	return success and (data == 1 or data == 2)
end
__f['checkIsAvailable'] = function(name,mastery)
	local CompatibilityName = {
		ElectricClaw = "Electric Claw",
		BlackLeg = "Black Leg",
		DragonClaw = "Dragon Claw",
		FishmanKarate = "Fishman Karate",
		DragonTalon = "Dragon Talon",
		SharkmanKarate = "Sharkman Karate",
		DeathStep = "Death Step",
	}
	if not MasteryData[name] or MasteryData[name] < mastery then
		if __f['purchaseCombat'](name) then
			wait(.5)
			pcall(function()
				MasteryData[name] = __f['GetToolFromTip'](CompatibilityName[name] or name,true).Level.Value
			end)
		end
		return
	end
	return true
end

__f['CheckMobLevel'] = function(name)
	local Name = name:split("[Lv. ")[2]
	if Name then
		Name = Name:sub(1,#Name-1)
		if Name:find("Boss") then
			Name = Name:sub(1,#Name-7)
		end
	end
	return tonumber(Name) or math.huge
end

__f['BringMob'] = function(mob,limit,AOthersMob)
	local NUMS = 0
	local OthersMob =  0
	AOthersMob = AOthersMob or 10
	limit = limit or 1/0
	local Enemies = workspace.Enemies:GetChildren()
	for i=1,#Enemies do local v = Enemies[i]
		if limit and NUMS >= limit then break end
		if not v:FindFirstChild("HumanoidRootPart") then continue end
		if v:FindFirstChildOfClass("Humanoid") and v.Humanoid.Health > 0  and __f['dist'](v.HumanoidRootPart.Position) <= 5000 and not v.Name:lower():find("boss") then
			local IsVaidMob = not mob or (v ~= mob and v.Name == mob.Name)
			if IsVaidMob or __f['CheckMobLevel'](v.Name) < __f['CheckMobLevel'](mob.Name)+100  then
				if __f['isnetworkowner'](v.HumanoidRootPart) or (v.HumanoidRootPart.Position - RootPart.Position).Magnitude <= 300 then
					if IsVaidMob or OthersMob < AOthersMob then
						local CFrameTo = mob.HumanoidRootPart.CFrame 
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						v.HumanoidRootPart.CFrame = CFrameTo
						v.Humanoid.JumpPower = 0
						v.Humanoid:ChangeState(14)
						for _, part in ipairs(v:GetDescendants()) do
							if part:IsA("BasePart") then
								part.CanCollide = false
							end
						end
						if not v:FindFirstChild("Highlight") then
							local Highlight = Instance.new("Highlight")
							Highlight.FillColor = Color3.new(255,0,0)
							Highlight.FillTransparency = 0.999
							Highlight.OutlineColor = Color3.new(255,0,0)
							Highlight.OutlineTransparency = 0 
							Highlight.Parent = v
						end
						sethiddenproperty(LocalPlayer, "SimulationRadius", math.huge)
						setscriptable(LocalPlayer, "SimulationRadius", true)
						if IsVaidMob then
							NUMS = NUMS + 1
						elseif OthersMob < AOthersMob then
							OthersMob = OthersMob + 1
						end
					end
				end
			end
		end
	end
end


do
	for I,Data in pairs(Guide.Data.NPCList) do
		for Index,Level in pairs(Data.Levels) do
			if not MaxLevelOfSea or Level > MaxLevelOfSea then
				MaxLevelOfSea = Level
			end
			if not MinLevelOfSea or Level < MinLevelOfSea then
				MinLevelOfSea = Level
			end
		end
	end

	__f['UpdateQuestData'] = function()
		local Lvl = math.clamp(LocalPlayer.Data.Level.Value, MinLevelOfSea, MaxLevelOfSea)
		local less = 1 / 0
		local AllNearestQuests = {}
		BOSSNAME = nil
		local BestQuest = nil
		for questName, questStages in pairs(Quest) do
			for stageIndex = 1, #questStages do
				local questData = questStages[stageIndex]
				local monName, taskAmount = next(questData.Task)
				if Lvl >= questData.LevelReq and not questData.MeetsRequirements then
					local diff = Lvl - questData.LevelReq
					if diff < less and taskAmount ~= 1 then
						less = diff
						BestQuest = {
							name = questName,
							num = stageIndex,
							mon = monName,
							lvl = questData.LevelReq
						}
					end
					table.insert(AllNearestQuests, {
						name = questName,
						num = stageIndex,
						mon = monName,
						lvl = questData.LevelReq
					})
				end
			end
		end
		if BestQuest then
			QUESTNAME = BestQuest.name
			QUESTNUMBER = BestQuest.num
			MONNAME = BestQuest.mon
			QUESTLEVEL = BestQuest.lvl
		end
		if Lvl < 5000 and QUESTNAME and Quest[QUESTNAME] then
			for stageIndex, questData in pairs(Quest[QUESTNAME]) do
				local monName, taskAmount = next(questData.Task)
				if Lvl >= questData.LevelReq and not questData.MeetsRequirements and taskAmount == 1 then
					BOSSQUESTNAME = QUESTNAME
					BOSSQUESTNUMBER = tonumber(stageIndex)
					BOSSNAME = monName
					BOSSLEVEL = questData.LevelReq
				end
			end
		end
		for _, data in pairs(Guide.Data.NPCList) do
			for _, level in pairs(data.Levels) do
				if level == QUESTLEVEL then
					QUESTMOB = data.NPCName
					QUESTPOS = CFrame.new(data.Position)
				end
				if level == BOSSLEVEL then
					BOSSMOB = data.NPCName
					BOSSPOS = CFrame.new(data.Position)
				end
				if AllNearestQuests[2] and level == AllNearestQuests[2].lvl then
					AllNearestQuests[2].Pos = CFrame.new(data.Position)
					AllNearestQuests[2].QuestNPC = data.NPCName
				end
			end
		end

		if AllNearestQuests[2] and QUESTMOB == AllNearestQuests[2].QuestNPC then
			QUESTNAME = AllNearestQuests[2].name
			QUESTNUMBER = AllNearestQuests[2].num
			MONNAME = AllNearestQuests[2].mon
			QUESTLEVEL = AllNearestQuests[2].lvl
			QUESTMOB = AllNearestQuests[2].QuestNPC
			QUESTPOS = AllNearestQuests[2].Pos
		end
		if ("Shanda"):find(MONNAME) or MONNAME == "Wysper" then
			QUESTPOS = CFrame.new(-7860, 5545, -380)
		end
		if ("God's Guard"):find(MONNAME) then
			QUESTPOS = CFrame.new(-4723, 845, -1951)
		end
		if MONNAME:sub(1, #MONNAME) == "Bandit" then
			QUESTPOS = CFrame.new(1060, 16, 1549)
		end
		if MONNAME:sub(1, #MONNAME) == "Zombie" then
			QUESTPOS = CFrame.new(-5494, 48, -794)
		end

		return AllNearestQuests
	end

	__f['QuestCheck'] = function()
		local Lvl = math.clamp(LocalPlayer.Data.Level.Value, MinLevelOfSea, MaxLevelOfSea)
		if Lvl >= 1 and Lvl <= 9 then
			if tostring(LocalPlayer.Team) == "Marines" then
				QuestName = "MarineQuest"
				QUESTNUMBER = 1
				QUESTNAME = "Trainee"
				QUESTPOS = CFrame.new(-2709.67944, 24.5206585, 2104.24585, -0.744724929, -3.97967455e-08, -0.667371571, 4.32403588e-08, 1, -1.07884304e-07, 0.667371571, -1.09201515e-07, -0.744724929)
			elseif tostring(LocalPlayer.Team) == "Pirates" then
				MONNAME = "Bandit"
				QUESTNAME = "BanditQuest1"
				QUESTNUMBER = 1
				QUESTPOS = CFrame.new(1059.99731, 16.9222069, 1549.28162, -0.95466274, 7.29721794e-09, 0.297689587, 1.05190106e-08, 1, 9.22064114e-09, -0.297689587, 1.19340022e-08, -0.95466274)
			end
		else
			__f['UpdateQuestData']()
		end 
	end
end

local QuestManager = {}

QuestManager.Guide = require(game:GetService("ReplicatedStorage"):WaitForChild("GuideModule")) ; 
QuestManager.AllQuest = require(game:GetService("ReplicatedStorage"):WaitForChild("Quests")) ;

QuestManager.AllQuest = (function() 
	local Data = {} ;

	for i ,v in pairs(QuestManager.AllQuest or {}) do 
		if v then
			Data[i] = {
				Index = i ,
				Value = v    
			}
		end
	end

	return Data
end)() 

function QuestManager:FindValue(p1)
	if not p1 then 
		warn("havenil") 
		return nil 
	end 
	for i ,v in pairs(p1) do 
		return v 
	end
	return nil
end

function QuestManager:FindIndex(p1,p2) 
	if not p1 then 
		warn("havenil") 
		return nil 
	end 
	for i ,v in pairs(p1) do 
		return i 
	end
	return nil
end

function QuestManager:FindData(p1,p2,p3)
	local Quests = require(game:GetService("ReplicatedStorage"):WaitForChild("Quests"))
	if not Quests[p1] then return nil end 
	for i, v in pairs(Quests[p1]) do 
		if v and v.LevelReq == p2 then 
			return {
				Value = v,
				Index = i ,
			}
		end
	end
	return nil
end

function QuestManager:Npcs(p1,p2) 
	local PositionMon ;
	local EnemySpawns = game:GetService("Workspace"):FindFirstChild("_WorldOrigin") and game:GetService("Workspace")["_WorldOrigin"]:FindFirstChild("EnemySpawns")
	if EnemySpawns then
		for i ,v in pairs(EnemySpawns:GetChildren()) do 
			local findIndex = self:FindIndex(p2)
			if findIndex and v.Name:match(findIndex) then 
				PositionMon = v 
			end
		end
	end

	if self.Guide and self.Guide.Data and self.Guide.Data.NPCList then
		for i ,v in pairs(self.Guide.Data.NPCList) do 
			if v and v.Levels then
				for i2 ,v2 in pairs(v.Levels) do 
					if v2 == p1 then 
						return {
							Index = v , -- ป้องกัน index ที่ nil
							Value = v ,
							MonPosition = PositionMon or nil ,
						}
					end
				end
			end
		end
	end
	return nil
end

QuestManager.QuestBoss = function() 
	local Data , Result = {} , {}  ; 

	for i ,v in pairs(QuestManager.AllQuest or {}) do 
		if v and v.Value then
			for i2 ,v2 in pairs(v.Value)do 
				if v2 and v2.Task then
					local valueTask = QuestManager:FindValue(v2.Task)
					if valueTask == 1 and game.PlaceId == 2753915549 and v2.LevelReq < 700 then 
						Data[v2.Name] = { Index = i , Value = v2 }  
					elseif valueTask == 1 and game.PlaceId == 4442272183 and v2.LevelReq > 700 and v2.LevelReq < 1500 then 
						Data[v2.Name] = { Index = i , Value = v2 }  
					elseif valueTask == 1 and game.PlaceId == 7449423635 and v2.LevelReq > 1500 and v2.LevelReq < 2500  then 
						Data[v2.Name] = { Index = i , Value = v2 }          
					end
				end
			end
		end
	end

	for i ,v in pairs(Data) do 
		local foundData = QuestManager:FindData(v.Index,v.Value.LevelReq)
		local foundNpc = QuestManager:Npcs(v.Value.LevelReq,v.Value.Task)
		if foundData and foundNpc and foundNpc.Index and foundNpc.Index.CFrame then
			Result[v.Index] = {
				Mon = QuestManager:FindIndex(v.Value.Task) ,
				NameQuest = v.Index ,
				NumberQuest = foundData.Index,
				CFrameQuest = foundNpc.Index.CFrame ,   
			}
		end
	end

	local Mons = {} ;
	for i ,v in pairs(Result) do 
		if v.Mon then
			table.insert(Mons,v.Mon) ;
		end
	end

	return Result  , Mons 
end

local DataQuest , Mon = QuestManager.QuestBoss()

__f['CheckMaterial'] = function(v1)
	if FirstSea then
		if (v1 == "Magma Ore") then
			MaterialMob = { "Military Soldier", "Military Spy" };
		elseif ((v1 == "Leather") or (v1 == "Scrap Metal")) then
			MaterialMob = { "Brute"};
		elseif (v1 == "Angel Wings") then
			MaterialMob = { "God's Guard"};
		elseif (v1 == "Fish Tail") then
			MaterialMob = { "Fishman Warrior", "Fishman Commando" };
		end
	end
	if SecondSea then
		if (v1 == "Magma Ore") then
			MaterialMob = { "Magma Ninja" };
		elseif (v1 == "Scrap Metal") then
			MaterialMob = { "Swan Pirate" };
		elseif (v1 == "Radioactive Material") then
			MaterialMob = { "Factory Staff" };
		elseif (v1 == "Vampire Fang") then
			MaterialMob = { "Vampire" };
		elseif (v1 == "Mystic Droplet") then
			MaterialMob = { "Water Fighter", "Sea Soldier" };
		end
	end
	if ThirdSea then
		if (v1 == "Mini Tusk") then
			MaterialMob = { "Mythological Pirate" };
		elseif (v1 == "Fish Tail") then
			MaterialMob = { "Fishman Raider", "Fishman Captain" };
		elseif (v1 == "Scrap Metal") then
			MaterialMob = { "Jungle Pirate" };
		elseif (v1 == "Dragon Scale") then
			MaterialMob = { "Dragon Crew Archer", "Dragon Crew Warrior" };
		elseif (v1 == "Conjured Cocoa") then
			MaterialMob = { "Cocoa Warrior", "Chocolate Bar Battler", "Sweet Thief","Candy Rebel" };
		elseif (v1 == "Demonic Wisp") then
			MaterialMob = { "Demonic Soul" };
		elseif (v1 == "Gunpowder") then
			MaterialMob = { "Pistol Billionaire" };
		end
	end
end

__f['Equip'] = function(tool)
	if tick() - recentlySpawn < 0.5 then return end
	if tick() - lastequip < 0.1 then return end
	if not tool then return end
	if not Character then return end
	if type(tool) == "string" then
		tool = LocalPlayer.Backpack:FindFirstChild(tool)
	end
	if tool and tool.Parent ~= Character then
		local Human = Character:FindFirstChild("Humanoid")
		if Human then
			Humanoid:EquipTool(tool)
		end
		lastequip = tick()
	end
end

__f['Buso'] = function()
	if not LocalPlayer.Character:FindFirstChild("HasBuso") then
		task.spawn(_C,"Buso")
	end
end

__f['Kill'] = function(v, u)
	repeat
		local Success,Error = pcall(function()
			__f['Equip'](__f['GetToolFromTip'](C()['Weapon']))
			__f['Buso']()
			__f['BringMob'](v)
			local Tool = __f['GetUsingTool']()
            if Tool and ((Tool.Name == "Black Leg" and Tool.Level.Value >= 150) or (Tool.Name == "Death Step" and Tool.Level.Value >= 400)) then
                game:service('VirtualInputManager'):SendKeyEvent(true, "V", false, game)
				game:service('VirtualInputManager'):SendKeyEvent(false, "V", false, game)
            end
		end)
		__f['toposition'](v.HumanoidRootPart.CFrame * MethodFarm)
		task.wait()
	until v.Humanoid.Health <= 0 or not v:FindFirstChild("HumanoidRootPart") or (u and u())
	if not Success then warn("Attack Function Error : ",Error) end
end

task.spawn(function()
	while task.wait(0) do
		pcall(function()
			if C()['Method'] == "Behind" then
				MethodFarm = CFrame.new(0, 0,  30)
			elseif C()['Method'] == "Below" then
				MethodFarm = CFrame.new(0, - 30, 0) * CFrame.Angles(math.rad(90), 0, 0)
			elseif C()['Method'] == "Upper" then
				MethodFarm = CFrame.new(0,  30, 0) * CFrame.Angles(math.rad(0), 0, 0)
			else
				MethodFarm = CFrame.new(0,  30, 0)
			end
		end)
	end
end)

do 
	for i, v in pairs({
		["Auto Pole V1"] = {['World'] = FirstSea,['Mob'] = "Thunder God",},
		["Auto Trident"] = {['World'] = FirstSea,['Mob'] = "Fishman Lord"},
		["Auto Factory"] = {['World'] = SecondSea,['Mob'] = "Core"},
		["Auto Cannon"] = {['World'] = FirstSea,['Mob'] = "Wysper"},
		["Auto Bizento V2"] = {['World'] = FirstSea,['Mob'] = "Greybeard"},
		["Auto Dragon Trident"] = {['World'] = SecondSea,['Mob'] = "Tide Keeper"},
		["Auto Dark Coat"] = {['World'] = SecondSea,['Mob'] = "Darkbeard"},
		["Auto Swan Glasses"] = {['World'] = SecondSea,['Mob'] = "Don Swan"},
		["Auto Serpent Bow"] = {['World'] = ThirdSea,['Mob'] = "Island Empress"},
		["Auto Twin Hook"] = {['World'] = ThirdSea,['Mob'] = "Captain Elephant"},
		["Auto Canvander"] = {['World'] = ThirdSea,['Mob'] = "Beautiful Pirate"},
		}) do
		Func[i] = function()
			if not v['World'] then return end
			while C()[i] and task.wait() do
				pcall(function()
					if __f['Monster'](v['Mob']) then
						__f['Kill'](__f['Monster'](v['Mob']), function() return not C()[i] end)
					else
						if C()[i .. " Hop"] then Hop() end
					end
				end)
			end
		end
	end
end 

do 
	for i, v in pairs({
		['Auto Farm Ectoplasm'] = {['World'] = SecondSea,['Mob'] = {"Ship Deckhand","Ship Engineer","Ship Steward","Ship Officer"}},
		['Auto Farm Bone'] = {['World'] = ThirdSea,['Mob'] = {"Reborn Skeleton","Demonic Soul","Living Zombie","Posessed Mummy"}},
		}) do
		Func[i] = function()
			if not v['World'] then return end
			while C()[i] and task.wait() do
				pcall(function()
					if __f['Monster'](v['Mob']) then
						__f['Kill'](__f['Monster'](v['Mob']), function() return not C()[i] end)
					else
						__f['WaitMonster'](v['Mob'], function()
							return __f['Monster'](v['Mob']) or not C()[i]
						end)
					end
				end)
			end
		end
	end 
end 


local levelquest = QUESTNUMBER

Func['Auto Farm Level'] = function()
	while C()['Auto Farm Level'] and task.wait() do
		pcall(function()
			__f['QuestCheck']()
			local lv = LocalPlayer.Data.Level.Value
			if C()['Enabled Farm Fast'] and (lv > 20 and lv < 119) then 
				if lv > 20 and lv < 49 then 
					if __f['Monster']("God's Guard") then
						__f['Kill'](__f['Monster']("God's Guard"), function()
							return not C()['Auto Farm Level']
						end)
					else
						__f['WaitMonster']("God's Guard", function()
							return __f['Monster']("God's Guard") or not C()['Auto Farm Level']
						end)
					end 
				elseif lv > 50 and lv < 74 then 
					if __f['Monster']("Shanda") then
						__f['Kill'](__f['Monster']("Shanda"), function()
							return not C()['Auto Farm Level']
						end)
					else
						__f['WaitMonster']("Shanda", function()
							return __f['Monster']("Shanda") or not C()['Auto Farm Level']
						end)
					end 
				elseif lv > 75 and lv < 119 then 
					if __f['Monster']({"Royal Squad","Royal Soldier"}) then
						__f['Kill'](__f['Monster']({"Royal Squad","Royal Soldier"}), function()
							return not C()['Auto Farm Level'] 
						end)
					else
						__f['WaitMonster']({"Royal Squad","Royal Soldier"}, function()
							return __f['Monster']({"Royal Squad","Royal Soldier"}) or not C()['Auto Farm Level'] 
						end)
					end 
				else
					if __f['Monster'](BOSSNAME) then 
						monkub = BOSSNAME
					else
						monkub = string.gsub(string.gsub(string.gsub(QuestC.Container.QuestTitle.Title.Text, "^Defeat %d+ ", ""), " %(.-%)$", ""), "s$", "")
					end 
					local mon = monkub
					if QuestC.Visible and string.find(QuestC.Container.QuestTitle.Title.Text, mon) then
						if __f['Monster'](mon) then
							__f['Kill'](__f['Monster'](mon), function()
								return not C()['Auto Farm Level'] or not QuestC.Visible
							end)
						else
							__f['WaitMonster'](mon, function()
								return __f['Monster'](mon) or not C()['Auto Farm Level'] or not QuestC.Visible
							end)
						end 
					else
						if __f['dist'](QUESTPOS.p) <= 50 then
							if __f['Monster'](BOSSNAME) then
								_C("StartQuest",BOSSQUESTNAME,BOSSQUESTNUMBER)
							else
								_C("StartQuest",QUESTNAME,levelquest)
							end
							if C()["Double Quest"] then 
								if levelquest == 2 then
									levelquest = 1
								elseif levelquest == 1 and QUESTNUMBER == 2 then
									levelquest = 2 
								else
									levelquest = QUESTNUMBER
								end
							else
								levelquest = QUESTNUMBER
							end 
						else
							__f['toposition'](QUESTPOS)
						end
					end
				end 
			else
				if __f['Monster'](BOSSNAME) then 
					monkub = BOSSNAME
				else
					monkub = string.gsub(string.gsub(string.gsub(QuestC.Container.QuestTitle.Title.Text, "^Defeat %d+ ", ""), " %(.-%)$", ""), "s$", "")
				end 
				local mon = monkub
				if QuestC.Visible and string.find(QuestC.Container.QuestTitle.Title.Text, mon) then
					if __f['Monster'](mon) then
						__f['Kill'](__f['Monster'](mon), function()
							return not C()['Auto Farm Level'] or not QuestC.Visible
						end)
					else
						__f['WaitMonster'](mon, function()
							return __f['Monster'](mon) or not C()['Auto Farm Level'] or not QuestC.Visible
						end)
					end 
				else
					if __f['dist'](QUESTPOS.p) <= 50 then
						if __f['Monster'](BOSSNAME) then
							_C("StartQuest",BOSSQUESTNAME,BOSSQUESTNUMBER)
						else
							_C("StartQuest",QUESTNAME,levelquest)
						end
						if C()["Double Quest"] then 
							if levelquest == 2 then
								levelquest = 1
							elseif levelquest == 1 and QUESTNUMBER == 2 then
								levelquest = 2 
							else
								levelquest = QUESTNUMBER
							end
						else
							levelquest = QUESTNUMBER
						end 
					else
						__f['toposition'](QUESTPOS)
					end
				end
			end 
		end)
	end
end

Func['Enabled Dressrosa Quest'] = function()
	while C()['Enabled Dressrosa Quest'] and task.wait() do
		pcall(function()
			if not FirstSea then return end
			if LocalPlayer.Data.Level.Value >= 700 and FirstSea then
				local Q_New = _C("DressrosaQuestProgress")
				if Q_New['UsedKey'] == false then
					_C("DressrosaQuestProgress","Detective")
					__f['Equip']("Key")
					__f['toposition'](CFrame.new(1347.7124, 37.3751602, -1325.6488))
				elseif Q_New['KilledIceBoss'] == false then
					if __f['Monster']("Ice Admiral") then
						__f['Kill'](__f['Monster']("Ice Admiral"), function() return not C()["Enabled Dressrosa Quest"] end)
					end
					_C("TravelDressrosa")
				elseif Q_New['KilledIceBoss'] == true then
					_C("TravelDressrosa")
				end
			end
		end)
	end
end

Func['Enabled Zou Quest'] = function()
	while C()['Enabled Zou Quest'] and task.wait() do
		pcall(function()
			if not SecondSea then return end
			if LocalPlayer.Data.Level.Value >= 1500 and SecondSea then
				local Q_Bar = _C("BartiloQuestProgress")
				if _C("TalkTrevor","1") == 0 and Q_Bar['KilledBandits'] == true and Q_Bar['DidPlates'] == true then
					if Kill_Don then
						if game:GetService("Workspace").Enemies:FindFirstChild("rip_indra") then
							if __f['Monster']("rip_indra") then
								__f['Kill'](__f['Monster']("rip_indra"), function() return not C()['Enabled Zou Quest'] end)
							end
						elseif _C("ZQuestProgress","Check") == 1 then
							_C("TravelZou")
						elseif not game:GetService("Workspace").Enemies:FindFirstChild("rip_indra") then
							_C("ZQuestProgress","Check")
							_C("ZQuestProgress","Begin")
							wait(3)
						end
					elseif not oijdfg then
						_C("ZQuestProgress","Check")
						_C("ZQuestProgress","Begin")
						wait(3)
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if v.Name == 'rip_indra' then
								Kill_Don = true
							end
						end
						oijdfg = true
					end
				else
					if not Q_Bar['KilledBandits'] and not Q_Bar['DidPlates'] then 
						if Q_Bar['KilledBandits'] == false then
							if QuestC.Visible and string.find(QuestC.Container.QuestTitle.Title.Text, "Swan Pirates") and string.find(QuestC.Container.QuestTitle.Title.Text, "50") then
								if __f['Monster']("Swan Pirate") then
									__f['Kill'](__f['Monster']("Swan Pirate"), function()
										return not C()['Enabled Zou Quest']
									end)
								else
									__f['WaitMonster']("Swan Pirate", function()
										return __f['Monster']("Swan Pirate") or not C()['Enabled Zou Quest']
									end)
								end 
							else
								_C("StartQuest","BartiloQuest",1)
							end
						elseif Q_Bar['KilledSpring'] == false then
							if __f['Monster']("Jeremy") then
								__f['Kill'](__f['Monster']("Jeremy"), function() return not C()['Enabled Zou Quest'] end)
							end
						elseif Q_Bar['DidPlates'] == false then
							repeat wait(.3) 
								__f['toposition'](CFrame.new(-1836, 11, 1714)) 
							until (Vector3.new(-1836, 11, 1714)-RootPart.Position).Magnitude < 10
							wait(1)
							_C("BartiloQuestProgress","DidPlates") 
						end
					elseif Q_Bar['KilledBandits'] and Q_Bar['DidPlates'] and _C("TalkTrevor","1") == 0 then 
						if not _C("TalkTrevor","1") == 0 then
							local bitx = false
							local fruit = _C("getInventoryFruits")
							for i,v in pairs(fruit)do
								if v['Price'] >= 1000000 and not bitx then
									result = {}
									local regex = ("([^%s]+)"):format("-")
									for each in v["Name"]:gmatch(regex) do
										table.insert(result, each)
									end
									local NameFruit = result[2] .. " Fruit"
									_C("LoadFruit",v["Name"])
									wait(1)
									for i,v in pairs(LocalPlayer.Backpack:GetChildren()) do
										if v:IsA('Tool') and v.Name == NameFruit then
											__f['Equip'](v.Name)
											wait(.5)
											_C("TalkTrevor","1")
											_C("TalkTrevor","2")
											_C("TalkTrevor","3")
										end
									end
									for i,v in pairs(Character:GetChildren()) do
										if v:IsA('Tool') and v.Name == NameFruit then
											__f['Equip'](v.Name)
											wait(.5)
											_C("TalkTrevor","1")
											_C("TalkTrevor","2")
											_C("TalkTrevor","3")
										end
									end
									bitx = true
								end
							end
						elseif _C("TalkTrevor","1") == 0 then
							__f['Kill'](__f['Monster']("Don Swan"), function()
								return not C()['Enabled Zou Quest']
							end)
						end
					end 
				end
			end
		end)
	end
end 

Func['Auto Saber'] = function()
	while C()['Auto Saber'] do task.wait()
		pcall(function()
			if not FirstSea then return end
			if LocalPlayer.Data.Level.Value >= 200 and workspace.Map.Jungle.Final.Part.Transparency == 0 then
				if game:GetService("Workspace").Map.Jungle.Final.Part.Transparency == 0 then
					if game:GetService("Workspace").Map.Jungle.QuestPlates.Door.Transparency == 0 then
						for i,v in next,game:GetService("Workspace").Map.Jungle.QuestPlates:GetChildren() do
							if v:IsA("Model") then
								if v.Button:FindFirstChild("TouchInterest") then
									firetouchinterest(RootPart, v.Button, 0)
								end
							end
						end
					else
						if not _C("ProQuestProgress")["UsedTorch"] then
							_C("ProQuestProgress","GetTorch")
							__f['Equip']("Torch")
							_C("ProQuestProgress","DestroyTorch")
						elseif not _C("ProQuestProgress")["UsedCup"] then
							_C("ProQuestProgress","GetCup")
							__f['Equip']("Cup")
							_C("ProQuestProgress","FillCup",LocalPlayer.Character.Cup)
							_C("ProQuestProgress","SickMan")
						elseif not _C("ProQuestProgress")["KilledMob"] then
							_C("ProQuestProgress","RichSon")
							if __f['Monster']("Mob Leader") then
								__f['Kill'](__f['Monster']("Mob Leader"), function()
									return _C("ProQuestProgress")["KilledMob"] or not C()['Auto Saber']
								end)
							end
						elseif not _C("ProQuestProgress")["UsedRelic"] then
							_C("ProQuestProgress","RichSon")
							__f['Equip']("Relic")
							_C("ProQuestProgress","PlaceRelic")
						end
					end
				else
					if __f['Monster']("Saber Expert") then
						__f['Kill'](__f['Monster']("Saber Expert"), function()
							return not C()['Auto Saber']
						end)
					else
						if C()["Auto Saber Hop"] then 
							Hop()
						end 
					end
				end
			end
		end)
	end
end

Func['Auto Bartlio Quest'] = function()
	while C()['Auto Bartlio Quest'] and task.wait() do
		pcall(function()
			if not SecondSea then return end
			if LocalPlayer.Data.Level.Value >= 850 and SecondSea then
				local Q_Bar = _C("BartiloQuestProgress")
				if Q_Bar['KilledBandits'] == false then
					if QuestC.Visible and string.find(QuestC.Container.QuestTitle.Title.Text, "Swan Pirates") and string.find(QuestC.Container.QuestTitle.Title.Text, "50") then
						if __f['Monster']("Swan Pirate") then
							__f['Kill'](__f['Monster']("Swan Pirate"), function()
								return not C()['Auto Bartlio Quest'] or not QuestC.Visible
							end)
						else
							__f['WaitMonster']("Swan Pirate", function()
								return __f['Monster']("Swan Pirate") or not C()['Auto Bartlio Quest'] or not QuestC.Visible
							end)
						end 
					else
						_C("StartQuest","BartiloQuest",1)
					end
				elseif Q_Bar['KilledSpring'] == false then
					if __f['Monster']("Jeremy") then
						__f['Kill'](__f['Monster']("Jeremy"), function() return not C()['Auto Bartlio Quest'] end)
					end
				elseif Q_Bar['DidPlates'] == false then
					repeat wait(.3) 
						__f['toposition'](CFrame.new(-1836, 11, 1714)) 
					until (Vector3.new(-1836, 11, 1714)-RootPart.Position).Magnitude < 10
					wait(1)
					_C("BartiloQuestProgress","DidPlates") 
				end
			end
		end)
	end
end

Func['Auto Don Swan Quest'] = function()
	while C()['Auto Don Swan Quest'] and task.wait() do
		pcall(function()
			if not SecondSea then return end
			if LocalPlayer.Data.Level.Value >= 1000 and SecondSea then
				if C()['Auto Farm Level'] then FarmLevel = false end 
				local bitx = false
				local fruit = _C("getInventoryFruits")
				for i,v in pairs(fruit)do
					if v['Price'] >= 1000000 and not bitx then
						result = {}
						local regex = ("([^%s]+)"):format("-")
						for each in v["Name"]:gmatch(regex) do
							table.insert(result, each)
						end
						local NameFruit = result[2] .. " Fruit"
						_C("LoadFruit",v["Name"])
						wait(1)
						for i,v in pairs(LocalPlayer.Backpack:GetChildren()) do
							if v:IsA('Tool') and v.Name == NameFruit then
								__f['Equip'](v.Name)
								wait(.5)
								_C("TalkTrevor","1")
								_C("TalkTrevor","2")
								_C("TalkTrevor","3")
							end
						end
						for i,v in pairs(Character:GetChildren()) do
							if v:IsA('Tool') and v.Name == NameFruit then
								__f['Equip'](v.Name)
								wait(.5)
								_C("TalkTrevor","1")
								_C("TalkTrevor","2")
								_C("TalkTrevor","3")
							end
						end
						bitx = true
					end
				end
				if _C("TalkTrevor","1") == 0 then
					__f['Kill'](__f['Monster']("Don Swan"), function()
						return not C()['Auto Don Swan Quest']
					end)
				end
			end
		end)
	end
end

Func['Auto Farm Material'] = function()
	while C()['Auto Farm Material'] and task.wait() do
		pcall(function()
			__f['CheckMaterial'](C()['Select Material'])
			if __f['Monster'](MaterialMob) then
				__f['Kill'](__f['Monster'](MaterialMob), function()
					return not C()['Auto Farm Material']
				end)
			else
				__f['WaitMonster'](MaterialMob, function()
					return __f['Monster'](MaterialMob) or not C()['Auto Farm Material']
				end)
			end
		end)
	end
end

Func['Farm Fruit Mastery'] = function()
	while C()['Farm Fruit Mastery'] and task.wait() do
		pcall(function()
			__f['QuestCheck']()
			monkub = string.gsub(string.gsub(string.gsub(QuestC.Container.QuestTitle.Title.Text, "^Defeat %d+ ", ""), " %(.-%)$", ""), "s$", "")
			local v = __f['Monster'](monkub)
			if QuestC.Visible and string.find(QuestC.Container.QuestTitle.Title.Text, monkub) then
				if __f['Monster'](monkub) then 
					repeat task.wait()
						NeedNoclip = true
						HealthMin = v.Humanoid.MaxHealth * C()['Kill At']/100
						print(HealthMin)
						if v.Humanoid.Health <= HealthMin then
							__f['Equip'](LocalPlayer.Data.DevilFruit.Value)
							__f['toposition'](v.HumanoidRootPart.CFrame * CFrame.new(0, 40, 10))
							PositionSkillMasteryDevilFruit = v.HumanoidRootPart.Position
							UseSkillMasteryDevilFruit = true
							__f['BringMob'](v)
							if game:GetService("Players").LocalPlayer.Character:FindFirstChild(LocalPlayer.Data.DevilFruit.Value) then
								MasteryDevilFruit = require(game:GetService("Players").LocalPlayer.Character[LocalPlayer.Data.DevilFruit.Value].Data)
								DevilFruitMastery = game:GetService("Players").LocalPlayer.Character[LocalPlayer.Data.DevilFruit.Value].Level.Value
							elseif game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(LocalPlayer.Data.DevilFruit.Value) then
								MasteryDevilFruit = require(game:GetService("Players").LocalPlayer.Backpack[LocalPlayer.Data.DevilFruit.Value].Data)
								DevilFruitMastery = game:GetService("Players").LocalPlayer.Backpack[LocalPlayer.Data.DevilFruit.Value].Level.Value
							end
							if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon-Dragon") then
								if C()['Skill Z'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.Z then
									game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
									wait(.1)
									game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
								end
								if C()['Skill X'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.X then
									game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
									wait(.1)
									game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
								end   
							elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Human-Human: Buddha") then
								if C()['Skill Z'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and LocalPlayer.Character.HumanoidRootPart.Size == Vector3.new(7.6, 7.676, 3.686) and DevilFruitMastery >= MasteryDevilFruit.Lvl.Z then
								else
									game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
									wait(.1)
									game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
								end
								if C()['Skill X'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.X then
									game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
									wait(.1)
									game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
								end
								if C()['Skill C'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.C then
									game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
									wait(.1)
									game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
								end  
							elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Venom-Venom") then
								if C()['Skill Z'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.Z then
									game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
									wait(4)
									game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
								end
								if C()['Skill X'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.X then
									game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
									wait(.1)
									game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
								end
								if C()['Skill C'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.C then
									game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
									wait(.1)
									game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
								end
							elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild(LocalPlayer.Data.DevilFruit.Value) then
								game:GetService("Players").LocalPlayer.Character:FindFirstChild(LocalPlayer.Data.DevilFruit.Value).MousePos.Value = v.HumanoidRootPart.Position
								if C()['Skill Z'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.Z then
									game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
									wait(.1)
									game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
								end
								if C()['Skill X'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.X then
									game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
									wait(.1)
									game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
								end
								if C()['Skill C'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.C then
									game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
									wait(.1)
									game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
								end
								if C()['Skill V'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.V then
									game:service('VirtualInputManager'):SendKeyEvent(true, "V", false, game)
									wait(.1)
									game:service('VirtualInputManager'):SendKeyEvent(false, "V", false, game)
								end
							end
						else
							__f['Equip'](__f['GetToolFromTip'](C()['Weapon']))
							__f['toposition'](v.HumanoidRootPart.CFrame * CFrame.new(0, 20, 0))
						end
					until not v.Parent or v.Humanoid.Health <= 0 or not C()['Farm Fruit Mastery']
					NeedNoclip = false
				else
					__f['WaitMonster'](monkub, function()
						return __f['Monster'](monkub) or not C()['Farm Fruit Mastery'] or not QuestC.Visible
					end)
				end 
			else
				if __f['dist'](QUESTPOS.p) <= 50 then
					if __f['Monster'](BOSSNAME) then
						_C("StartQuest",BOSSQUESTNAME,BOSSQUESTNUMBER)
					else
						_C("StartQuest",QUESTNAME,levelquest)
					end
					if C()["Double Quest"] then 
						if levelquest == 2 then
							levelquest = 1
						elseif levelquest == 1 and QUESTNUMBER == 2 then
							levelquest = 2 
						else
							levelquest = QUESTNUMBER
						end
					else
						levelquest = QUESTNUMBER
					end 
				else
					__f['toposition'](QUESTPOS)
				end
			end
		end)
	end
end

Func['Farm Gun Mastery'] = function()
	while C()['Farm Gun Mastery'] and task.wait() do
		pcall(function()
			__f['QuestCheck']()
			monkub = string.gsub(string.gsub(string.gsub(QuestC.Container.QuestTitle.Title.Text, "^Defeat %d+ ", ""), " %(.-%)$", ""), "s$", "")
			local v = __f['Monster'](monkub)
			if QuestC.Visible and string.find(QuestC.Container.QuestTitle.Title.Text, monkub) then
				if __f['Monster'](monkub) then 
					repeat task.wait()
						NeedNoclip = true
						HealthMin = v.Humanoid.MaxHealth * C()['Kill At']/100
						print(HealthMin)
						if v.Humanoid.Health <= HealthMin then
							__f['Equip'](LocalPlayer.Data.DevilFruit.Value)
							__f['toposition'](v.HumanoidRootPart.CFrame * CFrame.new(0, 40, 10))
							PositionSkillMasteryGun = v.HumanoidRootPart.Position
							__f['BringMob'](v)

						else
							__f['Equip'](__f['GetToolFromTip'](C()['Weapon']))
							__f['toposition'](v.HumanoidRootPart.CFrame * CFrame.new(0, 20, 0))
						end
					until not v.Parent or v.Humanoid.Health <= 0 or not C()['Farm Fruit Mastery']
					NeedNoclip = false
				else
					__f['WaitMonster'](monkub, function()
						return __f['Monster'](monkub) or not C()['Farm Fruit Mastery'] or not QuestC.Visible
					end)
				end 
			else
				if __f['dist'](QUESTPOS.p) <= 50 then
					if __f['Monster'](BOSSNAME) then
						_C("StartQuest",BOSSQUESTNAME,BOSSQUESTNUMBER)
					else
						_C("StartQuest",QUESTNAME,levelquest)
					end
					if C()["Double Quest"] then 
						if levelquest == 2 then
							levelquest = 1
						elseif levelquest == 1 and QUESTNUMBER == 2 then
							levelquest = 2 
						else
							levelquest = QUESTNUMBER
						end
					else
						levelquest = QUESTNUMBER
					end 
				else
					__f['toposition'](QUESTPOS)
				end
			end
		end)
	end
end

Func['Farm Fruit Mastery Bone'] = function()
	if not ThirdSea then return end
	while C()['Farm Fruit Mastery Bone'] and task.wait() do
		pcall(function()
			monkub = {"Reborn Skeleton","Demonic Soul","Living Zombie","Posessed Mummy"}
			local v = __f['Monster'](monkub)
			if __f['Monster'](monkub) then 
				repeat task.wait()
					NeedNoclip = true
					HealthMin = v.Humanoid.MaxHealth * C()['Kill At']/100
					print(HealthMin)
					if v.Humanoid.Health <= HealthMin then
						__f['Equip'](LocalPlayer.Data.DevilFruit.Value)
						__f['toposition'](v.HumanoidRootPart.CFrame * CFrame.new(0, 40, 10))
						PositionSkillMasteryDevilFruit = v.HumanoidRootPart.Position
						UseSkillMasteryDevilFruit = true
						__f['BringMob'](v)
						if game:GetService("Players").LocalPlayer.Character:FindFirstChild(LocalPlayer.Data.DevilFruit.Value) then
							MasteryDevilFruit = require(game:GetService("Players").LocalPlayer.Character[LocalPlayer.Data.DevilFruit.Value].Data)
							DevilFruitMastery = game:GetService("Players").LocalPlayer.Character[LocalPlayer.Data.DevilFruit.Value].Level.Value
						elseif game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(LocalPlayer.Data.DevilFruit.Value) then
							MasteryDevilFruit = require(game:GetService("Players").LocalPlayer.Backpack[LocalPlayer.Data.DevilFruit.Value].Data)
							DevilFruitMastery = game:GetService("Players").LocalPlayer.Backpack[LocalPlayer.Data.DevilFruit.Value].Level.Value
						end
						if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon-Dragon") then
							if C()['Skill Z'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.Z then
								game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
								wait(.1)
								game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
							end
							if C()['Skill X'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.X then
								game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
								wait(.1)
								game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
							end   
						elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Human-Human: Buddha") then
							if C()['Skill Z'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and LocalPlayer.Character.HumanoidRootPart.Size == Vector3.new(7.6, 7.676, 3.686) and DevilFruitMastery >= MasteryDevilFruit.Lvl.Z then
							else
								game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
								wait(.1)
								game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
							end
							if C()['Skill X'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.X then
								game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
								wait(.1)
								game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
							end
							if C()['Skill C'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.C then
								game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
								wait(.1)
								game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
							end  
						elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Venom-Venom") then
							if C()['Skill Z'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.Z then
								game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
								wait(4)
								game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
							end
							if C()['Skill X'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.X then
								game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
								wait(.1)
								game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
							end
							if C()['Skill C'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.C then
								game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
								wait(.1)
								game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
							end
						elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild(LocalPlayer.Data.DevilFruit.Value) then
							game:GetService("Players").LocalPlayer.Character:FindFirstChild(LocalPlayer.Data.DevilFruit.Value).MousePos.Value = v.HumanoidRootPart.Position
							if C()['Skill Z'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.Z then
								game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
								wait(.1)
								game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
							end
							if C()['Skill X'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.X then
								game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
								wait(.1)
								game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
							end
							if C()['Skill C'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.C then
								game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
								wait(.1)
								game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
							end
							if C()['Skill V'] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.V then
								game:service('VirtualInputManager'):SendKeyEvent(true, "V", false, game)
								wait(.1)
								game:service('VirtualInputManager'):SendKeyEvent(false, "V", false, game)
							end
						end
					else
						__f['Equip'](__f['GetToolFromTip'](C()['Weapon']))
						__f['toposition'](v.HumanoidRootPart.CFrame * CFrame.new(0, 20, 0))
					end
				until not v.Parent or v.Humanoid.Health <= 0 or not C()['Farm Fruit Mastery Bone']
				NeedNoclip = false
			else
				__f['WaitMonster'](monkub, function()
					return __f['Monster'](monkub) or not C()['Farm Fruit Mastery Bone']
				end)
			end 
		end)
	end
end

Func['Farm Gun Mastery Bone'] = function()
	if not ThirdSea then return end
	while C()['Farm Gun Mastery Bone'] and task.wait() do
		pcall(function()
			monkub = {"Reborn Skeleton","Demonic Soul","Living Zombie","Posessed Mummy"}
			local v = __f['Monster'](monkub)
			if __f['Monster'](monkub) then 
				repeat task.wait()
					NeedNoclip = true
					HealthMin = v.Humanoid.MaxHealth * C()['Kill At']/100
					print(HealthMin)
					if v.Humanoid.Health <= HealthMin then
						__f['Equip'](LocalPlayer.Data.DevilFruit.Value)
						__f['toposition'](v.HumanoidRootPart.CFrame * CFrame.new(0, 40, 10))
						PositionSkillMasteryGun = v.HumanoidRootPart.Position
						__f['BringMob'](v)

					else
						__f['Equip'](__f['GetToolFromTip'](C()['Weapon']))
						__f['toposition'](v.HumanoidRootPart.CFrame * CFrame.new(0, 20, 0))
					end
				until not v.Parent or v.Humanoid.Health <= 0 or not C()['Farm Gun Mastery Bone']
				NeedNoclip = false
			else
				__f['WaitMonster'](monkub, function()
					return __f['Monster'](monkub) or not C()['Farm Gun Mastery Bone'] 
				end)
			end 
		end)
	end
end

Func['Farm All Sword Mastery'] = function()
	while C()['Farm All Sword Mastery'] and task.wait() do
		pcall(function()
			if C()['Select Farm Mode'] == "Level Farm" then 

			elseif C()['Select Farm Mode'] == "Bone Farm" then 

			elseif C()['Select Farm Mode'] == "Cake Farm" then 

			end 
		end)
	end
end

Func['Auto Cake Prince'] = function()
	if not ThirdSea then return end
	while C()['Auto Cake Prince'] and task.wait() do
		pcall(function()
			if string.find(_C("CakePrinceSpawner"), "Do you want to open the portal now?") then
				_C("CakePrinceSpawner")
			end
			if __f['Monster']("Cake Prince") then
				__f['Kill'](__f['Monster']("Cake Prince"), function()
					return not C()['Auto Cake Prince']
				end)
			else
				local enemyNames = {
					"Cookie Crafter",
					"Cake Guard",
					"Baking Staff",
					"Head Baker"
				}
				if __f['Monster'](enemyNames) then
					__f['Kill'](__f['Monster'](enemyNames), function()
						return not C()['Auto Cake Prince']
					end)
				else
					__f['WaitMonster'](enemyNames, function()
						return __f['Monster'](enemyNames) or not C()['Auto Cake Prince']
					end)
				end
			end                
		end)
	end
end

Func['Auto Midnight Blade'] = function()
	if not SecondSea then return end
	while C()['Auto Midnight Blade'] and task.wait() do
		pcall(function()
            if _C("Ectoplasm","Check") >= 100 then
                _C("Ectoplasm","Buy",3)
            end
		end)
	end
end

task.spawn(function()
	if FirstSea then return end
	local RaidID
	JustStarted = false
	while wait(1) do
		if FirstSea then break end
		if LocalPlayer.Data.Level.Value < 1100 then continue end
		if not Character or not RootPart or not Character:FindFirstChild("Humanoid") then continue end
		if Humanoid.Health < 1 then continue end
		if (Settings.LockFragments and LocalPlayer.Data.Fragments.Value >= C()['Lock Fragments Amount']) and not ForceRaid then
			if Settings.LockFragmentsKick then
				StopAutoRejoin = true
				LocalPlayer:Kick("Fragments Reached")
			end
			continue
		end
		if (C()['Auto Start Raid'] or ForceRaid) and not __f['IsRaiding']() then
			local AvailableFruit = tick() - StoredSuccessFully > 0.5 and __f['hasFruit']()
			if LocalPlayer.Data.Level.Value < math.clamp(C()['Auto Start Raid Level'] or 1100,1100,1/0) and not AvailableFruit then DoNotStore = false continue end
			if not workspace:FindFirstChild("Message") then	
				DoNotStore = true
				if not Character or not RootPart or Humanoid.Health < 1 then continue end
				if not AvailableFruit and not __f['hasChip']() then
					if not __f['hasFruit']() then
						for i,v in pairs(game:GetChildren()) do
							if v:IsA("Tool") then
								v.Parent = workspace
							end
						end
						if not __f['CollectFruit']() then
							if _C("Cousin","Buy") ~= 1 then
								local Fruits = _C("getInventoryFruits")
								local Cheapest = {Price = 1/0}
								for i,v in pairs(Fruits or {}) do
									if v.Price < tonumber(1000000) and v.Price < Cheapest.Price then
										Cheapest = v
									end
								end
								if Cheapest.Name then
									_C("LoadFruit",Cheapest.Name)
								end
							end
						end
					end
				end
				wait(0.75)
				local Data
				if not Character or not RootPart or Humanoid.Health < 1 then continue end
				if not __f['hasChip']() and not __f['IsRaiding']() then
					if LocalPlayer.Data.DevilFruit.Value ~= "" then
						local FruitName = __f['RaidFruitName'](LocalPlayer.Data.DevilFruit.Value)
						Data = _C("RaidsNpc","Select",(C()['Raid Microship'] == "CurrentFruit" and LocalPlayer.Data.DevilFruit.Value ~= "" and table.find(RaidMicroship,FruitName) and FruitName) or __f['RaidFruitName'](C()['Raid Microship'] ~= "CurrentFruit" and C()['Raid Microship'] or "Dark"))
					else
						Data = _C("RaidsNpc","Select","Dark")
					end
					StartFragments = LocalPlayer.Data.Fragments.Value
				end
				wait(1)
				if not Character or not RootPart or Humanoid.Health < 1 then continue end
				DoNotStore = false
				if __f['hasChip']() and not __f['IsRaiding']() then
					fireclickdetector(workspace.Map:FindFirstChild("RaidSummon2",true).Button.Main.ClickDetector)
					local ID = HttpService:GenerateGUID()
					RaidID = ID
					JustStarted = true 
					task.delay(60,function()
						if RaidID == ID then
							JustStarted = false
						end
					end)
				end
				if (C()['Auto Start Raid'] or ForceRaid) and not __f['IsRaiding']() and not JustStarted then
					wait(.25)
					if not AvailableFruit and Data ~= 1 and not (type(Data) == "string" and Data:find("already")) and not JustStarted and not __f['IsRaiding']() and C()['Auto Raid Hop'] and not __f['hasChip']() and not __f['hasFruit']() then Hop() continue end
				end
			end
		end
		if (C()['Auto Raid'] or ForceRaid) and __f['IsRaiding']() then
			local Rif = __f['RaidInfo']()
			repeat
				Rif = __f['RaidInfo']() 
				task.wait(0.02)
			until Rif.ID or not (C()['Auto Raid'] or ForceRaid) or not __f['IsRaiding']()
			wait(1)
			if not (C()['Auto Raid'] or ForceRaid) then
				continue
			end
			local Success,Error = pcall(function()
				repeat
					NeedNoclip = true
					Rif.new()
					if Rif.LastestIsland then
						__f['toposition'](Rif.LastestIsland.CFrame * CFrame.new(0,50,25))
						for i,v in pairs(workspace.Enemies:GetChildren()) do
							local Human = v:FindFirstChildOfClass("Humanoid")
							if Human and Human.Health > 0 and Human.RootPart then
								if not C()['Kill Aura'] or (not __f['isnetworkowner'](Human.RootPart) and __f['dist'](Human.RootPart.Position) <= 1000) then
									repeat
										__f['Buso']()
										local POS = Human.RootPart.CFrame
										__f['toposition'](CFrame.new(POS.X,math.clamp(POS.Y,0,1/0),POS.Z) * CFrame.new(math.random(-2,2),40,math.random(-2,2)))
										__f['Equip'](__f['GetToolFromTip'](C()['Weapon']))
										task.wait(0.02)
									until not Human or v.Parent ~= workspace.Enemies or (__f['isnetworkowner'](Human.RootPart) and C()['Kill Aura'])
								end
							end
						end
					end
					task.wait(0.02)
				until not (C()['Auto Raid'] or ForceRaid) or not __f['IsRaiding']() or Humanoid.Health <= 0 
			end)
			if not Success then
				warn("Raid Error Send this yellow message to x1nxwny\n",Error)
			end
			repeat Rif.new() wait() until not Rif.ID or not Rif.ID.Parent or not __f['IsRaiding']()
			local Area = __f['InArea'](RootPart.Position)
			repeat
				Area = __f['InArea'](RootPart.Position)
				wait(.2)
			until Area and not Area.Name:find("Island") or not __f['IsRaiding']()
			workspace.NPCs:WaitForChild("Mysterious Entity",2)
			repeat wait() until not workspace.NPCs:FindFirstChild("Mysterious Entity")
			JustStarted = false
		end
	end
end)

spawn(function()
	while wait() do
		pcall(function()
			if C()['Auto Set Spawn Point'] then
				if LocalPlayer.Character.Humanoid.Health > 0 then
					_C("SetSpawnPoint")
				end
			end
			if C()['White Screen'] then
				game:GetService("RunService"):Set3dRenderingEnabled(false)
			else
				game:GetService("RunService"):Set3dRenderingEnabled(true)
			end
			if C()['Auto Ken'] then
				local args = {[1] = "Ken",[2] = true}
				game:GetService("ReplicatedStorage").Remotes.CommE:FireServer(unpack(args))
			end
			if C()['Auto Haki'] then
				__f['Buso']()
			end
			if C()['Hide Notifications'] then
				LocalPlayer.PlayerGui.Notifications.Enabled = false
			else
				LocalPlayer.PlayerGui.Notifications.Enabled = true
			end
			if C()['Auto Activate Race V3'] then
				game:GetService("VirtualInputManager"):SendKeyEvent(true,Enum.KeyCode.T,false,game)
				game:GetService("VirtualInputManager"):SendKeyEvent(false,Enum.KeyCode.T,false,game)
			end
			if C()['Auto Activate Race V4'] then
				game:GetService("VirtualInputManager"):SendKeyEvent(true,Enum.KeyCode.Y,false,game)
				game:GetService("VirtualInputManager"):SendKeyEvent(false,Enum.KeyCode.Y,false,game)
			end
		end)
	end
end)


Func['Auto Godhuman'] = function()
	task.spawn(function()
		local Success,Data = pcall(_C,"BuyGodhuman",not LaunchedSuccessfully)
		if Data == 1 or Data == 2 then
			wait()
			Finished.Superhuman = true
			return
		end
		while C()['Auto Godhuman'] and wait(.5) do
			if C()['Auto Godhuman'] and Finished.ElecticClaw and Finished.DragonTalon and Finished.DeathStep and Finished.Superhuman and Finished.SharkmanKarate then
				if not __f['checkIsAvailable']("ElectricClaw",400) then continue end
				if not __f['checkIsAvailable']("DeathStep",400) then continue end
				if not __f['checkIsAvailable']("SharkmanKarate",400) then continue end
				if not __f['checkIsAvailable']("DragonTalon",400) then continue end
				if not __f['checkIsAvailable']("Superhuman",400) then continue end
				if _C("BuyGodhuman",true) == 0 then
					if LocalPlayer.Data.Fragments.Value >= 5000 and not __f['IsRaiding']() then
						if LocalPlayer.Data.Beli.Value >= tonumber("5e+6") then
							ForceRaid = false
							if __f['purchaseCombat']("Godhuman") then
								Finished.Godhuman = true
								return
							end
						end
					else
						ForceRaid = true
					end
				end
			end
		end
	end)
end 
Func['Auto Superhuman'] = function()
	task.spawn(function()
		local Success,Data = pcall(_C,"BuySuperhuman",not LaunchedSuccessfully)
		if Data == 1 or Data == 2 then
			Finished.Superhuman = true
			return
		end
		while C()['Auto Superhuman'] and wait(.5) do
			if not __f['checkIsAvailable']("Electro",300) then continue end
			if not __f['checkIsAvailable']("BlackLeg",300) then continue end
			if not __f['checkIsAvailable']("FishmanKarate",300) then continue end
			if not __f['checkIsAvailable']("DragonClaw",300) then 
				ForceRaid = not __f['purchaseCombat']("DragonClaw")
				continue
			end
			ForceRaid = false
			if LocalPlayer.Data.Beli.Value >= tonumber("3e+6") then
				if __f['purchaseCombat']("Superhuman") then
					Finished.Superhuman = true
					ForceRaid = false
					return
				elseif LocalPlayer.Data.Fragments.Value < 5000 and not Finished.Superhuman then
					ForceRaid = true
				end
			end
		end
	end)
end
Func['Auto Sharkman Karate'] = function()
	task.spawn(function()
		local Success,Data = pcall(_C,"BuySharkmanKarate",not LaunchedSuccessfully)
		if Data == 1 or Data == 2 then
			wait()
			Finished.SharkmanKarate = true 
			Finished.TrueSharkmanKarate = true 
			return
		end
		local UsedKey = Data
		SharkmanBossAttacked = Data == 3
		if not SharkmanBossAttacked and not SecondSea then return end
		while C()['Auto Sharkman Karate'] and wait(2) do
			if Finished.TrueSharkmanKarate then break end
			if C()['Auto Sharkman Karate'] and (Finished.Superhuman or not C()['Auto Superhuman']) then
				UsedKey = _C("BuySharkmanKarate",true)
				SharkmanBossAttacked = UsedKey == 3
				if not SharkmanBossAttacked and SecondSea then
					if (not C()['Auto Farm Level'] and LocalPlayer.Data.Level.Value > 1100 or LocalPlayer.Data.Level.Value >= 1500) and not __f['Monster']("Tide Keeper") and C()['Auto Death Step'] and not Finished.DeathStep and NoDeathStepBoss and C()['Auto Death Step Hop'] then
						Serverhop("Auto DeathStep")
					end
					if ((LocalPlayer.Data.Level.Value > 1100 and not C()['Auto Farm Level']) or (LocalPlayer.Data.Level.Value >= 1500)) and not __f['Monster']("Tide Keeper") and C()['Auto Sharkman Karate Hop'] then
						Serverhop("Auto Sharkman Karate")
					end
					if __f['Monster']("Tide Keeper") then
						__f['Kill'](__f['Monster']("Tide Keeper"), function()
							return not C()['Auto Sharkman Karate']
						end)
					end
					if __f['hasItem']("Water Key") then
						UsedKey = _C("BuySharkmanKarate",true)
					end
				elseif SharkmanBossAttacked and (Finished.DeathStep or not C()['Auto Death Step']) and (Finished.DeathStep or NoDeathStepBoss or DeathStepBossAttacked or not C()['Auto Death Step']) and (Finished.ElecticClaw or not C()['Auto Electric Claw'] or SecondSea) then
					pcall(function()
						local Data = MasteryData.SharkmanKarate or _C("BuyFishmanKarate")
						if SecondSea and C()['Enabled Zou Quest'] then
							Finished.SharkmanKarate = true
						end
						if type(Data) == "number" and (Data == 1 or Data == 2 or Data > 100) and (MasteryData.SharkmanKarate or __f['GetToolFromTip']("Fishman Karate",true):WaitForChild("Level").Value) >= 400 then	
							MasteryData.SharkmanKarate = 400
							if Client.Data.Fragments.Value >= 5000 and not __f['IsRaiding']()  then
								ForceRaid = false
								if __f['purchaseCombat']("SharkmanKarate") then
									Finished.SharkmanKarate = true
									Finished.TrueSharkmanKarate = true
									wait()
									pcall(EquipBest)
									return
								end
							else
								if not C()['Enabled Zou Quest'] or not SecondSea then
									ForceRaid = true
								end
							end
						end
					end)
				end
			end
		end
	end)
end

Func['Auto Death Step'] = function()
	task.spawn(function()
		local UsedKey = _C("OpenLibrary")
		DeathStepBossAttacked = UsedKey
		if not UsedKey and not SecondSea then return end
		local Data = _C("BuyDeathStep",not LaunchedSuccessfully)
		if Data == 1 or Data == 2 then 
			Finished.DeathStep = true
			wait()
			return 
		end
		while C()['Auto Death Step'] and wait(0.75) do
			if C()['Auto Death Step'] then
				if not UsedKey and SecondSea then
					UsedKey = _C("OpenLibrary")
					DeathStepBossAttacked = UsedKey
					if not __f['Monster']("Awakened Ice Admiral") and C()['Auto Sharkman Karate'] and not SharkmanBossAttacked then 
						NoDeathStepBoss = true
						continue
					end
					if ((LocalPlayer.Data.Level.Value > 1100 and not C()['Auto Farm Level']) or (LocalPlayer.Data.Level.Value >= 1500)) and not __f['Monster']("Awakened Ice Admiral") then
						Serverhop("Auto DeathStep")
					end
					if __f['Monster']("Awakened Ice Admiral") then
						__f['Kill'](__f['Monster']("Awakened Ice Admiral"), function()
							return not C()['Auto Death Step']
						end)
					end
					if __f['hasItem']("Library Key") then
						UsedKey = _C("OpenLibrary")
					end
				elseif UsedKey and (Finished.ElecticClaw or not C()['Auto Electric Claw'] or SecondSea) and (Finished.Superhuman or not C()['Auto Superhuman']) then
					local Success,Data = true
					if not MasteryData.DeathStep then
						Success,Data = pcall(_C,"BuyBlackLeg")
					else
						Data = MasteryData.DeathStep
					end
					if not __f['GetToolFromTip']("Black Leg",true) then continue end
					if type(Data) == "number" and (Data == 1 or Data == 2 or Data > 100) and (MasteryData.DeathStep or __f['GetToolFromTip']("Black Leg",true):WaitForChild("Level").Value) >= 400 then	
						MasteryData.DeathStep = 400
						if SecondSea and C()['Enabled Zou Quest'] then
							Finished.DeathStep = true
						end
						if LocalPlayer.Data.Fragments.Value >= 5000 and not __f['IsRaiding']() then
							ForceRaid = false
							if __f['purchaseCombat']("DeathStep") then
								Finished.DeathStep = true
								wait()
								pcall(EquipBest)
								break
							end
						elseif not C()['Enabled Zou Quest'] or not SecondSea then
							ForceRaid = true
						end
					end
				end
			end
		end
	end)
end
Func['Auto Electric Claw'] = function()
	task.spawn(function()
		local Success,Data = pcall(_C,"BuyElectricClaw",not LaunchedSuccessfully)
		if Success then
			if Data == 1 or Data == 2 then 
				Finished.ElecticClaw = true
				wait()
				return 
			end
		end
		while C()['Auto Electric Claw'] and wait(0.5) do
			if not ThirdSea then Finished.ElecticClaw = true break end
			if C()['Auto Electric Claw'] and (Finished.Superhuman or not C()['Auto Superhuman']) then
				if not __f['checkIsAvailable']("BuyElectro",400) then continue end
				local Tool = __f['GetToolFromTip']("Electro",true)
				if Tool and type(Data) == "number" and (MasteryData.Electro or Tool.Level.Value) >= 400 and not __f['IsRaiding']() then
					MasteryData.Electro = 400
					if not ThirdSea then
						Finished.ElecticClaw = true
					end
					if _C("BuyElectricClaw",true) ~= 4 then
						if Client.Data.Fragments.Value >= 5000 and not __f['IsRaiding']() then
							if LocalPlayer.Data.Beli.Value >= tonumber"3e+6" then
								ForceRaid = false
								if __f['purchaseCombat']("ElectricClaw") then
									if Data == 1 or Data == 2 then
										Finished.ElecticClaw = true
										wait()
										break
									end
								end
							end
						else
							ForceRaid = true
						end
					else
						_C("BuyElectricClaw","Start")
						_C("requestEntrance",Vector3.new(-12462, 375, -7552))
					end
				end
			end
		end
	end)
end
Func['Auto Dragon Talon'] = function()
	if not ThirdSea then return end
	task.spawn(function()
		BoneBuys = 0
		local Success,Data = pcall(_C,"BuyDragonTalon",not LaunchedSuccessfully)
		if Data == 1 or Data == 2 then
			wait()
			Finished.DragonTalon = true
			return
		end
		while C()['Auto Dragon Talon'] and wait(0.5) do
			if not ThirdSea then break end
			if C()['Auto Dragon Talon'] and (Finished.TrueSharkmanKarate or not SharkmanBossAttacked or not C()['Auto Sharkman Karate']) and (Finished.DeathStep or not DeathStepBossAttacked or not C()['Auto Death Step']) and (Finished.Superhuman or not C()['Auto Superhuman']) and (Finished.ElecticClaw or not C()['Auto Electric Claw']) then
				local Success,Data = true
				if not MasteryData.ElecticClaw then
					Success,Data = pcall(_C,"BlackbeardReward","DragonClaw","2")
				else
					Success = true
					Data = 1
				end
				if not __f['GetToolFromTip']("Dragon Claw",true) then continue end
				if type(Data) == "number" and (Data == 1 or Data == 2 or (Data or 0) > 100) and (MasteryData.DragonClaw or __f['GetToolFromTip']("Dragon Claw",true):WaitForChild("Level").Value) >= 400 then
					MasteryData.DragonClaw = 400
					if LocalPlayer.Data.Fragments.Value >= 5000 and not IsRaiding() then
						ForceRaid = false
						if FireES then
							_C("BuyDragonTalon",1)
							if _C("BuyDragonTalon") == 1 or _C("BuyDragonTalon") == 2 then
								_C("BuyDragonTalon")
								Finished.DragonTalon = true
								wait()
								pcall(EquipBest)
								break
							end
						else
							_C("Bones","Buy",1,1)
							BoneBuys = BoneBuys + 1
						end
					else
						ForceRaid = true
					end
				end
			end
		end
	end)
end

task.spawn(function()
	local gg = getrawmetatable(game)
	local old = gg.__namecall
	setreadonly(gg,false)
	gg.__namecall = newcclosure(function(...)
		local method = getnamecallmethod()
		local args = {...}
		if tostring(method) == "FireServer" then
			if tostring(args[1]) == "RemoteEvent" then
				if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
					if UseSkillMasteryDevilFruit and (C()['Farm Fruit Mastery'] or C()['Farm Fruit Mastery Bone'] or C()['Farm Fruit Mastery Cake']) then
						if type(args[2]) == "vector" then 
							args[2] = PositionSkillMasteryDevilFruit
						else
							args[2] = CFrame.new(PositionSkillMasteryDevilFruit)
						end
						return old(unpack(args))
					end
					if AimbotSkill and SelectAimbotMode == "Fov" then
						args[2] = _G.Aim_Players[Character.HumanoidRootPart.Position]
						return old(unpack(args))
					elseif AimbotSkill and SelectAimbotMode == "Automatic" then
						args[2] = _G.Aim_Select_Players[Character.HumanoidRootPart.Position]
						return old(unpack(args))
					end
				end
			end
		end
		return old(...)
	end)
end)

task.spawn(function()
	while wait() do
		for i,v in pairs(LocalPlayer.Backpack:GetChildren()) do  
			if v:IsA("Tool") then
				if v:FindFirstChild("RemoteFunctionShoot") then 
					SelectWeaponGun = v.Name
				end
			end
		end
	end
end)

task.spawn(function()
	local gt = getrawmetatable(game)
	local old = gt.__namecall
	setreadonly(gt,false)
	gt.__namecall = newcclosure(function(...)
		local args = {...}
		if getnamecallmethod() == "InvokeServer" then 
			if SelectWeaponGun then
				if SelectWeaponGun == "Soul Guitar" then
					if tostring(args[2]) == "TAP" then
						if (C()['Farm Gun Mastery'] or C()['Farm Gun Mastery Bone'] or C()['Farm Gun Mastery Cake']) and UseSkillMasteryGun then
							args[3] = PositionSkillMasteryGun
						end
					end
				end
			end
		end
		return old(unpack(args))
	end)
	setreadonly(gt,true)
end)

local env = (getgenv or getrenv or getfenv)()
local rs = game:GetService("ReplicatedStorage")
local players = game:GetService("Players")
local client = players.LocalPlayer
local modules = rs:WaitForChild("Modules")
local net = modules:WaitForChild("Net")
local charFolder = workspace:WaitForChild("Characters")
local enemyFolder = workspace:WaitForChild("Enemies")

local Module = {
    AttackCooldown = tick()
}
local CachedChars = {}

-- ตรวจสอบว่ามีชีวิตอยู่มั้ย
function Module.IsAlive(Char: Model?): boolean
    if not Char then return false end
    local Hum = CachedChars[Char] or Char:FindFirstChildOfClass("Humanoid")
    if Hum then
        CachedChars[Char] = Hum
        return Hum.Health > 0
    end
    return false
end

-- ตั้งค่า
local Settings = {
    ClickDelay = 0.01,
    AutoClick = true,
    AttackDistance = 70,
    AttackPlayers = true
}

Module.FastAttack = (function()
    if not C()["Fast Attack"] then return end
    if env._trash_attack then return env._trash_attack end

    local AttackModule = {
        Distance = Settings.AttackDistance,
        FirstAttack = false
    }

    local RegisterAttack = net:WaitForChild("RE/RegisterAttack")
    local RegisterHit = net:WaitForChild("RE/RegisterHit")

    -- ฟังก์ชันโจมตี 1 ตัว
    function AttackModule:AttackEnemy(Enemy, Limb)
        if Enemy and Limb and client:DistanceFromCharacter(Limb.Position) < self.Distance then
            if not self.FirstAttack then
                RegisterAttack:FireServer(Settings.ClickDelay or 0)
                self.FirstAttack = true
            end
            RegisterHit:FireServer(Limb, {Enemy, Limb})
        end
    end

    -- ฟังก์ชันหาศัตรูใกล้ ๆ
    function AttackModule:AttackNearest()
        for _, Enemy in ipairs(enemyFolder:GetChildren()) do
            if Module.IsAlive(Enemy) then
                local part = Enemy:FindFirstChild("UpperTorso") or Enemy:FindFirstChild("HumanoidRootPart")
                self:AttackEnemy(Enemy, part)
            end
        end

        if Settings.AttackPlayers then
            for _, Char in ipairs(charFolder:GetChildren()) do
                if Char ~= client.Character and Module.IsAlive(Char) then
                    local part = Char:FindFirstChild("UpperTorso") or Char:FindFirstChild("HumanoidRootPart")
                    self:AttackEnemy(Char, part)
                end
            end
        end
    end

    function AttackModule:BladeHits()
        self:AttackNearest()
        self.FirstAttack = false
    end

    -- loop หลัก
    task.spawn(function()
        while task.wait(Settings.ClickDelay or 0) do
            if not C()["Fast Attack"] then continue end
            if not Settings.AutoClick then continue end
            if not Module.IsAlive(client.Character) then continue end
            if not client.Character:FindFirstChildOfClass("Tool") then continue end

            AttackModule:BladeHits()
        end
    end)

    env._trash_attack = AttackModule
    return AttackModule
end)()

task.spawn(function()
	while task.wait() do
		pcall(function()
			if C()["Fast Attack"] then
				for i, v in next, workspace.Enemies:GetChildren() do
					if v.Humanoid.Health > 0 and v:FindFirstChild("HumanoidRootPart") and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= tonumber(60) then
						game:GetService("ReplicatedStorage"):WaitForChild("Modules"):WaitForChild("Net"):WaitForChild("RE/RegisterAttack"):FireServer(0)
						local args = {
							[1] = v:FindFirstChild("HumanoidRootPart"),
							[2] = {}
						}
						for _, e in next, workspace:WaitForChild("Enemies"):GetChildren() do
							if e:FindFirstChild("Humanoid") and e.Humanoid.Health > 0 then
								table.insert(args[2], {
									[1] = e,
									[2] = e:FindFirstChild("HumanoidRootPart") or e:FindFirstChildOfClass("BasePart")
								})
							end
						end
						game:GetService("ReplicatedStorage"):WaitForChild("Modules"):WaitForChild("Net"):WaitForChild("RE/RegisterHit"):FireServer(unpack(args))
					end
				end
			end
		end)
	end
end)

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer

local Net = ReplicatedStorage:WaitForChild("Modules"):WaitForChild("Net")
local RegisterHit = Net:WaitForChild("RE/RegisterHit")
local RegisterAttack = Net:WaitForChild("RE/RegisterAttack")
local ShootGunEvent = Net:WaitForChild("RE/ShootGunEvent")

local HIT_FUNCTION
local PlayerScripts = LocalPlayer:WaitForChild("PlayerScripts")
local LocalScript = PlayerScripts:FindFirstChildOfClass("LocalScript")
while not LocalScript do
	LocalPlayer.PlayerScripts.ChildAdded:Wait()
	LocalScript = PlayerScripts:FindFirstChildOfClass("LocalScript")
end

if getsenv then
	pcall(function()
		local success, env = pcall(getsenv, LocalScript)
		if success and env then
			HIT_FUNCTION = env._G.SendHitsToServer
		end
	end)
end

-- ฟังก์ชันตรวจเป้าหมาย Valid
local function GetValidTargets(source)
	local targets = {}
	for _, entity in ipairs(source) do
		local humanoid = entity:FindFirstChild("Humanoid")
		local part = entity:FindFirstChild("HumanoidRootPart") or entity:FindFirstChildOfClass("BasePart")
		if humanoid and part and humanoid.Health > 0 then
			table.insert(targets, {entity, part})
		end
	end
	return targets
end

-- ฟังก์ชันโจมตีเป้าหมาย
local function attackEnemies(enemyTarget)
	local plr = LocalPlayer
	if not plr.Character then return end
	local rootPart = plr.Character:FindFirstChild("HumanoidRootPart")
	local toolEquipped = plr.Character:FindFirstChildOfClass("Tool")
	if not rootPart or not toolEquipped or not enemyTarget then return end

	local distance = (enemyTarget.Position - rootPart.Position).Magnitude
	if distance > 55 then return end

	if (toolEquipped.ToolTip == "Melee" or toolEquipped.ToolTip == "Sword") and not _G.RaidAura then
		RegisterAttack:FireServer(0)
		RegisterHit:FireServer(enemyTarget, {})
	end

	if toolEquipped.ToolTip == "Gun" and not _G.RaidAura then
		ShootGunEvent:FireServer(enemyTarget.Position, {[1] = enemyTarget})
	end
end

-- ฟังก์ชันโจมตีทุกเป้าหมาย
local function AttackNoCD()
	local plr = LocalPlayer
	local rootPart = plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")
	if not rootPart then return end

	for _, enemy in ipairs(workspace.Enemies:GetChildren()) do
		local hrp = enemy:FindFirstChild("HumanoidRootPart")
		if hrp then attackEnemies(hrp) end
	end

	for _, playerChar in ipairs(workspace.Characters:GetChildren()) do
		if playerChar.Name ~= plr.Name then
			local hrp = playerChar:FindFirstChild("HumanoidRootPart")
			if hrp then attackEnemies(hrp) end
		end
	end
end

-- Loop หลักโจมตีแบบ No CD
spawn(function()
	while true do task.wait()
		if C()["Fast Attack"] then
			pcall(function()
				AttackNoCD()

				-- ยิงและ Hit Combo สำหรับ Blade / Boss / Raid
				for _, enemy in ipairs(workspace.Enemies:GetChildren()) do
					local hrp = enemy:FindFirstChild("HumanoidRootPart")
					if hrp and enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 then
						local times = 6
						if enemy:GetAttribute("IsBoss") then times = 25
						elseif enemy:GetAttribute("RaidBoss") then times = 40 end

						local bladeHits = {}
						table.insert(bladeHits, {enemy, hrp})
						table.insert(bladeHits, math.random())

						local overheat = 0
						while overheat <= 0.4 do
							for i = 1, times do
								RegisterAttack:FireServer(0)
								if HIT_FUNCTION then
									HIT_FUNCTION(hrp, bladeHits)
								else
									RegisterHit:FireServer(hrp, bladeHits)
								end
							end
							overheat += task.wait(times > 10 and 0.07 or 0)
						end
					end
				end
			end)
		end
	end
end)

local _ENV = (getgenv or getrenv or getfenv)()

local Connections = {}

local ReplicatedStorage: ReplicatedStorage = game:GetService("ReplicatedStorage")
local Modules: Folder? = ReplicatedStorage:WaitForChild("Modules")
local Net: ModuleScript = Modules:WaitForChild("Net")
local Players: Players = game:GetService("Players")
local Player = Players.LocalPlayer
local VirtualInputManager: VirtualInputManager = game:GetService("VirtualInputManager")
local SeaBeasts: Folder = workspace:WaitForChild("SeaBeasts")
local Boats: Folder = workspace:WaitForChild("Boats")

local Remotes = ReplicatedStorage:WaitForChild("Remotes")
local getupvalue: (any, number) -> any = getupvalue or (debug and debug.getupvalue)
local GunValidator: RemoteEvent = Remotes:WaitForChild("Validator2")
local Characters: Folder = workspace:WaitForChild("Characters")
local Enemies: Folder = workspace:WaitForChild("Enemies")

local RunService: RunService = game:GetService("RunService")
local Stepped = RunService.Stepped

local Module = {}

local HIDDEN_SETTINGS: { [string]: any } = {
	SKILL_COOLDOWN = 0.5,
	CLEAR_AFTER = 50
}

local function CreateNewClear()
	local COUNT_NEWINDEX = 0

	return {
		__newindex = function(self, index, value)
			if COUNT_NEWINDEX >= HIDDEN_SETTINGS.CLEAR_AFTER then
				for key, cache in pairs(self) do
					if typeof(cache) == "Instance" and not cache:IsDescendantOf(game) then
						rawset(self, key, nil)
					end
				end
				COUNT_NEWINDEX = 0
			end

			COUNT_NEWINDEX += 1
			return rawset(self, index, value)
		end
	}
end

local function CheckPlayerAlly(__Player: Player): boolean
	if tostring(__Player.Team) == "Marines" and __Player.Team == Player.Team then
		return false
	elseif __Player:HasTag(`Ally{Player.Name}`) or Player:HasTag(`Ally{__Player.Name}`) then
		return false
	end

	return true
end


local Cached = {
	Closest = nil,
	Equipped = nil,
	Humanoids = setmetatable({}, CreateNewClear()),
	Enemies = {}, -- setmetatable({}, CreateNewClear()),
	Progress = {},
	Bring = {},
	Tools = {}
}

Module.Cached = Cached
Module.AttackCooldown = tick()


function Module.IsAlive(Character)
	if Character then
		local Humanoids = Cached.Humanoids
		local Parent = Character.Parent
		local Humanoid = Humanoids[Character] or Character:FindFirstChild(if Parent == SeaBeasts then "Health" else "Humanoid")

		if Humanoid then
			if not Humanoids[Character] then
				Humanoids[Character] = Humanoid
			end

			return Humanoid[if Humanoid.ClassName == "Humanoid" then "Health" else "Value"] > 0
		end

		return Parent == Boats
	end
end

Module.FastAttack = (function()
	local FastAttack = {
		Distance = 50,
		attackMobs = true,
		attackPlayers = true,
		Equipped = nil,
		Debounce = 0,
		ComboDebounce = 0,
		ShootDebounce = 0,
		M1Combo = 0,

		Overheat = {
			["Dragonstorm"] = {
				MaxOverheat = 3,
				Cooldown = 0,
				TotalOverheat = 0,
				Distance = 350,
				Shooting = false
			}
		},
		ShootsPerTarget = {
			["Dual Flintlock"] = 2
		},
		SpecialShoots = {
			["Skull Guitar"] = "TAP",
			["Bazooka"] = "Position",
			["Cannon"] = "Position",
			["Dragonstorm"] = "Overheat"
		},
		HitboxLimbs = {"RightLowerArm", "RightUpperArm", "LeftLowerArm", "LeftUpperArm", "RightHand", "LeftHand"}
	}

	local RE_RegisterAttack = Net:WaitForChild("RE/RegisterAttack")
	local RE_ShootGunEvent = Net:WaitForChild("RE/ShootGunEvent")
	local RE_RegisterHit = Net:WaitForChild("RE/RegisterHit")
	local Events = ReplicatedStorage:WaitForChild("Events")

	local SUCCESS_FLAGS, COMBAT_REMOTE_THREAD = pcall(function()
		return require(Modules.Flags).COMBAT_REMOTE_THREAD or false
	end)

	local SUCCESS_SHOOT, SHOOT_FUNCTION = pcall(function()
		return getupvalue(require(ReplicatedStorage.Controllers.CombatController).Attack, 9)
	end)

	local HIT_FUNCTION; task.defer(function()
		local PlayerScripts = Player:WaitForChild("PlayerScripts")
		local LocalScript = PlayerScripts:FindFirstChildOfClass("LocalScript")

		while not LocalScript do
			Player.PlayerScripts.ChildAdded:Wait()
			LocalScript = PlayerScripts:FindFirstChildOfClass("LocalScript")
		end

		if getsenv then
			local Success, ScriptEnv = pcall(getsenv, LocalScript)

			if Success and ScriptEnv then
				HIT_FUNCTION = ScriptEnv._G.SendHitsToServer
			end
		end
	end)

	local IsAlive = Module.IsAlive

	FastAttack.ShootsFunctions = {
		["Skull Guitar"] = function(self: FastAttack, Equipped: Tool, Position: Vector3)
			Equipped.RemoteEvent:FireServer("TAP", Position) -- Events.ShootSoulGuitar:Invoke(Position)
		end
	}

	local function ExpandsHitBox(Enemies)
		for i = 1, #Enemies do
			Enemies[i][2].Size = Vector3.one * 50
			Enemies[i][2].Transparency = 1
		end
	end

	function FastAttack:ShootInTarget(TargetPosition: Vector3): (nil)
		local Equipped = IsAlive(Player.Character) and Player.Character:FindFirstChildOfClass("Tool")

		if Equipped and Equipped.ToolTip == "Gun" then
			if Equipped:FindFirstChild("Cooldown") and (tick() - self.ShootDebounce) >= Equipped.Cooldown.Value then
				if self.ShootsFunctions[Equipped.Name] then
					return self.ShootsFunctions[Equipped.Name](self, Equipped, TargetPosition)
				end

				if SUCCESS_SHOOT and SHOOT_FUNCTION then
					local ShootType = self.SpecialShoots[Equipped.Name] or "Normal"

					if ShootType == "Position" or (ShootType == "TAP" and Equipped:FindFirstChild("RemoteEvent")) then
						Equipped:SetAttribute("LocalTotalShots", (Equipped:GetAttribute("LocalTotalShots") or 0) + 1)
						GunValidator:FireServer(self:GetValidator2())

						if ShootType == "TAP" then
							Equipped.RemoteEvent:FireServer("TAP", TargetPosition)
						else
							RE_ShootGunEvent:FireServer(TargetPosition)
						end

						self.ShootDebounce = tick()
					end
				else
					VirtualInputManager:SendMouseButtonEvent(0, 0, 0, true, game, 1);task.wait(0.05)
					VirtualInputManager:SendMouseButtonEvent(0, 0, 0, false, game, 1);task.wait(0.05)
					self.ShootDebounce = tick()
				end
			end
		end
	end

	function FastAttack:CheckStun(ToolTip: string, Character: Character, Humanoid: Humanoid): boolean
		local Stun = Character:FindFirstChild("Stun")
		local Busy = Character:FindFirstChild("Busy")

		if Humanoid.Sit and (ToolTip == "Sword" or ToolTip == "Melee" or ToolTip == "Gun") then
			return false
			-- elseif Stun and Stun.Value > 0 then {{ or Busy and Busy.Value }}
			--	 return false
		end

		return true
	end

	function FastAttack:Process(assert: boolean, Enemies: Folder, BladeHits: table, Position: Vector3, Distance: number): (nil)
		if not assert then return end

		local HitboxLimbs = self.HitboxLimbs
		local Mobs = Enemies:GetChildren()

		for i = 1, #Mobs do
			local Enemy = Mobs[i]
			local BasePart = Enemy:FindFirstChild(HitboxLimbs[math.random(#HitboxLimbs)]) or Enemy.PrimaryPart

			if not BasePart then continue end

			local CanAttack = Enemy.Parent == Characters and CheckPlayerAlly(Players:GetPlayerFromCharacter(Enemy))

			if Enemy ~= Player.Character and (Enemy.Parent ~= Characters or CanAttack) then
				if IsAlive(Enemy) and (Position - BasePart.Position).Magnitude <= Distance then
					if not self.EnemyRootPart then
						self.EnemyRootPart = BasePart
					else
						table.insert(BladeHits, { Enemy, BasePart })
					end
				end
			end
		end
	end

	function FastAttack:GetAllBladeHits(Character: Character, Distance: number?): (nil)
		local Position = Character:GetPivot().Position
		local BladeHits = {}
		Distance = Distance or self.Distance

		self:Process(self.attackMobs, Enemies, BladeHits, Position, Distance)
		self:Process(self.attackPlayers, Characters, BladeHits, Position, Distance)

		return BladeHits
	end

	function FastAttack:GetClosestEnemy(Character: Character, Distance: number?): (nil)
		local BladeHits = self:GetAllBladeHits(Character, Distance)

		local Distance, Closest = math.huge

		for i = 1, #BladeHits do
			local Magnitude = if Closest then (Closest.Position - BladeHits[i][2].Position).Magnitude else Distance

			if Magnitude <= Distance then
				Distance, Closest = Magnitude, BladeHits[i][2]
			end
		end

		return Closest
	end

	function FastAttack:GetGunHits(Character: Character, Distance: number?)
		local BladeHits = self:GetAllBladeHits(Character, Distance)
		local GunHits = {}

		for i = 1, #BladeHits do
			if not GunHits[1] or (BladeHits[i][2].Position - GunHits[1].Position).Magnitude <= 10 then
				table.insert(GunHits, BladeHits[i][2])
			end
		end

		return GunHits
	end

	function FastAttack:GetCombo(): number
		local Combo = if tick() - self.ComboDebounce <= 0.4 then self.M1Combo else 0
		Combo = if Combo >= 4 then 1 else Combo + 1

		self.ComboDebounce = tick()
		self.M1Combo = Combo

		return Combo
	end

	function FastAttack:UseFruitM1(Character: Character, Equipped: Tool, Combo: number): (nil)
		if self.UsingM1 then return end

		local M1Active = Equipped:FindFirstChild("M1Active")
		local Position = Character:GetPivot().Position
		local EnemyList = Enemies:GetChildren()

		for i = 1, #EnemyList do
			local Enemy = EnemyList[i]
			local PrimaryPart = Enemy.PrimaryPart
			if IsAlive(Enemy) and PrimaryPart and (PrimaryPart.Position - Position).Magnitude <= 50 then
				local Direction = (PrimaryPart.Position - Position).Unit
				Equipped.LeftClickRemote:FireServer(Direction, Combo)
			end
		end
	end

	function FastAttack:UseNormalClick(Humanoid: Humanoid, Character: Character, Cooldown: number): (nil)
		self.EnemyRootPart = nil
		local BladeHits = self:GetAllBladeHits(Character)
		local EnemyHitBox = self.EnemyRootPart

		if EnemyHitBox then
			if SUCCESS_FLAGS and COMBAT_REMOTE_THREAD and HIT_FUNCTION then
				RE_RegisterAttack:FireServer(Cooldown)
				HIT_FUNCTION(EnemyHitBox, BladeHits)
			elseif SUCCESS_FLAGS and not COMBAT_REMOTE_THREAD then
				RE_RegisterAttack:FireServer(Cooldown)
				RE_RegisterHit:FireServer(EnemyHitBox, BladeHits)
			else
				table.insert(BladeHits, { Enemy, EnemyHitBox })
				ExpandsHitBox(BladeHits)

				VirtualInputManager:SendMouseButtonEvent(0, 0, 0, true, game, 1);task.wait(0)
				VirtualInputManager:SendMouseButtonEvent(0, 0, 0, false, game, 1)
			end
		end
	end

	function FastAttack:GetValidator2()
		local v1 = getupvalue(SHOOT_FUNCTION, 15) -- v40, 15
		local v2 = getupvalue(SHOOT_FUNCTION, 13) -- v41, 13
		local v3 = getupvalue(SHOOT_FUNCTION, 16) -- v42, 16
		local v4 = getupvalue(SHOOT_FUNCTION, 17) -- v43, 17
		local v5 = getupvalue(SHOOT_FUNCTION, 14) -- v44, 14
		local v6 = getupvalue(SHOOT_FUNCTION, 12) -- v45, 12
		local v7 = getupvalue(SHOOT_FUNCTION, 18) -- v46, 18

		local v8 = v6 * v2									-- v133
		local v9 = (v5 * v2 + v6 * v1) % v3 -- v134

		v9 = (v9 * v3 + v8) % v4
		v5 = math.floor(v9 / v3)
		v6 = v9 - v5 * v3
		v7 = v7 + 1

		setupvalue(SHOOT_FUNCTION, 15, v1) -- v40, 15
		setupvalue(SHOOT_FUNCTION, 13, v2) -- v41, 13
		setupvalue(SHOOT_FUNCTION, 16, v3) -- v42, 16
		setupvalue(SHOOT_FUNCTION, 17, v4) -- v43, 17
		setupvalue(SHOOT_FUNCTION, 14, v5) -- v44, 14
		setupvalue(SHOOT_FUNCTION, 12, v6) -- v45, 12
		setupvalue(SHOOT_FUNCTION, 18, v7) -- v46, 18

		return math.floor(v9 / v4 * 16777215), v7
	end

	function FastAttack:UseGunShoot(Character, Equipped)
		if not Equipped.Enabled then return end

		local ShootType = self.SpecialShoots[Equipped.Name] or "Normal"

		if ShootType == "Normal" or ShootType == "Overheat" then
			if ShootType == "Overheat" then
				local Data = self.Overheat[Equipped.Name]

				if Data.Shooting then
					return nil
				end

				local Target = self:GetClosestEnemy(Character, Data.Distance or 100)

				if Target then
					Data.Shooting = true

					while Equipped and Equipped.Parent == Player.Character and Data.TotalOverheat < Data.MaxOverheat do
						if Target and Target.Parent and IsAlive(Target.Parent) then
							Equipped:SetAttribute("LocalTotalShots", (Equipped:GetAttribute("LocalTotalShots") or 0) + 1)
							GunValidator:FireServer(self:GetValidator2())
							RE_ShootGunEvent:FireServer(Target.Position, { Target })
							Data.TotalOverheat += task.wait(Data.Cooldown)
						else
							break
						end
					end

					while Data.TotalOverheat > 0 do
						Data.TotalOverheat = math.clamp(Data.TotalOverheat - task.wait(), 0, Data.MaxOverheat)
					end

					Data.Shooting = false
				end
			else
				local Hits = self:GetGunHits(Character, 120)
				local Target = Hits[1] and Hits[1].Position

				if Target then
					Equipped:SetAttribute("LocalTotalShots", (Equipped:GetAttribute("LocalTotalShots") or 0) + 1)
					GunValidator:FireServer(self:GetValidator2())

					for i = 1, (self.ShootsPerTarget[Equipped.Name] or 1) do
						RE_ShootGunEvent:FireServer(Target, Hits)
					end
				end
			end
		elseif ShootType == "Position" or (ShootType == "TAP" and Equipped:FindFirstChild("RemoteEvent")) then
			local Target = self:GetClosestEnemy(Character, 200)

			if Target then
				if self.ShootsFunctions[Equipped.Name] then
					return self.ShootsFunctions[Equipped.Name](self, Equipped, Target.Position)
				end

				Equipped:SetAttribute("LocalTotalShots", (Equipped:GetAttribute("LocalTotalShots") or 0) + 1)
				GunValidator:FireServer(self:GetValidator2())

				if ShootType == "TAP" then
					Equipped.RemoteEvent:FireServer("TAP", Target.Position)
				else
					RE_ShootGunEvent:FireServer(Target.Position)
				end
			end
		end
	end

	function FastAttack.attack()
		if not C()["Fast Attack"] or (tick() - Module.AttackCooldown) <= 0 then return end
		if not IsAlive(Player.Character) then return end

		local self = FastAttack
		local Character = Player.Character
		local Humanoid = Character.Humanoid

		local Equipped = Character:FindFirstChildOfClass("Tool")
		local ToolTip = Equipped and Equipped.ToolTip
		local ToolName = Equipped and Equipped.Name

		if not Equipped or (ToolTip ~= "Gun" and ToolTip ~= "Melee" and ToolTip ~= "Blox Fruit" and ToolTip ~= "Sword") then
			return nil
		end

		local Cooldown = Equipped:FindFirstChild("Cooldown") and Equipped.Cooldown.Value or 0

		if (tick() - self.Debounce) >= Cooldown and self:CheckStun(ToolTip, Character, Humanoid) then
			local Combo = self:GetCombo()
			Cooldown += if Combo >= 4 then 0.05 else 0

			self.Equipped = Equipped
			self.Debounce = if Combo >= 4 and ToolTip ~= "Gun" then (tick() + 0.05) else tick()

			if ToolTip == "Blox Fruit" then
				if ToolName == "Ice-Ice" or ToolName == "Light-Light" then
					return self:UseNormalClick(Humanoid, Character, Cooldown)
				elseif Equipped:FindFirstChild("LeftClickRemote") then
					return self:UseFruitM1(Character, Equipped, Combo)
				end
			elseif ToolTip == "Gun" then
				if SUCCESS_SHOOT and SHOOT_FUNCTION and C()["Fast Attack"] then
					return self:UseGunShoot(Character, Equipped)
				end
			else
				return self:UseNormalClick(Humanoid, Character, Cooldown)
			end
		end
	end

	table.insert(Connections, Stepped:Connect(FastAttack.attack))

	task.spawn(function()
		while task.wait() do
			if (tick() - Module.AttackCooldown) < 0 then continue end
			if not C()["Fast Attack"] then continue end
			FastAttack.attack()
		end
	end)

	return FastAttack
end)()

spawn(function()
	local rs = game:GetService("RunService")
	rs.RenderStepped:Connect(function()
		if C()["Fast Attack"] then
			pcall(Attack)
		end
	end)
end)

local Window = Fluent:CreateWindow{
	Title = "Astromy Hub Premium",
	SubTitle = "By x1nxwny - discord.gg/dqb2nsfD9d",
	TabWidth = 160,
	Size = UDim2.fromOffset(550, 420),
	Acrylic = false, 
	Theme = "Astromy Theme 5",
	MinimizeKey = Enum.KeyCode.LeftControl 
}

local Tabs = {
	['Genaral'] = Window:AddTab({ Title = "Genaral", Icon = "" }),
	['Farm'] = Window:AddTab({ Title = "Farm", Icon = "" }),
	['Items'] = Window:AddTab({ Title = "Items", Icon = "" }),
	['Stats'] = Window:AddTab({ Title = "Stats", Icon = "" }),
	['Visuals'] = Window:AddTab({ Title = "Visuals", Icon = "" }),
	['Shop'] = Window:AddTab({ Title = "Shop", Icon = "" }),
	['Settings'] = Window:AddTab({ Title = "Settings", Icon = "settings" })
}

local Options = Fluent.Options

function Toggle(tabs, title, funcs)
	local Toggle = Tabs[tabs]:AddToggle(title, {
		Title = title,
		Default = C()[funcs]
	})
	Toggle:OnChanged(function(v)
		save(funcs,v)
		if Func[funcs] then
			task.spawn(Func[funcs])
		end
	end)
	return Toggle
end

function Dropdown(tabs, title, multi, values, funcs)
	local Dropdown = Tabs[tabs]:AddDropdown(title, {
		Title = title,
		Values = values,
		Multi = multi or false,
		Default = C()[funcs],
	})

	Dropdown:OnChanged(function(v)
		save(funcs,v)
	end)

	return Dropdown
end

function Slider(tabs, title, min, max, def, funcs)
	local Slider = Tabs[tabs]:AddSlider(title, {
		Title = title,
		Description = nil,
		Default = C()[funcs] or def,
		Min = min,
		Max = max,
		Rounding = 1,
	})

	Slider:OnChanged(function(v)
		save(funcs,v)
	end)

	return Slider
end

Tabs['Genaral']:AddSection("Main Section")

Toggle('Genaral',"Auto Farm Level","Auto Farm Level")
Toggle('Genaral',"Enabled Dressrosa Quest","Enabled Dressrosa Quest")
Toggle('Genaral',"Enabled Zou Quest","Enabled Zou Quest")

Tabs['Genaral']:AddSection("Boss Section")

local Boss_Spawn = Tabs['Genaral']:AddParagraph({
    Title = "Name : Status :",
    Content = "Check boss spawn"
})

spawn(function()
	while task.wait() do 
		if __f['Monster'](C()['Select Boss']) then 
			Boss_Spawn:SetTitle("Name : ".. C()['Select Boss'] .. " Status : Spawn 🟢")
		else
			Boss_Spawn:SetTitle("Name : ".. C()['Select Boss'] .. " Status : Not Spawn 🔴")
		end 
	end 
end)

local BossTable = {}   
for i,v in pairs(Mon) do
	table.insert(BossTable, v)
end

Dropdown('Genaral',"Select Boss",false,BossTable,"Select Boss")
Toggle('Genaral',"Auto Farm Boss","Auto Farm Boss")
Toggle('Genaral',"Enabled Quest Boss","Enabled Quest Boss")
Toggle('Genaral',"Enabled Hop","Auto Farm Boss Hop")

Tabs['Genaral']:AddSection("Mastery Section")

Toggle('Genaral',"Farm Fruit Mastery","Farm Fruit Mastery")
Toggle('Genaral',"Farm Gun Mastery","Farm Gun Mastery")
Tabs['Genaral']:AddSection("")
Toggle('Genaral',"Farm Fruit Mastery (Bone)","Farm Fruit Mastery Bone")
Toggle('Genaral',"Farm Gun Mastery (Bone)","Farm Gun Mastery Bone")
Tabs['Genaral']:AddSection("")
Toggle('Genaral',"Farm Fruit Mastery (Cake Pirates)","Farm Fruit Mastery Cake")
Toggle('Genaral',"Farm Gun Mastery (Cake Pirates)","Farm Gun Mastery Cake")
Slider('Genaral',"Kill At %",1,100,30,"Kill At")

Tabs['Genaral']:AddSection("Sword Mastery")

Dropdown('Genaral',"Select Farm Mode",false,{"Level Farm","Bone Farm","Cake Farm"},"Select Farm Mode")
Toggle('Genaral',"Farm All Sword Mastery","Farm All Sword Mastery")

Tabs['Genaral']:AddSection("Settings Mastery")

Toggle('Genaral',"Skill Z","Skill Z")
Toggle('Genaral',"Skill X","Skill X")
Toggle('Genaral',"Skill C","Skill C")
Toggle('Genaral',"Skill V","Skill V")

Tabs['Farm']:AddSection("Material Section")

Dropdown('Farm',"Select Material",false,AllMaterial,"Select Material")
Toggle('Farm',"Auto Farm Material","Auto Farm Material")

if SecondSea then 
Tabs['Farm']:AddSection("Quest Section")

Toggle('Farm',"Auto Bartlio Quest","Auto Bartlio Quest")
Toggle('Farm',"Auto Don Swan Quest","Auto Don Swan Quest")

Tabs['Farm']:AddSection("Ectoplasm Section")

local Ectoplasm_Check = Tabs['Farm']:AddParagraph({
    Title = "Ectoplasm Total",
    Content = "Check ectoplasm total"
})

spawn(function()
	while task.wait() do 
		Ectoplasm_Check:SetTitle("Ectoplasm Total : ".. _C("Ectoplasm","Check"))
	end 
end)

Toggle('Farm',"Auto Farm Ectoplasm","Auto Farm Ectoplasm")
Toggle('Farm',"Auto Midnight Blade","Auto Midnight Blade")
end 

Tabs['Items']:AddSection("Fighting Style")

Toggle('Items',"Auto Superhuman","Auto Superhuman")
Toggle('Items',"Auto Electric Claw","Auto Electric Claw")
Toggle('Items',"Auto Dragon Talon","Auto Dragon Talon")
Toggle('Items',"Auto Death Step","Auto Death Step")
Toggle('Items',"Auto Sharkman Karate","Auto Sharkman Karate")
Toggle('Items',"Auto Godhuman","Auto Godhuman")
Toggle('Items',"Auto Godhuman (Fully)","Auto Godhuman Fully")

if FirstSea then 
	Tabs['Items']:AddSection("Saber Section")
	Toggle('Items',"Auto Saber","Auto Saber")
	Toggle('Items',"Enabled Hop","Auto Saber Hop")
	Tabs['Items']:AddSection("Trident Section")
	Toggle('Items',"Auto Trident","Auto Trident")
	Toggle('Items',"Enabled Hop","Auto Trident Hop")
	Tabs['Items']:AddSection("Pole Section")
	Toggle('Items',"Auto Pole V1","Auto Pole V1")
	Toggle('Items',"Enabled Hop","Auto Pole V1 Hop")
	Tabs['Items']:AddSection("Cannon Section")
	Toggle('Items',"Auto Cannon","Auto Cannon")
	Toggle('Items',"Enabled Hop","Auto Cannon Hop")
	Tabs['Items']:AddSection("Bizento Section")
	Toggle('Items',"Auto Bizento V2","Auto Bizento V2")
	Toggle('Items',"Enabled Hop","Auto Bizento V2 Hop")
elseif SecondSea then 
	Tabs['Items']:AddSection("Factory Section")
	Toggle('Items',"Auto Factory","Auto Factory")
	Toggle('Items',"Enabled Hop","Auto Factory Hop")
	Tabs['Items']:AddSection("Dragon Trident")
	Toggle('Items',"Auto Dragon Trident","Auto Dragon Trident")
	Toggle('Items',"Enabled Hop","Auto Dragon Trident Hop")
	Tabs['Items']:AddSection("Dark Coat")
	Toggle('Items',"Auto Dark Coat","Auto Dark Coat")
	Toggle('Items',"Enabled Hop","Auto Dark Coat Hop")
	Tabs['Items']:AddSection("Swan Glasses")
	Toggle('Items',"Auto Swan Glasses","Auto Swan Glasses")
	Toggle('Items',"Enabled Hop","Auto Swan Glasses Hop")
elseif ThirdSea then 
	Tabs['Items']:AddSection("Serpent Bow")
	Toggle('Items',"Auto Serpent Bow","Auto Serpent Bow")
	Toggle('Items',"Enabled Hop","Auto Serpent Bow Hop")
	Tabs['Items']:AddSection("Twin Hook")
	Toggle('Items',"Auto Twin Hook","Auto Twin Hook")
	Toggle('Items',"Enabled Hop","Auto Twin Hook Hop")
	Tabs['Items']:AddSection("Canvander")
	Toggle('Items',"Auto Canvander","Auto Canvander")
	Toggle('Items',"Enabled Hop","Auto Canvander Hop")
end 

Tabs['Stats']:AddSection("Stats Section")

Toggle('Stats',"Auto Stats Melee","Auto Stats Melee")
Toggle('Stats',"Auto Stats Defense","Auto Stats Defense")
Toggle('Stats',"Auto Stats Sword","Auto Stats Sword")
Toggle('Stats',"Auto Stats Gun","Auto Stats Gun")
Toggle('Stats',"Auto Stats Fruit","Auto Stats Fruit")
Slider('Stats',"Point Stats %",1,10,3,"Point")
Toggle('Stats',"Auto Stats Kaitun","Auto Stats Kaitun")
task.spawn(function()
	while wait() do 
		local stats = {
			["Melee"] = C()['Auto Stats Melee'], ["Defense"] = C()['Auto Stats Defense'],
			["Sword"] = C()['Auto Stats Sword'], ["Gun"] = C()['Auto Stats Gun'], ["Demon Fruit"] = C()['Auto Stats Fruit']
		}
		for i, v in pairs(stats) do
			if v then _C("AddPoint",i,C()['Point']) end
		end
	end
end)

spawn(function()
	while wait() do
		if C()['Auto Stats Kaitun'] then
			if LocalPlayer.Data.Stats.Melee.Level.Value <= 2749 then
				_C("AddPoint","Melee",1000)
			elseif LocalPlayer.Data.Stats.Defense.Level.Value <= 2749 then
				_C("AddPoint","Defense",1000)
			end
		end
	end
end)

local ESP = loadstring(game:HttpGet("https://raw.githubusercontent.com/hajibeza/File/main/ESP.lua"))()

Tabs['Visuals']:AddSection("Visuals Section")

Toggle('Visuals',"ESP Player","ESP Player")
Toggle('Visuals',"ESP Flower","ESP Flower")
Toggle('Visuals',"ESP Demon Fruit","ESP Demon Fruit")
Toggle('Visuals',"ESP Chest","ESP Chest")
Toggle('Visuals',"ESP Island","ESP Island")

Func['ESP Player'] = function(value)
	_G.ESP_Player = value
	while _G.ESP_Player and task.wait() do
		pcall(function()
			PlrESP()
		end)
	end
end
Func['ESP Flower'] = function(value)
	_G.FlowerEsp = value
	while _G.FlowerEsp and task.wait() do
		pcall(function()
			FlowerESP()
		end)
	end
end
Func['ESP Demon Fruit'] = function(value)
	_G.DFEsp = value
	while _G.DFEsp and task.wait() do
		pcall(function()
			UpdateBfEsp()
		end)
	end
end
Func['ESP Chest'] = function(value)
	_G.ChestEsp = value
	while _G.ChestEsp and task.wait() do
		pcall(function()
			ChestSESP()
		end)
	end
end
Func['ESP Island'] = function(value)
	_G.IslandEsp = value
	while _G.IslandEsp and task.wait() do
		pcall(function()
			IslandESP()
		end)
	end
end

Tabs['Visuals']:AddSection("Kaitun Screen")

Tabs['Visuals']:AddButton({Title = "Kaitun Screen Capture",Description = nil,Callback = function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/hajibeza/File/main/Kaitun_Cap.lua"))()
end})

Tabs['Visuals']:AddButton({Title = "Destroy Screen Kaitun",Description = nil,Callback = function()
	game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").localPlayer)
end})

Tabs['Shop']:AddSection("Shop Section")
Tabs['Shop']:AddSection("Ability Shop")

Tabs['Shop']:AddButton({
	Title = "Buy Geppo",
	Description = nil,
	Callback = function()
		_C("BuyHaki","Geppo")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Buso Haki",
	Description = nil,
	Callback = function()
		_C("BuyHaki","Buso")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Soru",
	Description = nil,
	Callback = function()
		_C("BuyHaki","Soru")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Ken Haki",
	Description = nil,
	Callback = function()
		_C("KenTalk","Buy")
	end
})
Tabs['Shop']:AddSection("Fighting Style Shop")

Tabs['Shop']:AddButton({
	Title = "Buy Black Leg",
	Description = nil,
	Callback = function()
		_C("BuyBlackLeg")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Electro",
	Description = nil,
	Callback = function()
		_C("BuyElectro")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Fishman Karate",
	Description = nil,
	Callback = function()
		_C("BuyFishmanKarate")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Dragon Claw",
	Description = nil,
	Callback = function()
		_C("BlackbeardReward","DragonClaw","1")
		_C("BlackbeardReward","DragonClaw","2")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Superhuman",
	Description = nil,
	Callback = function()
		_C("BuySuperhuman")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Death Step",
	Description = nil,
	Callback = function()
		_C("BuyDeathStep")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Sharkman Karate",
	Description = nil,
	Callback = function()
		_C("BuySharkmanKarate",true)
		_C("BuySharkmanKarate")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Electric Claw",
	Description = nil,
	Callback = function()
		_C("BuyElectricClaw")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Dragon Talon",
	Description = nil,
	Callback = function()
		_C("BuyDragonTalon")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy God Human",
	Description = nil,
	Callback = function()
		_C("BuyGodhuman")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Sanguine Art",
	Description = nil,
	Callback = function()
		_C("BuySanguineArt", true)
		_C("BuySanguineArt")
	end
})

Tabs['Shop']:AddSection("Race Shop")

Tabs['Shop']:AddButton({
	Title = "Buy Race Ghoul",
	Description = nil,
	Callback = function()
		_C("Ectoplasm","BuyCheck",4)
		_C("Ectoplasm","Change",4)
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Cyborg",
	Description = nil,
	Callback = function()
		local args = {
			[1] = "CyborgTrainer",
			[2] = "Buy"
		}
		_C(unpack(args))
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Random Race",
	Description = nil,
	Callback = function()
		local args = {
			[1] = "BlackbeardReward",
			[2] = "Reroll",
			[3] = "2"
		}
		_C(unpack(args))
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Reset Stats",
	Description = nil,
	Callback = function()
		local args = {
			[1] = "BlackbeardReward",
			[2] = "Refund",
			[3] = "2"
		}
		_C(unpack(args))
	end
})

Tabs['Shop']:AddSection("Accessory Shop")

Tabs['Shop']:AddButton({
	Title = "Buy Tomoe Ring",
	Description = nil,
	Callback = function()
		_C("BuyItem","Tomoe Ring")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Black Cape",
	Description = nil,
	Callback = function()
		_C("BuyItem","Black Cape")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Swordsman Hat",
	Description = nil,
	Callback = function()
		_C("BuyItem","Swordsman Hat")
	end
})

Tabs['Shop']:AddSection("Sword Shop")

Tabs['Shop']:AddButton({
	Title = "Buy Cutlass",
	Description = nil,
	Callback = function()
		_C("BuyItem","Cutlass")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Katana",
	Description = nil,
	Callback = function()
		_C("BuyItem","Katana")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Iron Mace",
	Description = nil,
	Callback = function()
		_C("BuyItem","Iron Mace")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Duel Katana",
	Description = nil,
	Callback = function()
		_C("BuyItem","Duel Katana")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Duel Katana",
	Description = nil,
	Callback = function()
		_C("BuyItem","Duel Katana")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Triple Katana",
	Description = nil,
	Callback = function()
		_C("BuyItem","Triple Katana")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Pipe",
	Description = nil,
	Callback = function()
		_C("BuyItem","Pipe")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Dual-Headed Blade",
	Description = nil,
	Callback = function()
		_C("BuyItem","Dual-Headed Blade")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Bisento",
	Description = nil,
	Callback = function()
		_C("BuyItem","Bisento")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Soul Cane",
	Description = nil,
	Callback = function()
		_C("BuyItem","Soul Cane")
	end
})

Tabs['Shop']:AddSection("Gun Shop")

Tabs['Shop']:AddButton({
	Title = "Buy Slingshot",
	Description = nil,
	Callback = function()
		_C("BuyItem","Slingshot")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Musket",
	Description = nil,
	Callback = function()
		_C("BuyItem","Musket")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Flintlock",
	Description = nil,
	Callback = function()
		_C("BuyItem","Flintlock")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Refined Flintlock",
	Description = nil,
	Callback = function()
		_C("BuyItem","Refined Flintlock")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Cannon",
	Description = nil,
	Callback = function()
		_C("BuyItem","Cannon")
	end
})

Tabs['Shop']:AddButton({
	Title = "Buy Kabucha",
	Description = nil,
	Callback = function()
		_C("BlackbeardReward","Slingshot","1")
		_C("BlackbeardReward","Slingshot","2")
	end
})

Tabs['Settings']:AddSection("Settings Section")

Dropdown('Settings',"Select Weapon",false,{"Melee","Sword","Gun","Blox Fruit"},"Weapon")
Toggle('Settings',"Enabled Fast Attack","Fast Attack")
Toggle('Settings',"Double Quest","Double Quest")
Toggle('Settings',"Auto Set Spawn Point","Auto Set Spawn Point")
Toggle('Settings',"White Screen","White Screen")
Toggle('Settings',"Auto Ken","Auto Ken")
Toggle('Settings',"Auto Haki","Auto Haki")
Toggle('Settings',"Hide Notifications","Hide Notifications")
Toggle('Settings',"Auto Activate Race V3","Auto Activate Race V3")
Toggle('Settings',"Auto Activate Race V4","Auto Activate Race V4")

SaveManager:SetLibrary(Fluent)
InterfaceManager:SetLibrary(Fluent)
SaveManager:IgnoreThemeSettings()
SaveManager:SetIgnoreIndexes({})
InterfaceManager:SetFolder("FluentScriptHub")
SaveManager:SetFolder("FluentScriptHub/specific-game")
InterfaceManager:BuildInterfaceSection(Tabs['Settings'])
SaveManager:BuildConfigSection(Tabs['Settings'])
Window:SelectTab(1)
SaveManager:LoadAutoloadConfig()
