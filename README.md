# YouTube goes 5G: Benchmarking YouTube in 4G vs 5G Through Open Datasets 

- As 5G technology evolves, its performance is expected to improve over time. Therefore, the QoE of the YouTube video streaming from Mobile Network Operators (MNOs) perspective is ideal and challenging compared to 4G/LTE networks. 
- Evaluating mobile carriers’ end-to-end network performance in the wild is known to be difficult and complicated. 
Critical issues for MNO include how to manage increased video traffic demands and provide a satisfactory Quality of Experience (QoE) experience to their end-users. 
- To ensure better QoE, understanding and monitoring the Key Performance Indicators (KPIs) that impact users' perceived QoE has become a trending topic.
- Therefore, we carry out a massive 4G and 5G dataset collection campaign using a commercial 4G and 5G network, where we consider YouTube as baseline for video streaming to collect Channel Metrics and YouTube QoE logs with 1-second granularity.

# Methodology
We collected 4G and 5G dataset using various use cases:
- Mobility - High
- Pedestrian
- Indoor - Static
- Outdoor - Croweded, Terminals - Railway and Bus.

> For each experiment, we select a video out of 10 4K-videos and played in a browser where we embedded YouTube IFRAME API and the same time, we are running Android Network Monitor Application in the background. We set 1-second granularity to collect both YouTube QoE Logs, i.e., Current Quality, Video Bytes Downloaded, etc. and Channel Logs, i.e., RSRQ, RSRP, CQI, Download Bitrate etc. 

## YouTube IFRAME API
- IFRAME data API to extract player information i.e., Stalls and Quality Shifts.
The IFrame player API lets you embed a YouTube video player on web-based applications and control the player using JavaScript.
We designed a custom web-based application and embedded the YouTube IFrame. Then, using Javascript, we define functions to save player events in MySQL database after every 1-second interval.
  - https://developers.google.com/youtube/iframe_api_reference
## Android Application - Network Monitor
- An Android application to collect channel level metrics e.g., CQI, RSRQ, RSRP, SNR, application download bitrate. It is a network monitor and drive test tool application for 5G/4G/3G/2G networks.  It allows monitoring and logging of mobile network parameters without using specialized equipment. It provides 2G/3G/4G/5G serving and neighbors cells information measurement and save it in logfiles (text and kml format).
  - We used Gnetrack Pro - https://play.google.com/store/apps/details?id=com.gyokovsolutions.gnettrackproplus&hl=en&gl=US&pli=1

# Dataset Description

## Channel Level Metrics (CLM) Logs
  - Each experiment generate 1-Channel log, whereas its corresponding YouTube QoE logs are saved in MySQL. 
  - For CLM, each file has name and the end of each file logs we inserted file name as "EID" as Experiment ID. This is unique EID given to each experiments, thus can be used to extract QoE of YouTube from other Tables.
  - In CLM we provide, Timestamp,	Longitude,	Latitude,	CellID,	NetworkTech,	NetworkMode,	Level,	Qual,	SNR,	CQI,	LTERSSI,	DL_bitrate,	UL_bitrate,	Altitude,	Height,	State,	EVENT,	SecondCell_RSRP,	SecondCell_RSRQ,	SecondCell_SNR and EID at end - Which is same as file name.
    - Detail of each features is available at - https://gyokovsolutions.com/manual-g-nettrack/
## YouTube QoE Logs
- YouTube QoE logs are of two types
  - Events
  - QoE
- Events:
  - For Events, we saved 6 events as: -1 – unstarted, 0 – ended, 1 – playing, 2 – paused, 3 – buffering, 5 – video cued
- QoE:
  - For QoE, we save player current state after every 1-second such as: Current Quality, Video Bytes Downloaded, Loaded Percentage, and Time

> For both Events and QoE, we have "EID", which is exactly the same as of CLM log file name, therefore, you can extract QoE of YouTube and CLM by using EID - Experiment ID. For example: "5A12.csv" is CLM log file, and its corresponding QoE and Events of YouTube are available in csv files by using EID as "5A12.csv"

# Use Cases Description
- Files starting with 4 are - 4G experiments, 4G cell phone, 4G technology
- File starting with 5 are - 5G experiments, 5G cell phone, 5G technology
 - 5Po30 - Experiment is done with 5G cell with 5G technology and the use case is - Pedestrian. The capital Letter (M, P, A, I, O) most of time second letter represents use case as M- Mobility, P - Pedestrian, A - Terminals, I - Indoor, O - Outdoor. For example:
 - 5Or29 - 5G technology, use case - Outdoor, O represents Outdoor.
 - 5Ae30 - 5G technology, use case - Outdoor - Bus and Railway Terminals
 - 4M30 - 4G technology, use case - Mobility
 - 4I7s - 4G technology, use case - Indoor

