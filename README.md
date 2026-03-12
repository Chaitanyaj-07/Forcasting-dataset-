# 🌲 ForestLang Dataset: Multi-Resident Smart Home with Natural Language Annotations

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.1234567.svg)](https://doi.org/10.5281/zenodo.1234567)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Kaggle](https://img.shields.io/badge/Kaggle-Dataset-blue)](https://kaggle.com/datasets/yourusername/forestlang)

## 📊 Dataset Overview

**ForestLang** is a novel dataset for multi-resident activity recognition in smart environments, combining ambient sensor data with rich natural language descriptions. Perfect for LLM-based HAR research!

### Key Features:
- 🏠 7 days of real-life simulated activities
- 👥 2 residents with distinct behavioral patterns
- 📡 15 ambient sensors across 6 locations
- 📝 56+ natural language activity descriptions
- ⏱️ 50,000+ timestamped sensor events

## 🎯 Use Cases
- Human Activity Recognition (HAR) with LLMs
- Multi-resident behavior analysis
- Time series forecasting
- Natural language generation from sensor data
- Smart home automation research

## 📁 Dataset Files

### 1. `sensor_events.csv`
| Column | Description | Example |
|--------|-------------|---------|
| timestamp | Exact event time | 2026-03-12 06:45:23 |
| session_id | Day identifier (1-7) | 1 |
| resident_id | A or B | A |
| sensor_id | Unique sensor code | MOT_1 |
| sensor_type | Motion/Contact/Temp/Light/Power | Motion |
| location | Room name | Bedroom A |
| value | Sensor reading | 1.0 |

### 2. `natural_language_log.csv`
| Column | Description | Example |
|--------|-------------|---------|
| session_id | Links to sensor data | 1 |
| start_timestamp | Activity start | 2026-03-12 06:45:23 |
| end_timestamp | Activity end | 2026-03-12 07:15:30 |
| primary_resident | A/B/Both | A |
| activity_description | Natural language text | "Resident A wakes up and goes to bathroom" |

## 🚀 Quick Start

```python
import pandas as pd

# Load the dataset
sensors = pd.read_csv('data/sensor_events.csv')
logs = pd.read_csv('data/natural_language_log.csv')

# Merge sensor events with language descriptions
merged_data = pd.merge_asof(
    sensors.sort_values('timestamp'),
    logs.sort_values('start_timestamp'),
    left_on='timestamp',
    right_on='start_timestamp',
    direction='backward'
)

print(f"Total events: {len(sensors)}")
print(f"Total activities: {len(logs)}")
print(f"Unique sensors: {sensors['sensor_id'].nunique()}")ing-dataset-
