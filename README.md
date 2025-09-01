# Nuxt4 Vite Rolldown i18n issues

Install @nuxtjs/i18n, add rolldown-vite integration to package.json

```
"overrides": {
    "vite": "npm:rolldown-vite@latest"
}
```

In dev mode:

```bash
$ npm run dev

ℹ Vite client warmed up in 2218ms                                                                                                                   6:01:32 AM
 WARN  Failed to load messages for locale "en" Failed loading locale (en): expected value at line 1 column 1                                         6:02:15 AM

    at getLocaleMessages (node_modules/@nuxtjs/i18n/dist/runtime/shared/messages.js:24:9)
    at process.processTicksAndRejections (node:internal/process/task_queues:105:5)
    at async node_modules/@nuxtjs/i18n/dist/runtime/shared/messages.js:35:107
    at async Object.callAsync (node_modules/unctx/dist/index.mjs:72:16)
    at async getLocaleMessagesMergedCached (node_modules/@nuxtjs/i18n/dist/runtime/shared/messages.js:35:66)
    at async Object.callAsync (node_modules/unctx/dist/index.mjs:72:16)
    at async loadMessagesFromClient (node_modules/@nuxtjs/i18n/dist/runtime/context.js:52:16)
    at async Object.loadMessages (node_modules/@nuxtjs/i18n/dist/runtime/context.js:92:37)
    at async loadAndSetLocale (node_modules/@nuxtjs/i18n/dist/runtime/utils.js:113:9)
    at async Object.callAsync (node_modules/unctx/dist/index.mjs:72:16)
[6:02:15 AM]  WARN  [nuxt] Failed to stringify dev server logs. Received DevalueError: Cannot stringify arbitrary non-POJOs. You can define your own reducer/reviver for rich types following the instructions in https://nuxt.com/docs/api/composables/use-nuxt-app#payload.
 WARN  Failed to load messages for locale "en" Failed loading locale (en): expected value at line 1 column 1                                         6:02:16 AM

    at getLocaleMessages (node_modules/@nuxtjs/i18n/dist/runtime/shared/messages.js:24:9)
    at process.processTicksAndRejections (node:internal/process/task_queues:105:5)
    at async node_modules/@nuxtjs/i18n/dist/runtime/shared/messages.js:35:107
    at async Object.callAsync (node_modules/unctx/dist/index.mjs:72:16)
    at async getLocaleMessagesMergedCached (node_modules/@nuxtjs/i18n/dist/runtime/shared/messages.js:35:66)
    at async Object.callAsync (node_modules/unctx/dist/index.mjs:72:16)
    at async loadMessagesFromClient (node_modules/@nuxtjs/i18n/dist/runtime/context.js:52:16)
    at async Object.loadMessages (node_modules/@nuxtjs/i18n/dist/runtime/context.js:92:37)
    at async loadAndSetLocale (node_modules/@nuxtjs/i18n/dist/runtime/utils.js:113:9)
    at async Object.callAsync (node_modules/unctx/dist/index.mjs:72:16)
[6:02:16 AM]  WARN  [nuxt] Failed to stringify dev server logs. Received DevalueError: Cannot stringify arbitrary non-POJOs. You can define your own reducer/reviver for rich types following the instructions in https://nuxt.com/docs/api/composables/use-nuxt-app#payload.

 ERROR  Internal server error: expected value at line 1 column 1                                                                                     6:02:21 AM
  Plugin: builtin:json
  File: [object Object]
```

In build mode:

```bash
$ npm run build

> build
> nuxt build

Nuxt 4.0.3 with Nitro 2.12.4                                                                                                                    nuxi 5:58:35 AM
ℹ Building for Nitro preset: node-server                                                                                                       nuxi 5:58:36 AM
ℹ Building client...                                                                                                                                5:58:37 AM

[5:58:37 AM]  WARN  You or a plugin you are using have set optimizeDeps.esbuildOptions but this option is now deprecated. Vite now uses Rolldown to optimize the dependencies. Please use optimizeDeps.rollupOptions instead.

ℹ rolldown-vite v7.1.5 building for production...                                                                                                   5:58:37 AM
✓ 175 modules transformed.

 ERROR  ✗ Build failed in 994ms                                                                                                                      5:58:38 AM


 ERROR  Nuxt Build Error: Build failed with 1 error:                                                                                            nuxi 5:58:38 AM

[UNHANDLEABLE_ERROR] Error: Something went wrong inside native plugin builtin:json. Please report this problem at https://github.com/rolldown/rolldown/issues.
expected value at line 1 column 1


    at normalizeErrors (node_modules/rolldown/dist/shared/src-Chn1S4O2.mjs:2275:18)
    at handleOutputErrors (node_modules/rolldown/dist/shared/src-Chn1S4O2.mjs:3013:34)
    at transformToRollupOutput (node_modules/rolldown/dist/shared/src-Chn1S4O2.mjs:3007:2)
    at RolldownBuild.write (node_modules/rolldown/dist/shared/src-Chn1S4O2.mjs:4221:10)
    at async buildEnvironment (node_modules/vite/dist/node/chunks/dep-Ql2zlmoZ.js:33366:64)
    at async Object.build (node_modules/vite/dist/node/chunks/dep-Ql2zlmoZ.js:33780:19)
    at async buildClient (node_modules/@nuxt/vite-builder/dist/index.mjs:1006:5)
    at async bundle (node_modules/@nuxt/vite-builder/dist/index.mjs:1784:3)
    at async bundle (node_modules/nuxt/dist/index.mjs:7286:5)
    at async build (node_modules/nuxt/dist/index.mjs:7146:3)
```

Doesnt mather if we use npm instead of bun either


```bash
$ bun run --bun build
$ nuxt build
Nuxt 4.0.3 with Nitro 2.12.4                                                                                                                    nuxi 5:56:54 AM
ℹ Building for Nitro preset: node-server                                                                                                       nuxi 5:56:56 AM
ℹ Building client...                                                                                                                                5:56:56 AM

[5:56:56 AM]  WARN  You or a plugin you are using have set optimizeDeps.esbuildOptions but this option is now deprecated. Vite now uses Rolldown to optimize the dependencies. Please use optimizeDeps.rollupOptions instead.

ℹ rolldown-vite v7.1.5 building for production...                                                                                                   5:56:56 AM
✓ 175 modules transformed.

 ERROR  ✗ Build failed in 1.40s                                                                                                                      5:56:58 AM


 ERROR  Nuxt Build Error: Build failed with 1 error:                                                                                            nuxi 5:56:58 AM

[UNHANDLEABLE_ERROR] Error: Something went wrong inside native plugin builtin:json. Please report this problem at https://github.com/rolldown/rolldown/issues.
expected value at line 1 column 1


    at normalizeErrors (node_modules/rolldown/dist/shared/src-Chn1S4O2.mjs:2275:22)
    at handleOutputErrors (node_modules/rolldown/dist/shared/src-Chn1S4O2.mjs:3013:34)
    at transformToRollupOutput (node_modules/rolldown/dist/shared/src-Chn1S4O2.mjs:3007:2)
    at processTicksAndRejections (native:7:39)

error: script "build" exited with code 1
```
