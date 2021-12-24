## Activity File: Exploring Kibana

* You are a DevOps professional and have set up monitoring for one of your web servers. You are collecting all sorts of web log data and it is your job to review the data regularly to make sure everything is running smoothly. 

* Today, you notice something strange in the logs and you want to take a closer look.

* Your task: Explore the web server logs to see if there's anything unusual. Specifically, you will:

:warning: **Heads Up**: These sample logs are specific to the time you view them. As such, your answers will be different from the answers provided in the solution file. 

---

### Instructions

1. Add the sample web log data to Kibana.

2. Answer the following questions:

    - In the last 7 days, how many unique visitors were located in India?
    
        246

    - In the last 24 hours, of the visitors from China, how many were using Mac OSX? 
    
      15

    - In the last 2 days, what percentage of visitors received 404 errors? How about 503 errors?
    
       404 errors:- 3.03%  503 errors:-89.394%
    - In the last 7 days, what country produced the majority of the traffic on the website?

      China

    - Of the traffic that's coming from that country, what time of day had the highest amount of activity?
     Time :- 18:45 Count = 2969
    - List all the types of downloaded files that have been identified for the last 7 days, along with a short description of each file type (use Google if you aren't sure about a particular file type).
   
       CSS (Cascading Style Sheets) are files that describe how HTML elements are displayed on the screen, paper, etc. 

      A DEB file is a standard Unix archive that contains two bzipped or gzipped archives, one for the installer control information and another for the actual installable data. DEB files are often used for software installation packages by multiple versions of Linux including Ubuntu

      A GZ file is an archive file compressed by the standard GNU zip (gzip) compression algorithm. 

      A file with the RPM file extension is a Red Hat Package Manager file that's used to store installation packages on Linux operating systems.

      ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed

3. Now that you have a feel for the data, Let's dive a bit deeper. Look at the chart that shows Unique Visitors Vs. Average Bytes.
     - Locate the time frame in the last 7 days with the most amount of bytes (activity).
     - In your own words, is there anything that seems potentially strange about this activity?

4. Filter the data by this event.
     - What is the timestamp for this event?
     
       2021-12-12 21:00
     - What kind of file was downloaded?

       rpm and zip
     - From what country did this activity originate?
     
       India
     - What HTTP response codes were encountered by this visitor?
     
       HTTP 200 Ok

5. Switch to the Kibana Discover page to see more details about this activity.
     - What is the source IP address of this activity?

       86.158.95.250
     - What are the geo coordinates of this activity?
      
       "lat": 33.12936111,
       "lon": -94.97563889

     - What OS was the source machine running?
       
       Win xp
     - What is the full URL that was accessed?

       https://www.elastic.co/downloads/beats
      
     - From what website did the visitor's traffic originate?

       www.elastic.co

6. Finish your investigation with a short overview of your insights. 

     - What do you think the user was doing?

       The user is visiting the website of the company "Elastic" who is behind Elastic Stack — that's Elasticsearch, Kibana, Beats, and Logstash , to download Beats
     - Was the file they downloaded malicious? If not, what is the file used for?
       
       No the file downloaded was not malicious . Beats are a collection of lightweight (resource efficient, no dependencies, small) and open source log shippers that act as agents installed on the different servers in your infrastructure for collecting logs or metrics.
       These can be log files (Filebeat), network data (Packetbeat), server metrics (Metricbeat),
     - Is there anything that seems suspicious about this activity?
       
       No
     - Is any of the traffic you inspected potentially outside of compliance guidlines?
       
       No

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  