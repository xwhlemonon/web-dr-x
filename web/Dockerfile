FROM node:18 AS builder

WORKDIR /app
COPY package.json pnpm-lock.yaml ./
RUN corepack enable && pnpm install --frozen-lockfile

COPY . .
RUN pnpm run build

FROM nginx:latest AS base

RUN rm -rf /etc/nginx/conf.d/*

COPY docker/nginx/ /etc/nginx/
COPY --from=builder /app/dist /usr/share/nginx/html/dist
RUN chown -R nginx:nginx /usr/share/nginx/html

USER nginx

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
