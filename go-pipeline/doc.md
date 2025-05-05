## Pipeline with Concurrency Patterns in Go

Use Copilot to assist in the design and implementation of a Go program using concurrency patterns with channels and goroutines. The pipeline processes data through three stages: generator, processor, and aggregator, showcasing "fly-in" and "fly-out" patterns.

### Overview
The application consists of:
1. Pipeline: orchestrates the execution of the three-stage pipeline.
2. Generator: Produces random integers within a configurable range and sends them to the processor.
3. Processor: Applies a computational transformation (e.g., factorial) to the integers and sends results to the aggregator.
4. Aggregator: Consolidates results (e.g., sum or average) and outputs a summary.
5. Main function: Initializes and starts the pipeline, managing goroutines and handling errors.
6. Tests: Validates the functionality of each stage and the overall pipeline.


### Project Setup Instructions

1. Create a Go module `pipeline-csp`.
2. Add a `.gitignore` file to exclude unnecessary files.
3. Organize the code into:
- go.mod: Defines the module and dependencies.
- go.sum: Contains checksums for module dependencies.
- `cmd/main.go`: Initializes the pipeline and manages goroutines.
- `internal/pipeline.go`: Implements the overall pipeline structure and flow.
- `internal/generator.go`: Implements the generator stage.
- `internal/processor.go`: Implements the processor stage.
- `internal/aggregator.go`: Implements the aggregator stage.
- `internal/pipeline_test.go`: Tests the overall pipeline functionality.
- `internal/generator_test.go`: Tests the generator stage.
- `internal/processor_test.go`: Tests the processor stage.
- `internal/aggregator_test.go`: Tests the aggregator stage.

### Specifications

- Main function (`cmd/main.go`):
  - Initializes and starts the pipeline, which consists of three stages: generator, processor, and aggregator.
  - Configures command-line flags:
    - `--min` and `--max`: Define the range of integers to generate.
    - `--count`: Specifies the number of integers to generate.
  - Validates input values:
    - Ensures `min < max`.
    - Ensures `count > 0`.
  - Creates channels for communication between stages:
    - `generator -> processor`: A channel to send generated integers.
    - `processor -> aggregator`: A channel to send processed results.
  - Uses `sync.WaitGroup` to ensure all goroutines complete before the program exits.
  - Handles errors gracefully:
    - Logs errors to the console.
    - Ensures all channels are closed properly.
  - Implements a signal handler to gracefully terminate the pipeline on receiving `SIGINT` or `SIGTERM`.

- Pipeline (`internal/pipeline.go`):
  - Orchestrates the execution of the three-stage pipeline.
  - Manages the flow of data between the generator, processor, and aggregator stages using channels.
  - Starts the generator, processor, and aggregator as separate goroutines.
  - Uses `sync.WaitGroup` to synchronize the completion of all stages.
  - Ensures proper cleanup:
    - Closes channels when a stage completes.
    - Handles errors and propagates them to the main function if necessary.
  - Provides a function `StartPipeline(min, max, count int) error` to initialize and run the pipeline.

- Generator (`internal/generator.go`):
  - Produces random integers within a configurable range (`min` to `max`) and sends them to the processor stage.
  - Accepts the following parameters:
    - `min`: Minimum value of the range.
    - `max`: Maximum value of the range.
    - `count`: Number of integers to generate.
    - `outChan`: A channel to send the generated integers.
  - Introduces random delays (e.g., `time.Sleep`) to simulate asynchronous behavior.
  - Uses multiple goroutines to implement the "fly-in" pattern:
    - Each goroutine generates a subset of the integers.
    - All goroutines write to the same output channel.
  - Closes the output channel when all integers are generated.

- Processor (`internal/processor.go`):
  - Applies a computational transformation (e.g., factorial) to each integer received from the generator and sends the results to the aggregator.
  - Accepts the following parameters:
    - `inChan`: A channel to receive integers from the generator.
    - `outChan`: A channel to send processed results to the aggregator.
  - Uses multiple goroutines to implement the "fly-in" pattern:
    - Each goroutine processes a subset of the integers.
    - All goroutines write to the same output channel.
  - Handles edge cases:
    - Ensures the transformation function (e.g., factorial) handles large numbers without causing overflow.
  - Closes the output channel when all integers are processed.

- Aggregator (`internal/aggregator.go`):
  - Consolidates results received from the processor and outputs a summary (e.g., sum or average).
  - Accepts the following parameters:
    - `inChan`: A channel to receive processed results from the processor.
  - Implements the "fly-out" pattern:
    - Consolidates results into a single output (e.g., a sum or average).
  - Outputs the final result to the console or a log file.
  - Handles edge cases:
    - Ensures the summary calculation is accurate even if no data is received (e.g., `count = 0`).

### Testing

- Generator (`internal/generator_test.go`):
  - Validates that the generator produces the correct number of integers (`count`) within the specified range (`min` to `max`).
  - Handles edge cases:
    - Ensures no integers are generated when `min == max`.
    - Ensures no integers are generated and the channel is closed properly when `count = 0`.
    - Handles large ranges to ensure performance and correctness.
  - Uses multiple goroutines to validate concurrency:
    - Ensures integers are generated without race conditions or deadlocks.
  - Handles invalid input values (e.g., `min > max`) gracefully.

- Processor (`internal/processor_test.go`):
  - Validates that the processor applies the transformation function (e.g., factorial) correctly to all integers received.
  - Handles edge cases:
    - Ensures the transformation function handles small and large integers (e.g., factorial of 0 or large numbers).
    - Handles invalid inputs (if applicable) gracefully.
  - Uses multiple goroutines to validate concurrency:
    - Ensures integers are processed without race conditions or deadlocks.
  - Handles channel closures and unexpected input gracefully.

- Aggregator (`internal/aggregator_test.go`):
  - Validates that the aggregator consolidates results (e.g., sum or average) correctly.
  - Handles edge cases:
    - Ensures the aggregator handles empty data gracefully when no input is received.
    - Ensures correctness with a single input.
    - Handles large datasets to ensure performance and correctness.
  - Uses multiple goroutines to validate concurrency:
    - Ensures results are consolidated without race conditions or deadlocks.
  - Handles channel closures and unexpected input gracefully.

- Pipeline (`internal/pipeline_test.go`):
  - Validates that the pipeline stages (generator, processor, aggregator) work together correctly and in order.
  - Handles edge cases:
    - Ensures the pipeline works correctly with `count = 0`, `min == max`, and large ranges.
  - Uses multiple goroutines to validate concurrency:
    - Ensures the pipeline handles concurrent operations across all stages without race conditions or deadlocks.
  - Validates error propagation:
    - Ensures errors in any stage are propagated correctly to the main function.
  - Validates signal handling:
    - Ensures the pipeline terminates gracefully on receiving `SIGINT` or `SIGTERM`.







