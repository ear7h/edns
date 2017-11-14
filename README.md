# ear7h DNS

this package is a successor to the e7 protocol. Rather than using a distributed architecture with each node a dns server. edns uses a master-slave architecture with the master node being the only dns server. 


## contents
* child/ - package for child server
    * use own repository to run
* master/ - package for dns server
    * use own repository to run
* edns/ - main package for administration through cli
* client_functions.go - exported library functions for programmatic administration

## differences from e7
* redis as a back end
* *username* and password authentication
    * root password built in
    * additional password module which uses the server record "auth"
    * "*.auth.domain.tld" should route to the authentication server. It then returns ok(200) or forbidden(403) for the service
    
 ## slave nodes
 * track attached services
 * reverse proxies request to the service based on the requested host
    * gets tls certs for services
 * renew edns records for services


__todo__
* not hardcoded authentication
* logging