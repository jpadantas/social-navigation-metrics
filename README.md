# Social Navigation Metrics

This repository provides a suite of tools designed to calculate critical navigation metrics and visualize aircraft trajectories in 3D. These metrics, which include velocity, acceleration, jerk, minimum distance between aircraft, and collision risk, are invaluable for simulating flight paths and conducting safety analysis in aerospace engineering.

## Installation

Ensure you have Python installed on your system along with the following libraries:

- pandas: For data manipulation and analysis.
- numpy: For numerical operations.
- matplotlib: For graph plotting.

Install these packages using pip with the command:

```bash
pip install pandas numpy matplotlib
```

### Usage

#### Overview

This project includes a class and several functions aimed at facilitating the analysis of aircraft trajectories:

- `SocialNavigationMetrics`: Calculates various metrics from trajectory data.
- `generate_flight_path`: Generates 3D flight paths with linear or curved trajectory options.
- `plot_3d_trajectories`: Visualizes flight paths in 3D, aiding in navigational and safety assessments.

#### Detailed Description of Classes and Functions

##### SocialNavigationMetrics

Initialized with a DataFrame containing trajectory data, this class offers methods to:

- `calculate_metric(order)`: Computes the mean squared derivative (velocity, acceleration, or jerk) based on the specified order.
- `minimum_distance()`: Finds the shortest distance between two paths throughout the sampled points.
- `collision_risk(epsilon, t_critical)`: Evaluates potential collision risks by identifying frames where the distance between trajectories falls below a safety threshold or the Time to Reach (TTR) is critically low.

##### Flight Path Generation

The `generate_flight_path(start_pos, end_pos, num_points, curve=False)` function creates flight paths between specified start and end points with a specified number of points. It can generate both linear and curved trajectories, with the option to include a sinusoidal variation in the y-axis.

##### Trajectory Visualization

The `plot_3d_trajectories(df, title, labels, styles)` function plots paths from the DataFrame `df` using Matplotlib. It allows customization of the plot with a title, labels for each path, and styles for plot appearance.

### Example

The following example demonstrates how to generate flight paths, compute metrics, and visualize trajectories:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

# Generate flight paths
num_points = 60
human_path = generate_flight_path([0, 0, 1000], [300, 50, 1200], num_points, curve=True)
wingman_path = generate_flight_path([0, -10, 1000], [300, 40, 1200], num_points, curve=True)

# Create DataFrame
data = {
    'human_x': human_path[:, 0],
    'human_y': human_path[:, 1],
    'human_z': human_path[:, 2],
    'wingman_x': wingman_path[:, 0],
    'wingman_y': wingman_path[:, 1],
    'wingman_z': wingman_path[:, 2]
}
df = pd.DataFrame(data)

# Initialize metrics calculation
metrics = SocialNavigationMetrics(df)
print("Velocity (M1):", metrics.calculate_metric(1))
print("Acceleration (M2):", metrics.calculate_metric(2))
print("Jerk (M3):", metrics.calculate_metric(3))
print("Minimum Distance (M4):", metrics.minimum_distance())
print("Collision Risk (M5):", metrics.collision_risk(10, 5))

# Plot trajectories
plot_3d_trajectories(df, title='3D Trajectories of Human Pilot and Wingman', labels=['Human Pilot', 'Wingman'], 
                     styles=[{'color': 'blue', 'marker': 'o'}, {'color': 'red', 'marker': '^'}])
```
