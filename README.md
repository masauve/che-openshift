# che-openshift


Pre-requisites

Admin access to an OpenShift instance.
Access to the OpenShift instance from the laptop where Eclipse CHE will be running.
Docker engine running on your laptop.

Instructions for various Operating Systems can be found here: https://docs.docker.com/engine/installation/

Step 1 - Prepare your laptop

Verify that your Docker engine is running
Set JAVA_HOME to the location of a JDK 1.8
Set DOCKER_HOST to localhost
Verify that port 8080 is available on your laptop

Step 2 - Download Eclipse CHE with OpenShift plugin

http://maven.codenvycorp.com/content/repositories/codenvy-public-snapshots/org/eclipse/che/openshift-plugin-assembly-main/4.6.0-SNAPSHOT/

Step 3 - Unzip Eclipse Che to a directory of your choice - $CHE_HOME.

If you are not installing in your home directory, Step 6a will have to be executed. By default, docker-machine only mounts the home filesystem in the docker machine. Eclipse CHE will need access to the file system where it is installed.

Step 4 - Create CHE user in OpenShift and obtain OAuthToken

Using your configured OpenShift security provider, add a user for Eclipse Che. In this example, I will use username: che

Request an OAuthToken for username: che  
https://10.1.2.2:8443/oauth/token/request
login as che
copy the token

Step 5 - Create CHE configuration files

Create the configuration file on your laptop as described here:
https://eclipse-che.readme.io/docs/openshift-config

oauth.openshift.clientid=che
oauth.openshift.clientsecret=$OPENSHIFT_OAUTH_TOKEN

Step 6 - Start Eclipse CHE

$CHE_HOME/bin/che.sh

Step 6a (if required) - Mount Eclipse CHE filesystem in che docker-machine

Before creating a workspace, if you have installed CHE outside your home directory, you will need to mount the CHE installation directory inside your docker-machine.

https://gist.github.com/cristobal/fcb0987871d7e1f7449e  
contains a script that you can use.

machine-diskutil.sh mount che $CHE_HOME

restart Eclipse Che


Step 7 - Create CHE workspace

Step 8 - Connect to OpenShift

Step 9 - Create project

Step 10 - Validate Environment
