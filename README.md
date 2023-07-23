# DNS test dataset

This is a collection of domain names (taken from [URLchecker by Ben Sooter](https://github.com/bensooter/URLchecker)) and query responses generated by a DNS stub resolver connected to the Google DNS server (8.8.8.8:53). The collection includes domain names and query responses for a thousand popular websites and are all error-free, both with regard to internal server errors and errors due to malformed queries.

The queries used in the project have been generated using my own DNS resolver, which can be found in [the following repository](https://github.com/MuhammedReza07/dns_resolver), and were generated to be able to test DNS string decoding since I was unable to find an existing dataset for this purpose.

Note that the list of domain names (domain_list.txt) is licensed under the MIT license and thus includes a copy of the
original license which should be taken into account when parsing the file.
