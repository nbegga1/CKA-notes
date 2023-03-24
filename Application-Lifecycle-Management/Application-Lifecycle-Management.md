## Rolling Updates and Rollbacks

- ![image](https://user-images.githubusercontent.com/64038272/226172819-cb4bde84-008d-4cbd-af3e-9f959e706850.png)

## Commands

- When using the `CMD` command in the Dockerfile, if you use the `docker run` with paramaters the whole command specified in `CMD` will be **replaced**. However when using the `ENTRYPOINT` command the parameter you append to the `docker run` command will be **appended** to the command specified in the `ENTRYPOINT`.
- If you want to override the `ENTRYPOINT` command specified in the Dockerfile, use the `--entrypoint` option with the `docker run` command.

## Environment variables

- Different ways to use Environment variables in pod.spec.container:
  - ![image](https://user-images.githubusercontent.com/64038272/226418138-0e135033-f746-4acb-9b07-eac39d0acb5f.png)
  - ![image](https://user-images.githubusercontent.com/64038272/226418440-f4619848-4f38-47e0-a646-56fcbbe94824.png)

## Secrets

- Encode secret: `echo -n <secret> | base64`
- Decode secret: `echo -n <secret> | decode`
- Create secret imperative way: `kubectl create secret generic my-secret --from-literal=<key1>=<supersecret> --from-literal=<key2>=<topsecret>`
- Inject secret in pod: ![image](https://user-images.githubusercontent.com/64038272/226535696-280e8213-14df-4dc5-bfd0-4d75ace7588b.png)

## Multi-container pods

- The containers are on the same network, they can call each other by `localhost`
- They can share the same volumes
- ![image](https://user-images.githubusercontent.com/64038272/226541094-8faf2686-335f-4621-8a55-6508fd1b7078.png)

## Init Containers


