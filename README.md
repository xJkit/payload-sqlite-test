
### Reproduction Steps

#### First, create payload app using pnpx with blank template and sqlite

```sh
pnpx create-payload-app
```

#### Update the dev script of  `package.json` to use next.js turbopack by adding `--turbo` like so:

```json
  "scripts": {
    "dev": "cross-env NODE_OPTIONS=--no-deprecation next dev --turbo",
  },
```

#### Run the dev script and go to the dev url (http://localhost:3000/admin):

```sh
pnpm dev

> payload-sqlite-test@1.0.0 dev /Users/jaychung/Documents/Workspace/payload-sqlite-test
> cross-env NODE_OPTIONS=--no-deprecation next dev --turbo

   ▲ Next.js 15.1.5 (Turbopack)
   - Local:        http://localhost:3000
   - Network:      http://192.168.1.119:3000
   - Environments: .env
   - Experiments (use with caution):
     · turbo

 ✓ Starting...
 ✓ Ready in 10.2s

```

Then you got the error message immediately:

```sh
○ Compiling /admin/[[...segments]] ...
 ✓ Compiled /admin/[[...segments]] in 7.8s
 ⨯ Error: could not resolve "@libsql/darwin-x64" into a module
    at [project]/node_modules/.pnpm/@libsql+client@0.14.0/node_modules/@libsql/client/lib-esm/sqlite3.js [app-rsc] (ecmascript) <module evaluation> (.next/server/chunks/ssr/8bf23_@libsql_client_1fbc27._.js:1806:186)
    at [project]/node_modules/.pnpm/@libsql+client@0.14.0/node_modules/@libsql/client/lib-esm/node.js [app-rsc] (ecmascript) <module evaluation> (.next/server/chunks/ssr/8bf23_@libsql_client_1fbc27._.js:2773:255)
    at [project]/src/payload.config.ts [app-rsc] (ecmascript) (src/payload.config.ts:2:0)
    at [project]/src/app/(payload)/layout.tsx [app-rsc] (ecmascript) (src/app/(payload)/layout.tsx:3:0)
    at [project]/.next-internal/server/app/(payload)/admin/[[...segments]]/page/actions.js { ACTIONS_MODULE0 => "[project]/src/app/(payload)/layout.tsx [app-rsc] (ecmascript)", ACTIONS_MODULE1 => "[project]/node_modules/.pnpm/@payloadcms+next@3.20.0_@types+react@19.0.7_graphql@16.10.0_monaco-editor@0.52.2_next@15.1.5__55gfamireb7q4ywe67aa66ktea/node_modules/@payloadcms/next/dist/layouts/Root/index.js [app-rsc] (ecmascript)" } [app-rsc] (ecmascript) <module evaluation> (.next/server/chunks/ssr/_fad272._.js:264:140)
    at [project]/.next-internal/server/app/(payload)/admin/[[...segments]]/page/actions.js { ACTIONS_MODULE0 => "[project]/src/app/(payload)/layout.tsx [app-rsc] (ecmascript)", ACTIONS_MODULE1 => "[project]/node_modules/.pnpm/@payloadcms+next@3.20.0_@types+react@19.0.7_graphql@16.10.0_monaco-editor@0.52.2_next@15.1.5__55gfamireb7q4ywe67aa66ktea/node_modules/@payloadcms/next/dist/layouts/Root/index.js [app-rsc] (ecmascript)" } [app-rsc] (ecmascript) (.next/server/chunks/ssr/_fad272._.js:290:757)
    at Object.<anonymous> (.next/server/app/(payload)/admin/[[...segments]]/page.js:45:9)
  1 | // storage-adapter-import-placeholder
> 2 | import { sqliteAdapter } from '@payloadcms/db-sqlite'
  3 | import { payloadCloudPlugin } from '@payloadcms/payload-cloud'
  4 | import { lexicalEditor } from '@payloadcms/richtext-lexical'
  5 | import path from 'path' {
  page: '/admin'
}
 ⨯ Error: could not resolve "@libsql/darwin-x64" into a module
    at [project]/node_modules/.pnpm/@libsql+client@0.14.0/node_modules/@libsql/client/lib-esm/sqlite3.js [app-rsc] (ecmascript) <module evaluation> (.next/server/chunks/ssr/8bf23_@libsql_client_1fbc27._.js:1806:186)
    at [project]/node_modules/.pnpm/@libsql+client@0.14.0/node_modules/@libsql/client/lib-esm/node.js [app-rsc] (ecmascript) <module evaluation> (.next/server/chunks/ssr/8bf23_@libsql_client_1fbc27._.js:2773:255)
    at [project]/src/payload.config.ts [app-rsc] (ecmascript) (src/payload.config.ts:2:0)
    at [project]/src/app/(payload)/layout.tsx [app-rsc] (ecmascript) (src/app/(payload)/layout.tsx:3:0)
    at [project]/.next-internal/server/app/(payload)/admin/[[...segments]]/page/actions.js { ACTIONS_MODULE0 => "[project]/src/app/(payload)/layout.tsx [app-rsc] (ecmascript)", ACTIONS_MODULE1 => "[project]/node_modules/.pnpm/@payloadcms+next@3.20.0_@types+react@19.0.7_graphql@16.10.0_monaco-editor@0.52.2_next@15.1.5__55gfamireb7q4ywe67aa66ktea/node_modules/@payloadcms/next/dist/layouts/Root/index.js [app-rsc] (ecmascript)" } [app-rsc] (ecmascript) <module evaluation> (.next/server/chunks/ssr/_fad272._.js:264:140)
    at [project]/.next-internal/server/app/(payload)/admin/[[...segments]]/page/actions.js { ACTIONS_MODULE0 => "[project]/src/app/(payload)/layout.tsx [app-rsc] (ecmascript)", ACTIONS_MODULE1 => "[project]/node_modules/.pnpm/@payloadcms+next@3.20.0_@types+react@19.0.7_graphql@16.10.0_monaco-editor@0.52.2_next@15.1.5__55gfamireb7q4ywe67aa66ktea/node_modules/@payloadcms/next/dist/layouts/Root/index.js [app-rsc] (ecmascript)" } [app-rsc] (ecmascript) (.next/server/chunks/ssr/_fad272._.js:290:757)
    at Object.<anonymous> (.next/server/app/(payload)/admin/[[...segments]]/page.js:45:9)
  1 | // storage-adapter-import-placeholder
> 2 | import { sqliteAdapter } from '@payloadcms/db-sqlite'
  3 | import { payloadCloudPlugin } from '@payloadcms/payload-cloud'
  4 | import { lexicalEditor } from '@payloadcms/richtext-lexical'
  5 | import path from 'path' {
  page: '/admin'
}
 ○ Compiling /_error ...
 ✓ Compiled /_error in 774ms
 GET /admin 500 in 9059ms
```