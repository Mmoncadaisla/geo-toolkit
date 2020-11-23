# Geo-Toolkit 

## What's in this repository


## Repository file structure

```
|____README.md
|____postgres
| |____alpine
| |____initdb-postgis.sh
| |____Dockerfile
| |____update-postgis.sh
|____docker-compose.yml
|____.git
|____data
| |____.gitkeep
|____notebooks
|____jupyter
| |____Dockerfile
| |____fonts
```

## Set up with docker-compose

>NOTE: to install this environment both [docker](https://docs.docker.com/get-docker/) and [docker-compose](https://docs.docker.com/compose/) are required

1. Clone the repository [using git](https://git-scm.com/docs/git-clone)

```bash
git clone https://github.com/Mmoncadaisla/geo-toolkit.git
```

2. Move to the main repository's folder 

3. Build with docker-compose build

```bash
docker-compose build
```

4. Start the corresponding containers with docker-compose up

```bash
docker-compose up
```

5. Access the link to access Jupyter within the notebooks directory 

To access the database through `psql` you could run the following,

1. Open a new terminal in the postgres container

```bash
docker exec -it geo-toolkit_postgres_1 /bin/bash
```

2. Initialize psql with user postgres

```bash
psql -U postgres
```
