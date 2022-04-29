When you call `proxyActivities` in a Workflow Function, you can set a range of ActivityOptions.

A Schedule-To-Start limits the maximum time that an Activity Task can sit in a Task Queue. It is used to identify whether a Worker is down or for Task routing.

Either `scheduleToCloseTimeout` or `scheduleToStartTimeout` must be set.

Type: time.Duration
Default: ∞ (infinity - no limit)

In this example, you can set the `ScheduleToStartTimeout` to 60 seconds.

```typescript
// Sample of typical options you can set
const { greet } = proxyActivities<typeof activities>({
  scheduleToCloseTimeout: '5m',
  ScheduleToStartTimeout: '60s',
  retry: {
    // default retry policy if not specified
    initialInterval: '1s',
    backoffCoefficient: 2,
    maximumAttempts: Infinity,
    maximumInterval: 100 * initialInterval,
    nonRetryableErrorTypes: [],
  },
});
```
