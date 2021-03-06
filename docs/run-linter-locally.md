# Run Super-Linter locally to test your branch of code
If you want to test locally against the **Super-Linter** to test your branch of code, you will need to complete the following:
- Clone your testing source code to your local environment
- Install Docker to your local environment
- Pull the container down
- Run the container
- Debug/Troubleshoot

## Install Docker to your local machine
You can follow the link below on how to install and configure **Docker** on your local machine
- [Docker Install Documentation](https://docs.docker.com/install/)

## Download the latest Super-Linter Docker container
- Pull the latest **Docker** container down from **DockerHub**
  - `docker pull admiralawkbar/super-linter:latest`
Once the container has been downloaded to your local environment, you can then begin the process, or running the container against your codebase.

## Run the container Locally
- You can run the container locally with the following **Base** flags to run your code:
  - `docker run -e RUN_LOCAL=true -v /path/to/local/codebase:/tmp/lint admiralawkbar/super-linter`
    - To run against a single file you can use: `docker run -e RUN_LOCAL=true -v /path/to/local/codebase/file:/tmp/lint/file admiralawkbar/super-linter`
  - **NOTE:** You need to pass the `RUN_LOCAL` flag to bypass some of the GitHub Actions checks, as well as the mapping of your local codebase to `/tmp/lint` so that the linter can pick up the code
  - **NOTE:** The flag:`RUN_LOCAL` will set: `VALIDATE_ALL_CODEBASE` to true. This means it will scan **all** the files in the directory you have mapped. If you want to only validate a subset of your codebase, map a folder with only the files you wish to have linted

### Flags for running Locally
You can add as many **Additional** flags as needed:

| **ENV VAR** | **Command** | **Default Value** | **Notes** |
| --- | --- | --- | --- |
| **VALIDATE_YAML** | `-e VALIDATE_YAML=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_JSON** | `-e VALIDATE_JSON=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_XML** | `-e VALIDATE_XML=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_MD** | `-e VALIDATE_MD=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_BASH** | `-e VALIDATE_BASH=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_PERL** | `-e VALIDATE_PERL=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_PYTHON** | `-e VALIDATE_PYTHON=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_RUBY** | `-e VALIDATE_RUBY=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_COFFEE** | `-e VALIDATE_COFFEE=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_ANSIBLE** | `-e VALIDATE_ANSIBLE=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_JAVASCRIPT_ES** | `-e VALIDATE_JAVASCRIPT_ES=<true\|false>` | `true` | Flag to enable or disable the linting process of the language (Utilizing: eslint) |
| **VALIDATE_JAVASCRIPT_STANDARD** | `-e VALIDATE_JAVASCRIPT_STANDARD=<true\|false>` | `true` | Flag to enable or disable the linting process of the language (Utilizing: standard) |
| **VALIDATE_TYPESCRIPT_ES** | `-e VALIDATE_TYPESCRIPT_ES=<true\|false>` | `true` | Flag to enable or disable the linting process of the language (Utilizing: eslint) |
| **VALIDATE_TYPESCRIPT_STANDARD** | `-e VALIDATE_TYPESCRIPT_STANDARD=<true\|false>` | `true` | Flag to enable or disable the linting process of the language (Utilizing: standard) |
| **VALIDATE_DOCKER** | `-e VALIDATE_DOCKER=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_GO** | `-e VALIDATE_GO=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **VALIDATE_TERRAFORM** | `-e VALIDATE_TERRAFORM=<true\|false>` | `true` | Flag to enable or disable the linting process of the language |
| **ANSIBLE_DIRECTORY** | `-e ANSIBLE_DIRECTORY=</path/local/to/codebase/with/ansible>` | `/ansible` | Flag to set the root directory for Ansible file location(s) |
| **ACTIONS_RUNNER_DEBUG** | `-e ACTIONS_RUNNER_DEBUG=<true\|false>` | `false` | Flag to enable or disable additional debug info |

## Troubleshooting

### Run container and gain access to the command line
If you need to run the container locally and gain access to its command line, you can run the following command:
- `docker run -it --entrypoint /bin/bash admiralawkbar/super-linter`
- This will drop you in the command line of the docker container for any testing or troubleshooting that may be needed.

### Found issues
If you find a *bug* or *issue*, please open a **GitHub** issue at: `https://github.com/github/super-linter/issues`
