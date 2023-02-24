## Evaluation Metrics


* Mean Absolute Percentage Error (MAPE)
    * ![image](https://user-images.githubusercontent.com/16402963/221255443-e5500982-68f2-492f-b3e3-ff7f5d284a6b.png)
    * Advantages
          * Expressed as a percentage, which is scale-independent and can be used for comparing forecasts on different scales. We should remember though that the values of MAPE may exceed 100%.
          * Easy to explain to stakeholders.
    * Shortcomings
          * MAPE takes undefined values when there are zero values for the actuals, which can happen in, for example, demand forecasting. Additionally, it takes extreme values when the actuals are very close to zero.
          * MAPE is asymmetric and it puts a heavier penalty on negative errors (when forecasts are higher than actuals) than on positive errors. This is caused by the fact that the percentage error cannot exceed 100% for forecasts that are too low. While there is no upper limit for the forecasts which are too high. As a result, MAPE will favor models that under-forecast rather than over-forecast.
          * MAPE assumes that the unit of measurement of the variable has a meaningful zero value. So while forecasting demand and using MAPE makes sense, it does not when forecasting temperature expressed on the Celsius scale (and not only that one), as the temperature has an arbitrary zero point.
          * MAPE is not everywhere differentiable, which can result in problems while using it as the optimization criterion.

* symmetric Mean Absolute Percentage Error (SMAPE)
    * ![image](https://user-images.githubusercontent.com/16402963/221255483-32e6a2d0-f564-4276-96b0-1c287bf2f638.png)
    * Advantages
          * Expressed as a percentage.
          * Fixes the shortcoming of the original MAPE — it has both the lower (0%) and the upper (200%) bounds.
    * Shortcomings
          * Unstable when both the true value and the forecast are very close to zero. When it happens, we will deal with division by a number very close to zero.
          * sMAPE can take negative values, so the interpretation of an “absolute percentage error” can be misleading.
          * The range of 0% to 200% is not that intuitive to interpret, hence often the division by the 2 in the denominator of the sMAPE formula is omitted.
          * Whenever the actual value or the forecast has the value is 0, sMAPE will automatically hit the upper boundary value.
          * Same assumptions as the MAPE regarding the meaningful zero value.
          * While fixing the asymmetry of boundlessness, sMAPE introduces another kind of delicate asymmetry caused by the denominator of the formula. Imagine two cases. In the first one, we have A = 100 and F = 120. The sMAPE is 18.2%. Now a very similar case, in which we have A = 100 and F = 80. Here we come out with the sMAPE of 22.2%.

*  (hfSMAPE)


* Mean Absolute Scaled Error (MASE)
    * In statistics, the mean absolute scaled error (MASE) is a measure of the accuracy of forecasts. It is the mean absolute error of the forecast values, divided by the mean absolute error of the in-sample one-step naive forecast.
    * ![image](https://user-images.githubusercontent.com/16402963/221256096-b053bb08-fa67-4d7b-9bd3-1ed7c7dab80e.png) ![image](https://user-images.githubusercontent.com/16402963/221256135-423c9c7d-b876-43ce-8e71-e59626bc82fe.png)
 ![image](https://user-images.githubusercontent.com/16402963/221256198-b5a6daeb-b041-4288-af86-26ed0293ea76.png)
    * MASE gives an indication of effectiveness of forecasting algorithm with respect to a naïve forecast. Its value greater than one (1) indicates the algorithm is performing poorly compared to the naïve forecast.
    * MASE is immune to the problem faced by Mean Absolute Percentage Error (MAPE) when actual time series output at any time step is zero. In this situation MAPE gives an infinite output, which is not meaningful. However, it is noted that for a time series with all values equal to zero at all steps, MASE output will also be not defined but such time series are not realistic.
    * MASE is independent of the scale of the forecast since it is defined using ratio of errors in the forecast. This means MASE values will be similar if we are forecasting high valued time series like number of internet traffic packet crossing a router hourly when compared to forecasting number of pedestrians crossing a busy traffic light every hour.
 
* Mean Directional Accuracy (MDA)
    * ![image](https://user-images.githubusercontent.com/16402963/221256664-8c771194-f8c3-4481-9314-a59bdfc199cc.png)
     
* the logarithm of the accuracy ratio (the ratio of the forecasted to the actual value)


### Reference
* https://towardsdatascience.com/choosing-the-correct-error-metric-mape-vs-smape-5328dec53fac
