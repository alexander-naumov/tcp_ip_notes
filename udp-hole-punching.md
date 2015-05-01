## UDP hole punching

UDP hole punching is technique that enables peer to peer commnication where they are behind NAT firewall. Basically if 
the NAT firewall allows UDP, it will work unless NAT symetric or restricted cone NAT is imposed.

An known intermediary is used by a peer to exchange their public facing `IP:PORT` with its counterpart. Once they know each 
other public `IP:PORT`, they use it for communication.

This technique is commonly used by a client of peer to peer network e.g. VOIP device, Skype.

**References**

* http://en.wikipedia.org/wiki/UDP_hole_punching
