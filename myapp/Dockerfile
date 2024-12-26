# install node at the top
FROM node:17-alpine

# create working directory for container
WORKDIR /app

# copy package json in it
COPY package.json .

# install dependencies
RUN npm install

# copy source file
COPY . .

# expose port => docker port
EXPOSE 3000

# start the container
CMD ["npm", "start"]