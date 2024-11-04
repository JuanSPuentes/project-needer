FROM node:18 AS build

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

FROM nginx:alpine

COPY --from=build /app/dist/needer-fronted /usr/share/nginx/html
COPY --from=build /app/dist/needer-fronted /app/dist/needer-fronted

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]