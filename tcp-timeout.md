## TCP timeout

There are 4 kind of timeout used in TCP

1. Retransmission timeout: restart when a segment is sent
2. Persist timeout: restart window size of other end is 0
3. Keepalive timeout: restart when a segment is send or received. Is used to prevent half open see also [tcp half close](tcp-half-close.md) when connection is idle for long time
4. 2xMSL - Maximum Segment Life: start when state is TIMEWAIT

References

* http://intronetworks.cs.luc.edu/1/html/tcp.html#tcp-timeout-and-retransmission
