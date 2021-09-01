# Kerberos 
## Terminology
- Key Distribution Center (KDC) database
	- Database of principles and associated keys
- Key Distribution Center (KDC) server
	- Central server that runs the authentication service and ticket granting service
- Principle
	- Verified client
- Realm
	- Administrative area of KDC
- Ticket Granting Ticker (TGT)
	- Initial certificate to identifiy a client
- Ticket Granting Service (TGS)
	- Service that runs on the KDC to issue tickets

## Authentication 
1. Client contacts authentication service
2. Authentication service produces a TGT
3. TGT is sent to the TGS
4. The TGS gives back a service ticket
5. Client presents the service ticket to the host
6. Service hosts decrypts it and grants access

- Passwords are never sent
- All data is encrypted

