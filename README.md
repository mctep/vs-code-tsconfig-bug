# vs-code-tsconfig-bug
Reproduce bug with multiple tsconfig.json in VSCode

VSCode: Version 1.13.1

MacOS Sierra: Version 10.12.5

## Overview

Project has next files:

```
/server.ts
/tsconfig.json
/client/client.ts
/client/tsconfig.json
```

```ts
// server.ts
typeof window;
typeof global;
```

```json
// tsconfig.json
{
  "compilerOptions": {
    "lib": ["es2015"],
    "types": ["node"]
  }
}
```

```ts
// client/client.ts
typeof window;
typeof global;
```

```json
// client/tsconfig.json
{
  "compilerOptions": {
    "lib": ["dom"],
    "types": []
  }
}
```

1) Clone repo `git clone https://github.com/mctep/vs-code-tsconfig-bug.git`
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
