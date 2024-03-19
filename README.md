Program Overview:
This C program provides solutions to various queries related to climate stations in a city. The program takes input data from a CSV file and processes it to answer the queries specified in the problem statement. The queries include identifying stations with the highest heat degree days, determining thermally comfortable days for selected urban stations, listing dates for stations with decreasing vegetation density and temperatures higher than the average city temperature, identifying top stations with minimum population density and highest maximum temperature, and calculating heat island intensity for urban stations.

File Structure:

main.c: Contains the main program logic and query functions implementation.
input.csv: Input data file containing information about climate stations, urban parameters, and weather parameters.

Input File Format (input.csv):

Each line in the input file represents data for one climate station.
The format of each line is as follows:
lua
Copy code
status, sky_vf, veg_dens, popl_dens, perv_sf, imperv_sf, dist1, dist2, ..., distN, temp1, humid1, temp2, humid2, ..., temp30, humid30
Where:
status: Station status (0 for urban, 1 for rural).
sky_vf: Sky view factor (float, range: 0.1 to 0.9).
veg_dens: Vegetation density ratio (float, percentage).
popl_dens: Population density (integer, number of people per square km).
perv_sf: Pervious surface fraction (float, range: 0 to 15).
imperv_sf: Impervious surface fraction (float, range: 0 to 15).
dist1, dist2, ..., distN: Distances of the station to other stations (float, in km).
temp1, humid1, temp2, humid2, ..., temp30, humid30: Temperature and relative humidity readings for 30 days.

Queries Supported:

1.List of stations with highest no. of heat degree days

2.Identifies stations with the highest number of days where temperature is higher than the average city temperature.
Thermally comfortable days of selected station

Determines the days for a selected urban station where the temperature difference between the station and its nearest rural station is minimum.
Dates for all station with decreasing vegetation density and for which temperature was more than average city temperature

3.Lists dates for all stations where the vegetation density ratio is decreasing and the temperature is higher than the average city temperature.
Top k stations with minimum population density

4.Lists the top 'k' stations with the minimum population density, ordered by the highest maximum temperature. If two stations have the same population density, they are ordered by the highest maximum temperature.
Heat Island Intensity for all urban stations

5.Calculates the heat island intensity for all urban stations, which is the difference between the average temperature of the urban station and its nearest rural station.

 Structure Definitions:
Two structures are defined:
urb_param: Represents urban parameters of a climate station, including sky view factor, vegetation density ratio, population density, pervious surface fraction, impervious surface fraction, station status (urban or rural), and distance to other stations.
weath_param: Represents weather parameters of a station for a single day, including air temperature and relative humidity.

 Function Definitions:
float maxtemp (station s): Finds the maximum temperature recorded for a given station.
float avg_temp( station s): Calculates the average temperature recorded for a given station.
int nearest_rural( station urb, station s[], int n): Finds the index of the nearest rural station for a given urban station among an array of stations.
void Query1( station s[],int n, float avg_city_temp): Lists stations with the highest number of heat degree days.
void Query2( station urb, station s[], int n): Finds thermally comfortable days for a selected urban station.
void Query3 ( station s[],int n, float avg_city_temp): Lists dates for all stations with decreasing vegetation density ratio and temperatures higher than the average city temperature.
void Query4 (station s[], int n , int k): Lists the top 'k' stations with minimum population density and highest maximum temperature.
void Query5( station s[], int n): Calculates and prints the heat island intensity for all urban stations.

Query 1: List of stations with highest number of heat degree days
Algorithm:

Iterate through each station.
For each station, count the number of days where the temperature is higher than the average city temperature.
Maintain a variable to keep track of the maximum count of heat degree days.
Output the stations with the highest count of heat degree days.
Optimization:

Instead of recalculating the number of heat degree days for each station, we can compute it while reading the input data from the file. This optimization reduces the need for repeated iteration through the weather data.
Time Complexity:

Let's denote the number of stations as n and the number of days as m (30 in this case).
The time complexity of this algorithm is O(n * m), as we need to iterate through all stations and check each day's temperature.
Query 2: Thermally comfortable days of selected station
Algorithm:

Find the nearest rural station for the selected urban station.
Calculate the temperature difference between the urban station and its nearest rural station for each day.
Find the minimum temperature difference.
Output the days where the temperature difference is equal to the minimum temperature difference.
Optimization:

The algorithm finds the nearest rural station twice. It can be optimized by finding it once and storing the result to avoid redundancy.
Time Complexity:

Finding the nearest rural station takes O(n) time, where n is the number of stations.
Calculating the temperature difference for each day takes O(m) time.
Thus, the overall time complexity is O(n + m).
Query 3: Dates for all stations with decreasing vegetation density and temperature higher than average city temperature
Algorithm:

Sort the stations based on decreasing vegetation density.
For each station, check if the temperature is higher than the average city temperature.
Output the station number and dates where the condition is met.
Optimization:

Sort the stations based on decreasing vegetation density only once before processing.
Use a flag to avoid redundant checks for temperature conditions if vegetation density is not decreasing.
Time Complexity:

Sorting the stations takes O(n log n) time.
Checking temperature conditions for each station takes O(n * m) time.
Thus, the overall time complexity is O(n log n + n * m).
Query 4: Top k stations with minimum population density and highest maximum temperature
Algorithm:

Sort the stations based on population density in ascending order.
If two stations have the same population density, sort them based on highest maximum temperature.
Output the top k stations after sorting.
Optimization:

Sort the stations based on both population density and maximum temperature in a single pass of sorting.
Use a custom comparison function to handle the sorting criteria.
Time Complexity:

Sorting the stations based on two criteria takes O(n log n) time.
Outputting the top k stations takes O(k) time.
Thus, the overall time complexity is O(n log n).
Query 5: Heat Island Intensity for all urban stations
Algorithm:

For each urban station, find its nearest rural station.
Calculate the average temperature difference between each urban station and its nearest rural station.
Output the heat island intensity for each urban station.
Optimization:

Compute the heat island intensity while finding the nearest rural station and store the results.
Time Complexity:

Finding the nearest rural station for each urban station takes O(n) time.
Calculating the heat island intensity for each urban station takes O(n * m) time.
Thus, the overall time complexity is O(n + n * m).

Overall Analysis:
The complexity of the algorithms depends on the number of stations (n) and the number of days (m).
Optimizations can be applied to reduce redundancy and improve efficiency in some queries.
Overall, the time complexity ranges from O(n) to O(n log n) depending on the specific query and optimization applied.

