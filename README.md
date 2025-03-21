# Eco-Ride-Sharer

Creating a Python program for an Eco-Ride-Sharer involves multiple components, including data handling, route optimization, and potential user interfaces. I'll provide a simplified version that outlines the core functionalities. This code assumes a simplified environment without real-time external data but can be expanded as necessary.

```python
import random
import logging
from typing import List, Tuple

# Configure logging
logging.basicConfig(level=logging.INFO)

# Sample data structure for ride requests
class RideRequest:
    def __init__(self, user_id, start_location, end_location, time_of_request):
        self.user_id = user_id
        self.start_location = start_location
        self.end_location = end_location
        self.time_of_request = time_of_request

    def __repr__(self):
        return f"RideRequest(user_id={self.user_id}, start={self.start_location}, end={self.end_location})"

# Sample users database
users_db = {
    1: {"name": "Alice"},
    2: {"name": "Bob"},
    3: {"name": "Charlie"}
}

# Assume a basic function to calculate the "eco-friendliness" of the route
def calculate_eco_score(route: List[Tuple[float, float]]) -> float:
    # An abstract eco-score calculation
    return random.uniform(0, 100)

# Assume a basic function to optimize routes for carpooling
def optimize_route_for_carpool(requests: List[RideRequest]) -> List[RideRequest]:
    # This function would include logic to cluster ride requests
    # For simplicity, let's just return the requests as is, assuming they are optimized
    return requests

# Function to display available ride requests
def display_ride_requests(requests: List[RideRequest]):
    logging.info("Current Ride Requests:")
    for request in requests:
        logging.info(request)

# Main function to run the Eco-Ride-Sharer
def main():
    try:
        # Sample ride requests
        ride_requests = [
            RideRequest(1, (40.7128, -74.0060), (40.73061, -73.935242), "08:30"),
            RideRequest(2, (34.0522, -118.2437), (34.052235, -118.243683), "09:00"),
            RideRequest(3, (41.8781, -87.6298), (41.881832, -87.623177), "09:30"),
        ]

        # Display current ride requests
        display_ride_requests(ride_requests)

        # Optimize routes for carpooling
        optimized_requests = optimize_route_for_carpool(ride_requests)
        logging.info("Optimized Ride Requests for Carpooling:")
        for request in optimized_requests:
            logging.info(request)

        # Calculate eco-scores for each optimized route
        for request in optimized_requests:
            eco_score = calculate_eco_score([request.start_location, request.end_location])
            logging.info(f"Eco-score for the route of user {request.user_id}: {eco_score:.2f}")

    except Exception as e:
        logging.error(f"An error occurred: {e}")

if __name__ == '__main__':
    main()
```

### Explanation:

1. **Logging Configuration**: Set up logging to capture information and errors.

2. **Class Definition**: `RideRequest` captures details of each ride.

3. **Users Database Simulation**: `users_db` is a dictionary simulating user information.

4. **Eco-score Calculation**: `calculate_eco_score()` currently returns a random score. This can be expanded to consider factors like distance, vehicle type, etc.

5. **Route Optimization**: `optimize_route_for_carpool()` is a placeholder where real optimization logic can be implemented.

6. **Error Handling**: The main function includes a try-except block, and in case of any errors, they are logged properly.

This is a basic structure and can be expanded and modified as necessary to include real-time data fetching (e.g., using GPS APIs), database integration, and a user interface.