# Use the official lightweight Node.js 12 image.
# https://hub.docker.com/_/node
FROM node:12-slim
RUN useradd engdata -u 10001 --create-home --user-group
# Create and change to the app directory.
WORKDIR /usr/src/app
RUN chown -R engdata /usr/src/app
# Copy application dependency manifests to the container image.
# A wildcard is used to ensure copying both package.json AND package-lock.json (when available).
# Copying this first prevents re-running npm install on every code change.
COPY --chown=engdata package*.json ./
# Install production dependencies.
# If you add a package-lock.json, speed your build by switching to 'npm ci'.
# RUN npm ci --only=production
USER 10001
RUN npm install --only=production
# Copy local code to the container image.
COPY --chown=engdata . ./

# Run the web service on container startup.
CMD [ "npm", "start" ]
