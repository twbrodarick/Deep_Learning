# LSTM Stock Predictors - Closing Prices vs. Fear & Greed

## Background

Due to the volatility of cryptocurrency speculation, investors will often try to incorporate sentiment from social media and news articles to help guide their trading strategies. One such indicator is the [Crypto Fear and Greed Index (FNG)](https://alternative.me/crypto/fear-and-greed-index/) which attempts to use a variety of data sources to produce a daily FNG value for cryptocurrency. The 2 notebooks included in this repo test whether the FNG indicator provides a better signal for cryptocurrencies than the normal closing price data and vice versa.

## Files

"../Closing_Prices" notebook:  Previous Bitcoin closing prices are used to predict the next closing price.
"../Fear_and_Greed" notebook: FNG values are used to predict the next closing price.
- - 
## Model Considerations

1. Each model uses 70% of the data for training and 30% of the data for testing.

2. Model data is scaled with MinMaxScaler.

3. The same parameters and training steps are used for each model in order to compare them accurately.

4. Note that 10 estimators are used for both models.

5. The same custom LSTM RNN architecture is produced in each notebook. 
    * Fear_and_Greed: Data is fit using FNG values
    * Closing_Prices: Data is fit using only Bitcoin closing prices.


### Model Evaluations

> Which model has a lower loss?

    * Closing Prices model produces significantly lower loss of 0.0167 compared to 0.1686 for the FNG model.
    
> Which model tracks the actual values better over time?

    * Closing Prices model tracks actual values very well compared to the material divergence experienced by the FNG model over time.
   ![closing](closing.png)  ![fng](fng.png)
   
> Which window size works best for the model?
    * Window size=1 appears to minimize loss the best for CLosing Prices. FNG's loss improved as the window size increased, but not enough to overtake Closing Prices as a preferable model.

### Resources

[Keras Sequential Model Guide](https://keras.io/getting-started/sequential-model-guide/)

[Illustrated Guide to LSTMs](https://towardsdatascience.com/illustrated-guide-to-lstms-and-gru-s-a-step-by-step-explanation-44e9eb85bf21)

[Stanford's RNN Cheatsheet](https://stanford.edu/~shervine/teaching/cs-230/cheatsheet-recurrent-neural-networks)
