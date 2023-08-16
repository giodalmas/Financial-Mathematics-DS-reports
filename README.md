# Financial-Mathematics-DS-reports
Reports for the course "Financial Mathematics for Data Science" realized using Excel VBA and data from Yahoo Finance.
The purpose of these reports is to learn the basic tools and methodologies for solving financial problems.

The main topics of each Report are:
 
 Report 1: Provide the price of a Call by using the (static) binomial model and compare it with the market quotes.
 
 Report 2: Learn how to use the Put-Call Parity and Box-Spread equations.
 
 Report 3: Compare the convergence of the Binomial Model and the Leisen-Reimer method.
 
 Report 4: Write a VBA code to compute Greeks.
 
 Report 5: Estimate the Value at Risk of an equibalanced Portfolio.
 
 Report 6: Evaluate the price of an option using several alternatives of the Monte Carlo simulation.
 
## Report 1

● Go in Yahoo finance and select an asset (Meta Platforms, Inc in this case)

● Go in "Options" and select a Call with maturity around 3 months and Strike AtTheMoney 

● Consider the Mid price: this market quote is the target price for our model

● Go in "Historical Data" and download in EXCEL the last 3 months of daily data (take Adj Close that take into account for dividends splits etc)

● From daily prices compute daily returns

● Compute sigma_day = the standard deviation of the daily returns 

● Compute sigma_year = the annual volatility = sigma_day*sqrt(252)

● Compute the parameters u,d of the binomial model that are related to sigma and T= 3 months

● Go in global-rates.com and select the Libor rate corresponding to T=3 months 

● Compute the capitalisation factor using simple compounding = 1+Libor*T and simple discounting = 1/(1+Libor*T)

● Compute the risk neutral probability weight q and apply the risk neutral pricing formula for the price of a Call -

● Compare your price with the market quote at point 4)

● Repeat the procedure for T= 6 months.

## Report 2

● Choose a dividend paying asset ( Mastercard Incorporated in this case)

● Fix a maturity T and consider Call a Put with K1 and K2 (K1<<K2)

● Find the corresponding discount factor for maturity T

● Find the implicit dividend for maturity T using the put-call parity and using At The Money options (that is new Call and Put with strikes ATM)

● Repeat the procedure for T=1m, 3m, 6m, 1year and deduce the term structure of implied dividends


## Report 3
● Set S=100; r=1%; vol=20%, T=1,K=100

● Write a VBA script that prices a Call with a binomial model where n (number of steps) is an input parameter

● Compare with the B&S formula

● Investigate the rate of convergence and compare with the Leisen and Reimer method

## Report 4

(theoretical)

● Set K=100; r=1%; vol=20%

● Provide a VBA script that computes the Greeks for a B&S model for S=60,65,70,..,130, 135, 140 and time to maturity tau=0.1,0.2,…,1, 2, 3, 4, 5 years

● Same as in 1 with a shock of the volatility of +-50%

● Display in a 3D graph the corresponding surfaces for all greeks

(empirical)

● Choose in Yahoo an asset which does not pay dividends and on which there is a book of European options (I choose Block Inc. (SQ))

● Visualize in a 3D picture the implied volatility surface (as a function of the strikes and time to maturities) using the Call prices

● Check the presence of the implied volatility smile/skew

● Check the smoothness of the Greeks as time to maturity increases

## Report 5
● Compute average and variance of an equibalanced portfolio of 2 assets (6 months time window of daily returns)

● Compute the parametric single and joint  Normal VaR at (95%, 99% , 99,5%) with T=1,..,100 days horizon (estimation of sigma flat)

● Same as in 2 with sigma estimanted following Riskmetrics EWMA with lambda=0,94

● Compute the MonteCarlo VaR with N (free input) simulations with T (free input) at the levels (99%,99,5%,95%)

● Compute the historical VaR (according to the historical value of the returns

● Compute the VaR with the method of historical simulation (not mandatory)

● Check in all cases the additivity (non additivity) of the VaR


## Report 6


● Fix some generic parameters for the BS market model 

1) simulate N trajectories (N free input of the script) for the GBM through a VBA code and visualise the paths in a figure for N=100

2) Build up a pricer of vanillas (call/put) through MC by 1 step simulation (that is by simulating N>500 values of the random variable S_T not the entire path)

3) Same as in 2) but using multiple step Euler-scheme based simulation with N>500 and compare the results

4) Same as in 3) but applied to Asian options, i.e. path-dependent options with payoff = (1/T\int_0^T S_tdt - K)^+

