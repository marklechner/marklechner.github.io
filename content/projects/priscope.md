+++
draft = false
date = '2024-10-20T18:00:00+01:00'
title = 'PRIscope'
+++

{{< figure src="/images/priscope.png" alt="priscope" caption="priscope" width="800px" >}}

## AI-Powered Security Analysis for Open Source Dependencies
### The Challenge
Software supply chain security has become one of the most critical challenges in modern software development. While the open-source community brings immense value through shared knowledge and collaborative development, it also introduces significant risks. Every merged pull request in an open-source project could potentially contain malicious code, backdoors, or security vulnerabilities that might go unnoticed during regular code reviews.

### The Solution
PRIscope is an attempt to see if and how AI could help address this challenge. It's a proof-of-concept tool that combines traditional code analysis with AI capabilities to provide an additional layer of security oversight for open-source projects.

The tool's core functionality is straightforward:
* Fetches recent merged pull requests from in-scope GitHub repositories
* Analyzes code changes using the Mistral small language model (or whatever is configured via ollama)
* Flags potential security concerns
* Provides clear, actionable summaries of findings

### Why I Built It
While working in various security leadership roles, I've witnessed firsthand how challenging it can be to keep track of open-source software we are dependent on fro cirtical/core business functionality. Traditional security tools are excellent at finding known vulnerabilities, but they often miss subtle, contextual security issues that could be introduced through seemingly innocent code changes.

PRIscope represents an initial attempt at leveraging AI to democratize security analysis. It's designed to be simple enough for individual developers to use in their daily work, yet informative enough to provide valuable insights for security teams.

### Current State
PRIscope is currently available as an open-source project, running with local AI models through Ollama for enhanced privacy, control and cost. While it's still in its early stages, the tool has already demonstrated promising results in identifying suspicious code patterns and potential security concerns.

I welcome feedback, contributions, and discussions about how we can better secure our software supply chains. You can find the full source code and documentation on GitHub [here](https://github.com/marklechner/priscope)
