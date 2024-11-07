FROM node:18 AS builder

RUN npm install -g @angular/cli@18.0.0

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN ng build --configuration=production

FROM nginx:alpine

COPY --from=builder /app/dist/needer-fronted/browser /usr/share/nginx/html

EXPOSE 80 

CMD nginx -g "daemon off;"