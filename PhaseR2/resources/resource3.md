# PyAlgoTrade Python Backtesting Library

**URL**: https://github.com/gbeced/pyalgotrade
**Accessed**: April 8, 2025

## Overview

PyAlgoTrade is an event-driven algorithmic trading Python library. It was created by Gabriel Becedillas (gbeced) and designed to be simple and easy to use. While its initial focus was on backtesting, it also supports paper trading and even live trading through extensions.

**Note**: The project has been marked as deprecated by its creator and is no longer maintained as of November 13, 2023.

## Key Features

1. **Event-Driven Architecture**
   - Efficient and scalable event-based system
   - Events trigger trading actions like signals and trade execution

2. **Simplicity and Ease of Use**
   - Lightweight and straightforward design
   - Built on top of the Python standard library
   - Lower complexity barrier for beginners

3. **Extensibility**
   - Designed to be easily extended
   - Allows implementing custom data feeds, indicators, and strategies
   - Integration with preferred data sources

4. **Comprehensive Documentation**
   - Well-documented codebase
   - Numerous examples and tutorials
   - Accessible to both beginners and experienced traders

5. **Technical Indicators**
   - Includes technical indicators like SMA, WMA, EMA, RSI, Bollinger Bands
   - Supports development of custom indicators

6. **Multiple Order Types**
   - Support for Market, Limit, Stop, and StopLimit orders

7. **Data Source Flexibility**
   - Supports CSV format data
   - Compatible with Yahoo! Finance, Google Finance, Quandl, and NinjaTrader
   - Supports Bitcoin trading through Bitstamp

8. **Performance Metrics**
   - Calculates metrics like Sharpe ratio
   - Includes drawdown analysis

9. **Additional Features**
   - TA-Lib integration
   - Twitter event handling
   - Event profiler

## Limitations

1. **Deprecated Status**
   - No longer maintained by its creator
   - May have compatibility issues with newer Python versions

2. **Limited Advanced Features**
   - Lacks some optimization tools found in other libraries
   - Limited support for complex order types
   - May be insufficient for sophisticated trading strategies

3. **Performance**
   - May not scale as well with large datasets compared to vectorized approaches

## Technical Details

- **Supported Python Versions**: 2.7/3.7
- **Dependencies**: NumPy, SciPy, pytz, dateutil, requests
- **Optional Dependencies**: matplotlib (plotting), ws4py/tornado (Bitstamp), tweepy (Twitter)
- **Installation**: `pip install pyalgotrade`
- **GitHub Stats**: 4.5K stars, 1.4K forks

## Example Usage

```python
from datetime import datetime
import pyalgotrade
from pyalgotrade import strategy
from pyalgotrade.barfeed import quandlfeed

class MyStrategy(strategy.BacktestingStrategy):
    def __init__(self, feed, instrument):
        super(MyStrategy, self).__init__(feed)
        self.__instrument = instrument
        
    def onBars(self, bars):
        bar = bars[self.__instrument]
        self.info("%s: %s" % (bar.getDateTime(), bar.getClose()))

# Load the bar feed from the CSV file
feed = quandlfeed.Feed()
feed.addBarsFromCSV("orcl", "WIKI-ORCL-2000-quandl.csv")

# Evaluate the strategy with the feed
myStrategy = MyStrategy(feed, "orcl")
myStrategy.run()
```

## Conclusion

Despite being deprecated, PyAlgoTrade remains a valuable option for beginners due to its simplicity and well-documented codebase. Its event-driven architecture provides a good foundation for algorithmic trading, but users should be aware of its limitations and lack of ongoing maintenance. For new projects, considering active alternatives like Backtrader might be more future-proof.