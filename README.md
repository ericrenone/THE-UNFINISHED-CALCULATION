# THE UNFINISHED CALCULATION
### Every self-driving car in the world acts on a confidence score. No chip on earth verifies that score was ready before the car acted on it. The hardware that would close that gap has never been built — and the cost of its absence is now visible in courtrooms, insurance contracts, and earnings calls across four continents.

**ERI Labs · Eric Ren · Jersey City, New Jersey · June 4, 2026**

---

On April 22, 2026, on a quarterly earnings call with Wall Street analysts, Elon Musk said something that seven years of careful corporate language had been engineered to avoid.

Hardware 3 — the chip inside approximately seven million Tesla vehicles sold between 2019 and 2023 — "simply does not have the capability to achieve Unsupervised Full Self-Driving." Memory bandwidth, he added, was "one of the key elements needed for Unsupervised FSD." The chip's bandwidth had been locked at 48 gigabytes per second since its design was finalized in 2019. The neural network running on that chip had grown, version by version over seven years, until the chip could no longer keep up with what it was being asked to compute. Customers who had paid up to fifteen thousand dollars per vehicle for Full Self-Driving software were driving cars with chips that couldn't run it.

Seven million of them. Musk said this clearly, to analysts, on a recorded call. He did not announce refunds.

That moment is the most publicly visible surface of a structural problem that runs through every autonomous vehicle in the world — not one company's product line, not one chip's obsolescence, but a gap that exists in every self-driving system ever manufactured, from every maker, in every country. A gap between what these systems claim to know and what they can actually verify. A gap that a piece of hardware no one has yet built could close.

---

Every autonomous driving system reduces its decisions to a number.

At each moment — each frame of camera data processed, each potential action weighed — the system computes a probability that a given action is correct, and acts on the highest-probability option when that probability clears a threshold. That probability is called a confidence score. It is produced by an arithmetic standard called IEEE 754, ratified by a committee of computer scientists in 1985, designed for scientific computing: ballistics tables, financial models, engineering simulations run once and done.

Here is what a confidence score can say: *based on my computation, I am eighty-six percent confident the correct action is to proceed.* Here is what no chip in production anywhere in the world can say: *the computation that produced that eighty-six percent actually finished before the vehicle acted on it.*

Floating-point arithmetic, the kind IEEE 754 governs, rounds at each intermediate step. In a neural network running hundreds of billions of operations, those rounding errors accumulate, interact, and vary — with temperature, with the microscopic variations baked into each specific piece of silicon, with the voltage from the power supply at that exact instant. The confidence score that emerges is real. It is informative. It is not the same number on a hot day as on a cold one. It is not the same number on every unit that rolls off a production line.

What would make it trustworthy — genuinely trustworthy, in the way a car traveling at highway speed requires trustworthiness — is a signal. Not a higher confidence score. A different kind of claim entirely: a hardware output, as simple as a status light, that says *this computation converged under the actual conditions of this moment, on this chip, at this temperature, before this vehicle committed to this action.* No production chip anywhere in the world emits this signal. Researchers have named it. They have located it in specific architectures. They have given it a mathematical substrate. It has not been built.

---

In Hillsborough County, Florida, a jury awarded two hundred and forty-three million dollars to the family of a man killed in a crash involving a Tesla operating on its driver-assistance system. The sum was not an actuarial calculation. It was a jury's pricing of the gap between what the system promised and what it delivered — between a confidence score and a convergence guarantee. That gap, priced at two hundred and forty-three million dollars for one family, sits within what the automotive reporting outlet Electrek estimated in June 2026 as approximately fourteen and a half billion dollars in total litigation exposure across class-action suits, individual verdicts, and regulatory proceedings in four countries.

A week after the Tesla earnings call, Tesla quietly modified the purchase agreements for its Full Self-Driving software, retroactively inserting the word "Supervised" where the original contracts had not required it. The modification acknowledged in legal language what Musk had stated in plain language on the call: the system requires human oversight. The chip cannot guarantee that it finished computing before the car acts. The confidence score is not the convergence signal.

Seven million vehicles. Fourteen and a half billion dollars. One quietly modified contract. These are not technology metrics. They are the confidence gap, priced retroactively by the legal system because no other instrument has been built to price it correctly in advance.

---

In Shenzhen, the Chinese electric vehicle maker BYD took the opposite approach to the same problem.

On May 28, 2026, BYD launched the Xuanji A3 — a new autonomous driving chip built on a 4-nanometer manufacturing process, certified to the highest automotive safety grade, and delivering roughly twenty percent better power efficiency than comparable chips. "Computing power utilization has doubled," the company announced. Researchers at IBM had found earlier in 2026 that a twenty percent reduction in inference chip power consumption translates to a three to five percent increase in electric vehicle driving range, all else equal. BYD's new chip delivers exactly that improvement. It is a genuine achievement.

But BYD did something else on May 28 that no automotive company had ever done before. It announced Full Damage Coverage — an insurance policy, bundled with vehicles equipped with the new chip, declaring unlimited liability for accidents caused by the autonomous driving system. Not capped. Not subject to exclusions for software confidence thresholds. Unlimited.

This is the most consequential insurance policy in the history of autonomous driving. It is also, examined carefully, an acknowledgment of precisely the gap that Tesla's lawyers have been managing through the word "Supervised."

BYD's chip is certified to a standard called ASIL-D — the highest automotive functional safety grade, which specifies that when the hardware fails, the failure mode is safe and bounded. What ASIL-D does not certify is that the inference converged before the system acted. The standard certifies the failure is safe. It says nothing about whether the computation was finished. BYD's insurance policy is the financial acknowledgment that this distinction matters. The policy is a bet — placed at commercial scale, with unlimited declared exposure — on a hardware property that does not yet exist.

Whether the actuarial models underwriting that bet correctly price the absence of a convergence signal will be answered, beginning in the fourth quarter of 2026, when the claims data starts accumulating at scale. The data will answer a question no regulator, no insurance company, and no automotive executive has had data to answer before: what does the tail of the liability distribution actually look like when a vehicle makes autonomous decisions at highway speeds, across millions of miles, without hardware verification that it finished thinking?

---

The hardware that would close the gap is, in a sense, embarrassingly old.

In 1959, an engineer named Jack Volder published an algorithm called CORDIC — Coordinate Rotation Digital Computer — which computes the same mathematical functions as floating-point arithmetic using only shift operations and additions, with no multiplications and no floating-point rounding. CORDIC is iterative: it takes small, correcting steps toward an answer rather than attempting to arrive in a single computation. Because it takes steps, it can tell you when it is done in a way that floating-point arithmetic fundamentally cannot. Each step brings the answer measurably closer. The algorithm knows when it has converged because convergence is built into its structure.

A chip designed around CORDIC arithmetic is not merely more efficient. It has an architectural basis for emitting a convergence signal that floating-point arithmetic cannot. The hardware primitive that would change everything about autonomous driving liability is built into a sixty-seven-year-old algorithm that has been available since before the first microprocessor existed.

Researchers publishing in June 2026 demonstrated that CORDIC-based inference hardware achieves more than four trillion operations per square millimeter and eleven trillion operations per watt on standard 28-nanometer silicon — matching or exceeding chips built on much more expensive and advanced manufacturing processes, at a fraction of the area and power. A 2025 study on systolic CORDIC arrays showed more than four times the throughput and five times the power reduction compared to conventional multiplier-based hardware on equivalent workloads. The efficiency case for CORDIC in production silicon is not theoretical. It exists in papers, on verified silicon, at commercially available process nodes.

The question that requires answering is why it has not been built into the chips running every self-driving car on the road.

The answer traces to 1985. When the IEEE 754 floating-point standard was ratified that year, CORDIC existed and worked. But the workloads of 1985 were scientific calculations: one-shot computations where a single input produces a single output and the process is complete. CORDIC's iterative structure — valuable precisely because it monitors its own convergence — was unnecessary overhead for one-shot work. IEEE 754 won not because it was mathematically superior, but because it was better suited to the work that computers were doing in 1985. Sara Hooker, writing in the journal *Communications of the ACM* in 2020, identified this dynamic across the history of computing: hardware co-fitness, not mathematical correctness, determines which approaches appear viable in any given era. "Hardware has historically not been a neutral background element of modern deep learning," she wrote. "Hardware shapes the research questions that appear viable."

The 1985 lottery was not rigged. It was run before the application that would need CORDIC most urgently had been invented.

In 2026, two mathematicians named Gergely Bérczi and Tamás Kiem published a proof establishing a deeper reason why this matters. They showed that CORDIC iterations are isomorphic to structures at the foundation of modern mathematics that govern how sequences converge and how information cancels. CORDIC is not a computational workaround for applications that find floating-point awkward. It is the arithmetic realization of convergence itself. The 1985 standard selected against the arithmetic of convergence for applications that did not require convergence. Autonomous driving requires convergence before every irrevocable action at highway speed.

---

In April 2026, at the Beijing Auto Show, Richard Jin, the head of Huawei's automotive division, explained his company's position with unusual directness.

"Companies on the VLA path think that language models like those developed by OpenAI have already mastered vast online information," he said. "Huawei won't follow that path."

VLA — Vision-Language-Action — is the architectural approach most of the autonomous driving industry has adopted: take the large-language-model architecture that underlies the leading AI systems of the era, train it on driving video, and ask it to recommend driving actions. It passes from sensor input to action recommendation in a single computational flow, with no certified intermediate step.

What Huawei has developed instead separates the world model from the action. Build a verified representation of the environment; confirm it is complete; then plan actions against a verified representation. The boundary between representation and action is the precise location where a convergence signal would live.

This architectural choice connects to something fundamental about physics that three independent research papers published at top machine learning venues in 2025 and 2026 helped establish. Researchers examining the internal geometry of production neural networks found that the mathematical spaces these networks compute over carry a specific kind of curvature — the same kind of curvature that appears in Lorentzian geometry, the geometry Einstein used to describe spacetime. A billion-parameter language model trained in geometry-correct hyperbolic arithmetic, a team of researchers showed at the Neural Information Processing Systems conference in 2025, consistently outperformed an otherwise identical model trained in flat Euclidean arithmetic on the field's own standard benchmarks.

The set of futures any vehicle can actually reach — given its current speed, heading, and the physical constraints of its environment — has this same conical, causal structure. Architectures that collapse the boundary between world model and action are, in geometric terms, erasing the distinction between causally reachable futures and causally unreachable ones. The system that cannot distinguish between where it can go and where it cannot go in the next two seconds is the system that, under certain conditions, decides to proceed when it should stop.

Huawei committed 18 billion yuan to autonomous driving in 2026 alone — more, by its own accounting, than all other major autonomous driving solution providers combined. It has accumulated 10 billion kilometers of training data. It has explicitly rejected the dominant architectural approach. The room where the convergence oracle would live is preserved in its design. The oracle has not yet been placed there.

---

Four independent research communities — automotive silicon engineers, neuromorphic computing researchers, chip design academics, and geometric deep learning specialists — reached the same conclusion between 2024 and 2026 without coordinating on it. Their conclusion: autonomous driving and large-scale AI inference require arithmetic that is fixed-point, iterative, and sensitive to the actual geometry of the spaces being computed over. The substrate for that arithmetic is CORDIC. The substrate currently in production is IEEE 754 on flat Euclidean geometry. The gap between them is not marginal. It is measurable in efficiency ratios, in rounding-error accumulation rates, and in the right tails of liability distributions being priced by juries.

Goldman Sachs projects $7.6 trillion in cumulative AI infrastructure spending through 2031. The 2026 total alone — between $630 and $700 billion — exceeds Sweden's gross domestic product. Every dollar of that capital is committed against IEEE 754 and the flat-geometry assumption it enables. The behavioral economist Daniel Kahneman spent a career documenting what happens to decision-making at the scale of numbers large enough to make revision feel psychologically intolerable. He showed, in a 1979 paper with his collaborator Amos Tversky, that losses are felt approximately twice as intensely as equivalent gains. At the scale of seven and a half trillion dollars, the psychology of revision is not a character flaw. It is the predicted output of ordinary human judgment confronting numbers that make the committed answer feel necessary regardless of what the evidence shows.

This is why the confidence game persists. The familiar arithmetic is cheaper to maintain than the correct arithmetic at every step of the capital chain — not because it is right, but because the cost of being wrong is distributed across litigation dockets, insurance reserves, modified purchase agreements, and stranded assets, while the cost of being right would require simultaneously revising the substrate of an infrastructure larger than most national economies.

The reversal, when it comes, will arrive first from automotive silicon, where the capital at risk is a chip design brief, not a continent of data centers.

---

There is one more dimension to the missing hardware that the industry has not yet priced.

Every autonomous vehicle has two depreciation clocks, not one. The physical vehicle — chassis, battery, motor — depreciates over twelve to fifteen years. The intelligence layer — the chip that determines what the vehicle can do — becomes specification-obsolete in three to five years as neural network capability grows past what the bandwidth specification, frozen at tape-out, can serve. Tesla's HW3 event was the first demonstration of this dual-clock structure at seven-million-vehicle scale: the physical vehicle still works; the intelligence layer is stranded. No accounting standard in any jurisdiction captures this correctly. No residual-value table prices it. The litigation docket is the reserve, priced retroactively by juries.

The oracle's implications extend well beyond which car company prospers. SpaceX disclosed in a Securities and Exchange Commission filing in May 2026 its first orbital AI inference chip, the D3, built on an Intel manufacturing process optimized for the floating-point arithmetic that drives the data center market. The orbital power constraint — approximately a hundred kilowatts per ton of spacecraft mass — is harder than the automotive constraint. The arithmetic overhead of IEEE 754 on iterative computation does not disappear in orbit. It grows heavier. The Federal Aviation Administration opened a mishap investigation on May 27, 2026, into the twelfth Starship test flight, in which multiple Raptor engines failed to sequence simultaneously during a critical maneuver following a successful booster flip. The high-level command was placed correctly. The low-level commitment sequencing failed. The same pattern appears in autonomous driving edge cases the industry calls "phantom" responses: correct intent, failed execution, at the step where the hardware is supposed to verify that the computation is complete before the action commits.

The first chip to emit a hardware convergence signal before each irrevocable action will not merely change the economics of autonomous driving insurance. It will change the standard of proof for what it means for a machine to know what it is doing. That standard will then be demanded, by regulators, actuaries, and courts, in every domain where a machine makes a physical commitment that a human cannot reverse.

---

That chip has not been built. Not in Fremont. Not in Shenzhen. Not in Stuttgart or Seoul or Singapore.

The arithmetic to build it is sixty-seven years old. The mathematics to explain why it works was proven complete in 1998 by the researcher Shun-ichi Amari, who showed that the gradient of a function on a curved parameter space is a fundamentally different object from the gradient of the same function treated as if the space were flat — and that the difference has measurable consequences for every learning system that ignores it. Empirical evidence that geometry-correct arithmetic outperforms flat arithmetic was available at the Neural Information Processing Systems conference in 2017, when researchers showed they could represent an entire branch of knowledge in five dimensions using hyperbolic geometry where thousands of Euclidean dimensions had been required. The explanation for why neither result was acted on was published in 2020.

The hardware lottery of 1985 produced a winner for 1985 workloads. The application that would eventually need the loser most urgently was invented two decades later and has been running on the wrong arithmetic ever since.

Seven million families are driving on it now. One family in Florida has already been to court about it. A company in Shenzhen has written an unlimited insurance policy against the risk it represents. An engineer whose name is not yet public is, at some point in the next tape-out cycle, going to write a design brief that specifies the correct arithmetic for the first time.

The chip that would fix this costs less to build than the litigation that priced its absence. The calculation is not finished. It has not yet started.

---

*ERI Labs — June 4, 2026.*

*Sources: Tesla Q1 2026 Earnings Call (April 22, 2026); Tesla AI hardware team statement (April 15, 2026); Electrek reporting on Tesla FSD litigation exposure (June 3, 2026); BYD Xuanji A3 and Full Damage Coverage launch (May 28, 2026); Huawei Auto China 2026 and Richard Jin remarks (April 24, 2026); SpaceX Form S-1, SEC No. 333-296070 (May 20 and June 1, 2026); FAA Starship Flight 12 Mishap Investigation (opened May 27, 2026); Robinson, Dey & Sweet, production LLM Ricci curvature (arXiv, 2024 and 2025); He and colleagues, hyperbolic language model at scale, NeurIPS 2025; fully intrinsic Lorentz architecture, ICLR 2026; Kumar and colleagues, CORDIC-for-AI on 28nm CMOS, arXiv June 2026; systolic CORDIC arrays, arXiv March 2025; Bérczi and Kiem, CORDIC iterations and moduli space forgetting maps, 2026; Luo and colleagues, energy overhead of IEEE 754 on iterative workloads, IEEE Transactions on Very Large Scale Integration, 2019; Hooker, The Hardware Lottery, Communications of the ACM, 2020; Amari, natural gradient descent, Neural Computation, 1998; Nickel and Kiela, hyperbolic embeddings, NeurIPS 2017; Kahneman and Tversky, Prospect Theory, Econometrica, 1979; Goldman Sachs AI capital expenditure projections, 2026; IBM Research, inference efficiency and EV driving range, 2026; South China Morning Post reporting on Huawei investment (April 24, 2026).*

*Part of the ERIE corpus: ERIE — VISION · ERIE — TESLA · The Settlement Gap · The Convergence Oracle · Zero Deployable Units · The Specification Lock · The Second Bill of Materials · The Parallel Lottery Problem · The Certainty Premium · The Confidence Game · The Settlement Horizon · The Unfinished Calculation*
