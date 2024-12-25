+++
date = '2024-12-17T18:00:00+01:00'
draft = false
title = 'Raven'
+++

{{< figure src="/images/raven.png" alt="raven" caption="raven" width="800px" >}}

## AI-Powered Security News Analysis
### The Challenge
Security teams face a constant deluge of security news, updates, and potential threats. With the chronic shortage of security talent and the ever-increasing volume of security information, it's becoming more and more difficult to efficiently filter and prioritize what's truly relevant for an organization given their industry and/or the tech stack they operate with. Traditional news aggregators lack the contextual understanding to effectively determine which security updates actually matter for a specific company's technology stack and security posture.

### The Solution
Raven comes from the idea of using LLMs to augment security teams' analytical capabilities. Think of it as having a tireless security analyst who excels at:
* Reading and analyzing security news from trusted sources
* Understanding your organization's technical context
* Filtering out irrelevant noise
* Delivering concise, actionated intelligence

The tool effectively serves as an AI-powered threat intelligence analyst that never sleeps, consistently monitoring and analyzing security news from sources like The Record by Recorded Future and The Risky Business Podcast.

### Why I Built It
Working in security leadership, I've observed how much time security teams would need to spend on routine analytical tasks that, while crucial, take away from more complex security work that requires human expertise. With recent advances in LLMs and their improving ability to understand context, I saw an opportunity to create a tool that could handle this initial analysis and filtering.

### How It Works
Raven uses a two-stage analysis process:
1) First, it collects news from configured sources
2) Then, it uses locally-running LLMs to analyze each item against your organization's profile
3) The profile, managed as config, includes your tech stack, compliance requirements, and critical dependencies
4) Finally, it delivers only the relevant updates, with optional deduplication across sources

The system is designed to be:
* Cost-effective (uses local LLMs)
* Extensible framework (easy to add new sources)
* Configurable (adaptable to your organization's needs)
* Privacy-conscious (runs entirely locally)

### Current State
Raven is available as an open-source project, and I welcome contributions from the community. Whether it's adding new news sources, improving the analysis capabilities, or enhancing the delivery mechanisms, there's plenty of room for collaboration.
You can find the full source code and documentation on GitHub [here](https://github.com/marklechner/raven)