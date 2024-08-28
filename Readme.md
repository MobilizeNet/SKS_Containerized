# Containerizing SKS-WebMap .NET8 Application with Docker

Containerization has become a pivotal technology in modern software development, offering a portable and efficient way to package, distribute, and run applications across diverse environments. This documentation serves as a guide to containerize a .NET application using Docker platform for container orchestration.

By encapsulating your .NET application within a Docker container, you gain advantages such as isolation, reproducibility, and scalability. This step-by-step guide will walk you through the process of creating a Docker image for your application, allowing it to run seamlessly on any system equipped with Docker.

To run this Docker Compose file and the associated container, you will need to ensure that you have the following prerequisites in place:

1. Docker: Install Docker on your machine. You can download and install Docker from the [official Docker website](https://docs.docker.com/engine/install/).

2. Docker Compose: Install [Docker Compose](https://docs.docker.com/compose/), which is a tool for defining and running multi-container Docker applications. Docker Compose is typically included with Docker Desktop for Windows and macOS, but you can also install it separately if needed.

Once you have the prerequisites installed, follow these steps to run the Docker Compose file:

1. Open a terminal or command prompt.

2. Navigate to the directory where your Docker Compose file is located. For example `.../downloads/SKS`.

3. Run the following command to start the containers defined in the Docker Compose file:

    ```
    docker compose up --build
    ```

    This command will build and start the containers specified in the Compose file. If the containers are already built, it will start them without rebuilding.

4. Wait for the containers to start up. You will see logs and output from the containers in the terminal.

5. Once the containers are up and running, you can access the services provided by the containers. Open a browser and then type the folllowing direction:

    ```
    localhost:90
    ```
You will see something like that:
    ![SKS running on localhost](https://raw.githubusercontent.com/MobilizeNet/SKS_Containerized/master/SKS/images/sks-image.png)

That's it! You have successfully run the Docker Compose file and started the associated containers. Remember to stop the containers when you are done using the following command:

```
docker-compose down
```

This will stop and remove the containers defined in the Docker Compose file.