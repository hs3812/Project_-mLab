**This folder contains  code and  result for TLS fingerprint project 2.**

Features used in TLS database: Cipher_suites, Version, Compression_method, Extension_types

Feature used in device  database: Device_id, Device_name, Device_vendor, Device_type, Dhcp_hostname


The flow of the program is as the following:

1. First process the data, clean NaNs. Convert features to string. 
2. Create TLS fingerprint for each row. Fingerprint = md5  hash(features  concatenated, seperated by ',')
3. Extract all the rows with the same TLS fingerprint(indicating same cipher configuration) 
4. Extract device  information from the device database
5. Aggregate extracted data into a new dataframe, write that dataframe into a result CSV




**Findings:**

The result CSV is created with fingerprints composed of four features.(Exact match) 
With four features combined to create fingerprint hash, the result is accurate in terms of identifying devices having the same TLS configuration

As you can see, under the 1st column, it shows mostly Apple device, which share the same TLS configuration. 

I have also done less strict match, 4 choose 2. So fingerprint = md5 hash(choose 2 out out (Cipher_suites, Version, Compression_method, Extension_types))

This less strict match  sometimes is  inaccurate. For instance, when fingerprint is created with compression method and version, there is a lot of different devices being put in the same group. (like Samsung TV and PS4)

