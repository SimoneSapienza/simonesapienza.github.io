---
layout: landing
title: "Simone Sapienza"
subtitle: "Cloud & AI Engineer — Technical Project Leader"

# FEATURED PROJECTS
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
    url: "/raven-iq-test/"
    btn_label: "View project overview"
    btn_class: "btn--primary"

# SKILLS / EXPERTISE
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

# HIGHLIGHTS
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

# CALL TO ACTION
cta_row:
  - title: "Let’s talk about real-time systems, AI, and architecture"
    excerpt: >
      I enjoy discussing complex systems: from market data streams and ML pipelines to mobile clients and field devices.
      If you’d like to talk about architecture, trading systems, or applied AI, feel free to reach out on LinkedIn
      or explore my work on GitHub.
    url: "https://www.linkedin.com/in/simone-sapienza-091a04169/"
    btn_label: "Connect on LinkedIn"
    btn_class: "btn--primary"
---

<section class="section hero-section">
  <div class="section-inner hero-inner">
    <h1>{{ page.title }}</h1>
    <h3 class="hero-subtitle">{{ page.subtitle }}</h3>
    <p class="lead">
      I design and build real-time, data-driven systems — from algorithmic trading engines
      to mobile and cloud applications. My work combines hands-on engineering with system
      architecture, machine learning, and real-world production constraints.
    </p>
  </div>
</section>

<section class="section section-light" id="projects">
  <div class="section-inner">
    <h2>Projects</h2>
    <p class="section-intro">
      A selection of projects that represent my work in terms of architecture, scalability,
      and real-world impact.
    </p>
    {% include feature_row id="feature_row" %}
  </div>
</section>

<section class="section" id="whatido">
  <div class="section-inner">
    <h2>What I Do</h2>
    <p class="section-intro">
      I work across the full stack of data-intensive systems: from real-time data ingestion
      and ML-driven decision engines to mobile clients and industrial field applications.
    </p>
    {% include feature_row id="skills_row" %}
  </div>
</section>

<section class="section section-dark" id="highlights">
  <div class="section-inner">
    <h2>Highlights</h2>
    <p class="section-intro">
      A quick overview of my experience, the types of systems I build, and the technologies
      I’m most comfortable with.
    </p>
    {% include feature_row id="highlights" %}
  </div>
</section>

<section class="section section-light" id="contact">
  <div class="section-inner">
    <h2>Contact</h2>
    <p class="section-intro">
      I’m always interested in technical conversations around real-time architectures, trading systems,
      and applied AI. Feel free to connect on LinkedIn or explore my work on GitHub.
    </p>
    {% include feature_row id="cta_row" type="center" %}
  </div>
</section>
