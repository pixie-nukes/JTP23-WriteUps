# O Data, All Ye Faithful 
## Description
### Data Science in Cybersecurity

The use of data science is quickly becoming more frequent in Cybersecurity because of its ability to offer insights. Analysing data, such as log events, leads to an intelligent understanding of ongoing events within an organisation. Using data science for anomaly detection is an example. Other uses of data science in Cybersecurity include:


    SIEM: SIEMs collect and correlate large amounts of data to give a wider understanding of the organisation’s landscape.
    Threat trend analysis: Emerging threats can be tracked and understood.
    Predictive analysis: By analysing historical events, you can create a potential picture of what the threat landscape may look like in the future. This can aid in the prevention of incidents.
![image](https://github.com/pixie-nukes/JTP23-WriteUps/assets/94845416/fe1a007d-a687-4ed8-9a21-46e89f63b860)

## Introducing Jupyter Notebooks

Jupyter Notebooks are open-source documents containing code, text, and terminal functionality. They are popular in the data science and education communities because they can be easily shared and executed across systems. Additionally, Jupyter Notebooks are a great way to demonstrate and explain proof of concepts in Cybersecurity.

## Tasks:
### 1. Open the notebook “Workbook” located in the directory “4_Capstone” on the VM. Use what you have learned today to analyse the packet capture.
no answer needed
### 2. How many packets were captured (looking at the PacketNumber)?
I Used the dataframe.count() Function to Count the count of Columns(Packet Number). In my case data frame name is df, so use df.count()
ans: `100`
### 3. What IP address sent the most amount of traffic during the packet capture?
Use the dataframe.groupteby([‘ColumnName’]).size() Function to find the IP that sent the most traffic. In our case data frame name is df, so use
df.groupby([‘Source’]).size()
ans : `10.10.1.4`
### 4. What was the most frequent protocol?
Use the dataframe[‘ColumnHere’].value_counts() Function to find the most frequent protocol. In our case data frame name is df, so use
df[‘Protocol’].value_counts()
ans: `ICMP`
