
Katzenpost Mixnet Docker
========================

This docker-compose configuration is a fork of the `katzenpost docker configuration`_. This configuration contains Meson-specific configs and is meant to be used in combination
with the **server** and **authority** repositories. It is meant for
testing client and server mix network components as part of the core
Katzenpost developer work flow. It should be obvious that this
docker-compose situation is not meant for production use.

1. build the mix server docker image
::

   cd server
   docker build --no-cache -t katzenpost/server .


2. build the authority docker image

nonvoting authority
::

   cd authority
   docker build -f Dockerfile.nonvoting --no-cache -t katzenpost/nonvoting_authority .


3. run docker-compose from this repository and cd into one of the folders depending on your usecase (control-c to exit)
::

   cd nonvoting_mixnet
   docker-compose up


**NOTE**: between restarting your local docker mixnet you **SHOULD**
remove the state changes on disk by running the following command:
::

   git clean -ffdx


**NOTE**: If you switch between voting and nonvoting authority mixnets then
you must run this command after shutting down the old docker composed mixnet:
::

   docker network prune

.. _`katzenpost docker configuration`: https://github.com/katzenpost/docker
