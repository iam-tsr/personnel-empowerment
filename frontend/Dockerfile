FROM node:18-alpine AS build

WORKDIR /app
COPY package.json package-lock.json ./
RUN yarn install
COPY . .
RUN yarn build

FROM nginx:1.24-alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]