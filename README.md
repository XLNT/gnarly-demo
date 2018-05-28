# Gnarly Demo

> This is a super simple demo of how gnarly and paperboy work together to produce an event feed.

It uses the `:demo` tags of `shrugs/gnarly-test` and `shrugs/paperboy`, which may eventually be out of date.

## Setup

This demo relies on `docker-compose`. If you don't have it already, [install docker](https://docs.docker.com/install/) and then install [docker-compose](https://docs.docker.com/compose/install/). Install instructions vary between machines, so [check the website](https://docs.docker.com/install/) for up-to-date docs.

_Note: unfortunately, gnarly and paperboy don't attempt reconnects on failure just yet, so the services need to be started in the correct order._

1. `docker-compose up -d postgres` and wait for it to be happy (~5 seconds), then
2. `docker-compose up -d gnarly`
3. in a separate window `docker-compose logs -f gnarly`
4. `docker-compose up -d paperboy`
5. `docker-compose up an-old-man-at-a-cafe-in-the-50s`

## Description

The postgres image is just vanilla postgres; nothing special.

Gnarly is configured with the erc721, blocks, and events reducers and is in charge of monitoring the blockchain and putting all that nice info in postgres for us.

Paperboy is just a websocket server that queries against the postgres `events` table for events that match the filter options you provide.

And `an-old-man-at-a-cafe-in-the-50s` is the image that reads the events that the paperboy delivers. It's just a dumb websocket client packaged as a docker container, nothing special.

Note that this docker-compose file exposes paperboy's port (`3000`) to your host, so you can query it yourself, following the details in the [paperboy repo](https://github.com/XLNT/paperboy)
