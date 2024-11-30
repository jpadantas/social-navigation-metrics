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

This project includes classes and functions aimed at facilitating the analysis of aircraft trajectories and experimental design:

- `SocialNavigationMetrics`: Calculates various metrics from trajectory data.
- `generate_flight_path`: Generates 3D flight paths with linear or curved trajectory options.
- `plot_3d_trajectories`: Visualizes flight paths in 3D, aiding in navigational and safety assessments.
- **Sample Size Calculation**: Implements statistical analysis for determining the required sample size for ANOVA tests, including adjustments for repeated measures.

#### Detailed Description of Classes and Functions

##### SocialNavigationMetrics

This class is initialized with a DataFrame containing trajectory data and provides the following methods:

- `calculate_metric(order)`: Computes the mean squared derivative (velocity, acceleration, or jerk) based on the specified order.
- `minimum_distance()`: Finds the shortest distance between two paths throughout the sampled points.
- `collision_risk(epsilon, t_critical)`: Evaluates potential collision risks by identifying frames where the distance between trajectories falls below a safety threshold or the Time to Reach (TTR) is critically low.

##### Flight Path Generation

The `generate_flight_path(start_pos, end_pos, num_points, curve=False)` function creates flight paths between specified start and end points with a specified number of points. It supports generating linear and curved trajectories, with the option to include a sinusoidal variation in the y-axis.

##### Trajectory Visualization

The `plot_3d_trajectories(df, title, labels, styles)` function plots paths from the DataFrame `df` using Matplotlib. Customization options include title, labels for each path, and plot appearance styles.

##### Sample Size Analysis (Sample Size Notebook)

The **sample_size.ipynb** notebook contains a detailed implementation of sample size calculations for ANOVA with repeated measures. It leverages the `statsmodels` library and generates a plot that shows:

- Required sample size as a function of effect size.
- Adjustments for repeated measures based on intra-class correlation.

The notebook includes:

- **Effect Size (Cohen's f)**: Specifies the magnitude of the difference expected to detect.
- **Alpha (α)**: Significance level, typically set at 0.05.
- **Power**: Probability of correctly rejecting the null hypothesis (default 0.8).
- **Number of Groups (k)**: Defines the number of independent groups or conditions.
- **Intra-class Correlation (ρ)**: Accounts for the correlation between repeated measures on the same subject.
- **Number of Repeated Measures (m)**: Specifies how many times each subject is measured.

The sample size calculations and corresponding plots can guide the experimental design process for aerospace studies or other applications.

#### Example

The repository provides code snippets to:

1. Generate synthetic flight paths.
2. Visualize 3D trajectories.
3. Calculate navigation metrics, including velocity, acceleration, jerk, minimum distance, and collision risk.
4. Analyze statistical sample size for ANOVA using the **sample_size.ipynb** notebook.

To get started, refer to the provided example scripts and the **sample_size.ipynb** notebook for detailed demonstrations.

---

### Dependencies

Ensure you have the following Python libraries installed:

```bash
pip install pandas numpy matplotlib statsmodels
