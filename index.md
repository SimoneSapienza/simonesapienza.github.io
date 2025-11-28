---
layout: splash
permalink: /
title: "Simone Sapienza"
subtitle: "Cloud & AI Engineer — Technical Project Leader"
author_profile: true

header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/overlay.jpg # opzionale, puoi cambiarla o rimuoverla
  actions:
    - label: "View GitHub"
      url: "https://github.com/simonesapienza"
    - label: "View LinkedIn"
      url: "https://www.linkedin.com/in/simone-sapienza/"

intro:
  - excerpt: >
      I design and build real-time, data-driven systems — from algorithmic trading engines to mobile and cloud applications.
      My work combines hands-on engineering with system architecture, machine learning, and production constraints.

feature_row:
  - title: "PulseTrader – AI-Driven Crypto Trading Engine"
    excerpt: >
      End-to-end crypto trading system built around real-time market data, technical indicators, and ML models
      (XGBoost, LSTM). Handles WebSocket streams, feature engineering, model inference, risk controls, and
      automated order execution on Binance.
    url: "/pulsetrader/"
    btn_label: "View project overview"
    btn_class: "btn--primary"
  - title: "IQ Test – Raven Matrices (130k+ downloads)"
    excerpt: >
      Android application implementing Raven’s Progressive Matrices–style IQ tests, with over 130,000 downloads
      on Google Play. Includes test logic, scoring, persistence, and a smooth UX optimized for mobile users.
    url: "https://play.google.com" # replace with your real Play Store link
    btn_label: "View on Google Play"
    btn_class: "btn--primary"

skills_row:
  - title: "Cloud & Backend Engineering"
    excerpt: >
      Designing and implementing APIs and backends for data-intensive, real-time systems using .NET, Python, Java,
      REST, WebSockets, and containerized services.
  - title: "AI, ML & Trading Systems"
    excerpt: >
      Building ML-driven engines with XGBoost, LSTM, feature engineering, backtesting, and model optimization
      (Optuna, SHAP) for high-frequency, micro-profit strategies.
  - title: "Mobile & Field Applications"
    excerpt: >
      Developing mobile apps (Android, Xamarin, .NET MAUI) that interact with sensors, Bluetooth LE devices,
      and real-world industrial workflows.

highlights:
  - title: "Experience & Focus"
    excerpt: >
      7+ years of experience as a Cloud & Mobile Project Leader, working on end-to-end solutions from requirements
      to production, with a strong focus on reliability, performance, and maintainability.
  - title: "Systems I Build"
    excerpt: >
      Real-time trading engines, inspection and data collection apps, BLE-based machine interfaces, cloud-backed
      dashboards, and mobile products used by thousands of users.
  - title: "Tech Stack"
    excerpt: >
      .NET, C#, Python, Java, Android, .NET MAUI, WebSockets, REST APIs, MySQL, InfluxDB, Docker, Git, CI/CD,
      XGBoost, LSTM, time-series modeling, technical indicators, and data pipelines.

cta_row:
  - title: "Let’s talk about real-time systems, AI, and architecture"
    excerpt: >
      I enjoy discussing complex systems: from market data streams and ML pipelines to mobile clients and field devices.
      If you’d like to talk about architecture, trading systems, or applied AI, feel free to reach out on LinkedIn
      or explore my work on GitHub.
    url: "https://www.linkedin.com/in/simone-sapienza/"
    btn_label: "Connect on LinkedIn"
    btn_class: "btn--primary"
---

{% include feature_row id="intro" type="center" %}

<h2 id="projects">Projects</h2>

{% include feature_row id="feature_row" %}

<h2 id="whatido">What I Do</h2>

{% include feature_row id="skills_row" %}

<h2 id="highlights">Highlights</h2>

{% include feature_row id="highlights" %}

<h2 id="contact">Contact</h2>

{% include feature_row id="cta_row" type="center" %}
