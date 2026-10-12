# Task 3 V2 — Submission Form

## Case study*
**File:** `01_FDE_Case_Study_Client_B.pdf`

## One-page client note*
**File:** `02_Client_Management_Note.pdf`

## In two sentences: what is the client's real problem, and how is it different from what they asked for?*
The client wants AI to optimise nesting, but the underlying problem is that they cannot reliably measure material use, separate avoidable waste from reusable offcuts and revision-driven losses, or compare manual nesting with the automatic option they already own. Before building a new system, we need to establish a trusted baseline and test whether better configuration or a constrained optimisation layer can improve material use without creating manufacturing, scheduling or project-costing problems.

## Who are the people in this deal, and what does each of them need to hear from you?*
- **Cost Control contact (our current contact):** needs a defensible baseline, clear project-level cost attribution and an ROI calculation that does not count reusable offcuts as both savings and avoided scrap. I would be explicit about what we know and what still needs validating.
- **Nesting lead and nesting engineers:** need to see that the work will test their concern that auto-nesting performs worse, rather than dismissing their experience. They need feasible plans, visible reasons for recommendations, low disruption to the current process and the ability to approve, edit or reject every plan.
- **Engineering:** needs reliable drawing-version linkage and a way to distinguish losses caused by client changes from internal engineering errors.
- **Warehouse/yard and procurement:** need clear material identity, dimensions, quality, stock location and eligibility for reuse. I would not promise cross-project reuse until project allocation and accounting rules are approved.
- **CNC/factory operations:** need confidence that any recommended layout respects machine, cutting, handling and quality constraints. During the pilot, no plan goes directly from the tool to CNC without an authorised person approving it through the existing workflow.
- **IT / StruMIS and PLM owners:** need a low-risk integration approach, data access controls and no unnecessary ERP replacement. I would start with agreed exports before proposing API or production integration.
- **Management / budget owner:** needs staged spend, a clear first result, decision gates and evidence that a larger investment is justified before approving it.

## The five questions you would ask on the next call, ranked. For each one: why it matters, and what you assumed while you wait for the answer.*

**1. Can we obtain a matched history for at least 100 completed nesting jobs, including released parts/drawing versions, the manual nest, StruMIS automatic output where available, stock issued, actual consumption, scrap and retained offcuts?**  
**Why it matters:** Without job-level inputs and outcomes, the client cannot know how much waste is real or whether one method is better than another. This also determines whether a fair retrospective benchmark is possible.  
**Assumption until answered:** Some records exist in StruMIS/PLM or exportable reports, but they may not all join cleanly. If 100 comparable jobs are unavailable, I would use the largest representative sample that can be reconciled and document the limitation.

**2. Can the nesting lead walk us through a real job and list the rules that make a nest usable on the factory floor?**  
**Why it matters:** A layout that looks efficient on screen is no good if it violates material, geometry, kerf, orientation, machine, handling, sequence or quality requirements. It is also the fastest way to learn why operators prefer manual plans.  
**Assumption until answered:** Important rules are partly undocumented and held as operator knowledge. They must be captured and approved before the optimiser can be trusted.

**3. Can the same released drawing and available stock be used to compare the historical manual plan, StruMIS auto-nesting and any proposed optimiser? Can StruMIS be rerun or its output exported?**  
**Why it matters:** If inputs differ, the comparison is not fair. We must also separate a weak StruMIS configuration from a true limit of its optimisation engine.  
**Assumption until answered:** At least a subset of jobs can be replayed or compared with enough detail. If not, I would not claim one approach outperforms another; the initial work would focus on data and process measurement.

**4. How are offcuts identified, measured, checked for quality, located and allocated to a project—and under what rules, if any, can they be used on another project?**  
**Why it matters:** Offcuts only create value if they are physically available, compatible and eligible for the job. The notes say material cost is loaded to individual projects, so cross-project reuse may have commercial or accounting implications.  
**Assumption until answered:** I would restrict the first pilot to offcuts with reliable identification and to the project's approved allocation. Cross-project transfers remain out of scope until Cost Control and the relevant owners approve the rules.

**5. What is the agreed definition of waste and financial saving, and what are actual annual throughput and material costs by plate/profile family?**  
**Why it matters:** We need a common denominator and must account for scrap credits, usable remnants, handling and drawing revisions. The notes state about 80,000 tonnes annual capacity but also 7,000–8,000 tonnes per month; those figures do not reconcile exactly and capacity may not equal throughput.  
**Assumption until answered:** The reported 7–10% overall loss and material costs are directional only. I will not treat all reported loss as avoidable or use the stated capacity as verified annual input for a savings forecast.

## Which options did you consider, and why did you pick the one you did? What did you rule out, and why?*
I considered four main paths: (1) an analytics-only baseline, (2) configuring and improving the automatic nesting capability already in StruMIS, (3) a custom constrained-optimisation and offcut-matching layer around the existing workflow, and (4) a broad, fully automated platform covering nesting, revisions, the yard, trailers and equipment.

I recommend a **phased Nesting Intelligence engagement**: first measure the current process and benchmark manual nesting against StruMIS auto-nesting; then, if the existing feature cannot meet the agreed target after fair configuration, pilot a custom constrained optimiser with offcut matching and engineer approval. This is the best fit because it gives the client evidence early, reuses its existing systems and keeps production risk controlled.

I ruled out replacing StruMIS, sending unapproved plans directly to CNC, automatic cross-project material transfers, warehouse robotics/computer vision and solving all six operational areas in one build. They add complexity before the value and the data are understood. I also ruled out an LLM as the geometric nesting engine: the core task is constrained packing/optimisation, not language generation. An LLM may be useful for separate document-related tasks later, but it is not needed for the first pilot.

## How will the client know the pilot worked? Metric, baseline, threshold, how many runs, who measures, and what result would make you stop.*
- **Baseline:** Establish job-level material utilisation and the treatment of scrap/offcuts during discovery using reconciled historical jobs. Use the same parts, material availability and approved constraints across methods. Record actual consumption and outcome where available; do not compare jobs with materially different inputs as if they were equivalent.
- **Primary metric:** Material utilisation, calculated consistently as material incorporated into accepted required parts divided by stock input to the nesting job. Cost Control and the nesting lead must agree the denominator and how retained reusable offcuts are handled before testing. Track retained/reused offcuts separately so value is not double-counted.
- **Secondary metrics:** scrap rate, eligible offcut reuse, material-equivalent input avoided, time to prepare an approved nest, infeasible recommendation rate and operator acceptance. Financial value uses Cost Control-approved net avoidable material cost per tonne, after scrap credits and extra handling.
- **Test size/protocol:** Target at least **100 distinct historical jobs**, stratified by plate/profile, grade, thickness and complexity where the data allows. For each job, compare the manual baseline, StruMIS automatic nesting (rerun where possible) and the proposed optimiser, using matched inputs and a fixed time budget. If the optimiser is stochastic, run three seeds per job and report both the best feasible result and the variation; do not quietly compare only easy wins.
- **Who measures:** The FDE/data engineer prepares the comparison and logs; Cost Control signs off the metric and value calculation; the nesting lead validates feasibility and explains rejections; engineering confirms the drawing version and relevant revision effects.
- **Provisional success threshold:** At least **+1.0 percentage point aggregate material-utilisation improvement** over the manual baseline on the representative sample, with **zero critical constraint violations in plans approved for production** and median planning time not more than 10% higher unless the client explicitly accepts that trade-off. This is a pilot threshold, not a promised outcome.
- **Stop / narrow criteria:** Stop or redesign if the historical baseline cannot be reconciled, matched comparisons cannot be made, plans violate critical manufacturing constraints, improvement is not repeatable, or the net benefit does not justify build and running costs. If StruMIS meets the target after configuration, use that path and do not build a competing optimiser.

## What does this cost the client, and what does it cost us to deliver? Show the arithmetic and name the pricing structure. What value does the client get, in their money?*

**Proposed pricing structure:** phased fixed fees with explicit go/no-go gates. The client approves discovery first; the pilot is authorised only after data readiness; production integration is a separate decision after pilot evaluation.

**Client price:**
- Discovery and data audit: **₹3.00 lakh**.
- Nesting pilot: **₹12.00 lakh**.
- Production integration: **₹20.00 lakh**.
- Total to first production release: **₹35.00 lakh**, excluding GST, StruMIS/PLM licence upgrades, new hardware, major out-of-scope customisation and separately priced support.

**Payment milestones:** discovery: 50% at kickoff (₹1.50 lakh), 50% on delivery of findings/baseline (₹1.50 lakh). Pilot: 40% at start (₹4.80 lakh), 40% at benchmark/demo (₹4.80 lakh), 20% on pilot evaluation (₹2.40 lakh). Production: 30% at kickoff (₹6.00 lakh), 40% at user acceptance (₹8.00 lakh), 30% at go-live (₹6.00 lakh).

**Internal delivery-cost estimate (planning assumptions, not supplier actuals):**
- Discovery: FDE 6 days × ₹10,000 = ₹60,000; data/integration 4 × ₹8,000 = ₹32,000; optimisation 3 × ₹10,000 = ₹30,000; manufacturing SME/QA 2 × ₹7,000 = ₹14,000. **15 person-days = ₹1.36 lakh.**
- Pilot: FDE 10 × ₹10,000 = ₹1.00 lakh; optimisation 24 × ₹10,000 = ₹2.40 lakh; data/integration 18 × ₹8,000 = ₹1.44 lakh; SME/QA 8 × ₹7,000 = ₹0.56 lakh. **60 person-days = ₹5.40 lakh.**
- Production: FDE 12 × ₹10,000 = ₹1.20 lakh; optimisation 20 × ₹10,000 = ₹2.00 lakh; data/integration 30 × ₹8,000 = ₹2.40 lakh; SME/QA 12 × ₹7,000 = ₹0.84 lakh. **74 person-days = ₹6.44 lakh.**
- Direct role-cost total: **149 person-days = ₹13.20 lakh**.
- Additional internal delivery overhead for non-billable project coordination, documentation, QA and handover (assumption): **₹3.00 lakh**.
- Test/deployment environment and implementation-period infrastructure (assumption): **₹1.50 lakh**.
- Delivery-risk contingency (15% of direct role cost: ₹13.20 lakh × 15%): **₹1.98 lakh**.
- Estimated internal delivery cost: ₹13.20 + ₹3.00 + ₹1.50 + ₹1.98 = **₹19.68 lakh**. Against ₹35 lakh in phased fees, the estimated contribution is **₹15.32 lakh** before sales/corporate overhead, tax and any costs outside these assumptions. These estimates should be replaced by the delivery team's actual rates and scope review before a binding quote.

**Ongoing client cost:** hosting, database/storage, backups and monitoring are estimated at **₹25,000–₹65,000 per month**. A separate support retainer may be **₹1.0–₹1.5 lakh per month**, depending on SLA and included hours. Combined indicative monthly run/support cost is ₹1.25–₹2.15 lakh, excluding third-party licences and taxes.

**Value to the client:** no actual savings can be claimed before the baseline and pilot. As sensitivity only, if actual annual throughput were 80,000 tonnes and a 1 percentage-point utilisation change translated into 800 tonnes of material-equivalent change, then at an illustrative ₹10,000 per tonne of net avoidable material cost, the gross annual value would be 800 × ₹10,000 = **₹80 lakh**, before implementation, hosting and support costs. This is not a forecast: ₹10,000/tonne is an assumption, the stated 80,000 tonnes is capacity rather than confirmed throughput, and Finance must validate the metric-to-tonnes conversion. If the pilot demonstrates value, annual net benefit is verified material purchase cost avoided plus other verified savings, minus scrap-credit changes, additional handling, service fees, hosting and support.

## Timeline. What is the first result the client sees, and when? Which steps depend on the client rather than on us?*
- **Weeks 1–2 — discovery/data audit:** the first result is a short baseline and feasibility report: which records can be reconciled, the current KPI definitions, major data gaps, the main manufacturing constraints, a benchmark plan and an initial ROI sensitivity. This depends on the client sharing historical exports and making Cost Control, nesting and IT available.
- **Weeks 3–4 — benchmark/prototype setup:** compare the existing manual plans with StruMIS automatic nesting on matched jobs; decide whether configuration alone is sufficient or a custom optimisation prototype is justified. Depends on access to comparable plans, material outcomes and a nesting engineer to validate constraints.
- **Weeks 5–8 (following data readiness) — pilot evaluation:** demonstrate the reviewer workflow and compare results on the agreed sample. Timing depends on the number and quality of usable jobs, the ability to rerun StruMIS jobs, and timely feedback from operators.
- **Weeks 9–20 — possible production integration:** an additional 8–12 weeks only after a positive pilot gate, signed scope and access to supported StruMIS/PLM interfaces. This is not committed until approved.

Client dependencies include timely access to data and software owners, drawing/version and material mapping, manufacturing constraints, Cost Control-approved material costs and scrap treatment, operator review time, and approval of project allocation rules. If those are delayed or records cannot be reconciled, I would revise the schedule rather than claim the model is progressing normally.

## Where did you push back on the client, narrow their ask, or tell them not to do something? [can only raise your score]*
I pushed back on the assumption that the answer must be a new AI system. StruMIS already has automatic nesting, so the first step is to test it fairly and check whether configuration or better inputs solve the issue. I narrowed the first engagement to nesting and offcut decisions instead of tackling nesting, drawing revisions, yard storage, trailer loading and equipment utilisation all at once. I also excluded direct CNC release and automatic cross-project stock transfer from the pilot. Finally, I would not turn the reported 7–10% waste into a savings promise: some loss may be unavoidable, some offcuts may still have value, and some loss may be caused by drawing revisions.

## What is most likely to go wrong with your plan, and what in these notes did you not trust? [can only raise your score]*
The biggest risk is that historical records do not connect the drawing version, nest, issued material, actual cut result and remaining offcuts well enough to make a fair comparison. The next risk is that the nesting team's practical rules are undocumented; the algorithm could make a better-looking layout that is slower or impossible to cut. StruMIS may also be difficult to rerun on historical inputs, and the potential improvement may be too small to justify a separate optimiser.

I would treat these points in the notes as unverified rather than facts: (1) the overall 7–10% waste figure and the plate/profile ranges, because the denominator and measurement method are not defined; (2) the belief that automatic nesting wastes more than manual nesting, because there is no matched benchmark; (3) the 80,000-tonne annual capacity alongside 7,000–8,000 tonnes per month, which implies 84,000–96,000 tonnes a year and needs reconciliation; (4) the amount of material that can be recovered from offcuts, because dimensions, quality, location and project eligibility are unclear; and (5) attribution of material losses to internal engineering errors versus client revisions, because revision-level history is described as incomplete. I have not assumed that I reviewed the original Word document or the client's web platforms; they were not included in the materials supplied for this case study.

## What did you use AI for? Which tools, where they helped, where they misled you, and what you threw away.*
I used **ChatGPT** to organise the supplied discovery notes, challenge the initial solution choice, structure and edit the case study and client note, and check the evaluation and cost arithmetic. It helped surface the need to compare StruMIS automation against manual nesting, separate the business baseline from the solution, and make assumptions and stop conditions explicit.

The main risk was that AI-generated proposals can sound more certain than the evidence supports. In particular, the reported waste percentages could easily be turned into an unjustified savings claim, and the request for “AI” could lead to an LLM-first design. I corrected for this by treating all savings as conditional, flagging the throughput discrepancy, and recommending constraint-aware optimisation rather than an LLM for geometric nesting. I discarded a broad all-operations AI transformation, a claim that the whole waste figure was recoverable, automatic CNC control, unapproved cross-project material transfer, and a synthetic demo presented as proof of client value. I did not train or evaluate a model on client data, access a client system, or use a paid external model API. No prototype was built because the brief makes it optional and the key question needs real historical data.

## Github Repo URL
**N/A — no prototype repository submitted.** The prototype is optional; I have not created a repository that would imply a validated nesting implementation. The case study and client note are provided as files.
