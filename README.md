# Lua 5.1 wasi

Builds Lua 5.1.5 to wasm32-wasi. Tested with wasi-sdk-27.0-x86_64.

```
cd lua-5.1.5/src
WASI_SDK={path to wasi SDK}  make wasi
```

If needed, the lua wasm binary can then be modified to use new EH
(error-handling) instructions:

```
wasm-opt lua -o lua.exnref.wasm --translate-to-exnref --emit-exnref -O2
```

After which `lua.exnref.wasm` should run with wasm engines that support the new
EH spec.
