# Mastering Interest Rate Risk (IRR) and Stress Testing in Banking

> **Disclaimer:** This guide is for educational and risk management purposes only. It does not constitute financial advice, regulatory guidance, or investment recommendations. Banks should consult with qualified risk management professionals and regulatory advisors for institution-specific applications.

---

## 1. Fundamentals of Interest Rate Risk (IRR)

### 1.1 What is Interest Rate Risk in the Banking Book?

**Interest Rate Risk in the Banking Book (IRRBB)** is the current or prospective risk to a bank's capital and earnings arising from adverse movements in interest rates that affect the bank's banking book positions. Unlike trading book risk (which is subject to market risk capital charges), IRRBB relates to traditional banking activities: taking deposits, making loans, and holding securities.

When interest rates change, they affect banks through two primary channels:

| Channel | Impact |
|---------|--------|
| **Earnings Perspective** | Affects **Net Interest Income (NII)** — the difference between interest earned on assets and interest paid on liabilities |
| **Economic Value Perspective** | Affects **Economic Value of Equity (EVE)** — the present value of all future cash flows from assets minus liabilities |

### 1.2 The Four Components of IRR

Understanding IRR requires decomposing it into four distinct but interrelated risk types:

#### **1. Repricing Risk**

**Definition:** The risk arising from timing differences in the maturity (for fixed-rate instruments) and repricing (for floating-rate instruments) of bank assets, liabilities, and off-balance sheet positions.

**Mechanism:**
- When rates rise, liabilities may reprice faster than assets → **margin compression**
- When rates fall, assets may reprice faster than liabilities → **margin expansion** (but reinvestment risk)

**Example:** A bank funds a 5-year fixed-rate mortgage with 1-year CDs. If rates rise after year 1, the CD reprices at higher rates while the mortgage yield remains fixed.

#### **2. Yield Curve Risk**

**Definition:** The risk arising from changes in the shape and slope of the yield curve (the relationship between interest rates across different maturities).

**Mechanism:**
- **Parallel shifts:** All rates move by the same amount
- **Non-parallel shifts:** Different maturities move by different amounts
  - **Steepening:** Long-term rates rise faster than short-term rates (or short-term fall faster)
  - **Flattening:** Short-term rates rise faster than long-term rates (or long-term fall faster)
  - **Inversion:** Short-term rates exceed long-term rates

**Example:** A bank with positive duration gap benefits from parallel rate increases but may suffer if the curve flattens unexpectedly.

#### **3. Basis Risk**

**Definition:** The risk arising from imperfect correlation between rate adjustments for assets and liabilities that are tied to different reference rates (indices).

**Mechanism:**
- Assets tied to **Prime Rate** vs. liabilities tied to **LIBOR/SOFR**
- Assets tied to **10-Year Treasury** vs. liabilities tied to **Fed Funds**
- Spread between indices can widen or narrow independently

**Example:** A bank's loans reprice with Prime Rate while deposits reprice with SOFR. If Prime-SOFR spread narrows, the bank's margin compresses even if both rates move in the same direction.

#### **4. Optionality Risk**

**Definition:** The risk arising from embedded options in bank products that allow customers to alter cash flows in response to interest rate changes.

**Common Embedded Options:**
| Product | Option Type | Risk When Rates... |
|---------|-------------|-------------------|
| **Mortgages** | Prepayment option | Fall → borrowers refinance |
| **Callable Bonds** | Issuer call option | Fall → issuer calls bonds |
| **Deposits** | Early withdrawal option | Rise → depositors withdraw |
| **Lines of Credit** | Drawdown option | Rise → borrowers draw more |

**Example:** When rates fall sharply, mortgage holders prepay and refinance at lower rates. The bank loses high-yielding assets and must reinvest at lower rates — a classic **prepayment risk**.

### 1.3 Why IRR Management is Critical

#### **Solvency Impact**

Interest rate risk directly threatens bank solvency through economic value erosion:

- **Unrealized losses on securities:** As demonstrated in the 2023 banking crisis, Available-for-Sale (AFS) and Held-to-Maturity (HTM) securities lose market value when rates rise
- **Capital ratio deterioration:** Declining economic value reduces regulatory capital ratios
- **SVB Lesson:** Silicon Valley Bank held $91.3B in HTM securities with over $15B in unrealized losses — nearly equal to its entire equity base. While not reflected in AOCI, these losses were economically real and contributed to insolvency concerns during the liquidity run.

#### **Liquidity Impact**

IRR and liquidity risk are deeply interconnected:

- **Deposit flight:** Rising rates may trigger deposit outflows as customers seek higher yields elsewhere
- **Asset liquidation pressure:** Unrealized losses may force asset sales at depressed prices to meet withdrawal demands
- **Funding cost spiral:** As perceived risk increases, funding costs rise, further compressing margins

#### **Earnings Volatility**

Unmanaged IRR creates unpredictable earnings:

- **NII compression:** Mismatched repricing can cause sudden margin deterioration
- **Provisioning pressure:** Economic stress from rate shocks may increase credit losses
- **Investor confidence:** Earnings volatility reduces market valuation and increases cost of capital

---

### Key Takeaways: Fundamentals of IRR

- **IRRBB** affects both earnings (NII) and economic value (EVE)
- **Four components** must be managed: Repricing Risk, Yield Curve Risk, Basis Risk, and Optionality Risk
- **Solvency and liquidity** are both at risk from unmanaged IRR
- **SVB collapse (2023)** demonstrated that unrealized HTM losses are economically real, not just accounting entries
- **Duration mismatch** between assets and liabilities is the primary driver of IRR exposure

---

## 2. The Economic Value of Equity (EVE) Approach

### 2.1 Definition and Conceptual Framework

**Economic Value of Equity (EVE)** is the net present value of a bank's expected future cash flows from all assets minus the present value of all expected future cash flows from liabilities.

```
EVE = PV(Assets) - PV(Liabilities)

EVE = Σ[CF(A,t) / (1 + r)^t] - Σ[CF(L,t) / (1 + r)^t]
```

**Where:**
| Variable | Definition |
|----------|------------|
| CF(A,t) | Expected cash flow from assets at time t |
| CF(L,t) | Expected cash flow from liabilities at time t |
| r | Discount rate applicable to time period t (based on yield curve) |
| t | Time period (typically in years) |
| T | Final maturity of all positions (can extend 30+ years) |

### 2.2 How EVE Measures Long-Term Economic Value Impact

EVE captures the **full economic impact** of interest rate changes across the entire life of all banking book positions:

#### **Discounting Mechanism**

When interest rates change, the discount rate (r) in the present value formula changes:

- **Rates Rise →** Discount factors decrease → Present values fall
- **Rates Fall →** Discount factors increase → Present values rise

**Critical Insight:** Assets and liabilities typically have different durations (sensitivities to rate changes). The **duration gap** determines whether EVE increases or decreases when rates move.

#### **Example Calculation**

Consider a simplified bank position:

| Position | Cash Flow | Maturity | Current Rate |
|----------|-----------|----------|--------------|
| Asset (Loan) | $1,000,000 | 5 years | 4% |
| Liability (CD) | $1,000,000 | 2 years | 3% |

**Current EVE:**
```
PV(Asset) = $1,000,000 / (1.04)^5 = $821,927
PV(Liability) = $1,000,000 / (1.03)^2 = $942,596
EVE = $821,927 - $942,596 = -$120,669
```

**After +200bps Parallel Shock:**
```
PV(Asset) = $1,000,000 / (1.06)^5 = $747,258  (decline of $74,669)
PV(Liability) = $1,000,000 / (1.05)^2 = $907,029  (decline of $35,567)
New EVE = $747,258 - $907,029 = -$159,771
```

**EVE Decline:** $39,102 (the asset lost more value than the liability due to longer duration)

### 2.3 EVE vs. Short-Term Earnings: Pros and Cons

| Aspect | EVE Approach | Short-Term Earnings (NII) |
|--------|--------------|--------------------------|
| **Time Horizon** | Entire life of all positions (10-30+ years) | 1-2 year forward period |
| **Measurement Focus** | Economic value / solvency | Accounting earnings / profitability |
| **Sensitivity** | Captures long-duration risk | Captures near-term repricing |
| **Rate Shock Impact** | Shows full economic impact | Shows budget/forecast impact |
| **Capital Planning** | Direct measure of capital at risk | Indirect through retained earnings |
| **Limitations** | Requires long-term assumptions; sensitive to behavioral models | Misses long-term value erosion; may show NII increase when EVE declines |

#### **Critical Tension: EVE vs. NII Can Move in Opposite Directions**

A bank can experience **rising NII but declining EVE** simultaneously:

- **Scenario:** Rising rate environment
- **NII Impact:** Positive — floating-rate assets reprice up faster than fixed-rate liabilities
- **EVE Impact:** Negative — long-duration fixed-rate assets lose significant present value

**Post-2023 Lesson:** Many banks (including SVB) reported strong NII in 2022 while their EVE was deteriorating rapidly due to unrealized securities losses. Relying solely on NII metrics created a false sense of security.

### 2.4 EVE Stress Testing with Rate Shocks

#### **Standard Regulatory Shocks**

Per Basel Committee IRRBB standards (BCBS d578), banks must calculate EVE under six standardized interest rate shock scenarios:

| Scenario | Shock Description | Typical Magnitude (USD) |
|----------|-------------------|------------------------|
| **Parallel Up** | Uniform increase across all maturities | +200 bps |
| **Parallel Down** | Uniform decrease across all maturities | -200 bps (with 0% floor) |
| **Steepener** | Short rates down, long rates up | Short: -100 bps / Long: +200 bps |
| **Flattener** | Short rates up, long rates down | Short: +100 bps / Long: -100 bps |
| **Short Rate Up** | Only short-term rates increase | +200 bps (≤1 year) |
| **Short Rate Down** | Only short-term rates decrease | -200 bps (≤1 year, with floor) |

#### **"EVE at Risk" Concept**

**EVE at Risk** quantifies the maximum decline in economic value under adverse scenarios:

```
EVE at Risk = Baseline EVE - EVE_shock
```

Often expressed as a percentage of Tier 1 Capital:

```
EVE Decline % of T1 Capital = (EVE at Risk / Tier 1 Capital) × 100%
```

**Regulatory Outlier Test:** Under Basel III, if EVE declines by more than **15% of Tier 1 Capital** under any standardized shock, the bank may be flagged as an "outlier" requiring enhanced supervisory scrutiny and potentially additional capital.

---

### Key Takeaways: EVE Approach

- **EVE = PV(Assets) - PV(Liabilities)** — measures full economic value impact
- **Long-term perspective** captures risks that NII misses
- **Six standardized shocks** required under Basel III IRRBB framework
- **EVE and NII can move in opposite directions** — both must be monitored
- **15% of Tier 1 Capital** is the regulatory outlier threshold for EVE decline
- **SVB Lesson:** Strong NII masked severe EVE deterioration from unrealized securities losses

---

## 3. Alternative IRR Measurement & Stress Testing Methodologies

While EVE provides the economic value perspective, comprehensive IRR management requires multiple complementary measurement approaches.

### 3.1 Net Interest Income (NII) Simulation

#### **Definition and Purpose**

**NII Simulation** is a dynamic earnings-based approach that projects changes in net interest income over a specified time horizon (typically 12-24 months) under various interest rate scenarios.

```
NII = Interest Income - Interest Expense

NII_shock = Σ(Asset Balances × shocked Rates) - Σ(Liability Balances × shocked Rates)
```

#### **Key Components of NII Simulation Models**

| Component | Description |
|-----------|-------------|
| **Balance Sheet Growth** | Assumptions about new loan originations, deposit gathering, securities purchases |
| **Pricing Relationships** | How asset and liability rates respond to market rate changes (betas, spreads) |
| **Repricing Schedules** | When each position resets to new rates |
| **Prepayment Assumptions** | Expected early payoffs on loans and securities |
| **Behavioral Assumptions** | How non-maturity deposits (checking, savings) reprice |
| **Option Features** | Impact of caps, floors, and callable securities |

#### **Contrast with EVE**

| Dimension | NII Simulation | EVE |
|-----------|----------------|-----|
| **Time Horizon** | 1-2 years | Full life of all positions |
| **Accounting Basis** | Accrual accounting | Present value / economic |
| **New Business** | Includes projected new volumes | Typically static balance sheet |
| **Sensitivity** | Near-term repricing mismatch | Long-duration exposure |
| **Use Case** | Budget planning, earnings guidance | Capital adequacy, strategic planning |
| **Regulatory Focus** | Secondary | Primary (Basel III) |

#### **Earnings at Risk (EAR)**

**EAR** expresses NII simulation results as a risk metric:

```
EAR = Baseline NII - NII_shock
```

Often expressed as percentage of baseline:

```
EAR % = [(Baseline NII - NII_shock) / Baseline NII] × 100%
```

**Example:** If baseline NII is $100M and NII under +200bps shock is $85M:
- EAR = $15M
- EAR% = 15%

### 3.2 Duration Gap Analysis

#### **Modified Duration**

**Modified Duration** measures the percentage change in a security's price for a 100-basis point change in interest rates.

```
Modified Duration = Macaulay Duration / (1 + YTM/n)
```

**Where:**
| Variable | Definition |
|----------|------------|
| Macaulay Duration | Weighted average time to receive cash flows |
| YTM | Yield to Maturity |
| n | Number of coupon periods per year |

**Price Sensitivity Formula:**
```
%ΔPrice ≈ -Modified Duration × ΔYield
```

**Example:** A bond with modified duration of 5.0 will decline approximately 5% in price if rates rise 100 bps.

#### **Duration Gap Calculation**

**Duration Gap** measures the mismatch between asset and liability durations, weighted by their respective balances:

```
Duration Gap = Duration_A - (L/A × Duration_L)
```

**Where:**
| Variable | Definition |
|----------|------------|
| Duration_A | Weighted average duration of assets |
| Duration_L | Weighted average duration of liabilities |
| L | Total liabilities |
| A | Total assets |

#### **EVE Sensitivity via Duration Gap**

```
ΔEVE ≈ -Duration Gap × Total Assets × ΔYield
```

**Interpretation:**
- **Positive Duration Gap:** Assets have longer duration than liabilities → EVE falls when rates rise
- **Negative Duration Gap:** Liabilities have longer duration than assets → EVE rises when rates rise
- **Zero Duration Gap:** Immunized against parallel rate shifts (theoretical ideal)

#### **Limitations of Duration Gap**

| Limitation | Explanation |
|------------|-------------|
| **Parallel Shift Assumption** | Assumes all rates move equally; doesn't capture yield curve risk |
| **Linear Approximation** | Duration is accurate only for small rate changes; convexity matters for large moves |
| **Static Measure** | Doesn't account for behavioral changes or new business |
| **Optionality Ignored** | Embedded options change effective duration as rates move |

### 3.3 Value at Risk (VaR) Approach

#### **Statistical Framework**

**VaR** applies statistical methods to estimate the maximum potential loss in EVE or NII over a specified time horizon at a given confidence level.

```
VaR(α,T) = Portfolio Value × σ × z_α × √T
```

**Where:**
| Variable | Definition |
|----------|------------|
| α | Confidence level (e.g., 95%, 99%) |
| T | Time horizon (days, months) |
| σ | Portfolio volatility (standard deviation of returns) |
| z_α | Z-score for confidence level (1.65 for 95%, 2.33 for 99%) |

#### **VaR Methodologies for IRR**

| Method | Description | Pros | Cons |
|--------|-------------|------|------|
| **Historical Simulation** | Revalues portfolio using historical rate changes | No distribution assumptions; captures fat tails | Requires long history; may miss unprecedented events |
| **Variance-Covariance** | Uses statistical parameters (mean, variance, correlation) | Computationally efficient; transparent | Assumes normal distribution; underestimates tail risk |
| **Monte Carlo Simulation** | Generates thousands of random rate paths | Most flexible; captures complex dynamics | Computationally intensive; model risk |

#### **Limitations for IRR**

- **Historical data may not predict future:** The 2022-2023 rate hiking cycle was unprecedented in speed
- **Correlation breakdown:** Relationships between rates at different maturities can change dramatically
- **Tail risk underestimation:** VaR may not capture extreme but plausible scenarios (the "black swan" problem)

### 3.4 Liquidity-Adjusted IRR

#### **The IRR-Liquidity Nexus**

The 2023 banking crisis demonstrated that IRR and liquidity risk are inseparable:

1. **Rising rates** → Unrealized losses on securities
2. **Unrealized losses** → Reduced collateral value for borrowing
3. **Deposit flight** → Need to liquidate assets at losses
4. **Asset sales** → Realize losses, erode capital
5. **Capital erosion** → Further deposit flight (vicious cycle)

#### **Liquidity-Adjusted IRR Framework**

This approach integrates funding stress scenarios with IRR measurement:

| Scenario Component | Description |
|--------------------|-------------|
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

---

### Key Takeaways: Alternative Methodologies

- **NII Simulation** provides earnings perspective (1-2 year horizon); complements EVE
- **Duration Gap** offers quick sensitivity measure but has limitations (parallel shift assumption, ignores optionality)
- **VaR** adds statistical rigor but may underestimate tail risk
- **Liquidity-Adjusted IRR** is critical post-SVB — IRR and liquidity risk are interconnected
- **No single metric is sufficient** — use multiple approaches for comprehensive view

---

## 4. Designing Stress Testing Scenarios

Effective stress testing requires diverse scenarios that capture regulatory requirements, historical precedents, and institution-specific vulnerabilities.

### 4.1 Regulatory Shocks: The Six Standardized Scenarios

Per Basel Committee IRRBB standards (BCBS d578) and OCC/Fed guidance, banks must evaluate IRR under six standardized interest rate shock scenarios:

#### **Scenario Specifications (USD)**

| # | Scenario | Short End (1Y) | Long End (25Y) | Interpolation |
|---|----------|----------------|----------------|---------------|
| 1 | **Parallel Up** | +200 bps | +200 bps | Linear |
| 2 | **Parallel Down** | -200 bps | -200 bps | Linear (0% floor) |
| 3 | **Steepener** | -100 bps | +200 bps | Linear |
| 4 | **Flattener** | +100 bps | -100 bps | Linear |
| 5 | **Short Rate Up** | +200 bps | 0 bps | Linear decay |
| 6 | **Short Rate Down** | -200 bps | 0 bps | Linear decay (0% floor) |

#### **Scenario Rationale**

| Scenario | Risk Captured |
|----------|---------------|
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
| USD, EUR, GBP, JPY, CHF | ±200 bps |
| Emerging markets | ±400 bps or higher |
| Low-rate environments | Adjusted for effective lower bound |

### 4.2 Historical Scenarios

#### **2008 Global Financial Crisis (GFC)**

**Characteristics:**
- Flight to quality → Treasury yields collapsed
- 10-Year Treasury: 4.0% (June 2008) → 2.2% (December 2008)
- Fed Funds: 5.25% → 0-0.25% (near ZIRP)
- Credit spreads widened dramatically

**Relevance for IRR:**
- Tests **parallel down** scenario with extreme magnitude
- Captures **basis risk** as spreads between indices diverged
- **Optionality risk:** Massive mortgage refinancing wave

#### **2022-2023 Rapid Rate Hike Cycle (SVB Collapse)**

**Characteristics:**
- Fed Funds: 0.25% (March 2022) → 5.25% (July 2023)
- Fastest hiking cycle in 40 years
- Yield curve inversion (2Y > 10Y for 18+ months)
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
| **Securities Duration** | 56% >15 years | Limit long-duration holdings |
| **HTM Accounting** | $15B unrealized loss not in AOCI | HTM losses are economically real |
| **Deposit Concentration** | 97% uninsured | Diversify funding base |
| **Hedging** | Minimal interest rate hedging | Actively hedge duration risk |

### 4.3 Hypothetical Scenarios

Hypothetical scenarios should be tailored to institution-specific risk profiles:

#### **Bank-Specific Worst-Case Models**

| Scenario Type | Description | Application |
|---------------|-------------|-------------|
| **Extreme Parallel Up** | +400 bps (beyond regulatory standard) | Test capital adequacy under severe stress |
| **Prolonged Low Rates** | Rates at 0-1% for 5+ years | Test business model viability |
| **Curve Inversion** | 2Y-10Y inversion of 200+ bps | Test NII compression from margin squeeze |
| **Basis Shock** | Prime-SOFR spread widens 150 bps | Test basis risk from index mismatch |
| **Deposit Beta Shock** | Deposit betas jump from 30% to 70% | Test funding cost sensitivity |

#### **Designing Effective Hypothetical Scenarios**

1. **Identify Key Vulnerabilities:** What rate moves would hurt this specific bank most?
2. **Consider Business Model:** Mortgage bank vs. commercial lender vs. consumer bank
3. **Incorporate Behavioral Assumptions:** How would customers actually respond?
4. **Include Management Actions:** What hedging or balance sheet actions would be taken?
5. **Link to Capital Planning:** What capital ratios result from each scenario?

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
Step 1: Define Failure Threshold
        ↓
Step 2: Model Current Position
        ↓
Step 3: Iteratively Increase Stress Severity
        ↓
Step 4: Identify Breaking Point
        ↓
Step 5: Assess Plausibility of Rate Move
        ↓
Step 6: Develop Mitigation Plans
```

#### **Example: Reverse Stress Test for EVE**

| Iteration | Rate Shock | EVE Decline | % of T1 Capital | Status |
|-----------|------------|-------------|-----------------|--------|
| 1 | +200 bps | -$50M | 10% | Pass |
| 2 | +300 bps | -$85M | 17% | Outlier |
| 3 | +400 bps | -$120M | 24% | Approaching Break |
| 4 | +450 bps | -$145M | 29% | **BREAK** |

**Result:** A +450 bps parallel shock would cause the bank to breach its risk appetite limit (25% of T1 Capital).

**Plausibility Assessment:** Is +450 bps plausible?
- Historical precedent: 1980s Volcker shock (+1000+ bps over 2 years)
- Recent precedent: 2022-2023 (+500 bps over 16 months)
- **Conclusion:** Plausible over multi-year horizon; mitigation required

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
| **2014** | BCBS publishes consultative document on IRRBB standards |
| **2016** | Final IRRBB standards issued (BCBS d368) |
| **2019** | Revisions to standardized shock scenarios |
| **2024** | BCBS d578 — Updated calibration and disclosure requirements |

#### **Two-Pillar Approach**

**Pillar 1 (Minimum Capital):**
- IRRBB is **not** subject to Pillar 1 minimum capital charges
- Remains under Pillar 2 (Supervisory Review)

**Pillar 2 (Supervisory Review):**
- Banks must have robust IRRBB measurement and management systems
- Supervisors evaluate adequacy of IRRBB frameworks
- Additional capital may be required if IRRBB is deemed inadequate

**Pillar 3 (Disclosure):**
- Public disclosure of IRRBB exposures and measurement results
- Enhances market discipline

#### **Key Regulatory Requirements**

| Requirement | Description |
|-------------|-------------|
| **Governance** | Board and senior management oversight of IRRBB |
| **Measurement** | EVE and NII under six standardized shocks |
| **Risk Limits** | Established limits for IRRBB exposures |
| **Stress Testing** | Regular stress testing beyond standardized shocks |
| **Model Validation** | Independent validation of IRRBB models |
| **Disclosure** | Pillar 3 public disclosures on IRRBB |

### 5.2 Disclosure Requirements (Pillar 3)

#### **Quantitative Disclosures**

Banks must disclose the following for each of the six standardized shocks:

| Metric | Description |
|--------|-------------|
| **ΔEVE** | Change in Economic Value of Equity (absolute and % of Tier 1 Capital) |
| **ΔNII** | Change in Net Interest Income over 12-month horizon |
| **Outlier Status** | Whether bank exceeds 15% of T1 Capital EVE decline threshold |

**Example Disclosure Format:**

| Scenario | ΔEVE ($M) | ΔEVE (% T1) | ΔNII ($M) | ΔNII (%) |
|----------|-----------|-------------|-----------|----------|
| Parallel Up | -$75 | -12% | +$15 | +8% |
| Parallel Down | +$45 | +7% | -$20 | -11% |
| Steepener | -$30 | -5% | +$8 | +4% |
| Flattener | -$20 | -3% | -$12 | -6% |
| Short Rate Up | -$40 | -6% | +$10 | +5% |
| Short Rate Down | +$25 | +4% | -$15 | -8% |

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
(Maximum ΔEVE across 6 shocks / Tier 1 Capital) > 15%
```

**Consequences of Outlier Status:**
1. **Enhanced Supervision:** Increased regulatory scrutiny and examination frequency
2. **Capital Add-On:** Supervisors may require additional Pillar 2 capital
3. **Remediation Plan:** Bank must develop and execute plan to reduce IRRBB
4. **Public Disclosure:** Outlier status disclosed in Pillar 3 report

#### **Internal Capital Adequacy Assessment Process (ICAAP)**

Banks must incorporate IRRBB into ICAAP:

- **Capital Planning:** Include IRRBB stress scenarios in capital forecasts
- **Risk Appetite:** Set IRRBB limits aligned with capital capacity
- **Recovery Planning:** Include IRRBB triggers in recovery plan indicators

---

### Key Takeaways: Regulatory Context

- **Basel III IRRBB** framework mandates EVE and NII measurement under six shocks
- **Pillar 2** (not Pillar 1) — supervisors evaluate adequacy and may require additional capital
- **15% of Tier 1 Capital** EVE decline triggers outlier status
- **Pillar 3 disclosures** require both quantitative results and qualitative methodology descriptions
- **ICAAP integration** ensures IRRBB is incorporated into capital planning

---

## 6. Mitigation and Hedging Strategies

### 6.1 Derivative Hedging Instruments

#### **Interest Rate Swaps**

**Definition:** An agreement to exchange fixed-rate payments for floating-rate payments (or vice versa) on a notional principal amount.

**Hedging Applications:**

| Position | Risk | Swap Strategy | Effect |
|----------|------|---------------|--------|
| **Fixed-Rate Assets** | Rates rise → value falls | Pay Fixed / Receive Float | Converts to floating; reduces duration |
| **Fixed-Rate Liabilities** | Rates fall → funding cost locked high | Receive Fixed / Pay Float | Converts to floating; benefits from rate decline |
| **Net Positive Duration Gap** | EVE falls when rates rise | Pay Fixed / Receive Float | Reduces overall duration gap |

**Example:** Bank has $100M of 5-year fixed-rate loans at 4%. To hedge against rising rates:
- Enter $100M notional 5-year swap
- Pay 4% fixed, receive SOFR floating
- If rates rise to 6%, swap payments increase, offsetting loan value decline

#### **Interest Rate Futures**

**Definition:** Exchange-traded contracts to buy/sell interest-bearing instruments at future dates at predetermined prices.

**Common Contracts:**
| Contract | Underlying | Duration | Use Case |
|----------|------------|----------|----------|
| **Eurodollar Futures** | 3-month LIBOR/SOFR | 0.25 years | Short-term rate hedging |
| **Treasury Futures** | 2Y, 5Y, 10Y, 30Y Treasury | Varies | Duration hedging |

**Advantages:**
- Highly liquid
- Transparent pricing
- No counterparty credit risk (cleared through exchange)

**Disadvantages:**
- Standardized contracts (may not match exact exposure)
- Daily margin requirements
- Basis risk vs. bank's actual positions

#### **Interest Rate Options**

**Definition:** Contracts giving the right (but not obligation) to enter into an interest rate transaction at specified terms.

| Option Type | Description | Hedging Use |
|-------------|-------------|-------------|
| **Interest Rate Cap** | Pays if reference rate exceeds strike | Hedge against rising funding costs |
| **Interest Rate Floor** | Pays if reference rate falls below strike | Hedge against falling asset yields |
| **Interest Rate Collar** | Long cap + short floor | Limit rate exposure within range; reduces cost |
| **Swaption** | Option to enter swap | Hedge future issuance or prepayment risk |

**Example — Interest Rate Cap:**
- Bank has $50M floating-rate liabilities tied to SOFR
- Concerned about rates rising above 5%
- Purchase $50M SOFR cap at 5% strike
- If SOFR rises to 7%, cap pays 2% × $50M = $1M annually

#### **Hedging EVE vs. Hedging NII**

| Objective | Preferred Instruments | Rationale |
|-----------|----------------------|-----------|
| **Hedge EVE** | Long-dated swaps, Treasury futures, swaptions | Match duration of long-term positions |
| **Hedge NII** | Short-dated swaps, Eurodollar futures, caps/floors | Match repricing horizon of earnings |

### 6.2 Balance Sheet Restructuring

#### **Product Mix Adjustments**

| Strategy | Implementation | IRR Impact |
|----------|----------------|------------|
| **Shift to Floating-Rate Loans** | Originate more ARMs, floating-rate commercial loans | Reduces asset duration; benefits from rising rates |
| **Extend Liability Duration** | Issue longer-term CDs, subordinated debt | Increases liability duration; reduces duration gap |
| **Securities Portfolio Rebalancing** | Reduce MBS duration; increase short-term Treasuries | Lowers overall asset duration |
| **Deposit Product Design** | Introduce rate-sensitive products with controlled betas | Manage deposit repricing behavior |

#### **Pricing Strategies**

| Strategy | Description | Risk Management Benefit |
|----------|-------------|------------------------|
| **Deposit Beta Management** | Set deposit rate policies to control funding cost sensitivity | Limits NII compression in rising rate environment |
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
| **ALCO Oversight** | Enhanced ALCO review of IRR metrics; frequent scenario analysis |

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
| Position | Balance ($M) | Avg. Rate | Duration (Years) |
|----------|--------------|-----------|------------------|
| Cash & Reserves | $50 | 0.5% | 0.0 |
| Securities (AFS) | $200 | 2.5% | 6.5 |
| Securities (HTM) | $150 | 2.0% | 8.0 |
| Commercial Loans (Fixed) | $300 | 5.0% | 3.5 |
| Commercial Loans (Float) | $200 | SOFR + 2% | 0.5 |
| Residential Mortgages | $250 | 3.5% | 5.0 |
| **Total Assets** | **$1,150** | **3.4%** | **4.2** |

**LIABILITIES & EQUITY**
| Position | Balance ($M) | Avg. Rate | Duration (Years) |
|----------|--------------|-----------|------------------|
| Demand Deposits | $300 | 0.1% | 0.5* |
| Savings Deposits | $250 | 0.5% | 1.0* |
| Money Market Deposits | $150 | 2.0% | 0.25 |
| CDs (<1 year) | $100 | 3.5% | 0.5 |
| CDs (>1 year) | $150 | 3.0% | 2.5 |
| FHLB Advances | $100 | 3.0% | 2.0 |
| Subordinated Debt | $50 | 4.5% | 5.0 |
| **Total Liabilities** | **$1,100** | **1.8%** | **1.3** |
| **Tier 1 Capital** | **$50** | — | — |
| **Total L&E** | **$1,150** | — | — |

*Behavioral duration for non-maturity deposits

**Key Metrics:**
- **Duration Gap:** 4.2 - (1,100/1,150 × 1.3) = **4.2 - 1.25 = 2.95 years** (positive)
- **Net Interest Margin:** 3.4% - 1.8% = **1.6%**
- **Annual NII:** $1,150M × 3.4% - $1,100M × 1.8% = $39.1M - $19.8M = **$19.3M**
- **Tier 1 Capital Ratio:** $50M / $1,150M = **4.35%** (simplified)

### 7.2 +200bps Parallel Shock Impact Analysis

#### **Step 1: Apply Rate Shock**

All interest rates increase by 200 basis points:

| Position | Current Rate | Shocked Rate |
|----------|--------------|--------------|
| Assets (weighted) | 3.4% | 5.4% |
| Liabilities (weighted) | 1.8% | 3.8% |
| Fed Funds / SOFR | ~5.0% | ~7.0% |

#### **Step 2: Calculate EVE Impact**

**Duration-Based Approximation:**

```
ΔEVE ≈ -Duration Gap × Total Assets × ΔYield
ΔEVE ≈ -2.95 × $1,150M × 0.02 = -$67.85M
```

**Detailed PV Calculation:**

| Component | Current PV ($M) | Shocked PV ($M) | Change ($M) |
|-----------|-----------------|-----------------|-------------|
| Assets | $1,120 | $1,035 | -$85 |
| Liabilities | $1,070 | $1,015 | -$55 |
| **EVE** | **$50** | **$20** | **-$30** |

*Note: Detailed PV calculation shows -$30M decline (less than duration approximation due to convexity and behavioral assumptions)*

**EVE Decline as % of Tier 1 Capital:**
```
($30M / $50M) × 100% = 60%
```

**Outlier Status:** **YES** — exceeds 15% threshold significantly

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

### 7.3 Risk Management Recommendations

Based on this analysis, the bank should consider:

| Action | Rationale | Expected Impact |
|--------|-----------|-----------------|
| **Reduce Securities Duration** | Sell long-duration AFS/HTM; reinvest in shorter maturities | Reduce duration gap from 2.95 to <2.0 |
| **Extend Liability Duration** | Issue 3-5 year CDs; extend FHLB advances | Increase liability duration to 2.0+ years |
| **Interest Rate Swaps** | Pay fixed on $200M notional 5-year swaps | Hedge ~$20M of asset duration |
| **Deposit Beta Review** | Analyze actual deposit repricing behavior | Refine NII projections; may show higher sensitivity |
| **HTM Reclassification** | Consider reclassifying some HTM to AFS | Increase transparency; may trigger AOCI impact |
| **Capital Raise** | Issue additional Tier 1 capital | Improve capital buffer against IRR losses |

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

| Term | Definition |
|------|------------|
| **AFS (Available-for-Sale)** | Securities carried at fair value with unrealized gains/losses in AOCI |
| **ALCO (Asset-Liability Committee)** | Senior management committee responsible for IRR and liquidity management |
| **AOCI (Accumulated Other Comprehensive Income)** | Balance sheet account where unrealized AFS gains/losses are recorded |
| **Basis Risk** | Risk from imperfect correlation between different rate indices |
| **Duration** | Measure of interest rate sensitivity; approximate % price change for 100bp rate move |
| **Duration Gap** | Difference between asset and liability durations, weighted by balance sheet size |
| **EVE (Economic Value of Equity)** | Present value of assets minus present value of liabilities |
| **HTM (Held-to-Maturity)** | Securities carried at amortized cost; unrealized gains/losses not in AOCI |
| **IRRBB** | Interest Rate Risk in the Banking Book |
| **NII (Net Interest Income)** | Interest income minus interest expense |
| **Optionality Risk** | Risk from embedded options that allow customers to alter cash flows |
| **Repricing Risk** | Risk from timing mismatches in asset and liability repricing |
| **VaR (Value at Risk)** | Statistical measure of potential loss at specified confidence level |
| **Yield Curve Risk** | Risk from changes in the shape or slope of the yield curve |

---

*This guide reflects regulatory standards and industry best practices as of early 2026. Banks should consult current regulatory guidance and qualified advisors for institution-specific applications.*
