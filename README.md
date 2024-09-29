# Challenge

## Overview

This repository contains a simple web application with two main components:

1. **API**: Written in Laravel PHP, the API serves as the backend for the application and listens on port 8000.
2. **Client**: Developed using Nuxt.js, the client is the frontend of the application and listens on port 3000.

### Environment Variables

- **API Directory**: Take a look at the `.env` file in the API directory. It should contain the necessary credentials to connect to the database.

  ```env
    DB_CONNECTION=mysql
    DB_HOST=db
    DB_PORT=3306
    DB_DATABASE=bookapi
    DB_USERNAME=app
    DB_PASSWORD=password
  ```

- **Client Directory**: Check the `.env` file in the Client directory. It should contain the connection string to connect to the API.

  ```env
    VITE_API_URL=http://api:8000
  ```


## Directory Structure

The project directory is organized as follows:

/Challenge: The root directory of the project.
api: Contains the Laravel API files.

app: Contains the core application files.
bootstrap: Contains the application bootstrapping files.
composer.lock: The locked dependencies file for Composer.
database: Contains database migrations and seed files.
package.json: The Node.js package configuration for the Laravel application.
public: The public-facing files, including the entry point for the application.
routes: Contains route definitions for the API.
tests: Contains automated tests for the application.
vite.config.js: Configuration file for Vite.
artisan: The Artisan command-line tool.
composer.json: The Composer configuration file.
config: Contains configuration files for the application.
Dockerfile: Docker configuration file for building the Laravel API image.
phpunit.xml: Configuration file for PHPUnit tests.
resources: Contains views and assets for the application.
storage: Contains compiled views, file uploads, and logs.
vendor: Contains the dependencies installed by Composer.
client: Contains the Nuxt.js client files.

app.vue: The main Vue component for the application.
Dockerfile: Docker configuration file for building the Nuxt.js client image.
nuxt.config.ts: Configuration file for the Nuxt.js application.
package.json: The Node.js package configuration for the Nuxt.js application.
package-lock.json: The locked dependencies file for the Nuxt.js application.
public: Contains public assets for the Nuxt.js application.
server: Contains server middleware and configurations for Nuxt.js.
tsconfig.json: TypeScript configuration file for the Nuxt.js application.
docker-compose.yaml: The Docker Compose configuration file to define and run multi-container Docker applications.

nginx.conf: Configuration file for the Nginx web server acting as a reverse proxy.


## Getting Started

Follow these steps to run the application:

### 1. Clone the Repository

```bash
git clone https://github.com/Ahmeddiaa128/Challenge.git
cd Challenge

### 2. Build the Docker Images

Run the following command to build the images for the Laravel API and Nuxt.js client:

docker-compose build

### 3. Start the Services

docker-compose up -d

### 4. Access the Application

Access the application through the Nginx proxy at https://<ip-vm>


### 5. Stopping the Services

docker-compose down



