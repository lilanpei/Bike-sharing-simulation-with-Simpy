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
  * (10, 20) minutes to get a bike, otherwise they would leave.
  * (20, 30) minutes to put a bike, otherwise they may not park the bike in the dock properly.

## Main :
* Run the system.

## Grid search parameters :
1. **num_stations** (20) : the number of stations. 
2. **num_vehicles** ([5,10,20]) : the number of vehicles in a depot station.
3. **capacity** ([5,15,25]) : the capacity of each station.
4. **init_ratio** ([0.6,0.7,0.8]) : #bikes / capacity in each station initially.
5. **reset ratio** ([0.1,0.3,0.5]) : #bikes/capacity to call for repositioning vehicles.
6. **reset_threshold** ([4,6,8]) : the number of stations received (10 - reset_threshold) for a vehicle to depart. 
7. **reset_delay** ([10,20,30]) : the time interval to send a vehicle.

## Case study :
1. Base case (no **Patience strategy**, no Refilling strategy **Refilling strategy**).
2. Base case + **Patience strategy**.
3. 
