# Stage 1 : install deps
FROM node:24-alpine AS deps

ENV COREPACK_ENABLE_DOWNLOAD_PROMPT=0 CI=true

RUN corepack enable

WORKDIR /app

COPY package.json pnpm-lock.yaml ./

RUN pnpm install --frozen-lockfile --ignore-scripts

RUN pnpm build


# Stage 2 : run the output of deps

FROM node:24-alpine AS runner

COPY --from=deps /app/.output ./.output

CMD ["node", ".output/server/index.mjs"]