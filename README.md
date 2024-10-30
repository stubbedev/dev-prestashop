# Prestashop DEV Environments

<!--toc:start-->
- [Prestashop DEV Environments](#prestashop-dev-environments)
  - [HOW TO](#how-to)
<!--toc:end-->

## HOW TO

You need to have docker and docker compose installed. Please follow the appropriate guide found [here](https://docs.docker.com/engine/install/).

Once you have docker installed you can pick your version of prestashop you wish to run.

As an example if you wanted to run the latest, you would run the following command from the root of this project.

```bash
cd latest && sudo docker compose up -d
```

Note that this requires port `8080` to be free for binding. If you have any other service bound to this port, you need to stop it for the container to launch.
If you previously ran another container with a different version, simply stop that container first.

The first time the container is composed/started, you will see the wizard for installing the prestashop version.

Here you can choose whatever you like for the user email and password, you just need to remember them.

The database should be configured to use the following:

```yaml
DB_SERVER: mysql
DB_NAME: prestashop
DB_USER: root
DB_PASSWD: password
```

The value for HOST should just be the string `mysql`

After the initial installation process, the wizard will ask you to do 2 things.

1. Delete the `install` directory.
2. Rename the `admin` directory.

Both of these directories can be found in the `./app` directory located alongside the docker-compose.yml file you chose to compose from.

The `install` directory you just outright delete.

The `admin` directory you rename to anything you like, Eg. `admin_24601`

You should now be able to access your local prestashop environment in the following ways:

- frontend: http://localhost:8080
- admin: http://localhost:8080/admin_24601
- files: `./app`

In case you want to edit the clerk module for example, it would be located in `./app/modules/clerk` after installing it.
