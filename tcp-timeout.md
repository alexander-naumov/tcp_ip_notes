## TCP timeout

There are 4 kind of timeout used in TCP

1. Retransmission timeout: restart when a segment is sent
2. Persist timeout: restart window size of other end is 0
3. Keepalive timeout: restart when a segment is send or received. Is used to prevent half open (see also [tcp half close](tcp-half-close.md)) when connection is idle for long time
4. 2xMSL - Maximum Segment Life: start when state is TIMEWAIT

**Retransmission timeout**

Retransmission interval is estimated using estimated RTT - Round Trip Time. Initially it is calculated as follow

    RTT = a*RTT + (1 - a)*SampleRTT where 0 < a < 1
    RTO = 2*RTT

To be more robust on variability of RTT, the new method to calculate RTO is introduced using deviation of SampleRTT

    SampleDev = |SampleRTT − RTT|
    Deviation = b*Deviation + (1 - b)*SampleDev where 0 < b < 1
    RTO = RTT + 4*Deviation
 

**Persist timeout**

When a sender want to send data and windows size of the receiver is 0, then the sender keep sending probe to receiver at each retransmission interval to prevent dead lock when segment of windows size from receiver is lost.

**Keepalive Timeout**

Keepalive timeout is controled by

    # cat /proc/sys/net/ipv4/tcp_keepalive_time 
    7200
    # cat /proc/sys/net/ipv4/tcp_keepalive_intvl 
    75
    # cat /proc/sys/net/ipv4/tcp_keepalive_probes 
    9

The above values mean first probe will be sent after 2 hours (7200 secs) and repeat after each 75 secs. If receives no ACK for 9 consecutive times the the connection is marked as broken.

References

* http://intronetworks.cs.luc.edu/1/html/tcp.html#tcp-timeout-and-retransmission
* http://tldp.org/HOWTO/TCP-Keepalive-HOWTO/usingkeepalive.html
* http://sgros.blogspot.ie/2012/02/calculating-tcp-rto.html
