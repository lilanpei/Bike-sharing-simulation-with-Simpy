# Bike-sharing-simulation-with-Simpy

## Station :

* The bike-sharing station with a capacity(maximum number of bikes/docks), init with $init_ratio \prod capacity$ of bikes.
* The monitor process : when the bikes in the station(a container) <= capacity times by reset_ratio or >= capacity times by (1-reset_ratio), the calling of reset station will triggered, the station will be reset with half number of capacity of bikes when the refilling vehicle arrived.

## Depot Station :
* The depot station with capacity(num_vehicles), a vehicle is a container which has the ability to reset maximum half number stations.
* The monitor process : when a vehicle accumulate for capacity minus reset_threshold number of request for reset or the reset_delay divide delay_rate of time passed.(the delay rate is the rate for generating passengers in different period of time during the day times by 0.5)

## Passenger :
* The passengers (around 3720 with the current rate) will be generated with different rate in five periods(early-hours, morning, noon, evening, midnight) of a day, the time interval between consecutive passengers follows the exponential distributing.
* The passenger will run out of patience when waiting for a random number of minutes from 10 to 20 to get a bike and leave the station.
* The passenger will run out of patience when waiting for a random number of minutes from 20 to 30 to put a bike and then leave the station with the bike thrown away at the station.

## Main :
* Start running the station for five periods (early-hours, morning, noon, evening, midnight) with different rate for refilling and generate passengers.

## Grid search parameters :
1. The number of stations : **num_stations** fixed to 20.
2. Number of total vehicles the depot station have : **num_vehicles** in range [5,10,20]
3. Maximum number of bikes each station have : **capacity** in range [5,15,25]
4. The initial percentage of N.bikes in the capacity of each station : **init_ratio** in range [0.6,0.7,0.8]
5. The percentage of N.bikes in the capacity of each station when calling for refilling : **reset_ratio** in range [0.1,0.3,0.5]
6. The threshold number of stations calling for a certain vehicle to reset : **reset_threshold** in range [4,6,8]
7. The time interval for a vehicle to reset the stations when the threshold is not reach : **reset_delay** in range [10,20,30]
