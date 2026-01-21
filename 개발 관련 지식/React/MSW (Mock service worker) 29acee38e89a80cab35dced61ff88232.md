# MSW (Mock service worker)

# 개요

# 초기 폴더 구성

- handler.ts
- browser.ts
- db.ts
- server.ts

## Browser.ts

`*import* { setupWorker } *from* 'msw/browser';`

`*import* { handlers } *from* './handlers/index';`

`*export* const *worker* = *setupWorker*(...*handlers*);`

## Db.ts

`*export* const *db* = **{`

`};`