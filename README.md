
# Patient No-Show Prediction System

A Python-based system that analyzes patient appointment data and identifies patterns contributing to no-shows. The program evaluates factors such as appointment time slots, day of the week, weather, and patient history of previous no-shows.



## Description 

This program processes appointment records from a CSV file and generates a detailed statistical report that highlights no-show trends. It helps clinics understand which factors most strongly correlate with patient absences—such as time of day, day of the week, weather conditions, or patient history—allowing for more informed scheduling and intervention strategies.





## Installation


1. Ensure Python 3.8 or higher is installed 

2. Clone or download this project folder
 git clone <>

 3. Place your appointment data file (CSV) in the project folder

 4. Run the program

 python main.py 


    
## Usage/Examples
Run the analysis on a CSV data file:

```python

def count_noshows_by_day(appt_data, days=["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"]): 
    no_show_counts = {day: 0 for day in days}
    
    for appt in appt_data:
        day = appt["day_of_week"]
        if str(appt["showed_up"]).strip().lower() == "false":
            if day in no_show_counts:
                no_show_counts[day] += 1
    return no_show_counts
```

### Output a report showing:
- Total number of appointments scheduled
- Total number of no-no_shows
- Total number of shows 
- Percentage of no-show appointments per day of the day of the week 
- Percentage of no-show appoitnments per time slot
- No-Show rate (%) for patients with 2+ noshows 
- No-show rate (%) on rainy vs sunny days 
## Authors

- [salamona@csp.edu](https://www.github.com/alex-filus)


## Features

- Import database file for analysis (csv format)
- Generate report for:
    - Overall statistics: total number of appointments, Total number of No-shows, Total number of shows
    - Analyzes and prints no-show patters by day and time
    - Generates high-risk factors: highest percentage of no-shows per time slot, day of the weeek, patients with previous no-shows, different weather types



## Technical Details

The system is organized into three main Python modules:

project/
│── main.py 
│── appt_stats.py 
│── data_processing.py 
│── ApptData.csv 

### Data Flow

1. CSV Import
import_appt() loads appointment data into a list of dictionaries.

2. Processing & Analysis (appt_stats.py)

- Count shows and no-shows

- Calculate daily and time-slot percentages

- Determine high-risk days and time slots

- Compare weather-based no-show rates

- Evaluate patients with ≥ 2 previous no-shows

- Report Generation (main.py)

- Calls analysis functions

- Formats and prints a multi-section no-show report

### Data Flow Summarized:
1. Load CSV
2. Print report header
3. Compute and print overall appointment statistics
4. Print daily no-show rates 
5. Print time-based no-show rates 
6. Print high-risk patterns (day, time, weather, patient history)
7. End of report

### Functions:
- count_noshow_by_time()
- total_appt_by_time()
- noshow_percentage_by_time()
- highest_noshow_time_slot()
- highest_noshow_day()
- noshow_rate_by_previous(min_prev_noshows=2)
- noshow_rate_by_weather(weather_types=["Sunny", "Rain"])


## Future Enhancements

1. Machine learning model for prediction
Predict likelihood of individual patient no-shows
2. SQL Database Integration
Replace CSV input with live database queries
3. Automated HTML Report Generation 
Produce formatted reports for clinics
4. No-Show analysis based on demographics
Age group, insurance type, chronic conditions, distance to clinic