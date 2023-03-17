VERSION 0.7

FROM denoland/deno:alpine
WORKDIR /app
RUN apk add --no-cache tini
ENTRYPOINT ["/sbin/tini", "--"]

dist:
    COPY deps.ts .
    RUN deno cache deps.ts
    COPY --dir src .
    RUN deno check src/server.ts
    CMD ["deno", "run", "--allow-net", "src/server.ts"]
    ARG EARTHLY_GIT_HASH
    SAVE IMAGE --push \
        theomessin/example:latest \
        theomessin/example:$EARTHLY_GIT_HASH
