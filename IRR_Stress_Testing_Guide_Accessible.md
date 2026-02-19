# Mastering Interest Rate Risk (IRR) and Stress Testing in Banking

> **Disclaimer:** This guide is for educational and risk management purposes only. It does not constitute financial advice, regulatory guidance, or investment recommendations. Banks should consult with qualified risk management professionals and regulatory advisors for institution-specific applications.

---

## 1. Fundamentals of Interest Rate Risk (IRR)

### 1.1 What is Interest Rate Risk in the Banking Book?

**Interest Rate Risk in the Banking Book (IRRBB)** is the risk that changes in interest rates will hurt a bank's financial health. This risk affects the bank's core banking activities: taking deposits from customers, making loans, and holding investment securities.

Think of it this way: Banks make money by charging higher interest on loans than they pay on deposits. When interest rates change, this profit margin can shrink or disappear.

When interest rates change, they affect banks through two main channels:

| Channel | What It Means | Impact |
|---------|---------------|--------|
| **Earnings Perspective** | How much profit the bank makes each year | Affects **Net Interest Income (NII)** — the difference between interest earned on assets (loans, securities) and interest paid on liabilities (deposits, borrowings) |
| **Economic Value Perspective** | What the bank is truly worth today | Affects **Economic Value of Equity (EVE)** — the present value (what future money is worth today) of all future cash flows from assets minus liabilities |

> **In Simple Terms:** Imagine you own a rental property. The *earnings perspective* is your monthly rental income minus your mortgage payment. The *economic value perspective* is what you could sell the property for today. Interest rate changes affect both your monthly cash flow AND your property's sale value.

### 1.2 The Four Components of IRR

Understanding IRR requires breaking it down into four distinct but connected risk types:

#### **1. Repricing Risk**

**Definition:** The risk that comes from timing differences in when assets and liabilities adjust to new interest rates.

**How It Works:**
- Some bank products have fixed rates (stay the same for years)
- Some have floating rates (change regularly based on market conditions)
- When rates change, assets and liabilities may adjust at different times

**Simple Example:** A bank makes a 5-year fixed-rate loan (the rate stays the same for 5 years) but funds it with 1-year certificates of deposit (CDs that renew every year). 

- **Year 1:** Bank earns 5% on the loan, pays 2% on the CD = 3% profit margin
- **Year 2:** Interest rates rise. The CD renews at 4%, but the loan still earns 5% = only 1% profit margin
- **Result:** The bank's profit got squeezed because the liability repriced faster than the asset

> **In Simple Terms:** This is like a homeowner with a fixed-rate mortgage but a savings account that earns whatever the current rate is. When rates rise, their mortgage payment stays the same, but their savings earn more. Banks face the opposite problem when their costs rise faster than their income.

#### **2. Yield Curve Risk**

**Definition:** The risk that comes from changes in the relationship between short-term and long-term interest rates.

**What is the Yield Curve?** It's a line that shows interest rates across different time periods. Normally, longer-term rates are higher than short-term rates (because lenders want more compensation for locking up money longer).

**How the Curve Can Change:**

| Type of Change | What Happens | Visual |
|----------------|--------------|--------|
| **Parallel Shift** | All rates move up or down by the same amount | The whole curve moves up or down together |
| **Steepening** | Long-term rates rise faster than short-term rates (or short-term fall faster) | The curve gets steeper |
| **Flattening** | Short-term rates rise faster than long-term rates (or long-term fall faster) | The curve gets flatter |
| **Inversion** | Short-term rates become higher than long-term rates | The curve flips upside down |

**Simple Example:** A bank borrows short-term (1 year) and lends long-term (10 years). This works well when long-term rates are much higher than short-term rates (steep curve). But if the curve flattens or inverts, the bank's profit margin disappears.

> **In Simple Terms:** Think of the yield curve like a hill. Normally it slopes upward (long-term rates higher). Banks often borrow at the bottom of the hill (short-term) and lend at the top (long-term). When the hill flattens or flips, this business model breaks.

#### **3. Basis Risk**

**Definition:** The risk that comes from assets and liabilities being tied to different reference rates that don't move perfectly together.

**What Are Reference Rates?** These are benchmark interest rates that banks use to set their own rates. Common ones include:
- **Prime Rate** (used for many business and consumer loans)
- **SOFR** (Secured Overnight Financing Rate — used for many financial transactions)
- **Treasury Rates** (used for some loans and securities)

**How It Works:** Even when the Federal Reserve changes rates, different reference rates may not move by the same amount. The gap (spread) between them can widen or narrow.

**Simple Example:** A bank's loans are tied to Prime Rate while its deposits are tied to SOFR. 
- Both rates might generally move in the same direction
- But if Prime Rate rises 1% while SOFR rises 1.5%, the bank's profit margin shrinks by 0.5%
- This happens even though "rates went up" across the board

> **In Simple Terms:** Imagine you get paid in US dollars but pay your bills in euros. Even if both currencies are "strong," if the euro gets stronger relative to the dollar, you lose purchasing power. Basis risk is similar — two rates that should move together don't.

#### **4. Optionality Risk**

**Definition:** The risk that comes from features in bank products that let customers change their behavior when interest rates change.

**Common Examples:**

| Product | What the Customer Can Do | Risk When Rates Fall | Risk When Rates Rise |
|---------|-------------------------|---------------------|---------------------|
| **Mortgages** | Pay off early and refinance | Borrowers refinance at lower rates; bank loses high-yielding loans | Borrowers stay put; bank is fine |
| **Callable Bonds** | Issuer can pay back early | Bonds get called away; bank must reinvest at lower rates | Bonds stay outstanding; bank is fine |
| **Deposits** | Withdraw money anytime | Depositors stay; bank is fine | Depositors withdraw to chase higher rates elsewhere |
| **Lines of Credit** | Borrow more when needed | Borrowers use less; bank earns less interest | Borrowers draw more; bank may face liquidity pressure |

**Simple Example:** When interest rates fall sharply, homeowners refinance their mortgages at lower rates. The bank loses its high-yielding loans and has to lend the money out again at the new, lower rates. This is called **prepayment risk**.

> **In Simple Terms:** This is like a tenant with a lease-break option. When rents go down, they break the lease and move to a cheaper place. You (the landlord) lose your high-paying tenant and have to rent at the new, lower market rate. Bank customers do the same thing with loans and deposits.

### 1.3 Why IRR Management is Critical

#### **Solvency Impact (Whether the Bank Can Survive)**

Interest rate risk can directly threaten a bank's ability to stay in business:

- **Unrealized losses on securities:** When interest rates rise, the market value of existing bonds and securities falls. These losses are "unrealized" (not yet booked) but are still economically real.
- **Capital ratio deterioration:** As the value of assets falls, the bank's capital ratios decline, potentially falling below regulatory minimums.
- **SVB Lesson:** Silicon Valley Bank held $91.3 billion in Held-to-Maturity securities with over $15 billion in unrealized losses when rates rose in 2022-2023. This was nearly equal to its entire equity base. While these losses weren't immediately visible on accounting statements, they were economically real and contributed to the bank's collapse when depositors ran.

#### **Liquidity Impact (Whether the Bank Has Cash)**

IRR and liquidity risk are deeply connected:

- **Deposit flight:** When rates rise, depositors may move their money to banks or investments offering higher yields
- **Asset liquidation pressure:** If depositors withdraw money, the bank may need to sell securities at a loss to raise cash
- **Funding cost spiral:** As the bank looks riskier, it must pay more to attract deposits, which further squeezes profits

#### **Earnings Volatility (Unpredictable Profits)**

Poorly managed IRR creates unpredictable earnings:

- **NII compression:** Mismatched timing can cause sudden profit margin deterioration
- **Provisioning pressure:** Economic stress from rate changes may lead to more loan defaults
- **Investor confidence:** Unpredictable earnings reduce the bank's stock price and make it more expensive to raise capital

---

### Key Takeaways: Fundamentals of IRR

- **IRRBB** affects both earnings (annual profits) and economic value (what the bank is worth)
- **Four components** must be managed: Repricing Risk, Yield Curve Risk, Basis Risk, and Optionality Risk
- **Solvency and liquidity** are both at risk from unmanaged IRR
- **SVB collapse (2023)** showed that unrealized losses are economically real, not just accounting entries
- **Duration mismatch** between assets and liabilities is the primary driver of IRR exposure

---

## 2. The Economic Value of Equity (EVE) Approach

### 2.1 Definition and Conceptual Framework

**Economic Value of Equity (EVE)** is what a bank's assets are worth today minus what its liabilities are worth today, considering all future cash flows.

**The Basic Formula:**
```
EVE = Present Value of Assets - Present Value of Liabilities
```

**What is Present Value?** Present value answers the question: "What is a future payment worth today?" 

The answer depends on interest rates. If you could earn 5% per year investing money, then $100 received one year from now is worth only about $95 today (because $95 invested at 5% grows to $100 in one year).

**How the Calculation Works (Without Complex Math):**

Instead of using sigma notation (Σ), think of it this way:

1. List all the cash flows you expect to receive from assets (loan payments, bond coupons, principal repayments)
2. List all the cash flows you expect to pay for liabilities (deposit withdrawals, debt payments)
3. For each future cash flow, calculate what it's worth today using the current interest rate
4. Add up all the present values of asset cash flows
5. Add up all the present values of liability cash flows
6. Subtract total liability value from total asset value = EVE

**In Simple Terms:** EVE is like calculating your net worth, but instead of using today's account balances, you estimate all the money you'll ever receive and pay in the future, then figure out what all that future money is worth in today's dollars.

### 2.2 How EVE Measures Long-Term Economic Value Impact

EVE captures the **full economic impact** of interest rate changes across the entire life of all banking positions.

#### **The Discounting Mechanism (How Present Value Works)**

When interest rates change, the value of future money changes:

- **Rates Rise →** Future money is worth less today → Present values fall
- **Rates Fall →** Future money is worth more today → Present values rise

**Why?** When rates are higher, you can earn more by investing money today. So a future payment is less valuable (you need less money today to grow into that future amount).

**Critical Insight:** Assets and liabilities typically have different **durations** (sensitivities to interest rate changes). The **duration gap** determines whether EVE increases or decreases when rates move.

> **In Simple Terms:** Duration is like a measure of how much something's price will change when interest rates change. A 10-year bond has higher duration than a 1-year bond — its price will swing more when rates move. If your assets have higher duration than your liabilities, rising rates will hurt you more than they help you.

#### **Example Calculation (Simplified)**

Consider a simplified bank position:

| Position | Future Payment | When Due | Current Interest Rate |
|----------|---------------|----------|----------------------|
| Asset (Loan) | $1,000,000 | 5 years | 4% |
| Liability (CD) | $1,000,000 | 2 years | 3% |

**Current EVE Calculation:**

To find present value, we divide the future amount by (1 + rate) raised to the number of years:

- PV of Asset = $1,000,000 ÷ (1.04)^5 = $1,000,000 ÷ 1.217 = **$821,927**
- PV of Liability = $1,000,000 ÷ (1.03)^2 = $1,000,000 ÷ 1.061 = **$942,596**
- EVE = $821,927 - $942,596 = **-$120,669** (negative equity in this simplified example)

**After Interest Rates Rise by 2% (200 basis points):**

*Note: "Basis points" (bps) are hundredths of a percent. 100 bps = 1%, so 200 bps = 2%*

- PV of Asset = $1,000,000 ÷ (1.06)^5 = $1,000,000 ÷ 1.338 = **$747,258** (decline of $74,669)
- PV of Liability = $1,000,000 ÷ (1.05)^2 = $1,000,000 ÷ 1.103 = **$907,029** (decline of $35,567)
- New EVE = $747,258 - $907,029 = **-$159,771**

**EVE Decline:** $39,102

**Why Did EVE Fall?** The asset lost more value than the liability because it has a longer time until maturity (5 years vs. 2 years). Longer-term items are more sensitive to interest rate changes.

> **In Simple Terms:** Think of two rubber bands — one long, one short. When you pull them (interest rates change), the long one stretches more. The 5-year asset is the long rubber band; it lost more value than the 2-year liability when rates rose.

### 2.3 EVE vs. Short-Term Earnings: Pros and Cons

| Aspect | EVE Approach | Short-Term Earnings (NII) |
|--------|--------------|--------------------------|
| **Time Horizon** | Entire life of all positions (10-30+ years) | Next 1-2 years |
| **What It Measures** | Economic value / whether the bank is solvent | Accounting earnings / profitability |
| **Sensitivity** | Captures long-term risk | Captures near-term changes |
| **Rate Shock Impact** | Shows full economic impact | Shows budget/forecast impact |
| **Capital Planning** | Direct measure of capital at risk | Indirect through retained earnings |
| **Limitations** | Requires long-term assumptions; sensitive to behavioral models | Misses long-term value erosion; may show profits increasing when bank value is declining |

#### **Critical Tension: EVE vs. NII Can Move in Opposite Directions**

A bank can experience **rising profits but declining value** at the same time:

- **Scenario:** Rising interest rate environment
- **NII Impact:** Positive — floating-rate assets reprice up faster than fixed-rate liabilities, so annual profits increase
- **EVE Impact:** Negative — long-duration fixed-rate assets lose significant present value, so the bank's economic value declines

**Post-2023 Lesson:** Many banks (including Silicon Valley Bank) reported strong profits in 2022 while their economic value was deteriorating rapidly due to unrealized securities losses. Relying solely on profit metrics created a false sense of security.

> **In Simple Terms:** This is like a company that shows good quarterly profits but is slowly selling off its factory to pay bills. The short-term numbers look fine, but the long-term health is deteriorating. EVE catches what NII misses.

### 2.4 EVE Stress Testing with Rate Shocks

#### **Standard Regulatory Shocks**

Per Basel Committee IRRBB standards, banks must calculate EVE under six standardized interest rate shock scenarios:

| Scenario | What Happens | Typical Size (US Dollars) |
|----------|--------------|--------------------------|
| **Parallel Up** | All rates increase by the same amount | +200 basis points (+2%) |
| **Parallel Down** | All rates decrease by the same amount | -200 basis points (-2%, with 0% floor) |
| **Steepener** | Short-term rates fall, long-term rates rise | Short: -100 bps / Long: +200 bps |
| **Flattener** | Short-term rates rise, long-term rates fall | Short: +100 bps / Long: -100 bps |
| **Short Rate Up** | Only short-term rates increase | +200 bps (for maturities up to 1 year) |
| **Short Rate Down** | Only short-term rates decrease | -200 bps (for maturities up to 1 year, with floor) |

> **In Simple Terms:** These are like standardized "what if" tests. Regulators want all banks to answer the same six questions: "What if all rates go up 2%? What if they all go down 2%?" etc. This makes banks comparable and ensures everyone is testing for similar risks.

#### **"EVE at Risk" Concept**

**EVE at Risk** measures the maximum decline in economic value under adverse scenarios:

```
EVE at Risk = Baseline EVE - EVE after shock
```

Often expressed as a percentage of Tier 1 Capital (the bank's core equity):

```
EVE Decline % of Tier 1 Capital = (EVE at Risk ÷ Tier 1 Capital) × 100%
```

**Regulatory Outlier Test:** Under Basel III, if EVE declines by more than **15% of Tier 1 Capital** under any standardized shock, the bank may be flagged as an "outlier" requiring enhanced supervisory scrutiny and potentially additional capital.

> **In Simple Terms:** Think of Tier 1 Capital as the bank's safety cushion. Regulators say: "If a standard stress test eats up more than 15% of your cushion, you're taking too much risk and we're going to watch you more closely."

---

### Key Takeaways: EVE Approach

- **EVE = Present Value of Assets - Present Value of Liabilities** — measures full economic value impact
- **Long-term perspective** captures risks that short-term earnings miss
- **Six standardized shocks** required under Basel III IRRBB framework
- **EVE and NII can move in opposite directions** — both must be monitored
- **15% of Tier 1 Capital** is the regulatory threshold for concern
- **SVB Lesson:** Strong profits masked severe economic value deterioration from unrealized securities losses

---

## 3. Alternative IRR Measurement & Stress Testing Methodologies

While EVE provides the economic value perspective, comprehensive IRR management requires multiple complementary measurement approaches.

### 3.1 Net Interest Income (NII) Simulation

#### **Definition and Purpose**

**NII Simulation** is a forward-looking approach that projects changes in net interest income over a specified time period (typically 12-24 months) under various interest rate scenarios.

**The Basic Formula:**
```
NII = Interest Income - Interest Expense
```

Under a stress scenario, banks calculate what NII would be if rates moved according to the scenario.

#### **Key Components of NII Simulation Models**

| Component | What It Means |
|-----------|---------------|
| **Balance Sheet Growth** | Assumptions about new loans, new deposits, and securities purchases |
| **Pricing Relationships** | How asset and liability rates respond to market rate changes (called "betas" — see below) |
| **Repricing Schedules** | When each position resets to new rates |
| **Prepayment Assumptions** | Expected early payoffs on loans and securities |
| **Behavioral Assumptions** | How non-maturity deposits (checking, savings) reprice |
| **Option Features** | Impact of rate caps, floors, and callable securities |

> **What is a "Beta"?** In banking, beta measures how much a bank's rate changes when market rates change. A deposit beta of 30% means that when market rates rise 1%, the bank's deposit rate rises only 0.30%.

#### **Contrast with EVE**

| Dimension | NII Simulation | EVE |
|-----------|----------------|-----|
| **Time Horizon** | 1-2 years | Full life of all positions (10-30+ years) |
| **Accounting Basis** | Accrual accounting (like financial statements) | Present value / economic |
| **New Business** | Includes projected new volumes | Typically assumes no new business |
| **Sensitivity** | Near-term repricing mismatch | Long-duration exposure |
| **Use Case** | Budget planning, earnings guidance | Capital adequacy, strategic planning |
| **Regulatory Focus** | Secondary | Primary (Basel III) |

#### **Earnings at Risk (EAR)**

**EAR** expresses NII simulation results as a risk metric:

```
EAR = Baseline NII - NII under shock
```

Often expressed as percentage of baseline:

```
EAR % = [(Baseline NII - NII under shock) ÷ Baseline NII] × 100%
```

**Example:** If baseline NII is $100 million and NII under a +2% shock is $85 million:
- EAR = $15 million
- EAR% = 15%

> **In Simple Terms:** EAR answers: "How much of my expected profit could I lose under this stress scenario?" A 15% EAR means you could lose 15% of your expected annual profit.

### 3.2 Duration Gap Analysis

#### **Modified Duration**

**Modified Duration** measures how much a security's price will change (in percentage terms) for a 1% change in interest rates.

**Simple Explanation:** Instead of using complex formulas, think of duration as a multiplier:

- A bond with duration of 5.0 will change approximately 5% in price for every 1% change in interest rates
- If rates rise 1%, the bond's price falls approximately 5%
- If rates fall 1%, the bond's price rises approximately 5%

**Price Change Formula (Simplified):**
```
Percentage Price Change ≈ -Duration × Change in Interest Rate
```

The negative sign means prices move opposite to rates (rates up → prices down).

**Example:** A bond with duration of 5.0 will decline approximately 5% in price if rates rise 1% (100 basis points).

> **In Simple Terms:** Duration is like a speedometer for interest rate risk. A duration of 5 means your investment's price moves 5 times as much as the interest rate move. It's a quick way to gauge sensitivity.

#### **Duration Gap Calculation**

**Duration Gap** measures the mismatch between asset and liability durations, adjusted for their relative sizes:

```
Duration Gap = Duration of Assets - (Liabilities ÷ Assets × Duration of Liabilities)
```

**Where:**
| Variable | Definition |
|----------|------------|
| Duration of Assets | Weighted average duration of all assets |
| Duration of Liabilities | Weighted average duration of all liabilities |
| Liabilities | Total liabilities |
| Assets | Total assets |

#### **EVE Sensitivity via Duration Gap**

```
Change in EVE ≈ -Duration Gap × Total Assets × Change in Interest Rate
```

**Interpretation:**
- **Positive Duration Gap:** Assets have longer duration than liabilities → EVE falls when rates rise
- **Negative Duration Gap:** Liabilities have longer duration than assets → EVE rises when rates rise
- **Zero Duration Gap:** Theoretically protected against parallel rate shifts (but other risks remain)

> **In Simple Terms:** Duration gap tells you which side of the balance sheet is more sensitive to rate changes. Positive gap = assets are more sensitive = rising rates hurt. Negative gap = liabilities are more sensitive = rising rates help.

#### **Limitations of Duration Gap**

| Limitation | What It Means |
|------------|---------------|
| **Parallel Shift Assumption** | Assumes all rates move equally; doesn't capture yield curve risk |
| **Linear Approximation** | Duration is accurate only for small rate changes; for large moves, the relationship curves |
| **Static Measure** | Doesn't account for behavioral changes or new business |
| **Optionality Ignored** | Embedded options (like prepayment) change effective duration as rates move |

### 3.3 Value at Risk (VaR) Approach

#### **Statistical Framework**

**VaR** applies statistical methods to estimate the maximum potential loss in EVE or NII over a specified time period at a given confidence level.

**Simple Explanation:** VaR answers: "What's the worst loss I might expect, with X% confidence, over Y time period?"

For example, a 95% VaR of $10 million over 1 day means: "We're 95% confident we won't lose more than $10 million in one day." Or put another way: "On about 1 out of 20 days, we might lose more than $10 million."

**The VaR Formula (Conceptual):**
```
VaR = Portfolio Value × Volatility × Confidence Factor × Square Root of Time
```

**Where:**
| Variable | Definition |
|----------|------------|
| Confidence Level | How sure you want to be (e.g., 95%, 99%) |
| Time Horizon | How long of a period (days, months) |
| Volatility | How much the portfolio value typically fluctuates |
| Confidence Factor | A number based on confidence level (1.65 for 95%, 2.33 for 99%) |

> **In Simple Terms:** VaR is like a weather forecast for losses. "95% VaR of $10M" is like saying "95% chance of no more than $10M in losses." But just as weather forecasts can be wrong, VaR can underestimate extreme events.

#### **VaR Methodologies for IRR**

| Method | How It Works | Advantages | Disadvantages |
|--------|--------------|------------|---------------|
| **Historical Simulation** | Revalues portfolio using actual historical rate changes | No assumptions about distribution; captures real-world patterns | Requires long history; may miss unprecedented events |
| **Variance-Covariance** | Uses statistical parameters (average, volatility, correlation) | Computationally efficient; transparent | Assumes normal distribution; underestimates extreme events |
| **Monte Carlo Simulation** | Generates thousands of random rate paths | Most flexible; captures complex dynamics | Computationally intensive; model risk |

#### **Limitations for IRR**

- **Historical data may not predict future:** The 2022-2023 rate hiking cycle was unprecedented in speed
- **Correlation breakdown:** Relationships between rates at different maturities can change dramatically
- **Tail risk underestimation:** VaR may not capture extreme but plausible scenarios (the "black swan" problem)

> **In Simple Terms:** VaR is like driving while looking only in the rearview mirror. It tells you what happened before, but the road ahead might be different. The 2022-2023 rate hikes were like a sudden curve that historical data didn't predict.

### 3.4 Liquidity-Adjusted IRR

#### **The IRR-Liquidity Connection**

The 2023 banking crisis demonstrated that IRR and liquidity risk are inseparable:

1. **Rising rates** → Unrealized losses on securities
2. **Unrealized losses** → Reduced collateral value for borrowing
3. **Deposit flight** → Need to liquidate assets at losses
4. **Asset sales** → Realize losses, erode capital
5. **Capital erosion** → Further deposit flight (vicious cycle)

> **In Simple Terms:** This is like a homeowner with a mortgage. When house values fall (like securities losing value), the homeowner has less equity to borrow against. If they lose their job (like depositors withdrawing), they might have to sell the house at a loss, which wipes out their remaining equity.

#### **Liquidity-Adjusted IRR Framework**

This approach integrates funding stress scenarios with IRR measurement:

| Scenario Component | What It Means |
|--------------------|---------------|
| **Rate Shock** | Standard IRR scenarios (parallel, steepener, etc.) |
| **Deposit Runoff** | Percentage of deposits withdrawn under stress |
| **Asset Haircuts** | Reduced collateral value for secured funding |
| **Funding Spread Widening** | Increased cost of wholesale funding |
| **Fire Sale Discounts** | Losses from forced asset liquidation |

#### **Integrated Stress Test Output**

```
Total Capital Impact = IRR Impact (EVE) + Liquidity Impact (Fire Sales) + Funding Cost Impact
```

**Post-SVB Best Practice:** Banks should model scenarios where IRR triggers liquidity stress, which then amplifies IRR losses through forced asset sales.

> **In Simple Terms:** Don't just test interest rate risk in isolation. Test what happens when rate losses cause depositors to run, which forces you to sell assets at fire-sale prices, which causes more losses. The combination is worse than the sum of the parts.

---

### Key Takeaways: Alternative Methodologies

- **NII Simulation** provides earnings perspective (1-2 year horizon); complements EVE
- **Duration Gap** offers quick sensitivity measure but has limitations (parallel shift assumption, ignores optionality)
- **VaR** adds statistical rigor but may underestimate tail risk (extreme events)
- **Liquidity-Adjusted IRR** is critical post-SVB — IRR and liquidity risk are interconnected
- **No single metric is sufficient** — use multiple approaches for comprehensive view

---

## 4. Designing Stress Testing Scenarios

Effective stress testing requires diverse scenarios that capture regulatory requirements, historical precedents, and institution-specific vulnerabilities.

### 4.1 Regulatory Shocks: The Six Standardized Scenarios

Per Basel Committee IRRBB standards and OCC/Fed guidance, banks must evaluate IRR under six standardized interest rate shock scenarios:

#### **Scenario Specifications (US Dollars)**

| # | Scenario | Short End (1 Year) | Long End (25 Years) | How It Works |
|---|----------|-------------------|---------------------|--------------|
| 1 | **Parallel Up** | +200 bps (+2%) | +200 bps (+2%) | All rates rise by 2% |
| 2 | **Parallel Down** | -200 bps (-2%) | -200 bps (-2%) | All rates fall by 2% (but not below 0%) |
| 3 | **Steepener** | -100 bps (-1%) | +200 bps (+2%) | Short rates fall, long rates rise |
| 4 | **Flattener** | +100 bps (+1%) | -100 bps (-1%) | Short rates rise, long rates fall |
| 5 | **Short Rate Up** | +200 bps (+2%) | 0 bps (no change) | Only short-term rates rise |
| 6 | **Short Rate Down** | -200 bps (-2%) | 0 bps (no change) | Only short-term rates fall (with 0% floor) |

#### **What Each Scenario Tests**

| Scenario | What Risk It Captures |
|----------|----------------------|
| **Parallel Up** | Traditional rising rate environment; tests positive duration gap |
| **Parallel Down** | Falling rate environment; tests negative duration gap; floor constraint |
| **Steepener** | Economic recovery scenario; long rates rise on growth expectations |
| **Flattener** | Monetary tightening or recession fears; short rates rise faster |
| **Short Rate Up** | Fed tightening cycle; tests deposit repricing and short-term funding |
| **Short Rate Down** | Fed easing cycle; tests reinvestment risk on short-term assets |

#### **Currency Variations**

Shock magnitudes vary by currency based on historical volatility:

| Currency Zone | Parallel Shock |
|---------------|----------------|
| US Dollar, Euro, British Pound, Japanese Yen, Swiss Franc | ±200 bps (±2%) |
| Emerging markets | ±400 bps (±4%) or higher |
| Low-rate environments | Adjusted for effective lower bound (can't go below 0%) |

> **In Simple Terms:** Different countries get different stress test severity based on how volatile their rates have been historically. Emerging markets get tougher tests because their rates swing more.

### 4.2 Historical Scenarios

#### **2008 Global Financial Crisis (GFC)**

**What Happened:**
- Flight to quality → Treasury yields collapsed
- 10-Year Treasury: 4.0% (June 2008) → 2.2% (December 2008)
- Fed Funds: 5.25% → 0-0.25% (near zero)
- Credit spreads widened dramatically (difference between safe and risky borrowing rates)

**Relevance for IRR:**
- Tests **parallel down** scenario with extreme magnitude
- Captures **basis risk** as spreads between indices diverged
- **Optionality risk:** Massive mortgage refinancing wave

#### **2022-2023 Rapid Rate Hike Cycle (SVB Collapse)**

**What Happened:**
- Fed Funds: 0.25% (March 2022) → 5.25% (July 2023)
- Fastest hiking cycle in 40 years
- Yield curve inversion (2-year rate higher than 10-year for 18+ months)
- 2-Year Treasury: 0.7% → 5.0%
- 10-Year Treasury: 1.5% → 4.2%

**Relevance for IRR:**
- Tests **parallel up** and **short rate up** scenarios
- Captures **yield curve risk** (inversion, then steepening)
- **Duration risk:** Long-duration securities lost 20-30% of value
- **Liquidity interaction:** Unrealized losses triggered deposit run

**SVB-Specific Lessons:**

| Factor | SVB Reality | Lesson |
|--------|-------------|--------|
| **Securities Duration** | 56% of securities had maturities over 15 years | Limit long-duration holdings |
| **HTM Accounting** | $15B unrealized loss not visible in capital | HTM losses are economically real |
| **Deposit Concentration** | 97% of deposits were uninsured (over $250K) | Diversify funding base |
| **Hedging** | Minimal interest rate hedging | Actively hedge duration risk |

> **In Simple Terms:** SVB was like someone who borrowed short-term to buy long-term bonds, didn't hedge, and had all their funding from a few large depositors who could leave anytime. When rates rose, everything went wrong at once.

### 4.3 Hypothetical Scenarios

Hypothetical scenarios should be tailored to institution-specific risk profiles:

#### **Bank-Specific Worst-Case Models**

| Scenario Type | Description | When to Use |
|---------------|-------------|-------------|
| **Extreme Parallel Up** | +400 bps (+4%) — beyond regulatory standard | Test capital adequacy under severe stress |
| **Prolonged Low Rates** | Rates at 0-1% for 5+ years | Test business model viability |
| **Curve Inversion** | 2-year rate exceeds 10-year rate by 200+ bps | Test profit compression from margin squeeze |
| **Basis Shock** | Prime-SOFR spread widens 150 bps | Test basis risk from index mismatch |
| **Deposit Beta Shock** | Deposit betas jump from 30% to 70% | Test funding cost sensitivity |

#### **Designing Effective Hypothetical Scenarios**

1. **Identify Key Vulnerabilities:** What rate moves would hurt this specific bank most?
2. **Consider Business Model:** Mortgage bank vs. commercial lender vs. consumer bank
3. **Incorporate Behavioral Assumptions:** How would customers actually respond?
4. **Include Management Actions:** What hedging or balance sheet actions would be taken?
5. **Link to Capital Planning:** What capital ratios result from each scenario?

> **In Simple Terms:** Don't just run the regulatory tests. Ask: "What specific scenario would hurt US the most?" Then test that. A mortgage bank should test refinancing waves. A commercial bank should test credit spread widening.

### 4.4 Reverse Stress Testing

#### **Definition and Purpose**

**Reverse Stress Testing** starts with a defined "breaking point" and works backward to identify the interest rate move (or combination of factors) that would cause the bank to fail.

**Breaking Point Definitions:**
- Tier 1 Capital Ratio falls below regulatory minimum (e.g., 6%)
- EVE declines by more than 25% of Tier 1 Capital
- NII turns negative
- Liquidity Coverage Ratio (LCR) falls below 100%

#### **Reverse Stress Test Methodology**

```
Step 1: Define Failure Threshold (What does "breaking" mean?)
        ↓
Step 2: Model Current Position (Where are we now?)
        ↓
Step 3: Iteratively Increase Stress Severity (Try bigger shocks)
        ↓
Step 4: Identify Breaking Point (What shock causes failure?)
        ↓
Step 5: Assess Plausibility of Rate Move (Could this actually happen?)
        ↓
Step 6: Develop Mitigation Plans (How do we prevent this?)
```

#### **Example: Reverse Stress Test for EVE**

| Iteration | Rate Shock | EVE Decline | % of Tier 1 Capital | Status |
|-----------|------------|-------------|---------------------|--------|
| 1 | +200 bps (+2%) | -$50M | 10% | Pass |
| 2 | +300 bps (+3%) | -$85M | 17% | Outlier |
| 3 | +400 bps (+4%) | -$120M | 24% | Approaching Break |
| 4 | +450 bps (+4.5%) | -$145M | 29% | **BREAK** |

**Result:** A +450 bps parallel shock would cause the bank to breach its risk appetite limit (25% of Tier 1 Capital).

**Plausibility Assessment:** Is +450 bps plausible?
- Historical precedent: 1980s Volcker shock (+1000+ bps over 2 years)
- Recent precedent: 2022-2023 (+500 bps over 16 months)
- **Conclusion:** Plausible over multi-year horizon; mitigation required

> **In Simple Terms:** Reverse stress testing is like asking: "How much can my car's suspension take before it breaks?" Instead of testing standard bumps, you keep increasing the bump size until something fails. Then you ask: "Will I ever encounter a bump that big?" If yes, you need to reinforce the suspension.

---

### Key Takeaways: Stress Testing Scenarios

- **Six regulatory shocks** are mandatory minimum under Basel III IRRBB
- **Historical scenarios** (GFC, SVB) provide real-world stress calibration
- **Hypothetical scenarios** should be tailored to institution-specific vulnerabilities
- **Reverse stress testing** identifies breaking points and informs risk limits
- **Post-SVB:** Include liquidity-IRR interaction in all severe scenarios

---

## 5. Regulatory Context

### 5.1 Basel III/IV IRRBB Framework

#### **Evolution of IRRBB Regulation**

| Timeline | Development |
|----------|-------------|
| **2014** | Basel Committee publishes consultative document on IRRBB standards |
| **2016** | Final IRRBB standards issued |
| **2019** | Revisions to standardized shock scenarios |
| **2024** | Updated calibration and disclosure requirements |

#### **Two-Pillar Approach**

The Basel framework has three pillars, but IRRBB is handled under two of them:

**Pillar 1 (Minimum Capital Requirements):**
- IRRBB is **not** subject to Pillar 1 minimum capital charges
- Remains under Pillar 2 (Supervisory Review)

**Pillar 2 (Supervisory Review):**
- Banks must have robust IRRBB measurement and management systems
- Supervisors evaluate adequacy of IRRBB frameworks
- Additional capital may be required if IRRBB is deemed inadequate

**Pillar 3 (Disclosure):**
- Public disclosure of IRRBB exposures and measurement results
- Enhances market discipline (investors and depositors can see the bank's risk)

> **In Simple Terms:** Pillar 1 is like a minimum credit score requirement. Pillar 2 is like a loan officer reviewing your full financial picture. Pillar 3 is like making your credit report public. IRRBB is handled by the loan officer review (Pillar 2) and public disclosure (Pillar 3), not the minimum requirement (Pillar 1).

#### **Key Regulatory Requirements**

| Requirement | What It Means |
|-------------|---------------|
| **Governance** | Board and senior management oversight of IRRBB |
| **Measurement** | EVE and NII under six standardized shocks |
| **Risk Limits** | Established limits for IRRBB exposures |
| **Stress Testing** | Regular stress testing beyond standardized shocks |
| **Model Validation** | Independent validation of IRRBB models |
| **Disclosure** | Public disclosures on IRRBB (Pillar 3) |

### 5.2 Disclosure Requirements (Pillar 3)

#### **Quantitative Disclosures**

Banks must disclose the following for each of the six standardized shocks:

| Metric | What It Means |
|--------|---------------|
| **ΔEVE** | Change in Economic Value of Equity (absolute amount and % of Tier 1 Capital) |
| **ΔNII** | Change in Net Interest Income over 12-month horizon |
| **Outlier Status** | Whether bank exceeds 15% of Tier 1 Capital EVE decline threshold |

**Example Disclosure Format:**

| Scenario | ΔEVE ($M) | ΔEVE (% of Tier 1) | ΔNII ($M) | ΔNII (%) |
|----------|-----------|-------------------|-----------|----------|
| Parallel Up | -$75 | -12% | +$15 | +8% |
| Parallel Down | +$45 | +7% | -$20 | -11% |
| Steepener | -$30 | -5% | +$8 | +4% |
| Flattener | -$20 | -3% | -$12 | -6% |
| Short Rate Up | -$40 | -6% | +$10 | +5% |
| Short Rate Down | +$25 | +4% | -$15 | -8% |

> **In Simple Terms:** This table is like a report card. It shows how the bank would perform under each stress scenario. Regulators and investors can see if the bank is taking too much risk.

#### **Qualitative Disclosures**

| Disclosure Area | Required Content |
|-----------------|------------------|
| **Governance** | Board oversight, risk committee structure, management responsibilities |
| **Risk Management Framework** | IRRBB identification, measurement, monitoring, control processes |
| **Measurement Methodologies** | EVE and NII models, key assumptions, limitations |
| **Key Assumptions** | Behavioral assumptions for non-maturity deposits, prepayment models, commercial margins |
| **Hedging Strategies** | Use of derivatives, hedging objectives, effectiveness assessment |
| **Stress Testing** | Scenarios used, frequency, integration with capital planning |

### 5.3 Capital Impact

#### **Outlier Framework**

Banks are classified as **IRRBB outliers** if:

```
(Maximum ΔEVE across 6 shocks ÷ Tier 1 Capital) > 15%
```

**Consequences of Outlier Status:**
1. **Enhanced Supervision:** Increased regulatory scrutiny and examination frequency
2. **Capital Add-On:** Supervisors may require additional capital
3. **Remediation Plan:** Bank must develop and execute plan to reduce IRRBB
4. **Public Disclosure:** Outlier status disclosed in public report

#### **Internal Capital Adequacy Assessment Process (ICAAP)**

Banks must incorporate IRRBB into ICAAP:

- **Capital Planning:** Include IRRBB stress scenarios in capital forecasts
- **Risk Appetite:** Set IRRBB limits aligned with capital capacity
- **Recovery Planning:** Include IRRBB triggers in recovery plan indicators

> **In Simple Terms:** ICAAP is the bank's internal process for figuring out how much capital it needs. IRRBB must be part of this calculation. It's like including insurance costs in your household budget.

---

### Key Takeaways: Regulatory Context

- **Basel III IRRBB** framework mandates EVE and NII measurement under six shocks
- **Pillar 2** (not Pillar 1) — supervisors evaluate adequacy and may require additional capital
- **15% of Tier 1 Capital** EVE decline triggers outlier status
- **Public disclosures** require both quantitative results and qualitative methodology descriptions
- **ICAAP integration** ensures IRRBB is incorporated into capital planning

---

## 6. Mitigation and Hedging Strategies

### 6.1 Derivative Hedging Instruments

#### **Interest Rate Swaps**

**Definition:** An agreement to exchange fixed-rate payments for floating-rate payments (or vice versa) on a notional (hypothetical) principal amount.

**How It Works:** No actual principal changes hands. The two parties just exchange the difference between fixed and floating payments.

**Hedging Applications:**

| Bank's Position | Risk | Swap Strategy | Effect |
|-----------------|------|---------------|--------|
| **Fixed-Rate Assets** | Rates rise → value falls | Pay Fixed / Receive Floating | Converts to floating; reduces duration |
| **Fixed-Rate Liabilities** | Rates fall → funding cost locked high | Receive Fixed / Pay Floating | Converts to floating; benefits from rate decline |
| **Net Positive Duration Gap** | EVE falls when rates rise | Pay Fixed / Receive Floating | Reduces overall duration gap |

**Example:** Bank has $100 million of 5-year fixed-rate loans at 4%. To hedge against rising rates:
- Enter $100 million notional 5-year swap
- Pay 4% fixed, receive SOFR floating
- If rates rise to 6%, swap payments increase, offsetting loan value decline

> **In Simple Terms:** A swap is like switching your fixed-rate mortgage to an adjustable-rate mortgage (or vice versa) without actually refinancing. You're swapping one type of interest rate exposure for another.

#### **Interest Rate Futures**

**Definition:** Exchange-traded contracts to buy/sell interest-bearing instruments at future dates at predetermined prices.

**Common Contracts:**

| Contract | What It's Based On | Duration | Use Case |
|----------|-------------------|----------|----------|
| **Eurodollar Futures** | 3-month SOFR | 0.25 years | Short-term rate hedging |
| **Treasury Futures** | 2Y, 5Y, 10Y, 30Y Treasury | Varies | Duration hedging |

**Advantages:**
- Highly liquid (easy to buy and sell)
- Transparent pricing
- No counterparty credit risk (cleared through exchange)

**Disadvantages:**
- Standardized contracts (may not match exact exposure)
- Daily margin requirements (must post collateral as prices move)
- Basis risk vs. bank's actual positions

#### **Interest Rate Options**

**Definition:** Contracts giving the right (but not obligation) to enter into an interest rate transaction at specified terms.

| Option Type | What It Does | Hedging Use |
|-------------|--------------|-------------|
| **Interest Rate Cap** | Pays if reference rate exceeds strike | Hedge against rising funding costs |
| **Interest Rate Floor** | Pays if reference rate falls below strike | Hedge against falling asset yields |
| **Interest Rate Collar** | Long cap + short floor | Limit rate exposure within range; reduces cost |
| **Swaption** | Option to enter swap | Hedge future issuance or prepayment risk |

**Example — Interest Rate Cap:**
- Bank has $50 million floating-rate liabilities tied to SOFR
- Concerned about rates rising above 5%
- Purchase $50 million SOFR cap at 5% strike
- If SOFR rises to 7%, cap pays 2% × $50 million = $1 million annually

> **In Simple Terms:** An interest rate cap is like insurance against rates rising above a certain level. You pay a premium, and if rates go above your "deductible" (strike), you get paid.

#### **Hedging EVE vs. Hedging NII**

| Objective | Preferred Instruments | Why |
|-----------|----------------------|-----|
| **Hedge EVE** | Long-dated swaps, Treasury futures, swaptions | Match duration of long-term positions |
| **Hedge NII** | Short-dated swaps, Eurodollar futures, caps/floors | Match repricing horizon of earnings |

> **In Simple Terms:** Hedge long-term risk (EVE) with long-term instruments. Hedge short-term risk (NII) with short-term instruments. Don't use a 30-year swap to hedge next year's earnings.

### 6.2 Balance Sheet Restructuring

#### **Product Mix Adjustments**

| Strategy | How to Implement | IRR Impact |
|----------|-----------------|------------|
| **Shift to Floating-Rate Loans** | Originate more adjustable-rate mortgages, floating-rate commercial loans | Reduces asset duration; benefits from rising rates |
| **Extend Liability Duration** | Issue longer-term CDs, subordinated debt | Increases liability duration; reduces duration gap |
| **Securities Portfolio Rebalancing** | Reduce mortgage-backed securities duration; increase short-term Treasuries | Lowers overall asset duration |
| **Deposit Product Design** | Introduce rate-sensitive products with controlled betas | Manage deposit repricing behavior |

#### **Pricing Strategies**

| Strategy | Description | Risk Management Benefit |
|----------|-------------|------------------------|
| **Deposit Beta Management** | Set deposit rate policies to control funding cost sensitivity | Limits profit compression in rising rate environment |
| **Loan Prepayment Penalties** | Charge fees for early loan payoff | Reduces optionality risk; compensates for reinvestment risk |
| **Rate Floors on Loans** | Set minimum rate on floating-rate loans | Protects yield in falling rate environment |
| **Callable Securities** | Invest in callable bonds/loans | Provides optionality to reduce duration if rates fall |

#### **Post-SVB Best Practices**

| Lesson | Implementation |
|--------|----------------|
| **HTM Limits** | Limit HTM securities as % of assets; recognize economic reality of unrealized losses |
| **Duration Limits** | Set maximum portfolio duration; monitor weighted average life |
| **Concentration Limits** | Limit deposit concentration by customer type, size, industry |
| **Hedging Mandates** | Require hedging for duration above threshold |
| **ALCO Oversight** | Enhanced ALCO (Asset-Liability Committee) review of IRR metrics; frequent scenario analysis |

> **In Simple Terms:** SVB taught us that you can't ignore interest rate risk hoping it will go away. Set explicit limits on how much duration risk you'll take, and hedge when you exceed those limits.

---

### Key Takeaways: Mitigation and Hedging

- **Interest rate swaps** are the primary tool for duration management
- **Futures and options** provide liquid, exchange-traded hedging alternatives
- **Hedge EVE with long-dated instruments; hedge NII with short-dated instruments**
- **Balance sheet restructuring** may be more cost-effective than derivatives for structural mismatches
- **Post-SVB:** Implement explicit duration limits, HTM limits, and hedging mandates

---

## 7. Practical Case Study (Hypothetical)

### 7.1 Simplified Bank Balance Sheet

**Community Bank — Current Position (as of January 1, 2026)**

**ASSETS**

| Position | Balance ($M) | Average Rate | Duration (Years) |
|----------|--------------|--------------|------------------|
| Cash & Reserves | $50 | 0.5% | 0.0 |
| Securities (AFS) | $200 | 2.5% | 6.5 |
| Securities (HTM) | $150 | 2.0% | 8.0 |
| Commercial Loans (Fixed) | $300 | 5.0% | 3.5 |
| Commercial Loans (Floating) | $200 | SOFR + 2% | 0.5 |
| Residential Mortgages | $250 | 3.5% | 5.0 |
| **Total Assets** | **$1,150** | **3.4%** | **4.2** |

**LIABILITIES & EQUITY**

| Position | Balance ($M) | Average Rate | Duration (Years) |
|----------|--------------|--------------|------------------|
| Demand Deposits | $300 | 0.1% | 0.5* |
| Savings Deposits | $250 | 0.5% | 1.0* |
| Money Market Deposits | $150 | 2.0% | 0.25 |
| CDs (<1 year) | $100 | 3.5% | 0.5 |
| CDs (>1 year) | $150 | 3.0% | 2.5 |
| FHLB Advances | $100 | 3.0% | 2.0 |
| Subordinated Debt | $50 | 4.5% | 5.0 |
| **Total Liabilities** | **$1,100** | **1.8%** | **1.3** |
| **Tier 1 Capital** | **$50** | — | — |
| **Total Liabilities & Equity** | **$1,150** | — | — |

*Behavioral duration for non-maturity deposits (estimated based on how quickly these deposits would reprice)

**Key Metrics:**

| Metric | Calculation | Result |
|--------|-------------|--------|
| **Duration Gap** | 4.2 - (1,100/1,150 × 1.3) | **2.95 years** (positive) |
| **Net Interest Margin** | 3.4% - 1.8% | **1.6%** |
| **Annual NII** | $1,150M × 3.4% - $1,100M × 1.8% | **$19.3M** |
| **Tier 1 Capital Ratio** | $50M / $1,150M | **4.35%** (simplified) |

> **In Simple Terms:** This bank has a positive duration gap of 2.95 years. This means its assets are more sensitive to interest rate changes than its liabilities. When rates rise, the bank's economic value will fall.

### 7.2 +200bps Parallel Shock Impact Analysis

#### **Step 1: Apply Rate Shock**

All interest rates increase by 200 basis points (2%):

| Position | Current Rate | Shocked Rate |
|----------|--------------|--------------|
| Assets (weighted average) | 3.4% | 5.4% |
| Liabilities (weighted average) | 1.8% | 3.8% |
| Fed Funds / SOFR | ~5.0% | ~7.0% |

#### **Step 2: Calculate EVE Impact**

**Duration-Based Approximation:**

```
Change in EVE ≈ -Duration Gap × Total Assets × Change in Interest Rate
Change in EVE ≈ -2.95 × $1,150M × 0.02 = -$67.85M
```

**Detailed Present Value Calculation:**

| Component | Current PV ($M) | Shocked PV ($M) | Change ($M) |
|-----------|-----------------|-----------------|-------------|
| Assets | $1,120 | $1,035 | -$85 |
| Liabilities | $1,070 | $1,015 | -$55 |
| **EVE** | **$50** | **$20** | **-$30** |

*Note: Detailed PV calculation shows -$30M decline (less than duration approximation due to curvature effects and behavioral assumptions)*

**EVE Decline as % of Tier 1 Capital:**
```
($30M / $50M) × 100% = 60%
```

**Outlier Status:** **YES** — exceeds 15% threshold significantly

> **In Simple Terms:** Under a standard 2% rate increase, this bank would lose 60% of its capital cushion. This is four times the regulatory concern threshold of 15%. The bank is taking significant interest rate risk.

#### **Step 3: Calculate NII Impact (12-Month Horizon)**

**Baseline NII Projection:**
- Interest Income: $39.1M
- Interest Expense: $19.8M
- **Baseline NII: $19.3M**

**Shocked NII Projection:**

| Component | Calculation | Amount ($M) |
|-----------|-------------|-------------|
| **Interest Income** | | |
| Fixed-Rate Assets (unchanged yield) | $700M × 3.8% | $26.6 |
| Floating-Rate Assets (repriced) | $450M × 5.8% | $26.1 |
| **Total Interest Income** | | **$52.7** |
| **Interest Expense** | | |
| Non-Maturity Deposits (30% beta) | $550M × 1.1% | $6.1 |
| CDs & Wholesale (100% beta) | $400M × 5.0% | $20.0 |
| **Total Interest Expense** | | **$26.1** |
| **Shocked NII** | | **$26.6** |

**NII Change:**
- Absolute: $26.6M - $19.3M = **+$7.3M**
- Percentage: +7.3 / 19.3 = **+38%**

> **In Simple Terms:** Here's the paradox: Under rising rates, the bank's annual profits would actually INCREASE by 38%. But its economic value would DECREASE by 60%. This is why you need both metrics — NII alone would make this look like a good scenario.

#### **Step 4: Impact on Capital Ratios**

| Metric | Baseline | After Shock | Change |
|--------|----------|-------------|--------|
| **Tier 1 Capital (starting)** | $50M | $50M | — |
| **Unrealized AFS Losses (AOCI)** | -$10M | -$25M | -$15M |
| **Adjusted Tier 1 Capital** | $40M | $25M | -$15M |
| **Risk-Weighted Assets** | $900M | $900M | — |
| **Tier 1 Capital Ratio** | 4.44% | 2.78% | **-1.66%** |
| **NII Contribution to Capital** | +$19.3M/yr | +$26.6M/yr | +$7.3M/yr |

**Critical Insight:** Despite NII **increasing** by 38%, the bank's capital ratio **deteriorates** due to unrealized losses on securities. This illustrates the **EVE vs. NII divergence**.

> **In Simple Terms:** This bank would look profitable on its income statement while simultaneously becoming insolvent on its balance sheet. This is exactly what happened to Silicon Valley Bank.

### 7.3 Risk Management Recommendations

Based on this analysis, the bank should consider:

| Action | Why | Expected Impact |
|--------|-----|-----------------|
| **Reduce Securities Duration** | Sell long-duration AFS/HTM; reinvest in shorter maturities | Reduce duration gap from 2.95 to less than 2.0 |
| **Extend Liability Duration** | Issue 3-5 year CDs; extend FHLB advances | Increase liability duration to 2.0+ years |
| **Interest Rate Swaps** | Pay fixed on $200M notional 5-year swaps | Hedge approximately $20M of asset duration |
| **Deposit Beta Review** | Analyze actual deposit repricing behavior | Refine NII projections; may show higher sensitivity |
| **HTM Reclassification** | Consider reclassifying some HTM to AFS | Increase transparency; may trigger AOCI impact |
| **Capital Raise** | Issue additional Tier 1 capital | Improve capital buffer against IRR losses |

> **In Simple Terms:** This bank needs to either: (1) make its assets less sensitive to rates, (2) make its liabilities more sensitive to rates, (3) hedge the difference with derivatives, or (4) raise more capital. Doing nothing is not an option given the 60% EVE sensitivity.

---

### Key Takeaways: Case Study

- **Positive duration gap of 2.95 years** creates significant EVE sensitivity to rising rates
- **+200bps shock** causes **60% EVE decline** relative to Tier 1 Capital (well above 15% outlier threshold)
- **NII increases 38%** while **capital ratio falls** — classic EVE vs. NII divergence
- **Unrealized AFS losses** directly reduce regulatory capital through AOCI
- **Multiple mitigation strategies** available: balance sheet restructuring, derivatives, capital raise

---

## Conclusion

Interest Rate Risk management is fundamental to bank safety and soundness. The 2023 banking crisis, particularly the collapse of Silicon Valley Bank, demonstrated that:

1. **Unrealized losses are economically real** — HTM accounting does not eliminate economic risk
2. **Duration mismatch can be fatal** — even with strong credit quality and liquidity
3. **EVE and NII tell different stories** — both perspectives are essential for comprehensive risk assessment
4. **Liquidity and IRR are interconnected** — one can trigger the other in a stress scenario
5. **Hedging is not optional** — active duration management is a core competency

Effective IRR management requires:
- **Robust measurement** using both EVE and NII approaches
- **Comprehensive stress testing** across regulatory, historical, and hypothetical scenarios
- **Clear risk limits** aligned with capital capacity and risk appetite
- **Active hedging strategies** using derivatives and balance sheet management
- **Strong governance** with Board and ALCO oversight

This guide provides the technical foundation for understanding and managing IRR. However, each institution's risk profile is unique. Risk managers must tailor these frameworks to their specific balance sheet structure, business model, and risk tolerance.

---

## Glossary of Key Terms

| Term | Simple Definition |
|------|-------------------|
| **AFS (Available-for-Sale)** | Securities carried at market value with unrealized gains/losses in a special equity account |
| **ALCO (Asset-Liability Committee)** | Senior management committee responsible for IRR and liquidity management |
| **AOCI (Accumulated Other Comprehensive Income)** | Balance sheet account where unrealized AFS gains/losses are recorded |
| **Basis Risk** | Risk from imperfect correlation between different rate indices (like Prime vs. SOFR) |
| **Basis Points (bps)** | Hundredths of a percent; 100 bps = 1%, 200 bps = 2% |
| **Duration** | Measure of interest rate sensitivity; approximate % price change for 1% rate move |
| **Duration Gap** | Difference between asset and liability durations, weighted by balance sheet size |
| **EVE (Economic Value of Equity)** | Present value of assets minus present value of liabilities |
| **HTM (Held-to-Maturity)** | Securities carried at original cost; unrealized gains/losses not immediately visible |
| **IRRBB** | Interest Rate Risk in the Banking Book |
| **NII (Net Interest Income)** | Interest income minus interest expense |
| **Optionality Risk** | Risk from embedded options that allow customers to alter cash flows |
| **Present Value** | What future money is worth today |
| **Repricing Risk** | Risk from timing mismatches in asset and liability repricing |
| **VaR (Value at Risk)** | Statistical measure of potential loss at specified confidence level |
| **Yield Curve** | The relationship between interest rates across different maturities |
| **Yield Curve Risk** | Risk from changes in the shape or slope of the yield curve |

---

*This guide reflects regulatory standards and industry best practices as of early 2026. Banks should consult current regulatory guidance and qualified advisors for institution-specific applications.*
