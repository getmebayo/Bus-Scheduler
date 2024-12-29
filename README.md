 Project Documentation: Bus Schedule Creator

Overview

The Bus Schedule Creator is a Python application designed to assist users in generating a bus schedule based on user-defined parameters such as origin, destination, travel time, terminal time, headway, and specific departure times. The application calculates the required number of vehicles and generates a detailed schedule that can be visualized in a tabular format using Matplotlib.

Purpose

The primary purpose of this project is to provide a tool for transportation planners and bus operators to efficiently manage bus schedules. By inputting key parameters, users can determine how many buses are needed for a given route and visualize the schedule in an easy-to-read format.

Features

•	User Input: The application prompts users for essential information, including:
  - Origin and destination of the bus route.
  - Travel time between stops.
  - Terminal time spent at the destination.
  - Headway (time interval between successive buses).
  - Departure date and start time.
  - End time for the schedule.

•	Dynamic Calculations: 
  - The application calculates the total cycle time based on travel and terminal times.
  - It determines the number of vehicles required based on headway.
  - It adjusts terminal times dynamically if additional vehicles are needed.

•	Visualization: 
The generated bus schedule is displayed in a table format using Matplotlib, making it easy to read and understand.

Code Logic

Structure

The code is structured into functions for better organization and reusability:

1. Input Functions:
   - `get_time_input(prompt)`: Prompts the user for time input in HH:MM format and validates it.
   - `get_date_input(prompt)`: Prompts the user for date input in YYYY-MM-DD format and validates it.

2. Main Functionality:
     - The `main()` function orchestrates the overall flow of the application:
     - It collects user input.
     - It calculates necessary values (total cycle time, number of vehicles).
     - It generates the bus schedule.
     - It displays the results using Matplotlib.

Key Calculations

1. Total Cycle Time Calculation:
   ```python
   total_cycle_time = 2 * (travel_time + terminal_time)
   ```
   This formula accounts for both directions of travel (to and from) along with any terminal time spent at the destination.

2. Number of Vehicles Calculation:
   ```python
   num_vehicles = total_cycle_time / headway
   ```
   This determines how many buses are needed based on the total cycle time divided by the headway. If this value is not an integer, it rounds up to ensure sufficient coverage.

3. Adjusted Cycle Time:
   If additional vehicles are required (i.e., when `num_vehicles` is not an integer), the code calculates an adjusted cycle time that considers any extra time needed due to rounding up:
   ```python
   adjusted_cycle_time = num_vehicles * headway
   ```

Visualization

The results are displayed in a table format using Matplotlib:
```python
table = ax.table(cellText=table_data, cellLoc='center', loc='center')
```
This creates a visually appealing representation of the bus schedule that includes departure and arrival times.

Usage Instructions

1. Run the Application: Execute the script in a Python environment that has Matplotlib installed.
2. Input Parameters: Follow the prompts to enter all required parameters.
3. View Results: A table displaying the bus schedule will appear after inputting all data.

Conclusion

The Bus Schedule Creator is a practical tool for anyone involved in transportation planning or management. By allowing users to easily input parameters and generate schedules, it streamlines operations and helps ensure efficient service delivery.


