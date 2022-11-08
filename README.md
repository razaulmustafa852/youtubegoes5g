# YouTube goes 5G: Benchmarking YouTube in 4G vs 5G Through Open Datasets 

- As 5G technology evolves, its performance is expected to improve over time. Therefore, the QoE of the YouTube video streaming from Mobile Network Operators (MNOs) perspective is ideal and challenging compared to 4G/LTE networks. 
- Evaluating mobile carriers’ end-to-end network performance in the wild is known to be difficult and complicated. 
Critical issues for MNO include how to manage increased video traffic demands and provide a satisfactory Quality of Experience (QoE) experience to their end-users. 
- To ensure better QoE, understanding and monitoring the Key Performance Indicators (KPIs) that impact users' perceived QoE has become a trending topic.
- Therefore, we carry out a massive 4G and 5G dataset collection campaign using a commercial 4G and 5G network, where we consider YouTube as baseline for video streaming to collect Channel Metrics and YouTube QoE logs with 1-second granularity.

# Methodology
- IFRAME data API to extract player information i.e., Stalls and Quality Shifts.
The IFrame player API lets you embed a YouTube video player on web-based applications and control the player using JavaScript.
We designed a custom web-based application and embedded the YouTube IFrame. Then, using Javascript, we define functions to save player events in MySQL database after every 1-second interval.
  - https://developers.google.com/youtube/iframe_api_reference
- An Android application to collect channel level metrics e.g., CQI, RSRQ, RSRP, SNR, application download bitrate. It is a network monitor and drive test tool application for 5G/4G/3G/2G networks.  It allows monitoring and logging of mobile network parameters without using specialized equipment. It provides 2G/3G/4G/5G serving and neighbors cells information measurement and save it in logfiles (text and kml format).
  - We used Gnetrack Pro - https://play.google.com/store/apps/details?id=com.gyokovsolutions.gnettrackproplus&hl=en&gl=US&pli=1


