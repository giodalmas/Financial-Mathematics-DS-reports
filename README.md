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

1) Go in Yahoo finance and select an asset (Meta Platforms, Inc in this case)

2) Go in "Options" and select a Call with maturity around 3 months and Strike AtTheMoney 

3) Consider the Mid price: this market quote is the target price for our model

4) Go in "Historical Data" and download in EXCEL the last 3 months of daily data (take Adj Close that take into account for dividends splits etc)

5) From daily prices compute daily returns

6) Compute sigma_day = the standard deviation of the daily returns 

7) Compute sigma_year = the annual volatility = sigma_day*sqrt(252)

8) Compute the parameters u,d of the binomial model that are related to sigma and T= 3 months

9) Go in global-rates.com and select the Libor rate corresponding to T=3 months 

10) Compute the capitalisation factor using simple compounding = 1+Libor*T and simple discounting = 1/(1+Libor*T)

11) Compute the risk neutral probability weight q and apply the risk neutral pricing formula for the price of a Call -

12) Compare your price with the market quote at point 4)

13) Repeat the procedure for T= 6 months.

## Report 2

1) Choose a dividend paying asset ( Mastercard Incorporated in this case)

2) Fix a maturity T and consider Call a Put with K1 and K2 (K1<<K2)

3) Find the corresponding discount factor for maturity T

4) Find the implicit dividend for maturity T using the put-call parity and using At The Money options (that is new Call and Put with strikes ATM)

5) Repeat the procedure for T=1m, 3m, 6m, 1year and deduce the term structure of implied dividends


## Report 3
1) Set S=100; r=1%; vol=20%, T=1,K=100

2) Write a VBA script that prices a Call with a binomial model where n (number of steps) is an input parameter

3) Compare with the B&S formula

4) Investigate the rate of convergence and compare with the Leisen and Reimer method

## Report 4

(theoretical)

1) Set K=100; r=1%; vol=20%

2) Provide a VBA script that computes the Greeks for a B&S model for S=60,65,70,..,130, 135, 140 and time to maturity tau=0.1,0.2,…,1, 2, 3, 4, 5 years

3) Same as in 1 with a shock of the volatility of +-50%

4) Display in a 3D graph the corresponding surfaces for all greeks

(empirical)

5) Choose in Yahoo an asset which does not pay dividends and on which there is a book of European options (I choose Block Inc. (SQ))

6) Visualize in a 3D picture the implied volatility surface (as a function of the strikes and time to maturities) using the Call prices

7) Check the presence of the implied volatility smile/skew

8) Check the smoothness of the Greeks as time to maturity increases

## Report 5
1) Compute average and variance of an equibalanced portfolio of 2 assets (6 months time window of daily returns)

2) Compute the parametric single and joint  Normal VaR at (95%, 99% , 99,5%) with T=1,..,100 days horizon (estimation of sigma flat)

3) Same as in 2 with sigma estimanted following Riskmetrics EWMA with lambda=0,94

4) Compute the MonteCarlo VaR with N (free input) simulations with T (free input) at the levels (99%,99,5%,95%)

5) Compute the historical VaR (according to the historical value of the returns

6) Compute the VaR with the method of historical simulation (not mandatory)

7) Check in all cases the additivity (non additivity) of the VaR


## Report 6


● Fix some generic parameters for the BS market model 

1) simulate N trajectories (N free input of the script) for the GBM through a VBA code and visualise the paths in a figure for N=100

2) Build up a pricer of vanillas (call/put) through MC by 1 step simulation (that is by simulating N>500 values of the random variable S_T not the entire path)

3) Same as in 2) but using multiple step Euler-scheme based simulation with N>500 and compare the results

4) Same as in 3) but applied to Asian options, i.e. path-dependent options with payoff = (1/T\int_0^T S_tdt - K)^+

