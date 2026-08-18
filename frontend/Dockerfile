# VITE_WS_URL is baked into the static bundle at build time (Vite inlines
# import.meta.env values during `npm run build`), so it has to be passed as a
# build arg here rather than set as a container runtime env var.
FROM node:20-alpine AS build
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci
COPY . .
ARG VITE_WS_URL
ENV VITE_WS_URL=$VITE_WS_URL
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
