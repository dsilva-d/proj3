For our milestone, we were able to implement the acceptance of messages of type "update" to call our update method, "dump" to call our dump method and "data" to handle simple instances of choosing a path, calling our send\_data method.
We added the field "asn" as a unique identifier to each of our routes.
For most of our get\_route helper functions, apart from lookup\_routes which removes the file digit indicating the number of hosts and replaces it with the network ip, we return the unaffected list of routes we have from this source and picks the first listed. Later, we will implement these helpers to narrow down a larger list of potential routes. 
We added a send\_data function which calls get\_route to create a connection to the destination packet given the source. 
Our forward method adds the given route's asn number to the ASPath of the packet given, if the packet has the type 'cust', will switch the source address with our local address and have the destination of the packet be each other neighbors, and send the given packet to each other neighbor.
Our update method stores the packet of a the specified source in our updates field, converts the 'msg' in the packet to network format provided, and calls the forward method on the source and packet.
We also added an argument in our \_\_main\_\_ for specifying an ASN.
