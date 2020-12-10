## 1. What is the P/E Ratio ?

The price-to-earnings ratio (P/E ratio) is the ratio for valuing a company that measures its current share price relative to its per-share earnings (EPS). The price-to-earnings ratio is also sometimes known as the price multiple or the earnings multiple.

P/E ratios are used by investors and analysts to determine the relative value of a company's shares in an apples-to-apples comparison. It can also be used to compare a company against its own historical record or to compare aggregate markets against one another or over time.

A high P/E ratio could mean that a company's stock is over-valued, or else that investors are expecting high growth rates in the future.

Companies that have no earnings or that are losing money do not have a P/E ratio since there is nothing to put in the denominator.

There are two kinds of P/E ratios, Trailing P/E and Forward P/E, are used in practice.

The trailing P/E relies on past performance by dividing the current share price by the total EPS earnings over the past 12 months. It's the most popular P/E metric because it's the most objective – assuming the company reported earnings accurately. The trailing P/E ratio will change as the price of a company’s stock moves, since earnings are only released each quarter while stocks trade day in and day out.

The forward (or leading) P/E uses future earnings guidance rather than trailing figures. Sometimes called "estimated price to earnings," this forward-looking indicator is useful for comparing current earnings to future earnings and helps provide a clearer picture of what earnings will look like – without changes and other accounting adjustments.


## 2. How to calculate P/E Ratio ?

To determine the P/E value, one simply must divide the current stock price by the earnings per share (EPS).

<p float="left">
    <img src="image/formula.png" width="380" height="190" />

The current stock price (P) can be gleaned by plugging a stock’s ticker symbol into any finance website, and this concrete value reflects what investors must currently pay for a stock.

EPS comes in two main varieties. The first is a metric listed in the fundamentals section of most finance sites; with the notation "P/E (TTM)," where “TTM” is a Wall Street acronym for “trailing 12 months.” This number signals the company's performance over the past 12 months. The second type of EPS is found in a company's earnings release, which often provides EPS guidance. This is the company's best-educated guess of what it expects to earn in the future.

## 3. What does P/E Ratio tell you ?

The price-to-earnings ratio or P/E is one of the most widely-used stock analysis tools used by investors and analysts for determining stock valuation. In addition to showing whether a company's stock price is overvalued or undervalued, the P/E can reveal how a stock's valuation compares to its industry group or a benchmark like the S&P 500 Index.

The P/E ratio shows what the market is willing to pay today for a stock based on its past or future earnings. A high P/E could mean that a stock's price is high relative to earnings and possibly overvalued. Conversely, a low P/E might indicate that the current stock price is low relative to earnings. 

A high P/E suggests that investors are expecting higher earnings growth in the future compared to companies with a lower P/E. A low P/E can indicate either that a company may currently be undervalued or that the company is doing exceptionally well relative to its past trends. When a company has no earnings or is posting losses, in both cases P/E will be expressed as “N/A.” Though it is possible to calculate a negative P/E, this is not the common convention.

## 3. Tradingview Pine Script

### · Step One: Initial Setting

    //@version=4
    study("SPY P/E Ratio", overlay = false)

(1) Since we are not using the P/E Ratio as a tool for our stock trading, we start with the study function instead of strategy.

(2) With study function, we have one parameters to set up.

(3) We set overlay to be false to place the P/E Ratio graph on a seperate window

### · Step Two: Parameter Setting

    earnings = security("ESD_FACTSET:AMEX;SPY" +  "EARNINGS", "D", open, lookahead=true) 

    eps=0.0
    for i=0 to 3
        eps := eps + earnings[i]

    pe = close/eps
    
(1) We first locate all S&P 500 earnings through the years

(2) The first line will give us all historical dividends that SPY has paid out

(3) On TradingView, the value of dividends on dates that the stock didn’t pay a dividend will be the last dividend paid.

(4) For example, one stock pays a 1 dollar dividend a week ago and nothing since then.

(5) If I look at stock’s dividend of today, it will also have the value of 1 dollar until the next dividend is paid out.

(6) Because SPY is an ETF that pays out dividends regularly on the last day of each quarter, we can easily calculate the yearly dividend we receive by adding up the dividend value of today, the value of 64 days ago, the value of 127 days ago, and 190 days ago

(7) Why the numbers here are not 0, 90, 180 and 270 days ago? Because TradingView only records prices and dividends on trading days, and there are only 252 trading days each year after deducting holidays and weekends

(8) So we must be careful when choosing the correct dates.

(9) Here, the variable yr-slash-div will give us the annual dividend of SPY on any single date.

(10) Finally, we calculate the dividend yield by dividing the annual dividend by the day’s closing price and times 100 to get a percentage

(11) That’s how we calculate the dividend yield with the most intuitive way


### · Step Three: Plotting

    plot(pe)

(1) With an easy command, we plot out the P/E ratio we just calculated. The curve looks like the following:

