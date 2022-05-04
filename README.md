# Docker - Tuffix

Install Docker Desktop

## VS Code

based on [VS Code Remote-Containers Docs](https://code.visualstudio.com/docs/remote/containers)

_don't need to pull image_

1. copy `.devcontainer` folder to same directory that also contains projects folders to mount
2. from VS Code > Open Folder. Open the folder containing `.devcontainer` from step 1
3. use `Remote-Containers: Reopen in Container` etc from VS Code Remote Extension

   _note: it should prompt you with a notification to reopen in the container when you are in the folder in step 2_

## Building / Running without VS Code

### Build:

_skip this step if you will be using vscode Remote-Containers extension_

`docker build -t ghcr.io/madisonjordan/tuffix:backend2022 -f Dockerfile .`

OR get pre-built image:

`docker pull ghcr.io/madisonjordan/tuffix:backend2022`

---

### Create/Run Container (CLI):

```
docker run \
-it \
-v %cd%:/home/projects \
ghcr.io/madisonjordan/tuffix:backend2022 \
/bin/bash
```

---

### Running Container:

#### Docker Desktop Launch

1. start Docker Desktop
2. start container created previously
3. click on "CLI" (`>_` icon)
