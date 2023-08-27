![Static Badge](https://img.shields.io/badge/protocol%20version-0_(dev)-yellow)
# Gluon protocol
This document outlines the design and specifications of a packet-based communication protocol aimed at facilitating
seamless data exchange between applications separated by network- or language barriers. The protocol defines a
structured message format, error handling mechanisms, and guidelines for efficient, reliable and language-agnostic
communication.

The protocol emphasizes flexibility and extensibility, allowing developers to adapt to evolving communication
requirements while maintaining backward compatibility. It employs a binary message format, optimized for performance,
and includes features such as pre-established message type identification, manageable encryption, event-based
communication basic mechanisms for simple shared state and automated versioning to ensure message integrity and
compatibility.

Errors are handled via standardized response- and error-codes that enable clear identification of points of failure
without giving up too much simplicity and ease of use. Developers can implement error recovery and diagnostic strategies
based on these codes and messages.

By adhering to this protocol, applications that are separated by network- or language-barriers can establish a robust
and efficient communication-link. Comprehensive documentation and tooling are provided to assist developers in the
implementation and integration of this protocol into their applications.

Gluon aims to simplify cross-language communication challenges and promote interoperability of simple applications.

### Early development notice
Please note that this library is still in early development and not officially supported until the first release.

# Table of contents
| Chapter | Title                               | Description                                                                                 |
|---------|-------------------------------------|---------------------------------------------------------------------------------------------|
| 1       | [Conformance](Conformance.md)       | A set of standards that rarely change across versions, mainly to establish universal rules. |
| 2       | [Core concepts](Core%20Concepts.md) | Terminology and definitions of the Gluon basics.                                            |
