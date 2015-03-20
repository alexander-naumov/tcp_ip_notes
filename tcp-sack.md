## TCP Selective Acknowledgment

TCP Acknowledgment is cummulative so if a segment is lost or arrives out of order. All segments from that segment has to be 
retransmitted.

TCP SACK allows receiver to inform the sender about gap and so it can retransmitt only these missing segments.

References

* https://tools.ietf.org/html/rfc2018
