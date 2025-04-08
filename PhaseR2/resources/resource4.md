# Custom vs. Established Backtesting Frameworks

**URL**: https://mayerkrebs.com/should-you-build-your-own-backtester/
**Accessed**: April 8, 2025

## Overview

This resource examines the key considerations when deciding whether to build a custom backtesting framework or use established libraries. It also compares vectorized vs. event-driven backtesting approaches and provides insights on the advantages and disadvantages of each method.

## Custom Backtesting Frameworks

### Advantages

1. **Understanding Limitations of Backtesting**
   - Forces active trade-offs between simplicity and reality
   - Helps recognize when a backtester might fail to generate all events that would occur in real trading
   - Provides deeper understanding of market microstructure

2. **Improved Programming Skills**
   - Enhances data science capabilities
   - Develops algorithmic thinking through solving computational bottlenecks
   - Tests programming skills when handling large time series

3. **Deeper Understanding of Algorithmic Trading**
   - Requires learning market microstructure aspects
   - Provides insights into assumptions made by other backtesting engines
   - Builds foundation for more advanced trading concepts

4. **Customized Assumptions**
   - Allows introduction of tailor-made assumptions relevant to specific trading needs
   - Can incorporate complex logic for calculations like slippage
   - Enables implementation of features often missing in standard libraries (margin calls, short-selling fees)

5. **Workflow Integration**
   - Can be designed to fit seamlessly with existing workflows
   - Enables quicker transition from testing to implementation
   - Especially valuable for proprietary trading firms with established processes

### Disadvantages

1. **Reinventing the Wheel**
   - High opportunity cost of development time
   - Requires specialized skills (programming + financial market knowledge)
   - Resources could be better spent researching trading ideas

2. **No Community Support**
   - No access to community tutorials, forums, or slack/discord channels
   - Inability to benefit from shared problem-solving
   - Lack of documentation and examples

3. **Feature Development Burden**
   - Requires development of all features from scratch (take profits, stop losses, trailing stops)
   - Need to implement optimization modules and reporting dashboards
   - Many standard features already exist in established libraries

4. **Increased Bug Risk**
   - Less reliable than well-tested community libraries
   - Difficult to thoroughly test complex features
   - No community to help identify and fix bugs

## Vectorized vs. Event-Driven Backtesting

### Vectorized Backtesting

**Advantages**:
- Faster computation through parallel processing
- Easier prototyping, especially with libraries like NumPy and Pandas
- Efficient for quick testing of simple trading ideas

**Disadvantages**:
- Difficult to implement features requiring complex conditionals based on previous data
- Challenging to implement take profits, stop losses, and especially trailing stop losses
- Less realistic compared to event-driven approaches

### Event-Driven Backtesting

**Advantages**:
- More intuitive and realistic approach
- Reduces common backtesting pitfalls like look-ahead bias
- Easier implementation of recursive features (take profits, stop losses)
- Simpler transition from backtesting to live trading
- Better for complex, path-dependent strategies

**Disadvantages**:
- Significantly slower computation
- More complex implementation for beginners

## Established Python Backtesting Libraries

### Most Recommended Libraries

1. **Backtesting.py**
   - Fastest event-driven backtesting engine for Python
   - Excellent documentation and tutorials
   - Active development and community support
   - Disadvantages: Slower than vectorized approaches, limited to single-asset backtesting

2. **VectorBT**
   - Incredibly fast computations using vectorized approach
   - Uses Numba (JIT compiler) for speed optimization
   - Disadvantage: Steep learning curve with opinionated syntax

3. **Backtrader**
   - Mature project with extensive features
   - Less active development but stable codebase
   - Robust community resources

## Conclusion

The choice between custom and established backtesting frameworks depends on specific needs, expertise level, and available resources. Building a custom backtester offers valuable learning experiences and flexibility but comes with significant development costs and potential reliability issues.

For most users, especially those new to algorithmic trading, established libraries provide the best balance of functionality, reliability, and community support. Custom development should be considered when specific features are required that aren't available in existing libraries, or for educational purposes to gain deeper understanding of backtesting methodologies.