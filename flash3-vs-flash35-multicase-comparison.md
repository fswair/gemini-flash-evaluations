# Gemini 3.5 Flash vs Gemini 3 Flash Preview — Batch Evaluation Report

## Executive Verdict

| Decision Axis | Winner | Why It Wins Clearly |
|---|---:|---|
| **Overall benchmark winner** | **Gemini 3 Flash Preview** | Same pass rate and same coverage, but **7.24x faster**, **19.88x cheaper**, and **12.37x lighter in output tokens** |
| **Pure eval-suite depth** | **Gemini 3.5 Flash** | More total cases, deeper stress testing, broader structural coverage, and more full expected-output specs |
| **Best practical eval-generator model** | **Gemini 3 Flash Preview** | Produces sufficiently strong evals with dramatically better cost, latency, and token efficiency |
| **Most exhaustive tester** | **Gemini 3.5 Flash** | Generates **107 cases vs 81**, including deeper `flatten` stress cases and broader `parse_cron` syntax coverage |
| **Most scalable benchmark model** | **Gemini 3 Flash Preview** | Similar correctness signal with much lower runtime and cost |

## Final Scores

| Model | Pure Eval-Suite Quality | Overall Practical Score | Final Interpretation |
|---|---:|---:|---|
| **Gemini 3.5 Flash** | **91 / 100** | **79 / 100** | Stronger and deeper test-suite generator, but too slow, too expensive, and very output-heavy |
| **Gemini 3 Flash Preview** | **86 / 100** | **95 / 100** | Slightly less exhaustive, but clearly better as a practical eval-generation model |

## Raw Benchmark Metrics

| Metric | Gemini 3.5 Flash | Gemini 3 Flash Preview | Winner | Interpretation |
|---|---:|---:|---:|---|
| Evaluated scenarios | 2 | 2 | Tie | Same comparison set |
| Pass rate | **2/2** | **2/2** | Tie | Both models passed every evaluated scenario |
| Average coverage | **100.0%** | **100.0%** | Tie | No difference in benchmark-level coverage |
| Total cases | **107** | 81 | **3.5 Flash** | 3.5 generated **1.32x more cases** |
| Average cases/scenario | **53.5** | 40.5 | **3.5 Flash** | 3.5 is more exhaustive |
| Raises cases | 23 | **24** | **3 Flash Preview** | 3 Flash has slightly more error/exception cases |
| Snippets | **88** | 82 | **3.5 Flash** | 3.5 explored slightly more implementation behavior |
| Error snippets | **31** | 28 | **3.5 Flash** | 3.5 explored more failure/error paths |
| Refinements | 1 | **0** | **3 Flash Preview** | 3 Flash needed no refinement |
| Runtime | 356.93s | **49.31s** | **3 Flash Preview** | 3 Flash is **7.24x faster** |
| Cost | `$0.9472395` | **`$0.047637`** | **3 Flash Preview** | 3 Flash is **19.88x cheaper** |
| Input tokens | 59,099 | **49,014** | **3 Flash Preview** | 3 Flash uses fewer input tokens |
| Output tokens | 95,399 | **7,710** | **3 Flash Preview** | 3 Flash is **12.37x lighter in output tokens** |
| Total tokens | 154,498 | **56,724** | **3 Flash Preview** | 3 Flash is **2.72x lighter overall** |
| Requests | 7 | **6** | **3 Flash Preview** | 3 Flash required fewer total requests |

## Efficiency Multipliers

| Efficiency Claim | Value | Better Model |
|---|---:|---:|
| Faster | **7.24x** | Gemini 3 Flash Preview |
| Cheaper | **19.88x** | Gemini 3 Flash Preview |
| Less output-token-heavy | **12.37x** | Gemini 3 Flash Preview |
| Less total-token-heavy | **2.72x** | Gemini 3 Flash Preview |
| Less input-token-heavy | **1.21x** | Gemini 3 Flash Preview |
| More cases generated | **1.32x** | Gemini 3.5 Flash |
| More snippets generated | **1.07x** | Gemini 3.5 Flash |

## High-Level Quality Comparison

| Dimension | Gemini 3.5 Flash | Gemini 3 Flash Preview | Winner |
|---|---|---|---|
| Core correctness coverage | Excellent | Excellent | Tie |
| Benchmark coverage | 100% | 100% | Tie |
| Eval-suite depth | Deeper | Slightly shallower | **3.5 Flash** |
| Structural stress testing | Stronger | Good | **3.5 Flash** |
| Error-path testing | Strong | Slightly stronger by count | **3 Flash Preview** |
| Full expected-output usage | Stronger | More assertion-heavy in `parse_cron` | **3.5 Flash** |
| Compactness | Weak | Excellent | **3 Flash Preview** |
| Runtime efficiency | Weak | Excellent | **3 Flash Preview** |
| Cost efficiency | Weak | Excellent | **3 Flash Preview** |
| Practical benchmark suitability | Good but inefficient | Excellent | **3 Flash Preview** |

---

# Scenario Scoreboard

| Scenario | 3.5 Flash Status | 3 Flash Preview Status | 3.5 Coverage | 3 Flash Coverage | Pure Suite Winner | Practical Winner |
|---|---:|---:|---:|---:|---:|---:|
| `flatten` | PASS | PASS | 100.0% | 100.0% | **3.5 Flash** | **3 Flash Preview** |
| `parse_cron` | PASS | PASS | 100.0% | 100.0% | **3.5 Flash** | **3 Flash Preview** |

## Per-Scenario Efficiency

| Scenario | Speed Advantage | Cost Advantage | Output Token Advantage | Practical Winner |
|---|---:|---:|---:|---:|
| `flatten` | 3 Flash Preview **8.79x faster** | 3 Flash Preview **24.36x cheaper** | 3 Flash Preview **14.51x lighter** | **3 Flash Preview** |
| `parse_cron` | 3 Flash Preview **6.32x faster** | 3 Flash Preview **17.45x cheaper** | 3 Flash Preview **11.17x lighter** | **3 Flash Preview** |

---

# Scenario-Level Detailed Evaluation

## 1. `flatten`

### Result

| Metric | Gemini 3.5 Flash | Gemini 3 Flash Preview | Winner |
|---|---:|---:|---:|
| Status | PASS | PASS | Tie |
| Coverage | 100.0% | 100.0% | Tie |
| Cases | **47** | 35 | **3.5 Flash** |
| Raises cases | 7 | 7 | Tie |
| Snippets | **39** | 36 | **3.5 Flash** |
| Error snippets | **15** | 11 | **3.5 Flash** |
| Refinements | 1 | **0** | **3 Flash Preview** |
| Runtime | 160.99s | **18.31s** | **3 Flash Preview** |
| Cost | `$0.4095015` | **`$0.0168135`** | **3 Flash Preview** |
| Input tokens | 31,561 | **16,989** | **3 Flash Preview** |
| Output tokens | 40,240 | **2,773** | **3 Flash Preview** |
| Requests | 4 | **3** | **3 Flash Preview** |

### Case-Level Evidence

| Inference | Gemini 3.5 Flash Evidence | Gemini 3 Flash Preview Evidence | Winner |
|---|---|---|---:|
| Both models cover basic flat lists | `flat_integers`, `already_flat` | `flat_integers` | Tie |
| Both models cover empty lists | `empty_list` | `empty_list` | Tie |
| Both models cover simple nesting | `simple_nesting`, `right_nested`, `left_nested` | `list_of_single_item_lists`, `single_level_nesting` | Tie |
| 3.5 Flash better tests deep nesting | `nesting_level_9`, `nesting_level_50`, `deeply_nested_one_element`, `deep_strings_nesting` | `nesting_depth_10`, `extreme_nesting_single_element`, `deep_nesting_end_of_list`, `deep_nesting_start_of_list` | **3.5 Flash** |
| 3.5 Flash better tests wide structures | `wide_nested_list`, `extremely_wide_flat`, `large_dense_nesting_matrix`, `deep_and_wide` | Less extensive wide-list coverage | **3.5 Flash** |
| 3.5 Flash better tests empty nested structures | `nested_empty_mixed`, `deeply_nested_empty`, `all_empty_nested`, `sparse_lists` | `nested_empty_lists`, `all_empty_at_various_depths`, `nesting_complexity_empty_interspersed` | **3.5 Flash** |
| Both models test mixed primitive values | `flat_diverse_primitives`, `nested_diverse_primitives`, `mixed_all_primitives`, `falsy_values`, `nested_falsy` | `mixed_types_nested`, `falsy_truthy_values`, `contains_none`, `zero_and_false_differentiation` | Tie |
| 3.5 Flash tests dictionaries more deeply as opaque values | `dicts_as_primitives`, `nested_dicts` | `contains_dict` | **3.5 Flash** |
| 3 Flash Preview tests tuples as opaque values better | Limited tuple-specific coverage | `contains_tuple_opaque`, `opaque_tuples_with_nested_lists`, `error_tuple_input` | **3 Flash Preview** |
| Both models test strings as opaque values | `nested_strings`, `special_characters_strings`, `empty_strings_nested` | `list_containing_strings`, `non_list_iterable_string` | Tie |
| Both models cover non-list TypeError behavior | `none_input`, `string_input`, `integer_input`, `dict_input`, `float_input`, `bool_input`, `error_typeerror_0` | `error_none_input`, `error_str_input`, `error_int_input`, `error_dict_input`, `error_tuple_input`, `error_float_input`, `error_set_input`, `error_typeerror_0` | Tie / slight 3 Flash |
| 3.5 Flash has more invariant-style evals | `IsList`, `NoNestedListsLeft`, `FastEnough` | `ReturnTypeList`, `FlatteningInvariant` | **3.5 Flash**, though `FastEnough` can be environment-sensitive |

### `flatten` Verdict

| Question | Answer |
|---|---|
| Which model created the deeper suite? | **Gemini 3.5 Flash** |
| Which model was more practical? | **Gemini 3 Flash Preview** |
| Why? | 3.5 generated broader deep/wide nesting coverage, but 3 Flash achieved the same pass and coverage with **8.79x faster runtime**, **24.36x lower cost**, and **14.51x fewer output tokens** |

**Pure suite winner: Gemini 3.5 Flash.**  
**Practical winner: Gemini 3 Flash Preview.**

---

## 2. `parse_cron`

### Result

| Metric | Gemini 3.5 Flash | Gemini 3 Flash Preview | Winner |
|---|---:|---:|---:|
| Status | PASS | PASS | Tie |
| Coverage | 100.0% | 100.0% | Tie |
| Cases | **60** | 46 | **3.5 Flash** |
| Raises cases | 16 | **17** | **3 Flash Preview** |
| Snippets | **49** | 46 | **3.5 Flash** |
| Error snippets | 16 | **17** | **3 Flash Preview** |
| Refinements | 0 | 0 | Tie |
| Runtime | 195.94s | **31.00s** | **3 Flash Preview** |
| Cost | `$0.537738` | **`$0.0308235`** | **3 Flash Preview** |
| Input tokens | **27,538** | 32,025 | **3.5 Flash** |
| Output tokens | 55,159 | **4,937** | **3 Flash Preview** |
| Requests | 3 | 3 | Tie |

### Evaluator Style Difference

| Evaluator Style | Gemini 3.5 Flash | Gemini 3 Flash Preview | Interpretation |
|---|---:|---:|---|
| Full expected-output cases | **44** | 4 | 3.5 checks more complete outputs directly |
| Assertion cases | 0 | **25** | 3 Flash uses more targeted assertions |
| Raises cases | 16 | **17** | 3 Flash has one more invalid-input case |

This is one of the biggest quality differences in the batch.

3.5 Flash often validates the full parsed cron dictionary:

```yaml
expected:
  minute: [...]
  hour: [...]
  day_of_month: [...]
  month: [...]
  day_of_week: [...]
````

3 Flash Preview often validates narrower properties:

```yaml
assertion: "output['minute'] == [...]"
```

That makes 3 Flash Preview much more compact, but also slightly weaker as a full oracle. A buggy implementation could pass some assertion-only cases while still producing incorrect values in fields that were not asserted.

### Case-Level Evidence

| Inference                                            | Gemini 3.5 Flash Evidence                                                                                                                                                                                              | Gemini 3 Flash Preview Evidence                                                                                                                                              |               Winner |
| ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------: |
| Both models cover all-wildcard cron expressions      | `standard_wildcard`                                                                                                                                                                                                    | `all_wildcards`                                                                                                                                                              |                  Tie |
| Both models cover min/max boundaries                 | `min_boundary`, `max_boundary`                                                                                                                                                                                         | `specific_point_in_time`, `maximum_valid_boundaries`                                                                                                                         |                  Tie |
| Both models cover comma lists                        | `comma_lists`, `duplicate_values`                                                                                                                                                                                      | `comma_list_minutes`, `redundant_comma_values`, `hour_comma_list`                                                                                                            |                  Tie |
| Both models cover ranges                             | `simple_range`, `single_element_range`, `custom_hour_range`, `custom_dom_range`, `custom_month_range`, `custom_dow_range`                                                                                              | `range_minutes`, `single_value_range`, `day_of_week_full_range`, `disjoint_ranges`                                                                                           |     Tie / slight 3.5 |
| 3.5 Flash better covers wildcard steps               | `step_wildcard`, `wildcard_unary_plus_step`                                                                                                                                                                            | `step_wildcard_minutes`                                                                                                                                                      |        **3.5 Flash** |
| Both models cover range steps                        | `step_range`, `short_range_step`, `range_unary_plus_step`                                                                                                                                                              | `step_range_minutes`, `step_max_boundary_minus_one`, `step_larger_than_range`                                                                                                |                  Tie |
| Both models cover implicit step starts               | `step_implicit_range`, `implicit_unary_plus_step`                                                                                                                                                                      | `step_start_value`                                                                                                                                                           |                  Tie |
| Both models cover overlapping and dedup behavior     | `duplicate_values`, `overlapping_ranges`, `overlapping_unary_plus`, `unary_plus_duplicates`                                                                                                                            | `overlapping_ranges`, `complex_overlap_zero`, `redundant_overlapping_step_ranges`, `redundant_comma_values`                                                                  |                  Tie |
| 3.5 Flash better tests all cron fields uniformly     | `custom_step_minute`, `custom_step_hour`, `custom_step_day_of_month`, `custom_step_month`, `custom_step_day_of_week`                                                                                                   | `month_step_check`, `hour_comma_list`, `dow_comprehensive`                                                                                                                   |        **3.5 Flash** |
| 3.5 Flash strongly covers unary plus behavior        | `unary_plus_min`, `unary_plus_max`, `unary_plus_ranges`, `unary_plus_ranges_step`, `unary_plus_start_only`, `implicit_unary_plus_step`, `overlapping_unary_plus`, `unary_plus_oversized_step`, `unary_plus_duplicates` | Mostly absent                                                                                                                                                                |        **3.5 Flash** |
| 3 Flash Preview has strong malformed syntax coverage | `error_invalid_multi_dash`, `error_invalid_multi_slash`, `error_wildcard_dash_step`, `error_double_comma`                                                                                                              | 3.5 has `error_malformed_range_multiple_hyphens`, `error_multiple_slashes`, `error_empty_part_comma_separated`                                                               | Tie / slight 3 Flash |
| 3 Flash Preview tests negative step explicitly       | Not directly emphasized                                                                                                                                                                                                | `error_step_negative`                                                                                                                                                        |  **3 Flash Preview** |
| Both models test invalid field count                 | `error_fewer_fields`, `error_more_fields`                                                                                                                                                                              | `error_too_few_fields`, `error_too_many_fields`                                                                                                                              |                  Tie |
| Both models test out-of-range values                 | `error_step_start_out_of_range`, `error_step_end_out_of_range`, `error_single_less_than_low_limit`, `error_single_greater_than_high_limit`, `error_range_end_greater_than_high_limit`                                  | `error_minute_out_of_range`, `error_hour_out_of_range`, `error_dom_out_of_range`, `error_month_out_of_range`, `error_dow_out_of_range`, `error_step_range_end_out_of_bounds` |                  Tie |

### `parse_cron` Verdict

| Question                              | Answer                                                                                                                                                                                                                                                                                              |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Which model created the deeper suite? | **Gemini 3.5 Flash**                                                                                                                                                                                                                                                                                |
| Which model was more practical?       | **Gemini 3 Flash Preview**                                                                                                                                                                                                                                                                          |
| Why?                                  | 3.5 generated more cases and much stronger full-output checking, especially around unary plus, field-specific steps, and full cron dictionary validation. But 3 Flash achieved the same pass and coverage while being **6.32x faster**, **17.45x cheaper**, and **11.17x lighter in output tokens** |

**Pure suite winner: Gemini 3.5 Flash.**
**Practical winner: Gemini 3 Flash Preview.**

---

# Detailed Inference Mapping

| Inference                                                   | Gemini 3.5 Flash Evidence                                                                                            | Gemini 3 Flash Preview Evidence                                                 |                            Winner |
| ----------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | --------------------------------: |
| Both models reached perfect benchmark success on this batch | 2/2 pass, 100% avg coverage                                                                                          | 2/2 pass, 100% avg coverage                                                     |                               Tie |
| 3.5 Flash writes more exhaustive suites                     | 107 total cases                                                                                                      | 81 total cases                                                                  |                     **3.5 Flash** |
| 3.5 Flash does deeper `flatten` stress testing              | `nesting_level_50`, `wide_nested_list`, `large_dense_nesting_matrix`, `deep_and_wide`                                | `nesting_depth_10`, `extreme_nesting_single_element`                            |                     **3.5 Flash** |
| 3.5 Flash better covers nested empty-list behavior          | `nested_empty_mixed`, `deeply_nested_empty`, `all_empty_nested`, `sparse_lists`                                      | `nested_empty_lists`, `all_empty_at_various_depths`                             |                     **3.5 Flash** |
| 3 Flash Preview better covers tuple opacity in `flatten`    | Limited tuple-specific coverage                                                                                      | `contains_tuple_opaque`, `opaque_tuples_with_nested_lists`, `error_tuple_input` |               **3 Flash Preview** |
| 3.5 Flash better validates full `parse_cron` outputs        | 44 expected cases                                                                                                    | 4 expected cases                                                                |                     **3.5 Flash** |
| 3 Flash Preview is more assertion-heavy in `parse_cron`     | 0 assertion cases                                                                                                    | 25 assertion cases                                                              | Mixed: compact, but weaker oracle |
| 3.5 Flash better covers unary plus cron syntax              | `unary_plus_min`, `unary_plus_max`, `unary_plus_ranges`, `unary_plus_ranges_step`, `implicit_unary_plus_step`        | Mostly absent                                                                   |                     **3.5 Flash** |
| 3.5 Flash better covers per-field cron step behavior        | `custom_step_minute`, `custom_step_hour`, `custom_step_day_of_month`, `custom_step_month`, `custom_step_day_of_week` | `month_step_check`, `hour_comma_list`, `dow_comprehensive`                      |                     **3.5 Flash** |
| 3 Flash Preview has slightly more raises cases              | 23 raises                                                                                                            | 24 raises                                                                       |               **3 Flash Preview** |
| 3 Flash Preview is much faster                              | 356.93s                                                                                                              | 49.31s                                                                          |               **3 Flash Preview** |
| 3 Flash Preview is much cheaper                             | `$0.9472395`                                                                                                         | `$0.047637`                                                                     |               **3 Flash Preview** |
| 3 Flash Preview is much more token-efficient                | 154,498 total tokens                                                                                                 | 56,724 total tokens                                                             |               **3 Flash Preview** |

---

# Score Breakdown

| Category                    |  Weight | Gemini 3.5 Flash | Gemini 3 Flash Preview | Rationale                                                       |
| --------------------------- | ------: | ---------------: | ---------------------: | --------------------------------------------------------------- |
| Core correctness coverage   |      20 |               20 |                     20 | Both pass all scenarios with 100% coverage                      |
| Eval depth                  |      20 |               19 |                     16 | 3.5 has more cases and broader structural/syntax coverage       |
| Full oracle strength        |      15 |               14 |                     10 | 3.5 uses more full expected outputs, especially in `parse_cron` |
| Error-path testing          |      10 |                8 |                      9 | 3 Flash has slightly more raises cases                          |
| Edge-case diversity         |      15 |               14 |                     12 | 3.5 covers more deep/wide nesting and cron syntax variants      |
| Compactness                 |       5 |                2 |                      5 | 3 Flash is dramatically more concise                            |
| Runtime efficiency          |       5 |                1 |                      5 | 3 Flash is 7.24x faster                                         |
| Cost efficiency             |       5 |                1 |                      5 | 3 Flash is 19.88x cheaper                                       |
| Token efficiency            |       5 |                1 |                      5 | 3 Flash is 12.37x lighter in output tokens                      |
| **Overall Practical Score** | **100** |           **79** |                 **95** | 3 Flash wins clearly as a practical model                       |

---

# Final Judgment

| Category               |     Gemini 3.5 Flash |         Gemini 3 Flash Preview |
| ---------------------- | -------------------: | -----------------------------: |
| Test depth             |        **Excellent** |                      Very good |
| Oracle strength        |         **Stronger** | Good, but more assertion-heavy |
| Edge-case coverage     |         **Stronger** |                         Strong |
| Runtime                |                 Weak |                  **Excellent** |
| Cost                   |                 Weak |                  **Excellent** |
| Token efficiency       |                 Weak |                  **Excellent** |
| Benchmark practicality | Good but inefficient |                  **Excellent** |

## Final Winner: Gemini 3 Flash Preview

**Gemini 3.5 Flash is the better pure test-suite writer.**
It creates deeper, broader, more exhaustive evals, especially for `flatten` stress cases and `parse_cron` full-output validation.

But **Gemini 3 Flash Preview is the better benchmark model overall.**

It achieves the same pass rate and same coverage while being:

* **7.24x faster**
* **19.88x cheaper**
* **12.37x lighter in output tokens**
* **2.72x lighter in total tokens**

## Final Conclusion

| Question                                             | Answer                                                                                                                 |
| ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Which model writes deeper eval suites?               | **Gemini 3.5 Flash**                                                                                                   |
| Which model is better for practical eval generation? | **Gemini 3 Flash Preview**                                                                                             |
| Which model wins overall?                            | **Gemini 3 Flash Preview**                                                                                             |
| Why?                                                 | It preserves the same benchmark-level correctness signal while massively improving cost, latency, and token efficiency |

**Final winner: Gemini 3 Flash Preview.**
