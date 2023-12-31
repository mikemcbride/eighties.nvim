# Eighties

The classic base16-eighties theme, with some slight modifications. Neovim theme is based off the excellent work in the [gruvbox.nvim](https://github.com/ellisonleao/gruvbox.nvim) plugin.

# Prerequisites

Neovim 0.8.0+

# Installing

## Using `lazy.nvim`

```lua
{ "mikemcbride/eighties.nvim", priority = 1000 }
```

## Using `packer`

```lua
use { "mikemcbride/eighties.nvim" }
```

# Basic Usage

Inside `init.lua`

```lua
vim.cmd([[colorscheme eighties]])
```

# Configuration

Additional settings:

```lua
-- Default options:
require("eighties").setup({
  terminal_colors = true, -- add neovim terminal colors
  undercurl = true,
  underline = true,
  bold = true,
  italic = {
    strings = true,
    emphasis = true,
    comments = true,
    operators = false,
    folds = true,
  },
  strikethrough = true,
  invert_selection = false,
  invert_signs = false,
  invert_tabline = false,
  invert_intend_guides = false,
  inverse = true, -- invert background for search, diffs, statuslines and errors
  palette_overrides = {},
  overrides = {},
  dim_inactive = false,
  transparent_mode = false,
})
vim.cmd("colorscheme eighties")
```

**VERY IMPORTANT**: Make sure to call setup() **BEFORE** calling the colorscheme command, to use your custom configs

## Overriding

### Palette

You can specify your own palette colors. For example:

```lua
require("eighties").setup({
    palette_overrides = {
        green = "#990000",
    }
})
vim.cmd("colorscheme eighties")
```

### Highlight groups

If you don't enjoy the current color for a specific highlight group, now you can just override it in the setup. For
example:

```lua
require("eighties").setup({
    overrides = {
        SignColumn = {bg = "#ff9900"}
    }
})
vim.cmd("colorscheme eighties")
```

It also works with treesitter groups and lsp semantic highlight tokens

```lua
require("eighties").setup({
    overrides = {
        ["@lsp.type.method"] = { bg = "#ff9900" },
        ["@comment.lua"] = { bg = "#000000" },
    }
})
vim.cmd("colorscheme eighties")
```

Please note that the override values must follow the attributes from the highlight group map, such as:

- **fg** - foreground color
- **bg** - background color
- **bold** - true or false for bold font
- **italic** - true or false for italic font

Other values can be seen in [`synIDattr`](<https://neovim.io/doc/user/builtin.html#synIDattr()>)
