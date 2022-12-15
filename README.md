# Divergence-Crypto-Strategy
In this notebook, we will create a strategy using RSI divergence.

### 1. Import data and libraries
First, we will import the necessary libraries and then, fetch the minute data for Ethereum/Bitcoin from a csv file

### 2. Compute the RSI and Aroon values for the price series
Set the same look back period for all the indicators to be used.

Calculate the RSI using the TaLib library and close prices.

Use the Aroon indicator in the TaLib library to calculate the AroonUp and AroonDown indicators. Later we will compare the Aroon Values of the price series with those of the RSI.

### 3. Compute the Aroon Values for the RSI
Now we will calculate the AroonUp and AroonDown values for the RSI values using the Aroon indicator in TaLib library. After this, we will use these values to observe how the market's highs and lows have behaved compared with the highs and lows of the RSI.

### 4. Calculate the UpSpread and DownSpread
Calculate the Spread (difference) of AroonUp values for the price series and the RSI.

Calculate the Spread (difference) of AroonDown values for the price series and the RSI.

Create new columns to hold the buy and sell signals.

Visualize the UpSpread with the threshold value.

### 5. Generate the Trading signal
We will buy wherever the UpSpread crosses the threshold value 't'.

We will buy wherever the DownSpread crosses the threshold value 't'.

If UpSpread value > 75 then buy the currency pair.

If DownSpread value > 75 then sell the currency pair.

Combine the two signals to create a signal column.

### 6. Compute the cumulative strategy return
The procedure for calculating the strategy performance is:

Candle 1 Closes ---> Indicators are calculated and the signal is generated

Candle 2 Opens ---> Signal generated at the end of the previous candle is used to enter the trade

Candle 2 Closes ---> Indicators are calculated and the new signal is generated

Candle 3 Opens ---> The returns for the position taken at the Open of candle 2 is calculated and the process is repeated

Assign the previous candles' signal as TradeSignal

Calculate the returns of each candle using the Open prices of the next candle and open price of the current candle
