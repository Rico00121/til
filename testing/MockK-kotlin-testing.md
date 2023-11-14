# MockK - mocking library for Kotlin

## Slot
a verifier and recorder for input params

```
enum class RecordingOutcome { RECORDED }

class Car {
    fun record(speed: Double): RecordingOutcome {
        TODO("not implement for showcase")
    }
}

// allow to capture parameter with non nullable type `Double`
val speedSlot = slot<Double>()

every {
    car.record(
        speed = capture(speedSlot), // makes mock match calls with any value for `speed` and record it in a slot
    )
} answers {
    println("Speed: ${speedSlot.captured}")
    RecordingOutcome.RECORDED
}

car.recordTelemetry(speed = 15.0,) // prints Speed: 15.0
```
