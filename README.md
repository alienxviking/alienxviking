<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,45:1f6feb,100:8957e5&height=210&section=header&text=Snehangshu%20Roy&fontSize=52&fontColor=ffffff&fontAlignY=36&desc=Systems%20%2B%20AI%20engineer&descSize=18&descAlignY=58&animation=fadeIn" width="100%" alt="Snehangshu Roy"/>

<p align="center">
  <a href="https://github.com/alienxviking">
    <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=19&duration=2800&pause=900&color=58A6FF&center=true&vCenter=true&width=620&lines=Rust+%2F+C%2B%2B+trading+infrastructure;Python+AI+agents+and+RAG+pipelines;AWS+%C2%B7+Kubernetes+%C2%B7+Terraform;Open+to+contract+and+freelance+work" alt="Rust / C++ trading infrastructure · Python AI agents and RAG pipelines · AWS · Kubernetes · Terraform · Open to contract and freelance work"/>
  </a>
</p>

<p align="center">
  <a href="https://snehangshu-roy-portfolio.vercel.app/"><img src="https://img.shields.io/badge/Portfolio-161b22?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio"/></a>
  <a href="https://www.linkedin.com/in/snehangshu-roy/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge" alt="LinkedIn"/></a>
  <a href="https://x.com/SnehangshuRoy15"><img src="https://img.shields.io/badge/X-161b22?style=for-the-badge&logo=x&logoColor=white" alt="X"/></a>
  <a href="mailto:snehangshu.roy.mail@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/></a>
</p>

<p align="center"><sub>CS @ Scaler School of Technology ('28)</sub></p>

I like building systems where correctness is checked, not assumed: a trading engine where backtest, paper and live run the same code path, a document pipeline that survives worker restarts, and infrastructure that can be destroyed and rebuilt from Terraform.

## 📈 Flagship: [quant](https://github.com/alienxviking/quant)

A quantitative trading platform in Rust. It captures market data, replays it deterministically, and runs **one strategy binary across backtest, paper and live trading with no code changes**.

```mermaid
flowchart LR
    H["HistoricalSource<br/>Parquet replay"] --> E
    L["LiveSource<br/>exchange WebSocket"] --> E
    E(("Engine")) <--> S["Strategy"]
    E --> R["RiskLayer<br/>mandatory chokepoint"]
    R --> SV["SimulatedVenue<br/>fills · fees · latency"]
    R -.-> LV["LiveVenue<br/>real orders · in progress"]

    classDef src fill:#0d2a4a,stroke:#1f6feb,color:#e6edf3
    classDef core fill:#2a1650,stroke:#8957e5,color:#e6edf3
    classDef venue fill:#0f2e1d,stroke:#2ea043,color:#e6edf3
    classDef wip fill:#2b2410,stroke:#9e6a03,color:#e6edf3,stroke-dasharray:4 3
    class H,L src
    class E,S,R core
    class SV venue
    class LV wip
```

| Mode | Source | Venue |
|---|---|---|
| Backtest | Historical | Simulated |
| Paper | Live | Simulated |
| Live | Live | Live |

- 🧱 **12 crates, 30K lines, 416 tests:** recorder, order-book reconstruction, Parquet normalization, engine, simulated venue and an offline verifier
- 🎯 **A 14-day live paper run reproduced its backtest exactly**: same fills, cash and realized P&L to the satoshi, across 97.9M recorded frames with zero missing
- 💰 **Money is fixed-point `i64`**; float arithmetic is denied by clippy across the whole workspace
- 🛡️ **Risk is a mandatory chokepoint**, not a library the strategy chooses to call: an oversized order never reaches the venue

## 🛠️ Other work

<table>
  <tr>
    <td width="50%" valign="top">
      <h3>🖍️ <a href="https://github.com/alienxviking/redpen">RedPen</a></h3>
      AI marking for answer papers. Every mark is tied to a verbatim quote from the student, mapped quote → character span → page rectangle, so the mistake is boxed where it actually is. The model judges, but code does the arithmetic: marks are clamped to the rubric and totals reconciled. Four model backends behind one interface; 102 offline tests.
      <br/><br/>
      <code>TypeScript</code> <code>React</code> <code>pdf.js</code> <code>Claude / Gemini / Groq</code>
    </td>
    <td width="50%" valign="top">
      <h3>🔎 <a href="https://github.com/alienxviking/sift">sift</a></h3>
      Document processing and hybrid search. Uploads (PDF, images, DOCX) go to Celery workers for text extraction, OCR, thumbnails and local embeddings, then become searchable through Postgres full-text + pgvector fused with Reciprocal Rank Fusion. Multi-tenant, with live status over WebSockets.
      <br/><br/>
      <code>FastAPI</code> <code>Next.js</code> <code>Celery</code> <code>pgvector</code>
      <br/><br/>
      <a href="https://sift-docprocess.vercel.app/"><img src="https://img.shields.io/badge/live_demo-1f6feb?style=flat-square&logo=vercel&logoColor=white" alt="live demo"/></a>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3>🏎️ <a href="https://github.com/alienxviking/scaler-HFT-C--2028/tree/capstone-order-book-10155/Capstone/24bcs10155-Snehangshu-Roy_24bcs10246-Saniya-Patil">Limit order book (C++)</a></h3>
      Three book designs benchmarked on 1M-op workloads. Ours (flat price array + bitmap + open-addressing table) won every op: <b>56.7 ns</b> add, <b>38.3 ns</b> cancel, <b>3.8×</b> faster than the <code>std::map</code> book. Explained with <code>perf</code> counters: ~5× fewer L1 misses, IPC 1.41 vs 0.79. Team of 2.
      <br/><br/>
      <code>C++17</code> <code>perf</code> <code>Docker</code>
    </td>
    <td width="50%" valign="top">
      <h3>🤖 <a href="https://github.com/alienxviking/web-automation-agent">web-automation-agent</a></h3>
      A browser agent that works from screenshots instead of CSS selectors. A vision LLM looks at the page, decides where to click and type, and drives Chromium through Playwright. Comes with a web UI to watch it work live, and a CLI.
      <br/><br/>
      <code>Python</code> <code>Playwright</code> <code>Llama 4 vision (Groq)</code>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3>💬 <a href="https://github.com/alienxviking/nexo">nexo</a></h3>
      Real-time 1:1 chat with sent/delivered/seen receipts, typing indicators, voice notes, and scheduled and self-destructing messages. Message delivery goes through Redis pub/sub so the socket servers can scale out.
      <br/><br/>
      <code>Socket.io</code> <code>Redis</code> <code>Prisma</code> <code>Postgres</code>
      <br/><br/>
      <a href="https://nexo-navy.vercel.app"><img src="https://img.shields.io/badge/live_demo-1f6feb?style=flat-square&logo=vercel&logoColor=white" alt="live demo"/></a>
    </td>
    <td width="50%" valign="top">
      <h3>☁️ <a href="https://github.com/alienxviking/devops-homework">DevOps on real AWS</a></h3>
      21 hands-on labs ending in TripBoard: GitHub Actions with SAST, dependency and secret scanning plus a Trivy gate, images to GHCR, Helm on Kubernetes, Argo CD GitOps, Prometheus + Grafana. Terraform provisions kind locally or EKS on AWS.
      <br/><br/>
      <code>Terraform</code> <code>EKS</code> <code>Helm</code> <code>Argo CD</code>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3>🔥 <a href="https://github.com/alienxviking/momentum">momentum</a></h3>
      A social accountability app: habit streaks, group leaderboards driven by a computed 0–100 accountability score, peer reviews, challenges and weekly recaps. Installable PWA with web push.
      <br/><br/>
      <code>Next.js</code> <code>Supabase</code> <code>PWA</code>
      <br/><br/>
      <a href="https://momentum-seven-flame.vercel.app"><img src="https://img.shields.io/badge/live_demo-1f6feb?style=flat-square&logo=vercel&logoColor=white" alt="live demo"/></a>
    </td>
    <td width="50%" valign="top">
      <h3>⚡ Right now</h3>
      Taking <a href="https://github.com/alienxviking/quant">quant</a> from paper trading to live order routing: the engine gains a second asynchronous input, and every live fill gets reconciled against the exchange.
    </td>
  </tr>
</table>

## 🧰 Stack

<p align="center">
  <img src="https://skillicons.dev/icons?i=rust,cpp,python,ts,java,fastapi,nextjs,spring,postgres,redis,docker,kubernetes,terraform,aws,githubactions,linux&perline=8&theme=dark" alt="Rust, C++, Python, TypeScript, Java, FastAPI, Next.js, Spring, PostgreSQL, Redis, Docker, Kubernetes, Terraform, AWS, GitHub Actions, Linux"/>
</p>

## 🤝 Work with me

I take contract work in **backend and systems engineering**, **AI agents and RAG pipelines**, and **cloud infrastructure (AWS, Kubernetes, Terraform)**.

<p align="center">
  <a href="mailto:snehangshu.roy.mail@gmail.com"><img src="https://img.shields.io/badge/Email_me-snehangshu.roy.mail%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white" alt="Email me"/></a>
</p>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:8957e5,55:1f6feb,100:0d1117&height=110&section=footer" width="100%" alt=""/>
