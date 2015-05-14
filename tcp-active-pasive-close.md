## TCP active vs passive close

Parties participated in TCP session can close direction of communication by sending `FIN` segment to other. To fully close TCP session both parties have to do so. Party sending the `FIN` segment before receiving `FIN` from other follows active close path. Party sending `FIN` after receiving `FIN` from other follows passive close path.

See [tcp half close](tcp-half-close.md)
