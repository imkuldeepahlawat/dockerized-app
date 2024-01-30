# use node.js image from dockerhub
FROM node:20 as build

# set working directory
WORKDIR /app

# install packages
RUN npm install

# copy project files from root directory to docker working directory
COPY . .

# create project build
RUN npm run build

# using nginx as production server
FROM nginx:alpine

# copy the build of react app in nginx working directory
COPY --from=build /app/build /user/share/nginx/html

# port expose
EXPOSE 80

# start nginx when container is runs

CMD ['nginx','-g','daemon off;']