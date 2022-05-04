# Docker - Tuffix

Install Docker Desktop

### Build:
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
if using prebuilt use `ghcr.io/madisonjordan/tuffix:backend2022` instead of shorter name

---

### Running Container:

#### Docker Desktop Launch
1. start Docker Desktop
2. start container created previously
3. click on "CLI" (`>_` icon)

#### VS Code
based on [VS Code Remote-Containers Docs](https://code.visualstudio.com/docs/remote/containers)

1. copy `.devcontainer` folder to same directory that also contains projects folders to mount
2. use `Remote-Containers: Reopen in Container` etc from VS Code Remote Extension
