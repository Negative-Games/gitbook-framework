# Task Builder

Our custom task building framework allows you to create bukkit tasks with ease.

## Code Example

```java
        // Single task
        Task.task(plugin, () -> {
            // Task code here
        });
        
        // Task with delay
        Task.taskDelayed(plugin, 10, () -> {
            // Task code here
        });
        
        // Repeating Task 
        Task.taskRepeating(plugin, 0, 20, () -> {
            // Task code here
        });
        
        // Async Task
        Task.async(plugin, () -> {
           // Task code here 
        });
        
        // Async Task with delay
        Task.asyncDelayed(plugin, 10, () -> {
           // Task code here  
        });
        
        // Async Repeating Task
        Task.asyncRepeating(plugin, 0, 20, () -> {
           // Task code here 
        });
```
