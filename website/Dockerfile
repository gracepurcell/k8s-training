FROM nginx:latest

# If we want the nginx config file outside of the website context
# we need to specify the user and the working directory
# Switch to root user for installation
# USER root
# # Set the working directory
# WORKDIR /usr/src/app

COPY ./website/index.html /usr/share/nginx/html/index.html

COPY ./nginx/nginx.conf /etc/nginx/conf.d/default.conf
