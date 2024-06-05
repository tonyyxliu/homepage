# 个人主页开发文档

## 问题解决办法（FAQ）

1. NodeJS版本过新导致OpenSSL相关问题

```bash
PS F:\Programs\Vue\homepage> npm run deploy
   
> homepage@0.1.0 predeploy
> npm run build


> homepage@0.1.0 build
> react-scripts build

Creating an optimized production build...
Error: error:0308010C:digital envelope routines::unsupported
    at new Hash (node:internal/crypto/hash:79:19)
    at Object.createHash (node:crypto:139:10)
    at module.exports (F:\Programs\Vue\homepage\node_modules\webpack\lib\util\createHash.js:90:53)
    at NormalModule._initBuildHash (F:\Programs\Vue\homepage\node_modules\webpack\lib\NormalModule.js:401:16)
    at handleParseError (F:\Programs\Vue\homepage\node_modules\webpack\lib\NormalModule.js:449:10)
    at F:\Programs\Vue\homepage\node_modules\webpack\lib\NormalModule.js:481:5
    at F:\Programs\Vue\homepage\node_modules\webpack\lib\NormalModule.js:342:12
    at F:\Programs\Vue\homepage\node_modules\loader-runner\lib\LoaderRunner.js:373:3
    at iterateNormalLoaders (F:\Programs\Vue\homepage\node_modules\loader-runner\lib\LoaderRunner.js:214:10)
    at iterateNormalLoaders (F:\Programs\Vue\homepage\node_modules\loader-runner\lib\LoaderRunner.js:221:10)
    at F:\Programs\Vue\homepage\node_modules\loader-runner\lib\LoaderRunner.js:236:3
    at runSyncOrAsync (F:\Programs\Vue\homepage\node_modules\loader-runner\lib\LoaderRunner.js:130:11)
    at iterateNormalLoaders (F:\Programs\Vue\homepage\node_modules\loader-runner\lib\LoaderRunner.js:232:2)
    at Array.<anonymous> (F:\Programs\Vue\homepage\node_modules\loader-runner\lib\LoaderRunner.js:205:4)
    at Storage.finished (F:\Programs\Vue\homepage\node_modules\enhanced-resolve\lib\CachedInputFileSystem.js:55:16)
    at F:\Programs\Vue\homepage\node_modules\enhanced-resolve\lib\CachedInputFileSystem.js:91:9
F:\Programs\Vue\homepage\node_modules\react-scripts\scripts\build.js:19
  throw err;
  ^

Error: error:0308010C:digital envelope routines::unsupported
    at new Hash (node:internal/crypto/hash:79:19)
    at Object.createHash (node:crypto:139:10)
    at module.exports (F:\Programs\Vue\homepage\node_modules\webpack\lib\util\createHash.js:90:53)
    at NormalModule._initBuildHash (F:\Programs\Vue\homepage\node_modules\webpack\lib\NormalModule.js:401:16)
    at F:\Programs\Vue\homepage\node_modules\webpack\lib\NormalModule.js:433:10
    at F:\Programs\Vue\homepage\node_modules\webpack\lib\NormalModule.js:308:13
    at F:\Programs\Vue\homepage\node_modules\loader-runner\lib\LoaderRunner.js:367:11
    at F:\Programs\Vue\homepage\node_modules\loader-runner\lib\LoaderRunner.js:233:18
    at context.callback (F:\Programs\Vue\homepage\node_modules\loader-runner\lib\LoaderRunner.js:111:13)
    at F:\Programs\Vue\homepage\node_modules\babel-loader\lib\index.js:51:103 {
  opensslErrorStack: [
    'error:03000086:digital envelope routines::initialization error',
    'error:0308010C:digital envelope routines::unsupported'
  ],
  library: 'digital envelope routines',
  reason: 'unsupported',
  code: 'ERR_OSSL_EVP_UNSUPPORTED'
}

Node.js v20.14.0
```

**解决办法：设置环境变量使用旧版OpenSSL**

```bash
$env:NODE_OPTIONS = "--openssl-legacy-provider"
```