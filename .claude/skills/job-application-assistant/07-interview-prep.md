---
framework_version: 1.0.0
---

# Interview Preparation Guide

<!-- STAR examples drafted by /setup from the candidate's CV, LinkedIn, and project descriptions.
     Every S/T/A/R below is grounded in a claim the candidate has already made in writing. -->

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## Ready-Made STAR Examples

### 1. Baatasari backend migration off Firebase (Ownership / vendor independence)
**S:** The product's core backend services ran on Firebase, which meant vendor lock-in and monthly infrastructure costs the team could not control.
**T:** Own the migration of those core services to self-hosted Supabase, end-to-end.
**A:** Migrated the core backend services off Firebase onto a self-hosted Supabase instance, then stood up production infrastructure on Hetzner through Coolify with automated CI/CD so deployments were reproducible rather than manual.
**R:** Eliminated vendor lock-in and reduced monthly infrastructure costs by ~25%; deployment time fell by ~40%.
**Use for:** "Tell me about a time you owned something end-to-end", "Describe a migration you led", "How do you handle technical debt?"

### 2. Strata event-driven feed architecture (Failure-mode design)
**S:** Social feed and notification systems degrade under load when ingestion and delivery aren't decoupled: slow feeds, lost events, and unrecoverable job failures during traffic spikes.
**T:** Design the event-driven engine so ingestion stayed reliable under load.
**A:** Engineered the feed and notification engine on BullMQ workers and Redis Pub/Sub, separating ingestion from delivery. Added dead-letter queues, replay mechanics, and exponential backoff retries, plus cursor-based pagination so offset queries would not degrade at scale, and Bull Board dashboards for queue observability.
**R:** Consistent delivery performance under load, lost events minimised to what dead-letter handling could recover, and runtime visibility into queue failures.
**Use for:** "Design a system that handles failure", "Tell me about a hard debugging problem", "How do you think about reliability?"

### 3. TranscodeX transcoding pipeline (Throughput / async architecture)
**S:** Serving video at scale requires multi-resolution transcoding and adaptive streaming, but naive synchronous pipelines block on I/O-heavy FFmpeg jobs.
**T:** Build a pipeline that turned raw uploads into adaptive streams without blocking.
**A:** Architected an asynchronous, event-driven pipeline using BullMQ and Redis to orchestrate FFmpeg transcoding into 480p/720p/1080p renditions with a default HLS packaging and thumbnail generation step. Added multipart S3 uploads with real-time progress telemetry over Redis Pub/Sub and Socket.IO.
**R:** Transcoding turnaround reduced by ~40%; upload progress visible to clients live rather than polled.
**Use for:** "Tell me about a performance problem you solved", "Describe a system you designed", "How do you handle long-running work?"

### 4. Project Intelligence Agent RAG system (Applied AI / retrieval)
**S:** Developers using LLM coding assistants lose significant time manually tracing context across large, unfamiliar codebases, which leads to shallow or hallucinated suggestions.
**T:** Build a system that retrieves real codebase context for an agent rather than letting it guess.
**A:** Built an automated repository-intelligence pipeline that clones repos, parses abstract syntax trees and indexes codebases for contextual retrieval. Designed the RAG architecture using LangChain for chunking, embedding and retrieval, with LangGraph orchestrating stateful multi-step agentic reasoning. Async worker queues handled diff analysis, dependency graphing, and LLM rate-limit throttling. Uses Claude Code for agentic development work.
**R:** Retrieval relevance improved by ~35%; average query latency reduced by ~30%.
**Use for:** "Tell me about an AI system you built", "How would you design a RAG pipeline?", "What have you learned recently?"

### 5. Baatasari frontend migration to Next.js (Cross-functional impact)
**S:** The web client ran on React/Vite with poor SEO indexing and slow initial loads.
**T:** Drive the migration to a framework that fixed both, alongside the backend work.
**A:** Re-engineered the client architecture from Vite to Next.js and used SSR caching for the initial render path.
**R:** Initial page load latency down ~30% and SEO indexing improved.
**Use for:** "Tell me about a time you worked outside your comfort zone", "How do you prioritise frontend performance?", "What does full-stack mean to you?"

### 6. Mentoring backend interns at Baatasari (Leadership without title)
**S:** The team was small and included backend interns who needed direction.
**T:** Review their work and set technical direction without formal authority.
**A:** Managed and mentored the interns, reviewing pull requests and guiding technical decisions rather than assigning tickets.
**R:** Interns contributed production work under review; the direction was set by technical reasoning rather than process.
**Use for:** "Tell me about mentoring or leadership", "How do you handle code reviews?", "How would you lead a team?"
**Gap:** Be honest that this was mentoring, not people management. If a role requires formal management experience, say it is a next step, not a past one.

## Common Tough Questions

### "Why are you leaving Accenture / why did you leave Baatasari?"
> Accenture is a strong first enterprise environment and the MEAN-stack training was useful, but the work is application development on a defined scope. My depth is in backend and distributed systems: queues, infrastructure ownership, LLM integration. I'm looking for a role where that is the core of the job, not an adjacent layer. Keep it forward-looking; no criticism of either employer.

### "You don't have [specific skill/experience]."
> Acknowledge it plainly, then bridge: "I haven't run [X] at enterprise scale. What I have done is design and operate [closest real thing] under real load - [concrete example]. The gap is scale and process, not the fundamentals." Never invent experience.

### "Where do you see yourself in 5 years?"
> Technical leadership: a tech lead or staff engineer role where I own architecture for a system or a small team. Distributed systems and applied AI are the two areas I want to go deep in, and I'd rather grow through ownership than through title changes.

### "What's your biggest weakness?"
> Enterprise process and cross-team coordination. Most of my experience has been small teams where one engineer owns a system, so I haven't had to navigate heavy multi-team planning. Accenture is my first real exposure to it. Mitigation: I default to writing things down and making decisions explicit, which is what makes coordination work at scale.

### "Why this company specifically?"
> Customize per company. Must reference: specific projects, company values, market position, or team structure. Never give a generic answer.

### "You built these projects alone - how is that team work?"
> Fair question. The projects are solo builds precisely so I can work through architecture decisions end-to-end, but the Baatasari work was collaborative: I reviewed PRs, mentored interns, and coordinated the frontend migration with the rest of the team. The solo work is where I deepen judgement; the team work is where I apply it.

## Questions You Should Ask Interviewers

### About the Role
- "What does a typical week look like in this role?"
- "What would success look like in the first 6 months?"
- "What's the biggest challenge the team is facing right now?"
- "How much of this role is new development versus maintenance of existing systems?"

### About the Team
- "How big is the team, and how do you divide work?"
- "What does the development/project lifecycle look like, from idea to production?"
- "Who owns production when something breaks at 2am?"
- "How do you onboard new team members?"

### About Tech & Growth
- "What's your current tech stack for [relevant area]?"
- "Is there room to grow into more architectural or strategic decisions?"
- "How does the team stay current with new tools and methods?"
- "What does the on-call rotation look like, if there is one?"

### About Culture (use these to prevent disappointment)
- "How would you describe the team culture?"
- "What does professional development look like here?"
- "Is there flexibility for remote/hybrid work?"
- "What's the balance between development/new projects and maintenance work?"
- "How would you describe the leadership style in this team?"
- "What do people who thrive here have in common?"

## Phone/Video Interview Tips
- Have STAR examples written out (use this file)
- Keep a glass of water nearby
- Smile when speaking (it changes your tone)
- Ask for clarification if a question is vague
- It's OK to take 5 seconds to think before answering
- End with: "Is there anything else you'd like to know about my background?"

## After the Application (Best Practice)

### Follow-Up Etiquette
- **Don't call to "stand out"** or to learn more about the role post-submission - this risks a negative impression
- If the employer specified a timeline, respect it and wait
- If no timeline was given and significant time has passed (2+ weeks), a brief call to ask about status is acceptable
- If you have genuinely new, relevant information to share, a short follow-up is fine

### Thank-You Notes
- When you receive any update (interview invitation, rejection, or status update), send a brief thank-you message
- Express appreciation for their time and the process
- Keep it short (2-3 sentences)

## Roleplay Guidelines
When the user asks for interview practice:
1. Ask which role/company to simulate
2. Start with easy warm-up questions ("Tell me about yourself")
3. Progress to role-specific technical questions
4. Include 1-2 behavioral questions using the competencies from the job posting
5. End with a tough question or curveball
6. After each answer, give brief feedback: what worked, what to sharpen
7. Suggest which STAR example would work best for each question
