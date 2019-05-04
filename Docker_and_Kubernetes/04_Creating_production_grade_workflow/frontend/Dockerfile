# Build phase using a tag.
FROM node:alpine as builder 
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
# The build is going to be created in the working directory /app/build  
RUN npm run build

# Run phase
# The new FROM statement is terminating the previous blok(the other FROM statement).
FROM nginx
# Copy build folder from a diffrent phase and copy build to nginx
# With the COPY statement we will drop all the other stuff from the build phase. So the container will only have nginx and the build we copied.
COPY --from=builder /app/build /usr/share/nginx/html
