graphite-amqp-tools
===================

_(A slight misnomer in that this branch actually supports STOMP)_

Basically gluing https://github.com/bodgit/libevent-stomp and https://github.com/bodgit/libevent-graphite together to make the following pair of daemons that should be reasonably efficient and have low memory usage:

* graphite-enqueue - provides the graphite TCP line receiver protocol and forwards all received messages on to a given STOMP destination. Uses libevent2 to handle multiple clients simultaneously.

* graphite-dequeue - does the opposite, receives messages from a given STOMP source and posts them on to a given graphite TCP line receiver.

Both daemons can use SSL to connect to the STOMP server and also periodically send their own various statistics to a given graphite TCP destination.