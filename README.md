# Stralende
Course: Project Computational Science, University of Amsterdam

Authors: Esmée van der Mark, Emma Kok, Tamara Stoof

Group: Stralend

Date: 26-01-2021

This repository consists of a number of files. Three python files and 13 txt files. The .txt files contain the data that was used in the statistics.py and visualisation.py files. The data in the txt files were created using the CA_Dumai_forest_fires.py file. As the simulation of the forest fires in the latter file makes uses of random probability, the values will always be different between any number of runs. Therefore, to ensure that others can reproduce our exact figures, the data from the CA_Dumai_forest_fires.py file was stored separately. Simply put all txt files in this repository in the same folder as the .py files and run the visualization.py or statistics.py file and you can recreate the same figures and statistical conclusions.

The CA_Dumai_forest_fires.py file contains the code that was used to construct a two dimensionsal cellular automaton that can simulate a forest fire in Dumai based on the paper of Mutthulakshmi et al. (2020). This CA makes use of Moore neighborhoods and the state of the cells depend on the vegetation types and density, as well as whether or not a cell is burning or has already been burnt to the ground. Burnt down areas, as well as city areas and areas outside of the area of interest cannot burn. Whether or not a cell can burn also depends on the probability of a neighbouring cell causing the cell to catch a flame. This burning probability depends on the vegation types and density, as well as the wind speed and direction. The location of the burning neighbouring cell relative to the cell is therefore an important factor that influences a neighbouring cell's chances of setting the cell ablaze.  
The CA_Dumai_forest_fires.py file tests the efficiency of numerous mitigation methods to stop the forest fire propagation front. Two main mitigation methods were used: constructed fire lines and temporary fire lines. The difference between the two lies in the fact that constructed fire lines, once initialized, will remain in the grid, while temporary fire lines will be removed affter several time steps. The type of fire lines used can be chosen on line 121. If you want to turn of the fire lines altogether, you should also set the variable noFireLines on line 115 to 1. This variable is used to make sure the data will be written to the correct .txt file.

Within the two methods, we have further divided the fire lines based on distance from the fire propagation front. The constructed and temporary fire lines can be placed on three different distances. The distance can be changed at line 128 or 134 for the temporary and constructed fire lines respectively. In addition to distance, we have created three different types of shapes the constructed fire lines can be: a triangle, a square or a straight line (similar to the temporary fire line, but permanent). The shape of the constructed fire lines can be changed on line 140. 

The CA_Dumai_forest_fires.py file computes the fraction of burnt cells at the end of a simulation run (14 time steps/2 weeks) and adds it to a list. You can manually change how many simulation runs you want to run (and thus the size of your fraction burnt data) by changing the repeats variable on line 153. If you want to visualize a simulation you can set the repeats variable to 1. The spread of the forest fire throughout the grid will be shown for every time step as well as the end result (the fourteenth time step).

Lastly, the variable write_to_file on line 159 is used to adjust the code to append data to a .txt file or not. The data appended to the .txt files are the final lists containing the final burnt fractions for all n simulation runs. Which file the data is written to depends on which combination of fire lines, distances, and shapes were used to run the simulation. The write_to_file variable's default is turned off, because it will otherwise always append more data to a .txt file after every run. This would cause problems if you wish to recreate the exact same figures as were used in our poster.  

To reproduce the same statistics and figures as were shown in our report and poster presentation, you should use the .txt files in this repository. Simply put all the .txt files and the visualization.py and statistics.py files in the same folder and run either the statistics.py file or the visualisation.py file. The visualization.py file can be run without any further adjustments and it will produce the figures (i.e. figures 6, 7 and 8) we have used for the report and poster. The statistics.py file contains all the codes, but no print statements. If you want to find the p-value of one of the tests, you should add the print statement manually. However, the p-value (either p < 0.05 or p > 0.05) of each test is added as a comment to ensure you don't necessarily have to. 

The statistics.py file first loads the data from all the .txt files and stores them in variables. These variables are subsequently tested for normallity. All variables were non-Gaussian, so we made use of two non-parametric tests, the Kruskal-Wallis test and the Wilcoxon-Mann-Whitney test. These tests are used to compare whether there is a significant difference in the mean of 2 (Wilcoxon-Mann-Whitney) or more (Kruskal-Wallis) groups. The latter test only tells you if one of the groups differs from the others, but does not say which one is different. That's why the Wilcoxon-Mann-Whitney test was used. If the p-value of one of the tests was less than 0.05, then there was a significant difference.
Lastly, the Wilcoxon-Mann-Whitney test offers an option to specify whether to use a one-side (both sides) or a two-sided test. We have chosen the type of alternative hypothesis based on findings drom the paper of Mutthulakshmi et al. (2020). The comments in the statistics.py file should provide sufficient information to interpret the findings.


Modules that were used in this project: (hier moeten dus nog versies van alle modules bij worden gezet enzo)

matplotlib.pyplot

numpy

random

math

json

pylab

scipy.stats

seaborn


Version of python used and the version of the used modules




