---
layout: portfolio
title: Network Monitoring Agent
permalink: /projects/network-monitoring/
---

<section class="portfolio-section">

  <div class="portfolio-container">

    <span class="portfolio-label">
      Network Engineering
    </span>

    <h2>
      Network Monitoring Agent
    </h2>

    <p class="portfolio-description">

      A network performance monitoring agent built to collect
      telemetry across availability, traffic, DNS, sockets, and
      interfaces, exposed through a REST API for integration
      with other systems.

    </p>


    <div style="margin-top: 40px;">

      <h2>
        The Challenge
      </h2>

      <p class="portfolio-description">

        Network problems, like latency spikes, packet loss, or DNS
        resolution failures, often show up first as vague user
        complaints, with no easy way to correlate them to what's
        actually happening at the network layer in real time.
        Off-the-shelf tools either cost more than the problem
        warranted or didn't expose the specific telemetry needed.

      </p>

    </div>


    <div class="portfolio-grid">


      <article class="portfolio-card">

        <span class="portfolio-card-number">
          01
        </span>

        <h3>
          Telemetry Collection
        </h3>

        <p>

          Agent-based collection of network availability,
          traffic, DNS, socket, and interface metrics.

        </p>

      </article>


      <article class="portfolio-card">

        <span class="portfolio-card-number">
          02
        </span>

        <h3>
          Active Probing
        </h3>

        <p>

          Scheduled probing to measure reachability and
          performance across monitored targets.

        </p>

      </article>


      <article class="portfolio-card">

        <span class="portfolio-card-number">
          03
        </span>

        <h3>
          API-Driven Integration
        </h3>

        <p>

          A REST API and PostgreSQL-backed store for querying
          and integrating collected telemetry.

        </p>

      </article>

    </div>


    <div style="margin-top: 70px;">

      <h2>
        How It Works
      </h2>

      <p class="portfolio-description">

        The agent, written in Go, runs on monitored
        infrastructure and combines two approaches: active
        probing (scheduled checks against key targets to
        measure reachability and latency) with passive
        observation of local network interfaces, socket state,
        and DNS resolution. Collected telemetry is persisted to
        PostgreSQL and exposed through a REST API, so it can be
        queried directly or wired into dashboards and alerting
        elsewhere.

      </p>

    </div>


    <div style="margin-top: 70px;">

      <h2>
        Technologies
      </h2>

      <div class="portfolio-tags">

        <span class="portfolio-tag">Go</span>
        <span class="portfolio-tag">Network</span>
        <span class="portfolio-tag">PostgreSQL</span>
        <span class="portfolio-tag">REST API</span>

      </div>

    </div>


    <div style="margin-top: 70px;">

      <h2>
        What I learned
      </h2>

      <p class="portfolio-description">

        Building this agent deepened my understanding of
        network telemetry collection, probing design, and how
        to expose monitoring data through a well-structured API.

      </p>

      <p class="portfolio-description">

        Writing it in Go also forced discipline around
        concurrency. Probing dozens of targets on independent
        schedules without one slow check blocking the rest meant
        thinking carefully about goroutines, timeouts, and
        failure isolation from the start.

      </p>

    </div>

  </div>

</section>
