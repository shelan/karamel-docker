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


### How to view Docker containers visually to obtain port mappings ?

You can download & install [Simple Docker UI chrome plugin] (https://chrome.google.com/webstore/detail/simple-docker-ui/jfaelnolkgonnjdlkfokjadedkacbnib). Then in the settings add Docker URL for each host. URL will be http://<publicIp of host machine>:2375

Then in the UI following details can be visualized.


