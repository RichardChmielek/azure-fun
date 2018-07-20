# azure-func

## Sample dockerfile usage

1. Build and publish azure func binaries to ./out folder. This can be done by running following command:

    ```bash
    dotnet publish -c release -o out
    ```

2. Create your own docker file

    ```bash
    FROM richardchmielek/azure-func:latest

    WORKDIR /app
    COPY ./out .
    ENV AzureWebJobsScriptRoot=/app

    ENTRYPOINT [ "func", "start" ]
    ```

3. Docker run

    ```bash
    docker run -it -p 7071:80 <YOUR_IMAGE>:<YOUR_TAG>
    ```

4. Execute (curl) function example

    ```bash
    curl http://localhost:7071/api/<YOUR_GET_FUNCTION>
    ```
