<h1 align="center">Snehangshu Roy</h1>

<p align="center">
  Systems + AI engineer &nbsp;·&nbsp; Rust/C++ trading infrastructure &nbsp;·&nbsp; Python AI agents &nbsp;·&nbsp; cloud infra<br/>
  CS @ Scaler School of Technology ('28) &nbsp;·&nbsp; <b>open to contract and freelance work</b>
</p>

<p align="center">
  <a href="https://snehangshu-roy-portfolio.vercel.app/"><img src="https://img.shields.io/badge/Portfolio-161b22?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio"/></a>
  <a href="https://www.linkedin.com/in/snehangshu-roy/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge" alt="LinkedIn"/></a>
  <a href="https://x.com/SnehangshuRoy15"><img src="https://img.shields.io/badge/X-161b22?style=for-the-badge&logo=x&logoColor=white" alt="X"/></a>
  <a href="mailto:snehangshu.roy.mail@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/></a>
</p>

---

I like building systems where correctness is checked, not assumed: a trading engine where backtest, paper and live run the same code path, a document pipeline that survives worker restarts, and infrastructure that can be destroyed and rebuilt from Terraform.

## Flagship: [quant](https://github.com/alienxviking/quant)

A quantitative trading platform in Rust. It captures market data, replays it deterministically, and runs **one strategy binary across backtest, paper and live trading with no code changes**.

- 12-crate workspace and ~400 commits: recorder, order-book reconstruction, Parquet normalization, engine, simulated venue and an offline verifier
- Money is fixed-point `i64`; float arithmetic is denied by clippy across the whole workspace
- Every event carries two timestamps and only receive time is dispatched on, so lookahead bias can't get in
- Feed gaps are recorded as events, and a mandatory risk layer sits between every strategy and every venue

## Other work

<table>
  <tr>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/alienxviking/sift">sift</a></h3>
      Document processing and hybrid search. Uploads (PDF, images, DOCX) go to Celery workers for text extraction, OCR, thumbnails and local embeddings, then become searchable through Postgres full-text + pgvector. Multi-tenant, with live status over WebSockets.<br/><br/>
      <code>FastAPI</code> <code>Next.js</code> <code>Celery</code> <code>pgvector</code> &nbsp;·&nbsp; <a href="https://sift-docprocess.vercel.app/">live</a>
    </td>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/alienxviking/web-automation-agent">web-automation-agent</a></h3>
      A browser agent that works from screenshots instead of CSS selectors. A vision LLM looks at the page, decides where to click and type, and drives Chromium through Playwright. Comes with a web UI to watch it work live, and a CLI.<br/><br/>
      <code>Python</code> <code>Playwright</code> <code>Llama 4 vision (Groq)</code>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/alienxviking/devops-homework">DevOps on real AWS</a></h3>
      21 hands-on labs ending in TripBoard: GitHub Actions with SAST, dependency and secret scanning plus a Trivy gate, images to GHCR, Helm on Kubernetes, Argo CD GitOps, Prometheus + Grafana. Terraform provisions kind locally or EKS on AWS.<br/><br/>
      <code>Terraform</code> <code>EKS</code> <code>Helm</code> <code>Argo CD</code>
    </td>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/alienxviking/nexo">nexo</a></h3>
      Real-time 1:1 chat with sent/delivered/seen receipts, typing indicators, voice notes, and scheduled and self-destructing messages. Message delivery goes through Redis pub/sub so the socket servers can scale out.<br/><br/>
      <code>Socket.io</code> <code>Redis</code> <code>Prisma</code> <code>Postgres</code> &nbsp;·&nbsp; <a href="https://nexo-navy.vercel.app">live</a>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3><a href="https://github.com/alienxviking/momentum">momentum</a></h3>
      A social accountability app: habit streaks, group leaderboards driven by a computed 0–100 accountability score, peer reviews, challenges and weekly recaps. Installable PWA with web push.<br/><br/>
      <code>Next.js</code> <code>Supabase</code> <code>PWA</code> &nbsp;·&nbsp; <a href="https://momentum-seven-flame.vercel.app">live</a>
    </td>
    <td width="50%" valign="top">
      <h3>Right now</h3>
      Taking <a href="https://github.com/alienxviking/quant">quant</a> from paper trading toward live order routing, and benchmarking three C++ limit-order-book designs under <code>perf</code> for a high-performance C++ course.
    </td>
  </tr>
</table>

## Stack

<p>
  <img src="https://img.shields.io/badge/Rust-161b22?style=flat-square&logo=rust&logoColor=white" alt="Rust"/>
  <img src="https://img.shields.io/badge/C%2B%2B-161b22?style=flat-square&logo=cplusplus&logoColor=white" alt="C++"/>
  <img src="https://img.shields.io/badge/Python-161b22?style=flat-square&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/TypeScript-161b22?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/Java-161b22?style=flat-square&logo=openjdk&logoColor=white" alt="Java"/>
  <br/>
  <img src="https://img.shields.io/badge/FastAPI-161b22?style=flat-square&logo=fastapi&logoColor=white" alt="FastAPI"/>
  <img src="https://img.shields.io/badge/Next.js-161b22?style=flat-square&logo=nextdotjs&logoColor=white" alt="Next.js"/>
  <img src="https://img.shields.io/badge/Spring_Boot-161b22?style=flat-square&logo=springboot&logoColor=white" alt="Spring Boot"/>
  <img src="https://img.shields.io/badge/PostgreSQL-161b22?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL"/>
  <img src="https://img.shields.io/badge/Redis-161b22?style=flat-square&logo=redis&logoColor=white" alt="Redis"/>
  <br/>
  <img src="https://img.shields.io/badge/Docker-161b22?style=flat-square&logo=docker&logoColor=white" alt="Docker"/>
  <img src="https://img.shields.io/badge/Kubernetes-161b22?style=flat-square&logo=kubernetes&logoColor=white" alt="Kubernetes"/>
  <img src="https://img.shields.io/badge/Helm-161b22?style=flat-square&logo=helm&logoColor=white" alt="Helm"/>
  <img src="https://img.shields.io/badge/Terraform-161b22?style=flat-square&logo=terraform&logoColor=white" alt="Terraform"/>
  <img src="https://img.shields.io/badge/AWS-161b22?style=flat-square" alt="AWS"/>
  <img src="https://img.shields.io/badge/GitHub_Actions-161b22?style=flat-square&logo=githubactions&logoColor=white" alt="GitHub Actions"/>
  <img src="https://img.shields.io/badge/Argo_CD-161b22?style=flat-square&logo=argo&logoColor=white" alt="Argo CD"/>
</p>

## Work with me

I take contract work in **backend and systems engineering**, **AI agents and RAG pipelines**, and **cloud infrastructure (AWS, Kubernetes, Terraform)**. Email me at **snehangshu.roy.mail@gmail.com**.
