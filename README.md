# Netdata deployment

This ansible role aims to deploy netdata easily and eventually make them interact with each others.

# Supported OS/version

Currently, this role was only tested against debian 10. *It may not work with other OS !*
The only installation possible is with docker (and docker-compose).
The only type of installation possible is a master node.

# Installation

## Configuration

The configuration of netdata's deployment relies on some variables defined by
default, which should make it work out of the box. To configure it, please
have a look at [the default values](defaults/main.yml) to override them.
Variables should be self-explanatory, and if there aren't, there should be a
link to the netdata documentation.

The only "homemade" parameter is the `nd_node_type`, explained right here:

## Node type

To ease the netdata deployment, this role provide a variable, `nd_node_type`
which will determine which settings should be applied depending on the
role you're willing to give to this node.
Here are the available role :

| type | use | status |
|:-----|:---:|-------:|
| master | Used to be the master node of a cluster. Enables the web interface and the database. Allows other netdata to stream their collected data to it. | Partially implemented |
| slave | Used to stream to a master node only. Does not have any web interface not database. | To be implemented |
| single | Used to be a single node, without further interaction with other nodes | To be implemented |

# TODO

- `slave` mode to stream to master
- Other install type than docker
- Database backend configuration options
- Test on other OS for maximum compatibility
