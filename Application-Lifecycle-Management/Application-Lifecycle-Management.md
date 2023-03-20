## Rolling Updates and Rollbacks

- ![image](https://user-images.githubusercontent.com/64038272/226172819-cb4bde84-008d-4cbd-af3e-9f959e706850.png)

## Commands

- When using the `CMD` command in the Dockerfile, if you use the `docker run` with paramaters the whole command specified in `CMD` will be **replaced**. However when using the `ENTRYPOINT` command the parameter you append to the `docker run` command will be **appended** to the command specified in the ENTRYPOINT 
