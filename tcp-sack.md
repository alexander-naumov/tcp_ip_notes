## TCP Selective Acknowledgment

TCP Acknowledgment is cummulative so if a segment is lost or arrives out of order. All segments received after that segment has to be retransmitted.

TCP SACK allows receiver to keep out of order segements and inform the sender about gap and so it can retransmitt only these missing segments.

References

* https://tools.ietf.org/html/rfc2018
* http://packetlife.net/blog/2010/jun/17/tcp-selective-acknowledgments-sack/
