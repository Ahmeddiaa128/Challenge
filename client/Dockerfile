# Stage 1: Build the application
FROM node:18-alpine AS build

# Set working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code to the working directory
COPY . .

# Build the application for production
RUN npm run build

# Stage 2: Production container
FROM node:18-alpine

# Set working directory
WORKDIR /usr/src/app

# Copy the production build from the build stage
COPY --from=build /usr/src/app/.output ./.output
COPY --from=build /usr/src/app/public ./public
COPY --from=build /usr/src/app/package*.json ./

# Install production dependencies
RUN npm install

# Expose port 3000 for the Nuxt.js server
EXPOSE 3000

# Set environment variables
ENV HOST=0.0.0.0
ENV PORT=3000

# Start the Nuxt.js application
CMD ["npm", "run", "serve"]