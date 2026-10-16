# Improved coordination: mechanical cloaking

Completed exploratory follow-up on the original supplied assignment. Both arms received the same 18-trial archived history and 30 distinct new full-resolution FEM evaluations, in ten rounds of three.

| Method | Retained masked displacement loss | Relative reduction from supplied assignment |
| --- | ---: | ---: |
| Supplied assignment | 12.761049% | — |
| Adaptive numerical search | 11.630822% | 8.857% |
| Coordinated hybrid | 10.694605% | 16.193% |

The hybrid final loss is 8.049% lower than this numerical comparator in this case. This compares displacement-loss norms, not squared losses.

## Coordination that was executed

One slot per hybrid round came from the same adaptive numerical optimizer. Response and interface specialists shared the hybrid measurement ledger, coordinated complementary hypotheses, and supplied the other two slots. A coordinator validated candidate eligibility, the four-cell cap, and full-assignment novelty before hash-committing all three proposals. Only lower finite full-resolution loss with force residual below 1e-7 could be retained. Failed proposals remain in the record.

Examples include transferring empirically useful blocks, testing smaller subsets after failed compositions, testing extensions of successful interface bands, and a round-nine matched comparison of a pair with versus without a singleton reversion. No scalar macro score was accepted as an actual FEM outcome.

## Retained trajectory

| Round | Evaluations per method | Numerical loss (%) | Hybrid loss (%) | Hybrid retained proposal |
| ---: | ---: | ---: | ---: | --- |
| 1 | 3 | 12.761049 | 12.545021 | agent_response |
| 2 | 6 | 12.756484 | 12.150600 | agent_response |
| 3 | 9 | 12.753283 | 11.857962 | agent_response |
| 4 | 12 | 11.980758 | 11.723329 | agent_response |
| 5 | 15 | 11.945736 | 11.500134 | agent_interfaces |
| 6 | 18 | 11.906258 | 11.302764 | agent_interfaces |
| 7 | 21 | 11.831545 | 11.204944 | agent_response |
| 8 | 24 | 11.777805 | 10.961472 | agent_response |
| 9 | 27 | 11.661216 | 10.780012 | agent_response |
| 10 | 30 | 11.630822 | 10.694605 | agent_interfaces |

Hybrid round winners: agent_response: 7, agent_interfaces: 3.

## Verification and limits

audit.json verifies 30 new distinct assignments per arm, no cached proposal evaluations, all 20 commitment hashes, valid changes, strict objective-based retention, identical prior ledgers, and unchanged scientific solver/feedback/numerical-selector code hashes. force_balance.json independently checks final element forces and support reactions. The underlying full-resolution port was previously validated against the supplied reference displacement (relative monitored difference about 1.3e-10); those original validation records are retained in the earlier archive.

This study uses one supplied loading case and one exploratory run. The specialists had prior conversational familiarity; both methods were given the same historical trial ledger. Numerical selection is a fixed policy, while specialist reasoning adapts. FEM counts are matched, but agent latency and token cost are not controlled. The comparison supports this hybrid versus this numerical policy on this case; it does not establish universal LLM superiority or isolate coordination causally from every policy difference. A matched 30-evaluation uncoordinated swarm control was not run.

Connectivity, material fraction, and interface costs are reported, not imposed as additional constraints. This remains the supplied linear ersatz-material model; mesh, loading generalization, and fabrication validation are outside this experiment. The manuscript source has not been revised to claim these results.

## Files

trials.csv preserves every new candidate, including failures. Arm round folders preserve feedback, specialist reasons, proposals, commitment hashes, outcomes, and state. MATLAB-compatible retained assignments are numerical_retained_labels.mat and hybrid_retained_labels.mat. See REPRODUCE.txt for dependencies, separate author inputs, literal-action replay, and the scratch-cache migration note.
