from node:14.14.0-alpine as builder

WORKDIR /app
copy package.json .
run npm install
RUN mkdir node_modules/.cache && chmod -R 777 node_modules/.cache
copy . .
run npm run build

from nginx
expose 3000
copy ./nginx/default.conf /etc/nginx/conf.d/default.conf
copy --from=builder /app/build /usr/share/nginx/html