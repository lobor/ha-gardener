# Prototype d'emballage Home Assistant pour Gardener.
# Pour un build reproductible, remplacez main par un tag/commit vérifié.
FROM node:26-alpine AS source-build

RUN apk add --no-cache git python3 make g++
WORKDIR /src
ARG GARDENER_REF=main
RUN git clone https://github.com/mniedermaier/gardener.git . \
    && git checkout "${GARDENER_REF}"

# Build frontend
RUN npm ci && npm run build

# Build backend
WORKDIR /src/backend
RUN npm ci && npx tsc

# Runtime: nginx serves the frontend; Node serves the API.
FROM node:26-alpine
RUN apk add --no-cache nginx
WORKDIR /app

COPY --from=source-build /src/dist /usr/share/nginx/html
COPY --from=source-build /src/public/locales /usr/share/nginx/html/locales
COPY --from=source-build /src/docker/nginx.conf /etc/nginx/http.d/default.conf
COPY --from=source-build /src/docker/security-headers.conf /etc/nginx/security-headers.conf

COPY --from=source-build /src/backend/dist ./backend/
COPY --from=source-build /src/backend/node_modules ./backend/node_modules
COPY --from=source-build /src/backend/package.json ./backend/

RUN mkdir -p /data
ENV NODE_ENV=production
ENV DB_PATH=/data/gardener.db
ENV PORT=3001

EXPOSE 80
CMD ["sh", "-c", "nginx && node /app/backend/index.js"]
