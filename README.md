# Comparison of Quasi-Random Sequences and Pseudo-Random Sequences for Monte Carlo Integration

## Introduction

In various scientific and engineering applications, such as numerical integration, computer graphics, and financial modeling, the generation of random or quasi-random points within a unit hypercube is essential for simulations and modeling. Traditional pseudo-random number generators produce sequences that can lead to clustering and gaps, resulting in higher variance and less reliable results in these simulations. This discrepancy becomes particularly significant in Monte Carlo integration tasks, where the goal is to approximate integrals using random sampling.

Quasi-random sequences, also known as low-discrepancy sequences, offer a promising alternative. These sequences are designed to cover the sampling space more uniformly, potentially reducing the variance and increasing the accuracy of numerical simulations. Among the various quasi-random sequences, Sobol, Halton, and Faure sequences are well-known for their effectiveness.

The primary objective of this research is to compare the performance of quasi-random sequences (Sobol, Halton, and Faure) with traditional pseudo-random sequences in terms of their uniformity and effectiveness in Monte Carlo integration tasks. The goal is to demonstrate the advantages of using quasi-random sequences by analyzing their discrepancy values and visualizing their distribution in a unit hypercube.

This study addresses the following questions:
1. How do Sobol, Halton, and Faure sequences compare with pseudo-random sequences in terms of uniformity of distribution?
2. What is the impact of using quasi-random sequences on the accuracy and variance of Monte Carlo integration results?
3. How do the discrepancy values of these sequences reflect their distribution characteristics and performance in simulations?

By answering these questions, this research aims to provide a comprehensive comparison of these sequences, highlighting the benefits of quasi-random sequences for scientific and engineering applications that require reliable and uniform sampling methods.

## Methodology

The methodology of this research involves generating and evaluating the performance of different types of sequences: Sobol, Halton, Faure, and pseudo-random sequences. The performance metrics include the discrepancy values and the accuracy of Monte Carlo integration results. The following steps outline the detailed methodology used in this study:

### Sequence Generation

Four types of sequences were generated: Sobol, Halton, Faure, and pseudo-random sequences. Each sequence was generated within a 2-dimensional unit hypercube `[0, 1] x [0, 1]`.

- **Sobol Sequence**: Generated using the `scipy.stats.qmc.Sobol` class, which produces low-discrepancy sequences.
- **Halton Sequence**: Generated using the `scipy.stats.qmc.Halton` class, which produces sequences based on different prime bases for each dimension.
- **Faure Sequence**: Generated using a custom implementation to ensure values are normalized within the unit hypercube. This involves converting digits to a specific base and normalizing the sequence.
- **Pseudo-Random Sequence**: Generated using `numpy.random.rand`, producing standard pseudo-random numbers within the unit hypercube.

### Monte Carlo Integration

To evaluate the performance of these sequences, a simple Monte Carlo integration task was used. The function chosen for integration is `f(x, y) = x^2 + y^2`. For each sequence, the mean value of the function over 1,000 points generated within the unit hypercube was calculated.

The Monte Carlo integration process for each sequence is as follows:
1. Generate 1,000 points for each sequence.
2. Apply the function `f(x, y) = x^2 + y^2` to each point.
3. Compute the mean of the function values as the result of the Monte Carlo integration.

### Discrepancy Calculation

Discrepancy is a measure of how uniformly the points cover the unit hypercube. Lower discrepancy values indicate more uniform coverage. The `scipy.stats.qmc.discrepancy` function was used to calculate the discrepancy of each sequence.

The discrepancy calculation process is as follows:
1. Generate 1,000 points for each sequence.
2. Ensure all points lie within the unit hypercube by normalizing if necessary.
3. Compute the discrepancy using the `scipy.stats.qmc.discrepancy` function.

### Visualization

To visually compare the distribution of points for each sequence, the 1,000 generated points for each sequence were plotted in a 2D scatter plot. This visual representation helps to intuitively understand the uniformity and distribution characteristics of each sequence.

### Analysis and Comparison

Finally, the results of the Monte Carlo integration and discrepancy calculations for each sequence were compared. The accuracy and variance of the integration results, as well as the discrepancy values, were analyzed to draw conclusions about the performance of each sequence type.

### Tools and Libraries

The following tools and libraries were used in this research:
- **Python**: The primary programming language for implementing the sequence generation, Monte Carlo integration, and discrepancy calculations.
- **NumPy**: Used for generating pseudo-random sequences and performing numerical operations.
- **SciPy**: Used for generating Sobol and Halton sequences, as well as for discrepancy calculations.
- **Matplotlib**: Used for plotting and visualizing the distribution of points for each sequence.

This methodology ensures a comprehensive evaluation of the sequences in terms of both uniformity and effectiveness in Monte Carlo integration tasks.

## Results

In this section, the results of the comparison between quasi-random sequences (Sobol, Halton, and Faure) and pseudo-random sequences are presented. The evaluation metrics include the discrepancy values and the accuracy of Monte Carlo integration results. The findings are based on sequences generated within a 2-dimensional unit hypercube `[0, 1] x [0, 1]`, each containing 1,000 points.

### Discrepancy Values

Discrepancy is a measure of how uniformly points cover the unit hypercube. Lower discrepancy values indicate more uniform coverage, which is desirable for reducing variance in Monte Carlo simulations. The discrepancy values for each sequence type are presented in the table below.

| Sequence Type | Discrepancy Value       |
|---------------|-------------------------|
| Sobol Sequence| 1.5929e-06              |
| Halton Sequence| 2.1981e-06             |
| Faure Sequence| 3.4823e-06              |
| Pseudo-Random Sequence| 1.0118e-03      |

From this table, it is observed that the quasi-random sequences (Sobol, Halton, and Faure) have significantly lower discrepancy values compared to the pseudo-random sequence. This indicates that the quasi-random sequences provide more uniform coverage of the unit hypercube.

### Monte Carlo Integration Results

The performance of each sequence type in a Monte Carlo integration task using the function `f(x, y) = x^2 + y^2` was evaluated. The results of the integration, which represent the mean values of the function over 1,000 points, are presented in the table below.

| Sequence Type      | Monte Carlo Integration Result |
|--------------------|--------------------------------|
| Sobol Sequence     | 0.666278                       |
| Halton Sequence    | 0.666328                       |
| Faure Sequence     | 0.665979                       |
| Pseudo-Random Sequence| 0.654316                   |

This table shows that the integration results for quasi-random sequences are closer to the expected value of `2/3 ≈ 0.6667` compared to the pseudo-random sequence. This indicates that quasi-random sequences provide more accurate integration results with lower variance.

### Visual Comparison

To visually compare the distribution of points, the 1,000 generated points for each sequence type were plotted in a 2D scatter plot. The figure below shows the combined plots for Sobol, Halton, Faure, and pseudo-random sequences.

![Distribution of Points for Different Sequence Types](images/sequences.png)

This figure illustrates that the quasi-random sequences (Sobol, Halton, and Faure) exhibit a more uniform distribution of points across the unit hypercube compared to the pseudo-random sequence. This visual evidence supports the discrepancy values and integration results, demonstrating the superior performance of quasi-random sequences.

### Summary of Results

The results of this study highlight the advantages of using quasi-random sequences over pseudo-random sequences for applications requiring uniform sampling. The key findings are:
- Quasi-random sequences (Sobol, Halton, and Faure) have significantly lower discrepancy values compared to pseudo-random sequences, indicating more uniform coverage of the unit hypercube.
- Monte Carlo integration results for quasi-random sequences are closer to the expected value, demonstrating higher accuracy and lower variance.
- Visual comparison of point distributions confirms the superior uniformity of quasi-random sequences.

These findings suggest that quasi-random sequences are more suitable for scientific and engineering applications that require reliable and uniform sampling methods.