# SEEDLabs
Collection the [SEED](https://seedsecuritylabs.org/Labs_20.04/) (SEcurity EDucation) labs, focusing on network and web security.

# Labs
## PKI (Public Key Infrastructure)
A lab focused on hands on application of public key encryption and how they interact with certificates.  
[Lab Instructions](https://seedsecuritylabs.org/Labs_20.04/Files/Crypto_PKI/Crypto_PKI.pdf)   
[Lab Report](Labs/thomas-PKI-SEEDLab.pdf)   
### Key Concepts & Tasks:
 - Certificate Authority (CA): Acted as root CA, generating self-signed certificates and managing the CA's private key.
 - Certificate Signing: Generated server-side RSA key pairs, created Certificate Signing Requests (CSRs) and used the CA to sign them.
 - Certificate Deployment: Deployed a signed certificate over an Apache web server, configuring the site for HTTPS.
 - Man-in-the-middle Attack:
   - Simulated a DNS cache poisoning attack to redirect a legitimate domain (royalroad.com) to a malicious server.
   - Demonstrated how browsers detect a domain mismatch in a certificate.
   - Leverage a compromised root CA to successfully trick the browser into trusting the malicious site.
 - Tech Stack
   - OpenSSL, Apache2, Docker
     
---
## TLS (Transport Layer Security)
Focus on the Transport Layer of security, with a tighter emphasis the handshake protocol used to secure trust between devices.
[Lab Instructions](https://seedsecuritylabs.org/Labs_20.04/Files/Crypto_TLS/Crypto_TLS.pdf)  
[Lab Report](Labs/thomas-TLS-SEEDLab.pdf)  
### Key Concepts & Tasks
 - Handshake Analysis: Utilized Python to initiate a TLS handshake and inspect the server's certificate chain and cipher suite.
 - Certificate Validation: Explored client-side stored certificates and demonstrated how hostname validation prevents spoofing.
 - TLS Proxy (MITM):
   - Built a python-based TLS proxy server that caught network traffic between the client and a legitimate site.
   - The proxy successfully intercepted traffic between client and target server (crunch.com) by dynamically managing separate TLS connections.
   - Printed capture data in plaintext.
 - Tech Stack
   - Python, OpenSSL, Docker
     
## DNSSEC (Domain Name System Security)
A hands on and in depth approach to how DNSSEC is used. Large emphasis on verifying the trust chain and how multiple domains interact with each other.
[Lab Instructions](https://seedsecuritylabs.org/Labs_20.04/Files/DNSSEC/DNSSEC.pdf)  
[Lab Report](Labs/thomas-DNSSEC-SEEDLab.pdf)  
### Key Concepts & Tasks
 - Key Generation: Generated and managed Key-Signing Keys (KSK) and Zone-Signing Keys (ZSK) for various domains.
 - Zone Signing: Used dnssec-signzone to sign zones, generating RRSIG and NSEC records.
 - Chain of Trust:
   - Built a complete DNSSEC trust chain from Root server down to TLD server.
   - Utilized Delegation Signer (DS) records to delegate trust from a parent zone to a child zone.
 - DNSSEC Validation:
   - Configured a local DNS to perform DNSSEC validation.
   - Verified the Authenticated Data (AD) flag in dig responses.
   - Tested failure modes by intentionally corrupting RRSIG.
- I found out that for Task 4, I did not need to include the bind.keys in the named.conf file. I had the dnssec-validation set to yes instead auto.
- Tech Stack
  - BIND9, dig, dnssec, Docker
