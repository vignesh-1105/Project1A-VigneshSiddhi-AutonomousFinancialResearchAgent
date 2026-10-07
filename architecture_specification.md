# AUTONOMOUS FINANCIAL RESEARCH AGENT

Project 1A — Architecture Specification

Prepared for ZeTheta Project Work Experience Program

Architecture documentation prepared before implementation

1. Project Overview

The Autonomous Financial Research Agent is designed to automate the workflow normally followed by a junior financial analyst. The system receives a research question, decides what information is needed, gathers information from relevant financial and public sources, compares the findings, and produces a structured research report.

The project focuses on making the research process autonomous rather than requiring a person to guide every step. The agent is expected to decide which tools are useful, work through multiple research steps, use memory where appropriate, handle conflicting information, and produce a final report based on retrieved evidence.

The project is designed around a ReAct or Plan-and-Execute reasoning approach, a registry containing at least ten tools, three layers of memory, multi-source synthesis, error handling and an evaluation framework. The final system is intended to be tested through eight progressively difficult research challenges.

1.1 Problem Statement

Financial research often requires information to be collected from several sources before a useful conclusion can be made. A single question may require regulatory filings, financial figures, earnings information, news and company information. Doing this manually takes time and makes the process repetitive.

The proposed agent addresses this problem by coordinating these research activities through an autonomous workflow. Instead of simply answering from the language model's existing knowledge, the system is designed to retrieve relevant information, reason over the retrieved results and generate a report grounded in those findings.

1.2 Project Goal

The main goal is to design and build an autonomous financial research agent that can take a research query and carry out the major stages of a junior analyst's research workflow with minimal step-by-step human guidance.

2. Project Objectives

Design an autonomous agent architecture suitable for financial research.

Use a ReAct reasoning loop to guide research decisions and tool usage.

Provide a tool registry containing at least ten research-related tools.

Support short-term, long-term and episodic memory.

Retrieve information from multiple financial and public sources.

Combine information from different sources into a coherent set of findings.

Detect and handle conflicting information between sources.

Provide fallback and error-handling mechanisms when tools or data sources fail.

Generate a structured financial research report from the collected evidence.

Evaluate the quality and behaviour of the agent using a set of defined metrics.

Validate the system using eight research challenges of increasing difficulty.

3. Proposed System Architecture

The proposed architecture separates the agent into logical components. The user provides the research question. The query is interpreted by the agent, which uses the ReAct loop to decide what information is required and which tools should be called. Retrieved information is maintained through the memory system and passed to the synthesis stage. The synthesis component combines the findings and handles conflicts before the report generator produces the final output.

The architecture is designed so that the reasoning process is separated from individual data sources. The agent should select the most suitable tool for the information it needs and combine the resulting evidence before producing the final report.

4. ReAct Agent Architecture

The project allows either ReAct or Plan-and-Execute as the primary reasoning pattern. For this project, the proposed design uses ReAct because it fits a research workflow where the next action can depend on the result of the previous action.

In the ReAct approach, the agent moves through a repeated cycle of reasoning, action and observation. The agent considers the current research state, chooses an appropriate action such as calling a tool, receives the result and then decides what should happen next.

4.1 ReAct Cycle

Receive the research query.

Understand the research objective and identify missing information.

Consider the information already available in the current context and memory.

Select an appropriate research tool.

Execute the selected tool.

Process the returned observation.

Decide whether more information is required.

Repeat the cycle when additional research is necessary.

Send the collected findings to the synthesis stage when the research is sufficient.

Generate the final research report.

4.2 Termination

The agent should not continue researching indefinitely. The architecture therefore includes termination conditions. The research loop should stop when the required information has been collected, the available evidence is sufficient for the requested report, or a defined iteration or error limit has been reached.

5. Cognitive Loop

The cognitive loop is the central control flow of the system. It determines how a research question moves from an initial request to a final answer.

6. Tool Registry

The tool registry is the central catalog of tools available to the agent. Each tool should have a clear purpose, input requirements and expected output. The registry allows the agent to select tools according to the information it needs instead of calling tools randomly.

The project requires a minimum of ten tools. The proposed tool set follows the tool categories provided in the project specification.

6.1 Tool Selection

Tool selection should depend on the current research state. Before calling a tool, the agent should consider what information is already available, what information is missing, which tool is most likely to provide it and whether the required information may already exist in memory.

The design should avoid unnecessary or repetitive calls. If a required fact has already been retrieved from an authoritative filing, the agent should not repeatedly search for the same fact without a reason.

7. Memory Architecture

The agent uses three layers of memory. Each layer serves a different purpose. Together they allow the system to maintain the information needed during a research session, retain useful knowledge across sessions and record lessons from previous research experiences.

7.1 Short-Term Memory

Short-term memory represents the working context of the current research session. It contains the original research question, the actions taken by the agent, tool observations and important intermediate findings. Because the context available to the language model is limited, older information may need to be summarized or selectively retained.

7.2 Long-Term Memory

Long-term memory stores useful research knowledge across sessions. The project specification proposes a vector database for this purpose. Retrieved findings can be represented as embeddings and stored with useful metadata such as company ticker, source type, research date and confidence.

When a new research task begins, the agent can search this memory for relevant previous findings before making unnecessary external calls.

7.3 Episodic Memory

Episodic memory records the agent's previous research experiences. This includes which research strategies worked well, which tools were useful for particular tasks, what types of errors occurred and how those errors were handled. This allows the system to use previous experience when planning future research.

7.4 Interaction Between the Three Layers

Short-term memory supports the current task. Long-term memory provides relevant information from previous research. Episodic memory provides experience about previous research strategies and outcomes. The agent can use these sources when deciding what action to take next.

8. Data Sources and Retrieval

The agent is designed to work with several types of public and financial information. The project specifically identifies SEC EDGAR filings, financial data APIs, earnings-call transcripts, news feeds and web search as important sources.

Different sources provide different types of evidence. Regulatory filings can provide formal company disclosures, financial data services can provide structured figures, earnings transcripts can provide management commentary, and news or web sources can provide current developments and context.

8.1 Retrieval Flow

Identify the information required by the research query.

Select the most suitable source or tool.

Retrieve the information.

Record the source and relevant metadata.

Pass the result to the agent for observation and further reasoning.

Store useful findings where appropriate.

Use the collected evidence during synthesis.

9. Multi-Source Synthesis

The synthesis stage combines information collected from different sources into a single research view. The purpose is not simply to place all retrieved text into one response. The system should identify the useful information, connect related findings and preserve the source of important claims.

A research conclusion should be based on the available evidence rather than on unsupported statements generated by the language model.

9.1 Conflict Resolution

Detect when two or more sources provide conflicting information.

Identify the sources involved and the specific claim that conflicts.

Compare the reliability and relevance of the sources.

Prefer the source that provides stronger or more authoritative evidence for the claim.

Record the reasoning used to resolve the conflict.

Preserve uncertainty when the available evidence does not support a clear resolution.

## 10. Error Handling and Fallback Design

A financial research agent must be able to deal with failures because external tools and data sources may not always return usable results. The architecture therefore includes error handling and fallback chains.

## 11. Research Report Generation

The final output of the system is a structured financial research report. The report should present the main findings clearly and should make it possible to understand where important information came from.

The report generation stage should organize the results of the research rather than introduce unsupported information. Where evidence is incomplete or conflicting, the report should make that limitation clear.

11.1 Proposed Report Structure

Executive Summary

Company / Topic Overview

Financial Analysis

Key Findings

Competitive Positioning

Risk Assessment

Relevant Developments and News

Outlook / Forward-Looking Analysis

Sources and Evidence

## 12. Evaluation Framework

The project requires the agent to be evaluated using more than twenty quality metrics. The evaluation is intended to measure both the quality of the final research report and the behaviour of the agent while it performs the research.

The evaluation results will be completed after the working agent has been tested. This document defines the evaluation design and does not assign results before implementation.

## 13. Research Challenge Validation

The completed agent will be tested using eight progressive research challenges. The challenges are intended to increase in difficulty and test different parts of the system, including information retrieval, reasoning, synthesis, memory use and recovery from problems.

Each challenge will be documented separately after execution. The challenge documents will contain the actual research output and observations from the working system.

## 14. Security and Confidentiality

The project requires the work and related implementations to remain private and confidential. The repository should therefore be private throughout the project and should only contain authorized collaborators.

API keys should be stored through environment variables rather than directly in source files.

A .env.example file should contain placeholders rather than real credentials.

Sensitive credentials should never be committed to the repository.

The project repository should remain private.

Only authorized collaborators should have access to the repository.

The final repository should follow the transfer and submission requirements provided by ZeTheta.

## 15. Proposed Technology Stack

The final technology choices will be based on the implementation requirements and available tools. The project specification identifies Python, an LLM API such as OpenAI or Anthropic, an agent framework such as LangChain or LangGraph, a vector database such as Pinecone, Weaviate, Chroma or Qdrant, SEC EDGAR and financial data APIs as the relevant technology categories.

Only the technologies actually used in the final implementation will be recorded as the final stack.

## 16. Repository Organization

## 17. Implementation Roadmap

The project methodology divides the work into five stages.

This architecture specification represents the design that will guide the implementation. Details that depend on actual execution, such as evaluation scores, challenge results, traces and optimization results, will be added after the corresponding work is completed.

## 18. Architecture Summary

The proposed system is an autonomous financial research agent built around a ReAct reasoning loop. It receives a research question, checks available context and memory, selects appropriate tools, gathers information from multiple sources, evaluates the returned observations and continues the research until sufficient evidence has been collected.

The collected information is then passed through a multi-source synthesis and conflict-resolution process before being formatted as a structured research report. Three layers of memory support the workflow: short-term memory for the current session, long-term memory for reusable research knowledge and episodic memory for previous research experiences.

The architecture is designed to support reliable research behaviour, clear source grounding, controlled tool usage and measurable evaluation. The implementation and later evaluation stages will provide the actual results of this design.



| Stage | Flow |

| --- | --- |

| 1 | User Research Query |

| 2 | Query Understanding |

| 3 | ReAct Agent / Cognitive Loop |

| 4 | Tool Registry → External Financial and Public Sources |

| 5 | Three-Layer Memory ↔ Agent |

| 6 | Multi-Source Synthesis and Conflict Resolution |

| 7 | Structured Financial Research Report |



| Stage | Description |

| --- | --- |

| Input | Receive the user's research question. |

| Understand | Identify the company, topic, time period and research requirements. |

| Plan internally | Determine what information is missing and what should be investigated. |

| Check memory | Look for useful information from the current or previous research. |

| Select tool | Choose the tool most suitable for the current information need. |

| Execute | Call the selected tool and collect its result. |

| Observe | Review the returned information and identify what it contributes. |

| Continue or stop | Decide whether another research step is required. |

| Synthesize | Combine the useful findings from the completed research. |

| Report | Produce the final structured financial research report. |



| Tool | Purpose |

| --- | --- |

| SEC Filing Search | Retrieve SEC filings such as 10-K, 10-Q, 8-K and other relevant filings. |

| Financial Data API | Retrieve financial figures and related market or company data. |

| Web Search | Find current public information, analysis and commentary. |

| News / Sentiment | Retrieve and analyse relevant news information. |

| Earnings | Retrieve earnings-call or transcript information. |

| Company Profile | Retrieve basic company information. |

| Peer Comparison | Compare a company with selected peer companies. |

| Calculator | Perform financial calculations and quantitative analysis. |

| Fact Checker | Cross-check important claims against available sources. |

| Report Generator | Format the final findings into a structured research report. |



| Situation | Expected Response |

| --- | --- |

| Tool failure | Record the failure and attempt an appropriate fallback when available. |

| Empty result | Check the query or use another suitable source. |

| Invalid input | Validate the input and use a corrected form where possible. |

| Rate limit | Use retry or a fallback source according to the configured policy. |

| Invalid model response | Validate the response and retry or terminate safely. |

| Conflicting evidence | Send the evidence to the conflict-resolution process. |

| Repeated failure | Stop the affected operation safely and report the limitation. |



| Evaluation Area | Examples |

| --- | --- |

| Factual Accuracy | Numerical accuracy, citation accuracy, temporal accuracy, entity accuracy and hallucination rate. |

| Completeness | Section coverage, source diversity, temporal coverage and risk-factor coverage. |

| Analytical Depth | Insight density, cross-source synthesis, quantitative reasoning and forward-looking analysis. |

| Coherence and Structure | Logical flow, internal consistency, executive summary quality and professional formatting. |

| Agent Behaviour | Tool efficiency, error recovery, planning quality and memory utilization. |



| Area | Technology / Option |

| --- | --- |

| Programming Language | Python |

| LLM | OpenAI or Anthropic API |

| Agent Framework | LangChain / LangGraph |

| Vector Database | Chroma / Pinecone / Weaviate / Qdrant |

| Regulatory Data | SEC EDGAR |

| Financial Data | Financial data API |

| Web / News Data | Web and news search tools |



| Directory / File | Purpose |

| --- | --- |

| README.md | Project overview and setup instructions. |

| agent/ | Core agent logic, prompts, parsing and error handling. |

| tools/ | Tool registry, schemas and individual research tools. |

| memory/ | Vector storage, context management and episodic memory. |

| synthesis/ | Synthesis, conflict resolution and narrative generation. |

| evaluation/ | Metrics, benchmarks and evaluation dashboard. |

| results/ | Outputs from the eight research challenges. |

| ERROR_LOG.md | Documentation of the deliberate errors identified in the project document. |

| .env.example | Example environment variables without real credentials. |

| requirements.txt | Python dependencies. |



| Stage | Days | Focus |

| --- | --- | --- |

| Foundation | 1–3 | Architecture design, tool registry and environment setup. |

| Core Build | 4–7 | Agent core, tools and memory system. |

| Integration | 8–10 | Multi-source synthesis and error handling. |

| Evaluation | 11–13 | Testing, benchmarking and optimization. |

| Delivery | 14–15 | Documentation, presentation and submission. |
