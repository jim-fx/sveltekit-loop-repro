# Repro of Infinite Loop Error

## What is happening?

The index.svelte uses the "load" function to load "/api/test", which should return 

```json
{"test": "works"}
```

Instead it returns a 404.

## Why is this happening

I think i tracked it down to the `ssr` function in `packages/kit/src/runtime/server/index.js` where the function detects an infinite loop and aborts the request. If the function is commented out everything works as expected.


Dunno if this is any help to anyone, but thx anyway for this amazing project, it is a lot of fun to work with.

