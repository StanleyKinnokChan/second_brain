---
title: Temperature
tags:
  - ai
---
### Temperature: Definition

Temperature is a value between 0 and 1 (sometimes higher), and it adjusts how the model samples from its possible next words. (aka. deterministic vs stochastic) 

### 🧠 How It Works

- **Low temperature (e.g., 0.0–0.3)**:
    
    - The output is **more deterministic** and **focused**.
        
    - The model picks the most **likely** next word almost every time.
        
    - Useful for **factual**, **reliable**, or **repetitive** tasks.
        
- **Medium temperature (e.g., 0.7)**:
    
    - The model becomes more **creative** and **varied**.
        
    - Still generally coherent and relevant.
        
- **High temperature (e.g., 1.0+)**:
    
    - The model produces more **diverse** and **unpredictable** outputs.
        
    - Can be creative but also **less accurate** or even nonsensical.