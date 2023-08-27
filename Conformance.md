# Gluon protocol | Conformance
## Protocol Version
The protocol version is defined as a single integer that is incremented with every breaking modification to any standard.
Any implementation of this protocol of a given version _n_ must be compatible with any other implementation of that same
version _n_. Cross compatibility is allowed in the form of a version negotiation during the initial handshake. Usually,
the server will downgrade to an older version to establish a viable connection to a client with that older version.

Any valid version number must be greater than 0. Version 0 is reserved for development purposes while negative version
numbers may be used for testing or closed environments.