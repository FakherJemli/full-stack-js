FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM node:18-alpine
ENV PORT=5050
ENV MYSQL_USER=
ENV MYSQL_PASSWORD=
ENV MYSQL_DATABASE=
COPY --from=build /app /app
WORKDIR /app
CMD ["node", "server.js"]
EXPOSE 5050
HEALTHCHECK --interval=30s --timeout=5s --retries=3 CMD curl -f http://localhost:5050/health || exit 1