Overview
This repository contains a Python implementation of a hybrid demand forecasting model combining Exponential Smoothing and Croston's method (25th & 75th percentile variants). The model was designed to optimize inventory management for perishable goods, achieving:
- 57.59% reduction in forecast error
- 75% decrease in inventory waste

There are three data frames ; expo data frame, Croston_25 data frame and Croston_75 data
frame
For exponential data frame

Initialize alpha = 0
Initialize mse = infinity
For loop (Iterating alpha from 0.1 to 1 with a step size of 0.1)
Calculate_mse(alpha, expo[‘actual quantity’]) ## function calling with arguments given
are current value of alpha and actual quantity sold column from exponential data
frame.
If (avg mse calculated using 7 day phased model using function calculate_mse &lt; mse)
Alpha for expo model = alpha
Mse = avg mse calculated using 7 day phased model
Else:
continue

Calculate_mse (alpha, actual quantity sold column) ## Function definition
Create a list to store the mse values to find the average mse for each alpha value
Initialize total_mse variable which will contain the sum of all the mse values
calculated from each 7 day window
Window_size = 7
Number of 7 day windows you can get from the data = len(actual quantity sold column)
– window_size + 1

For loop (Iterate I over a range of the number of 7-day window available)
Seven day actual quantity sold data is stored in the a one dimensional array
(Series) called actual
Another list called forecast is created populated with 7 values (seven values are
the same i.e the value at the zeroth position)
For loop ( iterating over a range of 1 to 7)

Populating forecast list using formula for exponential smoothing
## forecast now contains forecast values for 7 days
mse = mean_squared_error(actual, forecast)
append mse to mse_values
total_mse = sum(mse_values)
return total_mse/(number of 7 day window available)
