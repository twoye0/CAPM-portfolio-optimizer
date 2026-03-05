# Optimal Portfolio Allocation using CAPM

**CAPM 기반 포트폴리오 최적화 (Sharpe Ratio 최대화)**  

This project constructs an optimal portfolio under **Modern Portfolio Theory (MPT)** assumptions by estimating **expected returns** and the **covariance matrix**, then searching for the allocation that maximizes the **Sharpe ratio**.

금융 데이터를 이용하여 **기대수익률과 공분산 구조를 추정하고**,  
Sharpe Ratio를 기준으로 **최적 자산 배분(Optimal Portfolio)** 을 찾는 프로젝트입니다.

---

# Motivation | 연구 동기

Financial markets can be analyzed through **mathematics, probability, and statistical modeling**.  
This project explores how **risk and return** can be quantified and optimized using classical portfolio theory.

금융시장은 **수학적 모델링과 통계적 분석**을 통해 이해할 수 있습니다.  
본 프로젝트는 **위험과 수익의 관계를 정량적으로 분석하고 최적 자산배분을 찾는 과정**을 탐구합니다.

---

# Optimization Problem | 최적화 문제

We estimate expected returns and covariance matrix from asset return data and find portfolio weights that maximize the Sharpe ratio.

주어진 자산 수익률 데이터를 기반으로 **Sharpe Ratio를 최대화하는 포트폴리오 가중치**를 찾습니다.

### Sharpe Ratio Maximization

<img src="https://latex.codecogs.com/svg.image?\max_{w}\;Sharpe(w)=\frac{E[R_p]-r_f}{\sigma_p}" />

where

<img src="https://latex.codecogs.com/svg.image?R_p=w^{\top}R" />

<img src="https://latex.codecogs.com/svg.image?\sigma_p=\sqrt{w^{\top}\Sigma w}" />

---

# Dataset | 데이터

Example configuration:

- **Period:** historical market data  
- **Assets:** selected stocks or indices  
- **Frequency:** daily returns  
- **Source:** Yahoo Finance (`yfinance`)  

가격 데이터를 수집한 뒤 **수익률 데이터로 변환하여 분석**합니다.

---

# Methodology | 분석 방법

## Step 1 — Data Preprocessing

- Download price data
- Handle missing values
- Compute asset returns

수익률 계산

<img src="https://latex.codecogs.com/svg.image?r_t=\ln\left(\frac{P_t}{P_{t-1}}\right)" />

---

## Step 2 — Estimate Expected Return & Covariance

- Expected return vector \( \mu \)  
- Covariance matrix \( \Sigma \)

자산 수익률의 평균과 공분산을 계산합니다.

---

## Step 3 — Monte Carlo Portfolio Simulation

- Generate random portfolio weights  
- Compute return, volatility, and Sharpe ratio  
- Repeat simulation many times  

Example:

N = 10000

Monte Carlo 시뮬레이션을 통해 다양한 포트폴리오 조합을 생성합니다.

---

## Step 4 — Select Optimal Portfolio

The portfolio with the **highest Sharpe ratio** is selected as the optimal portfolio.

Sharpe Ratio가 가장 높은 포트폴리오를 **최적 포트폴리오**로 선택합니다.

---

# Results | 결과

## Efficient Frontier

The efficient frontier shows the relationship between **expected return and volatility**.

위험(변동성)과 기대수익률 사이의 관계를 시각화합니다.

![Efficient Frontier](assets/efficient_frontier.png)

---

## Capital Market Line

The capital market line represents the optimal risk-return tradeoff.

![CML](assets/cml.png)

---

# Interpretation | 해석

The results illustrate that under CAPM/MPT assumptions, there exists a portfolio that maximizes **risk-adjusted return**.

CAPM 가정 하에서는 **위험 대비 수익이 가장 효율적인 포트폴리오**가 존재하며  
이는 Efficient Frontier 상의 **Tangency Portfolio**로 해석됩니다.

---

# Limitations | 한계

- Strong CAPM assumptions  
- Historical estimation bias  
- Ignoring transaction costs  

CAPM 모델과 과거 데이터 기반 추정에는 한계가 존재합니다.

---

# Future Work | 향후 연구

Possible improvements:

- Robust covariance estimation  
- Black–Litterman model  
- GARCH volatility modeling  
- Transaction cost modeling  
- Out-of-sample backtesting  

보다 현실적인 포트폴리오 모델로 확장할 수 있습니다.

---

# How to Run

python -m venv .venv  
source .venv/bin/activate  
pip install -r requirements.txt  
jupyter notebook  

---

# Tech Stack

- Python  
- NumPy  
- Pandas  
- Matplotlib  
- yfinance  

---

# Author

Financial Mathematics Student  
Interested in **Quantitative Finance, Mathematical Modeling, and Systematic Trading**
