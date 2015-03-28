## Push vs Urgent Flag

Push flag is used by tcp stack to indicate that it is done with sending data. Note that user application make single call socket `send`,
the buffer then can be splited in to many TCP segments, the last one has push flag turn on. Upon receiving tcp stack forwards the segment immediately to the application. 

Urgent flag along with urgent pointer is used by application to indicate that urgent data is from the first byte until the 
urgent pointer. It is rarely used. In linux, tcp stack turn urgent flag on if we call socket `send` with `MSG_OBB` flag. 
The receiver will deliver the urgent segment out of the band by using signal `SIGURG` or the socket will become exceptional 
and can be checked as such using `select`.

References

* http://stackoverflow.com/questions/2264154/when-is-the-push-flag-set-in-tcp-segment
