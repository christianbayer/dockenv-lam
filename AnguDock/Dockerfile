FROM node
# RUN apt-get update

RUN npm install -g @angular/cli

RUN mkdir -p /app
WORKDIR /app

COPY  package.json /app/package.json

RUN npm install

# Get all the code needed to run the app
#COPY . /app/

EXPOSE 4200

# Serve the app
# CMD ["npm", "start"]