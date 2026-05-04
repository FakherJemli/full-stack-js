FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install --omit=dev --legacy-peer-deps
COPY . .
ENV PORT=5050
ENV MYSQL_USER=
ENV MYSQL_PASSWORD=
ENV MYSQL_DATABASE=
EXPOSE 5050
HEALTHCHECK --interval=30s --timeout=5s --retries=3 CMD curl -f http://localhost:5050/health || exit 1
CMD ["node", "index.js"]