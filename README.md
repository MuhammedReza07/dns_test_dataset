# DNS test dataset

This is a collection of domain names (taken from [URLchecker by Ben Sooter](https://github.com/bensooter/URLchecker)) and query responses generated by a DNS stub resolver connected to the Google DNS server (8.8.8.8:53). The collection includes domain names and query responses for a thousand popular websites and are all error-free, both with regard to internal server errors and errors due to malformed queries.

The queries used in the project have been generated using my own DNS resolver, which can be found in [the following repository](https://github.com/MuhammedReza07/dns_resolver), and were generated to be able to test DNS string decoding since I was unable to find an existing dataset for this purpose.

If the user wishes to manually inspect the files, it is suggested to do so using some Hex Editor to avoid the jibberish that would be displayed by a text editor inspecting binary files. When parsing the query responses, a simple solution would be to treat the text file as a sequence of response packets and reading is be done in 512 byte chunks.

## About the data
The query responses included in the dataset have the following form:

    Header:
        ID: 0,                      Packet Identifier
        QR: 1,                      Query Response (Response)
        OPCODE: 0,                  Operation Code (QUERY)
        AA: 0,                      Authoritative Answer (No)
        TC: 0,                      Truncated Message (No)
        RD: 1,                      Recursion Desired (Yes)
        RA: 1,                      Recursion Available (Yes)
        Z: 0,                       Z (no DNSSEC)
        RCODE: 0,                   Response Code (Success)
        QDCOUNT: 1,                 Question Count (Constant, 1)
        ANCOUNT: uint16,            Answer Count (Variable)
        NSCOUNT: 0,                 Authority Count (None, 0)
        ARCOUNT: 0,                 Additional Count (None, 0)
    Question Section:
        Question:
            QNAME: <domain name>,   Domain name from domain_list.txt
            QTYPE: 1,               Type A resource record, an IPv4 address
            QCLASS: 1,              Class IN query, for Internet
    Answer Section:
        Resource Record:
            NAME: <domain name>,    Domain name from domain_list.txt
            TYPE: 1,                Type A resource record, an IPv4 address
            CLASS: 1,               Class IN query, for Internet
            TTL: uint32,            Time to live in seconds for cached RR 
            RDLENGTH: 4,            Length of the RR data in bytes
            RDATA: <IPv4 address>,  The RR data
        ... (ANCOUNT RR:s)
    Authority Section: Empty,
    Additional Section: Empty
