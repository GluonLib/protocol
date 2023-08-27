# Gluon Protocol | Core concepts
This document describes a few core concepts of the Gluon protocol. Implementation specifics are left up to more precise
documents or the developer.

## Communication
### Nodes
Each _client_ or _server_ can be referred to as a _node_ of the network. This includes multiple instances running on the
same hardware, where each instance is handled as its own separate _node_.
When a node goes online it starts a new _session_, which will be closed once the node goes offline or the connection is
lost. Sessions can be used to track actions and map them to a specific application and / or point in time. Each session
has its own universally unique id.

### Packets
Gluon communication is fundamentally packet-based, meaning that any transmitted data is broken into discrete units in
consideration to the type of content that is being transmitted. While some packet types are provided by the Gluon
library, developers may use the existing structure of Gluon to implement their own application-specific packets. As long
as these can be represented in any required language, Gluon will handle (de-)serialization of data in the background.

A packet contains a data payload, which is usually referred to as the _content_, and some meta information, referred to
as the _header_.

The header can story an arbitrary number of entries in a key-value style. Forks or other modified versions of a Gluon
client or server node may use these header entries, while any other nodes can safely ignore them. Though, some
information is not optional. These entries are mandatory on every packet:
- Source node id
- Destination node id or mask for multiple nodes
- A unique sequencing number
- A hint on the type of the content
- Communications channel

### Channels
Channel-based communication is an extension of the packet-based communication, where a packet includes a header entry
specifying the _channel_ it belongs to.
Channels are logical communication pathways within the protocol, and they server as a means to categorize and segregate
packets based on their intended purpose or characteristics. This feature allows for a more fine-grained control over the
flow of data within the network, enabling nodes to selectively subscribe to and process packets from specific channels
while ignoring others.

Nodes within the network can dynamically open, close and otherwise maintain channels as needed. Subscription models are
used to determine which nodes listen to which channels, providing flexibility in network configuration and minimizing
useless traffic.

Different channels can have distinct configurations that optimize them for their specific use-case. One example would be
a higher level of encryption or additional security measures for channels that stream highly sensitive data. Other
channels may completely disregard encryption to ensure a faster transmission latency. Furthermore, channels can be
prioritized, ensuring that critical data is processed more quickly than less time-sensitive information or managing
limited bandwidth.
