# karamel-docker
This is the repository to store resources related to Karamel Docker integration

### Generating Docker image to use as the base image

[Docker definition](https://github.com/shelan/karamel-docker/tree/master/docker-image) is used to generate the basic image for Karamel. This includes several funtionalities such as

* Passwordless SSH user
* SSH server
* Vagrant default SSH key is used (change for a secure key according to the requirement)
* Chefdk and berkshelf installation
* openJDK 7 installation
* Port 22 is used for SSH

