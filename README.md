# vs-code-tsconfig-bug
Reproduce bug with multiple tsconfig.json in VSCode

## Overview

Sample project has next file:

```
/server.ts
/tsconfig.json
/client/client.ts
/client/tsconfig.json
```

Server use `lib: ["es2015"]` and `"types": ["node"]`.
Client use `lib: ["dom"]` and `types: []`.

1) Clone repo `gti clone https://github.com/mctep/vs-code-tsconfig-bug.git`
2) Install packages `cd vs-code-tsconfig-bug && npm i`

## Case 1

1) Open project in `VScode` with any closed tabs `code .`.
2) Open `client/client.ts.ts` in `VScode`. There is right error `[ts] Cannot find name 'global'`
3) Open `server.ts`. Right erorr `[ts] Cannot find name 'window'`;
4) Close `client.ts`. Open `client.ts`.
6) Focus `server.ts`. There are no errors. **All types have found.**
7) Close `server.ts`. Open `server.ts`. Right erorr `[ts] Cannot find name 'window'`.

## Case 2

1) Open project in `VScode` with any closed tabs `code .`.
2) Open `server.ts`. Right erorr `[ts] Cannot find name 'window'`;
3) Open `client.ts`. **Wrong erorr `[ts] Cannot find name 'window'`**;
