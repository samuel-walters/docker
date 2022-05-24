# Create a docker file to build a customised docker image
# Choose a base image
FROM nginx

# Label the image
LABEL MAINTAINER=SWALTERS@SPARTAGLOBAL.COM

# Migrate/transfer/copy/move data from localhost to our image/container. 
COPY index.html /usr/share/nginx/html/

# Expose 80
EXPOSE 80

# Launch the app - run this command at the end
CMD ["nginx", "-g", "daemon off;"]
