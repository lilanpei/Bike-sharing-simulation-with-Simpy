# Bike-sharing-simulation-with-Simpy

## Station :

* Init with init_rato × capacity(the number of docks in the station). 
* The monitor process : If #bikes/capacity is not in the range[reset_ratio, 1-reset_ratio], repositioning vehicle will be called to refill/remove bikes, resetting the station to a state that one half is empty, and one half is filled with bikes.

## Depot Station :
* Init with capacity(num_vehicles). A vehicle is a container with capacity 10, meaning one vehicle can only serve at most 10 stations during one trip.
* The monitor process : when a vehicle receives calls from some number of stations,  then it start departing to serve them. Note the number could be different in peak commuting hours.

## Passenger :
* Passengers are generated with different arrival rates in five periods(early-hours, morning, noon, evening, midnight), amounting to around 3720 per day. The time interval between two consecutive passenger follows the exponential distribution.
* Passengers have a limited patience to get/put a bike
   >> * (10, 20) minutes to get a bike, otherwise they would leave.
   >> * (20, 30) minutes to put a bike, otherwise they may not park the bike in the dock properly.

## Main :
* Run the system.

## Grid search parameters :
1. The number of stations : **num_stations** fixed to 20.
2. Number of total vehicles the depot station have : **num_vehicles** in range [5,10,20]
3. Maximum number of bikes each station have : **capacity** in range [5,15,25]
4. The initial percentage of N.bikes in the capacity of each station : **init_ratio** in range [0.6,0.7,0.8]
5. The percentage of N.bikes in the capacity of each station when calling for refilling : **reset_ratio** in range [0.1,0.3,0.5]
6. The threshold number of stations calling for a certain vehicle to reset : **reset_threshold** in range [4,6,8]
7. The time interval for a vehicle to reset the stations when the threshold is not reach : **reset_delay** in range [10,20,30]
