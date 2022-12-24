# Capped Accumulated Return Call Option with Two Way Return and Splitting Payoff

We developed and implemented a pricing model for capped-accumulated-return-call (CARC) with two features: two-way-return and splitting payoff.

Let   be a price process of a given underlying asset,   be a set of reset dates and   be a payoff settlement date.  The two-way-return CARC with the underlying S is a European type derivative security whose matured payoff at the settlement date is given by

	 	(1)

where   is the global floor (strike) of the return rate, N is the notional principal, and   is capped-accumulated-return and defined as

	 	(2)

where   is the two-way-capped return-rate for each period explained as follows.  Define the actual period return-rate as

	 	(3)

If the price of the underlying asset goes down,   would be the absolute value of the return up to a local floor  ; otherwise,   would be asset return up to a local cap  .  Mathematically,   can be expressed as

	 	(4)

Let t be the current value date, then the current value of this CARC can be written as

	 	(5)

where   is the discounting factor at the value date.  The above formula is in a world that is forward risk-neutral with respect to a specific currency  .  

As a result, the notional principal N is measured in the currency  , and the discounting factor should be calculated by a   zero curve (ref. https://finpricing.com/lib/IrInflationCurve.html) given at the value date.  If the underlying asset is measured in another currency  , assuming the option is a non-Quanto type transaction, the governing price dynamics of the underlying asset in the risk-neutral world of   should be written as

	 	(6)

where   is the short rate of  , q is the dividend yield of the asset,   is the volatility of the asset price, and   is the Wiener process.  All these parameters are assumed deterministic.

For the CARC model, we have made three different payoffs available, denoted P_1, P_2 and P_3.  Equation (1) is the definition for P_3.  P_1 and P_2 are respectively expressed as

				 								(7)
				 								(8)

An enhanced Quasi-Monte Carlo method is employed to evaluation this feature of CARC.  In this method, Sobol sequence in conjunction with Brownian Bridge path generation approach is applied.  In this transaction,   is  ,   is 0.12,   is 0.147, and the notional principal is USD 100.  Only the term structure of at-the-money volatility is used in calculation, i.e., volatility skew is NOT applied.

