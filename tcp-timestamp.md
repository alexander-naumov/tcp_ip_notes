## TCP timestamp option

TCP timestamps, defined in RFC 1323, can help TCP determine in which order packets were sent.
TCP timestamps are not normally aligned to the system clock and start at some random value. 
Many operating systems will increment the timestamp for every elapsed millisecond; 
however the RFC only states that the ticks should be proportional.

There are two timestamp fields:

* a 4-byte sender timestamp value (my timestamp)
* a 4-byte echo reply timestamp value (the most recent timestamp received from you).

TCP timestamps are used in an algorithm known as Protection Against Wrapped Sequence numbers, or PAWS (see RFC 1323 for details). 
PAWS is used when the receive window crosses the sequence number wraparound boundary. In the case where a packet was potentially 
retransmitted it answers the question: "Is this sequence number in the first 4 GB or the second?" And the timestamp is used to 
break the tie.

Also, the Eifel detection algorithm (RFC 3522) uses TCP timestamps to determine if retransmissions are occurring because 
packets are lost or simply out of order.
