# DEBUGGING.md: Android Auto EV Dashboard App - AGILE-AI Debugging Protocol

This document outlines the debugging protocol to be followed during the co-development of the Android Auto EV Dashboard application, adhering to the AGILE-AI Protocol. This protocol ensures a structured, analytical approach to error resolution, preventing the repetition of incorrect solutions.

## The Debugging Protocol: From Error to Insight

Upon any test failure or runtime exception, the primary workflow (RG-RR cycle) is immediately halted. The AI agent will then follow this structured debugging process:

### 1. HALT & DETECT

*   **Action**: Immediately stop the current development task upon detection of a test failure or a runtime exception.
*   **Purpose**: To prevent further erroneous actions and to isolate the point of failure.

### 2. INGEST & REFLECT

*   **Action**: Ingest the full context of the failure. This includes:
    *   The complete stack trace.
    *   The specific error message.
    *   The last 20 lines from the application logs (as generated per the Logging Standards in `SPEC.md`).
*   **Reflection**: Formulate a root cause analysis using a Chain-of-Thought process. The AI agent will use the `<error_hypothesis>` tag to explain the root cause step-by-step. **No code will be written at this stage.**
*   **Example Hypothesis Structure (AI Agent Output)**:
    ```xml
    <error_hypothesis>
    1. **Observation**: Test `test_ev_soc_display_updates` failed with `NullPointerException` at `EvDashboardService.kt:123`.
    2. **Log Analysis**: Logs show `CarInfoRepository.getLatestSoC()` returned null just before the crash.
    3. **Root Cause Hypothesis**: The `NullPointerException` is likely due to `EvDashboardService` attempting to dereference a null `SoC` value returned by `CarInfoRepository`. This could be because the repository is not correctly initialized or the data source is temporarily unavailable.
    4. **Proposed Investigation**: Check `CarInfoRepository` initialization and its data fetching logic, especially error handling for null or empty responses.
    </error_hypothesis>
    ```

### 3. PROPOSE & RETRY

*   **Action**: Based on the formulated hypothesis, propose a single, targeted code change to fix the issue. This change MUST be presented in a standard diff format.
*   **Purpose**: To apply a precise, minimal fix directly addressing the identified root cause.

### 4. VALIDATE

*   **Action**: Apply the proposed change and re-run the specific test that failed.
*   **Outcome**:
    *   If the test now passes, the debugging loop is exited, and the AI agent returns to the standard RG-RR cycle.
    *   If the test fails again, the loop repeats from Step 2. This time, the new error information and the failed hypothesis are added to the context, preventing the AI agent from trying the exact same failed solution twice.

## Logging for Debugging

Robust logging is crucial for effective debugging. Ensure that all code adheres to the Logging Standards defined in `SPEC.md`. Pay particular attention to:

*   Using `Log.d()` for detailed diagnostic information, including intermediate variable states and function inputs/outputs.
*   Using `Log.e()` with `exc_info=True` (or equivalent in Kotlin) for all caught exceptions to capture full stack traces.

By following this protocol, we aim to minimize debugging time, improve the reliability of fixes, and ensure a transparent and traceable error resolution process.
