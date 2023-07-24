# DNS test dataset

This is a collection of domain names (taken from [URLchecker by Ben Sooter](https://github.com/bensooter/URLchecker)) and query responses generated by a DNS stub resolver connected to the Google DNS server (8.8.8.8:53). The collection includes domain names and query responses for a thousand popular websites and are all error-free, both with regard to internal server errors and errors due to malformed queries.

The queries used in the project have been generated using my own DNS resolver, which can be found in [the following repository](https://github.com/MuhammedReza07/dns_resolver), and were generated to be able to test DNS string decoding since I was unable to find an existing dataset for this purpose.

If the user wishes to manually inspect the files, it is suggested to do so using some Hex Editor to avoid the jibberish that would be displayed by a text editor inspecting binary files. When parsing the query responses, a simple solution would be to treat the text file as a sequence of response packets and reading is be done in 512 byte chunks.