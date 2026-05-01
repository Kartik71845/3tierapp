FROM node:20-alpine as build
WORKDIR /app
COPY package.json ./
RUN npm install --legacy-peer-deps
RUN npm install vite@5.0.0 @vitejs/plugin-react@4.2.0 --legacy-peer-deps
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
