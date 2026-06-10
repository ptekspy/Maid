# Maid

A lightweight Luau cleanup manager for Roblox, inspired by common Maid-style patterns.

## Features

- Create a `Maid` instance with an optional lock key.
- Add cleanup objects, functions, instances, and RBXScriptConnections.
- Clean up all registered items in one call.
- Optionally lock cleanup until `Unlock(key)` is called.

## API

```lua
local Maid = require(path.to.Maid.init)
```

### Constructor

```lua
local maid = Maid.New()
local lockedMaid = Maid.New(lockKey)
```

### Methods

```lua
maid:IsActive() --> boolean
maid:Add(object) --> MaidToken
maid:Cleanup(...)
maid:Unlock(key)
```

### Usage example

```lua
local maid = Maid.New()

-- Add cleanup actions
maid:Add(function()
	print("cleaned up")
end)

-- Add an instance or connection
maid:Add(part)
maid:Add(connection)

-- Clean up everything later
maid:Cleanup()
```

### Token cleanup

The returned token can be destroyed manually to remove the item from the maid before cleanup:

```lua
local token = maid:Add(part)
token:Destroy()
```

## Building

Use `argon build` from the repository root to package the module.

## Installation

Install with Wally if you use it in your project:

```bash
wally add ptekspy/Maid
```
