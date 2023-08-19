Reproduction showing that `react` cannot be added to `ssr.noExternal` because Vite isn't able to process CJS npm packages.

```bash
git clone git@github.com:brillout/vite-ssr-noExternal-cjs
cd vite-ssr-noExternal-cjs/
pnpm install
pnpm run dev
```

Then go to [localhost:5173](http://localhost:5173) and observe this error:

```
11:16:12 AM [vite] Error when evaluating SSR module /node_modules/.pnpm/react@18.2.0/node_modules/react/jsx-dev-runtime.js:
|- ReferenceError: module is not defined
    at eval (/home/rom/tmp/vite-ssr-noExternal-react/node_modules/.pnpm/react@18.2.0/node_modules/react/jsx-dev-runtime.js:8:3)
    at instantiateModule (file:///home/rom/tmp/vite-ssr-noExternal-react/node_modules/.pnpm/vite@4.4.9/node_modules/vite/dist/node/chunks/dep-df561101.js:55974:15)

11:16:12 AM [vite] Error when evaluating SSR module /src/entry-server.jsx: failed to import "/node_modules/.pnpm/react@18.2.0/node_modules/react/jsx-dev-runtime.js"
|- ReferenceError: module is not defined
    at eval (/home/rom/tmp/vite-ssr-noExternal-react/node_modules/.pnpm/react@18.2.0/node_modules/react/jsx-dev-runtime.js:8:3)
    at instantiateModule (file:///home/rom/tmp/vite-ssr-noExternal-react/node_modules/.pnpm/vite@4.4.9/node_modules/vite/dist/node/chunks/dep-df561101.js:55974:15)

ReferenceError: module is not defined
    at /home/rom/tmp/vite-ssr-noExternal-react/node_modules/.pnpm/react@18.2.0/node_modules/react/jsx-dev-runtime.js:6:3
    at instantiateModule (file:///home/rom/tmp/vite-ssr-noExternal-react/node_modules/.pnpm/vite@4.4.9/node_modules/vite/dist/node/chunks/dep-df561101.js:55974:15)
```

This project was scaffolded with `pnpm create vite-extra --template ssr-react` and the only diff is this [commit adding `react` to `ssr.noExternal`](https://github.com/brillout/vite-ssr-noExternal-cjs/commit/f8a84530e1e7f7737f224676bbdbff2bbf90d040).
