# AgentArk (Chop Shop Refactor)

This repo was passed through a targeted stabilization/refactor process and updated in-place.  
Original files were preserved, and no files were removed from the original archive.

## What Changed

### Core Stability Improvements
- Refactored method registration and resolution to be safer and deterministic.
- Improved inference workflow with:
  - JSON/JSONL input handling
  - dry-run mode
  - resume behavior
  - safer batching and output cardinality checks
  - cleaner error handling for failed/incomplete responses
- Strengthened evaluation logic for more robust metric computation across workflows.
- Added strict validation around API/model configuration and safer auth handling.
- Reduced eager imports to improve startup reliability in constrained environments.

### New Infrastructure
- Added offline-only evaluation entrypoint:
  - `eval/saved_results.py`
- Added reusable JSONL utilities with:
  - UTF-8 BOM support
  - blank-line tolerance
  - strict object-row validation
  - atomic/safe write behavior
  - concurrent append handling
- Added targeted CI workflow for offline/stdlib checks:
  - `.github/workflows/offline-tests.yml`

### Added Files
- `CHOP-SHOP-REPORT.md`
- `OPERATIONS.md`
- `eval/__init__.py`
- `eval/saved_results.py`
- `examples/input.jsonl`
- `examples/predictions.jsonl`
- `LICENSES/ToRA-MIT.txt`
- `requirements-api.txt`
- `requirements-eval.txt`
- `tests/test_regressions.py`
- `THIRD-PARTY-NOTICES.md`
- `utils/jsonl.py`
- `utils/numeric.py`
- `model_api_configs/model_api_config.example.json`

### Updated Files (Representative)
- `evaluate.py`, `inference.py`, `label.py`
- `eval/calculate_metrics_numeric.py`
- `eval/calculate_metrics_short_answer.py`
- `eval/evaluate.py`
- `eval/math_eval.py`
- `eval/medmcqa_eval.py`
- `eval/parser.py`, `eval/process.py`
- `eval/eval_utils.py`, `eval/data_loader.py`
- `methods/__init__.py`, `methods/dylan/__init__.py`
- `methods/llm_debate/llm_debate_main.py`
- `methods/mas_base/mas_base.py`
- `requirements.txt`
- `utils/__init__.py`, `utils/utils.py`

### Third-Party Provenance
This pass includes an adapted nested-boxed-answer utility sourced from Microsoft’s ToRA project.
License and provenance were preserved in:
- `LICENSES/ToRA-MIT.txt`
- `THIRD-PARTY-NOTICES.md`

### Verification
- **52 offline tests passed**
- No original members/files were deleted from the archive
- Target archive was overwritten in place with a recoverable backup available

## Notes
- GPU and external-network dependent runs were not executed in this pass.
- Changes focus on offline stability, compatibility, safety, and maintainability.
