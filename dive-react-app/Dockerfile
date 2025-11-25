FROM node:22.21.0-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install --fetch-timeout=60000 --network-timeout=600000
COPY . .
RUN  npm run build
EXPOSE 5173
CMD [ "npm" , "run" , "build" ]

FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80

CMD [ "nginx" , "-g" , "daemon off;" ]


