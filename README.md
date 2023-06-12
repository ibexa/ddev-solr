# DDEV Solr Addon

This repository, `ibexa/ddev-solr` is a [DDEV add-on](https://ddev.readthedocs.io/en/latest/users/extend/additional-services/) that provides Solr service for Ibexa DXP. It uses the [Bitnami Solr image](https://bitnami.com/stack/solr/containers) and provides default configurations.

## Introduction

This repository is designed to help developers set up Solr for use with Ibexa DXP using DDEV. It is not a standalone project but is meant to be used in conjunction with your existing Ibexa DXP project and DDEV setup.

## Documentation

Before you start, it's important to familiarize yourself with the relevant documentation:

- [Ibexa DXP Documentation](https://doc.ibexa.co/en/latest/)
- [Solr Search Engine Documentation for Ibexa DXP](https://doc.ibexa.co/en/latest/search/solr_search_engine/)
- [DDEV Documentation](https://ddev.readthedocs.io/en/stable/)

## Getting Started

To use this configuration, you'll need to have DDEV installed and an existing Ibexa DXP project set up. Once you have those ready, you can use the DDEV `get` command to fetch this configuration and set up Solr for your project.

```bash
ddev get ibexa/ddev-solr
```

## Configuration

This add-on is configuring itself out-of-the-box, setting itself as the search engine for Ibexa DXP and configuring the connection.

### Internals

The `config.solr.yaml` file contains the following configurations:

- `web_environment`: Defines the environment variables for the web service container.
- `hooks`: Defines the actions to be performed after the service starts. In this case, it waits for Solr to start and then **proceeds with reindexing**.

The `docker-compose.solr.yaml` file defines the Solr service, including the container name, image, labels, environment variables, volumes, and healthcheck. It also defines a persistent Docker volume for Solr data.

Those files will be copied over to `.ddev` folder of the project, when the addon is installed via `ddev get` command.

## Contributing

Contributions to this repository are welcome. If you encounter any issues or have suggestions for improvements, please open an issue in the repository.
