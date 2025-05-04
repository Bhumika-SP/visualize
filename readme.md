from agent_torch.visualize import GeoPlot

# Initialize your simulation config (contains metadata like number of episodes, steps per episode, etc.)
# config = ...

# Set your Cesium Ion access token for 3D globe visualization
cesium_token = "your_cesium_ion_token"

# Create a visualizer instance with simulation config and Cesium access token
geoplot = GeoPlot(config, cesium_token)

# Run the simulation loop
for i in range(0, num_episodes):
  # Advance the simulation by a set number of steps
  runner.step(num_steps_per_episode)

  # Generate a 3D geospatial visualization from the state trajectory
  # 'entity_position' is the path to the coordinates (latitude, longitude)
  # 'entity_property' is the path to the value you want to visualize (e.g., money spent)
  geoplot.visualize(
    name = f"consumer-money-spent-{i}",  # Output file name (HTML + GeoJSON)
    state_trajectory = runner.state_trajectory,  # List of simulation states over time
    entity_position = "consumers/coordinates",  # Path to coordinates in the state dictionary
    entity_property = "consumers/money_spent",  # Path to the property being visualized
  )
