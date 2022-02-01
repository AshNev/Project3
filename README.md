# Project3
# Cryptocurrency VIP Trader
Cryptocurrency "Volume In Price" Trader is an automated trading algorithm that works on three levels.  First it will scan the Cryptocurrency market searching for volatility, second it will determine an entry and finally it will then manage the trade.

## Libraries Used
from binance import Client<br/>
import websockets<br/>
import json<br/>
import pandas as pd<br/>
import asyncio<br/>
import time<br/>
import threading<br/>
from colorama import Fore, Back, Style


## 1. Crypto Scanner
We first wanted to build a crypto scanner that would scan the Binance Exchange searching for an early indication of a potential move up.  For this to happen we needed volatility! In its simplest form we looked for an increase in upside momentum based on volume and price multiples.
### Variables
- Timeframe (15 seconds, 15 minutes)
- Price increase (a higher close (> 0.1%))
- Volume increase (0.1% up to 10%)


## 2. Crypto Entry Algorithm
Once momentum confirmed and the potential Cryptocurrency has been identified we then had to determine some generic entry requirements that would be robust enough to work over the vast majority of all Cryptos we included in the trader.  This proved a challenge as all cryptos do not move in the same way! But, however, it was decided that based on momentum we would first make sure the volume was indeed buyers coming into the market.  This was achieved by an increase in volume and a close higher than the previous close.  We also wanted to make sure that it was trending in our intended trade direction.  For this we made sure price was above the ('x' period)Simple Moving Average.  Once this criteria had been met an at market order was placed.  
### Multi Entry
Each and every time these conditions are met an additional order is initiated.


### Variables
- Simple Moving Average (SMA)
- Timeframe (15 seconds, 15 minutes)
- Price increase (a higher close (> 0.1%))
- Volume increase (0.1% up to 10%)


## 3. Trade Management
Trade management focussed on capital preservation and maximum capital return.  
Our initial Stop Loss is defined by the first close below the SMA.
To gain the maximum capital we have no target but rely on the multiple entries and an extended upmove to allow the SMA to extend higher and higher.
Using a trailing stop exit the first close below the SMA all open trades for that particular Crypto would be closed.
### Variables
- Simple Moving Average (SMA)


## Contributers 
Luke Macumber<br/>
Chapman Mong<br/>
Ashley Neville<br/>
Haong VT