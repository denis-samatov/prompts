# Evaluating a prompt variant

This is a small educational catalog, not a validated prompt library. No model
requests or evaluation results are included. Illustrative outputs are authored
examples, not measurements.

For a specific use case:

1. Freeze a versioned test set with inputs, independent reference answers and
   explicit failure conditions. Keep development examples outside the held-out set.
2. Compare the plain instruction and one changed prompt on the same inputs.
   Record model/provider version, prompt text/hash, parameters, seed if supported,
   date, tools, source versions and retries. Never assume a hosted alias is fixed.
3. Store raw outputs and score them against the same rubric. For code, execute
   independent tests in isolation; for factual questions, verify cited sources.
   Agreement between sampled outputs is not an independent correctness check.
4. Report per-case failures, paired aggregate results, uncertainty, tokens, cost
   and latency. Review unsupported claims separately from formatting errors.
5. State dataset and model boundaries; a synthetic smoke test does not qualify
   medical, financial or production use. Keep private data and credentials out
   of the repository and obtain permission before sending them to providers.

Suggested result columns: `case_id, split, prompt_revision, model_revision,
parameters, reference_revision, output_path, correct, failure_kind, tokens,
latency_ms, cost, evaluator_revision`. Publishing a comparison requires actual
raw results; this template supplies none.
