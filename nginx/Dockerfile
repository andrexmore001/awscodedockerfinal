# Stage 1: Compile and Build angular codebase

# Use official node image as the base image
FROM node:20.9.0 as build

# Set the working directory
WORKDIR /usr/local/app

# Add the source code to app
COPY ./appdocker/ .

# Install all the dependencies
RUN npm install

# Generate the build of the application
RUN npm run build


# Stage 2: Serve app with nginx server

# Use official nginx image as the base image
FROM nginx:latest
# Set working directory to nginx asset directory
WORKDIR /usr/share/nginx/html
# Remove default nginx static assets
#RUN rm -rf ./*
# Copy the build output to replace the default nginx contents.
COPY --from=build /usr/local/app/dist/prueba .
# Containers run nginx with global directives and daemon off
#ENTRYPOINT ["nginx", "-g", "daemon off;"]