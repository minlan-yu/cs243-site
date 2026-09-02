# CS 243, Fall 2026: Advanced Computer Networks

## Overview

This is a graduate-level course on computer networks that offers an in-depth exploration of selected advanced topics in networked systems. We will discuss the latest developments across the entire networking stack, the interactions between networks and high-level applications, and their connections with other system components such as computing and storage.

The course focuses on the intersection of machine learning and networking. As ML applications increasingly rely on larger models, longer contexts, and faster accelerators — from large-scale distributed training to efficient inference serving — the demand for enhanced networking capabilities becomes imperative. We will study cutting-edge networking solutions and principles for co-designing networks with computing and storage, covering topics such as parallelism strategies, collective communication, RDMA, congestion control, fault tolerance, and production ML infrastructure. The course will include lectures, in-class presentations, paper discussions, and a research project.

- Instructor: Minlan Yu
- Lecture time: TuTh 11:15 am to 12:30 pm
- Location: SEC 1.402
- Office hours: Tu 10-11 am, SEC 4.415
- Teaching fellows: Weifan Jiang weifanjiang@g.harvard.edu
- Prerequisite: This course has no prerequisites. Since this course will focus on reading papers on the latest topics in networking, you will need to be able to pick up the relevant background for each topic from textbooks or online materials.
- Recommended prep: system programming at the level of CS 61, CS 143, or CS 145.

## Getting Started

**If you are thinking of attending the class, please check [the infrastructure page](infra.md) to set up your cloud infrastructure and try the [warmup project](warmup.md) as soon as possible.**

## Textbook
There are no required textbooks for the course. You will read papers before each class to get the most out of the class. For background, you are encouraged to refer to the following references:
- For basic networking concepts, you can refer to the textbook (K&R) Computer Networking: A Top-Down Approach by Jim Kurose and Keith Ross. The latest edition is the 8th, but earlier editions are fine.
- An alternative book is Computer Networks: A Systems Approach, by Larry Peterson and Bruce Davie. You can find an online version [here](https://book.systemsapproach.org/).
- For large-scale training and the parallelism schemes we cover, [The Ultra-Scale Playbook: Training LLMs on GPU Clusters](https://huggingface.co/spaces/nanotron/ultrascale-playbook) from Hugging Face is a helpful reference. Individual chapters are linked as optional reading throughout the syllabus.
- Please feel free to contact me if some concepts are difficult to understand; I'll provide more supplemental materials.

## Coursework and Grading
- Project: 50% (1% project proposal, 4% initial project presentation, 5% mid-term report, 5% final project presentation, 35% final report and code)
- Class presentation: 40% (8% per role, one role in each of five paper presentations; for the four report roles, 4% for the in-class presentation/discussion and 4% for the report)
- Attendance: 10% (before-class posts; missing a call-up reduces your attendance points)

Please see the detailed requirements after the syllabus.

## Syllabus

The papers we read emphasize distributed systems and networking in ML Systems. Ed posts start from the 9/15 class.

### Introduction

- 9/3 Th: Introduction (Minlan)
  * Optional reading: [The Llama 3 Herd of Models](https://arxiv.org/pdf/2407.21783)
- 9/8 Tu: Transformer, scaling law, Hardware, high-level course project ideas (Minlan)
  * Optional Reading: [Transformer illustrated](https://jalammar.github.io/illustrated-transformer/)

### Distributed Training (Parallelism schemes and Communication)

- 9/10 Th: Data Parallelism and Sharding (Minlan)
  * Reading: [PyTorch FSDP: Experiences on Scaling Fully Sharded Data Parallel](https://arxiv.org/abs/2304.11277)
  * Reading: [ZeRO: Memory Optimizations Toward Training Trillion Parameter Models](https://arxiv.org/abs/1910.02054)
  * Optional Reading: [Hugging Face Playbook - Data Parallelism](https://nanotron-ultrascale-playbook.static.hf.space/#data_parallelism)
- 9/15 Tu: Model Parallelism and Pipelining
  * Reading: [PipeDream: Generalized Pipeline Parallelism for DNN Training](https://dl.acm.org/doi/10.1145/3341301.3359646)
  * Optional Reading: [Hugging Face Playbook - Pipeline Parallelism](https://nanotron-ultrascale-playbook.static.hf.space/#pipeline_parallelism)
- 9/17 Th: Tensor Parallelism, Sequence Parallelism, Context Parallelism
  * Reading: [Efficient Large-Scale Language Model Training on GPU Clusters Using Megatron-LM](https://arxiv.org/pdf/2104.04473.pdf)
  * Reading: [LoongServe: Efficiently Serving Long-Context Large Language Models with Elastic Sequence Parallelism](https://dl.acm.org/doi/10.1145/3694715.3695948)
  * Optional Reading: [Hugging Face Playbook - Tensor Parallelism](https://nanotron-ultrascale-playbook.static.hf.space/#tensor_parallelism), [Sequence Parallelism](https://nanotron-ultrascale-playbook.static.hf.space/#sequence_parallelism), and [Context Parallelism](https://nanotron-ultrascale-playbook.static.hf.space/#context_parallelism)
- 9/22 Tu: Mixture of Experts
  * Reading: [DeepSeek-V3 Technical Report](https://arxiv.org/abs/2412.19437)
  * Reading: [Insights into DeepSeek-V3: Scaling Challenges and Reflections on Hardware for AI Architectures](https://dl.acm.org/doi/epdf/10.1145/3695053.3731412)
  * Optional Reading: [MegaScale-Infer: Serving Mixture-of-Experts at Scale with Disaggregated Expert Parallelism](https://arxiv.org/abs/2504.02263)
  * Optional Reading: [Hugging Face Playbook - Expert Parallelism](https://nanotron-ultrascale-playbook.static.hf.space/#expert_parallelism)
  
### LLM Inferences
- 9/24 Th: LLM serving
  * Reading: [Efficient Memory Management for Large Language Model Serving with PagedAttention](https://arxiv.org/pdf/2309.06180)
  * Optional Reading: [Orca: A Distributed Serving System for Transformer-Based Generative Models](https://www.usenix.org/system/files/osdi22-yu.pdf) (OSDI 2022)
- 9/29 Tu: Course project pitch presentation
- 10/1 Th: Course project pitch presentation
- 10/6 Tu: KV Cache
  * Reading: [Mooncake: A KVCache-centric Disaggregated Architecture for LLM Serving](https://arxiv.org/abs/2407.00079)
  * Optional Reading: [CacheGen: KV Cache Compression and Streaming for Fast Large Language Model Serving](https://arxiv.org/abs/2310.07240)
- 10/8 Th: Distributed serving (Guest speaker: Raj Joshi, Red Hat)
  * Reading: [DistServe: Disaggregating Prefill and Decoding for Goodput-optimized Large Language Model Serving](https://www.usenix.org/system/files/osdi24-zhong-yinmin.pdf)
- 10/13 Tu: Inference kernel optimization
  * Reading: [FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness](https://arxiv.org/abs/2205.14135)
  * Reading: [Fast Inference from Transformers via Speculative Decoding](https://arxiv.org/abs/2211.17192)
  * Optional Reading: background on GPUs: [Stanford CS336 Lecture 5 (GPUs, TPUs)](https://github.com/stanford-cs336/lectures/blob/main/lecture_05.pdf)
- 10/15 Th: Diffusion inference
  * Reading: [DistriFusion: Distributed Parallel Inference for High-Resolution Diffusion Models](https://arxiv.org/abs/2402.19481)
  * Optional Reading: [Approximate Caching for Efficiently Serving Text-to-Image Diffusion Models](https://www.usenix.org/system/files/nsdi24-agarwal-shubham.pdf)
  * Optional Reading: [PipeFusion: Patch-level Pipeline Parallelism for Diffusion Transformers Inference](https://arxiv.org/abs/2405.14430)

### Networking and Communication

- 10/20 Tu: NCCLX
  * Reading: [Collective Communication for 100k+ GPUs](https://arxiv.org/abs/2510.20171)
  * Optional Reading: [Enabling Efficient GPU Communication over Multiple NICs with FuseLink](https://www.usenix.org/system/files/osdi25-ren.pdf)
- 10/22 Th: RDMA
  * Reading: [RDMA over Ethernet for Distributed AI Training at Meta Scale](https://dl.acm.org/doi/pdf/10.1145/3651890.3672233)
  * Optional Reading: [UCCL: An Extensible Software Transport Layer for GPU Networking](https://www.usenix.org/system/files/osdi26-zhou-yang.pdf)
- 10/27 Tu: AI networking (Guest speaker: Mario Baldi, Nvidia)
  * Reading: [OpenAI MRC](https://arxiv.org/pdf/2605.04333)
  * Optional Reading: [ESUN: Ethernet for Scale-Up Networking (OCP, 2025)](https://www.opencompute.org/blog/introducing-esun-advancing-ethernet-for-scale-up-ai-infrastructure-at-ocp)
  * Optional Reading: [UALink: An Open, High-Efficiency Scale-Up Interconnect for AI (UALink Consortium white paper)](https://ualinkconsortium.org/wp-content/uploads/2026/01/UALink_White_Paper_Publication_Candidate_FINAL_VERSION.pdf)
- 10/29 Th: Fused kernel
  * Reading: [MPK: A Compiler and Runtime for Mega-Kernelizing Tensor Programs](https://arxiv.org/abs/2512.22219)
  * Optional Reading: [ParallelKittens: Systematic and Practical Simplification of Multi-GPU AI Kernels](https://arxiv.org/abs/2511.13940)
  * Optional Reading: [ThunderKittens: Simple, Fast, and Adorable AI Kernels](https://arxiv.org/abs/2410.20399)


### RL, Agentic AI, and Power

- 11/3 Tu: Agentic AI
  * Reading: [Autellix: An Efficient Serving Engine for LLM Agents as General Programs](https://arxiv.org/abs/2502.13965)
  * Optional Reading: [Pie: A Programmable Serving System for Emerging LLM Applications](https://arxiv.org/abs/2510.24051)
- 11/5 Th: Prompt and program optimization
  * Reading: [GEPA: Reflective Prompt Evolution Can Outperform Reinforcement Learning](https://arxiv.org/abs/2507.19457)
  * Optional Reading: [optimize_anything: A Universal API for Optimizing any Text Parameter](https://arxiv.org/abs/2605.19633)
- 11/10 Tu: Computer use
  * Reading: [OSGym: Scalable OS Infra for Computer Use Agents](https://arxiv.org/abs/2511.11672)
  * Optional Reading: [OSWorld-Human: Benchmarking the Efficiency of Computer-Use Agents](https://arxiv.org/abs/2506.16042)
- 11/12 Th: Post-training; Reinforcement learning
  * Reading: [Verl (HybridFlow: A Flexible and Efficient RLHF Framework)](https://arxiv.org/abs/2409.19256)
  * Reading: [SkyRL: A Modular Full-stack RL Library for LLMs](https://github.com/NovaSky-AI/SkyRL)
  * Optional reading: [DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning](https://arxiv.org/abs/2501.12948)
- 11/17 Tu: Reinforcement learning systems
  * Reading: [TensorHub: Scalable and Elastic Weight Transfer for LLM RL Training](https://arxiv.org/abs/2604.09107)
  * Reading: [Accelerating RLHF with vLLM, Best Practice from OpenRLHF](https://blog.vllm.ai/2025/04/23/openrlhf-vllm.html)
- 11/19 Th: Power
  * Reading: [Power Stabilization for AI Training Datacenters](https://arxiv.org/abs/2508.14318)
  * Optional Reading: [Provisioning to Runtime Optimization of a 100 MW-Scale AI Cluster](https://arxiv.org/abs/2605.24461)


### Final project presentation

- 11/24 Tu: Final project presentation (batch I)
- 11/26 Th: No class: Thanksgiving
- 12/1 Tu: Final project presentation (batch II)
- 12/3 Th: Final project presentation (batch III)
- 12/16 Final Project Deadline (updated based on school examination group and dates)

## Paper reading and in-class presentations

We have reformatted the course to encourage more in-class participation and discussion. The goal of the presentation and in-class discussion is to learn how to form your own opinions about a paper.

Every student posts questions and comments about the paper before class. In addition, for each paper we select a few students to study the readings (and the optional readings) in depth. These students lead the class presentation and discussion, and submit slides or a report before the class. In class, we expect them to know all the details of the paper and to be able to answer questions during the discussion; they are graded on both the in-class presentation/discussion and the pre-class writing. If you have any questions about the paper, feel free to reach out to me before the class.

A useful method for every role below is the three-pass approach in S. Keshav, [How to Read a Paper](https://dl.acm.org/doi/pdf/10.1145/1273445.1273458) (ACM SIGCOMM CCR 37(3), 2007): a five-to-ten minute first pass for a bird's-eye view, a second pass of up to an hour to grasp the content but not the details, and a third pass that attempts to virtually re-implement the paper. The Ed post asks for a first or second pass; the in-depth roles ask for a third pass on one part of the paper.

### Questions and comments about the paper before the class by all the students

- Everyone is required to read the papers labeled as readings before the class. You do not have to read the optional readings.
- Everyone needs to post one comment or one question about the paper in Ed. The post should be just one paragraph, referring to the specific context from the paper first and then describing your comments or questions in depth. For example, rather than just asking how does this system scale to 10K GPUs, you should talk about the specific perspectives of the system (e.g., the paper has an evaluation of communication overhead as GPU number grows) and share your thoughts (so when we have more GPUs, the balance of compute and communication may change).
- If you are not sure what to write about, Keshav's "five Cs" are a good place to start: **Category** (what type of paper is this?), **Context** (which other papers is it related to?), **Correctness** (do the assumptions appear to be valid?), **Contributions** (what are the paper's main contributions?), and **Clarity** (is the paper well written?).
- Posts are due by noon one day before class (Monday noon for Tuesday classes; Wednesday noon for Thursday classes). This gives the presenting students time to collect your questions for the class discussion.
- It is acceptable to miss THREE posts throughout the course. We will count the rest of the posts for your attendance score.
- In each class, we will select two students at random to talk about the comments/questions in their post. If you are absent when called on, your attendance grade is reduced.

### Paper overview with slides
- Give a 20-minute talk about the whole paper, like a conference talk.
- Cover the motivation (what problem the paper is solving; why this problem wasn't solved before) and the challenges (why this problem is difficult to solve), and tie the parts of the paper together into a single story.
- Aim for what Keshav sets as the goal of the second pass: being able to summarize the main thrust of the paper, with supporting evidence, to someone who has not read it.
- You should prepare slides for the talk and submit them before the class.
- Some authors share slides online, and some conferences share conference talk videos. You are encouraged to check out these resources or reuse them for your presentation with clear citations. However, be aware that conference talks are often short and focus more on the motivation rather than the technical details. They may also highlight only the benefits of their approaches (Everyone likes their own work). So, if you reuse the slides, please add more technical details, ensure you understand the content thoroughly, and share your own understanding and opinions of the work (not just the authors').

### Related work with report
- Explain what came before this paper, and how this paper differs from it.
- Build that picture the way Keshav describes doing a literature survey: start from the paper's own related-work section, then look for shared citations and repeated author names across those papers, which point to the key papers and researchers in the area. Check where those researchers have published recently, and scan the recent proceedings of those venues for work that postdates this paper.
- Where the paper claims to improve on prior work, say whether the comparison is a fair one, and flag any citations you think are missing.

### System design with report
- Explain how the authors address the challenges.
- Take Keshav's third pass: attempt to virtually re-implement the design, making the same assumptions the authors made. Identify and challenge every assumption, and say where you would have made a different choice, and why.
- By the end you should be able to reconstruct the structure of the design from memory, and to pinpoint the assumptions it leaves implicit.

### Evaluation with report
- Explain whether the evaluation demonstrates that the problems and challenges are solved.
- Look carefully at the figures, and pay special attention to the graphs: are the axes properly labeled? Are results shown with error bars, so that the conclusions are statistically significant? As Keshav puts it, mistakes like these separate rushed, shoddy work from the truly excellent.
- Say whether the paper gives enough information to reproduce the experiments, and call out any problems you see with the experimental or analytical technique.

### Future looking with report
- Give a conference-style paper review: strengths and weaknesses, and your own opinions of the paper.
- Use the third pass to pinpoint the paper's strong and weak points and its hidden failings, and, as Keshav suggests, to jot down ideas for future work: what would you do next if this were your project?
- Summarize any other interesting points from the posts on Ed.
- Students in this role should read the posts submitted by your classmates, list their questions in your slides, and help lead the discussion of these questions in class.

## Projects
The semester-long project is an open-ended systems research project. Project topics are of your choice but should be related to ML systems and/or networking. Projects should be done in groups of two or three and include a systems-building component. Note that we do not consider the number of students in a group in grading — scope expectations are the same regardless of group size. Top projects will be invited to continue working over the winter break to submit peer-reviewed papers to [ICLR 2027 workshops](https://iclr.cc/) and [ICML 2027](https://icml.cc/).

### Project Timeline
- 9/13 Sun at noon: Form groups for course projects
- 9/27 Sun at noon: Course project proposal
- 9/29 Tu, 10/1 Th: Course project pitch presentation
- 11/8 Sun at noon: Midterm project report due at noon
- 11/9-13: Schedule individual meetings with Minlan to get feedback on your midterm report
- 11/24 Tu, 12/1 Tu, 12/3 Th: Final project presentation
- 12/16 Final project due at noon
- 12/17 Review of other students' projects due at midnight

### Project Proposal
The project proposal serves as a checkpoint, providing a basis for your pitch presentations.
Please check out the guidelines for pitch presentation below on what to write in your project proposal.
**You will receive the full 1% grade if you submit your proposal on time.** Unfortunately, late submissions will not be accepted, and there is no opportunity to make up the grade. After submission, you can keep updating your proposal.

### Project pitch presentation
Each group should deliver a 5-minute talk followed by 2-3 minutes of Q&A. Be mindful about the scope of your project to ensure it can be completed by your team within two and a half months.
The presentation should be 4-6 slides and include the following points:
- What problem are you solving?
- Why is it an important problem?
- What potential challenges might you face in solving the problem?
- What is your plan for the midterm report and division of work within the team?

Please submit your slides after the presentation.

**Your grade depends on how concrete your problem and execution plan are.**

### Midterm Project Report
The midterm report should be about 2-4 pages using the [ICML template](https://media.icml.cc/Conferences/ICML2025/Styles/icml2025.zip) and serve as a starting point for your final project report (see detailed requirements for the final report below). **To achieve a high score for your midterm report, it is important to deliver an initial evaluation of your system.** You don't need to complete the entire system; instead, focus on identifying the most critical component/question in your project and provide an initial quantitative evaluation. The midterm report should include the following:
- Describe the problem you plan to solve, why it is novel/unique, and the major challenges (similar to your project pitch presentation, but feel free to adapt it based on your new understanding of the problem).
- Describe the detailed design of your project and what you have implemented/evaluated so far.
- Provide one quantitative evaluation figure (e.g., a performance graph) about your initial system (This will be the focus of your meeting with Minlan).
- Discuss the remaining challenges, how you plan to address them, and your plan for the remaining time.

### Final project presentations
This presentation should resemble a workshop talk. You might consider covering the following content (not necessarily in the same order):
- What problem are you solving?
- Why is it an important problem?
- What is your basic solution to the problem?
- What are the challenges in the problem?
- How did you solve these challenges? Or how do you plan to solve them?
- Your preliminary evaluation results
- What do you plan to improve for the final report?


### Final Project Report
The report should be similar in spirit to a conference paper, spanning six pages of double-column, single-spaced, 10-point font, excluding references. Here is an [example LaTeX framework](https://media.icml.cc/Conferences/ICML2025/Styles/icml2025.zip) for formatting and building your paper. As shown in the framework, you may consider the following sections for your report (adapted from Eddie's version):

- Title: Something grabby that correctly describes a part of the contribution.
- Abstract: A paragraph or two that concisely describes the motivation for the work (the problem addressed), the contribution of the work, and a highlight of your results.
- Introduction: The introduction often covers the following questions: what problem are you trying to solve? Why is your problem important? What are the key challenges in solving your problem? What are your high-level ideas for addressing these challenges? What is your key design/system architecture? What are your key findings and evaluation results?
- Design: Start with the high-level architecture of your system, and then describe the details of your design in enough relevant detail that a skilled system builder could replicate your work. Compare your design choices with alternative approaches to explain why you designed your system this way.
- Evaluation: For systems work, this often includes the following subsections: (1) Experimental setup: Describe how you ran your experiments. What kinds of machines? How much memory? How many trials? How did you prepare the machine before each trial? (2) The experiments themselves, grouped by purpose. Include figures. (3) A summary of the experimental results. Some good evaluations are organized around performance hypotheses: statements that the experiments aim to support or disprove. It is important to discuss the implications of your observed results and why you see such results.
- Related work: Describe related research, especially research closely related to your work. This section serves to provide citations and comparisons. For each group of citations, describe (1) the core idea, (2) what is complementary to your work, (3) what is more advanced than your work, and (4) what is advanced upon by your work. (2)–(4) are optional—some papers will be entirely complementary with or orthogonal to your work.
- Limitations and Future Work: Briefly discuss what your system does not handle, known limitations, and directions for future improvement.
- Conclusion: Summarize your work and its contributions.

### Code submission
Together with the final report, you should submit the GitHub link of your project code. No need for superb software engineering, but ideally the code should be accompanied by enough documentation that a motivated user could attempt to replicate your results. You will need to demonstrate your product to the TFs at office hours after the final project deadline.

### Grading
The first four milestones (initial proposal, pitch presentation, midterm report, final project presentations) are mainly graded based on how well you keep up with the project progress at each stage. You will also get feedback at these milestones on how to improve your projects. The final project will be graded based on: Motivation, Design, delivered system, and its evaluation.

### Policy on AI tools
- **Paper reviews:** You are **not allowed** to use any AI tools (e.g., ChatGPT, Claude, Copilot) for writing paper reviews. Reviews must reflect your own reading and understanding of the papers. Violations of this policy will be considered academic misconduct.
- **Course projects:** You are highly encouraged to use AI tools for course projects (e.g., for coding, debugging, or brainstorming). Any such use must be appropriately acknowledged and cited in your project report. It is each student’s responsibility to assess the validity and applicability of any AI-generated output that is submitted; you bear the final responsibility. Violations of this policy will be considered academic misconduct.

We draw your attention to the fact that different classes at Harvard could implement different AI policies, and it is the student’s responsibility to conform to expectations for each course. There are also [Harvard guidelines for GAI tools](https://provost.harvard.edu/guidelines-using-chatgpt-and-other-generative-ai-tools-harvard).

## Diversity and Inclusion
I would like to create a learning environment in our class that supports a diversity of thoughts, perspectives and experiences, and honours your identities (including race, gender, class, sexuality, socioeconomic status, religion, ability, etc.). I (like many people) am still in the process of learning about diverse perspectives and identities. If something was said in class (by anyone) that made you feel uncomfortable, please talk to me about it. If you feel like your performance in the class is being impacted by your experiences outside of class, please don’t hesitate to come and talk with me. As a participant in course discussions, you should also strive to honour the diversity of your classmates. (Statement extracted from one by Dr. Monica Linden at Brown University.)

## Accommodations for Disabilities
If you have a health condition that affects your learning or classroom experience, please let me know as soon as possible. I will, of course, provide all the accommodations listed in your AEO letter (if you have one), but sometimes we can do even better if a student helps me understand what matters to them. (Statement adapted from one by Prof. Krzysztof Gajos.)
