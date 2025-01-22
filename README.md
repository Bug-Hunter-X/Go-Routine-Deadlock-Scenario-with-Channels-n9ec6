# Go Routine Deadlock Scenario with Channels

This repository demonstrates a potential deadlock scenario in Go when using goroutines and channels.  The problem occurs when the receiving goroutine finishes processing all the data from the channel before the sending goroutine closes the channel. This creates a deadlock situation where the sending goroutine is blocked indefinitely, waiting for the channel to be read, while the receiving goroutine is already done.

The example showcases this issue. The solution provides a way to avoid this problem by ensuring that the close happens correctly, regardless of how quickly the receiving end processes the data.

## How to Reproduce

1. Clone this repository.
2. Run `go run bug.go` to see the deadlock (or at least it will hang indefinitely). 
3. Run `go run bugSolution.go` to observe the corrected behavior. 