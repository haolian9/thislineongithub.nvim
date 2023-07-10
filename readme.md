resolving the github uri for the current line in a buffer

## status
* it just works (tm)
* it is feature-frozen

## design choices
* only for github.com
* no multiple lines
* based on the current line of the current buffer, not `vim.fn.getcwd()`

## prerequisites
* nvim 0.9.*
* haolian9/infra.nvim
* git

## usage
* `:lua =require'thislineongithub'()`
* my personal config:

```
usercmd("ThisLineOnGithub", function()
  local uri = require("thislineongithub")()
  if uri == nil then return end
  vim.fn.setreg("+", uri)
  jelly.info("copied to system clipboard: %s", uri)
end)
```
