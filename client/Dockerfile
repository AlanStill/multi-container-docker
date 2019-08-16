# This is the production-level dockerfile using a multi step deploy
# This will simply deploy our app and have it wrapped with an Nginx webserver

# An EBS environment/application is used for monitoring traffic (load balance)
# We created a Docker env
# 

# AS will tag the result of FROM to a given name that we 
# can refer to in the script

FROM node:alpine as builder 

WORKDIR '/app'
COPY ./package.json .
RUN npm install 
COPY . . 

RUN npm run build

# The second FROM will assume that the previous block has completed
FROM nginx 
# EBS will look for expose instruction for port that gets used for incoming traffic
# this is similar to using the -p flag when running docker run from the command line
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

# /build is the place where all the first steps (builder) output will be written to
COPY --from=builder /app/build /usr/share/nginx/html
