FROM node:16
# Installing libvips-dev for sharp Compatability
RUN apt-get update && apt-get install libvips-dev -y

# where our Strapi app will live
RUN mkdir -p /app

# Set /app as the working directory
WORKDIR /app

# Copy package.json and package-lock.json
# to the /app working directory
COPY ./server/package*.json ./server/package-lock.json /app/
COPY ./.env /app/

ENV PATH /app/node_modules/.bin:$PATH

# Install dependencies in /app
RUN yarn config set network-timeout 600000 -g && yarn install

# Copy the rest of our Strapi folder into /app
COPY ./server /app

EXPOSE 1337

# For production build
ENV NODE_ENV=${NODE_ENV}

# Build Strapi admin
RUN yarn build

# Run yarn dev, as we would via the command line
CMD ["yarn", "start"]
