# Pipeline Syntax  - Declarative Pipeline

```
- Declarative Pipeline is a relatively recent addition to Jenkins Pipeline

  pipeline {
      /* insert Declarative Pipeline here */
  }
  
  
  - The top-level of the Pipeline must be a block, specifically: pipeline { }.
  - No semicolons as statement separators. Each statement has to be on its own line.
  - Blocks must only consist of Sections, Directives, Steps, or assignment statements.
  - A property reference statement is treated as a no-argument method invocation. So, for example, input is treated as input().
```
