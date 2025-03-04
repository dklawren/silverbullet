API docs for Space Lua's `js` module, which provides JavaScript interoperability.

## js.import(url)
Imports a JavaScript module from a URL. Returns the imported module.

Example:
```lua
-- Import lodash library
local lodashLib = js.import("https://esm.sh/lodash@4.17.21")
local result = lodashLib.chunk({1, 2, 3, 4, 5, 6, 7, 8, 9, 10}, 3)

-- Import moment.js for date handling
local momentLib = js.import("https://esm.sh/moment@2.30.1")
local dateObj = momentLib("1995-12-25")
print(dateObj.format("DD-MM-YYYY"))  -- prints: 25-12-1995
```

## js.new(constructor, ...)
Creates a new instance of a JavaScript class. Takes a constructor function and its arguments.

Example:
```lua
local DateClass = js.import("https://esm.sh/date-fns")
local dateObj = js.new(DateClass, "2024-03-14")
```

## js.stringify(value)
Converts a Lua value to a JSON string representation.

Example:
```lua
local dataArray = {1, 2, 3}
print(js.stringify(dataArray))  -- prints: [1,2,3]

local nestedArray = lodashLib.chunk({1, 2, 3, 4, 5, 6}, 2)
print(js.stringify(nestedArray))  -- prints: [[1,2],[3,4],[5,6]]
```

## js.tolua(value)
Converts a JavaScript value to its Lua equivalent.

Example:
```lua
local jsArray = someJsFunction()
local luaTable = js.tolua(jsArray)
```

## js.tojs(value)
Converts a Lua value to its JavaScript equivalent.

Example:
```lua
local luaTable = {1, 2, 3}
local jsArray = js.tojs(luaTable)
```

## js.log(...)
Logs messages to the JavaScript console.

Example:
```lua
js.log("Debug message")
js.log("User data:", {name = "John", age = 30})
```

## js.eachIterable(iterable)
Creates an iterator for JavaScript async iterables.

Example:
```lua
local asyncIterator = js.eachIterable(someJsAsyncIterable)
for value in asyncIterator do
    print(value)
end
