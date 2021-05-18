## 1. IoT Health Monitoring and Analytics
When the connected infrastructure is deployed at scale (100s of 1000s of devices), it is important to monitor the health of the end to end pipeline so that proactive actions can be taken to address any problems in the systems deployed in the field. This will include:

Collecting appropriate health parameters from each end node - Zenatix already collects such parameters from all its systems.
Separating out the health information (e.g. RSSI) from application information (e.g. temperature data) at the edge side - Currently all the health and application information is combined and sent to the same pipeline on the cloud.
Collecting additional health information from the edge gateway - Zenatix already collects multiple such parameters.
Creating a separate pipeline for health information which addresses typical requirements such as timeseries storage, log storage, developing meaningful dashboards on that data, purging rules to delete data after a certain time etc. - Zenatix currently has this mixed up with application pipeline in cloud and we would like to separate out the whole health monitoring and analytics.
Beyond monitoring the health information of the IoT hardware deployed in the field, it will be desirable to extend the same system for monitoring the software applications running both on the edge and the cloud.
Create suitable dashboards for the account management team at Zenatix which can help them to get a quick high level overview of performance of the systems deployed for a customer so as to have improved customer engagement - this will require developing systems in a way that custom queries and custom UI elements can be easily added in the future.
There are several open source tools available - such as ELK stack or TICK stack or Prometheus based logging. The project will involve understanding Zenatix stack, performing some PoCs with these open source monitoring and logging tools and then suitably modifying one such tool to address the requirements laid out for health monitoring and analytics at Zenatix.

## 2. Remote firmware update using Eclipse Hawkbit
Zenatix currently uses an open source project - Eclipse Hawkbit, for rolling out software updates to the gateways deployed in the field. The cloud side is taken from the open source project and has been suitably modified to expose some APIs for our internal applications to interact with it. The edge side is custom developed to address our specific requirements. While the project has been running reliably over the years, we have created a list of upgrades that will be good to have in such a system used for rolling out software updates to IoT hardware deployed in the field. Some of these requirements are listed below:

#### Client side:
Re-factor the code to improve logging
Develop suitable APIs so that cloud can easily fetch the current status of any of the pending rollouts
#### Cloud side:
Simplified process for creating deployment packages
Filter sites based on different criteria (e.g. geography, size of store, enabled/disabled sites etc.) captured in the meta data, to then deploy the packages
Administration of pending packages for each site where the deployment packages are released
Increase efficiency of the communication messages exchanged with the edge for each deployment
Better visualisation of status of each deployment
Extracting relevant information from messages exchanged with the client to compile the status of each controller
Automation of development/local setup for testing

## 3. Implementation of LoRa stack on the open source Zenatix Gateway
Zenatix has developed a gateway based on open source Raspberry Pi compute module. The gateway supports modular slots such as mPCIE using which an off-the-shelf wireless modules can be connected to enhance the supported functionality. The gateway currently supports 4G card connected on the mPCIE slot. This project involves supporting the LoRa stack on the edge (using an off-the-shelf mPCIE LoRa card connected to off the shelf sensors such as temperature/humidity sensors). The project will involve exploring open source LoRa gateway and network server implementation (such as the one provided by Chirpstack) and integrating the same with the Zenatix middleware running on the edge.
