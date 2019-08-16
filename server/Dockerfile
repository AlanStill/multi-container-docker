FROM node:alpine
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . . 

# the "start" command will be specified in the package.json file
CMD ["npm", "run", "start"]