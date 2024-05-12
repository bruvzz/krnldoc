# Cache Library

## Invalidate Cache:
```lua
<void> cache.invalidate(<Instance> Object)
```
Invalidates `Object` within the instance cache.

---

## Replace Cache:
```lua
<void> cache.replace(<Instance> Object, <Instance> NewObject)
```
Replaces `Object` with `NewObject` within the instance cache.

---

## Is Cached:
```lua
<bool> cache.iscached(<Instance> Object)
```
Returns true if `Object` is cached.

---

## Get Instance Key:
```lua
<userdata> cache.getinstancekey(<Instance> Object)
```
Returns `Object`'s instance key.

Used for retrieving Instances within the instance cache.

### Example:
```lua
local instance_cache = getreg()[cache.getinstancecachekey()]
local instance_key = cache.getinstancekey(instance)

local instance = instance_cache[instance_key] -- this is the instance in the cache
```

---

## Get Instance Cache Key:
```lua
<userdata> cache.getinstancecachekey(<void>)
```
Returns the instance cache key.

Used for retrieving the instance cache table.

### Example:
```lua
local instance_cache = getreg()[cache.getinstancecachekey()] -- this is the instance cache
```

---

## Clone Instance:
```lua
<Instance> cache.cloneinstance(<Instance> Object)
```
Clones `Object` and returns it.