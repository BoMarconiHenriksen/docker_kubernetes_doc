FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .

# The build process. We get a folder called build. We have to copy that to nginx phase of our build
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# FRom builder copy /app/build to usr/share...
COPY --from=builder /app/build /usr/share/nginx/html
