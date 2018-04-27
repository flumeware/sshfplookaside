This is a patch for OpenSSH that adds support for lookaside sshfp retrival. This can be used where your main zone is for some reason not dnssec signed but you would like to take advantage of sshfp records for hosts contained within it.
By configuring clients to use lookaside validation for the host key, ssh will check for sshfp records that validate at both the hostname but also at *hostname*.*lookaside-zone* if the hostname does not have any valid sshfp records.

The patch has been tested against OpenSSH 7.4

The patch adds to config options to ssh **VerifyHostKeyDNSLookaside** and **VerifyHostKeyDNSLookasideName**. The first one should be set to yes to enable lookaside support and the second should be the zone you would like to do lookaside under. For lookaside validation to be used **VerifyHostKeyDns** must be either ask or yes.
