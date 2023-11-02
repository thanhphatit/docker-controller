# DOCKER CONTROLLER

This is tools created by bash shell to support for DevOps Engineer

- Create images and push to private server

NOTE:

    [+] Your machine need have bash and OS linux (Ubuntu is good)
    [+] The tools run on x86-64 and arm64 of linux (it's not support for macOS)
    [+] The tools must be placed in the git repository with located in the root folder

## SHORTENED NAME ENVIRONMENTS

| Environment | Shortened |
| --- | --- |
| Development | dev | 
| Staging | stg |
| User Acceptance Testing | uat |
| System Integration Test | sit |
| Production | prd|
| Disaster Recovery | drc |

## PATH

We will apply this format with identifier services have multi env
> environments/{env}/{provider}/{identifier}

Example: environments/stg/aws/eks

We will apply this format with identifier services have singal env
> environments/{company}/{provider}/{identifier}

Example: environments/itblognote/aws/s3/charts

## FILE INFO DATA

> `metadata.conf`

```
service_provider: ***
service_type: ***
service_identifier: ***
service_environment: ***
```

## VERSION

- Use character dash `.` between words, not using character underscore `-` between words.

```
0.0.1 => VALID
```

```
0-0-1 => NOT VALID
```

### DOCKER

#### Path

Usually a company will only need a Hub Registry containing images, so we will put the company name after the environments folder

Example:
> environments/itblognote/aws/ecr-name/metadata.conf

Case you want add Docker Images and Helm Chats same dir or you using ECR for Docker and Helm

```
environments/itblognote/aws/ecr-name/
                                |- images/
                                    |- ubuntu/
                                        |- apache2    
```

#### Setting file `metadata.conf`

| NAME | DOCKER | DIGITAL OCEAN | AZURE | AWS | GOOGLE CLOUD |
| --- | --- | --- | --- | --- | --- |
| service_provider | docker | doc | azure | aws | gcp |
| service_type | docker | dcr | acr | ecr | gcr |

service_identifier: We will add name of Hub Registry
service_environment: Name company becasue it is singal

#### Setting file `docker.info`

```
name: apache2.ubuntu
tag: 0.0.1
```

#### Delete mode

We will add 2 file to folder of Docker

Example Path: `environments/itblognote/aws/ecr-name/images/ubuntu/apache2/delete.lock`

* `delete.lock` Delete all docker images
* `delete.lock.tag` Delete with images and tag