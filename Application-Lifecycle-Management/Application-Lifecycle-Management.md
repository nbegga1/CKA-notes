## Rolling Updates and Rollbacks

- ![image](https://user-images.githubusercontent.com/64038272/226172819-cb4bde84-008d-4cbd-af3e-9f959e706850.png)

## Commands

- When using the `CMD` command in the Dockerfile, if you use the `docker run` with paramaters the whole command specified in `CMD` will be **replaced**. However when using the `ENTRYPOINT` command the parameter you append to the `docker run` command will be **appended** to the command specified in the `ENTRYPOINT`.
- If you want to override the `ENTRYPOINT` command specified in the Dockerfile, use the `--entrypoint` option with the `docker run` command.

## Environment variables

- ![image](https://user-images.githubusercontent.com/64038272/226418138-0e135033-f746-4acb-9b07-eac39d0acb5f.png)
- ![image](https://user-images.githubusercontent.com/64038272/226418440-f4619848-4f38-47e0-a646-56fcbbe94824.png)
