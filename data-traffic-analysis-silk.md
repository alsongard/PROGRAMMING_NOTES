# Data Communication Traffic Analysis

# Description
This file will be used to demonstrate and explain how to use silk(system for internet level knowledge) tool which can be used to analyse Communication traffic and provide useful insight in data analysis.

# Introduction
Network Traffic can be divided into 2:
Netflow format - Netflow provides a summary of the data traffic and is useful for fast  data analysis.
Packet Capture - Also known as full packet capture, it provides comprehensive view of the network traffic and mostly preffered for deep packet inspection.

# Features
SiLK (System for Internet Level Knowledge) Tool
the SiLK tool provides 2 options:
Packaging suite which can be used to collect multiple network flow types (e.g Netflow v9 / v5 and stores)  them into binary files
Analysis suite which can be used for data analysis by providing tools that can be used for statistics,count,filtering,sorting and listing. It also support use of linux CLI pipes .e.t.c 

********

# Usage
* ``silk_config -v``
> It is used to provide details about the version of silk software you are using and installation details

### rwfileinfo 
* ``rwfileinfo file_name``
> the command above is used to provide details about file. It provides information about the count-records,silk-versin record-length,byte-order e.t.c this can be both used in packing and analsyis suite.

********
### rwcut

* ``rwcut filename options``
> the rwcut command is used to diplay the whole binary file into text format by default if no options are given.It can also be used to filter specific fields of the file by using the ``--field`` parameter. Examples will be provided below each with an explanation

* ``rwcut file_name --num-recs=5 | --tail-recs=5`` 
the command above will output the first and last five lines of the file.
* ``rwcut file_name --field=protocol,sIP,sPort,dIP,dPort``
In the above command the rwcut fill filter out the data and display the protocol,sending IP address, destination IP address, ports. Remember the fields to be filtered depend on the data given. Use the rwcut command with no options to view the fields and characteristics of the data.
* ``rwcut file_name | wc -l ``
The rwcut can also be combined with Linux Cmd Line Pipes. The result will display the number of lines of that file

*******

### rwfilter 

* ``rwfilter filename -options --pass=stdout | rwcut ``
The rwfilter option provides better options for filtering data in columns. However it does not display the output on the terminal, it requires to be post processed.
Examples of the options provided by the rwfilter command:
the --pass=stdout is used for processing the output to the next command
>> Port : --any-port, --dport,--sport
>> IP address : --saddress,--daddress, --any-address ip\_address_number
>> Protocol : --proto , --protocol value
>> Port number : --aport(anyport)  value , --sport(sendingPort) value, -dport(destination port) value
>> Volume filters : --packets number_of_packets | --bytes number_of_bytes

********

#### rwstats 
the rwstats command is used to provide statistical data based on the traffic data
the syntax of the command is 
``rwstats file_name --field=column_values --values=bytes,packets,records, --count=number_value``
Explanation of the above syntax:
1rst argument : is used to take the file_name
2nd argument : ``--field=`` is used to filter out specific column data as in the example below it is used to filter out traffic on the destination port(dPort)
3rd argument : ``values=`` the values is used to provide how the statistical data will be represented either in bytes,records or packets
4th argument : ``--count=`` the count which is constantly required is used to limit how the output to the terminal
An example is provided below:
``rwstats File_name --fields=dPort --values=records,packtes,bytes,sIP-Distinct,dIP-Distinct --count-10``


