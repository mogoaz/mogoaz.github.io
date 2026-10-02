---
layout: portfolio
title: Connecting Independent Scanners Into One Security Signal
permalink: /labs/pipeline-scanner/
---

<section class="portfolio-section">

  <div class="portfolio-container">

    <span class="portfolio-label">
      Lab Challenge
    </span>

    <h2>
      Connecting Independent Scanners Into One Security Signal
    </h2>

    <p class="portfolio-description">

      Part of building out the
      <a
        href="/projects/pipeline-security/"
        style="color: var(--blue); text-decoration: underline;"
      >security pipeline scanner</a>: getting static analysis,
      dependency scanning, and secrets detection running was the
      easy part. The real problem was that four separate tools
      produce four separate pictures of risk, and dynamic testing
      can't even run the same way the others do.

    </p>


    <div style="margin-top: 40px;">

      <h2>
        Problem Statement
      </h2>

      <p class="portfolio-description">

        The pipeline needed static analysis (SAST), dependency
        scanning (SCA), and secrets detection running on every
        push, plus dynamic testing (DAST) against a running
        application. Each tool does its job well in isolation, but
        a reviewer checking four separate scanner outputs to judge
        whether a build is safe to ship doesn't scale, and DAST in
        particular couldn't be wired in the same way as the others.

      </p>

    </div>


    <div style="margin-top: 40px;">

      <h2>
        Approach
      </h2>

      <h3 style="color: var(--heading); font-size: 1.05rem; margin: 28px 0 10px;">
        Phase 1 · Static Coverage First
      </h3>

      <p class="portfolio-description">

        Semgrep was wired in for static analysis, Trivy for
        dependency and container scanning, and a secrets scanner
        for anything committed that shouldn't be. Each runs per
        push as a GitHub Actions step and produces a JSON report.
        Straightforward to add, and immediately useful on its own.

      </p>


      <h3 style="color: var(--heading); font-size: 1.05rem; margin: 28px 0 10px;">
        Phase 2 · DAST Needs a Target, Not Just a Step
      </h3>

      <p class="portfolio-description">

        Dynamic testing works differently from the rest: it
        doesn't analyze source, it attacks a running instance of
        the application the way a real attacker would. That means
        it can't just be dropped into the same pipeline step as
        the others, it needs a live, attackable deployment to point
        at. OWASP ZAP was set up to run against a dedicated staging
        environment rather than anything resembling production,
        with its own automation step separate from the static
        scanners.

      </p>


      <h3 style="color: var(--heading); font-size: 1.05rem; margin: 28px 0 10px;">
        Phase 3 · One Signal Instead of Four Dashboards
      </h3>

      <p class="portfolio-description">

        With four tools running, the next problem was making the
        output usable. Each scanner's JSON report was routed into
        a single downstream feed, so a reviewer (or the SIEM)
        gets one consolidated view of a build's risk instead of
        needing to separately check four tools' own dashboards.
        The scanning mattered less than making the results
        actually get looked at.

      </p>

    </div>


    <div style="margin-top: 40px;">

      <h2>
        Tools Used
      </h2>

      <div class="portfolio-tags">

        <span class="portfolio-tag">Semgrep</span>
        <span class="portfolio-tag">Trivy</span>
        <span class="portfolio-tag">Secrets Scanning</span>
        <span class="portfolio-tag">OWASP ZAP</span>
        <span class="portfolio-tag">GitHub Actions</span>

      </div>

    </div>


    <div style="margin-top: 40px;">

      <h2>
        Key Lessons Learned
      </h2>

      <p class="portfolio-description">

        SAST, SCA, secrets scanning, and DAST test fundamentally
        different things, source code, dependencies, committed
        history, and live runtime behavior, and treating them as
        interchangeable "security scanning" steps misses that each
        needs its own setup. DAST in particular is easy to
        underestimate: it needs real, dedicated infrastructure, not
        just another line in a CI config.

      </p>

      <p class="portfolio-description">

        Just as important: running the scans isn't the finish
        line. Four tools producing four reports nobody reads
        consistently isn't meaningfully safer than running none of
        them. Consolidating the signal into one place was what
        actually made the scanning useful day to day.

      </p>

    </div>

  </div>

</section>
