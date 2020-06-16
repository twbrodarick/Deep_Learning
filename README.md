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

* The Closing Prices model produces significantly lower losses across a variety of window sizes.
    
> Which model tracks the actual values better over time?

* The Closing Prices model tracks actual values very well compared to the material divergence experienced by the FNG model over time.

   ![closing](https://github.com/twbrodarick/Deep_Learning/blob/master/Data_Files/closing.png)  
   ![fng](https://github.com/twbrodarick/Deep_Learning/blob/master/Data_Files/fng.png)
   
> Which window size works best for the model?

* A *window size of 1* minimizes loss the best for Closing Prices at 0.0167. The loss trends upward for both models as window sizes are increased.
* FNG's loss at window size = 1 was 0.1686. 
* However, the FNG model loss rose much faster than the loss for the Closing Prices model as windows sizes increased. 
* For example, at window size = *2* the loss for Closing Prices increases to 0.0178 and 0.1820 for the FNG model.
* At window size = *10* the loss for Closing Prices rises to 0.0793 and *0.2332* for the FNG model.

### Resources

[Keras Sequential Model Guide](https://keras.io/getting-started/sequential-model-guide/)

[Illustrated Guide to LSTMs](https://towardsdatascience.com/illustrated-guide-to-lstms-and-gru-s-a-step-by-step-explanation-44e9eb85bf21)

[Stanford's RNN Cheatsheet](https://stanford.edu/~shervine/teaching/cs-230/cheatsheet-recurrent-neural-networks)
