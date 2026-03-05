# Optimal Portfolio Allocation using CAPM

**CAPM 기반 포트폴리오 최적화 (Sharpe Ratio 최대화)**  

This project constructs an optimal portfolio under **CAPM / Modern Portfolio Theory (MPT)** assumptions by estimating **expected returns** and the **covariance matrix**, then searching for the allocation that maximizes the **Sharpe ratio**.

금융 데이터를 이용하여 **기대수익률과 공분산 구조를 추정하고**,  
Sharpe Ratio를 기준으로 **최적 자산 배분(Optimal Portfolio)**을 찾는 프로젝트입니다.

---

# 1. Motivation | 연구 동기

Financial markets can be analyzed through **mathematics, probability, and statistical modeling**.  
This project explores how **risk and return** can be quantified and optimized using classical portfolio theory.

금융시장은 **수학적 모델링과 통계적 분석**을 통해 이해할 수 있습니다.  
본 프로젝트는 **위험과 수익의 관계를 정량적으로 분석하고 최적 자산배분을 찾는 과정**을 탐구합니다.

---

# 2. Problem Statement | 문제 정의

Given return data of several assets, we estimate

- Expected return vector \( \mu \)
- Covariance matrix \( \Sigma \)

and find the portfolio weights \( w \) that maximize the Sharpe ratio.

주어진 자산 수익률 데이터를 기반으로

- 기대수익률 벡터 \( \mu \)
- 공분산 행렬 \( \Sigma \)

를 추정한 뒤, 아래 목적함수를 최대화하는 포트폴리오 가중치 \( w^\* \)를 찾습니다.

\[
\max_{w} \quad \text{Sharpe}(w)=\frac{E[R_p]-r_f}{\sigma_p}
\]

\[
R_p = w^\top R,\quad \sigma_p=\sqrt{w^\top \Sigma w}
\]

Goal: **maximize risk-adjusted return.**

---

# 3. Dataset | 데이터

Example configuration:

- **Period:** historical market data
- **Assets:** selected stocks / indices
- **Frequency:** daily returns
- **Source:** Yahoo Finance (via `yfinance`)

가격 데이터를 수집한 뒤 **수익률 데이터로 변환**하여 분석에 사용합니다.

---

# 4. Mathematical Background | 수학적 배경

Key concepts used in this project:

- Expected Return  
- Variance / Covariance  
- Portfolio Return & Volatility  
- Sharpe Ratio  
- CAPM intuition (risk–return trade-off)

금융수학 및 포트폴리오 이론의 핵심 개념을 기반으로 분석합니다.

---

# 5. Methodology | 분석 방법

## Step 1 — Data Preprocessing
- Download historical price data
- Handle missing values
- Compute asset returns

수익률 계산:

\[
r_t = \ln\left(\frac{P_t}{P_{t-1}}\right)
\]

또는 단순수익률을 사용합니다.

---

## Step 2 — Estimate \( \mu \) and \( \Sigma \)

- Expected return vector \( \mu \)
- Covariance matrix \( \Sigma \)

자산 수익률의 평균과 공분산을 추정합니다.

---

## Step 3 — Monte Carlo Portfolio Simulation

- Generate random portfolio weights
- Compute return, volatility, and Sharpe ratio
- Repeat simulation **N times**

Example:

N = 10,000

Monte Carlo 시뮬레이션을 통해 다양한 포트폴리오 조합을 생성합니다.

---

## Step 4 — Optimal Portfolio Selection

Select the portfolio with the **maximum Sharpe ratio**.

Sharpe Ratio가 가장 높은 포트폴리오를 **최적 포트폴리오**로 선택합니다.

---

# 6. Results | 결과

## Efficient Frontier

The efficient frontier shows the trade-off between **expected return and volatility**.

위험(변동성)과 기대수익률 사이의 관계를 시각화합니다.

![Efficient Frontier](assets/efficient_frontier.png)

---

## Capital Market Line

The capital market line represents the optimal risk–return combination.

![CML](assets/cml.png)

---

## Optimal Portfolio

| Asset | Weight |
|------:|------:|
| Asset A | 0.xx |
| Asset B | 0.xx |
| Asset C | 0.xx |

Example statistics:

- **Max Sharpe Ratio:** x.xx  
- **Expected Return:** x.xx  
- **Volatility:** x.xx  
- **Risk-free rate:** x.xx

---

# 7. Interpretation | 해석

The results illustrate that under CAPM/MPT assumptions, there exists a portfolio that maximizes **risk-adjusted return**.

CAPM 및 MPT 가정 하에서는 **위험 대비 수익이 가장 효율적인 포트폴리오**가 존재하며,  
이는 Efficient Frontier 상의 **최적 지점(Tangency Portfolio)**으로 해석됩니다.

---

# 8. Limitations | 한계

- Strong CAPM assumptions  
- Historical estimation bias  
- Ignoring transaction costs and market impact  

CAPM 모델의 가정과 데이터 기반 추정에는 한계가 존재합니다.

---

# 9. Future Work | 향후 연구

Possible improvements:

- Robust covariance estimation
- **Black–Litterman model**
- **Regime switching / GARCH volatility**
- Transaction cost modeling
- Out-of-sample backtesting

보다 현실적인 포트폴리오 모델을 구축하기 위한 확장이 가능합니다.

---

# 10. How to Run

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
