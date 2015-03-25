## TCP Selective Acknowledgment

TCP Acknowledgment is cummulative so if a segment is lost or arrives out of order. All segments received after that segment has to be retransmitted.

TCP SACK allows receiver to keep out of order segements and inform the sender about gap and so it can retransmitt only these missing segments.

**SACK_PERM**

Parties notify each other about capability of allowing TCP SACK by setting SACK_PERM option in SYN and SYN/ACK segment.

    1012	10:08:03.050270000	ie-wk-128.wonga.com	csi.gstatic.com	TCP	66	54207 > http [SYN] Seq=0 Win=8192 Len=0 MSS=1460 WS=256 SACK_PERM=1
    1022	10:08:03.268625000	csi.gstatic.com	ie-wk-128.wonga.com	TCP	66	http > 54207 [SYN, ACK] Seq=0 Ack=1 Win=42900 Len=0 MSS=1387 SACK_PERM=1 WS=128

**SLE and SRE**

Receiver notify sender about  missing segment using left edge `SLE` and right edge `SRE`

    1377	10:08:06.406868000	ie-wk-128.wonga.com	proxy-gerrit02.aws.wonga.com	TCP	66	54242 > https [ACK] Seq=668 Ack=2311 Win=66304 Len=0 SLE=2045 SRE=2311

References

* https://tools.ietf.org/html/rfc2018
* http://packetlife.net/blog/2010/jun/17/tcp-selective-acknowledgments-sack/
