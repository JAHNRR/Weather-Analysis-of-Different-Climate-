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
