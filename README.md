# American Option Pricing and Greek Calculation Using Binomial Options Pricing Model (BOPM)

## Key Steps in BOPM

1. **Build the Price Tree**:
    - Compute the upward (`u`) and downward (`d`) movements based on volatility and time steps.
    - Construct the asset price tree by iterating through each time step and calculating possible asset prices.

2. **Compute Option Values at Maturity**:
    - For call options: `max(0, asset_price - strike_price)`
    - For put options: `max(0, strike_price - asset_price)`

3. **Calculate Option Prices at Intermediate Nodes**:
    - Use the risk-neutral probabilities to discount the expected future values back to the present value at each node.
    - For American options, compare the early exercise value with the binomial option price and take the maximum.

4. **Compute Greeks**:
    - Perturb the parameters (`S`, `T`, `sigma`, `r`) slightly and calculate the option prices for these perturbed values.
    - Use finite difference methods to compute the Greeks (Delta, Gamma, Theta, Vega, Rho).

## Helper Function to Build the Price Tree

- **Define the `binomial_tree_american_option` function**:
    - Calculate the time step (`dt`), upward movement (`u`), and downward movement (`d`).
    - Compute the risk-neutral probability (`p`).
    - Initialize arrays for asset prices and option values.

- **Build the Asset Price Tree**:
    - Iterate through each node to calculate the possible asset prices at maturity.

- **Calculate Option Values at Maturity**:
    - For call options: `max(0, asset_price - strike_price)`
    - For put options: `max(0, strike_price - asset_price)`

- **Step Back Through the Tree**:
    - Use the risk-neutral valuation to discount back the option values.
    - For American options, account for the possibility of early exercise by taking the maximum of the intrinsic value and the discounted expected value.

## Function to Calculate Greeks

- **Define the `calculate_greeks` function**:
    - Perturb each parameter slightly (`delta_S`, `delta_t`, `delta_sigma`, `delta_r`).
    - Compute the option price for each perturbed parameter using the `binomial_tree_american_option` function.

- **Compute the Greeks**:
    - **Delta**: Rate of change of the option price with respect to the underlying asset price.
    - **Gamma**: Rate of change of Delta with respect to the underlying asset price.
    - **Theta**: Rate of change of the option price with respect to time.
    - **Vega**: Rate of change of the option price with respect to volatility.
    - **Rho**: Rate of change of the option price with respect to the risk-free interest rate.

- **Return the Greeks**:
    - Return a dictionary containing the calculated values for Delta, Gamma, Theta, Vega, and Rho.
