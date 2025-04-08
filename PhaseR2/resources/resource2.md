# Zipline Python Backtesting Library

**URL**: https://github.com/quantopian/zipline
**Accessed**: April 8, 2025

## Overview

Zipline is a Pythonic algorithmic trading library with an event-driven system for backtesting. It was developed by Quantopian and used as their backtesting and live-trading engine. Despite Quantopian shutting down, Zipline remains one of the most popular backtesting libraries in the Python ecosystem.

## Key Features

1. **Event-Driven Architecture**
   - Uses an event-driven model for backtesting
   - Simulates market events to trigger trading decisions

2. **Ease of Use**
   - Designed to be intuitive and stay out of the way
   - Focuses on algorithm development rather than framework complexity

3. **"Batteries Included"**
   - Many common statistics built-in (moving averages, linear regression)
   - Readily accessible within user-written algorithms

4. **PyData Integration**
   - Uses Pandas DataFrames for historical data input and performance statistics output
   - Integrates with the broader PyData ecosystem

5. **Integration with Statistics and ML Libraries**
   - Compatible with matplotlib, scipy, statsmodels, sklearn
   - Supports development and analysis of sophisticated trading systems

6. **Pipeline API**
   - Powerful data manipulation capabilities
   - Enables complex factor-based models
   - Handles point-in-time data issues

7. **Data Bundles**
   - Built-in support for various data bundles
   - Simplifies historical price data management

## Limitations

1. **Limited Support for Multiple Assets**
   - Less suitable for complex portfolio-based strategies
   - Primarily designed for single-asset backtesting

2. **Documentation Gaps**
   - Less comprehensive documentation compared to some alternatives
   - Community support has diminished since Quantopian's shutdown

3. **Maintenance Status**
   - No longer maintained by Quantopian team
   - Community forks exist (zipline-reloaded) but fragmented support

## Technical Details

- **Supported Python Versions**: 2.7, 3.5, and 3.6
- **Installation Methods**: pip or conda
- **License**: Apache-2.0
- **GitHub Stars**: 18.3K
- **Forks**: 4.8K

## Community

Since Quantopian's shutdown, community support has decreased, but the library remains popular with many forks and active users. Alternative versions like zipline-reloaded aim to maintain and extend the library's functionality.

## Example Usage

```python
from zipline.api import order_target, record, symbol

def initialize(context):
    context.i = 0
    context.asset = symbol('AAPL')

def handle_data(context, data):
    # Skip first 300 days to get full windows
    context.i += 1
    if context.i < 300:
        return

    # Compute averages
    short_mavg = data.history(context.asset, 'price', bar_count=100, frequency="1d").mean()
    long_mavg = data.history(context.asset, 'price', bar_count=300, frequency="1d").mean()

    # Trading logic
    if short_mavg > long_mavg:
        order_target(context.asset, 100)
    elif short_mavg < long_mavg:
        order_target(context.asset, 0)

    # Save values for later inspection
    record(
        AAPL=data.current(context.asset, 'price'),
        short_mavg=short_mavg,
        long_mavg=long_mavg
    )
```