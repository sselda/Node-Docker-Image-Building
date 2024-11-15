Node.js Docker Image Project
This project demonstrates how to create a Docker image for a simple Node.js application. The Dockerfile is configured to use the official Node.js image and includes the necessary steps to build, install dependencies, and run the application inside a Docker container.

Project Structure
css
Code kopieren
.
├── Dockerfile
├── src
│   ├── server.js
│   └── package.json
└── README.md

> Dockerfile: Defines the steps to build the Docker image.
> src/server.js: Main application file for the Node.js server.
> package.json: Contains the dependencies and configuration for the Node.js application.

Prerequisites

> Docker installed on your system.
> Building the Docker Image
> To build the Docker image, navigate to the project directory (where the Dockerfile is located) and run the following command:

> bash
> Code kopieren
>> docker build -t node-app:1.0 -f src/Dockerfile .
>> -t node-app:1.0: Tags the image as node-app with version 1.0.
>> -f src/Dockerfile: Specifies the path to the Dockerfile in the src folder.

Running the Docker Container
>Once the image is built, you can run the container with this command:

bash
Code kopieren
>> docker run -d -p 9000:80 node-app:1.0
>> -d: Runs the container in detached mode.
>> -p 9000:80: Maps port 80 of the container to port 9000 on your machine.
You can now access the application by going to http://localhost:9000 in your browser.

Dockerfile Explanation
Here’s a breakdown of what each line in the Dockerfile does:

1.FROM node:19-alpine: Uses the lightweight Node.js Alpine image as the base.
2.COPY package.json /usr/app/: Copies the package.json file to the /usr/app/ directory in the container.
3.COPY src /usr/app/: Copies all files from the src folder to the /usr/app/ directory in the container.
4.WORKDIR /usr/app: Sets the working directory to /usr/app.
5.RUN npm install: Installs the dependencies specified in package.json.
6.CMD ["node", "server.js"]: Starts the Node.js application.

Additional Notes
This setup uses Node.js 19 (Alpine version) for a smaller, more efficient image size.
You can customize the Dockerfile and application files as needed.

Troubleshooting
If you encounter issues during the build process, ensure that:

The Dockerfile path is correctly specified.
Docker is running and properly installed.
Port 9000 is not occupied by another service.
