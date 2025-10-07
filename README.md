# DDoS Attack Clustering for Botnet Detection
## Overview
This project clusters malicious IPs involved in DDoS attacks to identify potential botnet infrastructure, using data from Malicious_ips.csv and attack_data.csv. The script merges these datasets, filters by date, and groups IPs into clusters based on customer and temporal proximity (within 300 seconds). It computes metrics like attack duration, bandwidth (gbps), and packet rates (pps), saving results to JSON files for further analysis. This supports cybersecurity efforts to detect patterns, trends, and anomalies in malicious network behavior.
Features

Data Merging: Combines Malicious_ips.csv and attack_data.csv on the mitigation column.
Temporal Filtering: Filters data for a specific date (e.g., September 29, 2025).
Clustering: Groups IPs into clusters based on customer and time proximity.
Metrics Calculation: Computes attack metrics (e.g., duration_avg, gbps_max, pps_avg) and metadata (e.g., industries, regions).
Output: Saves results to cluster_analysis.json, cluster_malicious_ips.json, and cluster_ip_history.json.

Prerequisites

Python Version: Python 3.11 or higher.
Dependencies: Install required packages from requirements.txt.

Installation

Clone the repository:git clone https://github.com/your-username/ddos-botnet-clustering.git
cd ddos-botnet-clustering


Create a virtual environment (optional but recommended):python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate


Install dependencies:pip install -r requirements.txt



Dependencies
The requirements.txt file includes:
pandas==2.2.3
numpy==1.26.4

These packages are required for DataFrame operations and numerical computations. Standard library modules (json, os, datetime, logging) are used but not listed in requirements.txt.
Usage

Prepare Input Files:

Place Malicious_ips.csv and attack_data.csv in the project directory.
Expected columns in Malicious_ips.csv: date_time, d_name, Malicious_IP, mitigation, customers_x.
Expected columns in attack_data.csv: mitigation, customers_y, duration, bps_average, bps_pct95, bps_max, pps_average, pps_pct95, pps_max, vectors, industry, country, region.


Run the Script:
python ddos_clustering.py

The script:

Loads and merges the CSV files.
Filters data for September 29, 2025 (modify start_time and end_time in the script for other dates).
Clusters IPs based on customer and time proximity (300 seconds).
Saves results to:
cluster_analysis.json: Cluster metadata (e.g., ClusterID, Industries, Regions, metrics).
cluster_malicious_ips.json: IP-to-cluster mappings.
cluster_ip_history.json: IP movement history.




Output Files:

cluster_analysis.json: Contains cluster details (e.g., ClusterID, Cluster_Size, duration_avg).
cluster_malicious_ips.json: Lists IPs with their cluster assignments and observation dates.
cluster_ip_history.json: Tracks IP movements across clusters over time.



Example Output

Log Output:2025-10-07 14:02:00,123 - INFO - Loaded 10000 records from Malicious_ips.csv
2025-10-07 14:02:00,456 - INFO - Loaded 5000 records from attack_data.csv
2025-10-07 14:02:01,789 - INFO - Saved 1039 clusters to cluster_analysis.json
2025-10-07 14:02:01,890 - INFO - Saved 61927 IPs to cluster_malicious_ips.json
2025-10-07 14:02:01,923 - INFO - Saved 35437 IP history entries to cluster_ip_history.json
This project is licensed under the MIT License. See the LICENSE file for details.
Contact
For issues or questions, open an issue on GitHub or contact the maintainer at [your-email@example.com].
